---
title: "Moving Client to Linux"
date: 2011-09-03
forum: General Help
---

### Post by Agg23 on 2011-09-03
I'm trying to move a client over to linux from XP.  She has a Toshiba 1005-S157 with 1.06GHz Celeron with 378MB of RAM (It's probably 384MB of RAM and XP is reporting it wrong :P).  Her needs are fairly simple...  Web browsing and Outlook support are all she really needs, with the occasional document editing in OpenOffice.

I was planning on hooking her up with Xubuntu or Lubuntu and Chrome/Firefox with Thunderbird for mail, but I would like to hear some input from here just in case.

Thanks,
agg23

---

### Post by Frogs Hair on 2011-09-03
Given the system information you have provided you have listed the best options already . Xubuntu recommends 512 mb of ram , so Lubuntu may be the best choice .

---

### Post by Agg23 on 2011-09-03
> **Frogs Hair said:**
> Xubuntu recommends 512 mb of ram , so Lubuntu may be the best choice .

Do you think it would be difficult to move from XP/Windows 7 to LXDE (I wouldn't know as I have only used GNOME for my XServer windows manager)?

---

### Post by JC Cheloven on 2011-09-03
> **Agg23 said:**
> Do you think it would be difficult to move from XP/Windows 7 to LXDE (I wouldn't know as I have only used GNOME for my XServer windows manager)?
In fact many people finds the lubuntu desktop similar to windows98 one, so I think it's not a problem. EDIT: I mean,not more of a problem than moving him to any other linux desktop environment.
I use lubuntu lately and I like its simplicity. Please come back if you need some guidance to help your friend/client (in fact, I'd suggest to install it youself in a virtual machine first -better than adding the lubuntu desktop to your current install- so you can jugde by your own).

oh... and remember [don't preach, mention]("http://ubuntuforums.org/showthread.php?t=865750"). Trying to "convert" someone who had no problems so far, may result in a self-defeating attempt.

Cheers
JC

---

### Post by Frogs Hair on 2011-09-03
That depends on the user , If the person is expecting something Windows like it may be a surprise . If the person is prepared to learn something new it is not a problem . I suggest running from the live disk so the user can see what Lubuntu is like before committing to an installation.

---

### Post by Agg23 on 2011-09-03
> **Frogs Hair said:**
> I suggest running from the live disk so the user can see what Lubuntu is like before committing to an installation.

I don't think that is a particularly available option, with only 384MBs of RAM  :)

---

### Post by whatthefunk on 2011-09-03
I use Lubuntu and love it.  I think that LXDE is very simple to figure out...I dont think she'll have to many problems.

OpenOffice will be slow on that computer...  Lubuntu comes with Abiword, which honestly is not my favorite word program.  What kind of documents does she need to edit?  Abiword doesnt do .doc extensions in a very good way....

---

### Post by Agg23 on 2011-09-03
> **whatthefunk said:**
> Abiword doesnt do .doc extensions in a very good way....

Exactly the problem...  It would need .doc and .docx

---

### Post by whatthefunk on 2011-09-03
Well, Abiword does save things as .doc and .docx, but they arent true .doc files.  What it does is saves the files as .rtf files and then gives this a .doc extension.  It works for some things, but if she intends to use the computer to do work at home and has to modify documents in both Abiword and Word, she will soon run into formatting issues.

---

### Post by lykwydchykyn on 2011-09-04
If the computer has an old version of MS office, those tend to run well in WINE -- I couldn't say if it'll run better than OpenOffice, but it might be worth comparing.

When you say "outlook support" -- is she connecting to an exchange server, or just using Outlook (or Outlook express) for POP3?  Thunderbird would be find for the latter, but not the former.

---

### Post by Agg23 on 2011-09-04
> **lykwydchykyn said:**
> When you say "outlook support" -- is she connecting to an exchange server, or just using Outlook (or Outlook express) for POP3?  Thunderbird would be find for the latter, but not the former.

Ooh...  I believe it is Exchange (at least I would assume so working at a college).  I would have thought it supports Exchange, as Mozilla totes it as an Outlook replacement.

---

### Post by occams_beard on 2011-09-04
AFAIK, Thunderbird does NOT support exchange. My boss recently tried to switch to Linux, but could not find a suitable MS outlook replacement.

1.06GHz Celeron with 378MB of RAM 

Maybe it is just time she gets a new computer? I think pretty much anything is going to run like crap with those specs.

---

### Post by lykwydchykyn on 2011-09-04
> **Agg23 said:**
> Ooh...  I believe it is Exchange (at least I would assume so working at a college).  I would have thought it supports Exchange, as Mozilla totes it as an Outlook replacement.

Exchange isn't just a mail server; it's got calendaring and other groupware-type features.  I understand Evolution is supposed to cover a larger set of the features, but I can't vouch for that.

It's best to look at Exchange as a service unto itself, rather than classify it as "email".  Outlook is an Exchange client, and it needs to be replaced by an "exchange client" rather than just an email client.

> **occams_beard said:**
> 
1.06GHz Celeron with 378MB of RAM 

Maybe it is just time she gets a new computer? I think pretty much anything is going to run like crap with those specs.

You can do a lot with a lightweight Linux distro on a computer with those specs, but when it comes down to working with Microsoft document formats and groupware services, things just get hairy.  I can't imagine XP is all that usable on those specs, especially with SP3, antivirus, and a recent version of Office.  We upped our minimum spec for XP where I work to 2.4 GHz and 1 Gb of RAM.

So the choices are (1) keep working with XP, sluggishly; (2) Switch to a lightweight distro and accept the loss of some functionality; (3) get a new PC.

---

### Post by Agg23 on 2011-09-04
> **lykwydchykyn said:**
> Exchange isn't just a mail server; it's got calendaring and other groupware-type features.  I understand Evolution is supposed to cover a larger set of the features, but I can't vouch for that.

It's best to look at Exchange as a service unto itself, rather than classify it as "email".  Outlook is an Exchange client, and it needs to be replaced by an "exchange client" rather than just an email client.

I concur.  I knew that, but I thought that Thunderbird with Lightning would handle both Exchange Mail and Calendar.


> **lykwydchykyn said:**
> You can do a lot with a lightweight Linux distro on a computer with those specs, but when it comes down to working with Microsoft document formats and groupware services, things just get hairy.  I can't imagine XP is all that usable on those specs, especially with SP3, antivirus, and a recent version of Office.  We upped our minimum spec for XP where I work to 2.4 GHz and 1 Gb of RAM.

So the choices are (1) keep working with XP, sluggishly; (2) Switch to a lightweight distro and accept the loss of some functionality; (3) get a new PC.

The problem with getting a new PC is that she doesn't really want to pay too much.  She probably doesn't even want to pay $200 which would be a barebones DIY build...

---

### Post by JC Cheloven on 2011-09-04
> 
Originally Posted by Frogs Hair View Post
I suggest running from the live disk so the user can see what Lubuntu is like before committing to an installation.
> **Agg23 said:**
> I don't think that is a particularly available option, with only 384MBs of RAM  :)
 
It's not the case. You should be able to run a lubuntu live session with that. [Minimum is said to be 256]("https://wiki.ubuntu.com/Lubuntu/ReleaseNotes/NattyNarwhal").
I second the idea of showing her lubuntu before. Making clear that everything will be slower during the live session, of course.

To bad if she needs exchange in particular, no nice solution to that I'm aware of. But if not, the provided client sylpheed is fine. I didn't feel the need of instaling evolution or thunderbird, which I had used before.

---

### Post by whatthefunk on 2011-09-04
Theres no way the live cd will work on that.  I doubt the normal install cd will even work.  Youll probably have to use the alternate install iso.

---

### Post by Agg23 on 2011-09-04
> **whatthefunk said:**
> Theres no way the live cd will work on that.  I doubt the normal install cd will even work.  Youll probably have to use the alternate install iso.

The live CD for what?  Ubuntu?  I'm not putting Ubuntu on...

---

### Post by whatthefunk on 2011-09-04
Lubuntu.  The normal Live CD will probably not work with those specs.  I guess you could try it, but Ill bet Ill the money in my pocket (admittedly not much) that it wont run and if it does it will be too slow to be of any use.

---

### Post by JC Cheloven on 2011-09-04
Hi again Agg, in a second read of my [link above]("https://wiki.ubuntu.com/Lubuntu/ReleaseNotes/NattyNarwhal"), Whatthefunk could be right to a point: 

> To use the graphical installer from the live-cd, you need at least 256 MB of memory. You need to use the "Install Lubuntu" entry when you boot the Live-CD. 
This strictly means that you can install from the standard cd, but does not guarantee that this amount of ram (or 384 MB for that matter) will be enough to run a live session from this same cd.

I just ran a live lubuntu session to ckeck. The system reports about 200Mb memory used, buffers included. Problem is that some ram has to be used as cache as well...
Well, you don't loose anything giving it a try. If it initially works, don't open more than a single app at a time though ;)

---

### Post by sbraz on 2011-09-04
before starting a major operation like this, make sure that very old lappy has an harddrive without bad blocks (unfortunately it is very likely imho :( ). you can check that using **gsmartcontrol**.

i don't think it'll run so bad as it is, but that laptop could be maxxed to 512mb. i don't think you'll easily find a brand new sdr pc133 256mb module, but it's worth checking at your local hardware stores if they still have some junk around (for example, i do :) ).

---

### Post by whatthefunk on 2011-09-04
I have a laptop with 512 RAM....it wont run LiveCDs.  After about an hour of waiting, I managed to get to the Lubuntu desktop but when I moved the mouse, it took the computer about ten minutes to settle down again.  Really couldnt do anything.  Its worth a try though and blank CDs cost next to nothing.

---

### Post by occams_beard on 2011-09-04
> **Agg23 said:**
> I concur.  I knew that, but I thought that Thunderbird with Lightning would handle both Exchange Mail and Calendar.

The problem with getting a new PC is that she doesn't really want to pay too much.  She probably doesn't even want to pay $200 which would be a barebones DIY build...

Well, sometimes you can't have your cake and eat it too :P I bought a reasonably nice Acer laptop last year for $320 USD, with a dual core pentium and 3 GB of ram. You see those deals all the time if you look around.

Time is money, as they say, and sometimes it's more cost effective to buy something new than waste a bunch of time trying to make antique hardware work.

The problem with so called "light weight" distros, is that sure the window manager is lightweight, but the apps you have to run are not. Firefox, open office, etc would run like crap on something that old.

---

