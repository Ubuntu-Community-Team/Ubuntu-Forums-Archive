---
title: "Thunar slow opening fix"
date: 2011-08-01
forum: General Help
---

### Post by mike555 on 2011-08-01
I think I have fixed the Thunar slow opening issue in Xubuntu , I noticed Thunar opened fast as root, but took almost 30 seconds to open normally, so I figured it was a permissions issue, so I opened Thunar, clicked on File > Properties > Permissions > then set your "group" to have read & write permissions ..... that worked good for me on two systems ...

please let me know if this works for you ,if your having the same problem on Xubuntu 11.04.

---

### Post by yetiman64 on 2011-08-03
Thanks for posting this mike555, I had barely booted into my xubuntu11.04 install in well over a month because of this (was driving me mad to the point of even installing nautilus, and that's not a real good idea I've found out, but it can be done :))

The change is from 35-40 seconds to open a folder down to 1-2 seconds if that. Near instant opening at the moment (nautilus is about to be kicked out by the looks of this :lol:)

Thanks again, this has renewed my interest in continuing trialing/using Xubuntu. yetiman64 (This is posted from Xubuntu btw :-))

---

### Post by Jose Catre-Vandis on 2011-08-03
An extra step I got:

1. "Cannot change permissions to symlinks" dialog, so clicked on "Skip for all"

No speed up for me, but was only about 5 seconds anyway on first run. because thunar goes into memory after that subsequent runs are much quicker.

Did you do this as your normal user, and only on your home folder ?

---

### Post by RHTopics on 2011-08-03
Like Jose Catre-Vandis, I had the extra step as well because I have a mounted partition named "data" that is symlinked in the top level of my home directory (ex. /home/rhtopics/data).

I rebooted the computer and then brought up Thunar.  Definitely noticed an improvement.  Took about 1-2 seconds to bring up Thunar while before it would take around 5 seconds to bring it up.

---

### Post by yetiman64 on 2011-08-03
I also skipped the symlinks, but at the time got an immediate drastic speed up. 

However since rebooting and on subsequent reboots I have now noted it is slow for about 3 or 4 minutes after startup (not as bad as before though), then drops down to a second or two for each opening. There may be a memory factor in this as well as Jose Catre-Vandis mentions.

Considering prior to making the permissions changes it was always painfully slow for me, this is still a very good result.

Edit: @ Jose Catre-Vandis, yes I did the changes as normal user and only on the Home Folder to get the improved Thunar opening.

---

### Post by eexcellent on 2011-11-03
Great tip, worked for me!

Thanks Mike555

---

### Post by gsmanners on 2011-11-03
Might be related to the gvfs issue.

