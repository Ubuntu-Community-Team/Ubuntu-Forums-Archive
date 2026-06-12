---
title: "Ubuntu crashed, I have no idea why. :( PLEASE HELP"
date: 2009-07-02
forum: General Help
---

### Post by sXeChris on 2009-07-02
Okay, this happened yesterday at 9 P.M. roughly, I was reading my Ubuntu user guide and was following the instructions on how to do things. I had like 4 programs running and they were simple things like having the mouse options open (the ones found in system>preferences>mouse) or the hardware drivers. But, when I opened the screensaver window, my screen started to freeze and stop, until it came to a point that it just froze completely, it was like loading the screensavers was too much for it or something. So, being originally a windows user and knowing as much as someone on page 47/140 on their usermanual of Ubuntu, I pressed Ctrl+Alt+Delete and a similar looking window to the Windows' response to Ctrl+Alt+Delete came up. There was the option to shut down and so I did, thinking this would resolve everything. Today in the morning, I turned on my computer and when Ubuntu finished loading, nothing happened, the only thing I saw were lines of pixels thrown across the screen. So then I booted again and I chose the recovery version of Ubuntu. I chose xfix but it didn't help at all and I tried choosing any other command there but none of them helped. I am currently on vacation and my Ubuntu CD is back home, 3,000 miles away, please, if there's a way I can recover it instead of having to wait to get back home that would be great. I am so interested in Ubuntu and all I want to do is learn that manual and all I can about Ubuntu! I will eagerly be awaiting anyone's response. PLEASE HELP!!

My details:
Dual Booting w/ Windows Vista
Ubuntu 9.04, x64 (I hear that x32 is better because of compatability issues, my system works heavenly on the x64 but THERE ARE somethings that I can't install and since I'm a complete noob I do think it might be better)

I'm currently on my Windows Vista partition

---

### Post by TeoBigusGeekus on 2009-07-02
Boot into command line from recovery mode and type
sudo dpkg-reconfigure xserver-xorg
Post us the result.
(Word of advice: never mess with screensavers in Ubuntu, leave them be - I've learnt that the hard way)

---

### Post by rxbristol on 2009-07-02
I experienced the same thing.  I found out that Ubuntu did not get enough space on the new partion.  More than likely, your only options will be to run Ubuntu from the CD or completely format your hard drive for Ubuntu.  Also, you could reload Windows and set up the partions manually giving enough space for both operating systems.
 
Rex

---

### Post by sXeChris on 2009-07-02
I'm sorry if I'm a complete idiot, but how do I get to the command line? Is it the option to get to 'root'? If it is, I went to root and I typed the command, I went through some weird process that asked me a lot about my keyboard type, I answered everything and booted regularly but there was no change.

Sorry for my ignorantness, please reply.

---

### Post by TeoBigusGeekus on 2009-07-02
Ok now...
Boot up and when you get to grub choose the recovery mode.
You will be directed on a screen with a lot of options, one of them being the reconfiguration of your graphics settings. Try this and post us back.

---

### Post by sXeChris on 2009-07-02
I didn't have an option to 'reconfigure' the graphics settings, but I had to one to 'repair' the graphics settings, I chose that one and I got to the command line but half-way into typing, warns me of data loss and closes the screen. The thing to fix the graphics settings was called 'xfix'.

---

