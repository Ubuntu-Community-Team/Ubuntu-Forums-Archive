---
title: "Is there life after Ubuntu?"
date: 2006-06-30
forum: General Help
---

### Post by bodhi.zazen on 2006-06-30
I am a realist and the Upgrade from 6.04 Beta to 6.06 LTS broke my install.

I have run on Ubuntu for over 1 year and enjoy this Forum. Prior to Ubuntu I was a Debian user and have enjoyed Ubuntu as a more up-to-date distro.

I regret to say I will be changing to an alternate distro. I wish Ubuntu all the best and will watch this distro. Hopefully it will mature and become stable once again, but I can not afford to run on a less then reliable system.

Two requests:

First, please do not flame me. It is not my fault Ubuntu has become unstable on my hardware. Such behavior reflects poorly on the Ubuntu community. I am happy for all those of you who are able to run Ubuntu, it is a great distro. Just ask yourself, what would you do in my shoes? I truly hope to return.

Second, any other Ubuntu users who have had a similar experience? Is there life after Ubuntu?

---

### Post by IYY on 2006-06-30
Of course, if Ubuntu didn't run on one of my machines, I wouldn't use it and switch to another distro. Luckily, it works very well.

As long as you're not switching to MS ;-)

---

### Post by lucia_engel on 2006-06-30
[QUOTE=bodhi.zazen]Just ask yourself, what would you do in my shoes?[/QUOTE]

If an upgrade didn't work, I'd back up my data and do a clean install. Although my Ubuntu didn't break after the upgrade, some random glitches did happen, mostly because of the many 'hacks' I did to fix my Breezy install. So when I receive my Dapper CD, I'll be doing a clean install.

If an upgrade destroyed all my data, then I'll consider switching to another distro.

---

### Post by phetre on 2006-06-30
Bodhi,Zazen, if you don't mind saying, what distro did you switch to?  Several of my friends are on the point of switching from Windows to Linux, and I'd like to be able to advise them on the relative strengths and weaknesses of different distros.

I'm not going anywhere -- still having way too much fun with Ubuntu!

---

### Post by woedend on 2006-06-30
use Arch.  The most up to date packages anywhere, extremely easy to make your own packages, and it will feel and boot 10x faster than ubuntu.  
Much much more knowledgeable community as a whole(no offense to the knowledgeable here), rolling release cycle, community repo(ubuntu should copy this idea!), and most everything is edited in one conf file.  Give it a try.

---

### Post by Drifter on 2006-06-30
what is arch, is it a linux distro, if so were can it be found.  Is it free etc.

---

