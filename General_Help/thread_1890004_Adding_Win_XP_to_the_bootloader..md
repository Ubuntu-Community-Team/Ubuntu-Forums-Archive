---
title: "Adding Win XP to the bootloader."
date: 2011-12-02
forum: General Help
---

### Post by okaokaokaokaokaokaokaoka on 2011-12-02
Hello.

I just installed installed Windows XP on an old partition but I cannot get it to display in the boot load menu. After the install I used boot-repair to get Ubuntu and Win 7 back, which worked fine, but it didn't add XP, which is less than desirable.

How do I get the problem fixed? 20 minutes with Google didn't help all that much as I'm a noob (shell scripts are scary), so I hope I can get some assistance from here :)

EDIT: Made a mistake in the problem description. It's actually that WinXP is  the one under the Win7 option, making Windows 7 inaccessible. Still am missing an OS and the oddities abound given that boot-repair mislabeled XP as 7.

---

### Post by zvacet on 2011-12-03
When using boot-repair just reinstall ubuntu grub where it suppose to be.After that boot ubuntu and run 

```
sudo update-grub
```

Grub should find all your OS.

---

### Post by oldfred on 2011-12-03
Welcome to the forums.

Windows always combines its boot into one primary NTFS partition that has the boot flag or in Windows is the active partition. Are both Windows installs in primary partitions? Normally Windows 7 controls the boot in a dual boot configuration with XP.

To get each MS to have its own boot loader make a primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

### Post by okaokaokaokaokaokaokaoka on 2011-12-04
Zvacet:

Gives the same results as before.

Oldfred:

So if I understand correctly the thread you linked resolved with install XP, remove boot flag, install 7, install Ubuntu.

Can I do it without reinstalling Ubuntu and 7? Backing up would be a major pain. Or would I just be better off figuring out how to use a virtual machine?

EDIT: And if I do opt for VM (I don't need XP for anything demanding), how do I change grub to get me into 7? Would simply formatting the XP partition and running boot-repair work?

---

### Post by oldfred on 2011-12-04
I think we need to see where the Windows files are at. Did you delete a 100MB hidden in Windows partition. If so that was a boot/repair partition with two of the boot files. If grub does not see those two files it does not find Windows 7 to boot (neither will Windows).

Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe 

Post this from Ubuntu or liveCD:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
sudo apt-get install mawk

---

