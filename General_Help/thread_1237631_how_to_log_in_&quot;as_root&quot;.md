---
title: "how to log in &quot;as root&quot;?"
date: 2009-08-11
forum: General Help
---

### Post by tinh_si on 2009-08-11
i'm an absolute noob at using ubuntu.  I followed some tips on how to make Linux looks like mac and some of the steps required me to perform the step "as root" ... can someone tell me what it means and how to do it?  i installed ubuntu on a vostro 1500 with vista installed first

TY in advance

---

### Post by oomar on 2009-08-11
its really simple. when you are in command line (terminal), you simply put the word "sudo" infront then a space and your commands. it will ask for your password which you then type in. dont worry if you dont see any asteriks or anything. its supposed to be that way. 

ex. you want to use nautilus (the file explorer) as root.

in CLI you would type this for a NON-root window.
```
nautilus
```

for root nautilus you would use
```
sudo nautilus
```

hope that helps

---

### Post by slakkie on 2009-08-11
Use the sudo command to execute a command as root.

eg

sudo aptitude safe-upgrade

or

sudo aptitude install apache2
sudo aptitude purge apache2

see also [https://help.ubuntu.com/6.06/kubuntu/desktopguide/C/root-and-sudo.html](https://help.ubuntu.com/6.06/kubuntu/desktopguide/C/root-and-sudo.html)

---

### Post by doas777 on 2009-08-11
oomar provided a good overview of 'sudo', the command ubuntu uses to elevate a user to an admin (a root privledged account).

you can learn more here:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

I would only caution you to use 'gksu' rather than sudo, when working with graphical apps like nautilus. sudo is for commandline, and gksu is for the graphical desktop; 
so to open a file window as root, jsut run
```
gksu nautilus
```

be very careful with that window. it will let you make destructive changes so do what you need to, and close it.

good luck, and welcome!

---

### Post by oomar on 2009-08-11
yea id listen to doas lol ive never even heard of gksu.

---

### Post by doas777 on 2009-08-11
> **tinh_si said:**
> i'm an absolute noob at using ubuntu.  I followed some tips on how to make Linux looks like mac and some of the steps required me to perform the step "as root" ... can someone tell me what it means and how to do it?  i installed ubuntu on a vostro 1500 with vista installed first

TY in advance
if you provide a link to the tutorial we may be able to give you more specific advice.
have fun,
franklin

---

### Post by Iowan on 2009-08-11
Another link that might be helpful:
[http://www.psychocats.net/ubuntu/graphicalsudo]("http://www.psychocats.net/ubuntu/graphicalsudo")

---

### Post by aysiu on 2009-08-11
I don't see why you should need root privileges to make Linux look like Mac.

Most themes can install locally. Can you link us to this tutorial? Maybe we can tell you the proper way to do it instead.

If you really do need a root prompt, just paste this command in [url=http://www.psychocats.net/ubuntu/terminal]the terminal[/code]: ```
sudo -i
```

If you need a root file browser, paste this command in ```
gksudo nautilus
```

---

### Post by tinh_si on 2009-08-11
> **doas777 said:**
> if you provide a link to the tutorial we may be able to give you more specific advice.
have fun,
franklin


this is the link to the tutorial

[http://www.howtoforge.com/mac4lin_make_linux_look_like_a_mac_p2](http://www.howtoforge.com/mac4lin_make_linux_look_like_a_mac_p2)

the step that i was talking about is 6 and 7 

and thank you all for your replies.  rest assured that your replies are greatly appreciated

---

### Post by aysiu on 2009-08-11
You're copying a few files to system folders.

```
gksudo nautilus
``` will be fine for this. If you want to create a launcher for it, follow these instructions:
[http://www.psychocats.net/ubuntucat/rootlauncher/](http://www.psychocats.net/ubuntucat/rootlauncher/)

---

