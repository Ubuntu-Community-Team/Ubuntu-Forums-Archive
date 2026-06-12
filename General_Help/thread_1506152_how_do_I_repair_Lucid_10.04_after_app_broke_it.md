---
title: "how do I repair Lucid 10.04 after app broke it"
date: 2010-06-10
forum: General Help
---

### Post by charonred on 2010-06-10
Is there a way to repair an install of Lucid 10.04 after the installation of an app from help.ubunt.com broke it severely

post on the [guilty app is here]("http://ubuntuforums.org/showthread.php?p=9438808#post9438808")

I have 2 monitors;
monitor 2 had a top panel that displayed all temps/fans etc - gone now
monitor 1 top panel had several apps added to the normal that are now gone
window buttons have now reverted to my left (I had moved them to the right) - fixed those things easy enough, but others won't fix.

I can no longer view videos in Movie Player or VLC; I get sound, but no video

and I've lost all my printers, and don't have the ability to 'Add Printer' - it's greyed out - I can't run my business without printers, if I don't get repair system by tonight, then I have no option but to back-up all my data and do a clean install of 10.04 

amended - easy-ocr may break Lucid 10.04, so don't install it as a text scanner and editor - unless it's required for visually impaired, then it seems to be a good text to voice reader.

---

### Post by dcstar on 2010-06-10
> **charonred said:**
> Is there a way to repair an install of Lucid 10.04 after the installation of an app from help.ubunt.com broke it severely

post on the [guilty app is here]("http://ubuntuforums.org/showthread.php?p=9438808#post9438808")

I have 2 monitors;
monitor 2 had a top panel that displayed all temps/fans etc - gone now
monitor 1 top panel had several apps added to the normal that are now gone
window buttons have now reverted to my left (I had moved them to the right) - fixed those things easy enough, but others won't fix.

I can no longer view videos in Movie Player or VLC; I get sound, but no video

and I've lost all my printers, and don't have the ability to 'Add Printer' - it's greyed out - I can't run my business without printers, if I don't get repair system by tonight, then I have no option but to back-up all my data and do a clean install of 10.04 

easy-ocr will break Lucid 10.04, so don't ever install it.

Create a new user account and see how things behave in it.

---

### Post by charonred on 2010-06-10
tried that, but same problem no printers, video etc - thing made changes to gnome, metacity, gimp, totem and a pile of other apps.

I even tried booting to the previous kernel, but of course that made no difference

---

### Post by charonred on 2010-06-10
Is there a command I use to run the install CD again to repair an existing 10.04 installation?

---

### Post by anand_30 on 2010-06-10
Have you tried Recovery Mode?

In recovery mode do "Repair broken packages".

This might help.

---

### Post by charonred on 2010-06-10
I've probably seen it somewhere, but how do I do that ?

---

### Post by anand_30 on 2010-06-10
> **charonred said:**
> I've probably seen it somewhere, but how do I do that ?

Hold shiftkey down during boot,it will show you various options including Recovery mode.

---

### Post by charonred on 2010-06-10
Thanks, just tried that, but packages aren't 'broken' as such, just changed by the install of easy-ocr; so seems like I have to do a clean install in the morning to get things working again.

Once done I'll make a image of the install and drop it on an external 1Tb as a safeguard for the future, and keep updating ... what a pain in the proverbial.

---

### Post by nalin4linux77 on 2010-06-10
sir 
 i am nalin4linux77,i have compiled this easy-ocr for my father who is blind. since then he has been scanning and reading profusely for he is an avid reader.

to help other visually impaird people who has no capacity to purchase propritory softwares i uploaded it i have tested it more than ten systems(lucid). and i have received no problems reporting from any of my friendes 


there is no possibility for the crash you reported, for i have made a few changes in the gconf and 99% of this package is deb packages which is already in lucid repository.
:sad:
[U][I][B][COLOR=Red]there is a remote posibility that it can come into conflict with compize fussion. and you can do away with 
compize fussion [COLOR=Lime]([COLOR=SeaGreen]go to system > preference > appearance > visual effect page > select non [/COLOR][/COLOR][/COLOR][/B][/I][/U][COLOR=SeaGreen]
[/COLOR]

a request easy-ocr is a jenuine effort to make the already existing ocr engines userfriendly so 
please find its glory by installing in some other system(lucid) and save it from misproppaganda

easy-ocr [http://code.google.com/p/easy-ocr/](http://code.google.com/p/easy-ocr/)

---

### Post by dnguyen1963 on 2010-06-10
> **charonred said:**
> Thanks, just tried that, but packages aren't 'broken' as such, just changed by the install of easy-ocr; so seems like I have to do a clean install in the morning to get things working again.

Once done I'll make a image of the install and drop it on an external 1Tb as a safeguard for the future, and keep updating ... what a pain in the proverbial.

Have you tried to remove/unistall the easy-ocr package by Synaptic?

---

### Post by charonred on 2010-06-10
nalin4linux77
 - I appreciate the intention of what you complied, and congratulate you on your effort. However I was looking for something that would allow me to scan text documents so that I could then copy n paste into Open Office etc - maybe a warning that easy-ocr is not intended for that use.

I set visual effects to none, but it made no difference, playback of video has sound only; also, I happen to like full desktop effects.

In any event it still removed all printer options except 'print to file' - the option to add a printer is 'grayed' out, which has effectively crippled my system. I use these 3 printers daily - Epson CX5300 MFP/scanner, Epson R310 Photo & CD, and Lexmark E230 mono laser; but now can't use or add any of them.



dnguyen1963
 - not listed in Synaptic or software center, so there doesn't appear to be a way to reverse it



It seems the only option I have is to clean install along side my existing Lucid 10.04 (32bit) and use the existing until I have the new install up n running with all my normal apps installed with their relevant data backups.

And I think I'll try the 64bit version this time, but will leave it to the working weeks ends tonight so I have the weekend to sort things out; then all I have to do is a little catchup printing still a pain though.

---