[https://bugzilla.xfce.org/show_bug.cgi?id=7373](https://bugzilla.xfce.org/show_bug.cgi?id=7373)

---

### Post by ankspo71 on 2011-11-04
Update: I found that gvfs-backends was the only culprit in my case. Also, It appears that gvfs-fuse is a package that is installed by default in Xubuntu 11.10, so I have installed it again and it doesn't slow down thunar for me.

Hi
I ended up doing something different:
When I installed Xubuntu 11.10 (clean install), Thunar had no problems at all launching for the first time after every startup.

Then I decided to install pcmanfm for a light file manager with a few more features, but pcmanfm installed 'gvfs-fuse' and 'gvfs-backends' (as recommends, not dependencies) too, which made Thunar very slow to start during each first launch (and it would open 2 instances of thunar on first launch too).

So I removed 'gvfs-fuse' and 'gvfs-backends' and Thunar is very quick again, but doing this removed the networking bookmark from Thunar (that isn't something I need myself though).

'gvfs' and 'gvfs-bin' are still installed (I found that trash applet and trash bookmark in thunar will not work without them).

---

### Post by ambrosa on 2011-11-09
1) gvfs-backends should be already installed in a fresh installation but it isn't. This is a Oneiric bug [https://bugs.launchpad.net/ubuntu/oneiric/+source/xubuntu-meta/+bug/878682](https://bugs.launchpad.net/ubuntu/oneiric/+source/xubuntu-meta/+bug/878682)
So if you use Xubuntu 11.10 Oneiric, please install gvfs-backends or Thunar/Gigolo cannot have access to FTP SSH WEDDAV SAMBA etc. etc. network filesystems

2) As described here [https://bugzilla.xfce.org/show_bug.cgi?id=7373](https://bugzilla.xfce.org/show_bug.cgi?id=7373) there is a problem in Thunar about "network://" search/browse. "network://" is enabled after you installed gvfs-backends.
When you open Thunar _the first time_, it run automatically a "network://" search (it's a samba scan) and you must wait it end before see Thunar in your desktop.
I'm waiting the new Thunar release (the bug above is fixed) but in meantime I've found a simple solution: as 'root' edit the text file
[FONT="Courier New"][SIZE="3"]/usr/share/gvfs/mounts/smb-browse.mount[/SIZE][/FONT]

Original code: remove type smb-network
```

[Mount]
Type=**[COLOR="Red"]smb-network;[/COLOR]**smb-server
Exec=/usr/lib/gvfs/gvfsd-smb-browse
DBusName=org.gtk.vfs.mountpoint.smb_browse
AutoMount=false
Scheme=smb

```

After editing:
```

[Mount]
Type=smb-server
Exec=/usr/lib/gvfs/gvfsd-smb-browse
DBusName=org.gtk.vfs.mountpoint.smb_browse
AutoMount=false
Scheme=smb

```

YOU MISS NETWORK:// SCAN but now Thunar open fast the first time also.
For me is ok: I've no Samba share in my local network (only FTP) :)

---

### Post by ernestj on 2011-12-19
> **ambrosa said:**
> 1) gvfs-backends should be already installed in a fresh installation but it isn't. This is a Oneiric bug [https://bugs.launchpad.net/ubuntu/oneiric/+source/xubuntu-meta/+bug/878682](https://bugs.launchpad.net/ubuntu/oneiric/+source/xubuntu-meta/+bug/878682)
So if you use Xubuntu 11.10 Oneiric, please install gvfs-backends or Thunar/Gigolo cannot have access to FTP SSH WEDDAV SAMBA etc. etc. network filesystems

2) As described here [https://bugzilla.xfce.org/show_bug.cgi?id=7373](https://bugzilla.xfce.org/show_bug.cgi?id=7373) there is a problem in Thunar about "network://" search/browse. "network://" is enabled after you installed gvfs-backends.
When you open Thunar _the first time_, it run automatically a "network://" search (it's a samba scan) and you must wait it end before see Thunar in your desktop.
I'm waiting the new Thunar release (the bug above is fixed) but in meantime I've found a simple solution: as 'root' edit the text file
[FONT="Courier New"][SIZE="3"]/usr/share/gvfs/mounts/smb-browse.mount[/SIZE][/FONT]

Original code: remove type smb-network
```

[Mount]
Type=**[COLOR="Red"]smb-network;[/COLOR]**smb-server
Exec=/usr/lib/gvfs/gvfsd-smb-browse
DBusName=org.gtk.vfs.mountpoint.smb_browse
AutoMount=false
Scheme=smb

```

After editing:
```

[Mount]
Type=smb-server
Exec=/usr/lib/gvfs/gvfsd-smb-browse
DBusName=org.gtk.vfs.mountpoint.smb_browse
AutoMount=false
Scheme=smb

```

YOU MISS NETWORK:// SCAN but now Thunar open fast the first time also.
For me is ok: I've no Samba share in my local network (only FTP) :)



Hello,
Do I put the code directly into a terminal? Or are there more steps involved?

Thanks,
Ernie

---

### Post by cottfcfan on 2011-12-19
Ernest
```
sudo leafpad /usr/share/gvfs/mounts/smb-browse.mount
```
Then edit the file accordingly.

---

### Post by geovino on 2012-01-26
> **mike555 said:**
> I think I have fixed the Thunar slow opening issue in Xubuntu , I noticed Thunar opened fast as root, but took almost 30 seconds to open normally, so I figured it was a permissions issue, so I opened Thunar, clicked on File > Properties > Permissions > then set your "group" to have read & write permissions ..... that worked good for me on two systems ...

please let me know if this works for you ,if your having the same problem on Xubuntu 11.04.

It worked a couple times, then went back to a long delay. Anyway other way to fix this problem?

---

### Post by Nuc72 on 2012-02-02
I think it's a better solution if you leave smb-browse.mount untouched, and edit network.mount instead. Set AutoMount to false.
If you need network, just click on network:/// in Thunar, it will mount itself.

---

### Post by sirweldsalot on 2012-02-15
@mike555:
oh thank-you sooooo much!!!!

---

### Post by Chaitaweede on 2012-02-15
Tra di noi dire, vi raccomando il check-out google.com

---

### Post by godsgifttoearth on 2012-02-23
still doesn't work for me. i've done every listed fix i can editing bits and pieces, still takes a good 30seconds to first open.

---

### Post by FOSScula on 2012-03-25
We also experienced same (bug?) Ubuntu 11.10 64bit (Thunar 1.2.3) Xfce 4.8

after trying all of above mentioned solutions and not finding a fix that retained samba-browsing functionality. and at the request for another alternative method.. heres what we did that is working just peachy \\:D/

flying in the face of all logic and whats previously been mentioned we set 
AutoMount=true
5th line down in file /usr/share/gvfs/mounts/smb-browse.mount
rebooted and all is well... thunar is a little slow on first start 5-10 seconds..better than 20-30 everytime we opened it before..  Subsequent openings of thunar take around 1 sec.. also network tab on left side still allows us to browse/scan any SMB shares/mounts.
 to recap
```
nano /usr/share/gvfs/mounts/smb-browse.mount
```or if you prefer a GUI
```
leafpad /usr/share/gvfs/mounts/smb-browse.mount
```> 
[Mount]
Type=smb-network;smb-server
Exec=/usr/lib/gvfs/gvfsd-smb-browse
DBusName=org.gtk.vfs.mountpoint.smb_browse
AutoMount=false
Scheme=smbchange 5th line down to true
> AutoMount=truehope it helps someone.. remember that to save changes to *smb-browse.mount* you MUST BE root in whichever text editor you opened it with.. ie leafpad, gedit, nano

---

### Post by ijustneedadownload on 2012-04-20
Though I'm on Slackware instead of Ubuntu, I got the same problem. 

I rarely use Thunar, but when I did it took approx 3 to 5 seconds to show the gui. In my case I had mounted a samba share an did not properly unmount it. So Thunar started and tried to open up that share, waiting some seconds for it to answer and finally giving up on it. Lazy unmounting the "dead" share solved the problem, the Thunar gui shows up instantly.

---

### Post by eshaw13 on 2012-07-15
Thanks, I had all around issues with slowness that were resolved by manually installing amd drivers from their website and so this was the only thing that was bugging me.  I'm glad it was such a simple fix :)

---

### Post by Nakarti on 2012-12-14
I for one don't need Samba browsing because my Samba server does NFS for Linux clients. So disabling smb-network is the correct and successful solution for me. It also resolved a side effect where once the first Thunar window opened, a duplicate would also open.

I am not sure the cause of that, but removing 'smb-network;' fixed both.
If the setting failed to fix and came back in the config, you may have forgotten to remove the semicolon, and Thunar would reactivate its automatic backup or a default of the config.

---

### Post by iMac71 on 2013-01-09
> **Nuc72 said:**
> I think it's a better solution if you leave smb-browse.mount untouched, and edit network.mount instead. Set AutoMount to false.
If you need network, just click on network:/// in Thunar, it will mount itself.Thank you very much: your tip has made Thunar very quick without any need of modifying files permissions; I've also left unmodified smb-browse.mount.

---

### Post by rustiguzzi on 2013-02-27
Running xubuntu 12.04.1 (LTS) - I've been through all the suggestions in previous posts, and the ONLY one that worked for me was the simplest, that of doing without thumbnails.

In Thunar, Edit>Preferences and in the Display tab uncheck "show thumbnails".

I can live without 'em.

---

### Post by pqwoerituytrueiwoq on 2013-02-27
> **rustiguzzi said:**
> Running xubuntu 12.04.1 (LTS) - I've been through all the suggestions in previous posts, and the ONLY one that worked for me was the simplest, that of doing without thumbnails.

In Thunar, Edit>Preferences and in the Display tab uncheck "show thumbnails".

I can live without 'em.
you could try updating to xfce 4.12
**this entire line is for precise (12.04)**
```
sudo apt-add-repository ppa:xubuntu-dev/xfce-4.10;sudo apt-add-repository ppa:xubuntu-dev/xfce-4.12;sudo apt-get update;sudo apt-get dist-upgrade
```

---

### Post by rustiguzzi on 2013-03-04
Thanks. Will give it a go. However, since my previous post something weird has happened. I reverted to "show thumbnails" intending it to be temporary, but on next reboot (and all subsequent ones) everything was, and remains, OK. File Manager comes up without delay, there is no instance of a second, unwanted File Manager appearing - and I have thumbnails as a bonus.

The only other alteration made to File Manager was to uncheck "Browse removable media when inserted" in the Advanced section of Preferences, but I can't see that causing this problem (and even when re-instated, it didn't made any difference). I remain baffled, but will certainly update xfce ASAP.

---

### Post by kbrodenhau on 2013-05-26
So, I'm in Mint Nadia 14 (XFCE 4.10) and this is still an issue...

On a guess, I did the following.. 
[LIST=1]
[*]Exited out of all thunar windows.
[*]Deleted the ~/.cache/Thunar/metafile.tdb file.
[*]Got back into Thunar (quick, since the metafile.tdb file is removed.)
[*]Exited out of Thunar immediately (which recreates the metafile.tdb file)
[*]Then, in a terminal window:
[/LIST]

[LIST]
[*]cd ~/.cache/Thunar
[*]sudo chown root.root metafile.tdb
[*]sudo chmod 444 metafile.tdb
[/LIST]

Now, the metafile.tdb file can be read by me but not written by me.

Anyway, over a two day period - thunar pops right up and I haven't noticed the issue... 

So it feels like, under certain unknown reasons, thunar corrupts the metafile.tdb file when you exit thunar, causing the delays in the future...

I hope this helps (AND be careful with sudo!)

---

### Post by kbrodenhau on 2013-05-26
> **kbrodenhau said:**
> So, I'm in Mint Nadia 14 (XFCE 4.10) and this is still an issue...

On a guess, I did the following.. 
[LIST=1]
[*]Exited out of all thunar windows. 
[*]Deleted the ~/.cache/Thunar/metafile.tdb file. 
[*]Got back into Thunar (quick, since the metafile.tdb file is removed.) 
[*]Exited out of Thunar immediately (which recreates the metafile.tdb file) 
[*]Then, in a terminal window: 
[/LIST]

[LIST]
[*]cd ~/.cache/Thunar 
[*]sudo chown root.root metafile.tdb 
[*]sudo chmod 444 metafile.tdb 
[/LIST]

Now, the metafile.tdb file can be read by me but not written by me.

Anyway, over a two day period - thunar pops right up and I haven't noticed the issue... 

So it feels like, under certain unknown reasons, thunar corrupts the metafile.tdb file when you exit thunar, causing the delays in the future...

I hope this helps (AND be careful with sudo!)

Oh, yes, you must also follow ambrosa's suggestion from November 9th, 2011 in this thread... That is, removing "smb-network;" from the 
/usr/share/gvfs/mounts/smb-browse.mount
file...

---

### Post by kbrodenhau on 2013-05-27
Sorry, I don't like my solution..

We need a fix from Xfce because the problem persists in Xfce 4.10...

---

### Post by Merrattic on 2013-05-30
The best solution is still as per these instructions (2)

[http://xubuntu.org/news/faq-1204-precise/](http://xubuntu.org/news/faq-1204-precise/)

---

### Post by adresse_test on 2013-11-23
I think it's a bug like the one for gimp.
I removed .tumbnails and it loads fast again.
Maybe thunar always loads all of the tumbnail images while starting.

---

