---
title: "Strange problems in Kubuntu 9.04 (9.10?)"
date: 2011-02-04
forum: General Help
---

### Post by SydneyGB on 2011-02-04
On my Dell Inspiron 1545, KDE has been behaving oddly for some time, but in the last week or two the the plasma desktop, while running, has not displayed the wallpaper or the comma.  I decided to update (or is it upgrade?) my packages as suggested by the Update Manager.

My original install was Jaunty, and until the package update I did yesterday, Update Manager was offering me to upgrade to Karmic (9.10).  Now it's offering to upgrade to Lucid (10.4), so I'm assuming I'm now running (a fouled-up) Karmic.  On reboot after the update, my touchpad failed to work (but I have a USB mouse I like better anyhow), and I've discovered my sound doesn't work any more.  The speakers pop a time or two on boot and desktop loading.  Also, I still have no Plasma desktop in KDE.  This machine has about five wms installed, so I've fallen back to Gnome for the moment.

Evolution displays my folders but says there's nothing in them and won't download new mail.  I did a restore of my last Evo backup, to no avail.  Simple Backup Restore has done apparently nothing, as it runs the drive for a minute, then goes idle.

I wish I had more concrete details about the weirdnesses that are going on, but this machine has been acting oddly for a few months.  I'd like some opinions on what I might do to get it working correctly again short of slapping in a  Kubuntu 10.10 disc and starting over.  I'm confused as to which version I'm currrently running, as Jaunty repositories still appear on my software sources list.  I know Jaunty is out of support, so this confuses me a bit.  I've been using Ubuntu for nearly two years and this is my first upgrade encounter on this machine.  My next plan was to uninstall KDE entirely from Gnome and reinstall it.  KDE is my favourite WM and I really miss it.

Apologies for what must sound like ravings.  I've not kept track of what's what with this machine as I ought to have. I'm hoping someone out there will take pity on me and give me some tips on how to help this poor machine.

---

### Post by SydneyGB on 2011-02-04
Are there any diagnostics I can run to get some concrete data on what's going on?  I'm still a newbie when it comes to the nuts and bolts of Linux systems.  I'd appreciate some help here.

---

### Post by ankspo71 on 2011-02-05
Hi,
To check your Ubuntu/Kubuntu version, Paste this command in your terminal then press enter:
```
cat /etc/lsb-release
```

If you are running ubuntu/kubuntu 9.10, disable all of the 9.04 repositories. You can do this in your package manager (synaptic, kpackagekit, etc)

If you believe your repositories are too messed up to work with, you can go here to generate a new sources list:
[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)
Then paste the contents it generates into your /etc/apt/sources.list file.
OR 
You can simply copy the /etc/apt/sources.list file from a running Ubuntu 9.10 live cd, then use it to replace the /etc/apt/sources.list file that is on the hard drive.

After doing either of the above, go check for any updates and install them. You might even want to try reinstalling KDE and any other items you are having trouble with.

As far as the KDE related problems go, look inside your home folder for a hidden directory called ".kde". Rename that folder to ".kde-backup". This will restore all of your personal KDE settings, and KDE will recreate this folder when necessary. Now log out of Gnome, then try to log back into KDE again. If KDE continues to fail to work, then it is not because of the KDE settings in your home folder... The problem would be elsewhere.

Hope this gives you some ideas.

---

### Post by SydneyGB on 2011-02-05
Thanks for your reply.  I've updated the repositories to Karmic as you suggested, since my lsb-release says I've got Karmic.  Update Manager now wants to do a 'partial upgrade' which will take several hours.  Here's where I'm uncertain: I also have a distro upgrade available, which I don't want to do just yet (to Lucid - had some graphics issues with that on other machines).  By doing this 'partial upgrade', I won't be upgrading to Lucid, will I?  It'll just repair the bad packages (it does give a long list) and leave me with Karmic?  As a long-time Windows user, I've learned to fear system updates/upgrades, so it may be unsubstantiated worry.  

I've opted to uninstall KDE entirely and reinstall it.  Renaming the .kde file prompted some odd changes.  My desktop became visible, but the only usable bit was about twenty pixels along the top of the screen, where part of a panel that usually lives at the bottom of the screen was displayed.  The correct menu displayed when I right-clicked on that portion, but nothing happened on right-clicking on the rest of the screen.  *shrug*  Hopefully a reinstall of KDE will help. :)

---

### Post by ankspo71 on 2011-02-06
Hi,
You can turn off notifications for new distribution releases in Synaptic Package Manager: menu ->  Settings -> Repositories -> Updates -> "Release Upgrade: Show New Distribution Releases"; change it to Never in the dropdown menu.

The same can be done by going to software sources in the System menu of your Gnome desktop, or by running "gksudo software-properties-gtk" in the terminal.

I recommend rebooting after that. The above will help ensure that updating your system will not automatically uprade to a new distribution release. You can then safely update your system.

On a side note: Kubuntu/KDE doesn't support distribution release upgrades and that is why Kubuntu itself doesn't have a convenient way to upgrade to new releases, but as you already know Ubuntu does. I don't know why this is but I figured it might be worth mentioning.

Hope this helps.

---

