---
title: "Screen freezes after Splash screen; Uprgraded from intrepid to jaunty"
date: 2009-09-18
forum: General Help
---

### Post by TheLifeRuiner on 2009-09-18
Yesterday, I upgraded to 9.04. Everything seemed to install fine, until I restarted my computer. Instead of hitting the login screen, a black screen with some scratchy-looking stuff - I've included an image attachment of it. This is the first problem I haven't been able to find on the forums, or anywhere else. I thought maybe it was GDM, so I did the Esc@GRUB, chose the first recovery kernel or w/e, went into root, and tried restarting. It failed the first two times, so I reinstalled it twice, and after the second reinstall, it finally said [OK] when it started up. That didn't solve my problem though. I also tried logging in from root and then booting up with startx, but it goes to the same scratchy screen. Sometimes, the screen will blink, and then the scratchy image will change...but I don't think that's important...

recap:
computer boots, starts loading on the splash screen, then freezes I guess, at which point I can do nothing.

If someone could help, it'd be greatly appreciated.

Sorry if this topic HAS already been covered, or if I posted in the wrong forum.

---

### Post by grikdog on 2009-09-18
Are you using ext4 and more than one big partition (plus swap)?  I had a similar problem.  Had to boot from USB, repartition, reinstall (ext3) and restore from backup.  No worries now.

I'm not SURE it's ext4, mind.  I'm almost positive there's a major memory leak of some kind involved, because in my case, the screen just before login was torn apart by streaks of random garbage.  If you restarted instead of cold booted, the streaks resolved (partially) into a torn up version of my wallpaper.

This finally locked up and nothing worked to recover.  I used the USB flash version of LiveCD and ran fdisk.  No problems.  Everything is ok now.  So far.  Jaunty here.

---

### Post by TheLifeRuiner on 2009-09-18
I found out it's because xorg 1.6 doesn't support my graphics card. I need to backport to 1.5: [http://ubuntuforums.org/showthread.php?t=1171445](http://ubuntuforums.org/showthread.php?t=1171445)
That or reinstall...

---

