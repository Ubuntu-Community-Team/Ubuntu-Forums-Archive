---
title: "USing Volume keys to Control PCM"
date: 2006-06-07
forum: General Help
---

### Post by caldevil on 2006-06-07
I want the volume keys on my keyboard to control to control PCM instead of master so that I can reduce both the headphone and computer speaker sound level. I remember using "aumix"  to do that in fedora. Is there any neat way to do that in both Gnome and KDE?

---

### Post by gookie on 2006-06-07
This has also been my problem since Breezy, and I was quite bummed when I saw the same thing in Dapper. 

I would like to know the solution too. :D

---

### Post by puelly on 2006-06-10
any luck finding the solution to this problem?

---

### Post by Anduu on 2006-06-11
Try right clicking the volume icon in the panel and select properties.From here you can select which device it controls.

Pick PCM and see if that works.

---

### Post by Anduu on 2006-06-11
BAH!!!

Nevermind it doesn't :-|

---

### Post by hvbakel on 2006-10-19
well a bit late perhaps but in KDE you can right-click the volume icon (kmix) and choose 'select master channel'. If you set this to PCM the volume control buttons control both speaker and headphone channels.

---

### Post by nelsong on 2006-10-25
I miss the old gnome days when you could select the channel right in the keyboard binding app...since it's been gone everybody has gotten around it by using different applications, xkeybind, hotkeys...I wonder when they'll fix this, it's getting very annoying.

---

### Post by VuDu on 2006-11-17
[http://gnomesupport.org/forums/viewtopic.php?t=10879](http://gnomesupport.org/forums/viewtopic.php?t=10879)

Looks like it's a know bug.
Too bad they haven't fixed it yet. :(


[http://bugzilla.gnome.org/show_bug.cgi?id=173035](http://bugzilla.gnome.org/show_bug.cgi?id=173035)

---

### Post by VuDu on 2007-01-20
[http://bugzilla.gnome.org/show_bug.cgi?id=173035](http://bugzilla.gnome.org/show_bug.cgi?id=173035)

Check the topic again...

>  Comment #36 from Jan Arne Petersen  (points: 18)
2007-01-08 15:41 UTC [reply]

Created an attachment (id=79756) [edit]
Patch to implement the sound-capplet and keybindings part


Comment #37 from Thomas Wood (control-center developer, points: 15)
2007-01-08 22:40 UTC [reply]

Patch looks generally good - let's get this in got 2.18!


Comment #38 from Rodrigo Moya (control-center developer, points: 21)
2007-01-08 22:55 UTC [reply]

Patch committed

Great news, no?

---

### Post by scifan2 on 2007-01-21
IF you are running KDE it's very easy...   see the above post... 

In theory, it would work in Gnome as well... Though I had issue's with gnome losing it's volume control.....

---

### Post by VuDu on 2007-01-22
But the problem is the fact that Gnome's Volume Applet and the Keyboard's Multimedia Keys don't produce the same result.
And since changing DE isn't a real solution I realized that people with be glad to know that the problem has been solved.
It's working on Gnome 2.17.5 :) So that's no longer a problem on Feisty ;)

---

### Post by Grog140 on 2007-02-16
I am running Feisty and I still have the problem?

Maybe I am missing something but the volume keys still only control mater instead of PCM or headphone.

---

### Post by VuDu on 2007-02-16
You have to go to "Control Center" -> "Sound" and there chose the default controller.
That way, both multimedia keys and the tray icon will obey to the default controller.

---

### Post by Grog140 on 2007-02-16
Thank you so much!

It worked! Finally the volume keys are good for something, lol

---

