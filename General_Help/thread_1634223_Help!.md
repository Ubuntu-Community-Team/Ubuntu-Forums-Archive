---
title: "Help!"
date: 2010-11-30
forum: General Help
---

### Post by Hybridchina on 2010-11-30
Hi, I'm new in Linux and I got into a problem:

I have a Dell 500 laptop and it doesnt have WiFi and earlier when I used Windows, I bought a Belkin Enchanced Wireless USB Adapter to enable to connect to my home WiFi station and it worked perfectly.

And then I instaled Ubuntu and when tried to instal Belkin I saw that it is Windows only!

Can someone help me to make it work on Ubuntu, cause I really like it but I can't "live" without WiFi.

I rly rly new at this so if someone can be as detailed as possible i would be so thankfull to him!
:D

---

### Post by Hybridchina on 2010-11-30
Hi, I'm new in Linux and I got into a problem:

I have a Dell 500 laptop and it doesnt have WiFi and earlier when I used  Windows, I bought a Belkin Enchanced Wireless USB Adapter to enable to  connect to my home WiFi station and it worked perfectly.

And then I instaled Ubuntu and when tried to instal Belkin I saw that it is Windows only!

Can someone help me to make it work on Ubuntu, cause I really like it but I can't "live" without WiFi.

I rly rly new at this so if someone can be as detailed as possible i would be so thankfull to him!
:D

---

### Post by Hybridchina on 2010-11-30
Hi, I'm new in Linux and I got into a problem:

I have a Dell 500 laptop and it doesnt have WiFi and earlier when I used  Windows, I bought a Belkin Enchanced Wireless USB Adapter to enable to  connect to my home WiFi station and it worked perfectly.

And then I instaled Ubuntu and when tried to instal Belkin I saw that it is Windows only!

Can someone help me to make it work on Ubuntu, cause I really like it but I can't "live" without WiFi.

I rly rly new at this so if someone can be as detailed as possible i would be so thankfull to him!
:D

---

### Post by Hippytaff on 2010-11-30
It's probably best to avoid multiple posts, it can get rather confusing.
 
You might be able to use the windows xp driver with ndiswrapper to get the wirless adapter working. :-)
 
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by 2011basket on 2010-11-30
no ideas

---

### Post by philinux on 2010-11-30
> **Hybridchina said:**
> Hi, I'm new in Linux and I got into a problem:

I have a Dell 500 laptop and it doesnt have WiFi and earlier when I used  Windows, I bought a Belkin Enchanced Wireless USB Adapter to enable to  connect to my home WiFi station and it worked perfectly.

And then I instaled Ubuntu and when tried to instal Belkin I saw that it is Windows only!

Can someone help me to make it work on Ubuntu, cause I really like it but I can't "live" without WiFi.

I rly rly new at this so if someone can be as detailed as possible i would be so thankfull to him!
:D

Try this.
Connect the machine wired to the router directly. Plug in the Adapter.

Then look in System>admin>additional drivers. See if anything is offered to be installed.

---

### Post by nickleboyblue on 2010-11-30
We need a little more information on what you've got to get it working, so let's get started.

step 1: plug your computer into your network with an ethernet cable.  run:

```
sudo apt-get update && sudo apt-get upgrade
```

That will update your repositories and upgrade your system to the latest developments in your distribution.

step 2: Plug your usb wifi adapter into your computer, run this command, and post the results back to this thread so that we can see it:

```
lsusb
```

step 3:  Look for something similar to "RT2870" in the ouput to lsusb.  That should tell you the chipset for your usb adapter.  Before anything else, run a Google search using keywords like "ubuntu usb wifi adapter (insert chipset here)."  If some other Ubuntu user has already had your problem (chances are, they have!) you'll likely find the solution by doing that.

(Just FYI, if your chipset really IS the RT2870 (or the RT3070), see this thread: [http://ubuntuforums.org/showthread.php?t=1342593](http://ubuntuforums.org/showthread.php?t=1342593) That should get you running.)

---

### Post by nickleboyblue on 2010-11-30
Oh, and because you are new, here's how to run those commands I gave you:

First, open a terminal.  There are several built-in terminals in Ubuntu, but the one i use most can be found in the menus.  Go to Applications->Accessories->Terminal, and a window should open up with an area for you to enter text.  Enter the commands I gave you exactly as written, because a single wrong letter will leave your computer very confused about what you want it to do.  Also, don't exit out of the terminal until the commands have been fully carried out, because doing so will cause the processes running those commands to fail half way through, which could cause some major problems depending on the command you ran.

The other way to open terminals is to hit ctrl+alt+F1-F6.  That key combination gives you a full-screen terminal and it's hard to know automatically how to get back to graphics.  To get back, just hit alt+F7 and you should see your graphical desktop again.

---

### Post by TBABill on 2010-11-30
Need to know the chipset the device has before knowing for sure it can't work in Linux. Can you type ```
lsusb
``` into a terminal and paste the output here?

---

### Post by Hybridchina on 2010-11-30
lsusb  
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 001 Device 003: ID 050d:935b Belkin Components  
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 hybrid@hybrid-HP-500-Notebook-PC-RQ257AA-AKN:~$ 



This is what I got.
Does it help?

---

### Post by Hybridchina on 2010-11-30
[http://ubuntuforums.org/showthread.php?t=1634225](http://ubuntuforums.org/showthread.php?t=1634225)

Sry for multi.

---

### Post by Hippytaff on 2010-11-30
you've got a belkin wireless usb - have a read here, if you get stuck post back :-)

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin%20F5D8053](https://help.ubuntu.com/community/WifiDocs/Device/Belkin%20F5D8053)

---

### Post by Iowan on 2010-12-01
> **Hybridchina said:**
> [http://ubuntuforums.org/showthread.php?t=1634225](http://ubuntuforums.org/showthread.php?t=1634225)

Sry for multi.
Threads merged.

---

### Post by Hybridchina on 2010-12-05
I did it!
:D
Followed [Hippytaff]("http://ubuntuforums.org/member.php?u=1133249")'s link and tan ta na na!
:D
Tnx soooo much!

---

### Post by Hippytaff on 2010-12-05
Excellent - Glad it's sorted - well done.

Remember to mark your thread as solved in the thread tools at the top of the page so others with the same issue can see how you solved it :-)

---

