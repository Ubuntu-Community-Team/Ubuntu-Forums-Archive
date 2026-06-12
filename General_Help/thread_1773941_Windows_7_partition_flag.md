---
title: "Windows 7 partition flag"
date: 2011-06-02
forum: General Help
---

### Post by Xenoryt on 2011-06-02
I made a stupid mistake. I just installed windows 7 and ubuntu stopped booting even though it was still there, so i thought i would just change the patition flag to boot. i found out later that i had to create a new mbr but after i changed the boot flag, windows 7 stopped booting and i tried changing it back, but it didnt work. so i was wondering if i didn't use the correct flags or is there another way to get windows 7 to boot again?

Edit:
forgot to mention that i was using GParted to change the partition flags and that i am using windows 7 ultimate 64bit

---

### Post by oldfred on 2011-06-02
Boot flag is used by windows to know what partition to boot and for windows repairs. Grub does not need it nor use it. But some BIOS have to have a boot flag on a primary partition. If win7, the boot flag should be on the 100MB boot partition, but that will not help grub to find & boot windows.

Post this:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

