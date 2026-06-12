---
title: "Banshee will only run with gksudo"
date: 2010-02-15
forum: General Help
---

### Post by JohnMac on 2010-02-15
I love Banshee (1.5.3). A bit bleeding edge, but when I tried to reinstall it I find I can only run it with gksudo.
Can anyone help here.

My system:

Karmic 32 bit
AMD Athlon 64 X2 Processor 5200+
Chipset Geforce 6100
Drive 160G
RAM 2G

---

### Post by saif_held on 2010-02-15
You might wanna try removing it and then install it all the way again.

---

### Post by JohnMac on 2010-02-16
Ok Thanks for that. I had to go back a version, from 1.5.3 to 1.5.1 to get it to work, I work out why later.

---

### Post by JohnMac on 2010-02-25
Oops it happened again. When I did I did the latest round of updates on "update manager" it broke again.

Anyone?

---

### Post by JohnMac on 2010-04-04
I have uninstalled Banshee 1.6 and reinstalled it and this is what I get when I run it from terminal:


john@john-desktop:~$ banshee
[Info  13:01:37.768] Running Banshee 1.6.0: [Ubuntu 9.10 51066b4 (linux-gnu, i486) @ 2010-04-02 16:10:03 UTC]

(/usr/lib/banshee-1/Banshee.exe:2819): GLib-WARNING **: g_set_prgname() called multiple times
[Info  13:01:41.362] All services are started 1.672092s
[Info  13:01:44.742] nereid Client Started

Unhandled Exception: System.ArgumentException: UNC pass should be of the form \\server\share.
  at System.IO.Path.InsecureGetFullPath (System.String path) [0x00000] 
  at System.IO.Path.GetFullPath (System.String path) [0x00000] 
  at Banshee.LibraryWatcher.IO.FileSystemWatcher.get_FullPath () [0x00000] 
  at (wrapper remoting-invoke-with-check) Banshee.LibraryWatcher.IO.FileSystemWatcher:get_FullPath ()
  at Banshee.LibraryWatcher.IO.InotifyWatcher.StartDispatching (Banshee.LibraryWatcher.IO.FileSystemWatcher fsw) [0x00000] 
  at Banshee.LibraryWatcher.IO.FileSystemWatcher.Start () [0x00000] 
  at Banshee.LibraryWatcher.IO.FileSystemWatcher.set_EnableRaisingEvents (Boolean value) [0x00000] 
  at (wrapper remoting-invoke-with-check) Banshee.LibraryWatcher.IO.FileSystemWatcher:set_EnableRaisingEvents (bool)
  at Banshee.LibraryWatcher.FileSystemWatcherProxy.set_EnableRaisingEvents (Boolean value) [0x00000] 
  at Banshee.LibraryWatcher.SourceWatcher.Watch () [0x00000] 
john@john-desktop:~$

---

### Post by 3rdalbum on 2010-04-05
I would remove Banshee's preferences files; they might be owned by root (which happens if you have ever used 'sudo banshee').

Preferences files are stored in hidden folders in your home directory - that is, folders beginning with a fullstop.

---

### Post by Nevyn on 2010-04-05
Just to make sure: your home folder isn't full or nearly full is it? It happened to me onece (I had about 1.5Gb free) and that caused a few applications that stored preferences-files there to go haywire.

---

### Post by JohnMac on 2010-04-14
Thanks for getting back to me. No my home folder is not full, I only have 2 partitions on this drive. There is a bug report (450166) on Launchpad which is similar to my issue, but is yet unresolved.
What is a little strange is that all the files in my Music have been made READ ONLY. For some reason I haven't been able to change the permission of the whole folder using gksudo nautilus. I am in the process of changing each individual file (over 600). 

Soon I am going to do a clean install on Lucid, that will fix it.

---

### Post by warfacegod on 2010-04-14
Try right clicking your Apps. Places, System Menu and selecting Edit menus. Find the Banshee entry and double click it for Properties. In that window, add gksudo to the beginning of the Command.

Example:

```
gksudo banshee
```

Note the space between the two words.

---

### Post by JohnMac on 2010-04-18
No, this won't work for me, Banshee will not run from the panel. I even tried purging the program and configuration. What is odd is the the command file it is: "banshee-1 --redirect-log --device-activate-play=%u" Maybe this is incorrect?

---

### Post by warfacegod on 2010-04-18
> **JohnMac said:**
> No, this won't work for me, Banshee will not run from the panel. I even tried purging the program and configuration. What is odd is the the command file it is: "banshee-1 --redirect-log --device-activate-play=%u" Maybe this is incorrect?

Try:

```
gksudo banshee-1 --redirect-log --device-activate-play=%u
```

---

