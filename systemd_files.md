# The Systemd files for running Peggy.

## 1. Systemd unit file for running peggy

To enable, copy the below to /etc/systemd/system/peggy.service

```
[Unit]
Description=Peggy Node
After=network-online.target

[Service]
User=[username]
ExecStart=/usr/bin/peggy start --pruning=nothing                  
Restart=always
RestartSec=3
LimitNOFILE=4096

[Install]
WantedBy=multi-user.target
```

Then you will need to reload systemd and start the service

```sudo systemctl daemon-reload```

```sudo systemctl start peggy```

To see the logs
```journalctl -u peggy -f```



## 2. Systemd unit file for running geth Testnet Service

To enable, copy the below to /etc/systemd/system/geth-testnet.service

```
[Unit]
Description=Geth Testnet Service
After=network-online.target

[Service]
User=[username]
ExecStart=/usr/bin/geth --syncmode "light" --rinkeby --http
Restart=always
RestartSec=3
LimitNOFILE=4096

[Install]
WantedBy=multi-user.target
```

Then you will need to reload systemd and start the service

```sudo systemctl daemon-reload```

```sudo systemctl start geth-testnet```

To see the logs
```journalctl -u geth-testnet -f```
