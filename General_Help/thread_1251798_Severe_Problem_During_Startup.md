---
title: "Severe Problem During Startup"
date: 2009-08-28
forum: General Help
---

### Post by ZekeDragon on 2009-08-28
I've been happily using my Ubuntu Intrepid Ibex box for about 8 months now, without any issues that couldn't be fixed with a quick sudo. However, this day it would seem that the fates have conspired against me and now I cannot fix my problem no matter how hard I try.

Today someone asked if they could have a user account on my computer, and of course I was more than happy to accommodate them. I set up their user name as usual, and put in my sudo password. After about 30 seconds where the computer was setting things up... I... guess... it returned control to me and showed me it had completed the instructions. I happily left the machine to it's own devices, and continued doing what I wanted to do from thereon. At some point, I gave another sudo command, only to be told "*MY_USERNAME is not in the sudoers file. This incident will be reported.*" After about two or three more hours of using my machine, I started having internet trouble, and in the process of fixing it, my machine **completely froze**. To say the least I was perturbed, I've never seen Ubuntu freeze in my life, and to have it do so bothered me. I wasn't doing anything weird either, simply browsing the web, going on forums, and programming in NetBeans.

Anyway, I performed a hard restart of the machine (I wasn't given much of a choice). The machine began starting up as normal, going into Splashy (which had already been working for months), and then exiting splashy after the timeout had occured (120 seconds). I wasn't too worried, whenever my machine needed to do a normal boot it required this, since it takes much longer when it doesn't have a decompressed boot record to go by. Anyway, it continued on it's merry way until this (**IMG:** [Figure 1]("http://img194.imageshack.us/img194/1195/imgp0362.jpg")) happened.

It only got worse. I was greeted with a blue screen containing this (**IMG:** [Figure 2]("http://img194.imageshack.us/img194/3901/imgp0366w.jpg")), indicating that apparently a great deal of user information had been completely hosed, with the only indication as to why being that I made a new user in my computer. I accepted it, and it then proceeded to ask me to login VIA the command line, apparently completely incapable of getting to the GUI desktop (**IMG:** [Figure 3]("http://img268.imageshack.us/img268/2411/imgp0363a.jpg")). I logged in and persisted to try and use sudo commands, where I was repeatedly told that my account was not in the sudoers file and to go screw myself. I'm the only user of this machine, I have no idea how I can NOT be in the sudoers file.

What I'm asking is how I could rectify this in my machine. Assuming I can gain access to it VIA a command line without sudo access, is there something I can do? If that's not an option, can I use a LiveCD to access the hard drive and fix this? Absent any other possibilities, am I left with no option other than to reinstall my Ubuntu installation? This would be a massive inconvenience, but if that is the case, could I be informed as to how to install only the / drive locations with etc and other information, and not replacing my /usr and /home directories (both of these directories are on separate partitions, so this should theoretically be possible). I appreciate any help I can get in fixing this, and I'll answer any questions you may have as quickly as possible.

---

### Post by P4man on 2009-08-28
ive seen someone else post a similar horror story here recently, where all user groups where deleted. It looks a lot like this bug:

[https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/187147](https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/187147)

Im not sure how to recover from that. Someone in that thread mentions "Recovered by using passwd, shadow and group files from a live session." but I wouldnt know how to do that exactly. Assuming it is your problem. I'll see if I can find the other thread, it was only a day ago or so..

---

### Post by P4man on 2009-08-28
here, read this, from post 7 onwards:

[http://ubuntuforums.org/showthread.php?t=1050113](http://ubuntuforums.org/showthread.php?t=1050113)

---

### Post by ZekeDragon on 2009-08-28
That seems helpful, P4man, I'll put in a LiveCD and see if I can replace the broken file (/etc/group) and I'll post my results. I'll also post any and all logs I have relating to this issue to help it get resolved and perhaps help others who face it.

---

### Post by P4man on 2009-08-28
Post in the bug report on launchpad as well. This is the kind of bugs we really dont need!

[https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/160862](https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/160862)

---

### Post by HiImTye on 2009-08-28
if youre in recovery mode (from GRUB) you don't need to sudo just type in commands as if you were in a root terminal (because you are)

---

### Post by Copernicus1234 on 2009-08-28
Wow. This seems like a serious bug...

---

### Post by P4man on 2009-08-28
yeah. dont understand why its labeled "low importance" on launchpad. If this is not a critical bug, then what is?

---

### Post by ZekeDragon on 2009-08-28
Okay, here's where I'm at so far.

This is what my auth.log reports:
```
Aug 27 14:30:35 zeke-comp sudo: zekedragon : TTY=unknown ; PWD=/home/zekedragon ; USER=root ; COMMAND=/usr/sbin/gdmsetup
Aug 27 14:32:37 zeke-comp polkit-grant-helper[18900]: granted authorization for org.freedesktop.systemtoolsbackends.self.set to pid 18876 [uid=1000] [auth=zekedragon]
Aug 27 14:32:38 zeke-comp usermod[18907]: change user `zekedragon' password
Aug 27 14:32:49 zeke-comp polkit-grant-helper[18918]: granted authorization for org.freedesktop.systemtoolsbackends.set to pid 18876 [uid=1000] [auth=zekedragon]
Aug 27 14:35:16 zeke-comp groupdel[18941]: remove group `adm' 
Aug 27 14:35:16 zeke-comp groupdel[18947]: remove group `admin' 
Aug 27 14:35:17 zeke-comp groupdel[18963]: remove group `cdrom' 
Aug 27 14:35:17 zeke-comp groupdel[18969]: remove group `crontab' 
Aug 27 14:35:17 zeke-comp groupdel[18977]: remove group `dialout' 
Aug 27 14:35:17 zeke-comp groupdel[18983]: remove group `dip' 
Aug 27 14:35:17 zeke-comp groupdel[18989]: remove group `disk' 
Aug 27 14:35:18 zeke-comp groupdel[18997]: remove group `fax' 
Aug 27 14:35:18 zeke-comp groupdel[19003]: remove group `floppy' 
Aug 27 14:35:18 zeke-comp groupdel[19009]: remove group `fuse' 
Aug 27 14:35:19 zeke-comp groupdel[19029]: remove group `kmem' 
Aug 27 14:35:20 zeke-comp groupdel[19041]: remove group `lpadmin' 
Aug 27 14:35:20 zeke-comp groupdel[19053]: remove group `mlocate' 
Aug 27 14:35:20 zeke-comp groupdel[19059]: remove group `netdev' 
Aug 27 14:35:21 zeke-comp groupdel[19069]: remove group `nvram' 
Aug 27 14:35:21 zeke-comp groupdel[19075]: remove group `operator' 
Aug 27 14:35:21 zeke-comp groupdel[19081]: remove group `plugdev' 
Aug 27 14:35:22 zeke-comp groupdel[19093]: remove group `pulse-access' 
Aug 27 14:35:22 zeke-comp groupdel[19099]: remove group `pulse-rt' 
Aug 27 14:35:22 zeke-comp groupdel[19107]: remove group `sambashare' 
Aug 27 14:35:22 zeke-comp groupdel[19115]: remove group `sasl' 
Aug 27 14:35:22 zeke-comp groupdel[19121]: remove group `scanner' 
Aug 27 14:35:23 zeke-comp groupdel[19127]: remove group `shadow' 
Aug 27 14:35:23 zeke-comp groupdel[19133]: remove group `src' 
Aug 27 14:35:23 zeke-comp groupdel[19139]: remove group `ssh' 
Aug 27 14:35:23 zeke-comp groupdel[19145]: remove group `ssl-cert' 
Aug 27 14:35:23 zeke-comp groupdel[19151]: remove group `staff' 
Aug 27 14:35:23 zeke-comp groupdel[19157]: remove group `sudo' 
Aug 27 14:35:24 zeke-comp groupdel[19167]: remove group `tape' 
Aug 27 14:35:24 zeke-comp groupdel[19173]: remove group `tty' 
Aug 27 14:35:24 zeke-comp groupdel[19179]: remove group `users' 
Aug 27 14:35:24 zeke-comp groupdel[19185]: remove group `utmp' 
Aug 27 14:35:24 zeke-comp groupdel[19193]: remove group `video' 
Aug 27 14:35:25 zeke-comp groupdel[19199]: remove group `voice' 
Aug 27 14:35:25 zeke-comp groupdel[19205]: remove group `winbindd_priv' 
Aug 27 14:35:26 zeke-comp usermod[19220]: change user `avahi' GID from `121' to `65534'
Aug 27 14:35:26 zeke-comp usermod[19220]: change user `avahi' password
Aug 27 14:35:26 zeke-comp usermod[19226]: change user `avahi-autoipd' GID from `112' to `65534'
Aug 27 14:35:26 zeke-comp usermod[19226]: change user `avahi-autoipd' password
Aug 27 14:35:26 zeke-comp usermod[19232]: change user `backup' GID from `34' to `65534'
Aug 27 14:35:26 zeke-comp usermod[19232]: change user `backup' password
Aug 27 14:35:26 zeke-comp usermod[19238]: change user `bin' GID from `2' to `65534'
Aug 27 14:35:26 zeke-comp usermod[19238]: change user `bin' password
Aug 27 14:35:26 zeke-comp usermod[19244]: change user `daemon' GID from `1' to `65534'
Aug 27 14:35:26 zeke-comp usermod[19244]: change user `daemon' password
Aug 27 14:35:26 zeke-comp useradd[19253]: new user: name=evelyn, UID=1001, GID=0, home=/home/evelyn, shell=/bin/bash
Aug 27 14:35:26 zeke-comp usermod[19260]: change user `evelyn' password
Aug 27 14:35:26 zeke-comp chfn[19265]: changed user `evelyn' information
Aug 27 14:35:26 zeke-comp usermod[19270]: change user `evelyn' password
Aug 27 14:35:26 zeke-comp usermod[19282]: change user `games' GID from `60' to `65534'
Aug 27 14:35:26 zeke-comp usermod[19282]: change user `games' password
Aug 27 14:35:26 zeke-comp usermod[19288]: change user `gdm' GID from `113' to `65534'
Aug 27 14:35:26 zeke-comp usermod[19288]: change user `gdm' password
Aug 27 14:35:26 zeke-comp usermod[19294]: change user `gnats' GID from `41' to `65534'
Aug 27 14:35:26 zeke-comp usermod[19294]: change user `gnats' password
Aug 27 14:35:26 zeke-comp usermod[19300]: change user `guest' GID from `127' to `65534'
Aug 27 14:35:26 zeke-comp usermod[19300]: change user `guest' password
Aug 27 14:35:26 zeke-comp usermod[19306]: change user `haldaemon' GID from `122' to `65534'
Aug 27 14:35:26 zeke-comp usermod[19306]: change user `haldaemon' password
Aug 27 14:35:26 zeke-comp usermod[19312]: change user `hplip' GID from `7' to `65534'
Aug 27 14:35:26 zeke-comp usermod[19312]: change user `hplip' password
Aug 27 14:35:26 zeke-comp usermod[19318]: change user `irc' GID from `39' to `65534'
Aug 27 14:35:26 zeke-comp usermod[19318]: change user `irc' password
Aug 27 14:35:26 zeke-comp usermod[19324]: change user `klog' GID from `103' to `65534'
Aug 27 14:35:26 zeke-comp usermod[19324]: change user `klog' password
Aug 27 14:35:26 zeke-comp usermod[19330]: change user `libuuid' GID from `101' to `65534'
Aug 27 14:35:26 zeke-comp usermod[19330]: change user `libuuid' password
Aug 27 14:35:26 zeke-comp usermod[19336]: change user `list' GID from `38' to `65534'
Aug 27 14:35:26 zeke-comp usermod[19336]: change user `list' password
Aug 27 14:35:26 zeke-comp usermod[19342]: change user `lp' GID from `7' to `65534'
Aug 27 14:35:26 zeke-comp usermod[19342]: change user `lp' password
Aug 27 14:35:26 zeke-comp usermod[19348]: change user `mail' GID from `8' to `65534'
Aug 27 14:35:26 zeke-comp usermod[19348]: change user `mail' password
Aug 27 14:35:26 zeke-comp usermod[19354]: change user `man' GID from `12' to `65534'
Aug 27 14:35:26 zeke-comp usermod[19354]: change user `man' password
Aug 27 14:35:26 zeke-comp usermod[19360]: change user `messagebus' GID from `119' to `65534'
Aug 27 14:35:26 zeke-comp usermod[19360]: change user `messagebus' password
Aug 27 14:35:26 zeke-comp usermod[19366]: change user `news' GID from `9' to `65534'
Aug 27 14:35:26 zeke-comp usermod[19366]: change user `news' password
Aug 27 14:35:26 zeke-comp usermod[19372]: change user `polkituser' GID from `120' to `65534'
Aug 27 14:35:26 zeke-comp usermod[19372]: change user `polkituser' password
Aug 27 14:35:26 zeke-comp usermod[19378]: change user `proxy' GID from `13' to `65534'
Aug 27 14:35:26 zeke-comp usermod[19378]: change user `proxy' password
Aug 27 14:35:27 zeke-comp usermod[19384]: change user `pulse' GID from `115' to `65534'
Aug 27 14:35:27 zeke-comp usermod[19384]: change user `pulse' password
Aug 27 14:35:27 zeke-comp usermod[19390]: change user `root' GID from `0' to `65534'
Aug 27 14:35:27 zeke-comp usermod[19390]: change user `root' password
Aug 27 14:35:27 zeke-comp usermod[19396]: change user `saned' GID from `118' to `65534'
Aug 27 14:35:27 zeke-comp usermod[19396]: change user `saned' password
Aug 27 14:35:27 zeke-comp usermod[19402]: change user `speech-dispatcher' GID from `29' to `65534'
Aug 27 14:35:27 zeke-comp usermod[19402]: change user `speech-dispatcher' password
Aug 27 14:35:27 zeke-comp usermod[19408]: change user `sys' GID from `3' to `65534'
Aug 27 14:35:27 zeke-comp usermod[19408]: change user `sys' password
Aug 27 14:35:27 zeke-comp usermod[19414]: change user `syslog' GID from `102' to `65534'
Aug 27 14:35:27 zeke-comp usermod[19414]: change user `syslog' password
Aug 27 14:35:27 zeke-comp usermod[19420]: change user `uucp' GID from `10' to `65534'
Aug 27 14:35:27 zeke-comp usermod[19420]: change user `uucp' password
Aug 27 14:35:27 zeke-comp usermod[19426]: change user `www-data' GID from `33' to `65534'
Aug 27 14:35:27 zeke-comp usermod[19426]: change user `www-data' password
Aug 27 14:35:27 zeke-comp usermod[19432]: change user `zekedragon' GID from `1000' to `0'
Aug 27 14:35:27 zeke-comp usermod[19432]: change user `zekedragon' password
Aug 27 14:35:27 zeke-comp usermod[19438]: change user `zeroinst' GID from `126' to `65534'
Aug 27 14:35:27 zeke-comp usermod[19438]: change user `zeroinst' password
Aug 27 14:35:27 zeke-comp groupdel[19445]: remove group `audio' 
Aug 27 14:35:27 zeke-comp groupdel[19451]: remove group `avahi' 
Aug 27 14:35:27 zeke-comp groupdel[19457]: remove group `avahi-autoipd' 
Aug 27 14:35:27 zeke-comp groupdel[19463]: remove group `backup' 
Aug 27 14:35:28 zeke-comp groupdel[19469]: remove group `bin' 
Aug 27 14:35:28 zeke-comp groupdel[19475]: remove group `daemon' 
Aug 27 14:35:28 zeke-comp groupdel[19483]: remove group `games' 
Aug 27 14:35:28 zeke-comp groupdel[19489]: remove group `gdm' 
Aug 27 14:35:28 zeke-comp groupdel[19495]: remove group `gnats' 
Aug 27 14:35:28 zeke-comp groupdel[19501]: remove group `guest' 
Aug 27 14:35:29 zeke-comp groupdel[19507]: remove group `haldaemon' 
Aug 27 14:35:29 zeke-comp groupdel[19513]: remove group `irc' 
Aug 27 14:35:29 zeke-comp groupdel[19519]: remove group `klog' 
Aug 27 14:35:29 zeke-comp groupdel[19525]: remove group `libuuid' 
Aug 27 14:35:29 zeke-comp groupdel[19531]: remove group `list' 
Aug 27 14:35:29 zeke-comp groupdel[19537]: remove group `lp' 
Aug 27 14:35:29 zeke-comp groupdel[19543]: remove group `mail' 
Aug 27 14:35:30 zeke-comp groupdel[19549]: remove group `man' 
Aug 27 14:35:30 zeke-comp groupdel[19555]: remove group `messagebus' 
Aug 27 14:35:30 zeke-comp groupdel[19561]: remove group `news' 
Aug 27 14:35:30 zeke-comp groupdel[19569]: remove group `polkituser' 
Aug 27 14:35:30 zeke-comp groupdel[19575]: remove group `proxy' 
Aug 27 14:35:30 zeke-comp groupdel[19581]: remove group `pulse' 
Aug 27 14:35:31 zeke-comp groupdel[19589]: remove group `saned' 
Aug 27 14:35:31 zeke-comp groupdel[19595]: remove group `sys' 
Aug 27 14:35:31 zeke-comp groupdel[19601]: remove group `syslog' 
Aug 27 14:35:31 zeke-comp groupdel[19607]: remove group `uucp' 
Aug 27 14:35:31 zeke-comp groupdel[19613]: remove group `www-data' 
Aug 27 14:35:31 zeke-comp groupdel[19621]: remove group `zeroinst'
```At the same time, my daemon.log reported this:
```
Aug 27 14:30:35 zeke-comp gdmsetup[18873]: Gtk-WARNING: GtkSpinButton: setting an adjustment with non-zero page size is deprecated 
Aug 27 14:30:36 zeke-comp last message repeated 6 times
Aug 27 14:30:47 zeke-comp gdmsetup[18873]: GLib-GObject-CRITICAL: g_value_set_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed 
Aug 27 14:30:47 zeke-comp gdmsetup[18873]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed 
Aug 27 14:30:47 zeke-comp gdmsetup[18873]: GLib-GObject-CRITICAL: g_value_unset: assertion `G_IS_VALUE (value)' failed 
Aug 27 14:30:47 zeke-comp gdmsetup[18873]: GLib-GObject-CRITICAL: g_value_set_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed 
Aug 27 14:30:47 zeke-comp gdmsetup[18873]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed 
Aug 27 14:30:47 zeke-comp gdmsetup[18873]: GLib-GObject-CRITICAL: g_value_unset: assertion `G_IS_VALUE (value)' failed 
```syslog.0 reports the same thing as daemon.log at that time. Thanks to these log files I should have all of my former user groups and I can add them in manually to the group file along with everything necessary. While the log doesn't contain information as to which groups my user belonged to, I should be able to derive that information thanks to this [other thread]("http://ubuntuforums.org/showthread.php?t=1095007&page=2") on the Ubuntu forums. I managed to find backups of my group and passwd files, located at /var/backups, which were referred to [here]("http://ubuntuforums.org/archive/index.php/t-1083487.html") in the Ubuntu forum archives. Unfortunately, my backup group file was ALSO overwritten, my OS was apparently on long enough to cause this problem, and may actually be the explanation for my crash.

My etc/sudoers file appears, at least according to the size in bytes, to be maintained, however I cannot be sure of this since the LiveCD will not grant me read access to that file, nor do I have any write access through the LiveCD, instead I will have to access it by using the recovery tool. I can get to GRUB recovery by following the instructions on [this page]("http://www.psychocats.net/ubuntu/sudo").

Alright, well I've got about an hour or so of work to do to get this all recovered, will make a final post on my progress. Thanks for the references to the problem, I started this with no clues whatsoever!

---

### Post by ZekeDragon on 2009-08-28
It's always good to fix problems.

I've finally managed to get everything working again, and as far as I can tell, everything is back to normal (and as an added bonus, the user I created is still there too). Going on from above, the way I actually fixed the problem was as such, you should be able to do the same if you encounter this problem:

The first thing you should do is find out if you have backups available already. Since I'm a lazy person and don't care much for command line instructions, I did this by putting in a LiveCD and doing some searching. This also allows you to look at a few files and see if they're hosed. Starting the LiveCD without changing anything to the hard drive, mount your drive and look for files in /var/backups, called "group.bak" and "passwd.bak". If your group.bak is greater than 50 bytes or so, then congratulations, you have a full back up of your group file! You should also have a proper backup of your passwd file, however this is harder to find out based on file size (seeing as the LiveCD shouldn't grant you read access to these files). If not, you're in for a wild ride, this is going to take a while.

**if (backup(group) == true) {**

All you've got to do is replace the messed up files with the pristine back ups. Go into recovery mode, by pressing ESC when GRUB prompts you to and selecting the "(recovery mode)" version of your OS, then type in the following commands, in order:
```
cp /etc/group /etc/group.old
cp /etc/passwd /etc/passwd.old
cp /var/backups/group.bak /etc/group
cp /var/backups/passwd.bak /etc/passwd
```And there you have it, all done. That should restore everything to it's former self.

**} else {**

Alright, this is a bit trickier. Go ahead and in the LiveCD you're still running find a file in */var/logs* called "auth.log", find where it reports all of the deletions of your user groups (see above post), and print out the area that that is in. If you have to, e-mail/sneakernet that file to a computer with a working attached printer and print it. Go into recovery mode (when GRUB gives you that two seconds of time before it starts, there's a menu you can go to by pressing ESC), and tell it to go to command line as root. Then type in the following:
```
cd /etc
cp group group.old
cp passwd passwd.old
nano group
```Then you're going to fill in everything on the *auth.log* print out text document. This retains all of the groups that were lost on your computer. The ones on the top (above the "change user" section) do not have any corresponding GID information, so don't worry about those ones just yet, instead go ahead and fill in the ones that have GID information, giving each of them their according GID in the following example format:
```
root:x:0:
daemon:x:1:
```The middle field is an x and is always an x. The first field is the name of the group, and the third field is that groups GID. You should fill in the GID's as they appear in the change user section. After this is all done, you'll need to fill in the ones on the top that don't have associated GID information. As far as I can tell, the actual GID's can be given any arbitrary number (however I could be **VERY** wrong about that), but I suggest you follow the general numbers available in [this post]("http://ubuntuforums.org/showpost.php?p=6904912&postcount=16"). Then you'll need to add yourself to these user groups: **adm, admin, dialout, fax, cdrom, floppy, audio, video, plugdev, scanner, fuse, lpadmin, sambashare**. Also add "*haldaemon*" to each of these groups: **cdrom, floppy, plugdev**. You can separate your name and "haldaemon" with the following syntax example:
```
plugdev:x:46:yourusername,haldaemon
```When all of that is finally said and done, save your changes to the group file, and then type "**nano passwd**" to open up the passwd file. This one has much less work involved, all you've got to do is change the fourth field in each line (which should currently be "65534") to the according proper GID as assigned in the group file (that number you've been writing there the whole time). These two numbers need to match, the fourth field in the passwd file and the third field in the group file, **but NOT NECESSARILY the THIRD field in the passwd file and the third field in the group file**! In fact, you should not change the third field at all.