### Post by matrooswolf on 2006-06-30
You could try Mepis as well (it's debian, and now Ubuntu based)

Very happy with Ubuntu here btw

---

### Post by matrooswolf on 2006-06-30
Arch can be found here:

[http://archlinux.org/about.php](http://archlinux.org/about.php)

---

### Post by bodhi.zazen on 2006-06-30
Phetre:

Right now I am looking at Zenwalk, Fedora core 5, and Debian (ELive).

For people new to Linux (from windows), my advice is to start with KDE as a window manager. Distro's to consider are Mepis, PCLinux, Fedora core, SUSE, Kanotix, or Ubuntu. Best to look at hardware and software requirements of newbies. In my opinion, of the large distros, Fedora core 5 is clearly the best full feature distro and comes with my strongest recommendation. Use frog to configure/install some extras post install (Java,etc). Don't let the 5 CD download fool you, Fedora is no more bloated then say Ubuntu.

[http://easylinux.info/wiki/Fedora_frog](http://easylinux.info/wiki/Fedora_frog)

One consideration is how familiar you may be with sys admin. My be best to stay with a Debian "clone" if you will need to assist your newbie friends with sys admin. This leaves Mepis, Ubuntu, and Kanotix. Of these 3 Mepis is the clear choice. Mepis is based on Ubuntu and a final release is due out in the next few days/weeks.

[http://www.mepis.org/](http://www.mepis.org/)

SUSE is nice, but it is VERY HELPFUL to review ALL the possible software options at the time of install. The main problem with SUSE is post-install the distro does not tend to keep up-to-date. Rather they release a new version every few months (ie 10.0 -> 10.1 -> 10.2). Problem: Up to now you can not upgrade 10.0 -> 10.1 -> 10.2. Make a home or better yet a data partition. The network install of SUSE is difficult, you need to nkow the IP address and directory of the suse server (you would think it would be on the install CD, but it is not). These are my (poor quality) SUSE notes for a network install:

SUSE 10.0
ftp protocol

Auto DHCP = yes

IP address = 216.165.129.140

directory on server = /pub/opensuse/distribution/SL-10.0-OSS/inst-source/



SUSE 10.1

http protocol

IP= 216.165.129.140

[http://suse.mirrors.tds.net/pub/opensuse/distribution/SL-OSS-current/inst-source/](http://suse.mirrors.tds.net/pub/opensuse/distribution/SL-OSS-current/inst-source/)

It makes more sense as you are installing and the program is asking you to configure the network card and instillation server.

ELive is interesting and unique. There is a thread in the Ubuntu forums regarding ELive. Enlightenment is interesting.

[http://www.elivecd.org/](http://www.elivecd.org/)

There are several nice live distros these days which allow one to try without a HD install. Wolvix is fast (although it is XFCE).

[http://wolvix.org/](http://wolvix.org/)



Some of the mini-distros are interesting, Puppy, DSL, and Austrumi. Puppy is clearly the best and runs in qemu (emulation).

[http://www.puppylinux.org/user/viewpage.php?page_id=1](http://www.puppylinux.org/user/viewpage.php?page_id=1)

[http://fabrice.bellard.free.fr/qemu/](http://fabrice.bellard.free.fr/qemu/)

Zenwalk is a nice, fast, medium weight distro based on slackware. I run with Fluxbox in combination with the ROX desktop.

[http://www.zenwalk.org/](http://www.zenwalk.org/)
[http://fluxbox.sourceforge.net/](http://fluxbox.sourceforge.net/)
[http://rox.sourceforge.net/desktop/ROX-All?PHPSESSID=2fa89a1469388f5a96473a8d1e98eebf](http://rox.sourceforge.net/desktop/ROX-All?PHPSESSID=2fa89a1469388f5a96473a8d1e98eebf)

Not for newbies however.

Source based distros are nice, but take a lot of love and solid foundation in Linux. Experience with BSD ports is also helpful. Experience in programing is also helpful. The main problem with source based distros is you are on your own if the install script fails. Examples include Arch, Furgalware, Gentoo, and VLOS. As an example I installed VLOS and after the first system upgrade the system was hurting. I just do not have the time or experience to constantly tweak the OS.

If you go with Arch, be prepaired to edit/write several sys scripts post install as not much is configured automatically by the installer. Arch uses pacman for package management which also requires some configuration. You will need to know where to look for packages and you may need to know how to resolve dependencies on your own.

You can try installing a few programs (from source) on Ubuntu and you will see what I mean. USE CHECKINSTALL. (ie ./configure; make; checkinstall rather then ./configure; make; make install). apt-get install checkinstall.

---

### Post by Drifter on 2006-06-30
Thanks, I looked at arch and right away knew it was not for me.  Mepis sounds good I tried a live cd of it and liked it.  Is it still like 50.00 bucks to buy it.  I love ubuntu, I just can't get my cdrw drive to work right with it. That was a typo mephis

---

### Post by bodhi.zazen on 2006-06-30
More on arch linux

Quote"  Arch Linux is a general purpose linux distribution that can be molded to do just about anything. It is fast, lightweight, flexible, and most of the parts under the hood are quite simple to understand and tweak, which can make it a good distro to "learn the ropes" on. We do not provide any configuration helper utilities (ie, you won't find linuxconf in here) so you will quickly become very proficient at configuring your system from the shell commandline. "

Translation: If you do not know how to spell vi, think twice. Not for newbies.

From : [http://wael.nasreddine.com/Articles/Articles/Install_Arch_Linux.html](http://wael.nasreddine.com/Articles/Articles/Install_Arch_Linux.html)

---

### Post by zba78 on 2006-06-30
Arch is superb, I just couldn't get it working with my current machine so that's why I switched to Kubuntu.

You could give Vector Linux a try. It's based on Slackware but uses slapt-get + gslapt by default.

Look at [http://distrowatch.com/](http://distrowatch.com/) for a list of distros (including links to their homepages)

---

### Post by steve.horsley on 2006-06-30
Before giving up on Ubuntu, try a clean install. That includes losing all your gnome config files from your home folder. That's what you'd do with another distro, so give Dapper an equal chance. I think a number of people have had broken upgrades but then working clean installs.

I know there are opinions both ways, but I do think that upgrades are likely to be more problematic because of all the little wrinkles that get carried over that don't quite work in the same way in the new s/w.

---

### Post by darkhatter on 2006-06-30
[QUOTE=steve.horsley]Before giving up on Ubuntu, try a clean install. That includes losing all your gnome config files from your home folder. That's what you'd do with another distro, so give Dapper an equal chance. I think a number of people have had broken upgrades but then working clean installs.

I know there are opinions both ways, but I do think that upgrades are likely to be more problematic because of all the little wrinkles that get carried over that don't quite work in the same way in the new s/w.[/QUOTE]

I agree with the user above, give it another shot. Is it safe to say that arch linux will give me a slackware like experience.

---

### Post by dspivey on 2006-06-30
Would you please be more specific about the issues you're experiencing, bodhi.zazen?

I did a clean installation of Dapper, and have had freezing problems (as have many others)

---

### Post by nameiwantistaken on 2006-06-30
Let's see, you used beta software and something got messed up?  Cry me a river.  You used BETA software.  I'll tell what I'd tell someone who was running Vista complaining about things getting messed up.  It's BETA and they call it that for a reason.  I'm all for gripes about things in linux not being as easy as they should, but please, be realistic.

---

### Post by bodhi.zazen on 2006-06-30
dspivey:

I described my problems, including error messages on boot, on this post:

[http://www.ubuntuforums.org/showthread.php?t=199549](http://www.ubuntuforums.org/showthread.php?t=199549)

As to a clean install, I have considered this possibility, but as I do not know what caused the problem and I need a stable OS I have decided to re-evaluate my options. I and leaning toward Fedora. I will watch Ubutnu and may return once it seems to be running a little more stable.

My decision is influenced by the fact that I do not seem to be the only one having trouble. I will l likely run an alternate OS as primary and re-install Ubuntu into a "test" partition. If Ubuntu stabilizes I can always return.

I have not yet lost data as I run a data partition and have /home backed up from prior to the update.

I am surprized as the Beta was so stable.



nameiwantistaken:

I did not have any significant problem with the Beta nor am I complaining about the Beta. My issue is with an update from the beta to LTS, and yes I expect LTS to be more stable then is now appears.

I am not complaining, just choosing to look into alternates after a total failure of what was my primary OS of the last year.

I otherwise agree with your comments regarding complaining about beta software.

---

### Post by woedend on 2006-06-30
arch is only as hard as you make it.
installing it is a chore the first time, use a short guide(or if you want, ill write you one).  Once you are up and running, there is nothing at all hard about it.  Some things I find easier than ubuntu.

---

### Post by bodhi.zazen on 2006-07-09
woedend

At your encouragement a took a "fresh look" at Arch Linux.

Although it looks interesting, I did not find it easy to install.

I am not sure how to configure all the files with the base install. I go through it OK.

After that I an not sure which daemons to install or exclude. Some I know, but others I do not.

Lastly, after the install X was non-functional and I was left with a CLI only OS.

If you would post a how-to or a web site that would be great.

Otherwise, if I am going to do this much effort, I would go to Gentoo.

---

### Post by woedend on 2006-07-09
[http://wael.nasreddine.com/Articles/Linux/Install_Arch_Linux.html](http://wael.nasreddine.com/Articles/Linux/Install_Arch_Linux.html)

got me started.  you NEED internet, once you got that down, install 
xorg gdm gnome gnome-extra and if you have nvidia install xf86-video-nv.

to get xorg configured, once installed, run
X -configure

then
cp /root/xorg.conf.new /etc/X11/xorg.conf
let me know if you need more help ill help out or get at me on AIM or yahoo mess

---

### Post by bodhi.zazen on 2006-07-09
Thank you woedend.

---

### Post by woedend on 2006-07-09
something I should touch on...
when it asks you for additional groups, i would use these
users,wheel,audio,video,storage,disk,optical

optical is needed for burning/reading cd, storage for automounting usb and whatnot, rest pretty self explanatory.  If youve already made the user its easy to add into these groups later.
as far as daemons, youll probably want to add
dbus hal alsa gdm
i prefer to use gdm in the daemon line rather than edit /etc/inittab because I cannot find a way to kill gdm otherwise.  when its in daemons i can just issue /etc/rc.d/gdm stop
this doesnt work with the inittab method.
Theres ton's of packages to be had, if you are looking for one let me know(gaim-2.0,xgl,compiz,alacarte,nautilus-open-terminal,etc etc)

youll also need to set the clock.  this is done in the /etc/rc.conf file.  find the appropriate section and edit as follows(UBUNTU uses UTC so i'm assuming yours is set this way)
HARDWARECLOCK="UTC"
TIMEZONE="US/Mountain"
(replace mountain with your actual time zone, i figured it would be mountain..if its pacific use US/Pacific)
lastly, if you get a locale error at times, do
vi /etc/locale.gen
uncomment the locales you use(in this case, the two EN_US ones), save the file, then issue the command locale-gen

---

### Post by chameleonkid on 2006-07-09
I recently just put Arch on my computer.

1.It was the easiest distro I have ever used to install, probably because you just install the base system (that means no gui).
2. No vim experience is needed, nano and mc worked fine for me ;) 
3. updating is easy but requires the internet.
4. getting xorg to work was a pain and a half but worth it, kde runs like a charm.
5. Like ubuntu, the documentation on the web is oh so helpful.

Overall I'd reccomend it if you don't mind a little hard work.

---

### Post by bodhi.zazen on 2006-07-10
Well, I did the deed. 

Installed Arch.

Configured Arch.

Updated Arch.

Installed nVidia driver.

Installed GNOME desktop. Not my favorite, but helpful to see a familiar face in a new OS.

Went to sleep (I was able to get 2 hours).

Reboot (for nVidia) --> GDM --> Log in

WOW. Arch is fast. WOW I like pacman. 2 seconds from log-in to desktop, I am used to 20-30. Arch is the fastest I have ever used.

No errors or conflicts at all with all that I installed. The only problem was a lack of knowledge (?How to configure Arch). The forums were very helpful.

I went with ARCH over Gentoo due to:
     1. I think Arch is more bleeding edge, at least that was my impression from several of the forums.
     2. Arch has pacman and I do not want to have to install and configure each and every application from source.

It looks like ARCH is likely to become my primary OS. Very light install and fast. pacman is very nice.

I need to learn to configure ARCH.

THANK YOU !!! Your post was invaluable, just enough info to take the edge off the install and configuration.

I need to further configure X and sound. Then install a light desktop, Fluxbox. Then wine (no I do not use M@@soft I just have one program for which there is not yet a Linux port).

Looks like it will be good bye to Ubuntu for now. My final list of Alternates:

For a full featured distro: Fedora core 5.

Light weight: Zenwalk.

Arch has the best of all worlds though, Light weight, fully configurable, and easy to install cutting edge software.

I reccomend arch to anyone who is willing to spend the time, newbie or otherwise. If you want to install and forget, maybe not. It seems fine once the install (and configuration of X and sound and the system)is over.

I'll keep you posted.

---

### Post by woedend on 2006-07-10
most settings are done in rc.conf.  The default gnome was kinda ugly but at the same time it ran much faster and looked cleaner to me.  I did install a nice icon package and GDM though(PS - I LOVE the Linsta GDM...you can customize the backdrop of it).  And the clearlooks-quicksilver has always been a favorite theme of mine.  search the arch forums for shadowhand, he has a repo with a few goodies in it(also search for cimi, he does too).  
shadowhand will bring up 2 results, use the os-zen one.  Danimoth now hosts the xgl/compiz packages.  The biggest limitation of pacman I've found is that the repos must be ordered.  That is, if a repo at the end of the file requires a package in a repo above, it will not resolve.  Also, if a lower repo has a newer version, its not used(weird, I know).  GTK-pacman is a frontend but I found it very buggy!
If you need help with anything feel free to im me or PM me on here, i check it often.

---

### Post by bodhi.zazen on 2006-07-13
woedend:

Just today finished installing and configuring Arch.

XFCE seems to work best with dual monitors (over GNOME and Fluxbox). I may look at IceWM or FVWM in The next few weeks.

Now that the configuration is done I am still enjoying Arch.

I've been looking for a distro without the bloat and adding only what I want. I like the control I have over the OS.

I am also impressed with pacman and the available, very up to date packages. I must say Arch "just works", really I have had no problems. I have dual monitors, three sound cards (yes, I use it all).

Arch is a BIG time saver over Gentoo and is VERY FAST. I can foresee Arch becoming very popular once the wiki and how to's are fleshed out somewhat.

I previously tried Frugalware which uses pacman, but I was always running into problems. I thought this was due to pacman and now I see it is with Frugalware.

Next I will need to start to compile from source, Fluxbox at least.

How is Arch for /.configure make make install?

Once again, thank you. You gave me just enough information to start with arch and I am grateful. Do you use the Arch Forums? 

I have remained active in the Ubuntu forums because Ubuntu has a large user base, is relatively cutting edge, and I enjoy helping newbies if I can.

---

### Post by woedend on 2006-07-13
i dont use arch forums much...a lot of those guys are way over my head.  Oh compiling is super easy because the dev packages are included in the main package...so you dont have to go fishing out *-dev files.  also, the make/gcc/ are included and the headers with the kernel as well for compilation.  Making packages is SUPER easy assuming you can find whats called a PKGBUILD file( a lot in the aur).  it basically just has a script of where to download the source, how to compile it, and turns it into a .pkg.tar.gz file(which installs similar to a deb, using pacman -A instead of -S).  so if you download the pkgbuild file into its own directory, then cd to that directory...simply run the command 'makepkg' and it does just that...nothing else!  I've had about 70% luck with PKGBUILDS, because a lot are CVS and simply not easily compilable.  You can make your OWN PKGBUILD files, but in reality I've never needed to.

---

