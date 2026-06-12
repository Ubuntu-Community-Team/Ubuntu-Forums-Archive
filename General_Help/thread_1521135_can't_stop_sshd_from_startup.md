---
title: "can't stop sshd from startup"
date: 2010-06-30
forum: General Help
---

### Post by w4rh4wk on 2010-06-30
i got a problem with the ssh daemon

i installed it, but every time i start my system, sshd is running, but i can't find out where it's startup entry is located.

```
ls /etc/rc*.d | grep ssh
```

returns nothing, which indeed is true, 'cause i removed the links from the runlevel directories. i checked the rc.local file which is empty and never added a line anywhere to start the ssh daemon explicit.

i'm using the latest ubuntu with updates and everything (at least i think so). in my gnome startup application preferences the only thing related to ssh is the ssh key agent. but if i deactivate it, sshd still startsup.

```
sudo update-rc.d -f ssh remove
```
didn't helped either

(adding the line "/etc/init.d/ssh stop" to rc.local doesn't prevent ssh from beeing run. which means.. ssh is started AFTER rc.local is excuted)

---

### Post by mhgsys on 2010-06-30
Guiwise but still; 
Look under System>Preferences>Startup Applications

ssh agent will be there

---

### Post by w4rh4wk on 2010-06-30
well can't find it...
disabling ssh key agent doesn't stop ssh from being launched.

---

### Post by mhgsys on 2010-06-30
I'm browsing around for you.

---

### Post by mhgsys on 2010-06-30
[http://ubuntuforums.org/showthread.php?t=1402580](http://ubuntuforums.org/showthread.php?t=1402580)

> **davidmb said:**
> Hi,

Haven't really tried it, but this should work:
1. Open a console.
2. Type the following:
```
[INDENT][FONT=Courier New]sudo update-rc.d -f ssh remove[/FONT]
[/INDENT]
```This won't remove the sshd software package, but it won't automatically start again.

After this, to start (alternatively "stop") sshd manually you can do the following from the command line:
```
[INDENT][FONT=Courier New]sudo invoke-rc.d ssh start
[/FONT][/INDENT]
```

---

### Post by w4rh4wk on 2010-06-30
i already found that post.
as i told in the first post:
```
sudo update-rc.d -f ssh remove
```
didn't helped and
```
sudo invoke-rc.d ssh start
```
didn't helped either

invoke-rc.d stops sshd for the current session, but after a reboot, it's online again.

---

### Post by prshah on 2010-06-30
```
sudo service ssh stop
``` And it will be stopped until manually restarted again (will not restart after a reboot).

You can check the status with ```
sudo service ssh status
```

If you want to remove the service permanently, then you can uninstall ssh server```
sudo apt-get remove openssh-server
```

---

### Post by w4rh4wk on 2010-06-30
> **prshah said:**
> ```
sudo service ssh stop
``` And it will be stopped until manually restarted again (will not restart after a reboot).

You can check the status with ```
sudo service ssh status
```

If you want to remove the service permanently, then you can uninstall ssh server```
sudo apt-get remove openssh-server
```

i didn't know about the "service" command, but it looks like that didn't fix it. i executed "sudo service ssh stop".. return message: "ssh stop/waiting"... then i reboot.. and when i check, ssh status: ssh is running

i viewed the man page and it looks like service is just a tool to handle the links located in the rc.d directories..

i don't want to remove ssh cause i need it (sometimes), but it annoys me that i can't work out how to remove that program from automatically starting up.

---

### Post by mhgsys on 2010-06-30
[COLOR="Red"]**Took me a while but I think I found it;**[/COLOR]
```

 [COLOR="SeaGreen"] 
}

check_config() {
    if [ ! -e /etc/ssh/sshd_not_to_be_run ]; then
        /usr/sbin/sshd $SSHD_OPTS -t || exit 1
    fi
}
[/COLOR]


```

So;....

**Create /etc/ssh/sshd_not_to_be_run**
```
sudo nano /etc/ssh/sshd_not_to_be_run
```

save it;
(Ctrl+O , enter, Ctrl+X)
reboot

[COLOR="Blue"]Test results over here; 
mhg@mhg-laptop:~$ killall sshd
sshd: no process found
 mhg@mhg-laptop:~$ sudo service ssh stop
stop: Unknown instance [/COLOR]

**if you want to run it again; remove /etc/ssh/sshd_not_to_be_run **
```
sudo rm /etc/ssh/sshd_not_to_be_run
```
and
```
sudo service ssh start
```

---

### Post by w4rh4wk on 2010-06-30
thx, it worked...
just created that file...

now if i wanna start sshd i need to rename that file.. no problem, just edited the init script.

which still doesn't solve the issue i don't know why it's starting all the time / even if i removed the rc.d links...

well thanks for the workaround that will do for now.

---

### Post by mhgsys on 2010-06-30
Your welcome; 

I was not able to figure out an other way.. took me long enough to figure this out. 
Reading the ssh scripts....

---

### Post by The Cog on 2010-06-30
For Lucid, the ssh server is started by upstart which runs scripts in /etc/init. The script /etc/init/ssh.conf is the file you need to edit. I think that commenting out the line **start on filesystem** by putting a hash in front will probably do the trick.

But reading that script further, it looks like creating a file **/etc/ssh/sshd_not_to_be_run** is the way you should do it, but I don't know if that will prevent starting the daemon when you want it with **sudo start ssh**.

---

### Post by mhgsys on 2010-06-30
I've been looking like crazy for a simple line like that; 

lol.

I'll leave the testing to w4rh4wk...

---

### Post by w4rh4wk on 2010-07-01
> **mhgsys said:**
> I'll leave the testing to w4rh4wk...

it works perfectly this way

---

