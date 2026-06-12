---
title: "GUI grub2 editor??"
date: 2009-12-05
forum: General Help
---

### Post by leopards on 2009-12-05
Does anyone have any idea when or if there will be a GUI grub2 editor? I would really like to remove extraneous entries and move my XP dual boot up to second from the top for those very rare occasions when I am forced to use it! I really miss the grub editor that was available for grub 1, I even got pretty good at hand editing the grub menu list after one incident of being forced back the the CLI by a kernel update! :D

---

### Post by Chriske on 2009-12-05
Me too! :)

---

### Post by leopards on 2009-12-05
Well I followed the advice in another post and did a complete remove of 2.6.31.14 kernel in Synaptic and did a sudo update-grub2 then rebooted and kernel .14 still showed up in the grub menu and it actually booted into it when I chose it! What the heck!! How can it boot into a kernel that has been completely removed???? Why is it still in the menu when it has supposedly been removed??? :confused:

---

### Post by leopards on 2009-12-05
OK, followed bad advice! search for and removal of linux-header 2.6.31.14 does nothing without removal of linux-image 2.6.31.14, once the linux-image is removed, then that kernel stops showing up in the grub 2 menu!!
Still would like to know how to move the very seldom used XP pro entry to the number 2 slot in the lineup!!

---

### Post by cariboo on 2009-12-05
You can use startupmanger to set the boot order, that's about the only thing it will do until a new version that supports grub2 is released. The developer is hard at work updating it. Startupmanager is in the repositories.

---

### Post by Chriske on 2009-12-06
Thanks for that info. I'll look forward to seeing that and wait patiently. :D

---

### Post by Zoot7 on 2009-12-06
A GUI editor for Grub 2 is much needed given the pointless complexity it introduces IMO.

---

### Post by pieguy on 2009-12-06
Moving to grub2 this earlier was stuuuupid.  Grub2 isnt even fraking done.  There should be a option to download 9.10 with grub or grub2, you guys would see which one people would be using, instead you saddle us with this siht.

---

### Post by ranch hand on 2009-12-06
If you read the link in my sig you will have a lot more info on grub2.

You should realize, too, that while we are waiting for the final Ubuntu version of grub1.97, it was released last month in the final grub1.97.  We are using grub1.97beta4.

This link is in my post in the sig link;

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

It will guide you to using grub0.97 (no longer supported by the grub folks).

Another thing to keep in mind is that when grub-legacy came out it was about as popular as a turd in the punch bowl.

---

### Post by oldfred on 2009-12-06
Even with old grub you could not put the windows entry right after the first Ubuntu entry as that would be inside the automagic area and would be overwritten with the next update.

New grub has added a lot of features but yes somethings are not quite as complete. I believe it finds other operating systems much better. It is safer for a user to edit as if you messed up menu.lst you could not boot at all. You can still add custom entries in 40_custom or you own custom files. And ranch hand, drs305 and others had tried many things and documented them for us.

---

### Post by leopards on 2009-12-06
> **cariboo907 said:**
> You can use startupmanger to set the boot order, that's about the only thing it will do until a new version that supports grub2 is released. The developer is hard at work updating it. Startupmanager is in the repositories.
Startupmanager in Karmik doesn't offer this option, only which one is set as default. It also does offer the option of how many kernels to show in the menu anymore either!

---

