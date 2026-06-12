---
title: "Folder wont open"
date: 2010-06-07
forum: General Help
---

### Post by maxwell-mays on 2010-06-07
Well here is my little problem... I go to PLACES and try opening any of my folders fox example   DOCUMENTS... and it wont open....  I have to actually go to  COMPUTER then on the sidebar go to DOCUMENts or Pictures and so on....  This problem started happening a wile ago when i started playing with WINE... i think by mistake i touch something i dint have to.... well... I removed wine and my folders where able to be looked at again.... but i recently installed wine again to playonlinux  some games.... and poof  again with the problem. 

HELP?

---

### Post by pytheas22 on 2010-06-07
What is the output in a terminal of:
```

cat ~/.gtk-bookmarks
```

---

### Post by maxwell-mays on 2010-06-07
> **pytheas22 said:**
> What is the output in a terminal of:
```

cat ~/.gtk-bookmarks
```


ken@ken-laptop:~$ cat ~/.gtk-bookmarks
file:///home/ken/Documents
file:///home/ken/Music
file:///home/ken/Pictures
file:///home/ken/Videos
file:///home/ken/Downloads
file:///home/ken/Games
ken@ken-laptop:~$

---

### Post by pytheas22 on 2010-06-07
Nothing looks strange there.  The only thing I can think to do is try to debug nautilus, the Ubuntu file manager.  To do that, first type:

```
gedit ~/nautilus-debug-log.conf
```

A blank file will open.  Add these lines to it, then save it:

```
[debug log]
max lines = 1000
enable domains = GLog;async;desktop-links
```

To start debugging, type:
```

sudo killall -USR1 nautilus
```

Now try accessing Documents from the Places menu a few times.  Afterwards, type:

```
cat nautilus-debug-log.txt
```

and post the output here.

---

### Post by maxwell-mays on 2010-06-07
> **pytheas22 said:**
> Nothing looks strange there.  The only thing I can think to do is try to debug nautilus, the Ubuntu file manager.  To do that, first type:

```
gedit ~/nautilus-debug-log.conf
```A blank file will open.  Add these lines to it, then save it:

```
[debug log]
max lines = 1000
enable domains = GLog;async;desktop-links
```To start debugging, type:
```

sudo killall -USR1 nautilus
```Now try accessing Documents from the Places menu a few times.  Afterwards, type:

```
cat nautilus-debug-log.txt
```and post the output here.

I did all the steps.... but nothing... i press in places for example DOCUMENTS and in the bottom taskbar it says  Opening Documents and  it wont open =\  this is the txt i got from the command..

===== BEGIN MILESTONES =====
0xa172008 2010/06/07 19:11:54.1314 (GLog): Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

0xa172008 2010/06/07 19:19:14.9033 (USER): user requested dump of debug log
===== END MILESTONES =====
===== BEGIN RING BUFFER =====
0xa172008 2010/06/07 18:33:28.0965 (USER): window 0xa204068 open location: old="(none)", new="x-nautilus-desktop:///"
0xa172008 2010/06/07 18:33:29.0711 (USER): finished loading window 0xa204068: x-nautilus-desktop:///
0xa172008 2010/06/07 18:34:22.7075 (USER): create new navigation window=0xa3f7028
0xa172008 2010/06/07 18:34:22.7076 (USER): window 0xa3f7028 open location: old="(none)", new="computer:///"
0xa172008 2010/06/07 18:34:24.4673 (USER): change view of window 0xa3f7028: "computer:///" to "OAFIID:Nautilus_File_Manager_Icon_View"
0xa172008 2010/06/07 18:34:24.6852 (USER): finished loading window 0xa3f7028: computer:///
0xa172008 2010/06/07 18:34:28.4349 (USER): activate from places sidebar window=0xa3f7028: file:///home/ken/Downloads
0xa172008 2010/06/07 18:34:28.4350 (USER): window 0xa3f7028 open location: old="computer:///", new="file:///home/ken/Downloads"
0xa172008 2010/06/07 18:34:28.4350 (USER): finished loading window 0xa3f7028: computer:///
0xa172008 2010/06/07 18:34:28.5994 (USER): change view of window 0xa3f7028: "file:///home/ken/Downloads" to "OAFIID:Nautilus_File_Manager_Icon_View"
0xa172008 2010/06/07 18:34:28.8482 (USER): finished loading window 0xa3f7028: file:///home/ken/Downloads
0xa172008 2010/06/07 18:34:36.4014 (USER): selection changed in window 0xa3f7028
    file:///home/ken/Downloads/jre-6u20-linux-i586.bin
