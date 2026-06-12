---
title: "gksudo nautilus does nothing after lucid upgrade"
date: 2010-05-20
forum: General Help
---

### Post by afrodeity on 2010-05-20
After recent Lucid upgrade, gksudo nautilus does nothing.

```
$ gksudo nautilus
Initializing nautilus-open-terminal extension
Initializing nautilus-image-converter extension
Initializing nautilus-gdu extension
```

Expecting a nautilus to come flying at me, but nothing.

If I click on an icon, the desktop reloads.

Sometimes I get a small window like this:

[http://www.flickr.com/photos/14887361@N05/4624055717/](http://www.flickr.com/photos/14887361@N05/4624055717/)

---

### Post by kaibob on 2010-05-20
I tried that command, and it worked fine for me. I wonder if it has something to do with one of the extensions.

---

### Post by Ozymandias_117 on 2010-05-20
Maybe you should try ```
sudo aptitude reinstall nautilus
```

---

### Post by theozzlives on 2010-05-20
```
gksu nautilus
```
works on the CLI but ALT+F2 don't bring up a run dialog.

---

### Post by dcstar on 2010-05-20
There is no need to run that command if you install the gksu extension for Nautilus.

---

### Post by theozzlives on 2010-05-20
> **dcstar said:**
> There is no need to run that command if you install the gksu extension for Nautilus.

I'm not sure that should've been shared, kinda like telling people how to log on as root.

---

### Post by jerome1232 on 2010-05-20
Adding a menu item that allows you to open a file as root is a huge difference from logging in as root.

If anything that extension is preferable to running nautilus as root.

---

### Post by afrodeity on 2010-05-21
```
sudo aptitude reinstall nautilus
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
The following packages will be REINSTALLED:
  nautilus 
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 4 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
E: I wasn't able to locate file for the nautilus package. This might mean you need to manually fix this package.
Writing extended state information... Done
E: I wasn't able to locate file for the nautilus package. This might mean you need to manually fix this package.
E: Internal error: couldn't generate list of packages to download

```

---

### Post by afrodeity on 2010-05-22
According to gdb (the gnome debugger) nautilus is seg faulting:

```

Program received signal SIGSEGV, Segmentation fault.
0x00ed1935 in gtk_range_set_value () from /usr/lib/libgtk-x11-2.0.so.0
(gdb) backtrace full
#0  0x00ed1935 in gtk_range_set_value () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
Cannot access memory at address 0xbf940bb0
(gdb) info registers
eax            0x9e7c400	166183936
ecx            0x0	0
edx            0x0	0
ebx            0x1123ff4	17973236
esp            0xbf940bb0	0xbf940bb0
ebp            0xbf940bd8	0xbf940bd8
esi            0xfdf	4063
edi            0x0	0
eip            0xed1935	0xed1935 <gtk_range_set_value+37>
eflags         0x210202	[ IF RF ID ]
cs             0x73	115
ss             0x7b	123
ds             0x7b	123
es             0x7b	123
fs             0x0	0
gs             0x33	51
(gdb) x/16i $pc
=> 0xed1935 <gtk_range_set_value+37>:	Cannot access memory at address 0xed1935
(gdb) thread apply all backtrace
Cannot find new threads: generic error
(gdb) quit
A debugging session is active.

```

Valgrind on the other hand, reports a memory leak

---

### Post by afrodeity on 2010-05-23
[https://bugs.edge.launchpad.net/ubuntu/+source/nautilus/+bug/413152](https://bugs.edge.launchpad.net/ubuntu/+source/nautilus/+bug/413152)

A[ full backtrace]("http://paste.ubuntu.com/438481/")

---

### Post by afrodeity on 2010-06-07
[http://ubuntuforums.org/showthread.php?p=9424292#post9424292](http://ubuntuforums.org/showthread.php?p=9424292#post9424292)

I also installed nautilus-gksu which was uninstalled for some reason.

---

### Post by afrodeity on 2010-06-28
> **afrodeity said:**
> [http://ubuntuforums.org/showthread.php?p=9424292#post9424292](http://ubuntuforums.org/showthread.php?p=9424292#post9424292)

I also installed nautilus-gksu which was uninstalled for some reason.

[http://ubuntuforums.org/showthread.php?t=1503801&page=3](http://ubuntuforums.org/showthread.php?t=1503801&page=3)

---

### Post by DeathRabbit on 2010-08-23
I was having this issue on a box at work and the nautilus reinstall someone suggested a few posts back fixed it. Strangely, though, this was a direct installation of lucid, not an upgrade from karmic. It would seem like something is buggered in the lucid install package. Oh well, not a huge deal I guess, but the root level file browser is a guilty pleasure.

---

### Post by mfdc1969 on 2010-08-23
I have tried all the posts with solutions referenced here and still can not get gksudo nautilus to work. I do now get an error message though:

```

~$ gksu nautilus
Initializing nautilus-gdu extension
** Message: Initializing gksu extension...**
Eel:ERROR:eel-preferences.c:117:preferences_gconf_value_get_string: assertion failed: (value->type == GCONF_VALUE_STRING)

~$ sudo killall -9 nautilus && gksu nautilus
Initializing nautilus-gdu extension
** Message: Initializing gksu extension...**
Eel:ERROR:eel-preferences.c:117:preferences_gconf_value_get_string: assertion failed: (value->type == GCONF_VALUE_STRING)
```

I searched Google for answers and [found this which worked]("http://us.generation-nt.com/answer/nautilus-error-help-199596141.html"):

The solution was:
sudo mv /root/.gconf /root/.gconf-old

---

