---
title: "Dual boot question"
date: 2012-05-18
forum: General Help
---

### Post by gopher38 on 2012-05-18
Hello,

I've got a strange dual boot question.  

I've got an HP D530 minitower that I'm dual booting with Lucid and XP Pro SP3.  95% of the time into Lucid, but I need XP occasionally for some work stuff.

Anyway, I had an old HD that I'd rescued from my dead iMac G3, and I decided to put it into the D530 as a second HD.  Works well with Lucid. No problems; my 2nd HD cranks along and all USB devices work as before.  On XP however, my wireless keyboard and mouse do not respond once I pass from grub over to XP.  If I unplug the 2nd HD, then the keyboard and mouse work again.

I figured maybe it had something to do with the 2nd HD pulling too much current, but - as I said - if I use the exact same config and boot into Lucid, it works fine.  It's not like the Ubuntu drivers could require less power, could they?

Anyway, if someone has a suggestion/explanation other than "drop xp", I'd love to hear it.  Thanks.

---

### Post by houseworkshy on 2012-05-18
I don't have the knowlage to answer your question, though I had something a little similar with a usb once ( I'd accidentially tied it into the bootloader which had ended up on the usb itself,  the fix was editing grub and moving it back to where it should be on an hd instead ).  It's possible that when xp was installed it's hardware autodetecting did all it should and it worked, then when something new was added the hardware map it had made no-longer fitted.  If so, and only if all else fails because I'm feeling in the dark really, one could try backing up everything in the xp, then reinstalling it ( with the new old drive sitting waiting to be found this time ).  One would then need to fix grub to show the linux systems again for the duel boot, via a live distro session probably.  

It's been a long time since I used xp, could probably give better advice on flint knapping.  Some experiments could be to play with the detect new hardware thing.  There was also an error log which could be handy; set it to log, force the error.  Reboot in the way windows can handle and then read the log.  Digging around in the hardware drivers could turn something up.  Not having mouse and keyboard it a bit of a limiter as otherwise one could look at the disc manager while the drive window found awkward was in ...., tricky one.   You could, when running lucid, install sysinfo and post the results of that as it could have something to do with the hd drive type ( sata, raid, scusy (?)  all that sort of thing ). Finding out why windows is upset whilst it's upset is the biggest problem here.  There are several rescue distros on distrowatch.com one of those might help to glean some info.  When I used xp installing it was never the end of it, one had to put in all sorts of extra drivers.  Perhaps something is missing?
If you can back up *everything* the easiest non techy way to sort it out that would almost certainly work is to start fresh, back up the lot, install xp first and then lucid.
Have you tried wine for the xp work stuff, if the progs you need worked in wine xp would ceace to be crucial.  One can also virtualise xp on a dynamically expanding virtual disc with virtual box.
This is actually a bump so don't do any of the above for a while, with luck an expert will amble past go "arrrrhhhh" at what I've posted and give you good advice instead.

---

### Post by GreatDanton on 2012-05-18
I don't know how to properly name that thing in English, but I have some kind of box where you can put your disk in. When you don't need Hard disk drive (in your case Linux), you just pull your box out of computer (no screwdriver needed), so there is only one disk in your computer (in your case Windows XP)). But when you need Linux you put your box back into the computer and use Linux. I really like that box because you can easily change Hard disk drives and also the operating systems on the same computer.

I hope you understand what I am trying to say, if not just ask again.

---

### Post by gopher38 on 2012-05-18
> **GreatDanton said:**
> I don't know how to properly name that thing in English, but I have some kind of box where you can put your disk in. When you don't need Hard disk drive (in your case Linux), you just pull your box out of computer (no screwdriver needed), so there is only one disk in your computer (in your case Windows XP)). But when you need Linux you put your box back into the computer and use Linux. I really like that box because you can easily change Hard disk drives and also the operating systems on the same computer.

I hope you understand what I am trying to say, if not just ask again.
I've got those external enclosures for 2.5 inch laptop HDs, but I don't want to buy a 3.5 enclosure.  Rather just mount it in the desktop.  Thanks for the suggestion though.

---

### Post by gopher38 on 2012-05-18
> **houseworkshy said:**
> I don't have the knowlage to answer your question, though I had something a little similar with a usb once ( I'd accidentially tied it into the bootloader which had ended up on the usb itself,  the fix was editing grub and moving it back to where it should be on an hd instead ).  It's possible that when xp was installed it's hardware autodetecting did all it should and it worked, then when something new was added the hardware map it had made no-longer fitted.  If so, and only if all else fails because I'm feeling in the dark really, one could try backing up everything in the xp, then reinstalling it ( with the new old drive sitting waiting to be found this time ).  ...

