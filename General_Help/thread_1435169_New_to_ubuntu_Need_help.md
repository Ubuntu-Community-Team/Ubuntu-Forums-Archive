---
title: "New to ubuntu: Need help"
date: 2010-03-21
forum: General Help
---

### Post by tripower on 2010-03-21
I made the plunge and I realize that I may not be able to do everything but I want to give it a try....

I would like to run the following programs in Ubuntu:

1. iTunes
2. Any tax software
3. OBDII software
4. eBay Turbo Lister
5. Are there generic scanner drivers for my Visioneer 8700 scanner?
6. Is there a way to store my FireFox favorites online?
7. I saved my profile data for both Thunderbird and Firefox from Windows before I migrated over to Ubuntu, how do I re migrate that data over to Ubuntu.
8. What VPN software is available? Is it compatible with Nortel VPN?
9. I need software for some sort of remote desktop between Ubuntu and windows specifically, what is available?
10. I still can't connect to my Windows 7 box on my home network has this issue been addressed?

---

### Post by 3rdalbum on 2010-03-21
I can only answer some of your questions.

1. Apparently, the latest versions of iTunes do not work on Wine. You could use a virtual machine if you really want iTunes, or choose from several hundred music players/music managers on Ubuntu.

6. Yes, there is a way to store Firefox favourites online; it involves a Firefox extension. I have heard about this. What I did, personally, is switch to Opera - the bookmarks sync is available out-of-the-box in Opera, and it even syncs to your mobile phone running Opera Mini.

8. I don't think you need VPN software; Ubuntu's Network Manager applet should be able to handle your VPN. Try it and see.

9. For remote desktop, what you want is some sort of VNC server and client. Ubuntu has a server and client preinstalled - System > Preferences > Remote Desktop for the server, Applications > Internet > Remote Desktop Client for the client.

There are other options, such as TightVNC.

VNC will work across platforms.

If you just want to be able to view a Windows machine's built-in remote desktop functionality, this uses RDP, and can be viewed with Ubuntu's preinstalled Terminal Server Client software.

10. I believe Samba has been updated to allow for Windows 7's changes to the protocol, so yes. Obviously, you'll need to be running a recent version of Ubuntu to get the later version of Samba.

---

### Post by sxmaxchine on 2010-03-21
itunes isnt made for ubuntu but you can get it to work using [wine]("http://winehq.org/")but i recomend installing it using [playonlinux]("http://www.playonlinux.com/")

for your VPN problem check [This]("https://wiki.ubuntu.com/VPN")

not to sure how to answer your other questions but i hope this helps and you have fun with ubuntu.

---

### Post by sxmaxchine on 2010-03-21
and for 6. i use Opera instead of firefox

---

### Post by linden940 on 2010-03-21
any tax software will work...i did my taxs on tax-act online

---

### Post by tripower on 2010-03-21
> **linden940 said:**
> any tax software will work...i did my taxs on tax-act online

I know I could do it online but for taxes I would prefer to do that locally.

---

### Post by mikesir87 on 2010-03-21
For saving bookmarks (if you want to keep Firefox), I recommend using the XMarks extension.  There is also one for Chrome, so you can have your bookmarks across all browsers, and multiple computers.

---

### Post by tripower on 2010-03-22
> **3rdalbum said:**
> 
1. Apparently, the latest versions of iTunes do not work on Wine. You could use a virtual machine if you really want iTunes, or choose from several hundred music players/music managers on Ubuntu.


This isn't a matter of just needing an MP3 player to play music I need iTunes to send updates to my iPhone...that's kinda important.

> **3rdalbum said:**
> 
6. Yes, there is a way to store Firefox favourites online; it involves a Firefox extension. I have heard about this. What I did, personally, is switch to Opera - the bookmarks sync is available out-of-the-box in Opera, and it even syncs to your mobile phone running Opera Mini.


I'll take a look.


> **3rdalbum said:**
> 
9. For remote desktop, what you want is some sort of VNC server and client. Ubuntu has a server and client preinstalled - System > Preferences > Remote Desktop for the server, Applications > Internet > Remote Desktop Client for the client.
There are other options, such as TightVNC.
VNC will work across platforms.

If you just want to be able to view a Windows machine's built-in remote desktop functionality, this uses RDP, and can be viewed with Ubuntu's preinstalled Terminal Server Client software.


I need a VNC client and server. I need to have something to run on both Ubuntu AND Windows.


> **3rdalbum said:**
> 
10. I believe Samba has been updated to allow for Windows 7's changes to the protocol, so yes. Obviously, you'll need to be running a recent version of Ubuntu to get the later version of Samba.

I am running Ubuntu 9.10 and I still cannot connect to Win 7. What version of Samba do I need to connect to Win 7 and where do I get it?

---

### Post by tripower on 2010-04-02
bump.

---

### Post by eriktheblu on 2010-04-02
> **tripower said:**
> 
I am running Ubuntu 9.10 and I still cannot connect to Win 7. What version of Samba do I need to connect to Win 7 and where do I get it?
To connect to a Windows share, you should just need the smbfs plugin. You can get that in the repositories through synaptic or in the terminal
```
sudo apt-get install smbfs
```

---

### Post by fisheater on 2010-04-02
re: 8. VPN

One very tidy option is NxNomachine. It is easy to set up, which is key for me - I am still learning how to do more advanced tasks in ubuntuu.

The free version allows 2 accounts. Encryption out of the box. Able to use a portable windows version on a USB, so files very accessible. Can t/f files. 

Good luck.

FE

---

### Post by tripower on 2010-04-07
> **eriktheblu said:**
> To connect to a Windows share, you should just need the smbfs plugin. You can get that in the repositories through synaptic or in the terminal
```
sudo apt-get install smbfs
```


THANKS! That worked!

Now can someone assist me in getting some sort of remote desktop client server working between Win 7 Home and Ubunty 9? Specifically what software do I need to run. There is no built in Remote Desktop Server with Win 7 Home.

---

