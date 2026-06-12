---
title: "External Hard Drive"
date: 2011-06-04
forum: General Help
---

### Post by Anthie95 on 2011-06-04
Hello! 

I just registered to Ubuntu Forums, because I decided to install Ubuntu to my PC permanently. 

I would to like to ask something. A few months ago I tried to install Linux Ubuntu, and I did so. I was excited with the OS, but when I plugged my external HD on my PC and copied my files, and then gave the HD to my Windows-user friend (who gave it to me), Windows could not access any of the files on the HD. Does anybody know why? After using an external HD with linux why can't you reuse it with Windows? And if possible, may I know what to do, so that my files can be accessed in both Operating Systems? 

Thanks in advance!

---

### Post by Joe- on 2011-06-04
Have you checked to see if the files are not hidden? In windows that is.

---

### Post by Anthie95 on 2011-06-04
Yes. I checked the files, but the problems appear only after i connect the HD to linux. What shall I do? I am usually using both OS...Not everyone has linux...

---

### Post by 3xp10r3r|X13 on 2011-06-04
If you formatted your hard drive into any kind of ext format, windows won't be able to read it, because it is not designed to recognize any ext format at all.  (ext, ext 2/3/4)

So you didn't format it? Hmm...sry, not a clue. :)

---

### Post by 3xp10r3r|X13 on 2011-06-04
So you are able to access the hard drive using windows after you've tried it a few times?

---

### Post by Anthie95 on 2011-06-04
No I didn't format my external HD. I just plugged it on Linux PC and afterwards Windows could not access the files

---

### Post by Joe- on 2011-06-04
Do you mean your win7 pc couldn't see the files or the files wouldn't work?

---

### Post by jamesisin on 2011-06-04
Yes, let's look a little more deeply.

Are you using FAT32 on the external?
Which version of Windows are we discussing?
Can Windows access the drive at all?
Can Windows write to the drive?
Can Windows see the files?
Can Windows get a property dialog for a file?
Give us an example file name.

---

### Post by Anthie95 on 2011-06-04
The files wouldn't work. I could see them, but not use them. 

My HD is NTFS.
Windows 7
Yes
Yes
Yes
Generally speaking, the HD works perfectly with windows 7 and Ubuntu. My only problem is that after it has been connected to Ubuntu, Windows cannot use the files written on the HD. I can use them only with linux. Even if I plug it once, and then remove it from Ubuntu System, Windows cannot use the files. I have to format the disk and then rewrite the files on it.

---

### Post by Joe- on 2011-06-04
The files aren't protected in anyway are they? Does viewing the properties in windows 7 say they're read only or locked?

---

### Post by jamesisin on 2011-06-04
As Joe suggests I would check the permissions in case Ubu has altered them for some reason.

---

### Post by Anthie95 on 2011-06-04
No. They are not locked or read-only...

---

### Post by Joe- on 2011-06-04
Do you use the safely remove hardware option each time?

---

### Post by jamesisin on 2011-06-04
And what happens, exactly, when you attempt to access one of these files?  It hangs?  You get an error message?  File types?  Applications used?  Be specific.

You ought to be able to open any file using Notepad.  The contents may be gibberish, but the point is to see if Notepad can open the file.

---

### Post by MartyBuntu on 2011-06-04
What do you mean, "Windows can't use the files"?

Are you trying to run a program off the external drive?

---

### Post by Anthie95 on 2011-06-06
Hi! I just read all of your comments, well the main problem is that windows show an error message. For example I have a folder full of music, and when i connect the HD to Ubuntu, I open the folder and i listen to my music. After disconnecting from Ubuntu and connecting to Windows (7 if it changes anything), I try to open the folder and I always get an error message. 

I really Thank all of you a lot for your interest and your helpful comments. I really appreciate every minute spent from you for my problem. :)

---

### Post by jamesisin on 2011-06-06
Ok, so you double-click on a folder and you get an error message.  What does the error message say exactly?

---

### Post by Anthie95 on 2011-06-08
"Windows could not open the folder". Sometimes, when i plug the HD on Windows after it has been used with Linux it doesn't even show the HD on Windows's "My Computer".

---

### Post by VanR on 2011-06-08
Because it's been formatted ext4 most likely.

---

### Post by jwcalla on 2011-06-08
> **VanR said:**
> Because it's been formatted ext4 most likely.

?

How would that happen?

OP-- are you safely removing the drive using the "eject" mechanism in the file browser (or right-clicking on the drive's desktop icon and selecting "Safely Remove Drive") before unplugging it from your computer?

---

