---
title: "Strange Behaviour in Shell Bash - everything that run as sudo or root get stopped"
date: 2011-03-11
forum: General Help
---

### Post by cripperz on 2011-03-11
Hi All,

i am not sure if anyone have experienced this, i realize that my server lags most of the time and after a restart, it goes back normal just for awhile

Other than that, i am not able to do any apt-get as it always get stopped. Wondering if there is any spawned process that kills every root command i made.

Below is an example

```
root@freeshell:/home/cp# sudo apt-get install mutt rkhunter chkrootkit logwatch
Reading package lists... Done
Building dependency tree... 52%
[1]+  Stopped                 sudo apt-get install mutt rkhunter chkrootkit logwatch
Building dependency tree
Reading state information... Done
rkhunter is already the newest version.
Suggested packages:
  mixmaster urlview
Recommended packages:
  libdate-manip-perl
The following NEW packages will be installed:
  chkrootkit logwatch mutt
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 1673kB of archives.
After this operation, 8434kB of additional disk space will be used.
Get:1 http://sg.archive.ubuntu.com hardy-updates/main chkrootkit 0.47-1.1ubuntu0.3 [281kB]
Get:2 http://sg.archive.ubuntu.com hardy-updates/main logwatch 7.3.6-1ubuntu1.1 [307kB]
Get:3 http://sg.archive.ubuntu.com hardy/main mutt 1.5.17+20080114-1ubuntu1 [1085kB]
Fetched 1673kB in 5s (290kB/s)
Preconfiguring packages ...


```


The last line will just remain there and it seems like it hang. Also, i wont be able to apt-get anymore after that.

```

root@freeshell:/home/cp# w
 05:48:47 up  1:00,  1 user,  load average: 0.70, 1.33, 1.77
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
cp       pts/3    cm25.eta92.maxon 05:40    0.00s  6.42s  0.17s sshd: cp [priv]

[1]+  Stopped                 sudo apt-get install mutt rkhunter chkrootkit logwatch
root@freeshell:/home/cp#

```

and i will always see that [1]+ Stopped message to any command i type thereafter. Strange behaviour isnt it? Has anyone every experience this before. Please share.

---

### Post by CharlesA on 2011-03-11
If you are already logged in as root, you don't need to use sudo.

Does it do the same thing if you don't use sudo?

---

### Post by cripperz on 2011-03-11
Hi There,

thanks for the reply. Yeap it does the same when im logged in as a sudo user doing the sudo command.

> cp@freeshell:~$ sudo apt-get install mutt rkhunter chkroot logwatch
Reading package lists... Done
Building dependency tree
Reading state information... Done

[1]+  Stopped                 sudo apt-get install mutt rkhunter chkroot logwatch


---

### Post by CharlesA on 2011-03-11
But does it happen if you are logged in as root and not using sudo?

Can you post the output of this as well:

```
free -m
```

---

### Post by cripperz on 2011-03-11
> **CharlesA said:**
> But does it happen if you are logged in as root and not using sudo?

Can you post the output of this as well:

```
free -m
```


Hi there,

at the moment, i just rebooted the server and there is no such lag or whatsoever. Just that i can apt-get or any commands i run as a sudo or root will be stopped / killed.

Below is the free -m print.

```
cp@freeshell:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           503        490         12          0          7        169
-/+ buffers/cache:        313        189
Swap:         5867         83       5784
cp@freeshell:~$

```

I also by default deny any logging by root directly to ssh. Do you still want me to try and enable the logging to ssh by root directly ?

---

### Post by CharlesA on 2011-03-11
> **cripperz said:**
> 
I also by default deny any logging by root directly to ssh. Do you still want me to try and enable the logging to ssh by root directly ?

You shouldn't need to login directly as root. You can just su or use sudo -i to get a root shell.

---

### Post by cripperz on 2011-03-11
Noted.

But that still doesnt explain the issue of all my sudo or root commands getting stopped. 

I am just wondering if anyone have come across this. I am pretty sure that its being hacked.

After all i offer free shell access to this server ...not suprise if someone have hacked it.

---

### Post by wilee-nilee on 2011-03-11
If your in root sudo isn't needed and wont work.

---

### Post by cripperz on 2011-03-11
> **wilee-nilee said:**
> If your in root sudo isn't needed and wont work.

Erm, i have been doing so for pass years. I have no issue using sudo in root. Well anyways that is not the main topic or issue.

Just finding out if someone who have similar issues or experience getting hacked like this before.

---

### Post by CharlesA on 2011-03-11
Does it do the same thing if you run something like this:

```
sudo vi somefile
```

---

### Post by matt_symes on 2011-03-11
Hi

Is apt-get the only admin command that fails under root ?

Kind regards

---

