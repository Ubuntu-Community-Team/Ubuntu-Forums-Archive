---
title: "help with placement of &quot;sshd&quot; command"
date: 2010-12-30
forum: General Help
---

### Post by 0949er on 2010-12-30
Hey guys, how are you? I would like my SSH deamon to start up at system boot. I have forgotten how linux in general handles "start-up" scripts so I am having trouble finding a place to put the command.

As of right now, my ssh server starts up only once my current users logs onto the system. now, I know that you need "root" permission to start the sshd server, so how come it waits for the user to log-in to start up? and furthermore, how does it even load if it requires root permission, and I dont have to enter my password for it to start?

I hope somebody can help answer these questions. Thank you for your time.

p.s. how do you see what is current set to "run at startup" in the first place? Like microsofts "msconfig"? (yuck, I hate microsoft)

---

### Post by 0949er on 2010-12-30
bump :)

---

### Post by hawkmage on 2010-12-30
I assume that you are running a version of Ubuntu more recent than 6.10.  Do you have a file named "/etc/init/ssh.conf"?  If so look at the file, is there a line that starts with "start on"? What is on that line?  Mine is "start on filesystem"

---

### Post by 0949er on 2010-12-31
> **hawkmage said:**
> I assume that you are running a version of Ubuntu more recent than 6.10.  Do you have a file named "/etc/init/ssh.conf"?  If so look at the file, is there a line that starts with "start on"? What is on that line?  Mine is "start on filesystem"

start on filesystem is present. But it doesnt seem to start UNTIL this user logs on. I have tried multiple times, and have waited up to 5 min after startup and no working ssh connection until log on.

---

### Post by cipherboy_loc on 2010-12-31
From the terminal (Applications -> Accessories -> Terminal):
```
sudo update-rc.d sshd defaults
```
will add the sshd init.d service to the default run levels.


Cipherboy

---

### Post by 0949er on 2010-12-31
> **cipherboy_loc said:**
> From the terminal (Applications -> Accessories -> Terminal):
```
sudo update-rc.d sshd defaults
```will add the sshd init.d service to the default run levels.


Cipherboy

```

swooshonln@power-house:/etc/init$ sudo update-rc.d sshd defaults
[sudo] password for swooshonln: 
update-rc.d: /etc/init.d/sshd: file does not exist

```


however there is a file "/etc/init.d/ssh"

---

### Post by hawkmage on 2010-12-31
Normally the /etc/init.d/sshd is not used by Upstart.  

Is there anything in the /var/log/daemon.log* about the ssh service?

---

### Post by cipherboy_loc on 2011-01-02
Sorry, my bad. It is /etc/init.d/ssh:
```
sudo update-rc.d ssh defaults
```


Cipherboy

> **0949er said:**
> ```

swooshonln@power-house:/etc/init$ sudo update-rc.d sshd defaults
[sudo] password for swooshonln: 
update-rc.d: /etc/init.d/sshd: file does not exist

```
however there is a file "/etc/init.d/ssh"

---

