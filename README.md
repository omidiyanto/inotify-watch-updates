1. Create user system service directory
    ```bash
    mkdir -p /home/info/.config/systemd/user
    ```

2. Create the service file
    ```bash
    nano /home/info/.config/systemd/user/watch-updates.service
    ```
    Fill with this configuration:
    ```
    [Unit]
    Description=Run watch-updates.sh script in background

    [Service]
    User=info
    ExecStart=/home/info/cronjob-scheduler/watch-updates.sh
    
    [Install]
    WantedBy=default.target
    ```

3. Enable linger for user 'info'
    ```bash
    loginctl enable-linger info
    ```

4. Reload user system services, also start and enable the service
    ```bash
    systemctl daemon-reload --user
    systemctl --user enable --now watch-updates.service
    ```
5. Check the service is now running 
    ```bash
    systemctl status watch-updates.service
    ```

