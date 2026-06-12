---
title: "hard drive crapped out"
date: 2011-12-30
forum: General Help
---

### Post by solaralchemy on 2011-12-30
I have a dell vostro laptop and have had it for about two years.
I have had various linux distros on it I was curently running mint nine on it. About two weeks ago my dell crapped out on me I have not had much time to tool around with it until now.
Fortunately I have an older and seemingly more robust computer that I have been using to get online.
Unfortunately I have a lot of files on the dell computer that I never got around to backing up and that I need to recover.

Late one night two weeks ago i had just finished an image file in gimp for a friend and had emailed it to her.
I decided to go for a walk and came back to see my computer was off(I had left it on)

When I pressed the power button the blue bar took a long time to fill up and when it  did it went to a screen that gave a bunch of technical jargon on what I believe was the hard drive
then it would say..........
OS not found
I did manage to boot into a live CD and after I did that I was able to do a normal boot that logged into my normal setup
with my files...(Wish I had my thumb drive ready)
but then that eventually crashed.
so I have been trying to find the drive in live mode with no luck
I tried following this
[http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/](http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/)
with the exception that I'm not running windows.
Unfortunately I do not see any drives to mount.
Nothing shows up except what is already on the live disk.
I'm really afraid the drive is dead.
if anybody has any suggestions or fixes I would be grateful.

---

### Post by dandnsmith on 2011-12-30
fdisk or gparted should show up any drives which are accessible.
If that disk isn't recognised there, then you should try some recovery software (but I haven't found any I could really recommend).

If you can get to the BIOS display, it should be able to tell whether it even considers a drive to be found - I forget whether that OS not found message comes from the BIOS or the first stage boot from HDD.

---

### Post by Paqman on 2011-12-30
First thing I would do is boot up into a LiveCD or USB and see if you can mount that drive. If you can, salvage all your data pronto.

Depending on what's wrong with the drive it's quite likely that you'll be able to mount it and read most/all of the contents.

Incidentally, do you have backups? If not, this might be a good opportunity to start thinking about a bombproof backup plan for the future. Hard drives always fail eventually.

---

### Post by solaralchemy on 2011-12-30
already tried mounting in live mode no luck.
And I was a dummy who pressed his luck and did not back up anything.

I figured i could always back it up some other time things like this happened to other people......................live and learn

---

