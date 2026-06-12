---
title: "Netbook software"
date: 2010-09-07
forum: General Help
---

### Post by ArbiterOfTruth on 2010-09-07
Hello all. I installed Ubuntu Netbook Remix 10.04 today on a netbook I purchased yesterday. The installation was flawless & I love how it looks however I seem to be having trouble getting additional software for basic tasks.

I get to the Ubuntu Software Center but I am not able to download Adobe Reader 9 or Pidgin Instant Messenger or any of the other little things I need for daily use. Is it that the netbook version doesn't allow you to get those things or have I done something wrong?

Thanks in advance.

---

### Post by kerry_s on 2010-09-07
try system-> synaptic package manager

you need to turn on the partner repo for adobe.
make sure you install "ubuntu-restricted-extras" to get most of the stuff you'll want.

---

### Post by ArbiterOfTruth on 2010-09-07
OK I am in the Package Manager now. Where do I find what you said?

Better yet. Add me to whatever IM you have:

MSN - [email]dtriniman@gmail.com[/email]

AIM - SyferDiaz

YIM - Syfer_Diaz

---

### Post by kerry_s on 2010-09-07
use the filter bar, type "restricted" & it should be in view.

at the top in the settings look for "repositories" partner repos should be on the second tab of that window.

i have to go off memory, not currently using ubuntu. ;)

---

### Post by Hobgoblin on 2010-09-07
> **kerry_s said:**
> 
at the top in the settings look for "repositories" partner repos should be on the second tab of that window.

i have to go off memory, not currently using ubuntu. ;)

I think your memory is failing you.  There's no such option unless you've added the repositories yourself.

pdf files should open using Document Viewer.

**ArbiterOfTruth**: what happens when you try to install software via the software centre?

[edit]
I think what kerry_s was getting at is the step 1 in [this thread](http://ubuntuforums.org/showthread.php?t=1517979).

> Enable repository: Click [FONT="Courier New"]System[/FONT] -> [FONT="Courier New"]Administration[/FONT] -> [FONT="Courier New"]Software Sources[/FONT], go to tab [FONT="Courier New"]Other Software[/FONT] and tick the first entry ("partner"). Close and confirm the "Reload".

---

### Post by kerry_s on 2010-09-07
> I think your memory is failing you. There's no such option unless you've added the repositories yourself.

i'm sure it's there. partner repos has things like adobe & java. it is usually the first 1 on the other sources tab, there are 2 lines, the other is source, which you don't need.

---

### Post by ArbiterOfTruth on 2010-09-08
OK thanks for that tip. The 1st line is already ticked so I didn't have to. I did however notice something; the stuff I want is there. I can see everything but they only have the > More Info option & not the>  Install option.


[http://i894.photobucket.com/albums/ac143/Tru3b0rn/General/no_install.png](http://i894.photobucket.com/albums/ac143/Tru3b0rn/General/no_install.png)

 The stuff underneath what I want does have the option. 

[http://i894.photobucket.com/albums/ac143/Tru3b0rn/General/install.png](http://i894.photobucket.com/albums/ac143/Tru3b0rn/General/install.png)

Do I have to do something to enable it? Does the Netbook Remix not have it? (in which case I will just install the regular Ubuntu onto the netbook) Did I do something wrong during installation? I mean it is a netbook & I can get onto the net but it would be nice to be able to do regular stuff like watch movies, listen to music, read .pdf documents etc. I really need to be able to install the relevant packages.

Thanks in advance,

---

### Post by kerry_s on 2010-09-08
i told you try synaptic, software center is crap.

in synaptic you just right click mark for install.

---

### Post by ArbiterOfTruth on 2010-09-08
I got through!!! What happened was the repositories was going to the server for my country. I changed it to the main server & it downloaded & updated the repositories. I was then able to go in & select the stuff I wanted. Pidgin, VLC etc. Thanks a lot guys!!!

Thanks again for everything Kerry!

---

