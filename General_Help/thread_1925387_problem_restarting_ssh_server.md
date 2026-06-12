---
title: "problem restarting ssh server"
date: 2012-02-14
forum: General Help
---

### Post by Mia_tech on 2012-02-14
(this is ubuntu 11.10) after I made some changes to the conf file, I tried to restart ssh, but it will not restart, I tried
```

jorge@nixboxen:~$ sudo /etc/init.d/ssh restart
[sudo] password for jorge: 
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service ssh restart
Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) and then start(8) utilities,
e.g. stop ssh ; start ssh. The restart(8) utility is also available.
ssh stop/waiting
ssh start/running, process 23455

```

also tried
```
jorge@nixboxen:~$ sudo stop ssh
stop: Unknown instance: 

```

how could I restart the service without restarting the machine?

Thanks

---

### Post by Doug S on 2012-02-14
In your first example, while there was a message about another way it did work. Your new sshd process id is 23455. You can verify with:```
ps aux | grep ssh
```You should see something like this:```
doug@test-smy:~$ ps aux | grep ssh
root     [COLOR=red]12002[/COLOR]  0.0  1.7   6420  2088 ?        Ss   14:14   0:00 /usr/sbin/sshd -D
root     12010  0.6  2.2   9384  2728 ?        Ss   14:17   0:01 sshd: doug [priv]
doug     12039  0.1  1.2   9384  1500 ?        S    14:17   0:00 sshd: doug@pts/0
doug     12157  0.0  0.6   4180   776 pts/0    S+   14:21   0:00 grep --color=auto ssh

```where 12002 is the new process id I got when I did the same command.

---

### Post by papibe on 2012-02-14
> **Mia_tech said:**
> how could I restart the service without restarting the machine?

Try this to stop the service
```
sudo service ssh stop
```
this to start it:
```
sudo service ssh start
```
and this to restart it (it must be running):
```
sudo service ssh restart
```
Hope it helps.
Regards.

---

### Post by Mia_tech on 2012-02-15
> **Doug S said:**
> In your first example, while there was a message about another way it did work. Your new sshd process id is 23455. You can verify with:```
ps aux | grep ssh
```You should see something like this:```
doug@test-smy:~$ ps aux | grep ssh
root     [COLOR=red]12002[/COLOR]  0.0  1.7   6420  2088 ?        Ss   14:14   0:00 /usr/sbin/sshd -D
root     12010  0.6  2.2   9384  2728 ?        Ss   14:17   0:01 sshd: doug [priv]
doug     12039  0.1  1.2   9384  1500 ?        S    14:17   0:00 sshd: doug@pts/0
doug     12157  0.0  0.6   4180   776 pts/0    S+   14:21   0:00 grep --color=auto ssh

```where 12002 is the new process id I got when I did the same command.

This is how I know it hasn't stop it

before trying to stop it
```
jorge@nixboxen:~$ ps -e | grep ssh
 2445 ?        00:00:00 ssh-agent
 4695 ?        00:00:01 sshd
 4891 ?        00:01:46 sshd

```

trying to stop it...

```
jorge@nixboxen:~$ sudo /etc/init.d/ssh stop
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service ssh stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop ssh
```

after supously stopped
```
jorge@nixboxen:~$ ps -e | grep ssh
 2445 ?        00:00:00 ssh-agent
 4695 ?        00:00:01 sshd
 4891 ?        00:01:46 sshd

```

as you can see, it is still looks the same, and I still can connect to ssh.. so it doesn't stop it

---

### Post by Mia_tech on 2012-02-15
> **papibe said:**
> Try this to stop the service
```
sudo service ssh stop
```
this to start it:
```
sudo service ssh start
```
and this to restart it (it must be running):
```
sudo service ssh restart
```
Hope it helps.
Regards.

tried that too.. doesn't work!..
```
jorge@nixboxen:~$ sudo service ssh stop
stop: Unknown instance: 

```

---

### Post by Mia_tech on 2012-02-15
I had to actually kill the process

```
sudo kill processNumber
```

well, after I killed it, it seems to responde just fine to 

```
sudo service ssh stop/start/restart
```

Anyway, don't know if this happened to me only, but if you're running 11.10 from an upgrade, and can't stop ssh, you probably gonna have to kill the process, and after that just use

```
sudo service ssh stop/start/restart
```

---

