---
title: "Copying large file blocks externally causes disk full"
date: 2010-10-15
forum: General Help
---

### Post by theronb on 2010-10-15
I've looked for this question but haven't seen it posted before. This has happened several times now, with 9.10 and 10.04. I back up my photos periodically to external drives, using Nautilus. At the next attempted login Gnome won't start and sometimes gives power manager incorrect installation error. 

First time this happened I was stumped and eventually did a clean install. Second time, I found advice elsewhere in this forum to solve this by emptying root trash, which did the trick. This time, however, root trash has nothing in it and 2 users trash were insignificant (I emptied them all anyway with rm -r). Tried looking for enormous directories but couldn't find a smoking gun. I would rather not end up doing another clean install - a painful and extreme solution. 

I'm continuing to look for solutions to the immediate problem, but my question really is, what causes this and how do I prevent it in the future? I've run Computer Janitor regularly and ran apt-get clean but no help. Should I do all my large scale copying from terminal? I'm not a total noob, but close.

---

### Post by coffeecat on 2010-10-15
I wonder if this is the problem:

> **theronb said:**
> I've run Computer Janitor regularly

From what I've read, computer janitor is somewhat - ahem - overenthusiastic. I've just opened it up and help tells me "This application helps you find and remove software packages you might not need any more" except that it's listing at least three  packages/apps I definitely don't want to lose and one of which I used only a couple of hours ago.

Failure of gnome to start and an incorrect installation error sounds more like missing dependencies and packages than bulging trash folders. I wonder if Computer Janitor has removed something essential.

