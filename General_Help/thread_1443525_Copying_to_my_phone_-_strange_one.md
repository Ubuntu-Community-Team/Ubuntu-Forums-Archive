---
title: "Copying to my phone - strange one"
date: 2010-03-31
forum: General Help
---

### Post by thered on 2010-03-31
Here's one for you.

I was happily ripping my Cd collection to mp3 and copying it via USB to my phone - a Nokia 5800 - using copy and paste.  This then was adding it to my 'library' and playing ok.

All of a sudden it will not allow me to copy saying file is read only? This happened half way through pasting a folder, it only copied 10 of the 14 tracks.  Since then it just won't have it via USB.

I can however copy using the same copy and paste using bluetooth. (Sloooow though)

This has got me scratching my head.

I have actually gone back to Windoze and installed and used the PC suite software which works OK, but I don't really want to do this.

Any ideas or help?

PS Ubuntu 9.10.  I've also tried Rhythmbox but it doesn't see my phone.

---

### Post by thered on 2010-03-31
<bump>

Anyone? :)

---

### Post by mechro on 2010-03-31
Do you know what file system is on the phone?

The other day I had similar problems with an SD card formatted with FAT16 file system. I re-formatted it to FAT32 and then everything was OK.

---

### Post by thered on 2010-04-01
I'm fairly certain it is Symbian OS

I didn't want to reformat unless I 'really' have to - 5gig of stuff on there at present. Althoguh If all else fails I supppose I have no option.

Thanks for reply

---

### Post by Bungler on 2010-04-01
Can you click on 'details' when you get this error message? Usually this provides some clues what the actual problem is.

I have a Nokia 5800 and Ubuntu 9.10 and all works fine for me (I use USB and put the phone is mass storage mode when I connect)

---

### Post by thered on 2010-04-05
Sorry about not getting back Bungler.

Details say Unable to copy - file read only (or very similar) - which doesn't make sense.

Mine worked OK too - I also used Mass Storage setting - all was well and I changed no settings.  

Still the same, using PC Suite or Bluetooth at present.

---

### Post by Bungler on 2010-04-07
How do you remove your phone, do you unmount and also in Windows, do you use 'remover mass storage device'? I remember I had trouble with reading/writing a regular usb key because I just removed them, especially when I used it on both windows and ubuntu computers.
Although it of course does not explain the initial error.
Perhaps you can check the permissions on your phone is mass storage mode through Ubuntu and add yourself as user with read/write access?

---

