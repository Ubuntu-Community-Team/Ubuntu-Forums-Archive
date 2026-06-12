---
title: "Boot problem with 11. 04"
date: 2011-05-02
forum: General Help
---

### Post by Benbow on 2011-05-02
After a huge calamity when my hdd went down, I reinstalled win 7 and then 11.04 for the first time as per the instructions to run both systems side by side. Normally I would format the drive myself and then install Ubuntu but this time, as it was a new install for both, I went the easy way.
Ubuntu installed ok but when I restarted instead of the dual boot screen it went straight to windows.
I am no stranger to Ubuntu but this is the first time this has happened to me and I would welcome any advice as to how to restore the dual boot.
Brian

---

### Post by oldfred on 2011-05-02
You may just need to reinstall grub2's boot loader to the MBR, but lets check on what is where, you can run from LiveCD:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

If Natty it would be slightly better to download the test version. It has no instructions see above link.  Grub 1.99 changes some internals and the test version of script works better, but has not been finalized.

Get last development version of Boot Info Script:
wget -O boot_info_script.sh 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=boot_info_script.sh;hb=HEAD'

V56 has improved formating and requires code tags to make it legible. 
Install these before running script:
Is able to search LVM partitions if the LVM2 package is install
# ("apt-get install lvm2" in debian based distros)
# Is able to search Linux Software Raid partitions (MD Raids) if
# the "mdadm" package is installed.

Supergrub may also let you boot directly. Not sure how well it works with Natty.
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

