---
title: "Can I access a computer with no monitor?"
date: 2011-06-26
forum: General Help
---

### Post by Mr_VeRiTy on 2011-06-26
Hey, my monitor broke and I can't get a new one for about a week, and there are files I need on my PC. I was wondering if I could move those files to a memory stick by using only the tty1 CLI, or better yet, get access to the PC via my laptop. How would I do this?

Could I use remote desktop? (My previous experience with remote desktop didn't go well, but maybe since the PC and the laptop are on the same network it would be easier?)

---

### Post by Bachstelze on 2011-06-26
You can use SSH for that, but if you don't have the SSH sever installed on the target machine, you will have a hard time installing it without a monitor...

---

### Post by Mr_VeRiTy on 2011-06-26
> **Bachstelze said:**
> You can use SSH for that, but if you don't have the SSH sever installed on the target machine, you will have a hard time installing it without a monitor...
Could I not just boot it up, press ctrl+alt+F1, type my user name and password, then sudo apt-get install openssh-server? Will it even boot without a monitor?

---

### Post by RunForIt222 on 2011-06-26
It will boot without a monitor, and I think that will work, you might have to hit Y once its downloaded.

You'll have to have someone with more experience answer you for sure though.

---

### Post by Mr_VeRiTy on 2011-06-26
I think openssh is installed now (I used "eject" to test if the commands were going through.) But what do I do next?

---

### Post by tredegar on 2011-06-26
> But what do I do next?
See if you can connect to your desktop. I hope laptop is running linux.
On laptop
```
ssh verity@LAN.IP.OF.DESKTOP
```
Answer the prompts.
Can you login and connect?
**exit** to close the connection

If that worked then put this into nautilus:
```
sftp://verity@LAN.IP.OF.DESKTOP/home/verity/
```
Press return. Give  your password.
Now you can drag and drop files between PCs

---

### Post by Mr_VeRiTy on 2011-06-26
> **tredegar said:**
> See if you can connect to your desktop. I hope laptop is running linux.
On laptop
```
ssh verity@LAN.IP.OF.DESKTOP
```Answer the prompts.
Can you login and connect?
**exit** to close the connection

If that worked then put this into nautilus:
```
sftp://verity@LAN.IP.OF.DESKTOP/home/verity/
```Press return. Give  your password.
Now you can drag and drop files between PCs

The laptop is running linux. I don't think the PC is connected to my wireless router.. How do I connect from the terminal? Gnome usually connects me automatically when I log in so I thought logging in by gdm would connect me, but gdm doesn't seem to be starting without the monitor. (I tried "sudo service gdm restart", but it didn't work). This also means openssh wasn't installed.

---

### Post by hawthornso23 on 2011-06-26
Very clever if you can get this to work. 

Before we get too carried away with the clever tricks
have you checked if you can use your TV as a monitor?

Assuming not, here is another clever trick. You might be able to get your machine to talk to you and tell you what it is doing. If you have espeak installed then
```
pwd | espeak
```
will tell you what directory you are in
```
ls | espeak 
```
will tell you what files are in that directory. And so on.

---

### Post by Mr_VeRiTy on 2011-06-26
> **hawthornso23 said:**
> Very clever if you can get this to work. 

Before we get too carried away with the clever tricks
have you checked if you can use your TV as a monitor?

Assuming not, here is another clever trick. You might be able to get your machine to talk to you and tell you what it is doing. If you have espeak installed then
```
pwd | espeak
```will tell you what directory you are in
```
ls | espeak 
```will tell you what files are in that directory. And so on.

I don't have it installed, but I am definitely gonna remember that. And no, my tv is ooold.

---

### Post by tredegar on 2011-06-26
> The laptop is running linux.
Good
>  I don't think the PC is connected to my wireless router.
Easiest way to connect it is to connect it to your router with an ethernet cable (you might have to move it close to the router).
Boot, and you should be connected to your LAN / the internet.

Your router can tell you what LAN IP it has assigned to the desktop. You will need to know this. Check by logging into your router from the laptop, and getting it to list the connected devices.

If the desktop is not listed as connected:

Login to your desktop as yourself. Type
```
sudo dhclient eth0
```
Give your password
Press return
Wait a minute, then try
```
sudo apt-get install openssh-server espeak
```
Give your password
Press return
Watch your router's lights they should indicate something is happening.
Wait a few minutes
See if **espeak** was installed (I like that idea!)
```
echo hello | espeak
```
If it was, then the **openssh-server** should be there as well. Remember, your volume may be turned down too low for you to hear anything, so silence does not necessarily mean "fail".

Now try connecting from your laptop with **ssh**. You must do this _once_ before you can use **sftp** and **nautilus** to connect.

---

### Post by Mr_VeRiTy on 2011-06-26
> **tredegar said:**
> Good

Easiest way to connect it is to connect it to your router with an ethernet cable (you might have to move it close to the router).
Boot, and you should be connected to your LAN / the internet.

Your router can tell you what LAN IP it has assigned to the desktop. You will need to know this. Check by logging into your router from the laptop, and getting it to list the connected devices.

If the desktop is not listed as connected:

Login to your desktop as yourself. Type
```
sudo dhclient eth0
```Give your password
Press return
Wait a minute, then try
```
sudo apt-get install openssh-server espeak
```Give your password
Press return
Watch your router's lights they should indicate something is happening.
Wait a few minutes
See if **espeak** was installed (I like that idea!)
```
echo hello | espeak
```If it was, then the **openssh-server** should be there as well. Remember, your volume may be turned down too low for you to hear anything, so silence does not necessarily mean "fail".

Now try connecting from your laptop with **ssh**. You must do this _once_ before you can use **sftp** and **nautilus** to connect.

What's the not-easy way? (I lost my Ethernet cables aeons ago..) If it helps I can easily get my routers mac address or essid from my laptop.

---

### Post by tredegar on 2011-06-26
The not-so-easy way is to type a shedload of awkward commands into a terminal, and /or edit some files blindly.

Is your wireless encrypted? WPA WPA2 or WEP?
What is the name of the wireless interface on your desktop (eg **eth1** **wlan0 ath0** or something else?

Once you have that information, try [this link]("http://www.thelinuxdaily.com/2010/03/setup-wireless-connection-in-terminal/") and you will understand why I am recommending you find a cable. Go next door and beg for one. Offer beer.

---

### Post by Mr_VeRiTy on 2011-06-26
> **tredegar said:**
> The not-so-easy way is to type a shedload of awkward commands into a terminal, and /or edit some files blindly.

Is your wireless encrypted? WPA WPA2 or WEP?
What is the name of the wireless interface on your desktop (eg **eth1** **wlan0 ath0** or something else?

Once you have that information, try [this link]("http://www.thelinuxdaily.com/2010/03/setup-wireless-connection-in-terminal/") and you will understand why I am recommending you find a cable. Go next door and beg for one. Offer beer.

0_o Sounds difficult, I think I'm just gonna have to put a rush on my monitor delivery.. I'll have to set my wireless up so I can connect from the terminal once I have the monitor though, just in case.

My neighbours didn't have a cable...

Thanks for your help though :)

---

