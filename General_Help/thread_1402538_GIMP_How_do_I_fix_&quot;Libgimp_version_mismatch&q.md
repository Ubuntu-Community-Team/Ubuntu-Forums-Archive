---
title: "GIMP: How do I fix &quot;Libgimp version mismatch&quot; error?"
date: 2010-02-09
forum: General Help
---

### Post by lightnb on 2010-02-09
I've made several attempts to install GIMP 2.7 (by compiling) to get layer group functionality, but the results were too buggy and I'd like to go back to 2.6. I installed gimp 2.6 again via apt-get, but it won't load, giving the error:

```

Libgimp version mismatch!

The GIMP binary cannot run with a libgimp version
other than its own. This is GIMP 2.6.6, but the
libgimp version is 2.7.0.

Maybe you have GIMP versions in both /usr and /usr/local ?

```

How do I fix this so that gimp 2.6 will run again?


Thanks!

---

### Post by gmargo on 2010-02-09
Did you remove all the gimp-2.7 stuff under /usr/local?  Including /usr/local/lib/libgimp*?

---

### Post by lightnb on 2010-02-09
/usr/local/lib$ ls
python2.4  python2.5  python2.6  site_ruby

/usr/local/bin is empty

/usr/local/etc is empty

---

### Post by gmargo on 2010-02-09
The perhaps the compile attempt overwrote the libraries in /usr/lib?

Your profile says Jaunty, so here is some info on libgimp2.0 for Jaunty.  I'll bet you'll see, under /usr/lib, symbolic links pointing to the wrong shared library.  This is what you should see for an up-to-date Jaunty system:

```

$ dpkg -l libgimp2.0
||/ Name                  Version               Description
+++-=====================-=====================-==========================================================
ii  libgimp2.0            2.6.6-0ubuntu1.1      Libraries for the GNU Image Manipulation Program

$ ls -l /usr/lib/libgimp*
lrwxrwxrwx 1 root root      22 Jan 19 12:44 /usr/lib/libgimp-2.0.so.0 -> libgimp-2.0.so.0.600.6
-rw-r--r-- 1 root root  206868 Jan  5 08:22 /usr/lib/libgimp-2.0.so.0.600.6
lrwxrwxrwx 1 root root      26 Jan 19 12:44 /usr/lib/libgimpbase-2.0.so.0 -> libgimpbase-2.0.so.0.600.6
-rw-r--r-- 1 root root   79636 Jan  5 08:22 /usr/lib/libgimpbase-2.0.so.0.600.6
lrwxrwxrwx 1 root root      27 Jan 19 12:44 /usr/lib/libgimpcolor-2.0.so.0 -> libgimpcolor-2.0.so.0.600.6
-rw-r--r-- 1 root root   42420 Jan  5 08:22 /usr/lib/libgimpcolor-2.0.so.0.600.6
lrwxrwxrwx 1 root root      28 Jan 19 12:44 /usr/lib/libgimpconfig-2.0.so.0 -> libgimpconfig-2.0.so.0.600.6
-rw-r--r-- 1 root root   55316 Jan  5 08:22 /usr/lib/libgimpconfig-2.0.so.0.600.6
lrwxrwxrwx 1 root root      26 Jan 19 12:44 /usr/lib/libgimpmath-2.0.so.0 -> libgimpmath-2.0.so.0.600.6
-rw-r--r-- 1 root root   17764 Jan  5 08:22 /usr/lib/libgimpmath-2.0.so.0.600.6
lrwxrwxrwx 1 root root      28 Jan 19 12:44 /usr/lib/libgimpmodule-2.0.so.0 -> libgimpmodule-2.0.so.0.600.6
-rw-r--r-- 1 root root   13772 Jan  5 08:22 /usr/lib/libgimpmodule-2.0.so.0.600.6
lrwxrwxrwx 1 root root      27 Jan 19 12:44 /usr/lib/libgimpthumb-2.0.so.0 -> libgimpthumb-2.0.so.0.600.6
-rw-r--r-- 1 root root   30320 Jan  5 08:22 /usr/lib/libgimpthumb-2.0.so.0.600.6
lrwxrwxrwx 1 root root      24 Jan 19 12:44 /usr/lib/libgimpui-2.0.so.0 -> libgimpui-2.0.so.0.600.6
-rw-r--r-- 1 root root  117920 Jan  5 08:22 /usr/lib/libgimpui-2.0.so.0.600.6
lrwxrwxrwx 1 root root      29 Jan 19 12:44 /usr/lib/libgimpwidgets-2.0.so.0 -> libgimpwidgets-2.0.so.0.600.6
-rw-r--r-- 1 root root 1143716 Jan  5 08:22 /usr/lib/libgimpwidgets-2.0.so.0.600.6


```

---