0xa172008 2010/06/07 18:34:38.2374 (USER): nautilus_mime_activate_files window=0xa3f7028
    file:///home/ken/Downloads/jre-6u20-linux-i586.bin
0xa172008 2010/06/07 18:34:46.4337 (USER): selection changed in window 0xa3f7028
    file:///home/ken/Downloads/jre-6u20-linux-i586-rpm.bin
0xa172008 2010/06/07 18:34:50.4646 (USER): selection changed in window 0xa3f7028
    file:///home/ken/Downloads/jre-6u20-linux-i586.bin
0xa172008 2010/06/07 18:34:50.9756 (USER): selection changed in window 0xa3f7028
0xa172008 2010/06/07 18:37:21.3087 (USER): create new navigation window=0xa3f7188
0xa172008 2010/06/07 18:37:21.3088 (USER): window 0xa3f7188 open location: old="(none)", new="computer:///"
0xa172008 2010/06/07 18:37:21.4968 (USER): change view of window 0xa3f7188: "computer:///" to "OAFIID:Nautilus_File_Manager_Icon_View"
0xa172008 2010/06/07 18:37:21.6635 (USER): finished loading window 0xa3f7188: computer:///
0xa172008 2010/06/07 18:37:23.6435 (USER): activate from places sidebar window=0xa3f7188: file:///home/ken/Downloads
0xa172008 2010/06/07 18:37:23.6436 (USER): window 0xa3f7188 open location: old="computer:///", new="file:///home/ken/Downloads"
0xa172008 2010/06/07 18:37:23.6436 (USER): finished loading window 0xa3f7188: computer:///
0xa172008 2010/06/07 18:37:23.6965 (USER): change view of window 0xa3f7188: "file:///home/ken/Downloads" to "OAFIID:Nautilus_File_Manager_Icon_View"
0xa172008 2010/06/07 18:37:23.7779 (USER): finished loading window 0xa3f7188: file:///home/ken/Downloads
0xa172008 2010/06/07 18:37:27.4977 (USER): selection changed in window 0xa3f7188
    file:///home/ken/Downloads/jre-6u20-linux-x64.bin
0xa172008 2010/06/07 18:37:27.6572 (USER): nautilus_mime_activate_files window=0xa3f7188
    file:///home/ken/Downloads/jre-6u20-linux-x64.bin
0xa172008 2010/06/07 18:37:31.5759 (USER): selection changed in window 0xa3f7188
    file:///home/ken/Downloads/jre-6u20-linux-i586.bin
    file:///home/ken/Downloads/jre-6u20-linux-x64.bin
0xa172008 2010/06/07 18:37:32.0237 (USER): selection changed in window 0xa3f7188
    file:///home/ken/Downloads/jre-6u20-linux-i586.bin
    file:///home/ken/Downloads/jre-6u20-linux-i586-rpm.bin
    file:///home/ken/Downloads/jre-6u20-linux-x64.bin
