---
title: "Nautilus unresponsive"
date: 2010-02-06
forum: General Help
---

### Post by afrodeity on 2010-02-06
Been struggling to fix this problem all week. Tried pretty much every "solution" I can find online.

Nautilus is basically frozen. I can set-up a new user and it works no problem. If I run it as root using gksudo, I can open folders, but the desktop is stuck fast.

I've tried deleting .nautilus

I've tried deleting .config and .gconf

Also, gfs-metadata.

There's some conflict going on. If I sudo killall nautilus and restart with nautilus I get this warning:

```

nautilus

** (nautilus:3194): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:3194): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:3194): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Initializing nautilus-open-terminal extension
Initializing nautilus-gdu extension

```

Not sure if its all connected or not. I also get strange messages in my syslog:

```

afrodeity-desktop init: kdm main process (1377) terminated with status 1
Feb  6 13:24:29 afrodeity-desktop init: kdm main process ended, respawning
Feb  6 13:24:30 afrodeity-desktop init: kdm main process (1381) terminated with status 1
Feb  6 13:24:30 afrodeity-desktop init: kdm main process ended, respawning
afrodeity-desktop init: kdm respawning too fast, stopped
Feb  6 13:24:30 afrodeity-desktop gdm-binary[1376]: WARNING: Unable to find users: no seat-id found
Feb  6 13:24:30 afrodeity-desktop acpid: client connected from 1540[0:0]
``` 

and

```

afrodeity-desktop rtkit-daemon[2133]: Failed to make ourselves RT: Invalid argument
Feb  6 13:24:54 afrodeity-desktop rtkit-daemon[2133]: Failed to make ourselves RT: Invalid argument

```

---

### Post by mdurham on 2010-02-06
I had a similar problem that I fixed by a process of elimination. Something was wrong with ~/.gconf/desktop/gnome/interface/%gconf.xml
If I remove that file nautilus works as it should, replace it and it goes slow again. So if nautilus is slow for you, try deleting that file. It's worth a try!
Cheers, Mike

---

### Post by afrodeity on 2010-02-06
> **mdurham said:**
> I had a similar problem that I fixed by a process of elimination. Something was wrong with ~/.gconf/desktop/gnome/interface/%gconf.xml
If I remove that file nautilus works as it should, replace it and it goes slow again. So if nautilus is slow for you, try deleting that file. It's worth a try!
Cheers, Mike

Already tried removing .gconf, now deleted the exact %gconf.xml file to be sure, and not solution yet. Thanks anyways.

---

### Post by afrodeity on 2010-02-07
I've renamed the following directories ~/.gnome ~/.gnome2 ~/.gconf ~/.gconfd and rebooted but no go.

Could be something wrong with bonobo server?

---

### Post by afrodeity on 2010-02-08
I've tried downgrading libsmbclient because of this posting [http://ubuntuforums.org/showthread.php?t=1394101](http://ubuntuforums.org/showthread.php?t=1394101) which appears to be a similar bug related to last round of karmic updates in mid-January.

I also removed samba and winbind, 

Only change in behaviour - nautilus now restarts automatically after I kill it. So presumably the error message has disappeared?

But no actual fix yet. Nautilus desktop still unresponsive. If I click on an icon, nothing.

---

### Post by afrodeity on 2010-02-09
Problem solved. Now why didn't I think about deleting ~/Desktop? Actually the thought had crossed my mind but I Googled and got lost in the general mayhem of free advice.

Just goes to show how Google is actually leading to brain disease. I'm absolutely struck dumb and stupid by the solution which was staring at me but which escaped when my mind got downsized by Google.

It should have been the very first thing I did, problem was with an *unresponsive nautilus desktop*,  but no I am an imbecile, and always far too open to suggestions from anywhere else except my own brain.

After trying out a million other suggestions all not the right one. I have Rashkae, on the Ubuntu Users list to thank for redirecting my cranium to the only solution that actually works.

