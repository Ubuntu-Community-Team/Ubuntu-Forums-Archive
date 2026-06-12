---
title: "Win 7 external hard drive issue"
date: 2009-10-22
forum: General Help
---

### Post by BlackSwordD2 on 2009-10-22
so i've had this issue with both Vista and now win 7 where my external hard drive is read-only. mind you, it works wonderfully in windows XP its read and write. its read and write in Ubuntu. but not in win 7. i dont want to have to pull all the information from the external to my hard drive just to reformat it and push the data back onto it. is there some setting that has made my external read only? this isn't an issue for either my 1g and 512mb flash drives just my 320g external

(since microsoft forums are useless at helping me hope someone out there may be able to help, my thougts are it may be bitlocker? being as it didn't exist until Vista)

---

### Post by Giblet5 on 2009-10-22
Is this intermittent or all the time? What filesystem type is the external drive?

I just tried a 320G FAT32 drive hooked up via USB and Win7 can write to that. There's nothing on it, so I have no problem with making it NTFS as a test.

---

### Post by BlackSwordD2 on 2009-10-22
its all the time, its also plugged in all the time and its NTFS format

---

### Post by Giblet5 on 2009-10-22
> **BlackSwordD2 said:**
> its all the time, its also plugged in all the time and its NTFS format

Feh. I have to go to a meeting shortly. I'll check back in 45 or so and if someone else hasn't answered this, I'll try NTFS on an external USB 320.

---

### Post by BlackSwordD2 on 2009-10-22
kk, thankyou

---

### Post by Giblet5 on 2009-10-22
It works. Read/write under Win7 x64 RC, patched to date.

I got nothin, but it looks like it's your Win7.

Sorry.

---

### Post by BlackSwordD2 on 2009-10-22
even if i had this same issue with both win 9 and Vista? why would there be a problem in both?

---

### Post by Giblet5 on 2009-10-22
I don't know why Windows does MANY things.

This is one more.

Better still, why does it happen on your Win7 (and Vista) and not mine?

Mine are both x64: Vista Ultimate and Win7 RC. Are you on 32-bit or 64-bit?

---

### Post by Sylslay on 2009-10-22
Connect USB drive to other machine with windows famlily, XP, Vista,,server03/08

than  shoutdown the windows with usb plug in.. maight help

Was kind bitlocker, work other way - I could not read unpluged 320gb toshiba in ubuntu 8.04,
but when I reboot XP to Ubuntu , works fine

PS. Remeber that win XP without SP1 could't  create partition large than 128GB.

---

### Post by P4man on 2009-10-22
I doubt its bitlocker. If it were, XP would be unable to read it.
No idea how to solve it though. Perhaps look for a bug report or file a new one. 

oh wait

:)

Joking asidem check the ntfs permissions on the drive. Perhaps take ownership of it again. I believe there is even a terminal command for that in windows, called ```
takeown
```. Since ```
man takeown
``` wont work, google for it

edit: perhaps your username is X in XP and Y in Vista and 7 and the drive is owned by X ?

---

### Post by BlackSwordD2 on 2009-10-22
> **Giblet5 said:**
> I don't know why Windows does MANY things.

This is one more.

Better still, why does it happen on your Win7 (and Vista) and not mine?

Mine are both x64: Vista Ultimate and Win7 RC. Are you on 32-bit or 64-bit?

both were 64 bit (Vista Ultimate and Windows 7 Professional) however the XP was 32 bit


> **P4man said:**
> I doubt its bitlocker. If it were, XP would be unable to read it.
No idea how to solve it though. Perhaps look for a bug report or file a new one. 

oh wait

:)

Joking asidem check the ntfs permissions on the drive. Perhaps take ownership of it again. I believe there is even a terminal command for that in windows, called ```
takeown
```. Since ```
man takeown
``` wont work, google for it

edit: perhaps your username is X in XP and Y in Vista and 7 and the drive is owned by X ?

takeown gave me privileges error as user and media is write protected as admin

also i have used the same login name on all three OS's

---

### Post by BlackSwordD2 on 2009-10-22
so i've been digging around a lot and it seems that this is a very common error...and everyone else seems to get their's solved :(

they way of choice seems to be using the comand line with the attrib command...yet mine doesn't work...

---

