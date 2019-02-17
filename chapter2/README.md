# bhnet.py

Netcatが使えない環境でのpythonスクリプトによる代用

## 使い方
```
$ python bhnet.py -h

BHP Net Tool

Usage: bhpnet.py -t target_host -p port
-l --listen              - listen on [host]:[port] for
                           incoming connections
-e --execute=file_to_run - execute the given file upon
                           receiving a connection
-c --command             - initialize a command shell
-u --upload=destination  - upon receiving connection upload a
                           file and write to [destination]


Examples:
bhnet.py -t 192.168.0.1 -p 5555 -l -c
bhnet.py -t 192.168.0.1 -p 5555 -l -u c:\target.exe
bhnet.py -t 192.168.0.1 p- 5555 -l -e"cat /etc/passwd"
echo 'ABCDEFGHI' | ./bhnet.py -t 192.168.11.12 -p 135
```

## やってみる
ポート開ける
```
$ python bhnet.py -l -t 0.0.0.0 -p 5555 -c
```

接続
```
$ python bhnet.py -t 0.0.0.0 -p 5555
<BHP:#>  ls -lha
total 32K
drwxr-xr-x 2 root root 4.0K Feb 17 22:16 .
drwxr-xr-x 4 root root 4.0K Feb 17 21:59 ..
-rwxr-xr-x 1 root root 6.0K Feb 17 22:16 bhnet.py
-rw-r--r-- 1 root root   11 Feb 17 22:09 README.md
-rw-r--r-- 1 root root  375 Feb 17 21:59 tcp-client.py
-rw-r--r-- 1 root root  796 Feb 17 21:59 tcp-server.py
-rw-r--r-- 1 root root  348 Feb 17 21:59 udp-client.py
<BHP:#>  pwd
/root/Documents/black-hat-python/chapter2
<BHP:#>  
```
EOFに到達すると，標準入力を読み込むので
始めに<CTRL-D>を押してEOFを送信する．
