---
title: "Cant install ANYTHING."
date: 2009-12-30
forum: General Help
---

### Post by kennyken747 on 2009-12-30
Wow, I'm pretty ticked off at this point.

For one, I'm using the Intel 845GL chipset which is supposedly widely supported. Oh really? Then why when I go to fullscreen in any video it is CHOPPY and GRAINY.

I decided to come to the forums for help. I started following an install guide, and next thing that happens? I get an error.

"DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable"


Apparently I can install anything in Ubuntu Software Center either.

Im not doing a re-install either, I went through way too much to even get the newest Ubuntu up and running. I'm not impressed. 9.10 has problems and yal need to work on them. I hate to come off this way but it's really frustrating when I erased my Windows partition to the point of no return.

---

### Post by judge jankum on 2009-12-30
Latest is not always greatest" I'm using 8.04 LTS and it's rock solid....Well until the bugs are worked out of the newer versions...:popcorn:

---

### Post by kennyken747 on 2009-12-31
I know bro but like I said, re-installing really isn't an option.

I just tried multiple re-installs and get this, an even newer problem arises! LOL!

Now my top panel is out of order.

---

### Post by kennyken747 on 2009-12-31
Well actually, is there an easier way to downgrade to 8.04 without completely re-installing? I'm willing to go to 8.04 if it means my video will be ok and I wont have these annoying bugs anymore. And of course I could update to 9.* whenever they work them out.. But I still want to try one more time.

Could anybody help? Please? :)

---

### Post by danastasio on 2009-12-31
```
sudo apt-get install xserver-xorg-video-intel
```

and restart. What happens?

---

### Post by kennyken747 on 2009-12-31
Ok I think I may have fixed it!!

-FOR EVERYONE WITH THIS PROBLEM-

Go to Startup Applications and disable the updater.

Restart.

When booted up, go to System - Administration - Update Manager

If it gives you an error message and tells you to enter 
sudo dpkg --configure -a
in the Terminal, you're in luck! Because Update Manager is the source of the problem!

I entered it, and apparently something made my terminal quit in the middle of an install. It was trying to update Java but the terminal was closed somehow. I didn't even notice lol, as I was running it in the background.

Now the only problem is full-screen video running smoothly :P

---

### Post by kennyken747 on 2009-12-31
Nooooooooooooooooooooooooooooooo

"E:I wasn't able to locate a file for the sun-java6-jre package. This might mean you need to manually fix this package. (due to missing arch): " comes up

When I try to install anything with Ubuntu Software Center!! :( I quit Ubuntu. I guess Ill just re-install Windows ;(

GOD I can install now.


I simply had to run the Java update through Update Manager. So to add to my little guide.

-
1.Go to Startup Applications and disable the updater.

2.Restart.

3.When booted up, go to System - Administration - Update Manager

4.If it gives you an error message and tells you to enter 
sudo dpkg --configure -a
in the Terminal, you're in luck! Because Update Manager is the source of the problem!

5. MAKE SURE you install the updates that are queued in the Update Manager, because most likely it is the source of the problem! Install them and you'll be able to install through apt-get and USC again!

6. Re-enable updates. You'll probably need them.


Still :/ video.... and danastasio it says I already have that installed.

---

### Post by danastasio on 2009-12-31
update manager isn't the source of the problem. what it sounds like happened is you were downloading a program (or something) and it was interrupted by something. power outage, totally random fail (really REALLY freaking rare), either way, it was an unclean kill. In a terminal, enter
```
sudo dpkg --configure -a
```

This should fix the broken package and restore synaptic. 

See my previous post for my answer to your video problem.

---

### Post by judge jankum on 2009-12-31
If your looking for a solid system with very few bugs, always check for the latest "stable" release... I'm not a techie, but these guys on the forum are, I'm sure they can help you work out the bugs in anything.

---

### Post by danastasio on 2009-12-31
Also, you've only given us half an hour to try to help you, patience is a virtue, trust me, I've gotten upset with the community before and it got me nowhere. Based on my experience, I'd be willing to bet that you've had this problem since you installed the OS 45 mins ago. If your coming to the forum for help, expecting an answer in less than half an hour is just plain silly. I'm pretty sure I'm the only one here who has nothing better to do than sit here and answer questions all day. It can even take a few hours to get a good answer, but given time, a good answer you will get.

---

### Post by kennyken747 on 2009-12-31
Yeah I'm sorry for that I totally didn't mean to come off that way.

I've had 9.10 installed since Saturday though.

I did your command and it said I already have it installed

I'm currently trying this guide [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

---

### Post by danastasio on 2009-12-31
Glad to see you calmed down!
Now lets see what we can do. Attach a copy of your /etc/X11/xorg.conf file and i'll poke around in it and see what's up, im willing to bet the problem lies either there, or in the driver itself. 

Regarding the HOWTO, what exactly did you do, it mentions the "safe/optimal vs. bleeding edge"

what from this did you follow (just so i get an idea of what you've been doing.

and how did the dpkg --configure -a command i suggest work out for you?

---

### Post by danastasio on 2009-12-31
Just for the record, i -DO- think that things like this on a clean install are unnacceptable and the Ubuntu dev's should really get some more testers because the last couple of releases have been a bit shakey on release.

I'll link you to an article that will tell you how to roll back your driver to an older "known working" driver. This may help should you decide you want to go that route.

I've put out a call for help, its 1 A.M. here and I'm starting to fall asleep, but i'll be back in a few hours to continue helping, and in the mean time, some people should be along to help in my absense.

EDIT: I guess you want that link eh?
[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

---

### Post by kennyken747 on 2009-12-31
Hey I really appreciate it man, I'm gonna go ahead and read the article and post my results

---

### Post by danastasio on 2009-12-31
No problem, I've been in your situation a few times :P

(And once, the -only- reason i DIDNT go back to windows was because the install disks didn't work :D)

Anyway, how did that link help you?

If it didn't help, can you post the output of 

```
sudo cat /etc/X11/xorg.conf
```

Also, how did dpkg work for you?
My experience tells me it doesn't always work the first time. dunno why.

---

### Post by danastasio on 2010-01-01
Just checking in to see how everything is going.

Happy New Year!!

---