```

rm ~/Desktop

```

---

### Post by mdurham on 2010-02-09
> **afrodeity said:**
> After trying out a million other suggestions all not the right one. I have Rashkae, on the Ubuntu Users list to thank for redirecting my cranium to the only solution that actually works.

```

rm ~/Desktop

```

But *why* does it work?

---

### Post by afrodeity on 2010-02-10
I remember back from the days of the old Apple System 7 - 9, one had to periodically rebuild the desktop. But this is probably why - either one of the files had a wrong mime type or introduced a mime-type conflict, or the permissions on the files in the desktop folder introduced some conflict. I'm busy working through this trying to figure it all out.

---

### Post by goustaroubunta on 2010-03-21
i didn't get how was this thread solved... anyway i got some issues with that too.. although root access works, the terminal shows >>
"
stef@stef-desktop:~$ gksudo nautilus
(nautilus:19976): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Initializing nautilus-gdu extension

** (nautilus:19976): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:19976): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:19976): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Nautilus-Share-Message: Called "net usershare info" but it failed: Failed to execute child process "net" (No such file or directory)

--- Hash table keys for warning below:
--> root
--> inode/directory
--> stef
--> l2049
--> Stef
Shutting down nautilus-gdu extension

(nautilus:19976): Eel-WARNING **: "unique eel_ref_str" hash table still has 5 elements at quit time (keys above)

(nautilus:19976): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 6 elements at quit time
stef@stef-desktop:~$    "

??

---

### Post by afrodeity on 2010-03-21
I deleted ~/Desktop which solved my problem.

---

### Post by lidex on 2010-03-21
This should work without deleting desktop:
Run this command and reboot:
```
rm -r ~/.local/share/gvfs-metadata
```

---

### Post by kodb on 2010-05-16
ok, same problem here and turning into major mess with nfs; i posted about this earlier in the beginner forum before I found this thread.
I tried to rm ~/Desktop and got the following return:
bob@maraposahomeserver:~$ sudo rm ~/Desktop
rm: cannot remove `/home/bob/Desktop': Is a directory
bob@maraposahomeserver:~$ sudo rmdir ~/Desktop
rmdir: failed to remove `/home/bob/Desktop': Directory not empty

Do I go ahead and delete everything in the directory and then remove the desktop?
Bob

---

### Post by lidex on 2010-05-16
I don't think all that is necessary. If you have .svg files on your desktop, delete them. Otherwise use the command from my previous post and log out/in.

---

### Post by afrodeity on 2010-05-21
Similar issue with nautilus in lucid after upgrade, i forgot about this posting and deleted my ~/Desktop thinking it would reset as in karmic, but now I have home folder as desktop. Tried recreating Desktop, but I think there is a problem with the permissions and/or ownership, because home folder still desktop. The box to normally do this in gconf-editor isn't checked, so can't workaround it with gconf. Any ideas?

---

### Post by afrodeity on 2010-05-21
This fixed the desktop issue [http://ubuntuforums.org/showthread.php?t=1489787](http://ubuntuforums.org/showthread.php?t=1489787)

Now all I have to figure out is how to repair the nautilus dbus problem with gconftool2

---

### Post by lidex on 2010-05-21
> **afrodeity said:**
> This fixed the desktop issue [http://ubuntuforums.org/showthread.php?t=1489787](http://ubuntuforums.org/showthread.php?t=1489787)

Now all I have to figure out is how to repair the nautilus dbus problem with gconftool2

Look here:
[http://ubuntuforums.org/showpost.php?p=4519065&postcount=8]("http://ubuntuforums.org/showpost.php?p=4519065&postcount=8")

---

### Post by lkjoel on 2010-06-29
Try LinuxEssentials in my sig.
Extract it, then type in a terminal window:
```
chmod +x FASTGNOME.sh
./FASTGNOME.sh
```

---

