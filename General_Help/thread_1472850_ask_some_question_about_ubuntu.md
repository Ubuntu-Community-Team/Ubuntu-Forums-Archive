---
title: "ask some question about ubuntu"
date: 2010-05-04
forum: General Help
---

### Post by 0918272 on 2010-05-04
I want ask some question ubuntu system I need solve this question:
 
 
1) I have ubuntu 9.10 .So How can upgrade ubuntu to 10.04 without install ubuntu beginning?
 
 
 
2) Does ubuntu need to Anti-Virus. If it need which program can I download?
 
 
3) I hear from my friend the program open office now issued new version is ((3.2)). 
 
So how can update open office to 3.2? 
 
 
4) I show on Youtube one can use Windows Live Messenger on ubuntu. This link site Youtube
 
 
[http://www.youtube.com/watch?v=QSj7v0Bt9q0&feature=related](http://www.youtube.com/watch?v=QSj7v0Bt9q0&feature=related)
 
 
Can you tell me how can use this?
 
 
 
I hope that I would see advantage answers O:)

---

### Post by moviemaniac on 2010-05-04
1) Start the update manager and you should find a button telling you 10.04 is available. Click it to update

2) No, Ubuntu doesn't need Antivirus. If you want to scan for Widnows viruses on a network or an external drive you can use ClamAV.

3) When you update to 10.04 Open Office 3.2 will be included

4) First install WINE from the Software center. Then download the messenger from Microsoft and you can install it like in Windows.

---

### Post by tgm4883 on 2010-05-04
> **0918272 said:**
> I want ask some question ubuntu system I need solve this question:
 
 
1) I have ubuntu 9.10 .So How can upgrade ubuntu to 10.04 without install ubuntu beginning?

You should be able to upgrade using the update manager. Or run "update-manager -c" from a command prompt



> **0918272 said:**
> 
2) Does ubuntu need to Anti-Virus. If it need which program can I download?


There is clamAV in the repos


> **0918272 said:**
> 
3) I hear from my friend the program open office now issued new version is ((3.2)). 
 
So how can update open office to 3.2? 

If you upgrade to 10.04, you will get Open Office 3.2


> **0918272 said:**
>  
4) I show on Youtube one can use Windows Live Messenger on ubuntu. This link site Youtube
 
 
[http://www.youtube.com/watch?v=QSj7v0Bt9q0&feature=related](http://www.youtube.com/watch?v=QSj7v0Bt9q0&feature=related)
 
 
Can you tell me how can use this?


Looks like he is using [Wine]("http://www.winehq.org/") to do that. You can install wine from the repos

---

### Post by DomesDKG on 2010-05-04
You could ins tall the MSN messager client, or you could use the built in chat client in 10.4, which supports MSN as well as several other networks.  It's less work :/

---

### Post by moviemaniac on 2010-05-04
> **DomesDKG said:**
> You could ins tall the MSN messager client, or you could use the built in chat client in 10.4, which supports MSN as well as several other networks.  It's less work :/
Would be my choice too to just use pidgin or empathy or whatever it is that's installed per default these days (don't use chat progs besides ekiga for sip so I don't keep track of these changes).

---

### Post by sxmaxchine on 2010-05-04
im going to keep this quick and clean.

1. go to the update manager
2. no, but you can use [avast]("http://www.debianadmin.com/avast-antivirus-for-ubuntu-desktop.html")
3. it is included with 10.04
4. Use wine or playonlinux (pol it is easier), although i would recomend emesene

Hope these answer your questions

---

### Post by 0918272 on 2010-05-04
Thank you all for help me for Answer  Q1,  Q2, and Q3 :D

about Answer Q4 

you say download wine. what's wine and what's does?

and how can install Windows Live Massenger if I have wine?
 
 
sorry you tired with me O:)

---

### Post by sxmaxchine on 2010-05-04
you can install it from the repos if it isnt there then follow [these instructions]("http://www.winehq.org/download/deb")

---

### Post by sxmaxchine on 2010-05-04
wine basically lets you use windows programs (.exe files) but remember it does not work for every program.

---

### Post by 0918272 on 2010-05-04
[SIZE=4]Thanks for help me for about information wine. 

But I'm ask how install windows live Massenger on wine or any windows program?

[COLOR=#000000][FONT=arial]If you can explain it with pictures [/FONT][/COLOR]

[/SIZE]

---

### Post by sxmaxchine on 2010-05-04
i cant give you pictures because im at tafe right now but  il be able to make a tutorial tonight when i get home and i can email you the tutorial 

or if you have enough internet you can watch this video on how to install wine

[this is the video]("http://www.youtube.com/watch?v=hZgjgeDQVo4")

---

### Post by 0918272 on 2010-05-04
Thanks anyway for help.;)

No problem any time you free post tutorial 

again Thanks for video but this video about how install wine

but I need how to install any program on wine.

---

### Post by tgm4883 on 2010-05-04
After you install wine, download msn messenger (like you would on windows), and double click on the install file (like you would on windows)

---

### Post by 0918272 on 2010-05-05
Thanks 

But I Followed download wine and I download windows live messenger

and install wine but can't install windows live messenger.

If I install it there display error :mad:

---

### Post by tgm4883 on 2010-05-05
Well it's hard to help you if you don't even list the error. If I had to guess, it's not set as executable, which can be fixed by right clicking on the msn installer and selecting properties, then checking the executable bit.

---

### Post by 3rdalbum on 2010-05-05
I don't think Windows Live Messenger works on Wine.

And even if it did, you should use native Linux software. The default Instant Messenging program, Empathy, works fine on the MSN (Windows Live) network.

---

### Post by 0918272 on 2010-05-06
Thank you guys for help me
 
about Messenger I go to in setup Messenger and  properties and permissions then cheek box Execute like picture.
 
[[IMG]http://store1.up-00.com/May10/esb71250.png[/IMG]]("http://www.up-00.com/")
 
Now I can install messenger and work like picture .
 
[[IMG]http://store1.up-00.com/May10/46F71250.png[/IMG]]("http://www.up-00.com/")
 
 
And now I can install another yahoo messenger.
 
[[IMG]http://store1.up-00.com/May10/qJx71250.png[/IMG]]("http://www.up-00.com/")
 
 
 
 
Thank you for every one help me

---

