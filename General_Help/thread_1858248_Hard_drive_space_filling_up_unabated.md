---
title: "Hard drive space filling up unabated"
date: 2011-10-12
forum: General Help
---

### Post by alman9898 on 2011-10-12
I have the latest release of Natty Narwhal.

My Ubuntu is currently installed as a 72 gig partition on a 500 gig hard drive.

Last night, the space suddenly got used up incredibly...to about 68 G of 72 G. The system slowed down like crazy, and then after rebooting, wouldn't return me to the desktop.

So, I deleted the partition off my hard drive and reinstalled Ubuntu, only to find that once again it's filling me hard drive up.  Last night I must have had 80% free, now I have something like 4 KB free (yes KB).

At first, I thought I may have installed too many apps on the system, but clearly that's not the case. There's no way I could have used up 60+ gigs in one day, simply by adding emacs, pidgin, and ubuntu-tweak.

Is my system FUBAR'd?  Here is what happens after running df

```

bash: cannot create temp file for here-document: No space left on device
alex@alex-EP45-UD3R:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda5             74912928  71107536         4 100% /
none                   2017312       700   2016612   1% /dev
none                   2027964       200   2027764   1% /dev/shm
none                   2027964        92   2027872   1% /var/run
none                   2027964         0   2027964   0% /var/lock
/home/alex/.Private   74912928  71107536         4 100% /home/alex
/dev/sdb2            244092924 179795764  64297160  74% /media/C8F8CA6AF8CA567A
alex@alex-EP45-UD3R:~$ 

```

---

### Post by peyre on 2011-10-12
That's weird.  It sounds like there's maybe some program or script making copies of your files in an infinite loop, or something.  I'm reminded of when I realized I was low on hard drive space, then figured out I had copied files over from my wife's computer to back up her system one night as an emergency measure.  That was at least my own doing and easily fixed--this sounds like something else that's gotten out of control.

You might try pulling up Gnome System Monitor (you may have to install it first) and looking around.  You may get some idea what's chewing up your hard drive; maybe you can Kill it there.  Also, I have a program that will analyze your hard drive and give you a visual on what's taking up how much space on it; write me at [email]email@removed.tld[/email] if you'd like a copy.  It might also give you some idea what's going on.

---

### Post by alman9898 on 2011-10-12
According to the Disk Usage analyzer, there's only 43 files in my /home directory, yet it takes up 64.1 GB.

Also, I cannot really download anything, as the disk displays 100% full and won't create new files.

Also, i-node usage:

```

alex@alex-EP45-UD3R:~$ df -i
Filesystem            Inodes   IUsed   IFree IUse% Mounted on
/dev/sda5            4759552  181323 4578229    4% /
none                  504328    1015  503313    1% /dev
none                  506991       7  506984    1% /dev/shm
none                  506991      49  506942    1% /var/run
none                  506991       1  506990    1% /var/lock
/home/alex/.Private  4759552  181323 4578229    4% /home/alex
/dev/sdb2            64919752  511784 64407968    1% /media/C8F8CA6AF8CA567A

```

Another update:

Disk usage analyzer reports that I am using 131.6 GB...the partition is 72 gigs!

---

### Post by drofart on 2011-10-12
> **alman9898 said:**
> I have the latest release of Natty Narwhal.

My Ubuntu is currently installed as a 72 gig partition on a 500 gig hard drive.

Last night, the space suddenly got used up incredibly...to about 68 G of 72 G. The system slowed down like crazy, and then after rebooting, wouldn't return me to the desktop.

So, I deleted the partition off my hard drive and reinstalled Ubuntu, only to find that once again it's filling me hard drive up.  Last night I must have had 80% free, now I have something like 4 KB free (yes KB).

At first, I thought I may have installed too many apps on the system, but clearly that's not the case. There's no way I could have used up 60+ gigs in one day, simply by adding emacs, pidgin, and ubuntu-tweak.

Is my system FUBAR'd?  Here is what happens after running df