After you've changed each number as they're supposed to be (use that printed out sheet as reference!), you should be pretty much done. Go ahead and save those changes, and say "**shutdown now**" to get out of recovery mode. Try starting everything up as normal and give your computer system some tests! Things should work again!

Alright, that's what I did. Figured I should at least write something.

---

### Post by grndplane on 2009-08-28
I have a quick question. Did you boot to GDM, or directly to your desktop before the user was added?

---

### Post by ZekeDragon on 2009-08-28
Always booted to GDM first.

---

### Post by grndplane on 2009-08-28
Thanks. I thought maybe you didn't have GDM.

---

### Post by P4man on 2009-08-28
Looks like you found the cause of the bug too. 
Will you create a launchpad account to post this information in that bug report too?  Posting a solution here is very useful and i appreciate the effort, but it would be better if someone solved this bug :)

---

### Post by nalimilan on 2009-08-28
Hmm, what's the "root cause" your're talking about? I can't find it in the posts. At least, now I'm sure that this bug happens when adding an user, under apparently normal circumstances. But I have no clue about how to find why the things went wrong, which would be required to fix it.

A way to solve that would be to redesign how the GUI is talking to the backends, so that an empty/corrupt list won't lead to that horror. But there must also be a more specific way of fixing the present bug. I may eventually fix the whole design, since debugging this kind of bugs is hard.

