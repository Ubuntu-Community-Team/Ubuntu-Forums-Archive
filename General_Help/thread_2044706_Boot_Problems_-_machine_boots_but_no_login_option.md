---
title: "Boot Problems - machine boots but no login option"
date: 2012-08-19
forum: General Help
---

### Post by ShadowMerlin on 2012-08-19
I'm *fairly* new to Linux and very new to Ubuntu.  I set up a server to run as a dedicated list server (postfix/mailman), and for ease of use, also installed the gui.

The system is running a mission-critical list server for a major state-wide organization.  Today we had a power failure.  Upon rebooting, I got "running in low graphics mode" error.  I did a little research and was able to boot up in command line mode.  

I reinstalled ubuntu-desktop, but that didn't help.  I've tried ctl-alt-F7 to switch to terminal mode.  Initially that worked, and I tried to configure grub for text mode, but apparently I didn't do it correctly.  Now, when I try to ctl-alt-F7 from the error screen, the system continues and then the display stops after

                                        Starting web server apache2
                                        Checking battery state...

The system is up and running; mailman is working properly, the web interface is working, but I can't get to a prompt to log in, either text or gui.

The only way I can get into the system is to boot with an install disk and get to files using repair mode.

I need some help to be able to log in to this server.

Please.

---

### Post by oldfred on 2012-08-19
I do not really know servers. But after any power failure on any type of system, you may have to run filechecks. For LInux that is e2fsck or fsck.

#From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1


If server is really mission critical you should have a battery back-up so you can shut down in normal fashion and not have file system issues due to a sudden shutdown.

---

### Post by ShadowMerlin on 2012-08-19
I left out some details.  I did run fsck - no help.

My bad about the battery backup.  I hadn't finished copying archive files from the old machine yet, so I hadn't put the new one physically in place and plugged it in to the ups.

---

### Post by ShadowMerlin on 2012-08-20
UPDATE:

CTL-ALT-F1 gets me to a log-in prompt!!!  [IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG]

Now I just need help getting the gui running again.

---

### Post by ShadowMerlin on 2012-08-21
Everything is back to normal now.  "sudo apt-get install gdm" got me back to where I want to be.

I realize that I had very little direct response to my question, but just having these forum available to browse was sufficient to help me solve my problem.

Thanks to all who post in these forums.

---

### Post by oldfred on 2012-08-21
Glad you got it resolved.

A suggestion.

There is a server sub-forum and if you post there you may get more help on server type issues. Those knowledgeable on may not ofter look at issues in General Help. Having good title also helps if you have an idea of issue or can specify hardware.

---

