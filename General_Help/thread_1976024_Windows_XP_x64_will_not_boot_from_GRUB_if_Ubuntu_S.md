---
title: "Windows XP x64 will not boot from GRUB if Ubuntu SATA drive is present"
date: 2012-05-08
forum: General Help
---

### Post by tslocum on 2012-05-08
I recently installed Ubuntu on a 3TB SATA drive alongside my Windows installation.  GRUB recognized the Windows installation however if I pick it from the list, I encounter the following error:

```
Windows could not start because the following file is missing or corrupt: 

<Windows root>\system32\ntoskrnl.exe. 
Please reinstall a copy of the above file. 
```

Initially I tried to reinstall ntoskrnl.exe from my Windows disk, thinking it was corrupt.  However, after that fix failing as well as others I tried unplugging my new SATA drive and booting directly into the Windows drive.  Lo and behold I found myself staring at the Windows boot screen.

Is this a problem which I can fix within GRUB?  I have a feeling the large hard drive is interfering with the boot process of Windows because of its size.  Thank you in advance for the help.

---

### Post by decrepit on 2012-05-08
This is going back a bit now, and the old memory's a bit hazy.
But I think windows needs to think it's on the primary partition of the main hdd.
If bios is reporting the new sata drive as the main, windows may be spitting the dummy.
There is a method in grub to convince windows this isn't the case.

sorry I can't remember the exact word, but it swaps the 2 hdds over as far as windows is concerned.
I think a bit of searching, or reading the grub manual will come up with the answer.
Or maybe somebody else will come up with the definitive solution.

---

### Post by oldfred on 2012-05-08
Is 3TB drive gpt? Windows XP will not read gpt, but if on a separate MBR drive it should be ok.

Post results.txt that this creates.
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

---

