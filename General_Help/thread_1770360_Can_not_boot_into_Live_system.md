---
title: "Can not boot into Live system"
date: 2011-05-29
forum: General Help
---

### Post by mastablasta on 2011-05-29
I am having trouble botoing into live system. Lubuntu 11.04 boots to command line. I am trying to boot from a CD at computer that is currently running Ubuntu and Xubuntu 10.04. 

I can see the dots on loading and also on shutdown but i can't start the X.

Computer is an Old compaq presario 731EA, S3 graphics card with 256 MB total ram (32MB goes to graphics card). I tried nomodeset but same thing happens.

any ideas why this is happening?

---

### Post by Rubi1200 on 2011-05-29
Hi,

Does it have to be Lubuntu?

I was going to suggest trying with the Ubuntu Alternate CD first and figure out if this is a graphics issue or something else.

---

### Post by mastablasta on 2011-05-29
yes it has to be Lubuntu :-P

So far computer has:
Ubuntu 10.04 and Xubuntu 10.04 (alongside) - installed.
I know that Mint 10 LXDE (based of Lubuntu 10.10 boots on it). i also know that Lubuntu 10.04 boots on it.

perhaps drivers for the graphics card were dropped?

---

### Post by dandnsmith on 2011-05-29
I suggest that you may be wasting your time trying to get a gui runnibg with 256MB of RAM.

---

### Post by MoebusNet on 2011-05-29
May I suggest Puppy Linux:

[http://www.puppylinux.com/about.htm](http://www.puppylinux.com/about.htm)

It runs quite well on older/low spec hardware. It works well as a Live CD/USB, but runs even faster installed to your hard drive.

---

### Post by Rubi1200 on 2011-05-29
Did you burn at the lowest speed and check the integrity (sorry for asking but sometimes we miss the obvious steps)?

I don't think the RAM would be an issue, but the graphics card might be.

Have you tried any other boot options other than nomodeset?

---

### Post by jerrrys on 2011-05-29
> **dandnsmith said:**
> I suggest that you may be wasting your time trying to get a gui runnibg with 256MB of RAM.

thought that whats lubuntu is all about.  anyhow, can you check your live cd on another box?

---

### Post by linuxinstalledfromhdd on 2011-05-29
Use Puppy Linux.

---

### Post by mastablasta on 2011-05-30
> **Rubi1200 said:**
> Did you burn at the lowest speed and check the integrity (sorry for asking but sometimes we miss the obvious steps)?

I burned at higher speed. nero checked data and verified it after the burn. i will check it with another programme in case nero is acting out again. but there is no error on screen. in fact i get a nice welcome to ubuntu message and some instructions on use of man command...
 
> 
Have you tried any other boot options other than nomodeset?
 
What should i try? acpi=off?
 
edit: just remembered that even on current install it wants me to use force=1 or upgrade BIOS (can't be upgraded more) but message goes away too fast to read. and there was no issues. 
> **jerrrys said:**
> thought that whats lubuntu is all about. anyhow, can you check your live cd on another box?
 
good idea - will try this as well.
 
> **linuxinstalledfromhdd said:**
> Use Puppy Linux.
 
No. wait, why? why would i want puppy linux? just because i am low on RAM? if Ubuntu 10.04 and 10.10 with GNOME work fine on it then so should Lubuntu. And i need the applications that Ubuntu has (such as Firefox, Thunderbird) and a few others. I know that there is a version of Puppy with Ubutnu repos, but again i dont' really like the way puppy works and if Ubuntu didn't work on this computer only then i would explore other options such as Slitaz, Peppermint, Chrunchbang and Puppy. But since previous version worked just fine) everyhting works out of the box) i am here looking for help to figure out why the latest one doesn't.
 
I would really like to see people read the posts before posting. or at least glance through them and get some key points (such as Ubuntu currently installed and works OK but got a little bit slower than on install - A.K.A. the Windows syndrome)
 
 
also 256 MB ram is plenty for Lubuntu that needs about 80-100 MB.

---

### Post by Rubi1200 on 2011-05-30
mastablasta,
yes you could try acpi=off and also possibly xforcevesa (which is also a bit heavy duty, but has worked in some cases).

I definitely think you need to consider burning at a lower speed and I have seen posts now and again where Nero was part of the problem in terms of burning the image to CD.

---

### Post by dandnsmith on 2011-05-30
I reread the posts, as suggested, and now suggested you do likewise.

You're not comparing like with like.
You can run versions of 10.04, and fail with 11.04 - all OS have the same problem (they require ever more resources).

Think about it!
I've had to cope with this one on several low memory systems (built from bits to hand at the time).

---

### Post by mastablasta on 2011-05-30
> **Rubi1200 said:**
> mastablasta,
yes you could try acpi=off and also possibly xforcevesa (which is also a bit heavy duty, but has worked in some cases).

Forcevesa would put it in"low graphics mode"? well i guess to see if it all works.
 
> 
I definitely think you need to consider burning at a lower speed and I have seen posts now and again where Nero was part of the problem in terms of burning the image to CD.
 
Interesting. Lately Nero has been acting strange (i am now more and more suspecting nero for this). But the strange behaviour was only on DVDs. So i already downloaded a couple of other burning software. It seems it is now time to install them. that's the reason i need to try out the CD on another computer...
 
i will post back when i figure out where the error is.
 
 
> **dandnsmith said:**
> I reread the posts, as suggested, and now suggested you do likewise.
 
