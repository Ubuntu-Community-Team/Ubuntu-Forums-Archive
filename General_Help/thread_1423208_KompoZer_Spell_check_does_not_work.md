---
title: "KompoZer Spell check does not work"
date: 2010-03-06
forum: General Help
---

### Post by chucksters on 2010-03-06
I don't understand how to enable the spellchecker in KompoZer version 0.8b2 (20090502)

The option is always grayed out. I don't want to use in-line spell-checking. Just selective. 

I'm using karmic. Can anybody help??

I tried installing new dictionaries and other versions of KompoZer.

---

### Post by dsmo223 on 2011-10-29
[SOLVED] 

Did you ever find a solution for this, as I am having the same problem. I am using this to create grading reports for students, and I would like to have my spelling correct on such a document.

---

### Post by oldtimer7777 on 2011-10-29
> **dsmo223 said:**
> Did you ever find a solution for this, as I am having the same problem. I am using this to create grading reports for students, and I would like to have my spelling correct on such a document.

This is a relatively easy solution.

sudo apt-get install kompozer

Then download the latest version for your language and uncompress it:

[http://sourceforge.net/projects/kompozer/files/current/0.8b3/linux-i686/](http://sourceforge.net/projects/kompozer/files/current/0.8b3/linux-i686/)

To install PCMANFM use:

sudo apt-get install pcmanfm

Open PCMANFM file manger and click Tools, and click Open Current Folder as Root.

Navigate PCMANFM file manager to /usr/lib/ 

Drag and drop that new Kompozer folder you just uncompressed and downloaded into:

/usr/lib/ 

When it prompts to overwrite files, select Yes.

And now restart Kompozer.. Go to preferences and advanced and enable spell check. 

Troubleshooting: If you catch errors, it is because you either didn't set PCMANFM to Open Folder as Root, or you dropped the downloaded Kompozer folder in the wrong place.



:guitar:

---

### Post by ronnoc on 2011-12-27
That solution worked for me. Awesome! Thanks. As a side note, one can simply "sudo dolphin" to do the above as well, if they do not wish to download another file manager...otherwise this trick worked great! 

BTW - Is it just a packaging issue as to why the version in the repos cannot spell check?

---

### Post by dsmo223 on 2011-12-27
Thanks oldtimer7777, this solution worked great.

---

### Post by dsmo223 on 2011-12-27
> **ronnoc said:**
> That solution worked for me. Awesome! Thanks. As a side note, one can simply "sudo dolphin" to do the above as well, if they do not wish to download another file manager...otherwise this trick worked great! 

BTW - Is it just a packaging issue as to why the version in the repos cannot spell check?


Another option is to use sudo nautilus.:)

---

### Post by KeesM on 2012-09-17
Unfortunately, did not work for me... After doing the steps (using sudo Nautilus, but that should not make a difference), Kompozer did not start anymore (and also did not give any error messages when starting from a terminal, just returned to the prompt). Had to uninstall and reinstall to get Kompozer back. No time to look into more details at the moment; maybe later. Ubuntu 12.04 64 bits.

---

### Post by Elfy on 2012-09-18
If you need help please start a new thread.

---

