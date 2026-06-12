---
title: "How to start Beagle daemon at bootup?"
date: 2006-01-23
forum: General Help
---

### Post by kwaanens on 2006-01-23
How do I start the Beagle daemon at boot or login?
And why isn't that set up when I install it? Installing it indicates that I would like to use it, right..?

- Ketil

---

### Post by RAOF on 2006-01-23
[QUOTE=kwaanens]OK, I actually figured it out by myself, but:
When trying beagled in console I get:

```
$ beagled
ketil@inspiron:~$
Unhandled Exception: GLib.GException: Unknown error
in <0x00187> Evolution.Cal:GetChanges (string,Evolution.CalComponent[]&,Evolution.CalComponent[]&,string[]&)
in <0x00121> Beagle.Daemon.EvolutionDataServerQueryable.CalContainer:IndexChanges ()
in <0x001c8> Beagle.Daemon.EvolutionDataServerQueryable.SourcesHandler:IndexSourceGroup (Evolution.SourceGroup,bool)
in <0x001c6> Beagle.Daemon.EvolutionDataServerQueryable.SourcesHandler:.ctor (string,System.Type,Beagle.Daemon.EvolutionDataServerQueryable.EvolutionDataServerQueryable,string)
in <0x000fc> Beagle.Daemon.EvolutionDataServerQueryable.EvolutionDataServerQueryable:Start ()
in <0x00016> Beagle.Daemon.Queryable:Start ()
in <0x000e9> Beagle.Daemon.QueryDriver:Start ()
in <0x0012e> Beagle.Daemon.BeagleDaemon:StartupProcess ()
in <0x00048> (wrapper delegate-invoke) System.MulticastDelegate:invoke_bool ()
in <0x0002a> IdleProxy:Handler ()
in <0x00036> (wrapper native-to-managed) IdleProxy:Handler ()
in (unmanaged) 0xb7f6b74f
in <0x00004> (wrapper managed-to-native) Gtk.Application:gtk_main ()
in <0x00007> Gtk.Application:Run ()
in <0x0057b> Beagle.Daemon.BeagleDaemon:Main (string[])

```

Consequently:

```
$ beagle-status

Could not connect to the daemon.
```

Ideas?

- Ketil[/QUOTE]
The Evolution backend (that indexes your evolution mail, appointments, etc) was broken at some time.  I'm no longer running Breezy, so I don't know it's current status, but you might have better luck disabling the evolution backend.  Just run the beagled command with
```
beagled --disable-backend-evolution-data-server
```
(I think).  If it doesn't like that switch, beagled --help will give a list of the commandline options - one of them will be something like --disable-backend, and one of them will be something like --list-backends.
Run --list-backends, note the one with "evolution" in it.  Then run beagled with the --disable-backend-<the-evolution-backend> (or whatever it is)

---

### Post by dcstar on 2006-01-23
[QUOTE=kwaanens]How do I start the Beagle daemon at boot or login?
And why isn't that set up when I install it? Installing it indicates that I would like to use it, right..?

- Ketil[/QUOTE]
You need to examine the provided package to see if it supplies a file that goes in /etc/init.d, if it does then it may be up to you to set up a link to it in /etc/rc2.d (do a forum search on how to do this), or run it on login by doing:

System-Preferences-Sessions-Startup Programs

There can be many (many) reasons why things aren't automatically set to run at boot up, you need to examine the package documentation to find out why.

---

### Post by drummer on 2006-01-23
You can add it to "System-Preferences-Sessions-Startup Programs", put in beagled as the command and give it an order of, say, 80.

---

### Post by kwaanens on 2006-01-23
OK, I actually figured it out by myself, but:
When trying beagled in console I get:

