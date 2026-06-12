---
title: "Help with screen"
date: 2010-10-05
forum: General Help
---

### Post by gnulnx on 2010-10-05
Hi everyone.  I am looking for some help with screen.  I am attempting to resume another user's screen (-r) and execute a command in it (-X)  While I can resume (-r), if I combine that with executing a command (-X), errors arise.  Instead of trying to explain my problems, see the below outputs.


[LIST]
[*]All screens are ran as one user ("minecraft")
[*]minecraft has his .screenrc file setup to enable multiuser mode, and to allow access from kjohnson
[/LIST]
```
minecraft@mc1:~$ screen -list
There are screens on:
    18810.threatgreater    (10/05/2010 02:23:31 PM)    (Multi, detached)
    1185.baron    (10/05/2010 07:29:26 AM)    (Multi, detached)
    1184.murpo    (10/05/2010 07:29:26 AM)    (Multi, detached)
    1182.michaelvash    (10/05/2010 07:29:26 AM)    (Multi, detached)
    1181.dungeonbstrd    (10/05/2010 07:29:26 AM)    (Multi, detached)
5 Sockets in /var/run/screen/S-minecraft.
minecraft@mc1:~$ ls -al !$
ls -al /var/run/screen/S-minecraft/
total 0
drwx------ 2 minecraft minecraft 140 2010-10-05 20:10 .
drwxr-xr-x 3 root      utmp       60 2010-10-05 07:29 ..
prw------x 1 minecraft minecraft   0 2010-10-05 20:00 1181.dungeonbstrd
prw------x 1 minecraft minecraft   0 2010-10-05 20:00 1182.michaelvash
prw------x 1 minecraft minecraft   0 2010-10-05 20:09 1184.murpo
prw------x 1 minecraft minecraft   0 2010-10-05 20:00 1185.baron
prw------x 1 minecraft minecraft   0 2010-10-05 20:00 18810.threatgreater

``````
kjohnson@mc1:~$ screen -r minecraft/
There are several suitable screens on:
    18810.threatgreater    (10/05/2010 02:23:31 PM)    (Multi, detached)
    1185.baron    (10/05/2010 07:29:26 AM)    (Multi, detached)
    1184.murpo    (10/05/2010 07:29:26 AM)    (Multi, detached)
    1182.michaelvash    (10/05/2010 07:29:26 AM)    (Multi, detached)
    1181.dungeonbstrd    (10/05/2010 07:29:26 AM)    (Multi, detached)
Type "screen [-d] -r [pid.]tty.host" to resume one of them.
kjohnson@mc1:~$ screen -r minecraft/murpo
<<SCREEN SHOWS UP>>
kjohnson@mc1:~$ screen -r minecraft/murpo -X date
Cannot opendir /var/run/screen/S-minecraft: Permission denied
kjohnson@mc1:~$ sudo chmod 755 /var/run/screen/S-minecraft/
kjohnson@mc1:~$ screen -r minecraft/murpo -X date
Directory /var/run/screen/S-minecraft must have mode 700.
kjohnson@mc1:~$ sudo chmod 700 /var/run/screen/S-minecraft/
kjohnson@mc1:~$ screen -r minecraft/murpo -X date
Cannot opendir /var/run/screen/S-minecraft: Permission denied

```

I've tried everything that I can find.  Please, any suggestions?

---

### Post by gnulnx on 2010-10-06
Reading through the screen man page again and I can't find anything that I might be doing wrong.
> [COLOR=#000000][FONT=Times New Roman][COLOR=#333333][FONT=Helvetica]  **-X**   Send the specified command to a running screen  session.  You  can             use  the  **-d** or **-r** option to tell screen to look only for attached             or detached screen sessions. Note that this command  doesn't  work             if the session is password protected.[/FONT][/COLOR][/FONT][/COLOR]
My sessions are not password protected.

What is confusing me most is, I can resume the screen, which I assume needs access to /var/run/screen/S-minecraft, however when I try to resume and execute (-r minecraft/name -X cmd), I get a permission denied error for that very directory.

---

