---
title: "Fix mbr?"
date: 2011-08-07
forum: General Help
---

### Post by JBoynton on 2011-08-07
Hello, I have recently fixed the problem with GRUB boot loader error by using the command

"*sudo apt-get install lilo*"
"[SIZE=1]*sudo lilo -M /dev/sda mbr*[/SIZE]"I probably shouldn't have used the exact command...
but now my laptop won't recognize that the hard drive has windows on it, but when i go to Disk Utility, it says all the data partitions are there, I mount the windows partition, and all the files are there, any help? I am using ubuntu 11.04 64-bit livecd from an sd card, and have the Asus EEE PC 1215b-pu17 netbook. Thanks for any help. I have windows 7 64-bit (and recovery) as the other partitions, these won't boot. I no longer have ubuntu on it, and that kinda screwed it... sorry for going on and on, but i need help

---

### Post by oldfred on 2011-08-07
That should have installed a windows boot loader that would boot your windows. You must also have some windows issues. Is boot flag on win7 boot/recovery (200MB)  partition. Or did you move boot files to main c:? Sometimes it just needs chkdsk or perhaps other windows repairs. Do you have windows repair CD?

To see entire configuration:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

