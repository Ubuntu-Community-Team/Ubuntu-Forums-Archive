---
title: "Lost ability to dual boot into Win 7 via fresh install"
date: 2012-04-30
forum: General Help
---

### Post by AJLChase on 2012-04-30
Hello all,

I recently as of Saturday installed the latest version of Ubuntu on my Win 7 machine. I have two hard drives in raid 0 with Win 7 on it and installed an old 300gb HD to put a fresh Ubuntu on. Once installing, my raid display didn't even show up, so I installed Ubuntu onto the 300gb HD with no problem. I know something popped up saying it couldn't install the boot loader into "" so I chose something else. Not thinking anything of it after I restarted I noticed my raid array is set to "offline member" and I cannot access it. Any tips? 

Thanks!

---

### Post by AJLChase on 2012-04-30
Shameless bump for help

---

### Post by oldfred on 2012-04-30
Where did grub get installed to? Or nowhere? The desktop installer does not include RAID drivers, you need the alternate install or add the RAID drivers, see below as you need them to run script.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/](http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
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

