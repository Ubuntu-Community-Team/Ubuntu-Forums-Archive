---
title: "Responses to Kubuntu Speed on Older Laptop"
date: 2006-03-03
forum: General Help
---

### Post by Cosmosis on 2006-03-03
Hi everyone,
This is my first post, and I should offer the caveat that I am a complete Linux newbie.  I've installed Kubuntu 5.10 on an older laptop, and have been enjoying the variety of software and the ultra-dependability of the OS.  However, the OS in general runs really slowly.  It takes a good 2-3 minutes to boot up, and generally the first time I open anything or access a menu, it takes a few seconds (between 5-10) - although after I open/access something once, it works almost immediately everytime afterward in that session.  My question is, is this slowness a facet of the OS itself, my laptops specs, or should I try a different, speedier distro better suited to an older laptop?
My general specs are:
Dell Inspiron 2500 (circa 2000) with Pentium 3 processors, 256 RAM, and 10 Gig Harddrive (40% up with the OS and software alone!).  Any responses or thoughts would be greatly appreciated!  Anyone else running Kubuntu on similar specs and finding it handling similarly?

---

### Post by gingermark on 2006-03-03
I think 4GB for the OS and unpacked software is relatively normal these days - a sign of the times.

I don't have a laptop, but ran Kubuntu on an 800MHz Celeron with 128MB RAM. It struggled, especially if left running for some time. I don't think KDE is particularly slow, but your specs are definitely at the lower end (dare I say minimum for it).

The wonderful thing about Linux is the choice that is out there. If you are looking for a light-weight environment, you don't have to choose another distro. In the repositories you will find many environments. XFCE is the most fully featured of these, but you can also try Window Maker (which I personally quite like from time to time), IceWM, Fluxbox, there are many.

Have a look at Kyral's "[Window Managers for Beginners]("http://ubuntuforums.org/showthread.php?t=87276")" for more info, experiment, and see if one meets your needs.

Also keep in mind your choice of applications you decide to use will determine speed - KOffice is lighter than OpenOffice.org for example.

---

### Post by Qrk on 2006-03-03
I've run Kubuntu and Ubuntu on things worse... and it can be painfull. 

Kubuntu uses more resources than Ubuntu, (specifically it uses more CPU, I've heard RAM is about the same) which may be your largest problem. Gnome can be run on older machines if you give them a Ram upgrade, but I haven't had as good of luck with KDE. 

But you would benifit from XFCE. Try Xubuntu (its called xubuntu-desktop in the repositories) and see if you notice a speed increase. Your speed problems may also be due to using the wrong x.org driver.

I wouldn't read too much into the bootup time. Linux in general is slow to boot, and Breezy is even slower. My desktop takes a good 1:30 to boot Breezy. The good news is that there is light coming at the end of that tunnel, as Dapper takes only 35 seconds to boot on my desktop.

---

### Post by aysiu on 2006-03-03
If you want to improve the performance of KDE (256 MB of RAM is modest, but not meager), do this ```
sudo apt-get update
sudo apt-get install kpersonalizer
kpersonalizer
``` and then choose fewer effects.

---

### Post by Cosmosis on 2006-03-04
Thanks for the help, Gingermark.  I checked out the forum link you provided and installed some new windows environments/managers.  It was fun trying them out (and seeing a bit of speed improvement on the XFCE), but I realized I prefer the default Kubuntu environment.  Now here's my NEW problem: I must have selected default or something by accident and changed my settings because now when I log-in and select "KDE" from the sessions manager, the Kubuntu GUI that loads looks like my old trusted version, but the menu/program options listed in the KMenu have changed (and even shows programs that never were listed before, like Abi Word Processor!)  Is there a way to get my old GUI/Configuration back?

---

### Post by Cosmosis on 2006-03-04
Thanks Qrk!  A couple of questions(and they are pretty basic, so please don't laugh): first, how would I find out whether or not I'm running the correct x.org driver?  Second, since I've only been using Breezy (5.10) since I installed it, when the new Dapper version is finally, fully released, will it install over my current system or will I have to do a fresh install; moreover, if it will install seamlessly into my current installation, will I see this speed increase?  Sorry for the silly question, but since I haven't yet had the joy of experiencing a Kubuntu version update, I'm still unsure exactly how it works.

---

### Post by moopere on 2006-03-04
[QUOTE=Qrk]I've run Kubuntu and Ubuntu on things worse... and it can be painfull. 

Kubuntu uses more resources than Ubuntu, (specifically it uses more CPU, I've heard RAM is about the same) which may be your largest problem. Gnome can be run on older machines if you give them a Ram upgrade, but I haven't had as good of luck with KDE. [/QUOTE]

I find that Kubuntu is far lighter and a lot more interactive (speedier) than Ubuntu right out of the box.  The previous post talks about kpersonalizer...good option, this will make it even faster if you tone down the eye candy a bit.

I've got to say, after a ton of testing on older boxes, there's really no comparison between Ubuntu (gnome) and Kubuntu (KDE), kde since about 3.2 has outstripped gnome in raw performance by a measureable amount.

[QUOTE=Qrk]But you would benifit from XFCE. Try Xubuntu (its called xubuntu-desktop in the repositories) and see if you notice a speed increase.[/QUOTE]

In general, I've found xfce to be about as responsive as gnome on CPU bound boxes (really old ones <600MHz)  If you have a bit more CPU but not much RAM then yes, I agree, xfce is a lot quicker, even a touch quicker than KDE.

XFCE used to be _really_ _really_ fast back in its 3.x days, but since going gtk in its v4.x incarnation, its suffering as is gnome due to something 'under the hood' which makes responsiveness and interaction woefull.

Cheers,
Craig

---

### Post by Cosmosis on 2006-03-04
That's a handy piece of software, aysiu!  Thanks for telling me about it.  It worked great, and things do seem to be running a little faster.

---

### Post by der_joachim on 2006-03-04
FWIW: [Here]("https://wiki.kubuntu.org/KubuntuOptimization")'s a Kubuntu optimization guide from the Kubuntu Wiki. 

Furthermore, there are some excellent guides in the HOWTO section of the forum on speeding up desktop. 

Good luck and have fun tweaking (it *is* fun ;))

---

### Post by aysiu on 2006-03-04
[QUOTE=Cosmosis]That's a handy piece of software, aysiu!  Thanks for telling me about it.  It worked great, and things do seem to be running a little faster.[/QUOTE] People are always slamming "wizards," and God knows there are many Windows "wizards" I hate, but kpersonalizer is magic.

---

### Post by reptil on 2006-03-04
hi .. i install ubuntu 5.10, at a compaq armada e500 to old, like a server without graphic interface, afther  i install xfce, and other thinks. i konw that i need some  prograns  more  but now.. this machine fly!!!! when it has win98 was very very slow...
tomorrow i wiil tay to configurate  with my domestic network...

reptil

---

### Post by junyah on 2006-10-05
I'm a newbie also.  I installed ubuntu dapper on my dell 2500.  I was having problems with every version of windows.. and i feared the dell had permanent brain damage or stroke.  I loaded the ubuntu on it and got the dell a cooling mat (two fans usb powered).  Now it has regained status as the second computer again.  Its been running pretty stable and no bsod and no crashes for almost two weeks.  It recognized my wifi card right away.. Praise Ubuntu Linux!   Dell Inspiron 2500 512 ram Dlink dwl g630

---

