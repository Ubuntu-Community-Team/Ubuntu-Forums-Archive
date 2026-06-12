---
title: "Adobe Flash Plugin Problem: menu buttons"
date: 2010-06-15
forum: General Help
---

### Post by MetapostAddict on 2010-06-15
Is anyone else having trouble with flash menus?  For many sites, if I click on flash menu buttons nothing happens.

For example, on this site, [http://www.lenscrafters.com/eyeglasses/4/eyeglass-and-sunglass-lens-guides](http://www.lenscrafters.com/eyeglasses/4/eyeglass-and-sunglass-lens-guides), if I click "View the eyeglass lens guide," nothing happens.

I have the same problem on this site: [http://www.sansu-sushi.com/](http://www.sansu-sushi.com/)

any ideas?

---

### Post by Smart Viking on 2010-06-15
Hello there. I suppose you installed 64 bit ubuntu, and then installed  ubuntu-restricted-extras?

If so, the problem you have is that in "ubuntu-restricted-extras", there  is only 32 bit flash, which does not work so well in 64 bit, i had the  same problem and it was really annoying. =)

Here is a howto install 64 bit flash: 
[http://ubuntuforums.org/showthread.php?t=1423423](http://ubuntuforums.org/showthread.php?t=1423423)

That should work for you. :)   (if you use 64 bit)

EDIT: You might need to reboot for the changes to take effect.

---

### Post by MetapostAddict on 2010-06-15
> **Smart Viking said:**
> Hello there. I suppose you installed 64 bit ubuntu, and then installed  ubuntu-restricted-extras?

If so, the problem you have is that in "ubuntu-restricted-extras", there  is only 32 bit flash, which does not work so well in 64 bit, i had the  same problem and it was really annoying. =)

Here is a howto install 64 bit flash: 
[http://ubuntuforums.org/showthread.php?t=1423423](http://ubuntuforums.org/showthread.php?t=1423423)

That should work for you. :)   (if you use 64 bit)

EDIT: You might need to reboot for the changes to take effect.

That did it!

Thanks for the quick reply :p

---

### Post by lovinglinux on 2010-06-16
The 64bit flash is no longer supported by Adobe and has a critical vulnerability. you shouldn't be using it anymore. You need to install the 32bit version and apply a simple workaround to fix the original problem with the buttons.

Install [FLASH-AID](http://flash-aid-extension.blogspot.com) extension for Firefox. It will remove conflicting plugins and install the proper flash version according to your browser architecture. 

Then, run this:

```
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
```

Add the following line before the last line of the file opened by the previous command:

```
export GDK_NATIVE_WINDOWS=1
```

Save and restart the browser.

---

### Post by philinux on 2010-06-16
Ah that's the fix, must have missed that one. Don't use much flash. But the speedtest.bbmax website had this, now it's fixed. :p

I think that's helping full screen flash too. I was getting about 2 frames a second. It's not great but definitely better.

---

### Post by Bluesan on 2010-06-16
Cool, thanks.

---

### Post by Cavsfan on 2010-06-16
Here is the bug and the workaround:

_[http://ubuntuforums.org/showpost.php?p=9380613&postcount=2](http://ubuntuforums.org/showpost.php?p=9380613&postcount=2)_

Step 3 as mentioned above is also all it took to work for me.

---

### Post by lovinglinux on 2010-06-16
> **philinux said:**
> I think that's helping full screen flash too. I was getting about 2 frames a second. It's not great but definitely better.

Thanks for the info.

---

### Post by MetapostAddict on 2010-06-16
Thanks!

---

