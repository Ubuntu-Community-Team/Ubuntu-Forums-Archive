---
title: "Configuring x11vnc to run at the login screen"
date: 2010-09-05
forum: General Help
---

### Post by pspkiller91 on 2010-09-05
I'm trying to set up x11vncto run at the login screen. This is so that the computer can be powered up remotely using Wake-On-LAN and then controlled remotely. I'm following this tuorial: [https://help.ubuntu.com/community/VNC/Servers#x11vnc](https://help.ubuntu.com/community/VNC/Servers#x11vnc)  I'm having some trouble whit the section about adding to the GDM config files. 

The tutorial asks me to add

```
#to get remote vnc to not die after login
KillInitClients=false
```to /etc/gdm/gdm.conf-custombut this file doesn't exist on my installation (Ubuntu 10.04 Lucid.) Is the tutorial out of date and actually referring to /etc/gdm/custom.conf?

My next problem is what and where to add a line a script file to actually start x11vnc on bootup. Which script file do I need and where can I find it? I have a general idea of a command that would start x11vnc with the settings I need.

```


x11vnc -safer -usepw -display :0 -shared -forever


``` In my own testing where I've just typed it into a terminal once logged in it works fine. Would this this work once added to the startup script?

Thanks.

---

### Post by krunge on 2010-09-05
> **pspkiller91 said:**
> 
```
#to get remote vnc to not die after login
KillInitClients=false
```to /etc/gdm/gdm.conf-custombut this file doesn't exist on my installation (Ubuntu 10.04 Lucid.) Is the tutorial out of date and actually referring to /etc/gdm/custom.conf?

What does your ubuntu 10.04 gdm documentation say about the config file? 

You could also just try to make changes the possible files with some obvious change and see if the changes take place after you restart gdm.
> 
My next problem is what and where to add a line a script file to actually start x11vnc on bootup. Which script file do I need and where can I find it? I have a general idea of a command that would start x11vnc with the settings I need.

```


x11vnc -safer -usepw -display :0 -shared -forever


```
That looks pretty good.  But you don't need the '-display :0'.

You will need to put it in the background with '&' or '-bg'.

Also be sure you have run it with '-usepw' as the SAME USER as it will be running under GDM (e.g. root)

See the section marked 'Continuously' here:

[INDENT][http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager](http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager)[/INDENT]

for more info.

---

### Post by pspkiller91 on 2010-09-06
Thanks for your reply. I've dealt with the config file. Reading up on your link now to work out the rest of it.

---

