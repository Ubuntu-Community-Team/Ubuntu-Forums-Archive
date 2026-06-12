---
title: "Which antivirus/firewall"
date: 2012-05-17
forum: General Help
---

### Post by samwillc on 2012-05-17
Hi everyone,

I am wondering what people use when they use antivirus or firewall software on ubuntu 12.04.

I have been reading over this thread on security:

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

...which was most enlightening. I would transfer files between linux and windows so maybe av software is important in my situation. I would also open up ports so I guess a firewall would be sensible too.

Any input would be very helpful.

Thanks.

Sam.

---

### Post by wilee-nilee on 2012-05-17
I use three AV bitdefender, avast, and clamav, The first two will give you options to remove or cage the problem, clam just identifies possible problems. All will give false positives, for example the avast on my set up sees some comodo stuff in my W7 set up as a problem, but with a quick look on the web before acting you can clear up the false hits and not remove anything that is not really a problem. 

If you install avast, post that you have, it needs a file tweak to run correctly.

There are a number of ways to protect yourself in the firewall dept, check here for info.
[http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)

---

### Post by samwillc on 2012-05-17
Hi willee-nilee,

Ok thanks for that.

I will use avast (as I'm used to that on windows - ran it for years). Do you think you could post the tweak required so I can get prepared beforehand?

Sam.

---

### Post by wilee-nilee on 2012-05-17
> **samwillc said:**
> Hi willee-nilee,

Ok thanks for that.

I will use avast (as I'm used to that on windows - ran it for years). Do you think you could post the tweak required so I can get prepared beforehand?

Sam.

Sure no problem, open this file and insert this at the bottom of the page.

```
sudo gedit  [FONT=Verdana, sans-serif][SIZE=1]/etc/sysctl.conf[/SIZE][/FONT]  
``````
 [FONT=Verdana, sans-serif][SIZE=1]kernel.shmmax = 128000000[/SIZE][/FONT]
```Then to have it running with out a reboot this first time, it will run automatically in the future.
[FONT=Verdana, sans-serif][SIZE=1]
```
sudo sysctl -w kernel.shmmax=128000000
```[/SIZE][/FONT]

---

### Post by samwillc on 2012-05-17
> **wilee-nilee said:**
> Sure no problem, open this file and insert this at the bottom of the page.

```
sudo gedit  [FONT=Verdana, sans-serif][SIZE=1]/etc/sysctl.conf[/SIZE][/FONT]  
``````
 [FONT=Verdana, sans-serif][SIZE=1]kernel.shmmax = 128000000[/SIZE][/FONT]
```Then to have it running with out a reboot this first time, it will run automatically in the future.
[FONT=Verdana, sans-serif][SIZE=1]
```
sudo sysctl -w kernel.shmmax=128000000
```[/SIZE][/FONT]

Sorry, linux is new to me! Can I just run this by you step by step, is this what will happen:

1) I presume this is AFTER I install avast.
2) The first command will open up the file /etc/sysctl.conf in gedit.
3) Paste in the code shown at the bottom of the file I just opened.
4) Save file?
5) Run the last code in the terminal to start the process, not requiring a reboot

Something like that?

Sam.

---

### Post by wilee-nilee on 2012-05-17
> **samwillc said:**
> Sorry, linux is new to me! Can I just run this by you step by step, is this what will happen:

1) I presume this is AFTER I install avast.
2) The first command will open up the file /etc/sysctl.conf in gedit.
3) Paste in the code shown at the bottom of the file I just opened.
4) Save file?
5) Run the last code in the terminal to start the process, not requiring a reboot

Something like that?

Sam.

You have got it, linux can seem confusing to say the least if the terminal is new to you and in other ways for sure. :)

I would basically set that file like this before you actually run a update with avast, that is where the problem happens, you will get a error on the next time you open it if not.

I set my avast, to auto update, so on firing it up  each time, it updates, it is just easier for me, that is in the edit preferences, which for some reason I am not seeing in my gnome-shell setup but does show in the unity desktop, in the top bar.

---

### Post by Grandma_DOG on 2012-05-20
How effective have you found avast?

---

### Post by samwillc on 2012-05-20
> **Grandma_DOG said:**
> How effective have you found avast?

Not installed it yet, been giving ubuntu a good run over first to make sure that it really is a replacement for win7 for me!

Will post back when it's up and running.

Sam.

---

### Post by Mopar1973Man on 2012-05-20
Noob question in regards to this?

Is anti-virus and firewall really need with Linux? :confused:

---

### Post by samwillc on 2012-05-20
> **Mopar1973Man said:**
> Noob question in regards to this?

Is anti-virus and firewall really need with Linux? :confused:

Thumbs up for the positive input. Thanks.

Sam.

---

### Post by GreatDanton on 2012-05-20
> **Mopar1973Man said:**
> Noob question in regards to this?

Is anti-virus and firewall really need with Linux? :confused:

The answer is no, because there are no known viruses for Linux (never heard of any Linux infection) . However you can install anti-virus program to scan Windows if needed.

---

### Post by Mopar1973Man on 2012-05-20
Whew! (Wipes sweat from brow)...

My Windows Drives have there own protection so I'm not worried about them but since I spend more time in Linux why not ask!

But thank you for the answer! ;)

---