---

### Post by P4man on 2009-08-28
Well, Im no developer so i could be wrong, but as a layman i would think this here:

> Aug 27 14:30:35 zeke-comp gdmsetup[18873]: **Gtk-WARNING: GtkSpinButton: setting an adjustment with non-zero page size is deprecated **
Aug 27 14:30:36 zeke-comp last message repeated 6 times
Aug 27 14:30:47 zeke-comp gdmsetup[18873]: [B]GLib-GObject-CRITICAL: g_value_set_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed 
[/B]Aug 27 14:30:47 zeke-comp gdmsetup[18873]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed 
Aug 27 14:30:47 zeke-comp gdmsetup[18873]: GLib-GObject-CRITICAL: g_value_unset: assertion `G_IS_VALUE (value)' failed 
Aug 27 14:30:47 zeke-comp gdmsetup[18873]: GLib-GObject-CRITICAL: g_value_set_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed 

Would be a smoking gun or not? I just read that as if the GUI is using the GtKSpinButton method wrongly resulting in a failure to set those booleans which in turns results in wiping data. Considering how simple the GUI is, it can't be called on many places, making debugging it not that hard..or ? 

Well, if this sounds like Im clueless,its only because I am :D

---

### Post by nalimilan on 2009-08-28
Well, it could be the culprit, but that's strange. Did the reporter use that program (gdmsetup is run from System->Administration->Login Window)?

I don't see why gdmsetup would have modified users, and the most problematic is that in the logs you have
org.freedesktop.systemtoolsbackends.set
which is the action used by the system-tools-backends, used by users-admin, not by gdmsetup. So the culprit would be the Users and Groups tool.

---

### Post by P4man on 2009-08-28
Im not sure if the OP is still following this thread. You could PM him if he doesnt reply. But reading this:

>  I set up their user name as usual, and put in my sudo password. After about 30 seconds where the computer was setting things up... I... guess... it returned control to me and showed me it had completed the instructions

It would seem natural to assume he used "users and groups".

---

### Post by ZekeDragon on 2009-08-28
Sorry I just had to go to sleep, I was up all night fixing this. :P

Anyway, yeah, I don't know what happened, I'm just posting all the logs that seemed relevant, so if they are, that's good, and if they're not, then I'm sorry they couldn't help. I do have a question though...

Where can I pick up the source code for this particular program? I was looking around in ftp.gnome.org but I haven't had any luck (there are tons of individual downloads there though). Does anyone know where I can get the User Administration Tool source code and any relevant back-end source code?

---