0xa172008 2010/06/07 18:37:33.1087 (USER): selection changed in window 0xa3f7188
0xa172008 2010/06/07 18:37:33.1094 (USER): selection changed in window 0xa3f7188
0xa172008 2010/06/07 18:37:33.1094 (USER): selection changed in window 0xa3f7188
0xa172008 2010/06/07 18:37:46.9703 (USER): create new navigation window=0xa3f72e8
0xa172008 2010/06/07 18:37:46.9703 (USER): window 0xa3f72e8 open location: old="(none)", new="computer:///"
0xa172008 2010/06/07 18:37:47.1571 (USER): change view of window 0xa3f72e8: "computer:///" to "OAFIID:Nautilus_File_Manager_Icon_View"
0xa172008 2010/06/07 18:37:47.2968 (USER): finished loading window 0xa3f72e8: computer:///
0xa172008 2010/06/07 18:37:48.2699 (USER): activate from places sidebar window=0xa3f72e8: file:///home/ken/Downloads
0xa172008 2010/06/07 18:37:48.2700 (USER): window 0xa3f72e8 open location: old="computer:///", new="file:///home/ken/Downloads"
0xa172008 2010/06/07 18:37:48.2700 (USER): finished loading window 0xa3f72e8: computer:///
0xa172008 2010/06/07 18:37:48.3088 (USER): change view of window 0xa3f72e8: "file:///home/ken/Downloads" to "OAFIID:Nautilus_File_Manager_Icon_View"
0xa172008 2010/06/07 18:37:48.3992 (USER): finished loading window 0xa3f72e8: file:///home/ken/Downloads
0xa172008 2010/06/07 18:41:10.3922 (USER): create new navigation window=0xa3f7448
0xa172008 2010/06/07 18:41:10.3922 (USER): window 0xa3f7448 open location: old="(none)", new="computer:///"
0xa172008 2010/06/07 18:41:10.5775 (USER): change view of window 0xa3f7448: "computer:///" to "OAFIID:Nautilus_File_Manager_Icon_View"
0xa172008 2010/06/07 18:41:10.7291 (USER): finished loading window 0xa3f7448: computer:///
0xa172008 2010/06/07 18:41:12.4808 (USER): activate from places sidebar window=0xa3f7448: file:///home/ken/Downloads
0xa172008 2010/06/07 18:41:12.4808 (USER): window 0xa3f7448 open location: old="computer:///", new="file:///home/ken/Downloads"
0xa172008 2010/06/07 18:41:12.4809 (USER): finished loading window 0xa3f7448: computer:///
0xa172008 2010/06/07 18:41:12.5202 (USER): change view of window 0xa3f7448: "file:///home/ken/Downloads" to "OAFIID:Nautilus_File_Manager_Icon_View"
0xa172008 2010/06/07 18:41:12.6330 (USER): finished loading window 0xa3f7448: file:///home/ken/Downloads
0xa172008 2010/06/07 18:41:14.8160 (USER): selection changed in window 0xa3f7448
    file:///home/ken/Downloads/LimeWireLinux.deb
0xa172008 2010/06/07 18:41:15.1595 (USER): nautilus_mime_activate_files window=0xa3f7448
    file:///home/ken/Downloads/LimeWireLinux.deb
0xa172008 2010/06/07 19:11:47.5039 (USER): create new navigation window=0xa3f7448
0xa172008 2010/06/07 19:11:47.5040 (USER): window 0xa3f7448 open location: old="(none)", new="computer:///"
0xa172008 2010/06/07 19:11:47.6912 (USER): change view of window 0xa3f7448: "computer:///" to "OAFIID:Nautilus_File_Manager_Icon_View"
0xa172008 2010/06/07 19:11:47.8495 (USER): finished loading window 0xa3f7448: computer:///
0xa172008 2010/06/07 19:11:49.2037 (USER): activate from places sidebar window=0xa3f7448: file:///home/ken/Downloads
0xa172008 2010/06/07 19:11:49.2038 (USER): window 0xa3f7448 open location: old="computer:///", new="file:///home/ken/Downloads"
0xa172008 2010/06/07 19:11:49.2038 (USER): finished loading window 0xa3f7448: computer:///
0xa172008 2010/06/07 19:11:49.2429 (USER): change view of window 0xa3f7448: "file:///home/ken/Downloads" to "OAFIID:Nautilus_File_Manager_Icon_View"
0xa172008 2010/06/07 19:11:49.3335 (USER): finished loading window 0xa3f7448: file:///home/ken/Downloads
0xa172008 2010/06/07 19:11:53.8117 (USER): activate from places sidebar window=0xa3f7448: file:///home/ken/Documents
0xa172008 2010/06/07 19:11:53.8118 (USER): window 0xa3f7448 open location: old="file:///home/ken/Downloads", new="file:///home/ken/Documents"
0xa172008 2010/06/07 19:11:53.8118 (USER): finished loading window 0xa3f7448: file:///home/ken/Downloads
0xa172008 2010/06/07 19:11:53.8416 (USER): change view of window 0xa3f7448: "file:///home/ken/Documents" to "OAFIID:Nautilus_File_Manager_Icon_View"
0xa172008 2010/06/07 19:11:54.1314 (GLog): Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

0xa172008 2010/06/07 19:11:54.1611 (USER): finished loading window 0xa3f7448: file:///home/ken/Documents
0xa172008 2010/06/07 19:11:55.8041 (USER): selection changed in window 0xa3f7448
    file:///home/ken/Documents/ps3server
0xa172008 2010/06/07 19:11:55.9551 (USER): nautilus_mime_activate_files window=0xa3f7448
    file:///home/ken/Documents/ps3server
