---
title: "GNOME 2.14 upgrade in Breezy"
date: 2006-04-07
forum: General Help
---

### Post by shuttleworthwannabe on 2006-04-07
I was wondering if one could actually upgrade from 2.12 to 2.14? Also applies to OOo upgrade to 2.0.2 in breezy?

Could we not just add the GNOME repo and OOo repo in Breezy sources.list???

Just curious. NOTE: this is in breezy, and do not want to move to Dapper development yet. but just upgrade these packages.

Thanks for your attention.

---

### Post by jazzi on 2006-04-07
[QUOTE=shuttleworthwannabe]I was wondering if one could actually upgrade from 2.12 to 2.14? Also applies to OOo upgrade to 2.0.2 in breezy?
[/QUOTE]

I am wondering also.Could it be and when?](*,)

---

### Post by TheEclypse on 2006-04-08
I was also just thinking this, I hope it is possible.

---

### Post by s|k on 2006-04-08
I don't recommend even trying unless you have *a lot* of spare time. Think hundreds of dependencies, hundreds of subdependencies, tons of configuring, debugging bad 'make' commands, etc.

You'll be doing it all from the console.

If you do manage to do it successfully, write a tutorial. ;)

It's not for those new to linux.

Also, if you live on the bleeding edge, you will get cut.

---

### Post by shuttleworthwannabe on 2006-04-08
so if there are many of us, what is the solution?

---

### Post by s|k on 2006-04-08
[QUOTE=shuttleworthwannabe]so if there are many of us, what is the solution?[/QUOTE]
Upgrade to dapper.

---

### Post by shuttleworthwannabe on 2006-04-08
slk, thanks fo rthe headsup! Dapper is the next logical move. But hey 2.12 GNOME is not bad considering some distros are still using 2.8 and 2.10 (MEPIS, FoXLinux 1.0 Pro)

EDIT: this just in, Breezy backports have 2.14??? check this thread: [http://www.ubuntuforums.org/showthread.php?t=157119](http://www.ubuntuforums.org/showthread.php?t=157119)

---

### Post by John.Michael.Kane on 2006-04-08
It looks like it would be a lot of time to compile. theres info on how to do it.
[http://www.gnome.org/start/2.14/](http://www.gnome.org/start/2.14/)
GARNOME [http://www.gnome.org/projects/garnome/](http://www.gnome.org/projects/garnome/)
GARNOME Dependencies [http://www.gnome.org/projects/garnome/deps-list-ubuntu.html](http://www.gnome.org/projects/garnome/deps-list-ubuntu.html)


[http://packages.ubuntulinux.org/breezy-backports/gnome/](http://packages.ubuntulinux.org/breezy-backports/gnome/) does not look like it is in the backports. still looks like you would have to compile it from source.

---

### Post by TheEclypse on 2006-04-08
I have just made a backup of my current install, so im gonna upgrade to Dapper now.

---

### Post by TheEclypse on 2006-04-08
I have just upgraded to Dapper, but I think things are running more slowly than they did with Breezy.  Although when I changed the theme away from the not-so-nice one that has replaced Human, to clearlooks, it seems to be more responsive.

---

### Post by xXx 0wn3d xXx on 2006-04-08
[QUOTE=TheEclypse]I have just upgraded to Dapper, but I think things are running more slowly than they did with Breezy.  Although when I changed the theme away from the not-so-nice one that has replaced Human, to clearlooks, it seems to be more responsive.[/QUOTE]
Do a clean install. If you dist-upgrade, your system is going to be very slow. Dapper was very slow when I dist-upgraded to it but I did a clean install and it was very fast.

---

### Post by Rory on 2006-04-08
May I ask why it's so difficult to move from Gnome 2.12 to 2.14 in Breezy?  Kubuntu manages to quickly build a repo for all new KDE releases and upgrading, for the most part, is very, very simple.  

I'm not trying to start a Gnome v. KDE war here.  Just interested in what the difference is.  

R.

---

### Post by shuttleworthwannabe on 2006-04-08
MasterChief1234,

I see you have an ATI card as well. How did you manage to get Dapper installed on your machine? I am having trouble installing flight 5 or 6 on my machine it keeps freezing at the boot splash screen. Hence, I have done a dist-upgrade. (NOTE: there is a big filed on this issue)

Would be nice to shre your experience for us all.

---

### Post by TheEclypse on 2006-04-08
[QUOTE=MasterChief1234]Do a clean install. If you dist-upgrade, your system is going to be very slow. Dapper was very slow when I dist-upgraded to it but I did a clean install and it was very fast.[/QUOTE]
Things seem to be running OK now - not sure what happened before.

---

### Post by xXx 0wn3d xXx on 2006-04-08
[QUOTE=shuttleworthwannabe]MasterChief1234,

I see you have an ATI card as well. How did you manage to get Dapper installed on your machine? I am having trouble installing flight 5 or 6 on my machine it keeps freezing at the boot splash screen. Hence, I have done a dist-upgrade. (NOTE: there is a big filed on this issue)

Would be nice to shre your experience for us all.[/QUOTE]
Well, it just worked. Dapper reconized it right away. If it keeps freezing at the boot splash, redownload Dapper flight 6 and re-burn it to a fresh cd. Meaning it has never been used before. Make sure to burn and the slowest possible speed. like 4x to avoid errors.

---

### Post by shuttleworthwannabe on 2006-04-09
unfortunately I have burnt about 10-12 cd at 2x speed, and I have chekced and overchecked the cd integrity; it install well on a non-ATI laptop well. The last download xubuntu dapper flight 6 daily yesterday (thinking that they have fixed the bug in the latest daily build, and xubuntu), just corrupted my BIOS: I lost the built in clock settings, and got a "BIOS bug, local APIC #0 not detected error"

I freaked out and shutdown. Rebooted and got into GRUB, selected WINDOWXP, and re-flashed my BIOS with the latest HP BIOS version. So what I am saying here is that I am jinxed not to install Dapper fresh (I am using breezy-->dapper upgrade). Why would it affect my BIOS settings???
here is my thread (that has not received any attention yet: [http://www.ubuntuforums.org/showthread.php?t=157052](http://www.ubuntuforums.org/showthread.php?t=157052) )

Thanks for replying

---

### Post by nazish on 2006-04-09
i think this isn't possible with gnome 2.14 as I have used dapper (but recently switched back to breezy due to a lot of crashes), I am saying so bcoz the ubuntu developers have done a lot of research with gnome too to make it a lot integrated with ubuntu and in that process gnome 2.14 has undergone a lot of changes in ubuntu. And if we need to dload gnome 2.14 we need do get the remaining changes too which in turn would mean upgrading to dapper, so it remains upto u. But my personal experience says we should wait some time b4 dapper stable hits out. 

and I am not any foreteller but as far as  I know dapper surely going to be one of the biggest sensations in the history of Linux. Do remember me after dapper comes out.
[B]
--naz--[/B]

---

