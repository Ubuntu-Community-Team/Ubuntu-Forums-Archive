---
title: "Lost Panels/main menu in Gnome"
date: 2009-12-23
forum: General Help
---

### Post by holmrun on 2009-12-23
Hello all... Running 9.10 and seem to have lost my panels in gnome... The only thing I have on the desktop are my 3 icons and then the background. If I right click I get options to create a folder/file or launcher but launcher doesn't work. I can change sessions to xfce and everything seems to work fine. If I ctrl-alt-f2 and try to run gnome-panel I get: error loading shared libraries: libavahi-glib.so.1: cannot open shared object file: no such file or directory


I have reset all gnome prefs to no avail, made sure the system is fully up to date and removed AWN just to be safe. I also tried to reinstall the desktop to no avail - says it is already the latest version. Any help would be appreciated.

---

### Post by oakgrove on 2009-12-23
$ sudo apt-get install libavahi-glib1

That's the package that contains libavahi-glib.so.1

See what that does for you.

---

### Post by holmrun on 2009-12-23
Thanks Oakgrove... I just ran that and it says it is already the newest version.

---

### Post by oakgrove on 2009-12-23
That's weird.

Maybe pull up a terminal and:
```

$ strace -o file.txt gnome-panel

```
then do ```

$ cat file.txt | grep -i libavahi

```
It should say something like ```
open("/usr/lib/libavahi-glib.so.1", O_RDONLY) = 3
```
If the /usr/lib/libavahi-glib.so.1 part isn't right, it may be looking in a non-standard location.  Then we can go from there.

---

### Post by holmrun on 2009-12-23
```
$ cat file.txt | grep -i libavahi
open("/lib/tls/i686/sse2/cmov/libavahi-glib.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/sse2/libavahi-glib.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libavahi-glib.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/libavahi-glib.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/lib/tls/sse2/cmov/libavahi-glib.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/lib/tls/sse2/libavahi-glib.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/lib/tls/cmov/libavahi-glib.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/lib/tls/libavahi-glib.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/lib/i686/sse2/cmov/libavahi-glib.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/lib/i686/sse2/libavahi-glib.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/lib/i686/cmov/libavahi-glib.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/lib/i686/libavahi-glib.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/lib/sse2/cmov/libavahi-glib.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/lib/sse2/libavahi-glib.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/lib/cmov/libavahi-glib.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/lib/libavahi-glib.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/tls/i686/sse2/cmov/libavahi-glib.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/tls/i686/sse2/libavahi-glib.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/tls/i686/cmov/libavahi-glib.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/tls/i686/libavahi-glib.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/tls/sse2/cmov/libavahi-glib.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/tls/sse2/libavahi-glib.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/tls/cmov/libavahi-glib.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/tls/libavahi-glib.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/i686/sse2/cmov/libavahi-glib.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/i686/sse2/libavahi-glib.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/i686/cmov/libavahi-glib.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/i686/libavahi-glib.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/sse2/cmov/libavahi-glib.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/sse2/libavahi-glib.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/cmov/libavahi-glib.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/libavahi-glib.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/lib/i486-linux-gnu/tls/i686/sse2/cmov/libavahi-glib.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/lib/i486-linux-gnu/tls/i686/sse2/libavahi-glib.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/lib/i486-linux-gnu/tls/i686/cmov/libavahi-glib.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/lib/i486-linux-gnu/tls/i686/libavahi-glib.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/lib/i486-linux-gnu/tls/sse2/cmov/libavahi-glib.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/lib/i486-linux-gnu/tls/sse2/libavahi-glib.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/lib/i486-linux-gnu/tls/cmov/libavahi-glib.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/lib/i486-linux-gnu/tls/libavahi-glib.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/lib/i486-linux-gnu/i686/sse2/cmov/libavahi-glib.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/lib/i486-linux-gnu/i686/sse2/libavahi-glib.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/lib/i486-linux-gnu/i686/cmov/libavahi-glib.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/lib/i486-linux-gnu/i686/libavahi-glib.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/lib/i486-linux-gnu/sse2/cmov/libavahi-glib.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/lib/i486-linux-gnu/sse2/libavahi-glib.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/lib/i486-linux-gnu/cmov/libavahi-glib.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/lib/i486-linux-gnu/libavahi-glib.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/tls/i686/sse2/cmov/libavahi-glib.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/tls/i686/sse2/libavahi-glib.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/tls/i686/cmov/libavahi-glib.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/tls/i686/libavahi-glib.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/tls/sse2/cmov/libavahi-glib.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/tls/sse2/libavahi-glib.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/tls/cmov/libavahi-glib.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/tls/libavahi-glib.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/i686/sse2/cmov/libavahi-glib.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/i686/sse2/libavahi-glib.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/i686/cmov/libavahi-glib.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/i686/libavahi-glib.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/sse2/cmov/libavahi-glib.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/sse2/libavahi-glib.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/cmov/libavahi-glib.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/libavahi-glib.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
writev(2, [{"gnome-panel", 11}, {": ", 2}, {"error while loading shared libra"..., 36}, {": ", 2}, {"libavahi-glib.so.1", 18}, {": ", 2}, {"cannot open shared object file", 30}, {": ", 2}, {"No such file or directory", 25}, {"\n", 1}], 10) = 129

```

