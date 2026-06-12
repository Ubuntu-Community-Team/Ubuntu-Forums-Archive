---
title: "Command line prompts in Karmic: Cut and Paste Directories to USB Flash Drive"
date: 2009-11-20
forum: General Help
---

### Post by vince.lupe on 2009-11-20
To make a long story short, I tried to install a theme in Emerald and it rendered my access to the desktop deniable - so, I need to cut and paste all of my folders and files from My Documents in Karmic to my USB Flash Drive. Can anyone tell me how to do that, step by step? Will it automatically merge all of my files and folders? I'd be greatly appreciative, for all of my college classwork and pictures and stuff is in there.
 
Thank you very much :')
 
- Vince

---

### Post by prshah on 2009-11-20
> **vince.lupe said:**
> I need to cut and paste all of my folders and files from My Documents in Karmic to my USB Flash Drive. 

To copy entire directories, you can use the cp recursive command, example```
sudo cp -p -r -v ~/My\ Documents /media/usbstick
```

This will copy your "My Documents" directory (assumed to be in your home (~) directory) to the usb stick (assumed to be in /media/usbstick).

If the usb stick already contains a directory "My Documents" then the source and destination will be merged; files in the source that exist on the destination will be overwritten; files in source that are not in the destination will be copied; files in destination that are not in source will remain untouched.

If you want to avoid overwriting possibly newer files on the usb stick, use the "-u" switch in addition to the above; this will "update" existing files, ie, it will only overwrite files on the destination if the source timestamp is more recent. Adding "--backup" to the switches will make a backup copy of each overwritten file- on the destination.

If you want to avoid ANY overwriting use "-n" (no-clobber); in this case, files in source that already exist in the destination will be not copied, no matter what the timestamp. Such files will simply be ignored.

Please post back if you need some more information. For details on what each switch does, please refer to the cp manual page```
man cp
```

You do this at your own risk, so please make a backup of your USB stick before running the above command(s).

---

### Post by vince.lupe on 2009-11-23
> **prshah said:**
> To copy entire directories, you can use the cp recursive command, example```
sudo cp -p -r -v ~/My\ Documents /media/usbstick
```This will copy your "My Documents" directory (assumed to be in your home (~) directory) to the usb stick (assumed to be in /media/usbstick).

If the usb stick already contains a directory "My Documents" then the source and destination will be merged; files in the source that exist on the destination will be overwritten; files in source that are not in the destination will be copied; files in destination that are not in source will remain untouched.

If you want to avoid overwriting possibly newer files on the usb stick, use the "-u" switch in addition to the above; this will "update" existing files, ie, it will only overwrite files on the destination if the source timestamp is more recent. Adding "--backup" to the switches will make a backup copy of each overwritten file- on the destination.

If you want to avoid ANY overwriting use "-n" (no-clobber); in this case, files in source that already exist in the destination will be not copied, no matter what the timestamp. Such files will simply be ignored.

Please post back if you need some more information. For details on what each switch does, please refer to the cp manual page```
man cp
```You do this at your own risk, so please make a backup of your USB stick before running the above command(s).

Thank you, pr. :')

---

