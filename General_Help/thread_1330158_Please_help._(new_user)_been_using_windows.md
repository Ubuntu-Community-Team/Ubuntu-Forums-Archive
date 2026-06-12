---
title: "Please help. (new user) been using windows"
date: 2009-11-18
forum: General Help
---

### Post by ibrahim.k on 2009-11-18
Hi,
I have just installed ubuntu 9.4 on my laptop (HP-dv6 1045)
But I faced some problems like.

I can't hear sounds, I can't play mp3 files.
How can I create a dial up connection some times I have to use it (using wireless now)
How can I switch input keyboard languages or how to install them,( I can only write in English)

Many thanks,
Ibrahim

---

### Post by Dale61 on 2009-11-18
I was just like you back with my first Ubuntu flavour - 6.06LTS.

What I did was browse ALL the forums and I eventually found all the fixes I needed.  The Tutorials & Tips forum would be the best place to start.

Another option is to read through this:
[http://ubuntuguide.org/wiki/Ubuntu:Jaunty]("http://ubuntuguide.org/wiki/Ubuntu:Jaunty")

---

### Post by lvlint67 on 2009-11-18
> **ibrahim.k said:**
> Hi,
I have just installed ubuntu 9.4 on my laptop (HP-dv6 1045)
But I faced some problems like.

I can't hear sounds, I can't play mp3 files.
How can I create a dial up connection some times I have to use it (using wireless now)
How can I switch input keyboard languages or how to install them,( I can only write in English)

Many thanks,
Ibrahim


a program like vlc should handle the mp3 issues:: mp3 is kinda shadey in ubuntu's eyes and there are a few things that you need to do to get support
google: ubuntu mp3 support

as for the dial up connection... :( I haven't used a modem in years and can't offer any help there.

the last question should be easy to solve with a good search: ubuntu change keyboard language?

---

### Post by ibrahim.k on 2009-11-18
Thank you.
But I didn't find anything related to the modem driver also I dont have 
Applications -> Internet -> GPPP Internet Dial-up 

do i have to download it ?

---

### Post by P4man on 2009-11-18
> **ibrahim.k said:**
> Hi,
I have just installed ubuntu 9.4 on my laptop (HP-dv6 1045)
But I faced some problems like.

I can't hear sounds, 

Appears there is (/was) a bug with laptops very similar to yours:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/363870](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/363870)

It has apparently been resolved in the current ubuntu release, but if you dont want to upgrade, you could try enabling the so called "backports" in case they backported this fix to ubuntu 9.04. Go to system > administation > software sources > updates. Enable "unsupported updates" (backports). Then update your system through system > adminstration > update manager. No guarantee but it might work.

> I can't play mp3 files.

Thats because of patent restrictions on the MP3 format. Read this:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

it also explains how to install those codecs (which may or may not be illegal where you live).
> 
How can I create a dial up connection 

See link above. Scroll down to dial-up.

> How can I switch input keyboard languages or how to install them,( I can only write in English)

Try system > adminstation > language support. To configure the keyboard system > preferences > keyboard > layout.

---

### Post by ibrahim.k on 2009-11-18
Thank you [P4man]("http://ubuntuforums.org/member.php?u=412374")
this is my first time using Ubuntu I have seen that post you gave to me I understand nothing and I am sorry for that.

According to the keyboard layout it worked thank you.

---

### Post by P4man on 2009-11-18
> **ibrahim.k said:**
> Thank you [P4man]("http://ubuntuforums.org/member.php?u=412374")
this is my first time using Ubuntu I have seen that post you gave to me I understand nothing and I am sorry for that.

According to the keyboard layout it worked thank you.

You dont have to understand it, Im just pointing out there is bug with sound on laptops which seems very similar to yours. What I wrote after that to enable "backports" and should be easy, even if you dont understand exactly  what it is  you;re doing, just follow the instructions I gave  and it might fix it.

---

### Post by P4man on 2009-11-18
> **ibrahim.k said:**
> Thank you.
But I didn't find anything related to the modem driver also I dont have 
Applications -> Internet -> GPPP Internet Dial-up 

do i have to download it ?

Missed this. Yes you might have to install it then. go to applications > add and remove software and search for ppp or dialer.

---

### Post by arnab_das on 2009-11-18
see if this helps as far as playing mp3s are concerned:

[http://thoughtsndreams.wordpress.com/2009/11/14/install-restricted-extras-for-ubuntu/](http://thoughtsndreams.wordpress.com/2009/11/14/install-restricted-extras-for-ubuntu/)

---

### Post by ibrahim.k on 2009-11-18
> **P4man said:**
> Missed this. Yes you might have to install it then. go to applications > add and remove software and search for ppp or dialer.


Thank you again p4man

I have installed a ppp dailer kppp 
But I don't know what settings to choose for modem device (hp- dv6 1045) 
How can I know if this device is correctly installed ?

And so far this moment I couldn't solve the sound problem why this is happening.

Sorry to prolong on you.

---

