---
title: "Disable ssh server"
date: 2010-02-24
forum: General Help
---

### Post by bfrederi on 2010-02-24
I need ssh to connect to other servers, but I want to disable the sshd server on Ubuntu 9.10 because I don't want incoming connections to my workstation.

Disabling sshd won't effect my ability to use the ssh client to connect to other servers, correct? How do I go about disabling the ssh server on Ubuntu 9.10?

---

### Post by jtdeloach10 on 2010-02-24
sudo apt-get remove openssh-server

You can still SSH to other servers.

---

### Post by PoHandle on 2010-02-24
I was under the assumption that openssh-server was not installed by default in 9.10.

---

### Post by Iowan on 2010-02-24
> **PoHandle said:**
> I was under the assumption that openssh-server was not installed by default in 9.10.
The client is pre-installed - the server must be added (to a workstation in particular - it can be installed during a server-install).

---

### Post by bfrederi on 2010-02-25
openssh-server doesn't come pre-installed. I installed it when I first set up my new workstation. I actually forgot that I installed it because I did it during a tutorial written by someone else without paying much attention to what I was doing, and then quickly forgot about it.

Edit:
> **jtdeloach10 said:**
> sudo apt-get remove openssh-server

You can still SSH to other servers.

Forgot to mention that this is what I was wanting. Thanks!

---

### Post by lavinog on 2010-02-25
> **bfrederi said:**
> openssh-server doesn't come pre-installed. I installed it when I first set up my new workstation. I actually forgot that I installed it because I did it during a tutorial written by someone else without paying much attention to what I was doing, and then quickly forgot about it.

```
sudo apt-get remove openssh-server
```

edit: Sorry, missed the 2nd post.

---

### Post by 2hot6ft2 on 2010-02-25
> **bfrederi said:**
> I need ssh to connect to other servers, but **I want to disable the sshd server** on Ubuntu 9.10 because I don't want incoming connections to my workstation.

Disabling sshd won't effect my ability to use the ssh client to connect to other servers, correct? How do I go about disabling the ssh server on Ubuntu 9.10?
I see posts to remove it but no one for just disabling it so here's how to just turn it off:
> How to start/stop/restart the SSH Server
```
sudo /etc/init.d/ssh stop
```

(Replace stop by start for starting it again, or restart to just restart it)

What I did was made a txt. file with that in it and put it in my home folder then drug it to the top panel and created a launcher so I can disable it when not using it. The options for it were.
Run in terminal
Name it whatever you want
in the command box put
```
sudo /etc/init.d/ssh stop
```
Click on the icon to change it to something else.
Done I didn't put anything in the command variables or comment areas.

When you click on it a terminal will open asking for your password just type it in and hit enter and it will turn ssh off and close the terminal.

---

### Post by San_SS! on 2010-02-25
If you want to disable it from startup you have to:
```
[B]
#update-rc.d -f ssh remove[/B]

```

Hope this was what you were looking for.

---

### Post by bfrederi on 2010-02-26
> **San_SS! said:**
> If you want to disable it from startup you have to:
```
[B]
#update-rc.d -f ssh remove[/B]

```

Hope this was what you were looking for.

This is also handy, because I noticed they removed Services from the System -> Administration menu. Any idea why they did that, or if it has moved somewhere else? That seemed to be the way people disabled it in previous distributions.

---

### Post by San_SS! on 2010-02-26
> **bfrederi said:**
> This is also handy, because I noticed they removed Services from the System -> Administration menu. Any idea why they did that, or if it has moved somewhere else? That seemed to be the way people disabled it in previous distributions.

I think they changed the way the services are managed. From SysV to Upstart, so the GUI service manager is not working. For more infor you can read [this thread]("http://ubuntuforums.org/showthread.php?t=1294610").

---

### Post by zer010 on 2011-02-06
> **San_SS! said:**
> If you want to disable it from startup you have to:
```
[B]
#update-rc.d -f ssh remove[/B]

```Hope this was what you were looking for.
I was wondering if I understand this one. I did a search for "rc.d" and it brought up several files.  I found one that looked like it might be what this refers to: /var/lib/update-rc.d that has a file named "ssh" that has the mentioned code as the only content.  To disable ssh from startup, are you suggesting that commenting that line will do the trick? I'm just trying to verify, because that code is a bit vague.

---

### Post by mikejonesey on 2011-02-21
> **zer010 said:**
> I was wondering if I understand this one. I did a search for "rc.d" and it brought up several files.  I found one that looked like it might be what this refers to: /var/lib/update-rc.d that has a file named "ssh" that has the mentioned code as the only content.  To disable ssh from startup, are you suggesting that commenting that line will do the trick? I'm just trying to verify, because that code is a bit vague.

?

update-rc.d is a command, you don't need to search for anything;

it'll run /usr/sbin/update-rc.d, -f refers to you are selecting a file, ssh (the filename), and remove removes all referenced from rc to the init...

ie it should prevent ssh without uninstalling it;

however I found ssh is one of two tricky ones to disable as it is referenced in more places...

after running;

```
sudo update-rc.d -f ssh stop
sudo /etc/init.d/ssh stop
sudo sevice ssh stop

```

I am still unable to disable the ssh server...

as a service that requires the latest security updates, it's best to have this service installed if you are going to use it; (rather than install and uninstall, let alone this would be frustrating)...

I'm testing a couple more things, worst case scenario would be a hacky script, (exta init.d script to shutdown ssh server on start...),

hopefully I can come up with something a little cleaner... or i've missed someting mondane...

---

### Post by mikejonesey on 2011-02-21
I found info here;

[http://fossplanet.com/f10/disable-ssh-startup-lucid-14539/](http://fossplanet.com/f10/disable-ssh-startup-lucid-14539/)

which states sshd can't be disabled via rc as it's started by upstart instead;

the fix they came up with was to mod / move the ssh.conf file depending on what you want...

good enough for me...

update: tested for ssh and samba, I added a hash before the start on filesystem in both conf files and it works on both.

---

### Post by zer010 on 2011-02-21
I appreciate the clarification and the update. :thumb-up: I think it was the "#" that confused me into thinking it was a line in a file that was commented out. :p

---

### Post by Insperatus on 2011-08-16
> **mikejonesey said:**
> I found info here;

[http://fossplanet.com/f10/disable-ssh-startup-lucid-14539/](http://fossplanet.com/f10/disable-ssh-startup-lucid-14539/)

which states sshd can't be disabled via rc as it's started by upstart instead;

the fix they came up with was to mod / move the ssh.conf file depending on what you want...

good enough for me...

update: tested for ssh and samba, I added a hash before the start on filesystem in both conf files and it works on both.

It seems after installing it, ssh server automatically starts itself at boot.  After following that link it looks like the best way to disable ssh server at startup is to edit the ssh configuration file like so:

```
sudo gedit etc/init/ssh.conf
``` 

Then find line "start on filesystem" and cancel it with a "#" so it looks like:  "#start on filesystem" 

Then save it and you're done.

Now the service won't start at boot but you can still start it using "sudo service ssh start"

Thanks to Florian Diesch and mikejonesey.

---

