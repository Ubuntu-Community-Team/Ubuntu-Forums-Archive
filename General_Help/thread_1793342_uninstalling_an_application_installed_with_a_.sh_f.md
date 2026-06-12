---
title: "uninstalling an application installed with a .sh file"
date: 2011-06-29
forum: General Help
---

### Post by mkwn on 2011-06-29
I am having trouble installing mathematica 8 and found this workaround: [http://ubuntuforums.org/showpost.php?p=10410947&postcount=2](http://ubuntuforums.org/showpost.php?p=10410947&postcount=2)

The workaround involves uninstalling Mathematica then installing in a specific way. However I seem to be unable to properly uninstall the program because even after I delete the directories /usr/local/Wolfram and /.Mathematica, after I reinstall, Mathematica is already activated. The activation data must be located somewhere that I haven't removed.

Is there a general way to remove all trace of a program installed by a .sh file? Alternatively, are there any common locations I could look for this data? I don't really understand the meaning of all the 3-letter directories like "usr" and "etc", where these things seem to be installed.

I am running Ubuntu 10.10, if that's relevant.

Many thanks

Matt

---

### Post by Ozymandias_117 on 2011-06-29
Check in /usr and /opt, a folder of it's stuff should be in one of those, and most will include a uninstall.sh there.

---

### Post by mkwn on 2011-06-29
Thank you! I found some files in /usr/share.

Just out of interest, what is the meaning of etc, opt, usr and such? my opt folder is totally empty.

(the workaround didn't work but that's another issue)

---

### Post by Dave_L on 2011-06-29
Here's an explanation of the Linux directories:

Filesystem Hierarchy Standard
[http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)

---

### Post by gandaran on 2011-06-29
> **mkwn said:**
> I am having trouble installing mathematica 8 and found this workaround: [http://ubuntuforums.org/showpost.php?p=10410947&postcount=2](http://ubuntuforums.org/showpost.php?p=10410947&postcount=2)

The workaround involves uninstalling Mathematica then installing in a specific way. However I seem to be unable to properly uninstall the program because even after I delete the directories /usr/local/Wolfram and /.Mathematica, after I reinstall, Mathematica is already activated. The activation data must be located somewhere that I haven't removed.

Is there a general way to remove all trace of a program installed by a .sh file? Alternatively, are there any common locations I could look for this data? I don't really understand the meaning of all the 3-letter directories like "usr" and "etc", where these things seem to be installed.

I am running Ubuntu 10.10, if that's relevant.

Many thanks

Matt
user configuration files are stored in your hidden home/'user' directory, these user files don't get removed when you uninstall the application you have to find and delete.

---

### Post by Antipacket on 2011-06-29
I had a similar problem a few months back. You can open the .sh file in a text editor and see where the install will be made too.

Cheers!

---