### Post by lightnb on 2010-02-09
This is what I got... it says version 2.6.6...

```
$ dpkg -l libgimp2.0
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name             Version          Description
+++-================-================-================================================
ii  libgimp2.0       2.6.6-0ubuntu1.1 Libraries for the GNU Image Manipulation Program
```


There's a ton of results for the second one:
```

rahl@SwiftFishII:/usr/lib$ ls -l /usr/lib/libgimp*
-rwxr-xr-x 1 root root    1145 2010-02-09 04:37 /usr/lib/libgimp-2.0.la
lrwxrwxrwx 1 root root      22 2010-02-09 04:37 /usr/lib/libgimp-2.0.so -> libgimp-2.0.so.0.700.0
lrwxrwxrwx 1 root root      22 2010-02-09 07:55 /usr/lib/libgimp-2.0.so.0 -> libgimp-2.0.so.0.700.0
-rw-r--r-- 1 root root  241096 2010-01-05 11:54 /usr/lib/libgimp-2.0.so.0.600.6
-rwxr-xr-x 1 root root  865326 2010-02-09 04:37 /usr/lib/libgimp-2.0.so.0.700.0
-rwxr-xr-x 1 root root    1050 2010-02-09 04:37 /usr/lib/libgimpbase-2.0.la
lrwxrwxrwx 1 root root      26 2010-02-09 04:37 /usr/lib/libgimpbase-2.0.so -> libgimpbase-2.0.so.0.700.0
lrwxrwxrwx 1 root root      26 2010-02-09 07:55 /usr/lib/libgimpbase-2.0.so.0 -> libgimpbase-2.0.so.0.700.0
-rw-r--r-- 1 root root   97248 2010-01-05 11:54 /usr/lib/libgimpbase-2.0.so.0.600.6
-rwxr-xr-x 1 root root  284764 2010-02-09 04:37 /usr/lib/libgimpbase-2.0.so.0.700.0
-rwxr-xr-x 1 root root    1060 2010-02-09 04:37 /usr/lib/libgimpcolor-2.0.la
lrwxrwxrwx 1 root root      27 2010-02-09 04:37 /usr/lib/libgimpcolor-2.0.so -> libgimpcolor-2.0.so.0.700.0
lrwxrwxrwx 1 root root      27 2010-02-09 07:55 /usr/lib/libgimpcolor-2.0.so.0 -> libgimpcolor-2.0.so.0.700.0
-rw-r--r-- 1 root root   51496 2010-01-05 11:54 /usr/lib/libgimpcolor-2.0.so.0.600.6
-rwxr-xr-x 1 root root  139099 2010-02-09 04:37 /usr/lib/libgimpcolor-2.0.so.0.700.0
-rwxr-xr-x 1 root root    1151 2010-02-09 04:37 /usr/lib/libgimpconfig-2.0.la
lrwxrwxrwx 1 root root      28 2010-02-09 04:37 /usr/lib/libgimpconfig-2.0.so -> libgimpconfig-2.0.so.0.700.0
lrwxrwxrwx 1 root root      28 2010-02-09 07:55 /usr/lib/libgimpconfig-2.0.so.0 -> libgimpconfig-2.0.so.0.700.0
-rw-r--r-- 1 root root   65000 2010-01-05 11:54 /usr/lib/libgimpconfig-2.0.so.0.600.6
-rwxr-xr-x 1 root root  198224 2010-02-09 04:37 /usr/lib/libgimpconfig-2.0.so.0.700.0
-rwxr-xr-x 1 root root    1054 2010-02-09 04:37 /usr/lib/libgimpmath-2.0.la
lrwxrwxrwx 1 root root      26 2010-02-09 04:37 /usr/lib/libgimpmath-2.0.so -> libgimpmath-2.0.so.0.700.0
lrwxrwxrwx 1 root root      26 2010-02-09 07:55 /usr/lib/libgimpmath-2.0.so.0 -> libgimpmath-2.0.so.0.700.0
-rw-r--r-- 1 root root   22664 2010-01-05 11:54 /usr/lib/libgimpmath-2.0.so.0.600.6
-rwxr-xr-x 1 root root   55333 2010-02-09 04:37 /usr/lib/libgimpmath-2.0.so.0.700.0
-rwxr-xr-x 1 root root    1117 2010-02-09 04:37 /usr/lib/libgimpmodule-2.0.la
lrwxrwxrwx 1 root root      28 2010-02-09 04:37 /usr/lib/libgimpmodule-2.0.so -> libgimpmodule-2.0.so.0.700.0
lrwxrwxrwx 1 root root      28 2010-02-09 07:55 /usr/lib/libgimpmodule-2.0.so.0 -> libgimpmodule-2.0.so.0.700.0
-rw-r--r-- 1 root root   18776 2010-01-05 11:54 /usr/lib/libgimpmodule-2.0.so.0.600.6
-rwxr-xr-x 1 root root   53977 2010-02-09 04:37 /usr/lib/libgimpmodule-2.0.so.0.700.0
-rwxr-xr-x 1 root root    1117 2010-02-09 04:37 /usr/lib/libgimpthumb-2.0.la
lrwxrwxrwx 1 root root      27 2010-02-09 04:37 /usr/lib/libgimpthumb-2.0.so -> libgimpthumb-2.0.so.0.700.0
lrwxrwxrwx 1 root root      27 2010-02-09 07:55 /usr/lib/libgimpthumb-2.0.so.0 -> libgimpthumb-2.0.so.0.700.0
-rw-r--r-- 1 root root   39584 2010-01-05 11:54 /usr/lib/libgimpthumb-2.0.so.0.600.6
-rwxr-xr-x 1 root root  102218 2010-02-09 04:37 /usr/lib/libgimpthumb-2.0.so.0.700.0
-rwxr-xr-x 1 root root    1544 2010-02-09 04:37 /usr/lib/libgimpui-2.0.la
lrwxrwxrwx 1 root root      24 2010-02-09 04:37 /usr/lib/libgimpui-2.0.so -> libgimpui-2.0.so.0.700.0
lrwxrwxrwx 1 root root      24 2010-02-09 07:55 /usr/lib/libgimpui-2.0.so.0 -> libgimpui-2.0.so.0.700.0
-rw-r--r-- 1 root root  137224 2010-01-05 11:54 /usr/lib/libgimpui-2.0.so.0.600.6
-rwxr-xr-x 1 root root  691283 2010-02-09 04:37 /usr/lib/libgimpui-2.0.so.0.700.0
-rwxr-xr-x 1 root root    1489 2010-02-09 04:37 /usr/lib/libgimpwidgets-2.0.la
lrwxrwxrwx 1 root root      29 2010-02-09 04:37 /usr/lib/libgimpwidgets-2.0.so -> libgimpwidgets-2.0.so.0.700.0
lrwxrwxrwx 1 root root      29 2010-02-09 07:55 /usr/lib/libgimpwidgets-2.0.so.0 -> libgimpwidgets-2.0.so.0.700.0
-rw-r--r-- 1 root root 1213696 2010-01-05 11:54 /usr/lib/libgimpwidgets-2.0.so.0.600.6
-rwxr-xr-x 1 root root 2865462 2010-02-09 04:37 /usr/lib/libgimpwidgets-2.0.so.0.700.0

```

