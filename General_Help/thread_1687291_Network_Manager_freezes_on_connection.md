---
title: "Network Manager freezes on connection"
date: 2011-02-13
forum: General Help
---

### Post by Aoude on 2011-02-13
Hi, I'm pretty new to Ubuntu and have been experiencing some problems with my internet connection. When I disable nm-applet from startup I do not have the problem, however then I cannot select a wireless connection. I have checked and Ethernet connections work and so does have nm-applet open (without connecting to my wifi network). Help would be appreciated [-o< , Thanks, Patrick.

---

### Post by gerowen on 2011-02-13
So you are unable to use your wireless?  Check to see if it requires a proprietary driver to work.  Plug in an ethernet cable so you have internet access, click "System" -> "Administration" -> "Additional Drivers" and activate any of them that you see in there.

---

### Post by Aoude on 2011-02-13
Thanks, I'll reboot, try that, and get back to you :)

---

### Post by Aoude on 2011-02-13
I tried that and the only thing I got was a driver for my graphics card (fresh install):(

I don't know what to do :confused:  It was working at my friend's house (1st time using it) then it stopped working at my house, I even tried a fresh install to  try and solve it.

---

### Post by gerowen on 2011-02-13
So when you right click on the network applet "Enable Wireless" is checked?

---

### Post by Aoude on 2011-02-13
Yes, I am currently connected to my neighbor's wifi successfully. Could the problem be with the configuration on my router? His connection is unprotected and mine is secured (WPA2 I believe).

And on an unrelated note, every time I open firefox it says
[INDENT]"Could not initialize the application's security component. The most likely cause is problems with files in your application's profile directory. Please check that this directory has no read/write restrictions and your hard disk is not full or close to full. It is recommended that you exit the application and fix the problem. If you continue to use this session, you might see incorrect application behaviour when accessing security features."

[/INDENT]I know this isn't the place for it, and I will be installing Chromium anyways, but just wondering if this is a common  error.

---

### Post by gerowen on 2011-02-13
Run the following commands to make sure all files in your home directory have the correct permissions.  Replace "username" with your username:

```

sudo chown -R username /home/username
sudo chgrp -R username /home/username
sudo chmod -R 770 /home/username

```

That error message mentioned something to do with permissions.

---

### Post by Aoude on 2011-02-13
This is what I got when I tried the code:
[INDENT]patrick@patrick-VPCEB19FX:~$ sudo chown -R patrick /home/patrick
[sudo] password for patrick: 
chown: cannot access `/home/patrick/.gvfs': Permission denied
patrick@patrick-VPCEB19FX:~$ sudo chgrp -R patrick /home/patrick
chgrp: cannot access `/home/patrick/.gvfs': Permission denied
patrick@patrick-VPCEB19FX:~$ sudo chmod -R 770 /home/patrick
chmod: cannot access `/home/patrick/.gvfs': Permission denied
[/INDENT]
How do I fix these permissions?

And for the wireless what settings should I adjust to be able to connect? I want to stay protected so should I switch to WEP?

---

### Post by gerowen on 2011-02-13
You'll get those error messages about .gvfs, that's a folder used for mounting samba shares and such, so those errors are normal and no biggie.

What I would do is start at the ground and work your way up.  Turn off encryption altogether, connect, make sure it works.  I would stick with at least WPA if you can.  WEP passwords can be cracked in a matter of minutes nowadays.  Let me know how it goes, :-)

---

### Post by Aoude on 2011-02-13
So why would Firefox be giving that error?

And I'll make those changes and see how it goes, thanks for the timely responses :D.

---

### Post by Aoude on 2011-02-13
[double post]

---

### Post by Aoude on 2011-02-13
It didn't work after turning off WPA :confused:, still freezing

It work on Windows 7 and my Ipod Touch.
I'm also pretty sure it worked on the Live CD when I was testing Ubuntu :(

---

### Post by Aoude on 2011-02-13
never mind I just restored Linux again and it worked.

---

### Post by gerowen on 2011-02-13
It was strange, but I'm glad you got the issue resolved.  :-)

---