```

bash: cannot create temp file for here-document: No space left on device
alex@alex-EP45-UD3R:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda5             74912928  71107536         4 100% /
none                   2017312       700   2016612   1% /dev
none                   2027964       200   2027764   1% /dev/shm
none                   2027964        92   2027872   1% /var/run
none                   2027964         0   2027964   0% /var/lock
/home/alex/.Private   74912928  71107536         4 100% /home/alex
/dev/sdb2            244092924 179795764  64297160  74% /media/C8F8CA6AF8CA567A
alex@alex-EP45-UD3R:~$ 

```

@WIlliam
"Well, let me tell you a story. Not long ago we had a problem where I used to work. There was a shared drive on one of our file servers that kept getting full. I won't mention that this legacy operating system did not support user quotas; that's another story. But the server kept getting full and stopping people from working. One of the software engineers in our company spent the better part of a day writing a C++ program that would look through the directories of all the users and add up the space they were using and make a listing of the results. Since I was forced to use the legacy OS while I was on the job, I installed [a version of the bash shell that works on it.]("http://www.cygwin.com/") When I heard about the problem, I realized I could do all the work this engineer had done with this single line:  du -s * | sort -nr > $HOME/space_report.txt"
[I]Though i am not confident with ur issue but with this clue may some folk would help u out.

good luck.


Sona
[/I]

---

### Post by WasMeHere on 2011-10-12
Hello alman9898,

I agree that it is very strange, particularly that it repeats after your reinstalled Ubuntu.

- Did you install some particular program?
- Is your home directory encrypted?
- Would it be OK to publish a list of the 43 files? > 43 files in my /home directory, yet it takes up 64.1 GB In that case post the output of ```
sudo du -a ~ | sort -n
``` By the way, this command should also print the hidden files (.xxx)

Have fun finding out about Ubuntu
Olle

---

### Post by alman9898 on 2011-10-12
> **Olle Wiklund said:**
> Hello alman9898,

I agree that it is very strange, particularly that it repeats after your reinstalled Ubuntu.

- Did you install some particular program?
- Is your home directory encrypted?
- Would it be OK to publish a list of the 43 files?  In that case post the output of ```
sudo du -a ~ | sort -n
``` By the way, this command should also print the hidden files (.xxx)

Have fun finding out about Ubuntu
Olle

Hello Olle.  In regards to your questions:

