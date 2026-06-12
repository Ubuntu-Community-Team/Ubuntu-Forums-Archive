---
title: "Weard boot process"
date: 2010-02-06
forum: General Help
---

### Post by soundofheaven on 2010-02-06
Hi guys,

recently I've been starting to use 9.10 and I have to say that the boot process including startup till the desktop loads is slow and weard-looking.

I have found the solution for the "slowness", but the boot process is switching between text-mode and graphics mode. I would really like to have only graphics which would fluidly turn into the desktop without any text-stuff in between.

Please help me, if anything can be done to make things more fluid and "graphic-only"..

Many thanks in advance!

---

### Post by warfacegod on 2010-02-06
First place to look is your BIOS. Set it to disable any messages or warnings.

---

### Post by soundofheaven on 2010-02-06
warfacegod: I checked it and everything is set to disabled. Plus I think that if it was something in the bios, it would show stuff also in 9.04 boot, but that one was fluid..can you think of anything else?

Thx for helping..

---

### Post by warfacegod on 2010-02-06
Try looking through here:

[http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub2]("http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub2")

Another way might be through Startup Manager:

```
 sudo apt-get install startupmanager
```

---

### Post by 23dornot23d on 2010-02-06
> **soundofheaven said:**
> warfacegod: I checked it and everything is set to disabled. Plus I think that if it was something in the bios, it would show stuff also in 9.04 boot, but that one was fluid..can you think of anything else?

Thx for helping..

Can you get a photo/vid of the problem when its booting up to show what is happening ... ?

is it just the drive information you see ? for a short time .....

---

### Post by soundofheaven on 2010-02-06
I'll record the whole process and post a youtube link when it'll be online..

---

### Post by 23dornot23d on 2010-02-06
Ok ..... 

I was wondering whether to do the same ..... as it  would change from day to day !!!

until I removed GDM .... but this may not be the solution you want .....

mine now boots with a MAndriva Grub and then into a KDM ..... Login screen .... link below ....
 

[http://www.youtube.com/watch?v=5KtO9R0pui0](http://www.youtube.com/watch?v=5KtO9R0pui0)


Still goes into Gnome ok and now looks a bit more professional  .... than it trying to re adjust the resolution every single time it booted up ......... 

(but alls well now) ..... I have a feeling yours may be doing the same as mine was ....

---

### Post by soundofheaven on 2010-02-06
I've been looking and this seems interesting - you think it might help? [http://ubuntuforums.org/showpost.php?p=8350408&postcount=2](http://ubuntuforums.org/showpost.php?p=8350408&postcount=2)

---

### Post by 23dornot23d on 2010-02-06
Nice one ..... that is exactly the problem that I was getting ..... thank you .....

thats why it keeps trying different resolutions out and was failing ......

Maybe the same problem here too ...... we will see ...... ;) 

good post soundofheaven .....

---

### Post by warfacegod on 2010-02-06
> **soundofheaven said:**
> I've been looking and this seems interesting - you think it might help? [http://ubuntuforums.org/showpost.php?p=8350408&postcount=2](http://ubuntuforums.org/showpost.php?p=8350408&postcount=2)

I tried doing something similar a few months ago and it wasn't pretty. I didn't use that thread though. Be careful and be sure you do everything properly.

---

### Post by soundofheaven on 2010-02-06
Yeah, I've heard, or better - read, about many people, who were fooling around with GDM and they couldn't boot to the os anymore..I think that this guy did it with the two methods described in the post..

I'll give it a shot and let you know how it went!

---

### Post by 23dornot23d on 2010-02-06
You just need the second option and you do not need to mess with anything else ....

**_Method #2 -- way easier:_**

So instead I chose to give that config file what it wants ... I created the sub-directory it wants so its paths are correct now. The commands I used for this:

 	Code:
 	cd /usr
sudo mkdir X11R6
cd X11R6
sudo ln -s /usr/bin bin

---

