---
title: "Choppy font problem."
date: 2012-09-02
forum: General Help
---

### Post by Cornova on 2012-09-02
I recently upgraded from Ubuntu 10.04 to Kubuntu 12.04 and noticed that fonts have strange lines in them. Attached is a screenshot of an article title. The lines are scattered like that throughout text. Any idea what is causing it?

---

### Post by Cornova on 2012-09-04
Here's another example of the problem attached below. The fc-cache command did not solve the problem. I've tried changing the fonts and altering the anti-aliasing settings but nothing has worked so far.

Any ideas?

---

### Post by SeijiSensei on 2012-09-04
I would do a clean install of Kubuntu 12.04.

---

### Post by Cornova on 2012-09-04
> **SeijiSensei said:**
> I would do a clean install of Kubuntu 12.04.

I have considered doing that, but do you have any reason in particular? It will take me hours to back everything up and reinstall and I don't want to do so needlessly, especially if I have the same problem as soon as I log in again.

---

### Post by bra|10n on 2012-09-04
The default font rendering on KDE is only passable at best, and so while you are experiencing this strange font-settings conflict it might be timely for you to consider this, 
IMO better font rendering than default.

A link to the thread, with screenshots and user comments [[COLOR="Blue"]here[/COLOR]](http://www.kubuntuforums.net/showthread.php?58703-New-font-configuration-Are-they-better&highlight=font+configuration)

HTH

---

### Post by Cornova on 2012-09-04
> **bra|10n said:**
> The default font rendering on KDE is only passable at best, and so while you are experiencing this strange font-settings conflict it might be timely for you to consider this, 
IMO better font rendering than default.

A link to the thread, with screenshots and user comments [[COLOR="Blue"]here[/COLOR]](http://www.kubuntuforums.net/showthread.php?58703-New-font-configuration-Are-they-better&highlight=font+configuration)

HTH

Thanks, I'll definately look through this thread tomorrow when I can sit and concentrate on it. I'm not really familiar with all the terminology and such.

---

### Post by bra|10n on 2012-09-04
Your welcome.
Ensure you download the latest patches (from infinality.net)
Familiarise yourself with the contained files after extracting the downloads. For anything else you'll find the thread explains most of the setup for it.

Good luck ):P

---

### Post by SeijiSensei on 2012-09-05
> **Cornova said:**
> I have considered doing [a clean install], but do you have any reason in particular? It will take me hours to back everything up and reinstall and I don't want to do so needlessly, especially if I have the same problem as soon as I log in again.

Well you have changed both the Ubuntu version and the desktop environment at the same time.  I can imagine lots of possibilities where things are hanging around from before that might create problems.  I have Kubuntu 12.04 running on a couple of different machines with very different video adapters, and the fonts look crisp and clear on all of them.

I do install the Microsoft fonts using the [ttf-mscorefonts-installer](http://packages.ubuntu.com/natty/ttf-mscorefonts-installer) because so many websites use fonts like Arial or Tahoma.  I don't know if that will help you.

If you decide to reinstall, I *strongly* recommend that you use the manual partitioning tool during installation to create a separate partition for /home.  The OS itself can easily fit in a 20GB partition with plenty of room to spare.  Then you can create a separate partition from the remainder of the disk and mount it as /home.  If you need to reinstall in the future all your personal files will be left intact.

As for whether you would have the same problem again, boot the Kubuntu 12.04 CD and choose the Try Ubuntu option.  See if it works better than what you have now.

---

### Post by Cornova on 2012-09-09
> **bra|10n said:**
> Your welcome.
Ensure you download the latest patches (from infinality.net)
Familiarise yourself with the contained files after extracting the downloads. For anything else you'll find the thread explains most of the setup for it.

Good luck ):P

Thanks, I was able to get through the instructions and the font appearance did change, but the problem still persists.

> **SeijiSensei said:**
> Well you have changed both the Ubuntu version and the desktop environment at the same time.  I can imagine lots of possibilities where things are hanging around from before that might create problems.  I have Kubuntu 12.04 running on a couple of different machines with very different video adapters, and the fonts look crisp and clear on all of them.

I do install the Microsoft fonts using the [ttf-mscorefonts-installer](http://packages.ubuntu.com/natty/ttf-mscorefonts-installer) because so many websites use fonts like Arial or Tahoma.  I don't know if that will help you.

If you decide to reinstall, I *strongly* recommend that you use the manual partitioning tool during installation to create a separate partition for /home.  The OS itself can easily fit in a 20GB partition with plenty of room to spare.  Then you can create a separate partition from the remainder of the disk and mount it as /home.  If you need to reinstall in the future all your personal files will be left intact.

As for whether you would have the same problem again, boot the Kubuntu 12.04 CD and choose the Try Ubuntu option.  See if it works better than what you have now.

I should have clarified that the OS is on it's own hard disk, I cleared it with killdisk before I installed it. By upgrade I just meant I switched to Kubuntu not used an upgrade feature in the old version I was using, my bad.


I may have to switch to another distro if I don't solve this soon. :(

---

### Post by bra|10n on 2012-09-09
I read that my earlier suggestion failed to remedy your font issue and the problem is no longer confined to your font rendering. It seems very likely you are one of the few who are affected by a bug in VSync. The kwin developers have said this issue will be fixed with the 4.9.1 release, however I am running 4.9.1-2 (Chakra) now and I am still experiencing different issues with VSync. I can only suggest you bide your time and wait for a fix.

---

### Post by Cornova on 2012-09-09
> **bra|10n said:**
> I read that my earlier suggestion failed to remedy your font issue and the problem is no longer confined to your font rendering. It seems very likely you are one of the few who are affected by a bug in VSync. The kwin developers have said this issue will be fixed with the 4.9.1 release, however I am running 4.9.1-2 (Chakra) now and I am still experiencing different issues with VSync. I can only suggest you bide your time and wait for a fix.

Thanks for the suggestions. Not sure if I'll wait or simply try another distro, sometimes the problem makes it impossible to work on documents.

Can I simply delete the files in /etc/profile.d that were added in order to return to where I was before? Or will this cause problems?

---

### Post by bra|10n on 2012-09-09
> **Cornova said:**
> Thanks for the suggestions. Not sure if I'll wait or simply try another distro, sometimes the problem makes it impossible to work on documents.
So far VSync problems in KDE have affected Kubuntu, Gentoo and Chakra distros. Which will you try? A suggestion might be another desktop environment while this gets sorted.

> **Cornova said:**
> Can I simply delete the files in /etc/profile.d that were added in order to return to where I was before? Or will this cause problems?

Sure. Delete from /etc/profile.d and etc/fonts and set via SystemSettings.

---

### Post by Cornova on 2012-09-09
> **bra|10n said:**
> So far VSync problems in KDE have affected Kubuntu, Gentoo and Chakra distros. Which will you try? A suggestion might be another desktop environment while this gets sorted.



Sure. Delete from /etc/profile.d and etc/fonts and set via SystemSettings.

I was thinking Mint but it doesn't have the full disk encryption feature which is why I updated from 10.04 in the first place. Other than Ubuntu/Kubuntu only OpenBSD has that feature that I know of.

What do you mean by Set SystemSettings? And is there any way to follow the VSync issue? I thinnk I'm going to hold out with Kubuntu for awhile to see if anyone pops in with a solution.

---

### Post by bra|10n on 2012-09-09
Sorry I meant re-check your font settings in SystemSettings after you delete those files.

You can follow progress on the KDE forums [here]("http://forum.kde.org/viewtopic.php?f=111&t=107607")

---

### Post by Cornova on 2012-09-15
> **bra|10n said:**
> Sorry I meant re-check your font settings in SystemSettings after you delete those files.

You can follow progress on the KDE forums [here]("http://forum.kde.org/viewtopic.php?f=111&t=107607")

I ran the KDE update that was suggested to address VSync and made sure everything else was up to date. Unfortunately the problem remains. Thanks for all the help though.

---

### Post by Cornova on 2012-09-15
I just burned a Linux Mint DVD because I was getting sick of this issue and planned to install it.

Low and behold, running the DVD (where you can preview the OS) it has the exact same problem, so this isn't limited to KDE.

I did not have this issue running Gnome on Ubuntu 10.04. New kernal problem?

---

### Post by bra|10n on 2012-09-15
I take it you burnt a Linux Mint DVD with KDE?

---

### Post by Cornova on 2012-09-15
> **bra|10n said:**
> I take it you burnt a Linux Mint DVD with KDE?

Nope, I forgot to mention that it's Cinnamon, I might use the first Unity DVD and preview that as well to see if it doesn't matter the distribution. So far it looks that way.

---

### Post by bra|10n on 2012-09-15
> **Cornova said:**
> Nope, I forgot to mention that it's Cinnamon, I might use the first Unity DVD and preview that as well to see if it doesn't matter the distribution. So far it looks that way.

Could you pull the kernel versions from each of these iso's or desktops as this might be useful...
cheers

---

### Post by Cornova on 2012-09-15
> **bra|10n said:**
> Could you pull the kernel versions from each of these iso's or desktops as this might be useful...
cheers

Kubuntu: 3.2.0-30-Generic
Mint: 3.2.0-23-Generic

I just ran the Mint CD on an old laptop and it doesn't have the font problem.

---

### Post by bra|10n on 2012-09-15
> **Cornova said:**
> Kubuntu: 3.2.0-30-Generic
Mint: 3.2.0-23-Generic

I just ran the Mint CD on an old laptop and it doesn't have the font problem.

It would need to be the same laptop you have experienced the problems with.
From memory you have a high resolution, 2560x1600?

---

### Post by Cornova on 2012-09-15
> **bra|10n said:**
> It would need to be the same laptop you have experienced the problems with.
From memory you have a high resolution, 2560x1600?

The kernals mentioned on are the problem desktop.

Resolution is 1920x1020 or thereabouts. I did try lowering it before.

---

### Post by bra|10n on 2012-09-15
And have you tried that Mint CD on the problem desktop?

---

### Post by Cornova on 2012-09-15
> **bra|10n said:**
> And have you tried that Mint CD on the problem desktop?

Yes and it has the same font problem.

---

### Post by bra|10n on 2012-09-15
I can only suggest you add your 'font experiences' to the link I gave above @forums.kde.
As kde-desktop 4.9.1 has been released and a few users are still experiencing what appears to be vsync issues, then a bug report would be in order...
Any bug report will be referenced in that link also...

---

### Post by Cornova on 2012-09-15
> **bra|10n said:**
> I can only suggest you add your 'font experiences' to the link I gave above @forums.kde.
As kde-desktop 4.9.1 has been released and a few users are still experiencing what appears to be vsync issues, then a bug report would be in order...
Any bug report will be referenced in that link also...

I'll write something up later and cross post them on Mint also to see if anyone has a clue.

---

### Post by Cornova on 2013-02-03
This issue was solved by creating a file named *xorg.conf*, with the following pasted into it and saved to desktop or wherever:

```
Section "Device"
 Identifier "Intel"
 Driver "intel"
 Option "DebugWait" "True"
EndSection
```

Once saved, move xorg.config to /etc/X11/

If you don't have permission to move it, open the terminal and paste the following:

```
sudo chmod 777 /etc/X11
```

Enter password, close the terminal, shutdown/restart the computer.

The solution was [found in this link]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/782855").

---