0xa172008 2010/06/07 19:11:55.9555 (USER): window 0xa3f7448 open location: old="file:///home/ken/Documents", new="file:///home/ken/Documents/ps3server"
0xa172008 2010/06/07 19:11:55.9555 (USER): finished loading window 0xa3f7448: file:///home/ken/Documents
0xa172008 2010/06/07 19:11:55.9957 (USER): change view of window 0xa3f7448: "file:///home/ken/Documents/ps3server" to "OAFIID:Nautilus_File_Manager_Icon_View"
0xa172008 2010/06/07 19:11:56.0900 (USER): finished loading window 0xa3f7448: file:///home/ken/Documents/ps3server
0xa172008 2010/06/07 19:12:03.9162 (USER): selection changed in window 0xa3f7448
    file:///home/ken/Documents/ps3server/pms-linux-1.20.409
0xa172008 2010/06/07 19:12:04.0430 (USER): nautilus_mime_activate_files window=0xa3f7448
    file:///home/ken/Documents/ps3server/pms-linux-1.20.409
0xa172008 2010/06/07 19:12:04.0433 (USER): window 0xa3f7448 open location: old="file:///home/ken/Documents/ps3server", new="file:///home/ken/Documents/ps3server/pms-linux-1.20.409"
0xa172008 2010/06/07 19:12:04.0433 (USER): finished loading window 0xa3f7448: file:///home/ken/Documents/ps3server
0xa172008 2010/06/07 19:12:04.0818 (USER): change view of window 0xa3f7448: "file:///home/ken/Documents/ps3server/pms-linux-1.20.409" to "OAFIID:Nautilus_File_Manager_Icon_View"
0xa172008 2010/06/07 19:12:04.1904 (USER): finished loading window 0xa3f7448: file:///home/ken/Documents/ps3server/pms-linux-1.20.409
0xa172008 2010/06/07 19:12:07.1721 (USER): selection changed in window 0xa3f7448
    file:///home/ken/Documents/ps3server/pms-linux-1.20.409/PMS.sh
0xa172008 2010/06/07 19:12:07.3155 (USER): nautilus_mime_activate_files window=0xa3f7448
    file:///home/ken/Documents/ps3server/pms-linux-1.20.409/PMS.sh
0xa172008 2010/06/07 19:12:08.4681 (USER): directory view activate_callback launch_in_terminal window=0xa3f7448: '/home/ken/Documents/ps3server/pms-linux-1.20.409/PMS.sh'
0xa172008 2010/06/07 19:12:19.1321 (USER): selection changed in window 0xa3f7448
    file:///home/ken/Documents/ps3server/pms-linux-1.20.409/linux
0xa172008 2010/06/07 19:12:19.2599 (USER): nautilus_mime_activate_files window=0xa3f7448
    file:///home/ken/Documents/ps3server/pms-linux-1.20.409/linux
0xa172008 2010/06/07 19:12:19.2602 (USER): window 0xa3f7448 open location: old="file:///home/ken/Documents/ps3server/pms-linux-1.20.409", new="file:///home/ken/Documents/ps3server/pms-linux-1.20.409/linux"
0xa172008 2010/06/07 19:12:19.2602 (USER): finished loading window 0xa3f7448: file:///home/ken/Documents/ps3server/pms-linux-1.20.409
0xa172008 2010/06/07 19:12:19.3087 (USER): change view of window 0xa3f7448: "file:///home/ken/Documents/ps3server/pms-linux-1.20.409/linux" to "OAFIID:Nautilus_File_Manager_Icon_View"
0xa172008 2010/06/07 19:12:19.4444 (USER): finished loading window 0xa3f7448: file:///home/ken/Documents/ps3server/pms-linux-1.20.409/linux
0xa172008 2010/06/07 19:12:21.4897 (USER): finished loading window 0xa3f7448: file:///home/ken/Documents/ps3server/pms-linux-1.20.409/linux
0xa172008 2010/06/07 19:12:21.5291 (USER): change view of window 0xa3f7448: "file:///home/ken/Documents/ps3server/pms-linux-1.20.409" to "OAFIID:Nautilus_File_Manager_Icon_View"
0xa172008 2010/06/07 19:12:21.6098 (USER): finished loading window 0xa3f7448: file:///home/ken/Documents/ps3server/pms-linux-1.20.409
0xa172008 2010/06/07 19:13:43.4455 (USER): create new navigation window=0xa3f72e8
0xa172008 2010/06/07 19:13:43.4456 (USER): window 0xa3f72e8 open location: old="(none)", new="computer:///"
0xa172008 2010/06/07 19:13:43.6430 (USER): change view of window 0xa3f72e8: "computer:///" to "OAFIID:Nautilus_File_Manager_Icon_View"
0xa172008 2010/06/07 19:13:43.8123 (USER): finished loading window 0xa3f72e8: computer:///
0xa172008 2010/06/07 19:13:48.7077 (USER): activate from places sidebar window=0xa3f72e8: file:///home/ken/Videos
0xa172008 2010/06/07 19:13:48.7078 (USER): window 0xa3f72e8 open location: old="computer:///", new="file:///home/ken/Videos"
0xa172008 2010/06/07 19:13:48.7078 (USER): finished loading window 0xa3f72e8: computer:///
0xa172008 2010/06/07 19:13:48.7317 (USER): change view of window 0xa3f72e8: "file:///home/ken/Videos" to "OAFIID:Nautilus_File_Manager_Icon_View"
0xa172008 2010/06/07 19:13:48.8439 (USER): finished loading window 0xa3f72e8: file:///home/ken/Videos
0xa172008 2010/06/07 19:13:50.1960 (USER): selection changed in window 0xa3f72e8
    file:///home/ken/Videos/300.mp4
