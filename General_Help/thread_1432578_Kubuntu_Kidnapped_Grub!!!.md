---
title: "Kubuntu Kidnapped Grub!!!"
date: 2010-03-17
forum: General Help
---

### Post by Dulwithe on 2010-03-17
Okay, so, I installed Kubuntu in a free partition of my computer 30 minutes ago.

I play with lots of distros just to see what's happening with them.

So, this is the FIRST time a distro has installed grub without prompting me to choose defaults or to specify custom location and customize contents.

So, now, my main production machine can't boot me into my main OS right now - Mandriva 2010.  Although it shows up in the grub list, an error (something about 788 or 800x600 - obviously a resolution issue) comes up.

So, I can't even boot into Mandriva to get Mandriva's control centre to reinstall my grub.

Any help would be greatly appreciated.

Thanks.

D.

PS - Why does Kubuntu 9.10 install a text based grub...???  This is 2010 and I thought we were beyond that...  ;-(

---

### Post by zvacet on 2010-03-18
One of possible solution is to reinstall Mandriva grub and then add Kubuntu to it.

---

### Post by Dulwithe on 2010-03-18
> **zvacet said:**
> One of possible solution is to reinstall Mandriva grub and then add Kubuntu to it.

Yes, I COULD do that if I COULD boot into Mandriva, but I can't boot into Mandriva, because Kubuntu kidnapped grub...

---

### Post by zvacet on 2010-03-18
> Yes, I COULD do that if I COULD boot into Mandriva, but I can't boot into Mandriva, because Kubuntu kidnapped grub...

You need Mandriva install CD to do that.See [here.]("http://wiki.mandriva.com/en/Docs/Support/Emergencies")

---

### Post by kngofbuntu on 2010-03-18
> **Dulwithe said:**
> 
PS - Why does Kubuntu 9.10 install a text based grub...???  This is 2010 and I thought we were beyond that...  ;-(
could any1 tell me what actually is a text based grub

---

### Post by Chame_Wizard on 2010-03-18
I am also wondering!!!:P
Although,I have know GRUB for 3 years.:lolflag:

---

### Post by Bradtek on 2010-03-18
> Originally Posted by Dulwithe  View Post
PS - Why does Kubuntu 9.10 install a text based grub...??? This is 2010 and I thought we were beyond that... ;-(

Mabe the OP wants a pretty picture behind the text

---

### Post by OldAlgis on 2010-03-18
> **Dulwithe said:**
> 

PS - Why does Kubuntu 9.10 install a text based grub...???  This is 2010 and I thought we were beyond that...  ;-(

I think this is your first encounter with Grub 2 - welcome to a very different boot system! I suggest you look for Forum and wiki articles about Grub 2.

A good overview can be found in [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

HTH,

OldAl.

---

### Post by Dulwithe on 2010-03-19
> **Bradtek said:**
> Mabe the OP wants a pretty picture behind the text

Quite simply - yes!

Why should I have to use a text based, 1980's style DOS-looking bootloader when the technology exists (has existed for years) to have a really nice, slick-looking, bootloader?

Part of user experience of any product is the way it looks - clothes, cars, cell-phones, etc...

---

### Post by Dulwithe on 2010-03-19
> **OldAlgis said:**
> I think this is your first encounter with Grub 2 - welcome to a very different boot system! I suggest you look for Forum and wiki articles about Grub 2.

A good overview can be found in [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

HTH,

OldAl.

Nope, not my first encounter with Grub2, just my first encounter installing a linux distro that installed a bootloader without any prompting whatsoever.  

Although I am not a pro nor a linux guru, I know enough so that I usually install my main distro's bootloader on the MBR, and my sub-distros (special purpose distro's and trial distros) on their respective /root partitions, with a link from the main MBR grub to the sub-grubs.

I really find it surprising that Ubuntu/Kubuntu has 1) an install that kidnaps one's MBR with no prompting as DEFAULT (yeah, probably the alternate install CD has other options, but that is not clear as a new ubuntu user - or a "previous" ubuntu user as in fact I am), and 2) that (mentioned above) the grub menu is ugly text based.

And to explain more about the above "special purpose" distros, for example I use Sabayon for XBMC - really slick.  But I can't use Sabayon for my main distro because I find it too difficult to manage installing software that isn't in the repos.

---

### Post by Dulwithe on 2010-03-19
> **zvacet said:**
> You need Mandriva install CD to do that.See [here.]("http://wiki.mandriva.com/en/Docs/Support/Emergencies")

Thanks for the link!

---

### Post by kngofbuntu on 2010-03-20
> **Dulwithe said:**
> Nope, not my first encounter with Grub2, just my first encounter installing a linux distro that installed a bootloader without any prompting whatsoever.
well ubuntu main cd is for users new to _linux_
I generally use the mini.iso which gives all the options including to setup the root user


> 2) that (mentioned above) the grub menu is ugly text based.
For me grub2 was the most amazing addition to kamic
you can modify anything including the resolution,adding a background,text color,and anything you want....
Guess you still seem to be living in those times where you let  someone else do the customizing for you  (An idea on which microsoft survives with end users.Loved to see its desperation when it started giving free installations through msdnaa to attract developers)

---

### Post by OldAlgis on 2010-03-20
[QUOTEDulwithe;8992447]Nope, not my first encounter with Grub2, just my first encounter installing a linux distro that installed a bootloader without any prompting whatsoever.  
[/QUOTE]

I suspect you feel offended at the suggestion that this is your first encounter with grub2. No offence was intended, I assure you. 

You need not feel alone having problems with grub2 - it is very different from the grub, now referred to as grub-legacy.

Since 9.10, ubuntu and kubuntu come with grub2 and the behaviour that you describe. OpenSuse 11.2 also comes with grub2 (though the ubuntu description of grub2  says the opposite).

Many people are unhappy with the change, mainly because we all got used to the grub-legacy!

You may as well relax about it all - no escape from it, not for a long time, anyway.  Also, notice that grub2 is still under a heavy development (you probably use grub 2 v 1.97 beta x, where x is an integer somewhere in the range of 1 to 9).

Good luck with it, anyway!

---

### Post by Dulwithe on 2010-03-22
> **kngofbuntu said:**
> 
Guess you still seem to be living in those times where you let  someone else do the customizing for you

That's quite condescending, in fact.

And truth is, no - I do not let others "do the customizing" for me.  I use kde (have tried gnome, xfce, enlightenment, and many other minor windows managers), but just from a window management and desktop management perspective (forget now, that kde is also now kde-sc - software compendium - which is a unified group of programs for a desktop user) KDE (especially kde4) allows me to easily put what I want, where I want, when I want, how I want, and allows me to have my window management how I want (shade/unshade on mouse scrolls, allow resizing of maximized windows, etc, etc, etc).

Everytime I install a distro, I customize my workspace to my needs.

Now, for a distro management team to realease a disto in 2009/2010 with a text based grub is a huge oversight.  And for users and devs to say, similar to your attitude, that you can edit it as you like - well this is true, but indulge me as I make a comparison.

Imagine a car company that makes a car and doesn't install any fabric on the seats nor do they paint the car stating, "The owner is going to want to put his/her own choice of fabric and color on the car anyway, so why should we do it?"

Your statement is a true sign of one of the main reasons why linux is not being adopted in greater mass - because many developers don't realize that users want to USE - not to fiddle and squiddle with "under-the-hood" style maintenance and finishing touches.

Seriously, you shouldn't assume things about a person because that makes an "***" out of "u" and "me".

I have enough to do without also trying to make a grub menu pretty.

---

### Post by Dulwithe on 2010-03-22
> **OldAlgis said:**
> 
You need not feel alone having problems with grub2

I never stated I have a problem with grub2.

The only problem is with ubuntu/kubuntu standard install cd's that:

1) kidnap grub with no option for choosing grub details during install, and 2) less of an issue, but ubuntu/kubuntu's grub menu looks like 1980's era DOS.  (Barf!)

Never, never stated that grub2 was an issue!

---

### Post by Dulwithe on 2010-03-22
SOLVED:

I solved the problem.

Installed the most recent Mepis Linux (RC2) and deleted kubuntu.

It, as with all other distros I have installed over my last 10 years with linux, allows for the user/installer to state where to install grub, and some other grub options.

And, wonderfully enough, Mepis's grub install allowed direct boot of my Mandriva partition!  ie: 1) kubuntu's grub showed an entry for my mandriva, but wouldn't boot it, and 2) Mepis's grub, better than Mandriva's or Suse's, allowed direct booting into all installed distros.

To explain (2) further, I have in the past installed a distro's grub onto the /root menu of the distro's own partition, and editted my computer's main grub to do a bootloader +1 (I think this is the correct code) to link the main grub to the secondary grub(s).  But, Mepis's grub install was the first to allow me to forgo this step and directly boot a distro without the need for the bootloader +1.

Good Job, Mepis Team!!!

Oh, and it looks up-to-date as well!!

Sweet!

---

### Post by jsriz on 2010-03-23
> **Dulwithe said:**
> That's quite condescending, in fact.

And truth is, no - I do not let others "do the customizing" for me.  I use kde (have tried gnome, xfce, enlightenment, and many other minor windows managers), but just from a window management and desktop management perspective (forget now, that kde is also now kde-sc - software compendium - which is a unified group of programs for a desktop user) KDE (especially kde4) allows me to easily put what I want, where I want, when I want, how I want, and allows me to have my window management how I want (shade/unshade on mouse scrolls, allow resizing of maximized windows, etc, etc, etc).

Everytime I install a distro, I customize my workspace to my needs.

Now, for a distro management team to realease a disto in 2009/2010 with a text based grub is a huge oversight.  And for users and devs to say, similar to your attitude, that you can edit it as you like - well this is true, but indulge me as I make a comparison.

Imagine a car company that makes a car and doesn't install any fabric on the seats nor do they paint the car stating, "The owner is going to want to put his/her own choice of fabric and color on the car anyway, so why should we do it?"

Your statement is a true sign of one of the main reasons why linux is not being adopted in greater mass - because many developers don't realize that users want to USE - not to fiddle and squiddle with "under-the-hood" style maintenance and finishing touches.

I have enough to do without also trying to make a grub menu pretty.

First of there is nothing such as text based grub(first i thought i was ignorant but now i changed my mind)
its just same old thing with a pic and some thrown in gfx....
well as for your comparison if i was getting a high powered supercar for free i would not really care what package or looks i get it in........
Yes that is a reason why end users don't prefer linux but there are many linux distros which are aimed at end users, not free and have everything preconfigured for their systems.
when i boot up my laptop i dont want to publicize the development team of a os i run but want it to show up my brand name its not about making it pretty,its about showing off "me".
Ubuntu is the linux distro with maximum number of users and mostly linux newbies, 
Even then it decides to release grub2 (something that is still in beta stage of development) with its main release this only shows that the development team team is keen on entrusting  more power and future proof material to the user.
you can look for yourself the plans and improvements planned for the next LTS release......
This world is filled with options ,happy to know that you found out a alternative for yourself.

Hope I have not offended you in any way.

---

### Post by kngofbuntu on 2010-03-23
Sorry if i have seemed too bossy with my words I am not quite good at persuading someone onto my point.
more or less the repost of the above for everything else.....

---

