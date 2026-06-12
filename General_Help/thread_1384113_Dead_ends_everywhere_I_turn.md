---
title: "Dead ends everywhere I turn"
date: 2010-01-18
forum: General Help
---

### Post by tzarcasm on 2010-01-18
Still trying to get my openVPN running.I can get the daemon running from terminal but nothing is configured. I copied my config file over from Windoze partition. My openVPN works flawlessly on both my windoze boxes.

Following [this]("https://help.ubuntu.com/9.10/serverguide/C/openvpn.html") but came to another dead end when Im instructed to:

[B]Next, edit /etc/openvpn/easy-rsa/vars adjusting the following to your environment:         
[FONT=monospace]
[/FONT]export KEY_COUNTRY="US"
export KEY_PROVINCE="NC"
export KEY_CITY="Winston-Salem"
export KEY_ORG="Example Company"
export KEY_EMAIL="steve@example.com"
[/B]

I cant edit that,I tried but its a 'read only'. 

Are these instructions designed for long time users? If so where are the ones for noobs?

Everywhere I turn I run into a dead end.

---

### Post by sliketymo on 2010-01-18
Try : sudo gedit /etc/......

---

### Post by alwayshere on 2010-01-18
Maybe ya got a bad install

------------------------------
To install openvpn.

sudo apt-get install openvpn
------------------------------

--------------------------------------
to get the blacklist cheeker.

sudo apt-get install openvpn-blacklist
---------------------------------------

---

### Post by tzarcasm on 2010-01-18
> **sliketymo said:**
> Try : sudo gedit /etc/......

Thanks 

I forgot to mention in my OP that Im simply trying to tunnel my traffic on open wifi networks. Im signed up to "Surfbouncer VPN" service.And tried to use the VPN GUI's available in the repositories,but theyre not working-Ive been trying.(Importing the config file to "Kvpnc" as required) So figures Id manual config and attempt to connect via terminal.

However it just occured to me that this probably is the wrong route as Ive already been issued a 'key'(s).

Wouldnt building new keys render the ones I have for my paid VPN service on my Windoze boxes useless? 

Also how do I view my log?I was earlier and was going to post it but forgot where it was at.

Thanks,

-Tzar (nooby)

---

### Post by tzarcasm on 2010-01-18
> **alwayshere said:**
> Maybe ya got a bad install


Thanks I got as a result: "**blacklist is already the newest version.**"

---

### Post by sliketymo on 2010-01-18
> **tzarcasm said:**
> Thanks 

I forgot to mention in my OP that Im simply trying to tunnel my traffic on open wifi networks. Im signed up to "Surfbouncer VPN" service.And tried to use the VPN GUI's available in the repositories,but theyre not working-Ive been trying.(Importing the config file to "Kvpnc" as required) So figures Id manual config and attempt to connect via terminal.

However it just occured to me that this probably is the wrong route as Ive already been issued a 'key'(s).

Wouldnt building new keys render the ones I have for my paid VPN service on my Windoze boxes useless? 

Also how do I view my log?I was earlier and was going to post it but forgot where it was at.

Thanks,

-Tzar (nooby)

Just guessing,but I think you are supposed to substitute the information you already have over to your Linux box,that is the purpose of editing.I also found this,kinda old,but should help:

[https://wiki.ubuntu.com/VPN](https://wiki.ubuntu.com/VPN)

---

### Post by tzarcasm on 2010-01-18
> **sliketymo said:**
> Just guessing,but I think you are supposed to substitute the information you already have over to your Linux box,that is the purpose of editing.I also found this,kinda old,but should help:

[https://wiki.ubuntu.com/VPN](https://wiki.ubuntu.com/VPN)

Thanks Im just figuring this all out. I just found the 'vars.bat.sample' file on the Windows partition so I think Im getting closer. And thanks for the **'gedit'**,Ive run across many many instructions that leave little things like that out and have been tripped up by such things a lot.

---

### Post by tzarcasm on 2010-01-18
Thanks,Following the directions in the link you (sliketymou) provided..

Part of step one:

[B]Media change: please insert the disc labeled
 'Ubuntu-Netbook-Remix 9.10 _Karmic Koala_ - Release i386 (20091028.4)'
in the drive '/cdrom/' and press enter[/B]

This netbook doesnt have a cdrom drive. Although I do have the .iso on my desktop so I tried:

* sudo mount -o loop /tzarcasm/desktop/ubuntu_netbook.iso /media/cdrom0*

To which I get something like *'could not find'*

Also step two:
**"Create file /etc/ppp/peers/YOUR_COMPANY with this content:"**

How does one create a a file?  

I dont mean to be a pain in the **** but authors of these steps leave little things out that trip up noobs such as myself.

---

### Post by audiomick on 2010-01-18
Ok, creating a file:
I will give you the long answer for future reference.

You need to use an editor. The standard one in Ubuntu is gedit. You start it with the terminal command
```
gedit
```
to open a file in the directory you are in
```
gedit <*filename*>
```

to open one in another directory
```
gedit */path/to/file*
```

if you do that for one that doesn't exist, it will create it.

On top of that, files in /etc belong to root, and such config files often have to belong to root to work properly, so you have to start gedit as root. Use "gksu" for this, i.e. put it in front of the command.

this gives you
```
gksu gedit /etc/ppp/peers/YOUR_COMPANY
```

to create what you need.

> authors of these steps leave little things out that trip up noobs such as myself.I sometimes wonder if that isn't a bit deliberate, to make sure people find out a bit about what they are doing before they dive into the depths of their system...;)

---

### Post by tzarcasm on 2010-01-18
Thanks **audiomick** I'll definitely take notes. 

Can someone tell my how to mount the 9.10.iso (thats on my desktop) so I can get past: 
[B]
Media change: please insert the disc labeled
 'Ubuntu-Netbook-Remix 9.10 _Karmic Koala_ - Release i386 (20091028.4)'
in the drive '/cdrom/' and press enter[/B]this step;

Since my netbook doesnt have a cdrom drive.

---

### Post by tzarcasm on 2010-01-18
Wow,just wow. 

Everything about this OS is exceedingly difficult for noobs. Even setting up a guest account can be "dangerous" [(as outlined here)]("http://ubuntuforums.org/showthread.php?t=513820")

Who the hell was I in thinking I could actually set up something in Ubuntu thats dead simple in Widows like VPN?

---

### Post by Ahriman on 2010-01-18
> **tzarcasm said:**
> ...
To which I get something like *'could not find'*


Make sure the /media/cdrom0 folder exists, this has tripped me up plenty of times.

---

### Post by ankspo71 on 2010-01-18
> **tzarcasm said:**
> Wow,just wow. 

Everything about this OS is exceedingly difficult for noobs. Even setting up a guest account can be "dangerous" [(as outlined here)]("http://ubuntuforums.org/showthread.php?t=513820")

Who the hell was I in thinking I could actually set up something in Ubuntu thats dead simple in Widows like VPN?

Hi, I think the dangerous part of that link has to do with creating a passwordless guest account as opposed to creating a regular guest account, which is easier to do. If you need an easy to remember password for everyone using the same account, you can name the password the same as the username. Not recommended for regular user accounts though.

---

### Post by tzarcasm on 2010-01-18
Thanks for everyones input but Im done with this for a while-I've been trying for weeks.

Which means back to Windows I  go for now. I have to agree with what **HermanAB** said [in my other thread]("http://ubuntuforums.org/showthread.php?t=1382610"):

[I][B]"Howdy,
 
If it will make you feel better... I have been using UNIX since 1984 and I have never been able to get OpenVPN to work either. So it is not easy, despite what other people may tell you.

When I need a VPN, I use SSH and Socks.
                                                                                               __________________
                Cheers,

Herman"[/B]                                


[/I]

---

### Post by sfenton on 2010-01-21
It's been a while back since I configured my openvpn with Surfbouncer. Did you load the openvpn package via synaptic and all the dependancies. You could use either the openvpn-nm and import the configuration, or use the terminal based openvpn and reference the configuration file. You need three files from them, if I remember correctly. 

All this stuff of generating keys should not be necessary, they provide all that. 

Cheers, 

Sig

---