0xa172008 2010/06/07 19:13:51.0437 (USER): selection changed in window 0xa3f72e8
0xa172008 2010/06/07 19:13:51.6520 (USER): selection changed in window 0xa3f72e8
    file:///home/ken/Videos/300.mp4
0xa172008 2010/06/07 19:15:08.0682 (USER): selection changed in window 0xa3f72e8
    file:///home/ken/Videos/Toy%20Story%20(1995)
0xa172008 2010/06/07 19:15:08.2037 (USER): nautilus_mime_activate_files window=0xa3f72e8
    file:///home/ken/Videos/Toy%20Story%20(1995)
0xa172008 2010/06/07 19:15:08.2040 (USER): window 0xa3f72e8 open location: old="file:///home/ken/Videos", new="file:///home/ken/Videos/Toy%20Story%20(1995)"
0xa172008 2010/06/07 19:15:08.2041 (USER): finished loading window 0xa3f72e8: file:///home/ken/Videos
0xa172008 2010/06/07 19:15:08.2421 (USER): change view of window 0xa3f72e8: "file:///home/ken/Videos/Toy%20Story%20(1995)" to "OAFIID:Nautilus_File_Manager_Icon_View"
0xa172008 2010/06/07 19:15:08.3549 (USER): finished loading window 0xa3f72e8: file:///home/ken/Videos/Toy%20Story%20(1995)
0xa172008 2010/06/07 19:15:10.5457 (USER): finished loading window 0xa3f72e8: file:///home/ken/Videos/Toy%20Story%20(1995)
0xa172008 2010/06/07 19:15:10.5845 (USER): change view of window 0xa3f72e8: "file:///home/ken/Videos" to "OAFIID:Nautilus_File_Manager_Icon_View"
0xa172008 2010/06/07 19:15:10.6624 (USER): finished loading window 0xa3f72e8: file:///home/ken/Videos
0xa172008 2010/06/07 19:15:27.8119 (USER): selection changed in window 0xa3f72e8
    file:///home/ken/Videos/Toy%20Story%20(1995)
0xa172008 2010/06/07 19:15:27.9315 (USER): nautilus_mime_activate_files window=0xa3f72e8
    file:///home/ken/Videos/Toy%20Story%20(1995)
0xa172008 2010/06/07 19:15:27.9318 (USER): window 0xa3f72e8 open location: old="file:///home/ken/Videos", new="file:///home/ken/Videos/Toy%20Story%20(1995)"
0xa172008 2010/06/07 19:15:27.9318 (USER): finished loading window 0xa3f72e8: file:///home/ken/Videos
0xa172008 2010/06/07 19:15:27.9610 (USER): change view of window 0xa3f72e8: "file:///home/ken/Videos/Toy%20Story%20(1995)" to "OAFIID:Nautilus_File_Manager_Icon_View"
0xa172008 2010/06/07 19:15:28.0617 (USER): finished loading window 0xa3f72e8: file:///home/ken/Videos/Toy%20Story%20(1995)
0xa172008 2010/06/07 19:19:14.9033 (USER): user requested dump of debug log
===== END RING BUFFER =====


This configuration for the debug log can be re-created
by putting the following in ~/nautilus-debug-log.conf
(use ';' to separate domain names):


