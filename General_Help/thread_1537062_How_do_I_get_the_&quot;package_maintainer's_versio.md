---
title: "How do I get the &quot;package maintainer's version&quot; of grub (chose local version!)"
date: 2010-07-23
forum: General Help
---

### Post by bluebrave on 2010-07-23
I'm still pretty new to ubuntu and chose the local version of grub when prompted on the last update.  However, after doing a bit of reading, it looks like I should have selected the "package maintainer's version" :oops:.

I've looked at the release notes ([https://wiki.ubuntu.com/LucidLynx/ReleaseNotes](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes)) related to grub and changing the menu.lst.  However, when I open the menu.lst per the instructions, it is blank (the file opens but there is no text in it).  I also ran the sudo update-grub command but was never prompted to choose a the local version or maintainer's version.

Is there a way to go back and get back to the prompt to select the ""package maintainer's version"?

---

### Post by WorMzy on 2010-07-23
Why do you think that you should have chosen the package maintainers version? update-grub should update your grub.cfg so that the new kernel is available for booting.

---

### Post by bluebrave on 2010-07-23
Basically, when update manager ran, it looked like a new grub version had come out.  Currently on boot, nothing is different.

I currently boot with  2.6.32-21.  I know there are newer versions, but I removed them as they didn't boot right on my laptop (see [http://ubuntuforums.org/showthread.php?t=1384662](http://ubuntuforums.org/showthread.php?t=1384662)).  However, if a new version is out, I would like to try it to see if it works.   Otherwise if there is no security/other issue, I may just stick with the old   2.6.32-21....any thoughts?

One more thing - should I be worried that the menu.lst file is blank when I open it?

---

### Post by WorMzy on 2010-07-23
> if a new version is out, I would like to try it to see if it works. Otherwise if there is no security/other issue, I may just stick with the old 2.6.32-21....any thoughts?

Have a look in /boot, it'll show you what kernels (e.g. vmlinuz-2.6.32-21-generic) are available. They should have been added to grub's boot list when you ran update-grub.

If there were any updates to grub, then running update-grub would also have applied any important changes to grub.cfg, so you don't need to worry; there won't be any substantial changes, just a couple of behind-the-scenes tweaks, probably.

> One more thing - should I be worried that the menu.lst file is blank when I open it? 

No, Ubuntu 10.04 doesn't use the version of grub that uses that file (grub legacy), it uses the most recent grub (grub 2), which does things in a slightly different way.

---

### Post by bluebrave on 2010-07-23
Thank you!  

I took a look and no other new version was in the boot directory, so it looks like I should be in good shape (maybe the update manager was simply adding some behind-the-scenes tweaks...).

Also, thanks for the information on grub2.

I've marked the thread as solved.

---

### Post by mcduck on 2010-07-23
This error isn't usually about the version of any package itself, but instead it's about the configuration files related to that package.

It's basically telling that you have yourself modified some configuration file, and asks if you want to keep on using your modified version or if it should replace it with the one that's in the update package.

In most cases related to Grub (the old Grub, not Grub2) this is a result of bad modifications in the menu.lst file, like moving a Windows (or any other third-party) boot entry into the "debian automagic kernels list"-section of the file, or editing the Linux boot options without doing the same edits in the default options-section.

Such modifications aren't permanent, and would get erased if the menu.lst file was updated as it should be during a kernel update, so you get a warning asking what you want to do.


(And by the way, Ubuntu 10.04 *will* use the old Grub version if you did an upgrade from previous Ubuntu version. It uses grub2 only if you do a fresh install of 10.04).

---

### Post by bluebrave on 2010-07-23
I did modify the grub file to deal with the nvidia smb2 problem I was having on boot (see link at my second comment).  

I also upgraded from 9.10 to 10.04 so does that really mean I am using grub legacy?  If so, then I what happened to the menu.lst file? 

I took a look at the /boot/grub/ directory and it doesn't appear that the menu.lst file even exits - which makes sense, since when I tried opening it with gedit, I only got a blank file.

Finally, if I really have the grub legacy version, how can I upgrade to grub2? 
Is anyone aware of possible issues I may run into by upgrading to grub2?

Thanks.

---

### Post by bluebrave on 2010-07-23
Actually, it does look like I have grub2 based on this: [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

(I also looked up the version and I definitely have grub2).  However, will having the edited grub entry related to the nvidia smb2 'error' (the edit only involved a few words, not even a line of commands) continue to create issues with grub updates?

I assume so, but should I really be concerned?

---

### Post by drs305 on 2010-07-23
You can find which version of Grub you are using in a couple of ways. When booting, the Grub version is displayed at the top of the menu. Grub legacy is 0.97. Grub 2 is version 1.96 or later.

You can also type "grub-install -v" in a terminal.

If you choose to keep your version and later decide you want the latest maintainer's version, one way to get it is to do so from a running Ubuntu install. You uninstall and then reinstall grub-common and grub-pc. [Technically you only have to uninstall grub-common and install grub-pc, the other will be taken care of due to dependencies.] The caveat is that for a few moments you will lose your ability to boot - until you reinstall. So unless your battery is about to run out or you experience an Internet failure at exactly the wrong moment, you should be safe.

If you want to reinstall to get the latest versions, you can run the following commands. I usually make copies of the /etc/grub.d folder and the /etc/default/grub file since these are the ones I modify and the changes will be lost during the reinstallation. If you have made your own custom menu (e.g. /etc/grub.d/06_custom) it won't be deleted.

```
sudo apt-get purge grub-pc grub-common 
sudo apt-get install grub-common grub-pc
```

Note that during your previous upgrade there are other options besides keeping your local version or accepting the installer's version. You can also elect to view the changes first. Added lines are designated with a +, lines to be removed with a -.

Added: The new grub version (1.98-1ubuntu7) changes the display options on where to install grub. It now only shows /, /boot and /boot/grub partitions (to reduce the chance of installing it in the wrong place). That is the only major change in the latest version on Ubuntu.

---

### Post by bluebrave on 2010-07-23
Thanks, drs305.  i entered the command in the terminal and I do currently have the latest grub version (1.98-1ubuntu7) so I won't worry about the manager update for now.  Next time I'm prompted I'll know what to do.

Thanks for everyone's help.

---

