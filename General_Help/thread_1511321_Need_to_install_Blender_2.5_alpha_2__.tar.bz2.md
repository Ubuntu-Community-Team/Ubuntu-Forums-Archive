---
title: "Need to install Blender 2.5 alpha 2  .tar.bz2"
date: 2010-06-16
forum: General Help
---

### Post by petellgra on 2010-06-16
I need to install Blender 2.5 alpha 2(Blender2.5 alpha2 linux glibc i686.tar.bz2) but it seems only available thru download and not on the repository. Is there an easy way to do it as I prefer not to run it only on windows as I only run one operating system at a time. I have read spme other tips on installing tar.bz2 files but have trouble following them. I'm fairly new at Linux. So far Ubuntus  impressive as long as I can load this.
Thanks in Advance
Peter

---

### Post by ellgor on 2010-06-17
Hi,

If your after the latest Blender then its a download for you, fortunately, (and I hope this still works from past use) get the download, extract it (homefolder will do) once extracted there should be 3-4 folders, right click on the Blender folder and from the options choose run, this will set off Blender and install it on your system, hope this works for you.

Regards, Ellgor.

---

### Post by petellgra on 2010-06-19
Ellgor, 
I chucked it in and did what you said but there's no run on right click so I double clicked the blender icon and it started but its not installed, I guess there may be dependant files missing.
So I put link on the desktop.   But have other programs that can't be downloaded from repository. So I extracted the file got to ./configure but wouldn't recognize $ make.
Thanks
Peter

---

### Post by ellgor on 2010-06-19
Hi,

Use Alt and F2 together which will bring up a run dialogue box, type in blender, watch as you do and if after say 3 letters or so it completes it for you, blender is installed, if after typing the whole thing and entering, an error message will be displayed saying no such file or program, if it is run it from here.
P.S. try left clicking on the icon.

Regards, Ellgor.

---

### Post by mubtasim123 on 2011-02-13
same problem happens to me

---

### Post by Synicade on 2011-05-02
sudo add-apt-repository ppa:cheleb/blender-svn
sudo apt-get update
sudo apt-get install blender

---

### Post by JustinHicks on 2011-08-22
> **Synicade said:**
> sudo add-apt-repository ppa:cheleb/blender-svn
sudo apt-get update
sudo apt-get install blender

Thanks! this worked perfectly I've been trying to learn blender and all the tutorials (even the basic ones) are for 2.5 and i had 2.4 makes things extremely difficult!

---

### Post by floral on 2012-09-13
it would be great if it worked
I get 
```
Error: can't find signing_key_fingerprint at https://launchpad.net/api/1.0/~cheleb/+archive/blender-svn

```

Any ideas? Any alternatives?

---