(1) The problem seems to coincidentally have shown up when running the "Sound Change Applier" located at  [http://www.zompist.com/sounds.htm](http://www.zompist.com/sounds.htm) The program provides a C source code (on the site, for reference), which I compiled using gcc. That's about the only constant I can think of.

(2) Yes, my home directory is encrypted. I don't remember if it was encrypted before I did my reinstall, but it is encrypted now.

(3) Yes, here:

After running your command, I got:

```
en0
32    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/scaleaddon/screen0
32    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/scale/screen0
32    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/screenshot/screen0
32    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/session/screen0
32    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/snap/screen0
32    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/switcher/screen0
32    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/thumbnail/screen0
32    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/titleinfo/screen0
32    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/unitymtgrabhandles/screen0
32    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/unityshell/screen0
32    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/vpswitch/screen0
32    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/water/screen0
32    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/winrules/screen0
32    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/wobbly/screen0
32    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/workarounds/screen0
32    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/zoom/screen0
32    /home/alex/.gconf/apps/evolution/addressbook
32    /home/alex/.gconf/apps/evolution/calendar
32    /home/alex/.gconf/apps/gedit-2/plugins/filebrowser
32    /home/alex/.gconf/apps/gedit-2/preferences/ui
32    /home/alex/.gconf/apps/gnome-terminal/profiles
32    /home/alex/.gconf/apps/metacity
32    /home/alex/.gconf/apps/panel/applets/window_list_screen0
32    /home/alex/.gconf/apps/panel/applets/workspace_switcher_screen0
32    /home/alex/.gconf/apps/panel/toplevels/bottom_panel_screen0
32    /home/alex/.gconf/apps/panel/toplevels/top_panel_screen0
32    /home/alex/.gconf/desktop/gnome/accessibility
32    /home/alex/.gconf/desktop/gnome/applications
32    /home/alex/.gconf/desktop/gnome/peripherals
32    /home/alex/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys
32    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/0/12
32    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/0/A1/38D66d01
32    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/0/C2/384D7d01
32    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/0/E4
32    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/2/34/ADA5Cd01
32    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/2/FB
32    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/3/83
32    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/4/39/23BC3d01
32    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/4/7E/4D9B2d01
32    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/5/8E
32    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/5/A8
32    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/5/FC
32    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/6/67
32    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/6/C2/3CB2Ed01
32    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/6/D0
32    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/8/7C/4C55Ad01
32    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/8/AB/BAA85d01
32    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/8/FE
32    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/9/8F
32    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/9/93
32    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/9/C1
32    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/A/12
32    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/A/A5
32    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/B/5B
32    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/C/1F
32    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/C/21
32    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/C/37/BF0D2d01
32    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/D/71/92A82d01
32    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/E/4C
32    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/F/4C
32    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/F/75/91F8Cd01
32    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/F/87
32    /home/alex/.thumbnails/fail
32    /home/alex/.thumbnails/normal/7777cbecd80867f19e57f2f41857772f.png
36    /home/alex/.cache/software-center/icons/sc-agent-admin-magazine-issue-003.png
36    /home/alex/.fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le32d4.cache-3
36    /home/alex/.gconf/apps/baobab
36    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/animation/screen0
36    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/core/screen0
36    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/ezoom/screen0
36    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/grid/screen0
36    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/ring/screen0
36    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/rotate/screen0
36    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/shift/screen0
36    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/staticswitcher/screen0
36    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/wall/screen0
36    /home/alex/.local/share/evolution/addressbook/1318287707.2673.0@alex-EP45-UD3R
36    /home/alex/.macromedia/Flash_Player/macromedia.com/support/flashplayer
36    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/0/A1
36    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/0/C2
36    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/1/5C/CEEF9d01
36    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/1/DD/B0FB0d01
36    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/2/34
36    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/4/39
36    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/4/7E
36    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/4/C5/B2870d01
36    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/6/03/38443d01
36    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/6/C2
36    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/7/4C/96037d01
36    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/7/87/777E2d01
36    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/8/7C
36    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/8/AB
36    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/9/C0/11176d01
36    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/A/75/31EE3d01
36    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/B/39/C5E39d01
36    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/B/F1/9B4B3d01
36    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/C/37
36    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/D/71
36    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/E/50/07872d01
36    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/E/F4/962AFd01
36    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/F/75
36    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/F/7F/697EAd01
36    /home/alex/.thumbnails/normal/331a4c7d6397b25743b2e2b7d28f2ccf.png
36    /home/alex/.thumbnails/normal/353744e3dfb60e8cfcdd8b83bd78e547.png
40    /home/alex/.cache/zeitgeist
40    /home/alex/.fontconfig/d52a8644073d54c13679302ca1180695-le32d4.cache-3
40    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/commands/screen0
40    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/put/screen0
40    /home/alex/.local/share/evolution/addressbook
40    /home/alex/.local/share/gvfs-metadata/computer:-56ed089f.log
40    /home/alex/.local/share/gvfs-metadata/home-c2f5b4c7.log
40    /home/alex/.local/share/gvfs-metadata/network:-15b0e2a7.log
40    /home/alex/.local/share/gvfs-metadata/root-d4289fad.log
40    /home/alex/.local/share/gvfs-metadata/uuid-12AAC6D6AAC6B60F-3517dbf0.log
40    /home/alex/.local/share/gvfs-metadata/uuid-B4648A82648A4758-34e26cab.log
40    /home/alex/.local/share/Trash
40    /home/alex/.macromedia/Flash_Player/macromedia.com/support
40    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/1/24/A5788d01
40    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/1/5C
40    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/1/69/D3F1Cd01
40    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/1/77/51ECEd01
40    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/1/DD
40    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/3/FA/28F7Ad01
40    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/4/C5
40    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/6/03
40    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/7/4C
40    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/7/87
40    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/7/AC/BB7C3d01
40    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/9/10/4C0F8d01
40    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/9/C0
40    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/A/75
40    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/B/39
40    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/B/F1
40    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/D/94/67AF2d01
40    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/E/50
40    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/E/89/3619Dd01
40    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/E/F4
40    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/F/46/21B68d01
40    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/F/7F
40    /home/alex/.mozilla/firefox/hixy0xse.default/cookies.sqlite-shm
40    /home/alex/.mozilla/firefox/hixy0xse.default/places.sqlite-shm
44    /home/alex/.local/share/evolution
44    /home/alex/.local/share/zeitgeist/activity.sqlite-journal
44    /home/alex/.macromedia/Flash_Player/macromedia.com
44    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/0/3D/C93F9d01
44    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/0/6B/7AB67d01
44    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/0/D8/40094d01
44    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/1/24
44    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/1/69
44    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/1/77
44    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/2/30/27195d01
44    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/2/F9/A744Ad01
44    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/3/FA
44    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/7/AC
44    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/9/10
44    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/A/B9/4D84Dd01
44    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/B/0B/61554d01
44    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/B/23/CF117d01
44    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/_CACHE_MAP_
44    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/D/94
44    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/E/89
44    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/E/D7/B5F28d01
44    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/F/46
48    /home/alex/.cache/software-center/rnrclient/reviews.ubuntu.com,reviews,api,1.0,review-stats,any,any,updates-last-3-days,,1ea08a227a615b5966270464124e4ee4
48    /home/alex/.gconf/apps/compiz-1/general
48    /home/alex/.gconf/apps/compiz-1/plugins/move
48    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/general
48    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/annotate
48    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/bailer
48    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/blur
48    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/clone
48    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/colorfilter
48    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/composite
48    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/cube
48    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/debugspew
48    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/decor
48    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/detection
48    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/expo
48    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/fade
48    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/gnomecompat
48    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/imgjpeg
48    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/kdecompat
48    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/mag
48    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/mousepoll
48    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/move
48    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/neg
48    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/obs
48    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/opacify
48    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/opengl
48    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/place
48    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/resize
48    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/resizeinfo
48    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/scale
48    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/scaleaddon
48    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/screenshot
48    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/session
48    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/snap
48    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/switcher
48    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/thumbnail
48    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/titleinfo
48    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/unitymtgrabhandles
48    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/unityshell
48    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/vpswitch
48    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/water
48    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/winrules
48    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/wobbly
48    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/workarounds
48    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/zoom
48    /home/alex/.gconf/apps/gedit-2/plugins
48    /home/alex/.gconf/apps/gedit-2/preferences
48    /home/alex/.gconf/apps/gnome-terminal
48    /home/alex/.gconf/apps/procman
48    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/0/3D
48    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/0/6B
48    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/0/D8
48    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/2/30
48    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/2/4D/A14FAd01
48    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/2/AF/5EA56d01
48    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/2/C4/7BFDBd01
48    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/2/F9
48    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/3/E9/35BCBd01
48    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/5/01/1F1A0d01
48    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/8/55/5E930d01
48    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/8/D1/15D6Cd01
48    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/A/44/66DE2d01
48    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/A/B9
48    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/B/0B
48    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/B/23
48    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/B/44/8EC5Bd01
48    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/B/8E/DB71Ad01
48    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/D/FF/9120Dd01
48    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/E/5B/E84EEd01
48    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/E/D7
52    /home/alex/.cache/software-center/icons/sc-agent-admin-magazine-issue-004.png
52    /home/alex/.compiz/session
52    /home/alex/.fontconfig/0f34bcd4b6ee430af32735b75db7f02b-le32d4.cache-3
52    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/animation
52    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/core
52    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/ezoom
52    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/grid
52    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/ring
52    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/rotate
52    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/shift
52    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/staticswitcher
52    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/wall
52    /home/alex/.mozilla/firefox/hixy0xse.default/bookmarkbackups
52    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/1/34/5E31Fd01
52    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/2/4D
52    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/2/AF
52    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/2/C4
52    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/3/E9
52    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/5/01
52    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/6/6F/6497Fd01
52    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/7/AE/83939d01
52    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/8/55
52    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/8/D1
52    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/9/CA/48AA0d01
52    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/A/44
52    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/B/0C/6387Fd01
52    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/B/44
52    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/B/64/4D49Cd01
52    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/B/8E
52    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/C/03/80C5Cd01
52    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/C/09/78555d01
52    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/D/FF
52    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/E/5B
56    /home/alex/.compiz
56    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/commands
56    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins/put
56    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/0/B7/31593d01
56    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/1/34
56    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/5/32/FDEDFd01
56    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/6/6F
56    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/7/AE
56    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/9/CA
56    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/A/70/53088d01
56    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/B/0C
56    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/B/64
56    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/C/03
56    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/C/09
56    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/D/6E/28915d01
56    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/F/4E/31DE8d01
56    /home/alex/.xsession-errors
60    /home/alex/.gnome2/accels
60    /home/alex/.local/share/zeitgeist/fts.index/position.DB
60    /home/alex/.local/share/zeitgeist/fts.index/postlist.DB
60    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/0/B7
60    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/3/40/323A4d01
60    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/8/21/3332Bd01
60    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/9/55/F9D4Cd01
60    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/A/25/0997Ed01
60    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/A/70
60    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/A/F2/66618d01
60    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/D/6E
60    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/E/F0/F0254d01
60    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/F/4E
64    /home/alex/.config/ubuntu-tweak/appcenter/apps.json
64    /home/alex/.gconf/apps/compiz-1/plugins
64    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/3/40
64    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/3/A0/038ADd01
64    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/3/BA/8E6F9d01
64    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/8/21
64    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/9/55
64    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/A/25
64    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/A/F2
64    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/B/7F/BCC32d01
64    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/D/89/3CF5Cd01
64    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/E/F0
68    /home/alex/.local/share/zeitgeist/activity.sqlite
68    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/3/A0
68    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/3/BA
68    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/4/E3/1B774d01
68    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/6/71/AD694d01
68    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/8/BB/FF537d01
68    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/B/7F
68    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/D/89
68    /home/alex/.pulse/39acc401eccdc92c1d50056000000004-device-volumes.tdb
72    /home/alex/.cache/software-center/software-center-agent.db/termlist.DB
72    /home/alex/.macromedia/Flash_Player
72    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/4/E3
72    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/6/71
72    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/8/BB
72    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/9/51/2B942d01
72    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/A/B5/4067Fd01
72    /home/alex/.mozilla/firefox/hixy0xse.default/cert8.db
72    /home/alex/.mozilla/firefox/hixy0xse.default/downloads.sqlite
72    /home/alex/.mozilla/firefox/hixy0xse.default/permissions.sqlite
72    /home/alex/.mozilla/firefox/hixy0xse.default/search.sqlite
76    /home/alex/.local/share/zeitgeist/fts.index/termlist.DB
76    /home/alex/.macromedia
76    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/3/7D/AC0ACd01
76    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/9/51
80    /home/alex/.gconf/apps/evolution
80    /home/alex/.gconf/apps/panel/objects
80    /home/alex/.gconf/apps/panel/toplevels
80    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/3/7D
80    /home/alex/.pulse/39acc401eccdc92c1d50056000000004-stream-volumes.tdb
84    /home/alex/.cache/software-center/apthistory.p
84    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/0/25/DF7C2d01
84    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/7/AF/A6630d01
88    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/0/25
88    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/7/AF
96    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/5/32/CFBEEd01
96    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/8/C1/F2509d01
100    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/8/C1
104    /home/alex/.mozilla/firefox/hixy0xse.default/chromeappsstore.sqlite
104    /home/alex/.mozilla/firefox/hixy0xse.default/webappsstore.sqlite
108    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/0/B6/D100Ad01
108    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/A/2F/E2662d01
112    /home/alex/.gconf/apps/gedit-2
112    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/0/B6
112    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/A/2F
116    /home/alex/Asmo
116    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/7/B3/A9427d01
116    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/8/7B/B3BE8d01
120    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/7/B3
120    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/8/7B
124    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/3/D7/1F82Dd01
128    /home/alex/.gconf/apps/compiz-1
128    /home/alex/.gconf/desktop/gnome
128    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/3/D7
140    /home/alex/files.txt
140    /home/alex/.gnome2
144    /home/alex/.gconf/apps/nautilus/desktop-metadata
144    /home/alex/.gconf/apps/panel/applets
144    /home/alex/.gconf/desktop
156    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/5/32
168    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/A/B5/A7F5Fd01
168    /home/alex/.mozilla/firefox/hixy0xse.default/formhistory.sqlite
188    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/4
188    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/D/FC/C446Cd01
192    /home/alex/.gconf/apps/nautilus
192    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/D/FC
192    /home/alex/.pulse
212    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/3/3F/99D7Dd01
216    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/3/3F
224    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/C
232    /home/alex/.mozilla/firefox/hixy0xse.default/content-prefs.sqlite
236    /home/alex/.mozilla/firefox/hixy0xse.default/addons.sqlite-journal
244    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/A/B5
248    /home/alex/.cache/software-center/software-center-agent.db/spelling.DB
248    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/F
260    /home/alex/.gconfd/saved_state
264    /home/alex/.gconfd
264    /home/alex/.mozilla/firefox/hixy0xse.default/addons.sqlite
264    /home/alex/.mozilla/firefox/hixy0xse.default/OfflineCache/index.sqlite
268    /home/alex/.mozilla/firefox/hixy0xse.default/OfflineCache
280    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/1
296    /home/alex/.cache/software-center/software-center-agent.db/postlist.DB
296    /home/alex/.local/share/zeitgeist/fts.index
296    /home/alex/.mozilla/firefox/hixy0xse.default/signons.sqlite
304    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/A/08/E91D2d01
308    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/5
308    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/A/08
316    /home/alex/.local/share/gvfs-metadata
324    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/E
328    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/2
336    /home/alex/.gconf/apps/panel
356    /home/alex/.cache/software-center/reviews.ubuntu.com_reviews_api_1.0_review-stats-pkgnames.p
364    /home/alex/.cache/wallpaper/zoom_1680_1050__usr_share_backgrounds_warty-final-ubuntu.png
368    /home/alex/.cache/wallpaper
380    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/9
392    /home/alex/.mozilla/firefox/hixy0xse.default/extensions.sqlite
396    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/7
424    /home/alex/.local/share/zeitgeist
440    /home/alex/.cache/software-center/rnrclient/reviews.ubuntu.com,reviews,api,1.0,review-stats,any,any,,1c66e24123164bb80c4253965e29eed7
452    /home/alex/.mozilla/firefox/hixy0xse.default/adblockplus/patterns-backup1.ini
452    /home/alex/.mozilla/firefox/hixy0xse.default/adblockplus/patterns-backup2.ini
452    /home/alex/.mozilla/firefox/hixy0xse.default/adblockplus/patterns.ini
460    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/D
500    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/B
520    /home/alex/.mozilla/firefox/hixy0xse.default/cookies.sqlite
540    /home/alex/.fontconfig
544    /home/alex/.cache/software-center/rnrclient
544    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/0
568    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/8
592    /home/alex/.mozilla/firefox/hixy0xse.default/startupCache/startupCache.8.little
596    /home/alex/.mozilla/firefox/hixy0xse.default/startupCache
624    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/6/D3/35F23d01
624    /home/alex/.mozilla/firefox/hixy0xse.default/extensions/{d10d0bf8-f5b5-c8b4-a8b2-2b9879e08c5d}.xpi
628    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/6/D3
628    /home/alex/.mozilla/firefox/hixy0xse.default/extensions
672    /home/alex/.mozilla/firefox/hixy0xse.default/adblockplus/cache.js
684    /home/alex/.mozilla/firefox/hixy0xse.default/cookies.sqlite-wal
684    /home/alex/.thumbnails/normal
720    /home/alex/.thumbnails
748    /home/alex/.cache/compizconfig-1
756    /home/alex/.cache/software-center/software-center-agent.db
768    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/3
824    /home/alex/.mozilla/firefox/hixy0xse.default/sessionstore.js
844    /home/alex/.gstreamer-0.10/registry.x86_64.bin
848    /home/alex/.gstreamer-0.10
868    /home/alex/.local/share
872    /home/alex/.local
904    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/6
932    /home/alex/.mozilla/firefox/hixy0xse.default/adblockplus/elemhide.css
972    /home/alex/.mozilla/firefox/hixy0xse.default/places.sqlite-wal
992    /home/alex/Downloads/ubuntu-tweak_0.5.14-1~natty1_all.deb
996    /home/alex/Downloads
1064    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/A
1264    /home/alex/.cache/software-center/icons
1268    /home/alex/.config/ubuntu-tweak/temp/appcenter-1304049780.tar.gz
1272    /home/alex/.config/ubuntu-tweak/temp
1352    /home/alex/.mozilla/firefox/hixy0xse.default/sessionstore.bak
1676    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/_CACHE_001_
2572    /home/alex/.gconf/apps/compizconfig-1/profiles/unity/plugins
2636    /home/alex/.gconf/apps/compizconfig-1/profiles/unity
2652    /home/alex/.gconf/apps/compizconfig-1/profiles
2668    /home/alex/.gconf/apps/compizconfig-1
2976    /home/alex/.mozilla/firefox/hixy0xse.default/adblockplus
3032    /home/alex/.cache/software-center
3748    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/_CACHE_002_
3776    /home/alex/.gconf/apps
3924    /home/alex/.gconf
4312    /home/alex/.cache
4988    /home/alex/.mozilla/firefox/hixy0xse.default/Cache/_CACHE_003_
7008    /home/alex/.config/ubuntu-tweak/appcenter/appcenter/logo
7012    /home/alex/.config/ubuntu-tweak/appcenter/appcenter
7120    /home/alex/.config/ubuntu-tweak/appcenter
8432    /home/alex/.config/ubuntu-tweak
8588    /home/alex/.config
10248    /home/alex/.mozilla/firefox/hixy0xse.default/places.sqlite
17944    /home/alex/.mozilla/firefox/hixy0xse.default/Cache
30732    /home/alex/.mozilla/firefox/hixy0xse.default/urlclassifier3.sqlite
70188    /home/alex/.mozilla/firefox/hixy0xse.default
70232    /home/alex/.mozilla/firefox
70240    /home/alex/.mozilla
67113240    /home/alex/.xsession-errors.old
67205616    /home/alex
alex@alex-EP45-UD3R:~$ 

```

The terminal output fills up, and I cannot output all the files, I've never figured out how to do that...I tried piping the output to a text file, but it gave me a "cannot access /home/alex/.gvfs: Permission denied"

---

### Post by WasMeHere on 2011-10-12
This is the big directory (size is in kB), so it is 67 GiB.
> 
67113240    /home/alex/.xsession-errors.old

I guess it is some repeated complaint about your xsession. Can you look into the directory and try to see what is written in the files?

xsession should be about graphics, not sound, but what if you remove your program "Sound Change Applier" anyway, just to be sure it does not interfere?

What graphics card or chip do you use? Are you using the default driver or have you installed and activated a proprietary driver (e.g. nvidia)?

[I]Edit: I looked into my corresponding files (not directories)
```
olle@April-2008:~$ ls -l .xsession-errors*
-rw------- 1 olle olle 7210 2011-10-12 07:20 .xsession-errors
-rw------- 1 olle olle 9085 2011-10-12 01:38 .xsession-errors.old
```
and there are two files of approximately the same size. I think your current file *.xsession-errors* is fairly small. **Check if it grows with time**! If not, simply delete the big file:
```
rm /home/alex/.xsession-errors.old
```
otherwise we must find the reason why it grows[/I]

---

### Post by alman9898 on 2011-10-12
Well, after taking a break from this experience, I logged back in to Ubuntu and everything seems to be OK. I'll have to use the system longer to see if it overflows again. 

I didn't try deleting the x-sessions file as it seems to be the right size...but the problem could always re-appear, given that the system was experiencing similar problems before I reinstalled.

Just for information sake:

I'm using a proprietary driver from nvidia.

the "sound change" program doesn't actually deal with audio, it deals with manipulating text files.

---

### Post by Stanwilliamsmusic on 2012-04-13
There seems to be No delete option for posts here ?
I was replying and  made a mistake and now just want to delete my post...

---

