# Lab 2: Answers

Name: Onat Uzun  
Student ID: 20231701019

## Part A: Creating and Organizing

**A1.**
```
$ pwd
/home/codespace/lab2/techcorp
```

**A2.**
```
$ mkdir -p projects/2026/{alpha,beta,gamma}
$ ls projects/2026
alpha  beta  gamma
```

**A3.**
```
$ touch projects/2026/alpha/README.md
$ ls -l projects/2026/alpha/README.md
-rw-r--r-- 1 codespace codespace 0 Oct 20 07:59 projects/2026/alpha/README.md
```

**A4.**
```
$ cp -r hr/policies projects/2026/beta/
$ ls -l projects/2026/beta/policies/
total 8
-rw-r--r-- 1 codespace codespace 13 Oct 20 08:00 leave.txt
-rw-r--r-- 1 codespace codespace 14 Oct 20 08:00 remote.txt
```

**A5.**
```
$ mv projects/2026/gamma projects/2026/delta
$ ls projects/2026
alpha  beta  delta
```

**A6.**
```
$ ln -s ../engineering/docs/api.md shared/api_link
$ ls -l shared/api_link
lrwxrwxrwx 1 codespace codespace 26 Oct 20 08:01 shared/api_link -> ../engineering/docs/api.md
```

**A7.**
```
$ cat shared/api_link
api reference
```
The symbolic link points to the original file and displays its contents without copying the file.

## Part B: Users and Groups

**B1.**
```
$ id
uid=1000(codespace) gid=1000(codespace) groups=1000(codespace),986(pipx),987(python),988(oryx),989(golang),990(docker),991(sdkman),992(ruby),993(php),994(conda),995(nvm),996(hugo),1001(ssh)
```

**B2.**
```
$ sudo groupadd engineering
$ sudo groupadd finance
$ getent group engineering finance
engineering:x:1002:
finance:x:1003:
```

**B3.**
```
$ sudo useradd -m alice
$ sudo useradd -m bob
$ ls -ld /home/alice /home/bob
drwxr-x--- 2 alice alice 4096 Oct 20 08:02 /home/alice
drwxr-x--- 2 bob bob 4096 Oct 20 08:02 /home/bob
```

**B4.**
```
$ sudo usermod -aG engineering alice
$ sudo usermod -aG finance bob
$ sudo usermod -aG finance alice
```
No output (commands executed successfully).

**B5.**
```
$ groups alice
alice : alice engineering finance

$ groups bob
bob : bob finance
```

## Part C: Permissions

**C1.**

$ ./engineering/src/build.sh
bash: ./engineering/src/build.sh: Permission denied

$ chmod u+x engineering/src/build.sh

$ ./engineering/src/build.sh
building

$ ls -l engineering/src/build.sh
-rwxr--r-- 1 codespace codespace 26 Oct 20 07:55 engineering/src/build.sh

**C2.**



$ find . -type f -perm -0002
./hr/records/anna.txt
./finance/invoices/inv_103.csv
find: './engineering/locked/flag.txt': Permission denied
./engineering/src/mod_7.c

**C3.**

$ chmod o-w hr/records/anna.txt finance/invoices/inv_103.csv engineering/src/mod_7.c

$ find . -type f -perm -0002
find: './engineering/locked/flag.txt': Permission denied



**C4.**

$ touch shared/team.txt
$ sudo chgrp engineering shared/team.txt
$ ls -l shared/team.txt
-rw-r--r-- 1 codespace engineering 0 Oct 20 08:14 shared/team.txt
