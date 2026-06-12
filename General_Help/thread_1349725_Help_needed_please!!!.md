---
title: "Help needed please!!!"
date: 2009-12-08
forum: General Help
---

### Post by Justin91 on 2009-12-08
ok...  SO...  I'm new at this whole computer savvy thing...  However I have learned a lot...
I've installed Ubuntu 7.1 on my machine.

My issue is I need help configuring the routing tables.
I have a Dynex dx-e402 wired router.

I'm trying to run an apache2 virtual host server from the machine.

---

### Post by hwttdz on 2009-12-08
Why 7.1, that reached it's end of life a long time ago.  If this is a fresh install maybe you'd want to get a newer version before setting up things like this.

What do you mean by configure routing tables?  Are you having a problem in particular?

---

### Post by Justin91 on 2009-12-09
> **hwttdz said:**
> Why 7.1

Cause its what my dad told me to put on the machine and use.  Honestly it doesn't seem to work too bad.

> **hwttdz said:**
> Are you having a problem in particular?

Uh....  yeah kinda.  I have no clue what i'm doing lol.
I have all of my settings set to default I think

---

### Post by derrick81787 on 2009-12-09
> **Justin91 said:**
> Cause its what my dad told me to put on the machine and use.  Honestly it doesn't seem to work too bad.

The current version is 9.10.  You should install it unless your dad has a VERY good reason not to do so.  It may just be that he installed that back in 2007 when it came out and liked it and didn't realize there was a new version.  Either way, you'd be missing out on 2 years of improvements and updated software if you went with the old version.  Not to mention the fact that older versions will be harder for the people on the forums to support when they are running the newer version themselves.

> Uh....  yeah kinda.  I have no clue what i'm doing lol.
I have all of my settings set to default I think

What I think hwttdz meant was, why are you messing with routing tables?  Are you trying to get your router to forward port 80 to your computer so that you can access whatever you have hosted on Apache?  If so, that's specific to your router, not Ubuntu.  Otherwise, you need to explain your problem better.

- Derrick

---

### Post by Justin91 on 2009-12-15
> **derrick81787 said:**
> The current version is 9.10.  You should install it unless your dad has a VERY good reason not to do so.  It may just be that he installed that back in 2007 when it came out and liked it...

Thats possible, but its what I'm using.  :P


> **derrick81787 said:**
>  What I think hwttdz meant was, why are you messing with routing tables?  Are you trying to get your router to forward port 80 to your computer so that you can access whatever you have hosted on Apache?  If so, that's specific to your router, not Ubuntu.  Otherwise, you need to explain your problem better.

Yea I guess that would be what I'm trying to do.  I'm not having any issues with the system.  I was just wondering if Ubuntu had anything to do with it?

All I know is that I am trying to host a virtual host server for sites A and B from one machine.  
The machine is running Ubuntu 7.1 and has apache2 installed on it. thats all I know.
My dad told me to "figure out routing tables" so we can get the sites working.  
So I guess that means forwarding port 80?

---

### Post by Justin91 on 2009-12-21
So...  am i just not getting anymore help with this or...?

---