[debug log]
max lines=1000

---

### Post by pytheas22 on 2010-06-07
I was hoping there would be some feedback in that log file that would help troubleshoot what was going on, but unfortunately I don't see anything at all.  From what I can make of it, the log seems to think the Documents window opened without a problem.

So I'm kind of out of ideas, unless you can remember more about what changes you might have made involving wine around the same time that this problem appeared.

Also, if you want to stop nautilus from logging everything, you can delete the log configuration file with:
```

rm ~/nautilus-debug-log.conf
```

---

### Post by maxwell-mays on 2010-06-07
> **pytheas22 said:**
> I was hoping there would be some feedback in that log file that would help troubleshoot what was going on, but unfortunately I don't see anything at all.  From what I can make of it, the log seems to think the Documents window opened without a problem.

So I'm kind of out of ideas, unless you can remember more about what changes you might have made involving wine around the same time that this problem appeared.

Also, if you want to stop nautilus from logging everything, you can delete the log configuration file with:
```

rm ~/nautilus-debug-log.conf
```


=) thanks ima try it. also im gonna try uninstalling wine.... to see if it works if it does is there anyways to un install EVERY CONFIGURATION of WINE so when i re install is fresh and clean?

---

### Post by pytheas22 on 2010-06-08
> also im gonna try uninstalling wine.... to see if it works if it does is there anyways to un install EVERY CONFIGURATION of WINE so when i re install is fresh and clean?

Wine stores most of its data in a directory in your home folder named .wine, so if you just delete or rename that, you'll force a fresh configuration.  This command would rename the directory:
```

mv ~/.wine ~/.wine-old
```

You can also purge the wine binaries from your system with:
```

sudo apt-get remove --purge wine
```

and then reinstall the "wine" package in the Software Center to get a clean installation.

I'm curious to see if wine is really causing problems with the Nautilus menu, so let us know how you get on.

---

### Post by maxwell-mays on 2010-06-09
> **pytheas22 said:**
> Wine stores most of its data in a directory in your home folder named .wine, so if you just delete or rename that, you'll force a fresh configuration.  This command would rename the directory:
```

mv ~/.wine ~/.wine-old
```You can also purge the wine binaries from your system with:
```

sudo apt-get remove --purge wine
```and then reinstall the "wine" package in the Software Center to get a clean installation.

I'm curious to see if wine is really causing problems with the Nautilus menu, so let us know how you get on.


I tried to PURGE the application but...   it wont Un Install it...

this is all i get on terminal. 

ken@ken-laptop:~$ sudo apt-get remove --purge wine
[sudo] password for ken: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  wine*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 65.5kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 174662 files and directories currently installed.)
Removing wine ...
ken@ken-laptop:~$

---

### Post by maxwell-mays on 2010-06-09
> **maxwell-mays said:**
> I tried to PURGE the application but...   it wont Un Install it...

this is all i get on terminal. 

ken@ken-laptop:~$ sudo apt-get remove --purge wine
[sudo] password for ken: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  wine*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 65.5kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 174662 files and directories currently installed.)
Removing wine ...
ken@ken-laptop:~$

Ok so i dont know if you remember but i was the one that posted the WINE  problem not letting me OPEN FOLDERS O.O.... well... i actually PURGE  the application and i also uninstall every component of wine. and  NOW  when i go to PLACES and open every folder =\... but i want wine..... i  need wine =\

---

### Post by pytheas22 on 2010-06-09
So to be clear: with wine install, the menu works correctly?  That seems really quite strange, as I'm not sure how wine could affect that.

Have you tried removing (or renaming) your ~/.wine folder in order to force a fresh configuration?  It could also possibly help to do the same with the ~/.nautilus directory, which will force a fresh configuration of nautilus.

---

### Post by maxwell-mays on 2010-06-13
> **pytheas22 said:**
> So to be clear: with wine install, the menu works correctly?  That seems really quite strange, as I'm not sure how wine could affect that.

Have you tried removing (or renaming) your ~/.wine folder in order to force a fresh configuration?  It could also possibly help to do the same with the ~/.nautilus directory, which will force a fresh configuration of nautilus.

I actually Un Install WINE and i can browse my folders correctly!  now without wine i can open them... BUT i want wine... to run games =\   how can i fresh install with a diferent folder name or something?

---

### Post by pytheas22 on 2010-06-13
> I actually Un Install WINE and i can browse my folders correctly! now without wine i can open them... BUT i want wine... to run games =\ how can i fresh install with a diferent folder name or something?

