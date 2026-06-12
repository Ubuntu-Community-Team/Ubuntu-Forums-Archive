---
title: "Grub won't add Gentoo to my list of operating systems"
date: 2012-03-17
forum: General Help
---

### Post by wilsonsamm on 2012-03-17
I've used gentoo linux for some time, and now I'm just setting up ubuntu on a spare partition. I will have Ubuntu doing the Grub stuff.
At the terminal I type the following:
```
 $ sudo update-grub
[sudo] password for sam: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-39-generic
Found initrd image: /boot/initrd.img-2.6.32-39-generic
Found linux image: /boot/vmlinuz-2.6.32-33-generic
Found initrd image: /boot/initrd.img-2.6.32-33-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Gentoo Base System release 2.0.3 on /dev/sda2
done

```

But even so, Gentoo is not showing up on the boot-up menu! Am I missing something? Is there something else I should do?

---

### Post by wilsonsamm on 2012-03-18
```
sudo update-grub2
``` has the same behaviour. I am using GRUB 2 I suppose.

---

### Post by Helen McCall on 2012-03-18
if you have a command update-grub2 then it is highly likely you are using grub 2.

You might need to write a custom menu. Try reading [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) and follow the links to other documentation for Grub 2.

---

### Post by 3Miro on 2012-03-18
This is a bug and it has been there for quite a while. You have to either add Gentoo manually to the grub2 configuration or just use Grub 1 from Gentoo and add Ubuntu to it (also manually).

---

### Post by oldfred on 2012-03-18
You can post this to see where everything is installed:

The git/testing version has some fixes:
```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript

```

This is the older version that does not included the fixes above but has instructions:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

Is able to search LVM partitions if the LVM2 package is install
# ("apt-get install lvm2" in debian based distros)
# Is able to search Linux Software Raid partitions (MD Raids) if
# the "mdadm" package is installed.
sudo apt-get install lvm2
sudo apt-get install mdadm
sudo apt-get install xz-utils
unlzma is equivalent to xz --format=lzma --decompress.

---

### Post by garyed on 2012-03-18
I had a similar problem with ZenMini Linux & had to put the commands in "/etc/grub.d/40_custom" file.
If you have an old menu.lst that shows the menu commands for Gentoo you could just copy them into the 40_custom file & then run update-grub.
After I get everything to boot up right I make my 30_os-prober un-executable & copy all the menu items I want & give them all the names I want over to my 40_custom file & run update-grub. That's the easiest way to make a custom grub2 menu.

---