I hope that's the output you were looking for? I wasn't expecting it to be so long. Thanks again Oakgrove.

---

### Post by oakgrove on 2009-12-23
The package libavahi-glib1 I mentioned earlier puts the file libavahi-glib.so.1 into your /usr/lib directory.  Strangely even though your system thinks the package is installed, it doesn't appear to have actually deposited the file.  You have a couple of options.  The easiest is probably to download the package manually from [http://mirrors.kernel.org/ubuntu/pool/main/a/avahi/libavahi-glib1_0.6.25-1ubuntu5_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/a/avahi/libavahi-glib1_0.6.25-1ubuntu5_i386.deb).  Then when you have it downloaded, right click on it and select "extract here"  Then go into the libavahi-glib1_0.6.25-1ubuntu5_i386 directory that it makes and right click on data.tar.gz file that you see in there and extract it.  It'll make a usr directory, go into it and the lib directory inside of that.  At this point, you should see the libavahi-glib.so.1 file you need.  Use the terminal and as root, copy that file to /usr/lib and try to start gnome-panel again.  If anything is unclear, just let me know.  The other way is try to completely remove the libavahi-glib package and reinstall it and see if it works.

This is all assuming you are using the 32 bit version of Karmic.  If 64 bit, proceed accordingly.

---

### Post by holmrun on 2009-12-23
I really thought that would work... now it is getting stuck on libavahi-common.so.3 with the same no such file or directory message... Should we remove the package and reinstall?

---

### Post by oakgrove on 2009-12-23
You've got a pretty serious problem going on there.  To get you on your feet, we can just manually add the files one at a time as it says you need them until it finally works but, I would suggest trying to figure out what the problem really is.

[http://mirrors.kernel.org/ubuntu/pool/main/a/avahi/libavahi-common3_0.6.25-1ubuntu5_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/a/avahi/libavahi-common3_0.6.25-1ubuntu5_i386.deb) is where you will find libavahi-common.so.3.

When you get it downloaded, put the libavahi-common.so.3 into your /usr/lib directory just like before and see if it works.  If not, let me know.

---

### Post by holmrun on 2009-12-23
oh what fun....

Now hung at libavahi-client.so.3... I hate when this stuff happens after the machine was off for a week and not even used. Arrgh. Thanks again Oakgrove


Where are you looking to find these files? Is there a repository I can use to just look for them and download them as they come up? (I'm not sure how many there are so I was just trying to save both of us a headache if possible)

---

### Post by oakgrove on 2009-12-23
```

$ sudo apt-get install apt-file
$ sudo apt-file update
$ apt-file search libavahi-client.so.3

```
It'll tell you what package the file is in on the left hand side before the colon.  With the package name in hand, go to [http://packages.ubuntu.com/karmic/libavahi-common3](http://packages.ubuntu.com/karmic/libavahi-common3) and paste the package name into the search box in the upper right hand corner then just download whatever pops up.  This is a great thing for finding missing libraries and stuff when you want to compile your own software too.

And no problem at all on the help.

---

### Post by holmrun on 2009-12-23
EXCELLENT! That was the last file it needed apparently, but I feel I've learned a lot nonetheless... I am back in Gnome and aside from having to reconfigure the panels (and general appearance of gnome) back to the way I had them - everything is working again. Thanks again Oakgrove, you've been a tremendous help!

---

### Post by oakgrove on 2009-12-23
No problem at all.  My pleasure.

---

