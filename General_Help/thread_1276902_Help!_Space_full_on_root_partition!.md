---
title: "Help! Space full on root partition!"
date: 2009-09-27
forum: General Help
---

### Post by patrick365 on 2009-09-27
I moved some files over to a directory on my root partition temporarily to free up some space somewhere else, and stupidly I used up almost all of my remaining space on my root partition. After rebooting, I see that all of my free space on the root partition is used up, and I can't login as root to do anything! Trying to use Synaptic package manager, for instance (which usually requires my root password) gives me the error 'Failed to run /usr/sbin/synaptic as user root. Unable to copy the user's Xauthorization file.' Same for trying to use other things that usually require this password. What's worse is that when I try to login as root to delete files on my root partition and clear some space, I get a similar error: 'Failed to run nautilus as user root. Unable to copy the user's Xauthorization file.', with the terminal window reading 'No space left on device'.

Have I encountered a problem here that is impossible to solve? Is there anyway I can delete some files in my root partition without logging in as root, so that I can then login as root as normal and clear up more space?

(I'm running Ubuntu 8.04 (Hardy Heron))

---

### Post by drs305 on 2009-09-27
Can you run this or right click on your Trash bin to empty trash (if HOME is on your / partition)?:
```

rm -r $HOME/.local/share/Trash

```

If you can gain a bit of space, then you can run:
```

sudo apt-get clean

```
to empty your program cache.

Once you a bit of breathing room, you can investigate. Most often it is undeleted root trash, large log files, or backups made to the system partition because the backup partition wasn't mounted at the time of the backup.

This guide will help you investigate and solve your space problems:
[URL="http://ubuntuforums.org/showthread.php?t=1122670"]HOWTO: Recover Lost Disk Space
[/URL]

---

### Post by patrick365 on 2009-09-27
My trash was already empty (and my home is on a different partition than my root anyway), but I was able to run sudo apt-get clean . Now I'm being told I have a few megabytes of free space on root and am able to login as root, but deleting files on the root partition doesn't seem to be freeing up space. Any idea why this is happening?

---

### Post by ajgreeny on 2009-09-27
Use a live CD to move files from your root filesystem (where you should not really put files just for storage) on to a usb drive or somewhere else.  You will probably see that this just copies files, and does not move them out of root, so you will then need to totally delete them from your root system, either by using shift+delete or adding the delete files option in the live CD's nautilus preferences.  If you just hit the delete button alone, the files will just go into root's trash, and no extra space will be freed.

EDIT
Just seen your comment about sudo apt-get clean, etc, but see my comment about deleting files from trash now, as you may again need to empty root trash.

---

### Post by drs305 on 2009-09-27
> **patrick365 said:**
> My trash was already empty (and my home is on a different partition than my root anyway), but I was able to run sudo apt-get clean . Now I'm being told I have a few megabytes of free space on root and am able to login as root, but deleting files on the root partition doesn't seem to be freeing up space. Any idea why this is happening?

Trash continues to take up space until it is removed. The safest way to remove it is probably opening a root nautilus window. Use SHIFT-DEL to delete the entire Trash folder/subfolders (info and files). They will be recreated when needed. Using DEL will move it to the ... Trash!

```

gksu nautilus /root/.local/share/

```

If you don't review the other link I provided, this one deals specifically with the Trash issue:
[http://ubuntuforums.org/showthread.php?t=898573]("http://ubuntuforums.org/showthread.php?t=898573")

---

### Post by patrick365 on 2009-09-27
Thanks drs, gksu nautilus /root/.local/share/ showed me my trash and allowed me to shift+delete it, which solves my initial problem. Thanks for the help!

One more thing: how much free space is reccommended to be kept on the root partition?

Also, strangely, clicking on the 'Trash' link on the pane on the left when I'm in a nautilus window logged in as root gives me the error 'The folder contents could not be displayed. Sorry, couldn't display all the contents of "trash": Operation not supported'. Any idea why this would be happening?

---

### Post by drs305 on 2009-09-27
> **patrick365 said:**
> One more thing: how much free space is reccommended to be kept on the root partition?

It would depend on a lot of factors and I can't really give you a definitive answer. In part it depends on your habits regarding update frequency, how often you delete things as root, and how disciplined you are in keeping the 'cruft' out of /.

You have /home on a separate partition so accumulation of data files shouldn't be a problem You want to consider how often you do updates. These files will be downloaded to /var/cache/apt/archives. You can remove them with the "clean" command you used previously, but if you didn't run the clean command often or if you wait and do updates when you might download a lot of packages at once, you would need more free space. These updates generally are well less than 500KB for me, but I update often. And remember the packages will take up more space during the install.

If you delete really large files as root, they can fill up your system quite fast. 

I tend to keep at least a few GBs free, but I have enough disk space to spare. 

I don't know why the left pane Nautilus reacts the way it does - the behavior is the same on my machine.

---

