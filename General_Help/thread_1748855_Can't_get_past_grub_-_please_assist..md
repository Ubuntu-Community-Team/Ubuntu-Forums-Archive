---
title: "Can't get past grub - please assist."
date: 2011-05-04
forum: General Help
---

### Post by Duncan Williams on 2011-05-04
About a month a go I downloaded and installed ubuntu maverick as dual boot with windows XP.
I was getting problems with display re/ nvidia fx5200 graphics card.
I downloaded and installed Natty (11.4-alternative daily release - around beta 2 release).
**Both versions of ubuntu worked in unity mode**.
I was still having problems with graphic card, nvidia drivers and nouveau drivers.
So I went out and spent (AU)$120 on a ATI HD 3650 - 512mb video card (agp).
With my spare (40 gig)hard drive formatted, I inserted and installed ubuntu natty from same CD.
Couldnt get past grub.
Tried to boot from maverick CD, no luck there.

Reinstalled windows on freshly formatted 80 gig harddrive.
installed amongst other peripherals, etc, `ATI HD3650 Graphics card' with full `ATI Catalyst Control Centre' at 1920 by 1080 (24" monitor) what a beautifull card when all set correctly.

OK.
Now after installing ubuntu 11.4 (natty) from daily disc on a 40 gig partition to dual boot with windows on my 80 gig drive.
I get **grub** with options for ubuntu, recovery mode,memory test, memory test serial and windows XP.
1. click on `ubuntu' > goes to blank screen.
2. click on `recovery mode' > scrolls information then > blank screen.
3. click on `windows xp' > boots up windows with full video card support, etc.

I am pretty sure it is a graphics card issue.

What do I do to install correct drivers or whatever is required to get ubuntu/unity up?

I have 2 cd's > `maverick' (stable 10.1) and `natty' (alternative daily build around beta-2)

I don't want to download another distro if possible.

I think I can get into a terminal through booting with cd at least.
Can someone tell me how to sort this out?

---

### Post by your imaginary friend on 2011-05-04
Hi Duncan,

Just to clarify: you had 11.04 up and running with nvidia drivers installed (but not working correctly), then you installed an ATI graphics card.  Is this correct?

Did you uninstall the nvidia drivers BEFORE putting in the new ATI card and booting up?  nvidia drivers don't work happy with ATI cards.

Can you get to a tty prompt? ctrl-alt-f1 and log into your system without graphics.  From there, uninstall (purge) the nvidia drivers and try rebooting into your system.

Once you're back in you should be able to get the ATI driver installed and working.

EDIT typos

---

### Post by Duncan Williams on 2011-05-04
thanks, will try again 2moro. any other comments/advise with thanks,

---

### Post by Duncan Williams on 2011-05-04
I only have ati drivers installed in windows. I have not installed any in ubuntu partition but it might have set something when I installed ubuntu. 
How do I find out what video drivers / reset video drivers etc.

As stated I can't get past grub. But should be able to use terminal.

Thanks again.

---

### Post by your imaginary friend on 2011-05-05
It's possible you have nvidia drivers installed in ubuntu. If you can get into the terminal (ctrl-alt-f1) run
```
dpkg --get-selections | grep nvidia
```
to see what is installed, then uninstall (purge) the drivers present:
```
sudo apt-get purge nvidia-*
```

To install ati drivers, try rebooting first (after purging nvidia) and run jockey-gtk to automatically fetch the right drivers. (my understanding is there are the open source ati ones as well as the proprietary fglrx one.  you only want one installed at a time, and i think natty has very good ati support with the open source driver.)

Hopefully that works.  Don't want to have to do a clean reinstall of natty...but if worse comes to worst that's what I'd do :S

---

### Post by Duncan Williams on 2011-05-05
I have done cleaninstalls, natty, maverick, windows.
If xp wasn't so old I would just plain give up.
I mean, new video card etc, to keep linux happy, and now, no linux.
So, I can get a full distro of redhat from the newsagents and try it from there.
BUT: I so liked ubuntu unity and decided to go that way.
and, as stated, have 2 CD's 
1. maverick live cd
2. natty daily release (around beta-2)
and ubuntu 11.4 installed on a 40 gig partition on my computer.
 It would be nice to log in as root administrator and tell the grub or X or Gnome or whatever to let me use the system in low graphics so I can properly install ATI drivers or open-source version. or whatever else is required, but I am new to linux and don't know what to do.

I need precise, specific, assistance.
maybe this and maybe that aint know use.
I don't mean to sound arrogant or whatever, But the booting up and use of OS is what I need.

---

