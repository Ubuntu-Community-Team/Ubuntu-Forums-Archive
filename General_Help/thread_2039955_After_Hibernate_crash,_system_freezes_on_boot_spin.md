---
title: "After Hibernate crash, system freezes on boot spinner"
date: 2012-08-09
forum: General Help
---

### Post by Hypocee on 2012-08-09
Hi folks. I'm trying to unwedge my boot sequence after a crash during my first attempt to hibernate a years-old installation.  The system was installed as a 10.04, but has been updated per Synaptic's requests roughly weekly, which I hope means it's "current" in terms of practices and files to hack. The last update was a few days, and a few boots, before this incident.  

The installation is in a multi-boot system alongside XP and Win 7. Both of the latter boot fine, and Ubuntu gets to its graphical spinner screen so I doubt any GRUB problems.   

This OS is primarily used to manage my large eSATA disks and backup protocol through rsync. A few days ago I got an unusual amount of browser tabs open and casually tried to hibernate instead of shutting down, for the first time. During shutdown the system crashed on a "not enough swap" message. Since shutting it off via the power button from that I haven't been able to get it back to the login screen.  

The system displays the normal GRUB menu. If the Ubuntu installation is selected (or selected by timeout; it's the default), a moment of ISOLinux terminal screen appears as usual, followed by the splash screen with the Ubuntu logo and spinner composed of a line of four red/white dots. Some small gray/beige dialog box appears then vanishes near the center of the screen for an instant, which I believe is new to this situation. The system then displays HDD activity until the spinner dots have all filled red, then white, then all four red again if that indicates anything concrete about progress. At that point the spinner ceases to "spin", hard disk activity ceases and the keyboard dies - Numlock/Capslock LEDs go out and do not respond. I've left the system in this state for half an hour with no change. Because the keyboard doesn't work I'm unable to switch to terminals or kill X. I have not attempted to switch to terminal before the crash.  

Recovery mode, on a separate GRUB option, happily boots and logs in. I suspect it's going to be my main tool, although I have LiveCDs as well.  

I have about a decade of low-grade GNU/Linux experience. For various purposes I've used Red Hat, Puppy, Arch and a dozen flavors of Debian, with window manager/desktop environments ranging from screen and wmii through Enlightenment and xfce to KDE and GNOME. I'm comfortable with common uses of command line tools and do basic vim, emacs, mc, regex etc. I have successfully hand-built GRUB, X and SMB configs, though it's rarely been pleasant. I've had little time to screw around with GNU/Linux the past few years and treat Ubuntu as a more dev-managed and amorphous solution, so know little about anything specific to Ubuntu's setup. Replies are likely to be weirdly delayed since I work second shift.  

I'm aware of 
[http://lovehateubuntu.blogspot.com/2009/08/ubuntus-hibernate-wont-wake-up.html](http://lovehateubuntu.blogspot.com/2009/08/ubuntus-hibernate-wont-wake-up.html) 
but it's old and doesn't match my symptoms well. I've been trying various Webwide searches for a few days but it's hard to filter out old bug reports, flames etc. I've gone through every result of a couple searches here, of which 
[http://ubuntuforums.org/showthread.php?t=2036161](http://ubuntuforums.org/showthread.php?t=2036161) 
and 
[http://ubuntuforums.org/showthread.php?t=1477500](http://ubuntuforums.org/showthread.php?t=1477500) 
are the most applicable, but not very. 

What do please?  

Thanks for your attention.

---

