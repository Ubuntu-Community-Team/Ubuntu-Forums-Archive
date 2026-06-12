---
title: "Internet speed slowed down"
date: 2010-05-21
forum: General Help
---

### Post by shaquille on 2010-05-21
I am using ubuntu 10.04. I install it inside windows xp. I use broadband Internet through wireless LAN. the problem is my internet speed slowed down. In windows xp the speed is fine, but in ubuntu it is working very slowly. I am using swiftfox web browser. 

What should I do now?

---

### Post by batharoy on 2010-05-21
> **frank002 said:**
> I had the same problem and then I remembered IPV6.
Open Firefox and type about:config. Scroll down to network.dns.disable IPV6. If it says 
FALSE, change it to TRUE. It worked for me.

Should work in Swiftfox also.

---

### Post by shaquille on 2010-05-21
> **batharoy said:**
> Should work in Swiftfox also.

it was already set "true"

the problem doesn't solved

---

### Post by sammyboy405 on 2010-05-21
Ive been fighting this problem for a while now.   I have all of IPv6 turned off even did the deal where you tell grub to disable it too.  Im using firefox..  Ive tried using even chrome and the Internet is just slow.. 

For example,  In Windows or my Mac, I goto the same website and down the same 50meg file it downloads with in a couple of mins.  But Inside Ubuntu (10.04 or 9.10) it takes atleast 5 to 10 mins.

I thought Ok Maybe its my computer.  So I got my work to allow me to install Ubuntu on my Work PC.  and Holy cow the Problem followed. 

Funny thing is when you first install Ubuntu and it worked great speed wise on the internet for a couple of days and then.. its like magic it slows down to a crawl.  

And it dont matter Browser either, I Switch back and forth from Chrome to Firefox and the speed is the same.   I hook my Netbook, Macbook or windows computer up and there's the speed.

Where else in Ubuntu can I look for issues that would cause this? Fresh installs work for a few days at what I would consider Optimal surfing speeds.  And like someone waving a magic wand Poof! Surfing and downloading is back to a crawl.

Ive read MANY MANY posts on here.  About the Internet being slow. And everyone keeps coming back and saying the same thing.. to disable IPv6  .  Trust me that has been done in more ways than 1. There has to be an issue here for the amount of posts Ive seen with people complaining about this issue.  I haven't seen many on 10.04 but in Previous Releases 9.10 / 9.04 I can tell ya if you search the boards the threads are in the thousands. 

Route Tables seem to be fine.  Nothing Fancy No Customizations.
UFW / Any other Firewalls are turned off.
Link speeds are correct.
Network card and Wifi both set to DHCP. (Ive even tried turning Wired off while using Wireless and Vice Versa)
IPv6 is Disabled though out the Entire box.
This happens on 3 different Machines (all different HW) That I have 10.04 Installed on.
Internet is Confirmed to work correctly using a Box that isnt running Ubuntu.
On an Idea I loaded a box using Mint / Fedora and the Problem dont exist..

Its not unusable by no means.  But I just know it can go faster. What all else can be checked out?

---

### Post by calinut1 on 2010-05-21
I had the same problem in Firefox. The fix is easy, you just need to set some DNS adresses.

Do this:

1)Copy these DNS adresses: 

```
208.67.222.222; 208.67.220.220
```

2)Go to your internet icon in the tray(up there on the right), right click it and select Edit Connections.

3) You said you had Wireless so go on the Wireless tab and you should see something like "auto eth0" or anything. Select it and click Edit 

4) Go on the IPv4 tab and change the method to: Automatic(DHCP) adresses only.

5) Paste the DNS adresses you copied before in the DNS servers section. 

6) Now click apply and then left click o your internet icon and click on the Wireless LAN name or whatever is written there, just reconnect to your internet.

DONE!

Hope I helped you!

---

