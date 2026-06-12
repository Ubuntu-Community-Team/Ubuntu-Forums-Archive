---
title: "Running Lucid but need libstdc++.so.5 for 3rd party software install"
date: 2010-06-23
forum: General Help
---

### Post by apesa on 2010-06-23
Greetings, I am on a fresh install of 32 bit Lucid as of 4 days ago. I have no problems with Lucid, but I do have a problem installing a 3rd party DB/Application. I am trying to get SAP MaxDB installed using a download from SAP. During the initial phase of the install it is failing citing a missing lidstdc++.so.5. I know I have libstdc++.so.6 and would have thought it would notice a higher version than needed, but it doesn't. 

I am looking for options that would allow me to either turn back to libstdc++.so.5 or fool the install into going with version 6.

TIA, 
Pat

---

### Post by mc4man on 2010-06-23
see here for 2 things to try (I'd try installing   libstdc++.so.5 first and see
[http://ubuntuforums.org/showthread.php?t=1406616](http://ubuntuforums.org/showthread.php?t=1406616)

---

### Post by apesa on 2010-06-24
Thanks, that worked, but it revealed a couple other dependencies that I need to fix. libtiff3 is my current problem. I can't seem to find anything but libtiff4 all the way back to Heron.

Thanks again for the link

Pat

---

### Post by Zill on 2010-06-24
As suggested in the link supplied by mc4man, I would add symbolic links to link "missing" files to the actual versions installed on your PC.

Use the "locate" command (without version number) to show the installed file eg.
```
locate libtiff
```
Then create a symbolic link in the same directory eg.
```
sudo ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3
```
Obviously, change this as required to use the correct filenames and paths for your PC and application.

Keep testing your app each time, adding new symbolic links as necessary until the app runs correctly.

Note that this method is *likely* to work, but may not if some particular feature of a specific library version is necessary.  However, it is worth a try. :-)

---

### Post by apesa on 2010-06-24
Thanks Zill,
I am doing just that, but I am discovering that even libtiff3 has a dependency that I have to link.. Digging through it all now. I find it hard to believe that MaxDB has such obsolete dependencies. Especially the latest release. Linux has been the last OS to gain updated support at SAP unless you're running RHEL.

Thanks for all the support,
Pat

---

### Post by Zill on 2010-06-24
> **apesa said:**
> Thanks Zill,
I am doing just that, but I am discovering that even libtiff3 has a dependency that I have to link...
Symbolic links only really help by pointing to different versions of the same lib file etc.

If actual dependent programs are missing then I suggest you will have to install these as required.  As long as these are packages for your particular Ubuntu version and are installed via apt-get, aptitude or synaptic they should be OK.  Just keep an eye on the installations to make sure nothing you actually want is uninstalled!

You may still need to tinker with symlinks to make it all talk to your app though. :-(

---

