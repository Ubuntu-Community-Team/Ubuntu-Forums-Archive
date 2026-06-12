---
title: "Grub list mess"
date: 2010-12-09
forum: General Help
---

### Post by poxet on 2010-12-09
Hello, there,
So... I went ahead and reinstalled both Windows 7 and Ubuntu, but I ended up making a huge mess. I don't know EXACTLY what is it that it is messed up (if the mbr or what) but I have a bunch of operating systems detected as installed which are actually not, and some are not detected but are installed.
I don't know why I never could install Win7 so that the "boot thing" (boot.ini or whatever) is saved in the same disk as the Win7 install.
Is there a way I can view all the operating systems I have that are detected as installed and do some sort of a cleanup?

---

### Post by oldfred on 2010-12-10
the grub menu will show all the kernels you have and you should always keep one older one that you know works, just in case the current gets hosed.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

Delete old kernels:
Be sure what kernel you are using, so you do not delete it.
lsb_release -a
Go to Synaptic Package Manager and search for linux-image.
More info in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

---

