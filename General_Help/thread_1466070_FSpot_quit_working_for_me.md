---
title: "FSpot quit working for me"
date: 2010-04-30
forum: General Help
---

### Post by Chuck_N on 2010-04-30
using 9.10 Ubuntu Karmic Koala
recently FSpot quit working.
Whether I choose from Applications,
or rightclick a JPG and choose Open With FSpot,
it tries for about 15 seconds, the spinny-jiggy goes around,
and then nothing.............

I'm a newbie; don't know how to go about
deleting and reinstalling, which I assume is what to do....?
I searched and found nothing similar.

-Chuck

---

### Post by jobix on 2010-04-30
If you go to System->Administration->Synaptic Package Manager, you can search for "f-spot". When it shows up, delete it. Then install it again. You can also do this from the command line if you want to using apt-get.

---

### Post by Chuck_N on 2010-04-30
I get to Package Manager and get

[COLOR=Red]E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please repor[/COLOR]t.

I will try to enter
   [COLOR=Black]sudo dpkg --configure -a[/COLOR]

---

### Post by Chuck_N on 2010-04-30
okay, I got that to happen:

[COLOR=Red]chuck@chuck-desktop:~$ sudo dpkg --configure -a
[sudo] password for chuck: 
Setting up libpq5 (8.4.3-0ubuntu9.10.1) ...

Setting up linux-libc-dev (2.6.31-21.59) ...
Setting up linux-image-2.6.31-21-generic (2.6.31-21.59) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.31-21-generic
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-21-generic
Found initrd image: /boot/initrd.img-2.6.31-21-generic
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows 2000 Professional on /dev/sdb1
grub-probe: error: Cannot find a GRUB drive for /dev/sdb1.  Check your device.map.

done
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/nvidia-common

Setting up gnome-games-common (1:2.28.0-0ubuntu3) ...

Setting up gnotravex (1:2.28.0-0ubuntu3) ...

Setting up linux-headers-2.6.31-21 (2.6.31-21.59) ...
Setting up linux-image-generic (2.6.31.21.34) ...
Setting up glchess (1:2.28.0-0ubuntu3) ...

Setting up gnometris (1:2.28.0-0ubuntu3) ...

Setting up gnomine (1:2.28.0-0ubuntu3) ...

Setting up gnome-mahjongg (1:2.28.0-0ubuntu3) ...

Setting up linux-headers-2.6.31-21-generic (2.6.31-21.59) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common

Setting up gnobots2 (1:2.28.0-0ubuntu3) ...

Setting up iagno (1:2.28.0-0ubuntu3) ...

Setting up linux-generic (2.6.31.21.34) ...
Setting up gnibbles (1:2.28.0-0ubuntu3) ...

Setting up linux-headers-generic (2.6.31.21.34) ...
Setting up same-gnome (1:2.28.0-0ubuntu3) ...

Setting up aisleriot (1:2.28.0-0ubuntu3) ...

Setting up gnotski (1:2.28.0-0ubuntu3) ...

Setting up glines (1:2.28.0-0ubuntu3) ...

Setting up gtali (1:2.28.0-0ubuntu3) ...

Setting up gnect (1:2.28.0-0ubuntu3) ...

Setting up gnome-blackjack (1:2.28.0-0ubuntu3) ...

Setting up gnome-sudoku (1:2.28.0-0ubuntu3) ...

Setting up gnome-games (1:2.28.0-0ubuntu3) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...
chuck@chuck-desktop:~$ ^C
chuck@chuck-desktop:~$ [/COLOR]                     


Don't really understand what I did, but I did it ...........

---

### Post by Chuck_N on 2010-04-30
did an   FSpot  remove
then an   FSpot  install
and a restart

no difference; running FSpot gets me nowhere new.

---

### Post by jobix on 2010-04-30
The earlier error about dpkg -configure was because somehow dpkg got corrupted. Maybe you lost a connection while it was doing its update or something? Anyway, you seem to have that fixed. As for why f-spot still doesn't work, at this point, I don't know. The one thing I might try to do is remove f-spot, restart the system, reinstall f-spot again. Though I'm sure not how much that will help. 

