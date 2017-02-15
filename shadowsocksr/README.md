# shadowsocksr

This image uses CMD to run the containers as an executable.

## Usage

### Server

    docker run -d --name ssserverr -p 8388:8388 zhenkyle/shadowsocksr ssserver -s 0.0.0.0 -p 8388 -k mypassword -m aes-256-cfb -o tls1.2_ticket_auth_compatible -O auth_sha1_v2_compatible

### Client
    docker run -d --name sslocalr -p 1080:1080 zhenkyle/shadowsocksr sslocal -s SERVER_ADDR -p 1080 -k mypassword -m aes-256-cfb -o tls1.2_ticket_auth_compatible -O auth_sha1_v2_compatible

## More Option

### Server

    docker run --rm zhenkyle/shadowsocksr ssserver -h

    usage: ssserver [OPTION]...
    A fast tunnel proxy that helps you bypass firewalls.

    You can supply configurations via either config file or command line arguments.

    Proxy options:
      -c CONFIG              path to config file
      -s SERVER_ADDR         server address, default: 0.0.0.0
      -p SERVER_PORT         server port, default: 8388
      -k PASSWORD            password
      -m METHOD              encryption method, default: aes-256-cfb
      -o OBFS                obfsplugin, default: http_simple
      -t TIMEOUT             timeout in seconds, default: 300
      --fast-open            use TCP_FASTOPEN, requires Linux 3.7+
      --workers WORKERS      number of workers, available on Unix/Linux
      --forbidden-ip IPLIST  comma seperated IP list forbidden to connect
      --manager-address ADDR optional server manager UDP address, see wiki

    General options:
      -h, --help             show this help message and exit
      -d start/stop/restart  daemon mode
      --pid-file PID_FILE    pid file for daemon mode
      --log-file LOG_FILE    log file for daemon mode
      --user USER            username to run as
      -v, -vv                verbose mode
      -q, -qq                quiet mode, only show warnings/errors
      --version              show version information

    Online help: <https://github.com/shadowsocks/shadowsocks>

### Client

    docker run --rm zhenkyle/shadowsocksr sslocal -h

    usage: sslocal [OPTION]...
    A fast tunnel proxy that helps you bypass firewalls.

    You can supply configurations via either config file or command line arguments.

    Proxy options:
      -c CONFIG              path to config file
      -s SERVER_ADDR         server address
      -p SERVER_PORT         server port, default: 8388
      -b LOCAL_ADDR          local binding address, default: 127.0.0.1
      -l LOCAL_PORT          local port, default: 1080
      -k PASSWORD            password
      -m METHOD              encryption method, default: aes-256-cfb
      -o OBFS                obfsplugin, default: http_simple
      -t TIMEOUT             timeout in seconds, default: 300
      --fast-open            use TCP_FASTOPEN, requires Linux 3.7+

    General options:
      -h, --help             show this help message and exit
      -d start/stop/restart  daemon mode
      --pid-file PID_FILE    pid file for daemon mode
      --log-file LOG_FILE    log file for daemon mode
      --user USER            username to run as
      -v, -vv                verbose mode
      -q, -qq                quiet mode, only show warnings/errors
      --version              show version information

    Online help: <https://github.com/shadowsocks/shadowsocks>