### Post by soundofheaven on 2010-02-06
I tried following the tutorial in that post, but I couldn't access the reppositories while being logged out of gnome. It is neccessary to have the internet connection because I have to type sudo apt-get install gdm-2.20 

How can I download reppositories from outside of gnome session? I use wireless connection btw...

Pls help:)

---

### Post by warfacegod on 2010-02-06
> **soundofheaven said:**
> I tried following the tutorial in that post, but I couldn't access the reppositories while being logged out of gnome. It is neccessary to have the internet connection because I have to type sudo apt-get install gdm-2.20 

How can I download reppositories from outside of gnome session? I use wireless connection btw...

Pls help:)

Yeah, there's the killer. I'm strictly wireless myself. It's why I haven't built Ubuntu from the minimal install. Using wireless, outside of GUI, can be a real hassle from what I gather. Search the forums for a way, if you find one let me know.

---

### Post by soundofheaven on 2010-02-06
Well I can use wired connection if that will work? I thought it is the same for wireless or wired..

---

### Post by warfacegod on 2010-02-06
> **soundofheaven said:**
> Well I can use wired connection if that will work? I thought it is the same for wireless or wired..

Yes, a wired connection should work from CLI. Give it a shot.

---

### Post by 23dornot23d on 2010-02-06
gdm2.0 should already be installed .... once you have done the mod it should boot up ok

for the commands I printed in my last post ..... 

you need to 

**cd /usr**

this puts you in the right directory .....

**sudo mkdir X11R6**

this makes the directory that might be missing ..... I found it was already there ,,,,

**cd X11R6**

this just changes into the directory

Then this should link the two places  ..... where the files are .... for the graphics ....

[B]sudo ln -s /usr/bin bin
[/B]
_______________________________________________________________________________________________________

 When you reboot hopefully it will load gdm ok ..... if its not been removed ...... thats
unless something else is wrong ...... did you do a vid or photo of whats happening ....
would still like to see what the boot situation was or is ......
______________________________________________________________________

This just re-installs gdm ...... did you remove it ? ....... 
(if not it should still be there ,,,,, and run ok) so you probably do not need this any way ....
**sudo apt-get install gdm-2.20 **

---

### Post by soundofheaven on 2010-02-06
I tried, following exactly what that guy said and everything went ok until i finaly rebooted...I ended up unable to boot with some wierd windows logos and garbled picture which eventually turned black and i could only hard-reset the computer...

I am writing this from my mobile phone and will have to reformat the computer tomorrow..

So THIS METHOD DOESNT WORK:)

---

### Post by warfacegod on 2010-02-06
No need to format. Try this first.

From the command line:

```
sudo apt-get purge gdm2.20

sudo apt-get install gdm
```

You'll need to connect it to the internet, of course.

---

### Post by 23dornot23d on 2010-02-06
If all that you have done is the four lines above ..... you cannot break it ....

if you want remove gdm2.2 and replace it with either gdm or kdm ...... these are the display managers ,,,,

it asks you which you want to run when you install gdm ...... choose gdm ......

**sudo apt-get remove gdm**2.2

then do .....

either this
**sudo apt-get install gdm**
or as I did this
**sudo apt-get install kdm**

and choose the one you want when its installing  .......

There is no need to reformat ..... 
(unless there are lots of other things wrong .....)

---

### Post by soundofheaven on 2010-02-07
Many many thanks for that:) I was used to windows, when you just had to reformat everything when things went so bad that Windows wouldn't load anymore - it was faster that way:) 

So I tried what you've said using the recovery console with networking and whoala, I'm back and guess what..I think that there was  no text-graphic changes during the boot process:) I'll try a few more times just to be sure, but i think it worked somehow:)

I love Ubuntu..

---

### Post by 23dornot23d on 2010-02-07
Great News ... well done another success ..... hope all goes well ... now ....

---

### Post by soundofheaven on 2010-02-07
Yep, it looks like everything is OK :) I'll keep my fingers crossed!

Thank you both for helping!

All best

---