### Post by Duncan Williams on 2011-05-05
to be honest, and sad as it may be.
I am just going to use my peripherals to their maximum capabilities by using windows XP3. with supported proprietory drivers.
I do have a nice 24" HD monitor and a phat 1/2 gig graphics card now at:
> 1920by1080 32bit resolution (inc, videos/games/photo's,etc)
> most of my data is in the cloud.
> ubuntu dont work since I upgraded my video card.
so my forced re-install of windows XP made me:
> only put sp2 as far as updates.
> only use malwarebytes scanner for malware protection.
> use browser extensions as all basic utilities.
so now it is like so fast and loves the basic enviroment...

---

### Post by your imaginary friend on 2011-05-05
To go back to the question I asked in my first reply: you had 11.04 up and running with nvidia drivers installed (but not working correctly), then you installed an ATI graphics card. Is this correct?

OR, did you install the ati card and do a clean install?

Trying to figure out exactly what you did so I can provide the "precise, specific, assistance" you asked for.

I'll ask again: can you boot into the system at all from the "terminal" (tty prompt) when you press ctrl-alt-f1 after selecting "ubuntu" or "recovery mode" from grub?

---

### Post by your imaginary friend on 2011-05-05
To go back to the question I asked in my first reply: you had 11.04 up and running with nvidia drivers installed (but not working correctly), then you installed an ATI graphics card. Is this correct?

OR, did you install the ati card and do a clean install?

Trying to figure out exactly what you did so I can provide the "precise, specific, assistance" you asked for.

I'll ask again: can you boot into the system at all from the "terminal" (tty prompt) when you press ctrl-alt-f1 after selecting "ubuntu" or "recovery mode" from grub?

---

### Post by Duncan Williams on 2011-05-05
*`OR, did you install the ati card and do a clean install?'*
thats the one as stated in my first comment.

I can press > C < at grub and get command line.
I typed `help' and `videoinfo' and `videotest' and got feedback.

It seems to be using `vesa driver' 
seems to say it supports > 1920by1080
something about pcivideo
I tried a number of times to enter `**ubuntu**' and `**recovery**' modes. No success.
led on monitor stays blue (on/connected) on one of the boots and goes orange after grub on the other one. (disconnected).

Thats pretty much were I am at the moment.

I do like unity and I do want to use linux. After having it working for a month it is annoying to not be able to use it now.

---

### Post by your imaginary friend on 2011-05-05
> **Duncan Williams said:**
> *`OR, did you install the ati card and do a clean install?'*
thats the one as stated in my first comment.


Have you tried reinstalling using the release version of natty 11.04?  (ie have you only been using the ~beta daily build?)


The daily builds might not have full hardware support, whereas the full release should.  If it booted from the install disc/usb then it should boot after install.

---

### Post by Duncan Williams on 2011-05-05
I am using to date the daily build disk I burnt about 3 weeks ago.(which installed correctly the first time)
I have stable maverick cd (which I installed succesfully a month or so ago)
I am paying $60 for 4 gig of bandwidth, so don't like to use over a gig with distro and updates, and am not sure if it will work.

---

### Post by Duncan Williams on 2011-05-05
just tried maverick cd.
after getting:
try ubuntu without installing
install ubuntu
check disc
test memory
boot from hard disc

i click on `try ubuntu without installing'
and boots to blank screen.

---

### Post by Duncan Williams on 2011-05-06
just went out and purchased a distro of `peppermint'.
livecd boots to blank screen.

---

### Post by Duncan Williams on 2011-05-06
Well thanks for your support and assistance ubuntu community.

I will post any solutions for any-one else it may be of use to.

I now have 3 cd distros of linux.
1.  ubuntu maverick, live cd.
2.  peppermint ice, live cd.
3.  ubuntu natty, beta, alternative cd.

I have 2 partitions on my 80 gig hard drive.
[I]Partition 0
	Partition ID	Disk #0, Partition #0
	Disk Letter	C:
	File System	NTFS
	Volume Serial Number	B0E4C982
	Size	37.5GB
	Used Space	19.6GB (53%)
	Free Space	17.9GB (47%)
Partition 1
	Partition ID	Disk #0, Partition #1
	Size	36.9 GB[/I]

I have natty installed by my cd on partition 1.

> Windows boots from grub.
> ubuntu wont boot from grub (blank screen)

Neither of the 2 live cd's will boot to a gui.

So, I am starting to think its is one of the following:

> The partition is corrupt/faulty instalation?
> There is a component of my current system that linux won't recognise (ie/video card)

I have as per previous comments in this thread reinstalled windows and ubuntu from scratch onto newly formatted hard-drive.

* I can't work out why the live cd's wont just boot and operate.

The next thing I am going to try is:
 format another hard-drive I have.
 Try to install from live cd to formatted drive (with no operating system onboard - ie/ change the hard-drives over)

over the next day or so.

meanwhile my newly installed 3650/512mb video card has totally given new life to my pc and 24" hd monitor.
After installing latest video drivers (ati-catalyst) in my re-installed from scratch windows XP (also:latest via-motherboard drivers) I have High Definition video at 1920by1080 at 75hz. Full opengl and direct x 3D affects. And the 512mb memory is getting used a lot. Also photos and other images are much more detailed. So it's all good I suppose.

---

### Post by Duncan Williams on 2011-05-07
OK HUMANOIDS......   I SOLVED THE PROBLEM...  
and I am so happy about it (2 weeks later)

After amongst a lot of other things and not for the first time:
I went into my bios and slowly went through every setting.

there it was staring me in the face.

AGP APERTURE SIZE
[www.google.com/search?q=AGP APERTURE SIZE]("www.google.com/search?q=AGP APERTURE SIZE")

Mine was set to 128mb from my previous nvidia graphics card
I set it to 512mb as per my new ati-3650-512mb graphics card.

Hey presto.

After booting into grub selected `ubuntu recovery mode' went into `failsafe graphics mode' and got errors and switched to `classic ubuntu'.

which is what I want, coz now I can setup my graphics card in linux at long last.

---

### Post by wilee-nilee on 2011-05-07
Check in with us from the mother ship Star Captain.:)

---

### Post by Duncan Williams on 2011-05-07
Post Update:
I forgot what could by a major factor in last post.
I also switched  `HDD S.M.A.R.T. Capability' to `disabled' in the bios.

I got partial updates offer from update manager from existing install of ubuntu.
so.
>  Re-installed ubuntu from daily build natty disk.
>  Used failsafe graphics in recovery mode to intall ATI-proprietory drivers from `additional drivers'.
>  downloaded and installed 300 mb of updates from update manager.

Now in unity 3D with full 1920by1080 and 3D graphics, HD etc.

I also switched the AGP APERTURE SIZE back to 180mb and it boots from grub with that setting.

Thats my jump from XP (which is 10 years old) sorted.

---