What should I do to repair it?

---

### Post by lightnb on 2010-02-09
Can I do:

```

sudo rm /usr/lib/libgimp*
sudo apt-get install gimp
```

Or will that make things worse?

---

### Post by gmargo on 2010-02-09
While it is possible to remove those ".700." files and use ldconfig to repair the symbolic links, I see other files there (libgimp*.la) that are from the compile attempt, plus there's probably files in /usr/include/gimp*. I think your best bet is to purge libgimp2.0 and libgimp2.0-dev, then remove any /usr/lib/libgimp* and /usr/include/gimp* leftovers, then reinstall.

And by "purge" I mean "aptitude purge libgimp2.0 libgimp2.0-dev"

---

### Post by lightnb on 2010-02-09
Ok, I purged libgimp2.0, libgimp2.0-dev and gimp, and removed the left over files. Then  reinstalled gimp using aptitude. The original error is gone, but I now get:

```
gimp: error while loading shared libraries: libgimpwidgets-2.0.so.0: cannot open shared object file: No such file or directory
```

...when attempting to start gimp from the command line. I guess something got purged and didn't get put back by the install?

---

### Post by gmargo on 2010-02-09
That file is in the libgimp2.0 package; it should have installed.  I purged and reinstalled gimp and libgmp2.0 myself (on Jaunty) and it works fine.  I'm at a loss.  Try running ldconfig on the command line?

---

### Post by lightnb on 2010-02-10
Ok,

Did:
```

reboot
sudo apt-get purge libgimp2.0
sudo ldconfig
reboot
sudo apt-get install gimp

```

And now it's moved on to a new error message. It's complaining that BABL is outdated, but I actually have a NEWER version installed.
```

BABL version too old!

GIMP requires BABL version 0.0.22 or later.
Installed BABL version is 0.1.0.

Somehow you or your software packager managed
to install GIMP with an older BABL version.

Please upgrade to BABL version 0.0.22 or later.

```

Since I have a more up to date version this should be working? Is there a way to ignore the BABL check?

---

### Post by lightnb on 2010-02-10
Finally got this working. I had to delete a bunch of library files and "upgrade" to a previous version. Thanks for your help!

---

