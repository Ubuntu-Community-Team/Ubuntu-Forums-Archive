---
title: "Can't connect to Remote Desktop after reboot unless I open the preferences window"
date: 2010-02-08
forum: General Help
---

### Post by smozoma on 2010-02-08
After I restart my computer (running ubuntu 9.10), I can't connect to the Remote Desktop with VNC, unless i first go to System->Preferences->Remote Desktop and bring up the preferences window.

Is this the way it's supposed to work?  I want it to work without needing to bring up the preferences window.  This computer's going in the basement.. without a monitor...

I tried adding this command to Startup Applications, but it also doesn't work:
```
x11vnc -forever -usepw -httpdir /usr/share/vnc-java/ -httpport 5800
```(but it works fine if I manually enter it in a terminal.. which I don't want to do!)

Is there some way to fix this?

thanks

---

### Post by krunge on 2010-02-08
'System->Preferences->Remote Desktop' has nothing to do with x11vnc. It probably configures vino or krfb depending on your desktop.

So, if you are going to use x11vnc be sure to disable 'System->Preferences->Remote Desktop'.  Perhaps this is why your 'Startup Applications' line didn't work? 

Maybe add "-o /tmp/x11vnc.log" to your x11vnc line to collect messages in that file.  Post the contents of that log here if you cannot figure out the problem. 

To have x11vnc start at boot time showing the desktop login greeter (no one logged in yet) you can insert the command you posted into the file /etc/gdm/Init/Default (assuming GDM is your login greeter.) More info is here:
[INDENT][http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager](http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager)[/INDENT]

BTW, some bugs in GDM and Xorg in recent ubuntu versions can make this VNC login greeter process less smooth than it once was.

---

### Post by smozoma on 2010-02-08
Thanks for your reply; however, I haven't gotten it to work.

> **krunge said:**
> 'System->Preferences->Remote Desktop' has nothing to do with x11vnc. It probably configures vino or krfb depending on your desktop.

So, if you are going to use x11vnc be sure to disable 'System->Preferences->Remote Desktop'.  Perhaps this is why your 'Startup Applications' line didn't work? 

I tried them separately, and neither worked on startup on its own (I had ubuntu set to automatically log in, btw).  I have to either open the preferences window for one (makes no sense), or run a command manually for the other, in order to be able to connect from my windows machine with VNC viewer.

My preferred method of getting this working would be to use Remote Desktop (just because it's built in), but I tried x11vnc when Remote Desktop didn't work.  The website interface of x11vnc is pretty cool, though...

Does anyone know why I need to open the Remote Desktop preference window in order to be able to connect?  It's just a preferences window, that shouldn't be necessary.


> **krunge said:**
> Maybe add "-o /tmp/x11vnc.log" to your x11vnc line to collect messages in that file.  Post the contents of that log here if you cannot figure out the problem. 


No file is created after rebooting.  Maybe I need to set some permissions of some sort?  It seems like the command isn't being run (or run successfully), even though it's in "Startup Applications" and has a checkmark next to it.
Come to think of it, the session saving doesn't work either (restoring running programs after logging out and back in) -- i wonder if the issues are related.


> **krunge said:**
>  To have x11vnc start at boot time showing the desktop login greeter (no one logged in yet) you can insert the command you posted into the file /etc/gdm/Init/Default (assuming GDM is your login greeter.) More info is here:[INDENT][http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager](http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager)[/INDENT]BTW, some bugs in GDM and Xorg in recent ubuntu versions can make this VNC login greeter process less smooth than it once was.

I added the following command to /etc/gdm/Init/Default 
```
x11vnc -forever -usepw -httpdir /usr/share/vnc-java/ -httpport 5800 -o /tmp/vnc.log -reopen
```and also added  KillInitClients=false in /etc/gdm/custom.conf (there was no gdm.conf file).
I disabled auto-login since this is for vnc during the login screen.
A log file is created containing:
```
8/02/2010 16:09:03 passing arg to libvncserver: -httpport
08/02/2010 16:09:03 passing arg to libvncserver: 5800
08/02/2010 16:09:03 passing arg to libvncserver: -reopen
Enter VNC password: stty: standard input: Inappropriate ioctl for device
stty: standard input: Inappropriate ioctl for device
x11vnc -usepw: could not find a password to use.
```I have already created a password when I was logged in, using "x11vnc -storepasswd", but that put it in my home directory, so it doesn't work during the login before I've logged in.  
I tried doing 'su' to try to recreate the password as root, but I don't seem to know the password (I don't recall setting one up when installing ubuntu, other than my user account password..)
The instructions for -usepw don't say you can specify a password file to use.  I tried making one in /etc/bin/.vnc/passwd, but it didn't pick it up.  I tried adding the location of one of the password files after it, but it also didn't work.

Is there some location I can put a password file where it'll pick it up?

Thanks

---

### Post by smozoma on 2010-02-08
adding to the above, I enabled the Ubuntu root account and created a vnc password in /root/.vnc/passwd.  However, I still get the same error, 'could not find a password to use' in the log file

---

### Post by smozoma on 2010-02-08
I also tried adding "vino-preferences" (which is the command to launch the Remote Desktop preferences window) to the Startup Applications.  It doesn't appear on startup.  

Is my Ubuntu 'broken'?  Does this work for anyone else?

What good is a Startup Applications launcher.. if it doesn't launch your startup applications...

---

### Post by smozoma on 2010-02-09
I got vino-preferences to load on startup using a ~/.xinitrc file, as explained at [https://wiki.ubuntu.com/CustomXSession](https://wiki.ubuntu.com/CustomXSession)

---

### Post by krunge on 2010-02-09
> 
No file is created after rebooting.  Maybe I need to set some permissions of some sort?  It seems like the command isn't being run (or run successfully), even though it's in "Startup Applications" and has a checkmark next to it.
Yes, I think that is your problem. Somehow you haven't configured 'Startup Applications' properly.  Sorry but I don't use this mechanism.

```
8/02/2010 16:09:03 passing arg to libvncserver: -httpport
08/02/2010 16:09:03 passing arg to libvncserver: 5800
08/02/2010 16:09:03 passing arg to libvncserver: -reopen
Enter VNC password: stty: standard input: Inappropriate ioctl for device
stty: standard input: Inappropriate ioctl for device
x11vnc -usepw: could not find a password to use.
```
As you point out, x11vnc is running as root from /etc/gdm/Default/Init, so root needs to be the one to run -storepasswd (or you can skip -usepw and point -rfbauth directly to your user's vnc passwd file.)

From your later posts, it seems like you got it working for vino via ~/.xclients. That method should work for x11vnc too I believe. So I think you are able to run either one now.

---

### Post by EminNew on 2010-02-17
I had the exact same problem as you did.

The problem was that I had Remote Desktop unchecked in the Startup Application list.

So go to System->Preferences->Startup Applications and make sure Remote Desktop is enabled.

---

### Post by smozoma on 2010-02-17
> **EminNew said:**
> I had the exact same problem as you did.

The problem was that I had Remote Desktop unchecked in the Startup Application list.

So go to System->Preferences->Startup Applications and make sure Remote Desktop is enabled.

It was already checked.

---

### Post by eddywebs on 2011-09-25
Hello there , I just got started using ubuntu as my home server lately, quite satisfied with it so far.
However I am having exactly the same problem , my remote desktop wont be enabled after reboot unless I launch the remote desktop configuration utility from  System >> Administration.

I also checked the below whether the Remote desktop is enabled as startup application and it already is.
One thing I noticed the Statup command for the Remote Desktop application had been set to
> /usr/lib/vino/vino-server --sm-disable


So what exactly are we missing here ? 
Should the last parameter in the startup command be --sm-enable or is it a bug maybe 
Using 10.04 LTC distribution.


> **EminNew said:**
> I had the exact same problem as you did.

The problem was that I had Remote Desktop unchecked in the Startup Application list.

So go to System->Preferences->Startup Applications and make sure Remote Desktop is enabled.

---

### Post by smozoma on 2011-09-25
> **eddywebs said:**
> I am having exactly the same problem , my remote desktop wont be enabled after reboot unless I launch the remote desktop configuration utility from  System >> Administration.



The workaround I've been using is from this page: [https://wiki.ubuntu.com/CustomXSession](https://wiki.ubuntu.com/CustomXSession)

Create the file ~/.xinitrc and put the following in it:

```
#!/usr/bin/env bash

vino-preferences &

exec gnome-session

```Then make the file executable, either by doing "chmod +x ~/.xinitrc" or right-clicking it, going to Properties, Permissions, and checking "allow executing file as program".

The preferences window will come up when you start your computer, and then VNC will work.  You can close the preferences window and it'll continue working.


> **eddywebs said:**
> 
One thing I noticed the Statup command for the Remote Desktop application had been set to
     Quote:
                                                 /usr/lib/vino/vino-server --sm-disable                                 

So what exactly are we missing here ? 
Should the last parameter in the startup command be --sm-enable or is it a bug maybe 


--sm-diable:  Disable connection to session manager

So maybe you are on to something there.. what happens if you remove that flag?

---

### Post by eddywebs on 2011-09-26
Hi @smozoma really appreciate some guiding light on getting the remote desktop running , 
I created the .xinitrc file with the code mentioned and also went ahead and linked .xsession to .xinitrc 
however after restart still wont launch the the xino, I also went ahead and tried changed the parameters of the remote desktop command at startup to sm-enable but still no luck :(


> **smozoma said:**
> The workaround I've been using is from this page: [https://wiki.ubuntu.com/CustomXSession](https://wiki.ubuntu.com/CustomXSession)

Create the file ~/.xinitrc and put the following in it:

```
#!/usr/bin/env bash

vino-preferences &

exec gnome-session

```Then make the file executable, either by doing "chmod +x ~/.xinitrc" or right-clicking it, going to Properties, Permissions, and checking "allow executing file as program".

The preferences window will come up when you start your computer, and then VNC will work.  You can close the preferences window and it'll continue working.




--sm-diable:  Disable connection to session manager

So maybe you are on to something there.. what happens if you remove that flag?

---