### Post by audiomick on 2009-12-21
Hi.
I have know idea about that stuff, but here is a page to look at:
[http://ubuntuforums.org/showthread.php?t=1349725](http://ubuntuforums.org/showthread.php?t=1349725)

I would also highly recommend moving to 9.10. I have been using Ubuntu since 7.04, and the improvements have been massive.

---

### Post by HappyFeet on 2009-12-21
As was suggested, you should download the newest version of ubuntu before continuing on. Here it is ---> [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by Justin91 on 2009-12-21
> **HappyFeet said:**
> As was suggested, you should download the newest version of ubuntu before continuing on. Here it is ---> [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

I appreciate the suggestions, but i'm using 7.1 cause its what my boss told me to use.
I work for him so i kinda have to abide.

---

### Post by HappyFeet on 2009-12-21
> **Justin91 said:**
> I appreciate the suggestions, but i'm using 7.1 cause its what my boss told me to use.
I work for him so i kinda have to abide.

Tell him 7.10 is no longer supported and the kind and friendly people at the forums highly recommend a newer version.

---

### Post by Iowan on 2009-12-21
Does the machine have some resource limitations that prevent a newer version? I used Gutsy until earlier this year when I maxed out this machine @ 512M RAM. 
Is the machine a desktop or Server install? (not that it matters - other than GUI)
[Here]("http://httpd.apache.org/docs/2.0/vhosts/name-based.html") is an article on name-based virtual hosts - may not be what you're looking for, though.
Official support for Gutsy may have ended, but...

---

### Post by Justin91 on 2009-12-22
Well we kinda have the server set up on the machine and ready to go, which is why we cant change it, cause then we'd have to start all over.
Our only dilemma is this forwarding port 80?  I guess?

---

### Post by Justin91 on 2009-12-22
> **Iowan said:**
> Does the machine have some resource limitations that prevent a newer version? I used Gutsy until earlier this year when I maxed out this machine @ 512M RAM. 
Is the machine a desktop or Server install? (not that it matters - other than GUI)
[Here]("http://httpd.apache.org/docs/2.0/vhosts/name-based.html") is an article on name-based virtual hosts - may not be what you're looking for, though.
Official support for Gutsy may have ended, but...

Yea, I read that site while I was looking through things trying to figure it all out.

---

### Post by dasy2k1 on 2009-12-22
I should also point out that
7.1 IS NOT SUPPORTED
this means that any security problems (of which there are still a few) 
WILL NOT GET FIXED!

it is quite possible that there are horrendous exploits still in 7.1 that have been discovered by some cracker, if so thats all to their gain as there will be no effort even made to plug the hole.

perhaps you should be telling this to your boss before he entrusts it to a mission critical situation,
i certainly wouldn't.

if you insist on using massivly outdated software then im afraid there is very little help we can give.

---

### Post by houseworkshy on 2009-12-22
Actually you could update to 8.04 which is the long term support release, it is actually recomnended for large deployments.  Bear with me on this, I know that you don't have the authority to make this decision but you could point the machine owner at this thread.  There are several reasons why this is a good idea some of which have been mentioned above more can be found on the official Ubuntu site itself.  There are two extra reasons I'd suggest going up only one distribution, the applications have had a chance to catch up with the system so there is more available and, just as important in your case, you wouldn't need to reinstall everything as you would simply use the "dist upgrade" command and it would all be done automatically. I did use 7.10 but don't recall if there was a gui way of doing it or not but there is certainly a way of doing it in the terminal.  Don't remember what that is either but if you open a terminal and use the man command in front apt-get, or aptitude, or whatever it was then, the built in help will tell you ( man = manual ).  I should also point out for the sake of the owner who, I hope, you can get to read this that an upgrade is an improvement not a massive sea change, he will still have no problem finding his way around what is a nearly identical graphic user interphase.

---

### Post by Justin91 on 2009-12-22
Ok, so I checked it over with my boss and he told me to go ahead and upgrade to whatever.  
I'll let you know when I'm done with that.

---

### Post by houseworkshy on 2009-12-22
I forgot to mention that any of your work in 7.10 will still be there after and upgrade and that it will be far safer in a system which gets security updates.  In your first post you said that you are quite new to this.  I found this guide invaluabe when starting out
[http://www.ubuntupocketguide.com/download_main.html](http://www.ubuntupocketguide.com/download_main.html)
The pdf download is free.

---

### Post by Justin91 on 2009-12-23
[--]("https://help.ubuntu.com/community/BurningIsoHowto%5B/URL")[ _[COLOR=Blue]4 and 5[/COLOR]_ ]("https://help.ubuntu.com/community/BurningIsoHowto")[--]("https://help.ubuntu.com/community/BurningIsoHowto%5B/URL") Dont work for me?

It brings up a screen and asks me for the same things but i cant select a speed or anything.
All I can do is Help, Cancel, or Write.  
When I click write it burns too fast?  or it just doesnt burn?  idk, but it doesnt work right

The other way I tried instead of 1-3, I dragged the file from my desktop into the CD/DVD Creator, 
then the "Write to Disk" button became clickable.  ....no, its not a word but oh well lol.
So I do that and I get a different menu....
Brings up a "Write to Disk" menu, but it also instantly pops up a window in front saying:


> ----Create disc containing a single disc image file?----
-It appears that the disk, when created, will contain a
single disc image file.  Do you want to create a disk
from the contents of the image or the image file
inside?
-create from image-     ....  -cancel-   ...... -create with file-

Should I create from image or with file?

---

### Post by houseworkshy on 2009-12-23
[http://a5.video2.blip.tv/0500000158482/Dai-InfraRecorderBurningAnISO505.wmv?bri=0.2&brs=73](http://a5.video2.blip.tv/0500000158482/Dai-InfraRecorderBurningAnISO505.wmv?bri=0.2&brs=73)

---

### Post by Justin91 on 2009-12-28
ok, so i wrote the disc as an image, and it did the same thing that it did before, 
it didnt work.
So then I wrote it as a File.  It seemed to work, it actually took the time to write it?

But then I tried to boot my system from the CD and it didnt work.
My system like, idk, didnt recognize the content on the disc?

And now its reacting as though nothing was written to the disc...?

---

### Post by houseworkshy on 2010-01-05
Just a thought on your last post ( sorry it has been so long....Christams and new year, hope you have a good one by the way ).  Have you had a look at your boot disc priorities in bios.  To get in one taps a key during boot, the keys vary from pc to pc, delete is a common one, it usually tells you which key it is during the boot sequence. If not documentation which came with your machine or a search online will soon find it for you.
Be very cautious in bios as one can really mess things up down there.  The option you are looking for would be called something like "boot priority".  Remember exactly what it looks like before you change anything.  Make sure that your cd/dvd drive is checked for a boot record BEFORE your hard drive is.  If it isn't then whatever boot you have on the cd/dvd would be bypassed.  Which would be one explaination for the problem above.  To change it is a simple matter of using drop down menues and selecting.  The convention is that those at the top of the list are checked first.

---

