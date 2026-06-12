---
title: "I want to like Ubuntu but it ain't easy"
date: 2011-09-14
forum: General Help
---

### Post by AliPM on 2011-09-14
Hi, I've been an Ubuntu user for about 18 months now, and although when it works it's great, I've had so many problems I would like to ask if there's something obvious I've missed.

I have 2 pcs - an AMD X2 desktop and a VIA C7M netbook - and I've been dual-booting with XP, on both, since I figured out how to.

Unfortunately, on the netbook I frequently have the problem that after logging in, I am taken back to the login screen, and the only way to get to the desktop seems to be to log in in a GNOME failsafe session, then log out and log in again normally. This is not the only problem, but the others seem mostly to relate to the esoteric screen resolution (1024*600).

On the desktop, Firefox and other programs frequently freeze for periods up to a couple of minutes, with no explanation as to why.

If there is a log file I can look at (or post) for answers to frequent problems, I'd love to hear about it.

I've been evangelising about Ubuntu to so many people since I started using it, I really feel like I'm being betrayed a little by this OS! (Even though it's free...)

Thanks in advance

---

### Post by Basher101 on 2011-09-14
What version of Ubuntu do you use? Did you try a reinstall for fixing your problems?

---

### Post by AliPM on 2011-09-14
I've reinstalled many times on the laptop, not so many on the desktop. I'm using 10.04 on both.

Is there a way of restoring it to a fresh-install state without actually doing a fresh install? A friend-of-a-friend IT tech told me when I started out with Linux that Ubuntu was great because you don't have to reinstall it all the time like with Windows.

I had a lot of problems with GRUB when I reinstalled in the past. The only thing holding me back from having another go is the daunting task of backing up everything on my XP disk and starting from scratch in case I lose access to XP (that happened once before).

---

### Post by Basher101 on 2011-09-14
You dont need to reinstall it more frequently than windows because ubuntu has no registry that gets sluggish. The developers of the programs for windows dont always write a decent uninstaller and then there are always leftovers that slow windows down. In linux this does not happen. Although your issues maybe are a result of some hardware incompatibility. Not sure though, on my eMachines e725 everything worked out of the box. (1366x768 screen resolution)

---

### Post by LowSky on 2011-09-14
VIA processors are known to be slow, and graphically not well supported. But the issue sounds more like a bad install, or a case of the overzealous user enabling the root and logging into Gnome with full privileges. Which is a very bad thing, and leads to failures like that.

As for the desktop freezing using firefox, probably just a flash issue. Just install the firefox add-on called flash-aid and it should fix your issues.

I'm sorry if this offends you, I don't mean to, but it sounds as if you installed Ubuntu and may have enabled some features incorrectly. Doing so can lead to these types of problems. Many people come on the forums saying X doesn't work and forget to explain that they tried to do Y before the issue arose. So is there anything that you can think of that you tried to do before these issues started?

---

### Post by AliPM on 2011-09-14
OK, maybe I'll sit down and do a reinstall on the desktop some time soon then. Can't say i relish the prospect tbh :(

I spent a long time trying to reinstall 10.04 on the laptop and get the video working correctly, eventually ended up reinstalling 9.04 with an external monitor, changing xorg.conf (because this wasn't present in a fresh install of 10.04), and upgrading incrementally to 10.04. Loooooong!

---

### Post by AliPM on 2011-09-14
@LowSky No offence taken at all! I came here asking for help, didn't I?!

I'm  sure I've never fully enabled root privileges INTENTIONALLY - however, I've entered a lot of terminal commands on the advice of websites and other forum users. Can't say I understood all of it, was just going on faith.

I think a reinstall may be necessary, I know not what I may have done to Ubuntu in the year or so since my last fresh install.

Installed flash-aid, I'll see if that helps matters.

---

### Post by Blasphemist on 2011-09-14
I can't much get behind re-installing as a solution. There are times for it and I have done it but only on partitions that I just experiment with. The biggest thing relates to what you mentioned about not understanding everything you've done. None of us understand everything I'm sure. But the main way that we understand more and more is by working through solving issues. If you are going to re-install, and that most definitely is up to you, I do recommend installing 11.04 to allow you to benefit from the improvements over the last 18 months. If you want to work on the issues beyond the flash change you've already made, let's start with the specifics of your hardware models.

Thanks

---

### Post by SparTacux on 2011-09-14
> **AliPM said:**
> @LowSky No offence taken at all! I came here asking for help, didn't I?!

I'm  sure I've never fully enabled root privileges INTENTIONALLY - however, I've entered a lot of terminal commands on the advice of websites and other forum users. Can't say I understood all of it, was just going on faith.

I think a reinstall may be necessary, I know not what I may have done to Ubuntu in the year or so since my last fresh install.

Installed flash-aid, I'll see if that helps matters.

I know the feeling..

I decided to create an Ubuntu setup manual for all the stuff I need to do from a fresh install. Things like applications and packages to remove, applications to download, configuration file settings printed on paper with explanations on what it does, Firewall settings, Network Settings - the lot.

when it comes to doing an install I go through my manual and do all the stuff I've made notes of rather than trying to remember it.

---

### Post by walt.smith1960 on 2011-09-14
> **SparTacux said:**
> I know the feeling..

I decided to create an Ubuntu setup manual for all the stuff I need to do from a fresh install. Things like applications and packages to remove, applications to download, configuration file settings printed on paper with explanations on what it does, Firewall settings, Network Settings - the lot.

when it comes to doing an install I go through my manual and do all the stuff I've made notes of rather than trying to remember it.

A manual is a good idea and time saver.  I don't know how to do it but I may learn how to create a post-install script, a means to download & install things like Ubuntu Restricted Extras, TCSH and other things I need that aren't included on the LiveCD.

---

### Post by rewyllys on 2011-09-14
> **AliPM said:**
> . . . . I think a reinstall may be necessary, I know not what I may have done to Ubuntu in the year or so since my last fresh install.

Installed flash-aid, I'll see if that helps matters.
If you decide to do a reinstall, I'd urge you strongly to take the occasion to set up your /home folder on a separate partition.  If you do this, then you can reinstall the OS much more easily and, best of all, without affecting any of your personal data files and configuration files.

---

### Post by AliPM on 2011-09-15
> **rewyllys said:**
> If you decide to do a reinstall, I'd urge you strongly to take the occasion to set up your /home folder on a separate partition.  If you do this, then you can reinstall the OS much more easily and, best of all, without affecting any of your personal data files and configuration files.

Yes, I barely save anything in the home folder. Mostly just save things in the C: partition (as Windows sees it).

When you say "set up your /home folder on a separate partition", is that anything to do with setting the mount point during installation? I always set that to "/", because changing it to  anything else gives me an error message. Is the mount point the same place the GRUB is installed?

Thanks for everyone's input on this.

---

### Post by Topsiho on 2011-09-15
> **AliPM said:**
> Yes, I barely save anything in the home folder. Mostly just save things in the C: partition (as Windows sees it).

When you say "set up your /home folder on a separate partition", is that anything to do with setting the mount point during installation? I always set that to "/", because changing it to  anything else gives me an error message. Is the mount point the same place the GRUB is installed?

Thanks for everyone's input on this.

In /home the personal files of the users are stored, if you use Linux (Ubuntu) normally. And if /home has its own partition on the disk, then when reinstalling (which is not so terrible as you make it sound) you can leave it as it is (NOT format). Indeed, you must not forget to set the mount point to /home again, so you should remember what partition is the /home one. Just as when you need to retain Windows, you should know what partition(s) it occupies.

My netbook freezes too occasionally, specially when using Firefox, and I think it's due to the very small disk space it has (8GB), and the bad (early generation) SSD. I'll try the flash-aid plugin and see what happens :)

Mount point and GRUB are not related. You best place GRUB in the default place, during the install.

Topsiho

---

### Post by holycow131415 on 2011-09-15
I would recommend you download a new iso of ubuntu for you to burn to a new disk as well before you reinstall.

---

### Post by SeijiSensei on 2011-09-15
> **AliPM said:**
> When you say "set up your /home folder on a separate partition", is that anything to do with setting the mount point during installation? I always set that to "/", because changing it to  anything else gives me an error message. Is the mount point the same place the GRUB is installed?

During boot, the "root" partition, "/", is mounted so that the OS can use the programs in /bin and /sbin to get the system up and running.  At that point Ubuntu, like most Linux systems, switches to multi-user mode, which brings the /usr, /var , and /home directory trees into play.  It's actually possible to place all three of these on separate partitions, but putting /home on its own partition is most common.  

You may not think that you've stored much in your home directory, but if you run 'ls -la ~' you'll see a lot of "hidden" files, ones starting with dots, that contain the configuration files for your desktop environment and for the programs you've used.  Things like bookmarks in Firefox, mail folders in Thunderbird, configuration files for smplayer, etc., etc., are all stored in your home directory.  Placing /home on a separate partition means that a re-installation of Ubuntu won't change these configurations.

I routinely install grub to the "master boot record" ("MBR") of the system drive.

---

### Post by karen729 on 2011-09-15
I'm an 'almost' ex-Windows XP user. About all I use XP for now is the printer and Netfilx in IE. I spent probably 2 years worth of spare time learning everything I could about XP to make it do what I wanted it to.

I've been using Ubuntu for about 1 year and still have a ways to go before I learn everything I want to about it. When I think about the time and aggravation and frustration I had with XP, and still wasn't satisfied, I'm not giving up on Ubuntu. I find the support to be way much better for Ubuntu than it ever was or is for Microsoft. Ubuntu has a great bunch of folks behind it.

As some of the others have said, I too keep a "manual" - I have probably  2 dozen text files with notes for almost everything I have done.

One thing that can be hard to deal with, is that Ubuntu and Linux use names for things that are different from Microsoft; like Microsoft calls them folders and Linux tends to call them directories.

Anyway, I hope you don't give up on Ubuntu, because I think in the end you'll be much happier with ubuntu. Good Luck with whatever you decide to do :D

---

### Post by AliPM on 2011-09-15
Again, thanks for all the input.

Do I really want to back up my /home directory if there's a possibility that something I've inadvertently changed is causing the problems I'm having?

I know reinstalling shouldn't be too big a deal, but in the past I've rendered my computer unusable for a few days after reinstalling, and I just can't have that happen at the moment. I'm also jaded by my experience with the netbook - because of the screen resolution, a reinstall means attaching my projector, which is a whole cables-everywhere pain in the neck. On the desktop this won't be a problem.

I'll probably give a reinstall a try over the weekend. Is it worth installing 11.04?

---

### Post by AliPM on 2011-09-15
[LEFT]@karen729 That's funny you say you keep XP just for the printer, because neither my laptop nor my desktop can see my printer when I'm running XP. Ubuntu wins hands down on that count :D
[/LEFT]

---

### Post by Topsiho on 2011-09-16
> **AliPM said:**
> 
Do I really want to back up my /home directory if there's a possibility that something I've inadvertently changed is causing the problems I'm having?


I don't understand this question. But you always need to backup your personal files, which you would hate to loose, and put the backup some place else, even with a friend or so, to prevent them getting lost if something happens to your hard disk, your computer or your house (or your town, country or earth :) ).

Your /home map (folder, directory, what's in a name) contains your personal files, of all the users if there are more than one. And of course the personal settings. If it's these settings (in the hidden files, with a . in front) that cause trouble you can delete these, so that in the new install they will not cause problems again.
I never tried this latter myself though, never needed to. Please listen to someone carefully if [s]he comments on this.


Topsiho

---

