---
title: "Can't transfer anything to or from the HDD"
date: 2011-05-13
forum: General Help
---

### Post by totoes on 2011-05-13
Hello,
I have a Iomega Prestige 1TB harddrive bought it half a year ago, but now I have a problem copying anything from it or to it. When copy something to the harddrive the copying window pops up, and when the green progress bar fills about 9/10 of the bar it stops, and another window pops up saying "can't read from the source file or disk", and below it the discription of the file and two buttons "Try Again" and "Cancel", but for most of the files the green progress bar in the copying window doesn't even show, and a green small bar just keeps going from left to right without starting the copying, this stays for about 15 minutes then the "can't read from source or disk" pops out.
I can't copy or move anything to it or from, and right now my computer's HD is full so I really need the External HD.
Please help me with this problem.

---

### Post by ajgreeny on 2011-05-13
Are you trying to copy a file of 4GB or larger, and is the disk an external USB formatted to fat32?  There is a fat32 file size limit of 4GB.

If this is the problem, format the problem drive to something other than fat32, ntfs if you need both linux and windows access, or ext# if only linux.

---

### Post by varunendra on 2011-05-13
Seems like a low power/signal or failing drive problem to me. I think the 4GB limit issue doesn't allow even starting the copy process, so I doubt it to be the case here.

If it is a portable hard disk (one that has no additional power adapter), try only back panel USB ports if it is an old motherboard (newer Gigabyte boards provide boosted power on front USB ports) + a good quality cable as short as possible. This will ensure the external drive gets sufficient power (and strong signals) to drive it.

If it is a 3.5" drive (with external power adapter), then only the length of the USB cable matters (should be as short as possible). Also, if its warranty has expired, then you may try opening the case, pull out the drive and attach it directly to the SATA (I assume it is SATA as 1TB IDE is rare) port on the motherboard. This will eliminate the chances of USB cable or external power issues.

---

### Post by totoes on 2011-05-13
> **ajgreeny said:**
> Are you trying to copy a file of 4GB or larger, and is the disk an external USB formatted to fat32? There is a fat32 file size limit of 4GB.
 
If this is the problem, format the problem drive to something other than fat32, ntfs if you need both linux and windows access, or ext# if only linux.
 
thank you for your reply, but my HDD is formatted to NTFS
 
 
> **varunendra said:**
> Seems like a low power/signal or failing drive problem to me. I think the 4GB limit issue doesn't allow even starting the copy process, so it I doubt it to be the case here.
 
If it is a portable hard disk (one that has no additional power adapter), try only back panel USB ports if it is an old motherboard (newer Gigabyte boards provide boosted power on front USB ports) + a good quality cable as short as possible. This will ensure the external drive gets sufficient power (and strong signals) to drive it.
 
If it is a 3.5" drive (with external power adapter), then only the length of the USB cable matters (should be as short as possible). Also, if its warranty has expired, then you may try opening the case, pull out the drive and attach it directly to the SATA (I assume it is SATA as 1TB IDE is rare) port on the motherboard. This will eliminate the chances of USB cable or external power issues.
 
it's a 2.5" drive it has a USB cable with two USB heads (I don't know why), and it is 50 centimeters long. And the HDD didn't come with a driver, and it's warranty is still not expired.

---

### Post by varunendra on 2011-05-13
> **totoes said:**
> it's a 2.5" drive it has a USB cable with [COLOR=Red]**two USB heads**[/COLOR] (I don't know why), and it is 50 centimeters long. And the HDD didn't come with a driver, and it's warranty is still not expired.
Useful info!

The two heads in the USB cable are meant to address the same power issue I mentioned. More paths=more current for the drive. Use both the heads (plug them in two separate USB ports on the back panel). 50 cm is not too long for data signals or even the current if the source supply is good.

When the copying starts then fails, can you still browse/open (without hangs or delays) the folders and files in the external drive?

---

### Post by gradinaruvasile on 2011-05-13
What OS do you use (if Ubuntu what version)?
What is the program do you use to copy?
What are you copying? Are those files that trigger the problem the same?
What file systems sre involved? How many files (and their total size) are you trying to copy?
Were these file systems checked beforehand?

---

### Post by totoes on 2011-05-13
> **varunendra said:**
> Useful info!
 
The two heads in the USB cable are meant to address the same power issue I mentioned. More paths=more current for the drive. Use both the heads (plug them in two separate USB ports on the back panel). 50 cm is not too long for data signals or even the current if the source supply is good.
 
When the copying starts then fails, can you still browse/open (without hangs or delays) the folders and files in the external drive?
 
I tried connecting both of the heads, and still have the same problem
I can still browse the folders but can't open the files.
and when I enter a folder a green progress bar appears going slowly until it stops a little before the end and stays like this forever, as you can see in the picture:
[IMG]http://img820.imageshack.us/img820/8791/capturebtl.jpg[/IMG]
 
 
> **gradinaruvasile said:**
> What OS do you use (if Ubuntu what version)?
What is the program do you use to copy?
What are you copying? Are those files that trigger the problem the same?
What file systems sre involved? How many files (and their total size) are you trying to copy?
Were these file systems checked beforehand?
 
I use Windows 7
I use the default copier of the windows
I'm try to copy all kinds of files, videos, pictures, music, RARs
Tried to copy all the files in it with different sizes and tried copying one by one
I used these file before so I am sure that the problem is not from the files

---

### Post by K_45 on 2011-05-13
Can you open the files/drive from an Ubuntu Live CD?

---

### Post by varunendra on 2011-05-14
Most often the read/write problems on an external drive are related with permission issues. But the symptoms in your case seem to me as if there is a physical or file-system error.

Open command prompt in Windows 7 and enter this command:
```
chkdsk g:
```
(assuming your external drive always connects as G: drive)
This will run chkdsk in read-only mode and will report if any physical or file-system errors are found.
Run the same command on the source drive. You may be prompted to set it to run at startup if it is your system drive.

Consider this as a very important check since if there are such problems on either of the drives, there is a potential risk of loosing all your data on it anytime!

After performing chkdsk, if no errors are found, then I'd suggest what K_45 suggested. Right now your first priority is to make space on your internal drive. So if there are no physical errors on the source and destination drives, there should be no problem doing this through a Live CD. If you encounter any permission issues in Live mode, we're here to help!

By the way, if your external drive is NTFS and you are using Windows 7 then what is that brought you here in ubuntu forums? Not a complain, just curiosity.. :)

---

### Post by totoes on 2011-05-17
> **varunendra said:**
> Most often the read/write problems on an external drive are related with permission issues. But the symptoms in your case seem to me as if there is a physical or file-system error.

Open command prompt in Windows 7 and enter this command:
```
chkdsk g:
```
(assuming your external drive always connects as G: drive)
This will run chkdsk in read-only mode and will report if any physical or file-system errors are found.
Run the same command on the source drive. You may be prompted to set it to run at startup if it is your system drive.

Consider this as a very important check since if there are such problems on either of the drives, there is a potential risk of loosing all your data on it anytime!

After performing chkdsk, if no errors are found, then I'd suggest what K_45 suggested. Right now your first priority is to make space on your internal drive. So if there are no physical errors on the source and destination drives, there should be no problem doing this through a Live CD. If you encounter any permission issues in Live mode, we're here to help!

By the way, if your external drive is NTFS and you are using Windows 7 then what is that brought you here in ubuntu forums? Not a complain, just curiosity.. :)
I tried that adn it didn't fing any errors

---

### Post by varunendra on 2011-05-19
> **totoes said:**
> I tried that adn it didn't fing any errors

Then what happened with the Live CD option we suggested?

---