```
$ beagled
ketil@inspiron:~$
Unhandled Exception: GLib.GException: Unknown error
in <0x00187> Evolution.Cal:GetChanges (string,Evolution.CalComponent[]&,Evolution.CalComponent[]&,string[]&)
in <0x00121> Beagle.Daemon.EvolutionDataServerQueryable.CalContainer:IndexChanges ()
in <0x001c8> Beagle.Daemon.EvolutionDataServerQueryable.SourcesHandler:IndexSourceGroup (Evolution.SourceGroup,bool)
in <0x001c6> Beagle.Daemon.EvolutionDataServerQueryable.SourcesHandler:.ctor (string,System.Type,Beagle.Daemon.EvolutionDataServerQueryable.EvolutionDataServerQueryable,string)
in <0x000fc> Beagle.Daemon.EvolutionDataServerQueryable.EvolutionDataServerQueryable:Start ()
in <0x00016> Beagle.Daemon.Queryable:Start ()
in <0x000e9> Beagle.Daemon.QueryDriver:Start ()
in <0x0012e> Beagle.Daemon.BeagleDaemon:StartupProcess ()
in <0x00048> (wrapper delegate-invoke) System.MulticastDelegate:invoke_bool ()
in <0x0002a> IdleProxy:Handler ()
in <0x00036> (wrapper native-to-managed) IdleProxy:Handler ()
in (unmanaged) 0xb7f6b74f
in <0x00004> (wrapper managed-to-native) Gtk.Application:gtk_main ()
in <0x00007> Gtk.Application:Run ()
in <0x0057b> Beagle.Daemon.BeagleDaemon:Main (string[])

```

Consequently:

```
$ beagle-status

Could not connect to the daemon.
```

Ideas?

- Ketil

---

### Post by dcstar on 2006-01-23
[QUOTE=kwaanens]OK, I actually figured it out by myself, but:
When trying beagled in console I get:
.......
Consequently:

```
$ beagle-status

Could not connect to the daemon.
```

Ideas?

- Ketil[/QUOTE]
Possibly it only runs as root, try it with "sudo" in front of the command.

---

### Post by kwaanens on 2006-01-23
```
$ sudo beagled
Password:
You can not run beagle as root.
Beagle is designed to be run from your own user account.
Beagle Daemon exited with errors.  See ~/.beagle/Log/current-Beagle for more details.
```

- Ketil

---

### Post by thermans on 2006-01-23
Try running "beagled --foreground --debug" from the console and see what it says.  Looks like it might not be installed correctly....

---

