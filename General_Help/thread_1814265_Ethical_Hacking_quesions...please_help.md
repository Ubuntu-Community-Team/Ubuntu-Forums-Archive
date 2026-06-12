---
title: "Ethical Hacking quesions...please help"
date: 2011-07-29
forum: General Help
---

### Post by schwabdale on 2011-07-29
Question 1
Is it harder for an intruder to hack into a Ubuntu OS, or a Windows OS? Why?

Question 2  
In Ubuntu, you can click on your wireless icon and create a new wireless network. I think this will broadcast a wireless network name for people to logon to, then they are using your computer as a repeater. Can a hacker make this the same name as your wireless router...so when you logon, they can get your password? If so, how do they get your password...a software program installed on Ubuntu?

Question 3
How would you know if your logging onto a Laptop (setup as a wireless router) instead of your real physical router? Are there tools to prevent this?

---

### Post by hakermania on 2011-07-29
1) AFAIK on the one hand it is harder because there aren't so many exploits out there yet and the possibilities are very low, so generally it is harder to have a working exploit especially with the latest updates and releases. Also, ubuntu have a super user protection so the hacker could not do actual damage to the PC or to major files, only to user files and folders. This rescues the PC itself (the hacker cannot format it etc but it can steal your firefox passwords and anything accessible wihout password)
2) Search for airbase-ng ;)
3) First of all, if somebody had the idea of making his fake access point's name similar to your router you'd see 2 entries of the same name so you'd understand that something suspicious takes place! What is more, you can see your modems MAC address and compare it with others (this is a secure way but the hacker can change his mac with macchanger as well and have the same Name and Mac with your modem)...

PS as for (3) I don't know a good way to protect yourself, of course be aware of duplicate entries and keep in mind i.e. the last 2 digits of your modem's MAC address!

---

### Post by schwabdale on 2011-07-29
1. If they hacked your computer, they prob got your SU Password anyway right? 
    A. I thought there was a really good built in firewall in Ubuntu? Unlike Windows weak
        firewall...is this correct?

2. This seems to be command line, are there any graphical tools? How about Backtrack?

3. Why are the last 2 digits important?

---

### Post by Matt__ on 2011-07-29
ok so right clicking your network icon and creating a new network dosnt make your pc/laptop into a router(unless you specify it as shared connection in IPv4).

define "ethical hacking" your idea of ethics may vary from another persons.
what are you trying to do?

secondly what you are trying with airbase is password cracking wireless  networks..so as soon as that isnt your own or a clients network......

---

### Post by community on 2011-07-29
I think a hacker can easily change your root password without any difficulty.If the single user mode is enabled in your linux then it is more easy for them to change your root password.Hacker with better knowledge on linux kernel otherwise can edit the grub menu entries and get the root access.Any way one of the above methods can be disabled i.e the single user mode.That's all...

---

### Post by schwabdale on 2011-07-29
I see...

As for Ethical Hacking, I would like to secure our wireless network better than it is. I would like to be able to "hack it" to prevent others from hacking it. I know very little about doing this, but I know it needs to be done. 

From what I understand, hackers will setup their laptop to look like yours, when you logon to the wireless network (their laptop) they can get your passwords and access your system. If Im correct, they can even duplicate your wireless access points mac address. 

I would like to know how to prevent any of my users from logging on to a fake WIFI. The only way I know to understand this, is to be able to do it.



So, single user mode should be turned off if their workstations have ubuntu installed?

---

### Post by Frogs Hair on 2011-07-29
Using any aspect of anybodies computer without permission is unethical . As stated there are fewer exploits , but like everything else the newer exploits are more sophisticated .

In windows environment there are self replicating .exe's  that can attach themselves downloaded items . In Linux the exploit would have to be part of a programs code and require a password . That is why it is suggested to use items from trusted repositories . This makes invasion more difficult but not impossible .

In my wireless experience I could see the other wireless services being used by the people next door and the local Starbucks . I never tried  to use them because of my first sentence and I also have no idea about the state of security on those networks .

---

### Post by community on 2011-07-29
I am not able to give you one solution for hacking WiFi as I am not good  at the network hacking field.But I know it is possible to hack the WEP  key for the wireless network using the tools which are already installed  in the backtrack(bt) linux distro.As far as I know bt linux provides the full root acces to perform the WiFi hacking operation.To know more about the Wireless hacks using bt linux follow  the link to download the various tutorials.So that you can get a complete picture about the wireless hacking.I recommend backtrack linux for any type of hacks i.e system hacks,wireless and network etc......