You can make a "fresh" install of your wine configuration by renaming your /home/username/.wine folder to something else, or just deleting that folder entirely.  Then reboot and wine will start off with a fresh configuration.  Any applications you currently have installed in wine will be lost.

You can rename the folder by opening up a file browser to your home folder, pressing control-H to show hidden files, and then finding the .wine folder.

---

### Post by maxwell-mays on 2010-06-13
> **pytheas22 said:**
> You can make a "fresh" install of your wine configuration by renaming your /home/username/.wine folder to something else, or just deleting that folder entirely.  Then reboot and wine will start off with a fresh configuration.  Any applications you currently have installed in wine will be lost.

You can rename the folder by opening up a file browser to your home folder, pressing control-H to show hidden files, and then finding the .wine folder.


OK... here is a pic of my HOME =\  but i cant find WINE.... im sorry for being such a noob to this... im just starting and learning.  What folder is the equivelant to PROGRAM FILES on windows =\  but for ubuntu? is it HOME?  i cant find it..  

look   [IMG]http://i45.tinypic.com/2qn3add.png[/IMG]

---

### Post by pytheas22 on 2010-06-14
No worries; we were all beginners once.  You had the right folder (your Home folder) opened, but your .wine folder is a hidden directory inside of it.  To show it, you have to press control-H, or go to View>Show Hidden Files.  The wine folder will then become visible.

The equivalent of Program Files is inside the .wine folder, along with some other stuff.  Deleting or renaming the entire .wine folder to something else, and then rebooting, will give you a fresh Wine configuration with default settings.

I'd recommend just renaming it, so that you can always restore it later if for some reason you want to--as long as it's named something other than .wine, Wine will ignore it and everything in it.

---

### Post by maxwell-mays on 2010-06-14
> **pytheas22 said:**
> No worries; we were all beginners once.  You had the right folder (your Home folder) opened, but your .wine folder is a hidden directory inside of it.  To show it, you have to press control-H, or go to View>Show Hidden Files.  The wine folder will then become visible.

The equivalent of Program Files is inside the .wine folder, along with some other stuff.  Deleting or renaming the entire .wine folder to something else, and then rebooting, will give you a fresh Wine configuration with default settings.

I'd recommend just renaming it, so that you can always restore it later if for some reason you want to--as long as it's named something other than .wine, Wine will ignore it and everything in it.


=) OK i got it and this is what has happened !

1- I Un-Installed Wine and PLAYONLINUX.
2- Then i go to Places>HOME>-Show Hidden Folders> .WINE
3- I deleted .WINE
4- Restarted Laptop
5- When i got in I Could go to Places and open my folders example PICTURES, VIDEOS, when before i could not.
6- Now i tried RE INSTALLING PlAYONLINUX  this also installs WINE.
7- Restarted the PC...
8- I go to PLACES and... i cant open the folders again.
9- All i see is like WINE is configurating folders.... and then a little window with the word ERROR comes out. And it looks like WINE is trying to open those folders as it was EMULATING something from windows =\ ......

10- I tried to RENAME the .WINE folder to .WINEX   to see if it would re configure everything...

11... Fail... also the same problem

If i have WINE un-installed.... it works i can browse my folders from my Places...

if i have it installed... POOF i cant. =\

---

### Post by pytheas22 on 2010-06-14
At least you have more certainty regarding the source of the problem.  I wonder, does it persist if you install just Wine, without installing PlayOnLinux too?

---

### Post by maxwell-mays on 2010-06-14
> **pytheas22 said:**
> At least you have more certainty regarding the source of the problem.  I wonder, does it persist if you install just Wine, without installing PlayOnLinux too?


I have not tried that.   but i think its just WINE it self... =\   how can i just delete PLAY ON LINUX?

---

### Post by pytheas22 on 2010-06-14
Open the Software Center, search for PlayOnLinux, and remove it.  Then delete your .wine folder as you did before.  Finally, install just Wine from the Software Center, without installing PlayOnLinux.

---

### Post by maxwell-mays on 2010-06-14
> **pytheas22 said:**
> Open the Software Center, search for PlayOnLinux, and remove it.  Then delete your .wine folder as you did before.  Finally, install just Wine from the Software Center, without installing PlayOnLinux.