### Post by kaamos on 2006-01-23
[QUOTE=dcstar]Possibly it only runs as root, try it with "sudo" in front of the command.[/QUOTE]
->
[quote=http://www.beaglewiki.org/FAQ]**Does Beagle require root to run?**

No. In fact, since 0.0.10 the Beagle Daemon will refuse to run as root. The daemon is designed to handle per-user indexing. This is why it's run as the user, and why it only indexes home directories. (You can, however, add other directories outside of the home directory if you wish) [/quote]

---

### Post by kwaanens on 2006-01-24
[QUOTE=thermans]Try running "beagled --foreground --debug" from the console and see what it says. Looks like it might not be installed correctly....[/QUOTE]

```
$ beagled --foreground --debug
INFO: Starting Beagle Daemon (version 0.1.1)
DEBUG: Command Line: /usr/lib/beagle/BeagleDaemon.exe --foreground --debug
WARN: Extended attributes are not supported on this filesystem.  Many search backends will not be available
DEBUG: Starting main loop
DEBUG: Starting messaging server
DEBUG: Starting QueryDriver
DEBUG: Found index helper at /usr/lib/beagle/beagled-index-helper
DEBUG: Found 1 types in EvolutionDataServer, Version=0.0.0.0, Culture=neutral
INFO: KMail folders not found. Will keep trying
DEBUG: Starting Inotify Backend
DEBUG: Loading Beagle.Util.Conf+IndexingConfig from indexing.xml
DEBUG: Loading Beagle.Util.Conf+DaemonConfig from daemon.xml
DEBUG: Loading Beagle.Util.Conf+SearchingConfig from searching.xml
DEBUG: Loading Beagle.Util.Conf+NetworkingConfig from networking.xml
DEBUG: Loading Beagle.Util.Conf+WebServicesConfig from webservices.xml
DEBUG: Found 12 types in BeagleDaemonLib, Version=1.4.3.3, Culture=neutral
DEBUG: Found 0 user-configured static queryables
INFO: Scanning addressbooks and calendars
DEBUG: Getting addressbook changes for file:///home/ketil/.evolution/addressbook/local/system
DEBUG: Addressbook file:///home/ketil/.evolution/addressbook/local/system: 0 added, 0 changed, 0 removed
DEBUG: Getting addressbook changes for file:///home/ketil/.evolution/addressbook/local/1134071997.9578.1@inspiron.ketil
DEBUG: Addressbook file:///home/ketil/.evolution/addressbook/local/1134071997.9578.1@inspiron.ketil: 0 added, 0 changed, 0 removed
DEBUG: Getting calendar changes for file:///home/ketil/.evolution/calendar/local/system

Unhandled Exception: GLib.GException: Ukjent feil
in <0x00187> Evolution.Cal:GetChanges (string,Evolution.CalComponent[]&,Evolution.CalComponent[]&,string[]&)
in <0x00121> Beagle.Daemon.EvolutionDataServerQueryable.CalContainer:IndexChanges ()
in <0x001c8> Beagle.Daemon.EvolutionDataServerQueryable.SourcesHandler:IndexSourceGroup (Evolution.SourceGroup,bool)
in <0x001c6> Beagle.Daemon.EvolutionDataServerQueryable.SourcesHandler:.ctor (string,System.Type,Beagle.Daemon.EvolutionDataServerQueryable.EvolutionDataServerQueryable,string)
in <0x000fc> Beagle.Daemon.EvolutionDataServerQueryable.EvolutionDataServerQueryable:Start ()
in <0x00016> Beagle.Daemon.Queryable:Start ()
in <0x000e9> Beagle.Daemon.QueryDriver:Start ()
in <0x0012e> Beagle.Daemon.BeagleDaemon:StartupProcess ()
in <0x00048> (wrapper delegate-invoke) System.MulticastDelegate:invoke_bool ()
in <0x0002a> IdleProxy:Handler ()
in <0x00036> (wrapper native-to-managed) IdleProxy:Handler ()
in (unmanaged) 0xb7e9f74f
in <0x00004> (wrapper managed-to-native) Gtk.Application:gtk_main ()
in <0x00007> Gtk.Application:Run ()
in <0x0057b> Beagle.Daemon.BeagleDaemon:Main (string[])


```

---

### Post by Michael Steinberg on 2006-01-24
As far as I know, Beagle isn't fully supported in the Ubuntu kernel; it will index some but not all of the files. To make it index everything you have to do some kernel customizing and some other work. Check out the Beagle site for more info.

I haven't messed with the kernel myself but still find Beagle useful. It runs in the background; I'd probably see the exception messages if I bothered but I'm resigned to the fact that I'm too lazy to make it do more. Or maybe too cowardly.

---

### Post by kwaanens on 2006-01-24
Beagle is not that important. I see that the 2.6.15 kernel has some improvements regarding Beagle, so I guess I'll wait for Dapper.

- Ketil

---

### Post by omegamike on 2006-01-24
Just out of curiousity, did you make sure to enable indexing in your fstab file?

---

### Post by RAOF on 2006-01-24
[QUOTE=omegamike]Just out of curiousity, did you make sure to enable indexing in your fstab file?[/QUOTE]
Where "enable indexing in your fstab file" means adding the "user_xattr" option to your mount options.  Meaning your fstab lines would look something like:
```
# /etc/fstab: static file system information.
#
# <file system>                         <mount point>   <type>          <options>                       <dump>  <pass>
proc                                    /proc           proc            defaults                        0       0
/dev/mapper/storage-dapper--root        /               reiserfs        notail,user_xattr               0       1
/dev/sda2                               /boot           ext3            defaults                        0       2
/dev/mapper/storage-shared--home        /home           reiserfs        notail,user_xattr               0       2
/dev/sda4                               /media          reiserfs        notail,user_xattr               0       2
/dev/mapper/storage-shared--swap        none            swap            sw                              0       0
/dev/hda                                /media/cdrom0   udf,iso9660     user,noauto                     0       0
#I 'aint got no floppy drive now :)
#/dev/fd0                               /media/floppy0  auto            rw,user,noauto                  0       0
#And now, for the Windows Drive (TM)
/dev/sda1                               /media/WinXP    ntfs            defaults,fmask=0333,dmask=0000  0       0

```
although your actual device names will probably be different.  The important part is the ,user_xattr bit :)

However, beagle should run (but more slowly) without extended attribute support (which is enabled in the Breezy kernel anyway).  Looking at the actual error message, it looks like the evolution backend is playing up.  You could try starting beagled without the evolution backend.  I believe the command is 
```
beagled --deny-backend evolution-data-server
```but it's been a while, and beagle seems to be broken on Dapper at the moment.  Try beagled --help, too - it'll list all the command line options, including one that lists all the possible backends.  If disabling the evolution one doesn't work, try disabling others.

---