[http://www.backtrack-linux.org/tutorials](http://www.backtrack-linux.org/tutorials)

---

### Post by blind2314 on 2011-07-29
> **schwabdale said:**
> 1. If they hacked your computer, they prob got your SU Password anyway right? 
A. I thought there was a really good built in firewall in Ubuntu? Unlike Windows weak
firewall...is this correct?
 
2. This seems to be command line, are there any graphical tools? How about Backtrack?
 
3. Why are the last 2 digits important?
 
 
In response to your #2 point.
 
If you want to learn to be a "hacker" (used in quotations since that term is way overused, and people often label themselves without truly knowing anything) and secure your network, you should probably accept that CLI tools are much more flexible and give you far greater control. There are far more CLI only tools than there are tools with a GUI frontend written for them, and they are also more stable (in addition to a myriad of other reasons).
 
Don't take this personally, it's not an attack; merely stating some facts and opinions of my own.

---

### Post by maxpain on 2011-07-29
basicly sometimes when something is new is difficult or easy to hack into the system as someone have to search about bugs and system vulnerabilties if you want to capture packets and more wireshark is a greatsoftware to do it , as I am new on Ubuntu I will suggest you get C|EH 7 Books and start learning I already got them to beta test them and I am sure that you will learn how all these things works .

---

### Post by stefangr1 on 2011-07-29
> **schwabdale said:**
> Question 1
Is it harder for an intruder to hack into a Ubuntu OS, or a Windows OS? Why?

As there are usually a lot of known security holes in Windows that await fixing, whereas problems with Ubuntu are fixed quickly, Windows is more vulnarable in practice.

> Question 2  
In Ubuntu, you can click on your wireless icon and create a new wireless network. I think this will broadcast a wireless network name for people to logon to, then they are using your computer as a repeater. Can a hacker make this the same name as your wireless router...so when you logon, they can get your password? If so, how do they get your password...a software program installed on Ubuntu?

No this is not possible. They will be able to view network traffic and possibly use (unsecured) devices on the same network, though.

> Question 3
How would you know if your logging onto a Laptop (setup as a wireless router) instead of your real physical router? Are there tools to prevent this?

I think it is theoretically possible to configure a system as an access point. If it has the same name as your router, and a stronger signal, your system may automatically connect to this fake ap in stead of your router.

---

### Post by hakermania on 2011-07-29
> **schwabdale said:**
> 1. If they hacked your computer, they prob got your SU Password anyway right? 
    A. I thought there was a really good built in firewall in Ubuntu? Unlike Windows weak
        firewall...is this correct?

2. This seems to be command line, are there any graphical tools? How about Backtrack?

3. Why are the last 2 digits important?

(1) No ! Do they? I am not sure but I don't think so :O On the other hand they're called **root**kits. Idk :)
(2) Terminal > GUI
(3) Because you wouldn't really like to remember the whole thing, believe me ;) (00:21:6b:3c:06:cc)

---

### Post by haqking on 2011-07-29
> **Matt__ said:**
> ok so right clicking your network icon and creating a new network dosnt make your pc/laptop into a router(unless you specify it as shared connection in IPv4), you can do this via your router setup though(amongst other methods).

define "ethical hacking" your idea of ethics may vary from another persons.
what are you trying to do?

secondly what you are trying with airbase is password cracking wireless  networks..so as soon as that isnt your own or a clients network......


To define ethical hacking as concisely as possible, it is when a individual or team of individuals are tasked with testing the security of a given system or systems for vulnerabilities, threats and exposure with the explicit documented permission of the legal owner of that or those systems and data and within the laws and constraints pertinent to the task.
It is also known as a Pen test or Penetration test.

Anything outside of this is usually not legal or ethical, and when it is so it becomes malicious hacking which is known as Cracking.

in response to the OP the answers are very in depth and broad for your questions and require a greater knowledge of so many aspects.

I suggest learning as much as you can about networks and programming languages both low level and high level and as much about network protocols as possible then you should have a good foundation to explore the realms of security which is a broad area with many areas of experties.  usually on a Tiger team or red team of people carrying out a ethical hack or pen test there will be specific skill sets required which certain individuals will have, a bit like a 4 man special forces patrol where each member has a specific area of expertise though all are cross trained.

A true ethical hack or pen test can often take many months and that should give you an idea of how in depth it can be and also depends on whether is it is  a White box, grey box and black box attack (in the know, know a little, know nothing) about the system/s.

The CEH books, study materials/courses provide an entry level cert and study base for this profession, and covers alot of material and tools (some out of date) for many areas.

There are then alot more in depth areas of expertise and certs such as CREST, GSEC etc etc and also after CEH ec council themselves do a LPT or licenced pen tester which is a step up from the CEH.

---

### Post by aeiah on 2011-07-29
fake access points by their nature have to be open/unsecured. If someone is doing this at a coffee shop that also has free open wifi, users could accidentally join the wrong one. the fake ap could then read all the traffic, redirect people to malware sites etc.

from a domestic setting, if you've any sense you will have WPA encryption. you'll be able to see if someone's set up an open access point with the same name. further more, your system's preferences will be to attach to your access point. your system remembers more than just the access point name, so it'll still connect to the right one. it'll remember the name, the MAC, the channel, the type of encryption and the password. the fake access point could use the same ones as you for all but the password - and so connection will fail. this is why a fake access point must be unsecured for it to stand any chance of attracting clients to connect.

if your system tried to connect to the fake one and tried to authenticate, the fake access point wouldnt be able to grab your password because it's hashed. they'd have to crack it with brute force methods and if you've got a strong password, its unlikely their system will be able to crack it within their lifetime (or the earth's lifetime, if computers dont get faster).

---