Thanks, that's a very good idea, but unfortunately I don't have the install disks any more.  Good thinking though.
> **houseworkshy said:**
> 
It's been a long time since I used xp, could probably give better advice on flint knapping.  Some experiments could be to play with the detect new hardware thing.  There was also an error log which could be handy; set it to log, force the error.  Reboot in the way windows can handle and then read the log.  Digging around in the hardware drivers could turn something up.  Not having mouse and keyboard it a bit of a limiter as otherwise one could look at the disc manager while the drive window found awkward was in ...., tricky one.   You could, when running lucid, install sysinfo and post the results of that as it could have something to do with the hd drive type ( sata, raid, scusy (?)  all that sort of thing ). Finding out why windows is upset whilst it's upset is the biggest problem here.  There are several rescue distros on distrowatch.com one of those might help to glean some info.  When I used xp installing it was never the end of it, one had to put in all sorts of extra drivers.  Perhaps something is missing?
If you can back up *everything* the easiest non techy way to sort it out that would almost certainly work is to start fresh, back up the lot, install xp first and then lucid.

You're over my head here.
> **houseworkshy said:**
> 
Have you tried wine for the xp work stuff, if the progs you need worked in wine xp would ceace to be crucial.  One can also virtualise xp on a dynamically expanding virtual disc with virtual box.
...
I like wine, but it doesn't work for everything I need.

Thanks for the great suggestions. I did have one idea of my own.  I thought maybe the fact that keyboard and mouse were wireless might be affecting the system, so I tried with a usb pair, but no luck.

---

### Post by houseworkshy on 2012-05-19
Not having the installation disks is a huge pain.  I've been through  that one when I didn't know better; getting a machine with xp was £60  cheaper if I didn't have the cd ... so I didn't and ended up having to  spend far too much time on maintainence, a friend told me that keeping  it running fast for five years, which I did, was pretty good going.  So I  splashed out on a Vista cd with the next machine which only lasted a  couple of months, I was offline at the time and it locked me out of my  own work on my own machine with my own legally owned and regestered copy  of the operating system.  I made the phone call which allowed me to use  the thing for another 29 days a couple of times but the second drive  which was supposed to be for learning about linux in my spare time had  had already become the system I relied on.  Now both drives are linux;  Vista and the motherboard driver disk it needed,  and a copy of nero,   and the bios driver disk, and the sound driver disk it also needed just  sit in the rack gathering dust.  
That was pure aside but it does remind me that you will need a couple of  extras to keep xp going.  I'm very out of date so there may be better  out there even so.   Get the sysinternal suit from the microsoft  website, the tools in there are so useful I was suprised they weren't  part of the operating system.  There was also one called regseeker (  from hoverdesk I think) which was essential, xp was not at all good at  cleaning it's regrestry so something else had to do it, without a reg  cleaning tool an xp install gets slower and slower.  All the anti  malware stuff is essential too if you take the thing online, the built  in stuff is rubbish.
You will probably need an unregestered disk; I've just looked online and  couldn't find one on microsoft but it seems that xp can still be  purchased elsewhere, and there is still some very limited support untill  April 2014 or one can get Vista and downgrade it. There are quite a lot  of sealed ones on Ebay, probably from retailers who couldn't shift them  before Vista, looks like you should be able to get XP proffesional for  $10 - 20.  The microsoft site doesn't have much info about xp anymore  but in their installing guide ( which assumes one has the original disk )  great emphasis is placed on having hardware manufacturers driver disks  handy, I'd try one if you got one with the old hd.  It seems highly  probable that your version of xp simply doesn't have the driver support  for the new old disk.
  
Personally I wouldn't bother having read this  [http://windows.microsoft.com/en-US/windows/help/end-support](http://windows.microsoft.com/en-US/windows/help/end-support)  

If you don't want buy windows 7 and do want to use some xp programs that  wine can't handle your best route may be to install virtual box ( it's  in the repositories ).  That way linux can support your hardware and XP  can run anything it normally could in it's virtual machine. The only  downside is that virtual box is cripple ware, meaning that it is  partially disabled in the free version.  Specifically the free version  doesn't support external drives.  One can get round it to some extent by  telling it that an iso is it's virtual cd drive so if you get hold of  an xp disk you'll have to make an iso of it, which as the owner you'd be  legally ok to do, one can also paste into it's virtual drive from your  master OS.  There is a way of making an iso from the bak files which is  the only option for an OEM owner but I don't know how it's done, tried  and failed to do that years ago for myself.   
If you can get all the bits for a straighforward reinstall then make  sure that one of the first programs you run is "rundills" from the  sysinternals suit, windows is also not at all good at deleting redundant  startup dills, they can slow things down too and are malware  favorites.  It can't even see them without sysinternals, when task  manager or confic.sys tells you that there are 20 running processes or  startup entries there are in fact several hundred.  
You'd also need to use linux to look at the system 32 directory to keep  the hidden logs from getting out of hand, and to scan the system when  it's dead ( malware often hides in running processes ).
It's hard work without support unless you stay offline, if other  programs can do your xp tasks I'd just switch altogether. Office stuff  is very well covered, try "save as" with a document in open office or  libre office to see if you are likely to have any problems with  formats.  Microsoft office and word perfect are well covered.  Most  audio visual media is ok too if one puts in the restricted extras.    Games are the weak spot as many are window only, I haven't found a good  open source .swf editor either. 
Again not a fix but a bump, there is bound to be an easy way of doing it  .... some sort of fstab equivelent perhaps, but I don't know it.   Failing that some of the above may be of some use so I'll leave it  there, it was more fun writing this than actually tidying up anyhow.
In short ...good luck and Bump.

---