I don't know how to fix this because we don't know what CJ removed, but this following won't do any harm. Open System > Administration > Synaptic. Go to the Edit menu and try 'Fix broken packages'. If this doesn't seem to do much, mark the ubuntu-desktop package for re-installation. (But only if you're running the standard gnome version of Ubuntu.) The package ubuntu-desktop is a so-called meta-package which has as dependencies all the many packages needed for a complete Ubuntu gnome desktop. Hopefully, by re-installing that it will bring in anything CJ might have removed.

Lastly, while you still have Synaptic open you might want to uninstall computer-janitor.

---

### Post by theronb on 2010-10-15
Thanks, coffeecat - will do, as soon as I get enough disk space back to load Gnome and run the gui. I have /home/ in a separate partition and the root partition (74 G) is full, so I'm trying to track down what and where. Will also check my automatic backup settings, as I understand that can cause escalation of fullness.

---

### Post by coffeecat on 2010-10-15
> **theronb said:**
> I have /home/ in a separate partition and the root partition (74 G) is full, so I'm trying to track down what and where.

Whoa! Hold back on my earlier suggestions just for the moment. Something is seriously awry there. So long as you haven't been storing video files or something on the root partition, I cannot see how it could contain 74GB. With a separate /home it should only contain the OS and apps and even if you installed everything in the repositories, I should think you wouldn't get anything like 74GB.

> **theronb said:**
> Will also check my automatic backup settings, as I understand that can cause escalation of fullness.     

What were you using? I can't remember the details, but there was something about a backup app in the repository that did something like this. A seriously bad design flaw in the app iirc.

---

### Post by theronb on 2010-10-15
Thanks for the quick reply! Don't remember the name of the backup app right now and can't get into the menu to check. I may have identified a (the?) immediate problem - 67 GB in / is attributed to /media/Free Agent, a usb drive that is no longer plugged in. I tried to unmount it before removing but I've seen comments that partition names with spaces don't behave well. I just tried unmounting it again with umount -a but the system thinks it's still there. Any suggestions?

---

### Post by coffeecat on 2010-10-15
> **theronb said:**
> Thanks for the quick reply! Don't remember the name of the backup app right now and can't get into the menu to check. I may have identified a (the?) immediate problem - 67 GB in / is attributed to /media/Free Agent, a usb drive that is no longer plugged in. I tried to unmount it before removing but I've seen comments that partition names with spaces don't behave well. I just tried unmounting it again with umount -a but the system thinks it's still there. Any suggestions?

That's very curious because mountpoints in /media should be autodeleted as soon as you  unplug the mounted filesystem, even if you haven't gracefully unmounted it. The comments about spaces in filenames and folders is simply to do with the complication of referencing them in the terminal. You can get round a space by escaping it with the backslash character.

The other curious thing is that if the usb drive is unplugged or unmounted, the 67GB shouldn't be showing up at all.

Anyway, try this:

```
sudo umount /media/Free\ Agent
```If that doesn't make any difference, try rebooting without the Free Agent drive plugged in. I'd be tempted to try to delete the mountpoint (if it's still there) but let's see what a reboot will do. 

By the way, you don't have an entry for "Free Agent" in your /etc/fstab, do you?

---

### Post by The Cog on 2010-10-15
Hmm. I wonder if somehow the FreeAgent drive got unmounted and the pictures got written to the mount point directory on the root filesystem instead of the external drive. coffeecat's suggestions are good ones and should show up whether this is the case. If so, be warned that you probably don't have a backup of those files on the external drive.

---

### Post by theronb on 2010-10-15
Thanks, both! Good news is that the backup went to a different USB drive - I had removed Free Agent a while ago because of problems mounting and unmounting, so I do have the backups.

Tried umount with the \escaped space, no result; rebooted and it's still there in /media when I ls. Checked fstab and it's not listed - here are the contents:

/device/sda1: /
/device/sda3: /home
/device/sda5: swap

...and that's all. Tried plugging Free Agent in, rebooted, ran umount again, unplugged, rebooted, still there. Ran umount again (yes, using sudo) and it tells me it's not mounted but it still shows up when I ls for /media. I'm confused.

I'm downloading 10.10 (and so is everyone else, apparently) as my last report plan. Thanks goodness for a second machine.

---

### Post by coffeecat on 2010-10-15
I wonder if The Cog's suggestion that many GB of files got copied to the mountpoint at some point when the Free Agent drive was not mounted. You can mount a drive to a folder which has contents but when you do, the contents "disappear" from sight for the the time being.

Try this. **Don't** mount the Free Agent drive or, better still, boot up with it not plugged in. At least then we'll know that whatever you see in the mountpoint is not on the Free Agent drive. Go to the Places menu and open a 'Computer' Nautilus window. Double-click on filesystem and then navigate to /media/Free\ Agent. Do you see anything there? If there are 67GB of files and you are confident you have backed them up, you can delete them. Check the ownership first - they might be owned by root. If so you'll need to use a 'gksu nautilus' or 'sudo rm' from the terminal, not forgetting that from the terminal the folder will be '/media/Free\ Agent'.

Let us know how you get on. I'm intrigued.

---

### Post by theronb on 2010-10-15
TAADAA! Couldn't use the menu commands because Gnome wouldn't start, but did essentially the same thing in terminal. Free Agent had two large SimpleBackup files but I couldn't get in with sudo, had to switch to root with sudo -i (I know, but I was getting desperate). Removed everything in Free Agent, then used rm -r to delete Free Agent, which worked. Does this confirm Cog's hypothesis? Anyway, now I can start Gnome and everything appears to be normal.

Also, does this mean you can't mount an external drive to a partition that is small in size than the contents of the external drive or was that only a problem because of the misallocated files?

Thanks so much to both of you for your time, thoughtful responses and courtesy! One reason I love Ubuntu is the community.

---

### Post by The Cog on 2010-10-15
> Also, does this mean you can't mount an external drive to a partition that is small in size than the contents of the external drive 
No. What happens when you plug an external drive in is that it automatically creates an empty directory in /media to use a s a mount point. It then mounts the external drive to that mount point so that the directory contents are stored on the external drive. The only space needed on the / partition fot this is the few bytes needed to store the empty directory. 

What seems to have happened here is that the mount point directory was created but mount has gone wrong or failed somehow. So then the backup files went into the empty directory in the root partition instead of going into the external drive.

Probably, next time you plugged the drive in, it created /media/FreeAgent-1 or something like that because FreeAgent was already taken.

---

### Post by theronb on 2010-10-15
That is, indeed, exactly what I found. The full path of the original drive was /media/FreeAgent Drive and that is one that had 67 GB in it. There was also a /media/FreeAgent Drive_ that was empty, apparently the second mount point. Thanks!

---

### Post by coffeecat on 2010-10-16
And I believe SimpleBackup was the utility that was giving similar problems. I'm going from memory here, so you might want to check this. Quite how an automounted drive could get unmounted but the dynamic mountpoint remain, I don't know. Perhaps SimpleBackup has something to do with this. It would be worth investigating.

---

### Post by dcstar on 2010-10-16
> **coffeecat said:**
> And I believe SimpleBackup was the utility that was giving similar problems. I'm going from memory here, so you might want to check this. Quite how an automounted drive could get unmounted but the dynamic mountpoint remain, I don't know. Perhaps SimpleBackup has something to do with this. It would be worth investigating.

Apps copying to removable drives need to be smart enough to know a removable drive is actually there or you need to write a script to detect if a mount point is an actual mounted filesystem or just a folder before starting the backup app.

This sort of issue is all too common with some apps simply creating the backup destination folder if it does not already exist instead of stopping with an error.

BTW, there is a shell command called **mountpoint** which does the job.

---

### Post by theronb on 2010-10-18
Now that everything is working again, I plugged in the same FreeAgent usb drive, then tried to unmount it but it will not respond to either GUI or terminal unmounting. This is a NFTS formatted drive; would ext3 or ext4 be more likely to behave properly?

---