You're not comparing like with like.
You can run versions of 10.04, and fail with 11.04 - all OS have the same problem (they require ever more resources).
 
Think about it!
I've had to cope with this one on several low memory systems (built from bits to hand at the time).
 
I know that. But Lubuntu needs 80-100MB ram so 224MB ram should be plenty for it. even in live session it won't go over 130 MB unless you start opening resource heavy applications. No, there is likely a graphics card issue or something is really wrong with the CD/image. too bad the nobook can't boot from USB...

---

### Post by mastablasta on 2011-05-30
ok so nothing worked.

CD is defiantelly good (works well on another computer).

Graphics n loading screen i see are not as they are supposed to be. It' sbasically Lubuntu 11.04 in text form with dots under it. no theme...

What i wonder now is if the processor is not compatible. processor is Athlon 4 1.2 Ghz. And support for i586 processor types was dropped in 11.04. which makes me wonder how is that going to help people with older computers to use the new OS...

but i think this one has K7 architecture (from internet base of knowledge...). graphics card i S3 i tried to get the chip number but wi-fi network started acting out.

anyway if someone has any other idea....

Otherwise i will stay with ubuntu 10.04 for the next two years. it seems batery is giving wrong readings or might be dying (so soon?!?!?!?!), in the mean time i need to start putting some money on the side for a new portable maschine. and windows 7 or 8 (for the other computer).

---

### Post by dandnsmith on 2011-05-31
> CD is defiantelly good (works well on another computer)
Unfortunately, that is no guarantee - I've had a number of instances where a home-generated CD will work on some devices but not others (it's usually an indication that either the writer or the writer is getting a bit marginal). Usuall, but not always, a professionally produced CD/DVD is a better guide.

I made the decision to avoid Ubuntu 10.10 until some of the reported problems were solved, as they would be likely to occur on my hardware, and also to not attempt later releases, as the different softwares in the graphics side of things would probably involve no end of trouble.

---

### Post by linuxinstalledfromhdd on 2011-05-31
> **mastablasta said:**
> ok so nothing worked.

CD is defiantelly good (works well on another computer).

Graphics n loading screen i see are not as they are supposed to be. It' sbasically Lubuntu 11.04 in text form with dots under it. no theme...

What i wonder now is if the processor is not compatible. processor is Athlon 4 1.2 Ghz. And support for i586 processor types was dropped in 11.04. which makes me wonder how is that going to help people with older computers to use the new OS...

but i think this one has K7 architecture (from internet base of knowledge...). graphics card i S3 i tried to get the chip number but wi-fi network started acting out.

anyway if someone has any other idea....

Otherwise i will stay with ubuntu 10.04 for the next two years. it seems batery is giving wrong readings or might be dying (so soon?!?!?!?!), in the mean time i need to start putting some money on the side for a new portable maschine. and windows 7 or 8 (for the other computer).

If I was running that system I would probably want to try crunchbang 9.04
and it really should fly with that.

---

### Post by mastablasta on 2011-05-31
> **dandnsmith said:**
> Unfortunately, that is no guarantee - I've had a number of instances where a home-generated CD will work on some devices but not others (it's usually an indication that either the writer or the writer is getting a bit marginal). Usuall, but not always, a professionally produced CD/DVD is a better guide.

 
aha! i will try it on yet another computer or burn a new one.
 
yeah i didn't plan to do upragdes. but on one i was "forced" due to continuous sound issues with LTS version. on this one i just heard that Lubuntu improved a lot since the 10.04  version. and i want to give it a try, possibly install it. 10.04 version didn't recognise battery propperly and Fn keys didn't work. it also had some other infancy issues that drove me to Ubuntu. 11.04 Lubuntu hopefully solved plenty of them.
 
 
 @inuxinstalledfromhdd - i know about others, but question is how compatible are they with this notebook and with new software. since Linux has this "great" idea of shared libraries a newer programme version can be incompatible with older OS version. while in windows you always get some backwards compatibility by software makers.
 
windows aside i am mor einterested in Slitaz, but i doubt configuring it would be as straight. another option i am considering is Debian stable LXDE.

---

### Post by mastablasta on 2011-06-20
i just gave it another go - this time with various OS i could boot. i even used the bootmanager to be able to boot from USB key and thus remove any CD burning error. the result is that:
 
Debian Live stable XFCE boots OK
Mint 11 XFCE boots ok (based on debian testing)
Crunchbang statler (base don debian stable) boots ok (very nice and very fast).
 
Lubuntu doesn't boot to GUI
Xubuntu doesn't boto to GUI
 
Both have splash screen in some low res with some strange looking fonts - will try to provide a pic and both end the boto in command line only (as described above).
 
What was changed? obviously support for the graphics card is still there as debian testing works fine. is there any way i can boto this propperly? or hsould i give up on the whole thing? 
 
currently i am running Ubuntu and Xubuntu (i added XFCE to Gnome) 10.04.

---

### Post by mastablasta on 2011-06-22
Bump!

---

### Post by mastablasta on 2011-06-27
Still unsloved and unable to boot into the live system.

---

### Post by mastablasta on 2011-06-30
Bump

---

### Post by Noob672 on 2011-07-13
Did you try

[FONT=Courier New]$ sudo lxdm[/FONT]

from the terminal?

---

### Post by mastablasta on 2011-07-15
well that works, but why is this necessary?

shouldnt the window manager load by itself?

also OFFTOPIC: these Ubuntu live disk could really use an .ogg file so users can test the sound.

---

### Post by mastablasta on 2011-07-19
bump!

---

