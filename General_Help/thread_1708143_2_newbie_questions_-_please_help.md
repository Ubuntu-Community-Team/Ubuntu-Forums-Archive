---
title: "2 newbie questions - please help"
date: 2011-03-16
forum: General Help
---

### Post by xempyrean on 2011-03-16
Hi everyone,

I'm new in Ubuntu, and my machine is a HP laptop.
I got 2 problems.
Currently I'm using 10.04 LTS edition.

1. I plugin my iphone then start my machine, it/ubuntu froze at splash screen. But I can get in recovery mode and boot, then use startx to start the desktop.
I wanna know how to start with iphone plugged in, and no need to get into recovery mode.

2. I clicked a setup by mistake. It was a setup for rhythmbox everytime I plugin iphone the rhythmbox shows up. I want to cancel it but I cant find where to set it again. 

Thsoe problems are both about iphone :S  

Many Thanks
Chev

---

### Post by Bucky Ball on 2011-03-16
Welcome. Please give descriptive thread titles like 'iPhone problems with 10.04' or 'How to change media player default' in future perhaps. You will get more help that way. ;)

So, don't have your iPhone plugged in when you boot up. Once looking at the desktop plug it in. I am presuming in the latter scenario that is when Rhythmbox pops up?

Try 'Removable Drives and Media'. I am on Xubuntu at the moment but in Ubuntu I would think it would be in System>Administration or System>preferences.

---

### Post by xempyrean on 2011-03-16
> **Bucky Ball said:**
> Welcome. Please give descriptive thread titles like 'iPhone problems with 10.04' or 'How to change media player default' in future perhaps. You will get more help that way. ;)

So, don't have your iPhone plugged in when you boot up. Once looking at the desktop plug it in. I am presuming in the latter scenario that is when Rhythmbox pops up?

Try 'Removable Drives and Media'. I am on Xubuntu at the moment but in Ubuntu I would think it would be in System>Administration or System>preferences.
Thanks for your info.
But I cant find the Removable Drives and Media in preference.
I tried to find in gconf-editor in alt-F2. but cant find it.
I also tried rhythmbox settings, I couldnt find it.

---

### Post by steaksauce on 2011-03-16
> **xempyrean said:**
> Thanks for your info.
But I cant find the Removable Drives and Media in preference.


I believe System >  Administration > Disk Utility is what you're looking for in Gnome ;)

---

### Post by xempyrean on 2011-03-16
> **steaksauce said:**
> I believe System >  Administration > Disk Utility is what you're looking for in Gnome ;)
thanks man , Ill take a note ;)

---

### Post by steaksauce on 2011-03-16
Don't quote me on it. I did a search on the Software Center for media and it says it manages media XD It's my best guess.

---

### Post by Bucky Ball on 2011-03-16
Just logged into Gnome and I was thinking System>Preferences>Preferred Application. Then the Multimedia tab. That will let you change the default. ;)

---

### Post by xempyrean on 2011-03-16
thanks, I have set the preferred app to Custom/None. 
But when I plugin iphone , rhythmbox still shows up.

And I tried gconf-editor - rhythmbox - state/plugins - ipod , I set both hide or disable. when i plugin iphone, the rhythmbox still shows up but "cant" detect my iphone.

I think there must be some program called rhythmbox

---

### Post by Bucky Ball on 2011-03-17
Oh, now I think I get you!

There *is* a program called Rhythmbox!

---

### Post by xempyrean on 2011-03-17
lol xD
well I didnt find the program which calls the rhythmbox

---

### Post by gcomito11 on 2011-03-17
> **xempyrean said:**
> lol xD
well I didnt find the program which calls the rhythmbox
 
 
 Rhythm box is the defualt music palyer in ubuntu 10.10 and 10.04

---

### Post by Bucky Ball on 2011-03-17
Applications>Sound and Video? It's not there??

---

### Post by YfoMp5QBh2 on 2011-03-17
It should of been installed with the generic install of Ubuntu, if not and you want to install it, go to the Ubuntu Software Centre and type rhythmbox into the search box and install it from there.

---