So i removed PlayOnLinux from Software Center. I deleted all the .Wine folders from HOME by pressing SHOW ALL HIDDEN FOLDERS and looking for them,   I can still see WINE on Applications TAB on my desktop with 2 things i installed already.  Diablo 2  and windows live messenger. 

where do i delete this from Applications?

---

### Post by pytheas22 on 2010-06-14
Did you reboot or logout after deleting the .wine folders?  You would need at least to log out of your desktop and log back in for changes to take effect (if that doesn't work, try a full reboot).  That's probably why you're still seeing applications inside the Wine folder.

---

### Post by maxwell-mays on 2010-06-15
> **pytheas22 said:**
> Did you reboot or logout after deleting the .wine folders?  You would need at least to log out of your desktop and log back in for changes to take effect (if that doesn't work, try a full reboot).  That's probably why you're still seeing applications inside the Wine folder.
  

I did FULL RESTART =(... i fallowed the instructions to the letter....  and still.. 

im gonna do it again and let you know. 

In the mean time can i ask you something else about the system?

---

### Post by pytheas22 on 2010-06-15
Sure, I'll do my best to answer.

---

### Post by maxwell-mays on 2010-06-16
> **pytheas22 said:**
> Sure, I'll do my best to answer.


How do i change my SPLASH SCREEN?

Like when i boot ubuntu...    the Purple Background that says UBUNTU..

I wanna change that RESOLUTION...  how do i do that?

btw im installing WINE AGAIN right now =)

---

### Post by pytheas22 on 2010-06-17
I've never changed the boot splash myself, but I'm pretty sure you can configure it in any way you want.  Have a look at [this thread]("http://ubuntuforums.org/showthread.php?t=1446949") for instructions.

---

### Post by maxwell-mays on 2010-06-18
> **pytheas22 said:**
> I've never changed the boot splash myself, but I'm pretty sure you can configure it in any way you wan.  Have a look at [this thread]("http://ubuntuforums.org/showthread.php?t=1446949") for instructions.


I cant find in this post how to change the resolution =(... and i havent installed wine but i will right now =)

---

### Post by pytheas22 on 2010-06-19
Didn't know you wanted to change the resolution specifically (I guess you did say that).  Try [this]("http://knowledge76.com/index.php/Fixing_Bad_Plymouth_Resolution").

Why do you want to change the resolution?  Is it really low or looking bad for some other reason?

---

### Post by maxwell-mays on 2010-06-19
Yea  and thanks i fixed the resolution problem with that  same tutorial =)  btw... i un-installed everything that had to do with wine.... but  nop my error still persist....

---

### Post by maxwell-mays on 2010-06-19
> **pytheas22 said:**
> Didn't know you wanted to change the resolution specifically (I guess you did say that).  Try [this]("http://knowledge76.com/index.php/Fixing_Bad_Plymouth_Resolution").

Why do you want to change the resolution?  Is it really low or looking bad for some other reason?

I manage to fix my resolution but my WINE problem with folders... NOT YET.... look at this 
[IMG]http://i50.tinypic.com/2djt0ud.png[/IMG]

[IMG]http://i46.tinypic.com/2ebwqqf.png[/IMG]

---

### Post by pytheas22 on 2010-06-19
Good to hear you got the resolution straightened out.

Unfortunately, I'm afraid I'm kind of out of answers on the wine problem.  I googled a lot and can't find anyone else having this issue, and I can't think of any conceivable way that having wine installed should cause problems for your places menu--although that does appear to be manifestly  the case.  The only other thing I can think to do is file a bug report against Gnome and Wine, so that you'd stand a better chance of getting attention from actual developers, who might have a better idea what could be going wrong.

---

### Post by pytheas22 on 2010-06-19
Sorry, I hadn't seen your last post when I submitted my last post.  What were you trying to do when you got the "File not found" dialog box?  Or were you doing nothing and it appeared on its own?

---

### Post by maxwell-mays on 2010-06-20
> **pytheas22 said:**
> Good to hear you got the resolution straightened out.

Unfortunately, I'm afraid I'm kind of out of answers on the wine problem.  I googled a lot and can't find anyone else having this issue, and I can't think of any conceivable way that having wine installed should cause problems for your places menu--although that does appear to be manifestly  the case.  The only other thing I can think to do is file a bug report against Gnome and Wine, so that you'd stand a better chance of getting attention from actual developers, who might have a better idea what could be going wrong.


Thank you my friend you have been of great help =) 

I will do that but i just dont know how yet =) dont worry ill figure it out =)

---