You could try to see if there is anything being logged. Check the file /var/log/messages and also the file named .xsession-errors in your home directory.

If none of this proves helpful, check this page to see if there's anything similar logged as a bug:
[https://bugs.launchpad.net/ubuntu/+source/f-spot/+bugs?field.status:list=NEW](https://bugs.launchpad.net/ubuntu/+source/f-spot/+bugs?field.status:list=NEW)

As a last resort, you might just want to try to install it manually:
[https://launchpad.net/ubuntu/+source/f-spot/0.6.1.5-2ubuntu6](https://launchpad.net/ubuntu/+source/f-spot/0.6.1.5-2ubuntu6)
Just be sure to remove it via Synaptic before going this route.

Download the f-spot_0.6.1.5.orig.tar.gz file and follow instructions from there.

Good luck.

---

### Post by Chuck_N on 2010-05-01
The earlier error about dpkg -configure was because somehow dpkg got corrupted. Maybe you lost a connection while it was doing its update or something? Anyway, you seem to have that fixed. As for why f-spot still doesn't work, at this point, I don't know. The one thing I might try to do is remove f-spot, restart the system, reinstall f-spot again. Though I'm sure not how much that will help. 
[COLOR=Red]removed, restarted, reinstalled; redisappointed.[/COLOR]

You could try to see if there is anything being logged. Check the file /var/log/messages and also the file named .xsession-errors in your home directory.
[COLOR=Red]I looked in Administration/LogFileViewer   The file messages has thousands of lines.  Could not find   .xsession-errors[/COLOR]

If none of this proves helpful, check this page to see if there's anything similar logged as a bug:
[https://bugs.launchpad.net/ubuntu/+s...tatus:list=NEW]("https://bugs.launchpad.net/ubuntu/+source/f-spot/+bugs?field.status:list=NEW")
[COLOR=Red]I went through the entire list and found nothing similar.[/COLOR]

As a last resort, you might just want to try to install it manually:
[https://launchpad.net/ubuntu/+source...6.1.5-2ubuntu6]("https://launchpad.net/ubuntu/+source/f-spot/0.6.1.5-2ubuntu6")
Just be sure to remove it via Synaptic before going this route.

Download the f-spot_0.6.1.5.orig.tar.gz file and follow instructions from there.
  [COLOR=Red] Downloaded  [f-spot_0.6.1.5-0ubuntu1.dsc]("https://launchpad.net/ubuntu/karmic/+source/f-spot/0.6.1.5-0ubuntu1/+files/f-spot_0.6.1.5-0ubuntu1.dsc") ; extracted; found a file INSTALL. Opened it and got these instructions:[/COLOR]
  [COLOR=SeaGreen] The simplest way to compile this package is:

  1. `cd' to the directory containing the package's source code and type
     `./configure' to configure the package for your system.  If you're
     using `csh' on an old version of System V, you might need to type
     `sh ./configure' instead to prevent `csh' from trying to execute
     `configure' itself.

     Running `configure' takes awhile.  While running, it prints some
     messages telling which features it is checking for.

  2. Type `make' to compile the package.

  3. Optionally, type `make check' to run any self-tests that come with
     the package.

  4. Type `make install' to install the programs and any data files and
     documentation.

  5. You can remove the program binaries and object files from the
     source code directory by typing `make clean'.  To also remove the
     files that `configure' created (so you can compile the package for
     a different kind of computer), type `make distclean'.  There is
     also a `make maintainer-clean' target, but that is intended mainly
     for the package's developers.  If you use it, you may have to get
     all sorts of other programs in order to regenerate files that came
     with the distribution.[/COLOR]
[COLOR=Red]Unfortunately, I get lost on step 1.  I understand  cd  and  dir  and all that DOS-stuff from pre-Windows days, but I can't see how to do it on this system.[/COLOR] [COLOR=Red] Don't I need a DOS prompt, like   >   ?[/COLOR]

Good luck.

---

### Post by jobix on 2010-05-01
You will need to open a terminal. Go to Applications->Accessories->Terminal. You can find "Applications" in the top left corner of your screen.

---

### Post by todak on 2010-05-01
Open a terminal and type in the command *f-spot*. Any error messages will be displayed in the terminal while f-spot tries to load. Copy and paste the error message here.

---

### Post by HC48 on 2010-05-10
hello,
I have a similar problem in Lucid. I can't open f-spot using the program menu but "sudo f-spot" in the terminal opens it. It's strange because I used the same CD to install Lucid as someone else who can open f-spot in the normal way.
I have tried deleting and reinstalling with the graphic interface and via the synaptic packets, restarting in between each action to no avail. I can always use the terminal but would like to have the usual lazy way if possible...
When I type f-spot in the terminal I get:
[Info  14:43:54.043] Initializing DBus
[Info  14:43:54.250] Initializing Mono.Addins
[Info  14:43:54.529] Starting new FSpot server (f-spot 0.6.1.5)
[Info  14:43:54.693] Updating F-Spot Database

Unhandled Exception: Mono.Data.SqliteClient.SqliteSyntaxException: no such table: tags
  at Mono.Data.SqliteClient.SqliteCommand.GetNextStatement (IntPtr pzStart, System.IntPtr& pzTail, System.IntPtr& pStmt) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteReader (CommandBehavior behavior, Boolean want_results, System.Int32& rows_affected) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteNonQuery () [0x00000] 
  at Banshee.Database.QueuedSqliteCommand.Execute () [0x00000] 

Thank you for any suggestions.
H :)

---

### Post by HC48 on 2010-05-20
I'm replying to myself...
got Wine and Xnview. Fine!
H :)

---

### Post by Matt3223 on 2010-06-11
I noticed a similar problem with my new ubuntu netbook edition - lucid system.

Opening f-spot while logged into the admin account works just fine, however, while logged into the second "desktop user" account, f-spot doesn't open, and terminal gives the following:

> family@mjh-laptop:~$ f-spot
[Info  22:57:14.881] Initializing DBus
[Info  22:57:15.219] Initializing Mono.Addins
[Info  22:57:15.723] Starting new FSpot server (f-spot 0.6.1.5)
[Info  22:57:15.953] Updating F-Spot Database

Unhandled Exception: Mono.Data.SqliteClient.SqliteSyntaxException: no such table: tags
  at Mono.Data.SqliteClient.SqliteCommand.GetNextStatement (IntPtr pzStart, System.IntPtr& pzTail, System.IntPtr& pStmt) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteReader (CommandBehavior behavior, Boolean want_results, System.Int32& rows_affected) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteNonQuery () [0x00000] 
  at Banshee.Database.QueuedSqliteCommand.Execute () [0x00000] 
family@mjh-laptop:~$ 

can the database only be accessed and updated using the admin account because it has more privileges?

---

### Post by Chuck_N on 2010-06-30
> **todak said:**
> Open a terminal and type in the command *f-spot*. Any error messages will be displayed in the terminal while f-spot tries to load. Copy and paste the error message here.

I did and F-Spot worked.  Here is what was generated in terminal

chuck@chuck-desktop:~$ f-spot
[Info  17:35:00.647] Initializing DBus
[Info  17:35:01.136] Initializing Mono.Addins
[Info  17:35:02.213] Starting new FSpot server (f-spot 0.6.1.5)
error checking orientation
[Info  17:35:06.381] Starting BeagleService
[Info  17:35:06.543] Hack for gnome-settings-daemon engaged
error checking orientation

(f-spot:1603): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.
error checking orientation

(f-spot:1603): Gdk-WARNING **: losing last reference to undestroyed window

[Info  17:35:13.706] Exiting
chuck@chuck-desktop:~$ ^C
chuck@chuck-desktop:~$ ^C
chuck@chuck-desktop:~$

---

### Post by HC48 on 2012-06-24
later... gThumb works great! I gave up Fspot.

---

### Post by sffvba[e0rt on 2012-06-24
*Back to sleep **old **thread...*


404

---