### Post by brookie on 2009-12-06
[quote=Another thing to keep in mind is that when grub-legacy came out it was about as popular as a turd in the punch bowl.[/quote]

That's pretty dang funny! LOL :)

---

### Post by leopards on 2009-12-06
> **oldfred said:**
> Even with old grub you could not put the windows entry right after the first Ubuntu entry as that would be inside the automagic area and would be overwritten with the next update.

New grub has added a lot of features but yes somethings are not quite as complete. I believe it finds other operating systems much better. It is safer for a user to edit as if you messed up menu.lst you could not boot at all. You can still add custom entries in 40_custom or you own custom files. And ranch hand, drs305 and others had tried many things and documented them for us.
Don't know anything about Automagic zone, but my XP Pro was in the second slot for over 2 years, till the move to Grub2! menu.lst could be modified by hand from the command line, or with a LiveCD if you messed it up as I did a couple of time when I first tried to edit it! with Grub2 it seems you need to be an actual programmer to be able to change anything! Way too complicated for a non-programmer like me! It's usable as is (as long as nothing goes wrong) Guess I will have to live with the small inconvenience of XP Pro being at the bottom of the list till someone writes a GUI editor for the darned thing! Not going to attempt to make changes that will lock me out of my system with no easy way to get back in other than a re-install!

---

### Post by ranch hand on 2009-12-06
If you read my post (link in sig), you will find how to have a custom menu.

You will also find a link to a great How To on how to revert to grub-legacy.

You should keep in mind that grub-legacy is no longer supported by anyone.

---

### Post by Zoot7 on 2009-12-06
> **pieguy said:**
> Moving to grub2 this earlier was stuuuupid.  Grub2 isnt even fraking done.  There should be a option to download 9.10 with grub or grub2
You can install Grub Legacy pretty easily after installing Karmic. 
But yeah moving to Grub 2 was a bit too ambitious, the current version used in Karmic (1.97 Beta 4) doesn't really inspire confidence.

---

### Post by ranch hand on 2009-12-06
> **Zoot7 said:**
> You can install Grub Legacy pretty easily after installing Karmic. 
But yeah moving to Grub 2 was a bit too ambitious, the current version used in Karmic (1.97 Beta 4) doesn't really inspire confidence.
I am not sure why you say that.  I already have grub2 so that it is easier to use than grub-legacy (I have a long time love affair with grub-legacy).

Grub2 is different and there is a learning curve.

Os-prober has been a sore spot in grub-legacy and it is some improved in grub2.  It needs a lot more work (this is not a grub project but obviously a dependency).

Debian based OS' and MS OS' seem handled very well.  RPM OS' are a little rough but you can generally fix them with a custom menu.

A custom menu is what every one should use anyway as all your Debian based OS' can use the symbolic menu entry and never need editing for kernel changes.

That ability, alone, to me, makes grub2 vastly better than grub-legacy.

---

### Post by Zoot7 on 2009-12-06
> **ranch hand said:**
> I am not sure why you say that.  I already have grub2 so that it is easier to use than grub-legacy (I have a long time love affair with grub-legacy).

Grub2 is different and there is a learning curve.

Os-prober has been a sore spot in grub-legacy and it is some improved in grub2.  It needs a lot more work (this is not a grub project but obviously a dependency).

Debian based OS' and MS OS' seem handled very well.  RPM OS' are a little rough but you can generally fix them with a custom menu.

A custom menu is what every one should use anyway as all your Debian based OS' can use the symbolic menu entry and never need editing for kernel changes.

That ability, alone, to me, makes grub2 vastly better than grub-legacy.
It is nifty that a simple sudo update-grub finds all your OS's and sets them up accordingly.
But it does add needless complexity IMO, Grub 1 was quite easy to manage, a simple edit of menu.lst would suffice and it wasn't too hard to do. But to manually add stuff to Grub 2 is a chore to say the least.
Also shipping a Stable release with something as critical as a bootloader in Beta isn't really the thing to do, granted that version works fine booting Ubuntu along with openSUSE and XP for me.

All that said though, Grub 2 does have promise, the scripting support alone should pave the way towards much more advanced features in the future, but keeping it more simple to configure would have been better IMO.

---

### Post by mikewhatever on 2009-12-06
> **pieguy said:**
> Moving to grub2 this earlier was stuuuupid.  Grub2 isnt even fraking done.  There should be a option to download 9.10 with grub or grub2, you guys would see which one people would be using, instead you saddle us with this siht.

Well, if that's what you call it, stop using it. Ubuntu has a number of other supported releases with GRUB1, and I'd recommend you use Jaunty or Hardy. You can also use another distro. What's really stupid is this utterly ridiculous whining about anything and everything some think they want.

---

### Post by ranch hand on 2009-12-06
Well, I have to admit that I have used grub2 since 9.10 Alpha2 when it was added.  It was rough.  It really is not that hard to manipulate.

I suspect that folks fresh to Linux will have an easier time than those of us who are used to grub-legacy.  We had some very interesting discussions on that in the testing forum and wanted a sticky in the absolute Beginners Forum (Grub Basics by drs305 would be my pick).

Could have prevented a lot of "where in tarnation is my menu.lst posts.

I am glad we are still on 1.97beta4.  The 1.97 final came out early (the 4th?) in November.  The Ubuntu devs have not done their magic on it yet (I guess).

I know that we started with 1.96 (final) in 9.10alpha2, as worked over for Ubuntu.  It did not do a lot of things it should.  I have PhatDebian on my main drive and boot from it.  I installed grub1.96 from the Debian repo on it.  It does fine for the 4 OS' on that drive.  I was booting from a 9.04 respin with grub-legacy.  All 4 of those OS' are grub-legacy by default.  I can't boot from Lenny because Lenny doesn't have ext4 support.  But the PhatDebian uses the 2.6.30 kernel and does fine with Lenny, Jaunty and Stoner Edittion1.0 booting from grub2.

All of them are using the symbolic menu entry and I have just had a kernel update in both Jaunty and SE1.0 without having to do a thing to the menu in PhatDebian.

I don't know if you can tell but I am becoming quite a fon of grub2.

That said, I am probably more aware of the short comings of grub2 than most users so I can see why a lot of folks just don't like it.

Anyone reverting to grub-legacy should use kansasnoob's How To when doing it.  There are a couple of pit falls you want to avoid so that you don't end up with an unusable grub-legacy.  The need to remove os-prober is not intuitive.

---

### Post by matty83 on 2010-03-02
> **pieguy said:**
> Moving to grub2 this earlier was stuuuupid.  Grub2 isnt even fraking done.  There should be a option to download 9.10 with grub or grub2, you guys would see which one people would be using, instead you saddle us with this siht.
yep grub 2 is hailed by all the geeks but for all of use who don't what to spend 20 years messing around with the programming code we'd like to see kgrub2editor or ggrub2editor makes life so much easier and although it saddens me to say it if the is to be no gui grub 2 editor im abbandoning ubuntu perminatly.

---

### Post by Ozymandias_117 on 2010-03-02
I think grub2 will be much better than grub... when it's done >.> They decided to adopt it too early in my opinion. You can't even put an encrypted password on it yet. (At least as of a few months ago)

---

### Post by uRock on 2010-03-02
It doesn't get much easier than ```
sudo update-grub
``` who needs a GUI to run that command?

---

### Post by Ozymandias_117 on 2010-03-02
> **iRock said:**
> It doesn't get much easier than ```
sudo update-grub
``` who needs a GUI to run that command?

You still have to modify the files manually first, before you can run that, which can be difficult for new users.

---

### Post by uRock on 2010-03-02
> **Ozymandias_117 said:**
> You still have to modify the files manually first, before you can run that, which can be difficult for new users.
I have run that many of times without configuring anything. I have added OSes and removed them with no problems.

I am sure one would have to edit the config files to do other stuff, but I only do the basics.

---

### Post by alfem on 2010-04-27
[QUOTE=leopards;8443228]Does anyone have any idea when or if there will be a GUI grub2 editor? /QUOTE]

You can test this brand new Grub2 editor:

[https://launchpad.net/grubaker2]("https://launchpad.net/grubaker2")

It is in beta stage, so be careful!

---

### Post by balaram on 2010-04-27
I find Grub2 extremely annoying. It seems like I spend a ridiculous amount of time trying to get it to work properly.
 
Most recent problem - Windows menu entry has completely disappeared. Os-prober doesn't see it. Have now spent two hours reading documentation and trying countless fixes - none of which have worked. This sucks, at least Grub legacy took maybe 90 minutes to fully understand and implement. Grub2 is too complex, like using a chainsaw to cut butter. 

Is this a just a Ubuntu problem or does Grub2 have issues with other Linux OS?
Would be willing to go with another distro just to get away from it.

---

### Post by oldfred on 2010-04-28
With old grub we often had to manually add windows and virtually all other operating systems to menu.lst. 

With grub2 if the windows is bootable osprober will find it. If it is not finding it, then it almost always is a windows issue.

since it is not related to this thread - balaram post this to a new thread.
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by jastonas on 2010-05-08
> **alfem said:**
> [QUOTE=leopards;8443228]Does anyone have any idea when or if there will be a GUI grub2 editor? /QUOTE]

You can test this brand new Grub2 editor:

[https://launchpad.net/grubaker2]("https://launchpad.net/grubaker2")

It is in beta stage, so be careful!

Does this seem to work for you??

---

### Post by kiddieland on 2011-06-03
> **leopards said:**
> Don't know anything about Automagic zone, but my XP Pro was in the second slot for over 2 years, till the move to Grub2! menu.lst could be modified by hand from the command line, or with a LiveCD if you messed it up as I did a couple of time when I first tried to edit it! with Grub2 it seems you need to be an actual programmer to be able to change anything! Way too complicated for a non-programmer like me! It's usable as is (as long as nothing goes wrong) Guess I will have to live with the small inconvenience of XP Pro being at the bottom of the list till someone writes a GUI editor for the darned thing! Not going to attempt to make changes that will lock me out of my system with no easy way to get back in other than a re-install!

Hey guys, I found an easy workaround to the boot order

(OPTIONAL)First paste this code into the terminal
```
gedit /etc/grub.d/README 
```Even if you didn't paste the code, you can see that the numbers at the beginning determine what is done first when you run update-grub.

Thus, to make Windows XP the first in the grub2 menu, just run this command in the terminal

```
sudo mv 30_os-prober 08_os-prober
```And then run

```
sudo update-grub
```Voila, Windows XP option is at the top again :smile:   :biggrin:

---

### Post by Chriske on 2011-06-04
The GUI tool to edit GRUB2 is available - the excellent Grub Customizer.

Find it here:

[https://launchpad.net/grub-customizer](https://launchpad.net/grub-customizer)

:)

---

