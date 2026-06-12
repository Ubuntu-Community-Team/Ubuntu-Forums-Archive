---
title: "Save My Marriage"
date: 2009-09-22
forum: General Help
---

### Post by seataltea on 2009-09-22
For the last 10yrs I've backed up all photos but since installing Ubuntu 9.04 earlier this year have failed to do that on this years snaps. Idiocy.

The upgrade of the pre-release version on 9.1 has gone belly up (it only reboots to a text command line with no GUI?) and so I'm running 9.04 from a live CD and moving all files across to an external HD before a fresh installation and new start.

The problem I have is that the 2009 file of photographs accessed on the laptops HD is locked and I do not have the savvy to unlock it and so transfer the files across to the external HD.

I'm one of the new bunch of Ubuntu users without the technical skills on the command line to unlock the file (I have no idea why it would be locked anyway) and need to save the photos or I will suffer at the hands of my wife for losing this years photographs of our daughter. Totally my fault, I should have waited for the proper release of 9.1 and it serves me right.

Simple, direct and specific advice would be very grateful.

---

### Post by P4man on 2009-09-22
A "lock" icon afaik, wouldnt prevent you from copying. It means you cant write to those files or folders. If you don't have read permission though, try opening the file manager as root. Press alt+F2 and type "gksudo nautilus". That should open the file manager with root permission.

edit btw, in the karmic testing thread there is a sticky post that explains how to solve the problem you had with karmic.

---

### Post by yeats on 2009-09-22
Sorry to hear about your trials and tribulations.  Using the live CD, you should be able to execute commands using sudo that let you act as root.  You will need to know the full directory path from your hard drive to the external drive, but it will go something like this (in the terminal):

```
sudo cp -r /media/*[HD directory]*/*[path]*/2009-photos /media/*external-HD*/*[Recovery_directory]*/2009-photos
```

which will create a new directory with your photos within whatever "Recovery_directory" is. 
sudo = "execute this command as root"
cp  -r = "copy recursively" (-r is required for a directory)

Does that help?

*EDIT* - try P4man's method first :-)

---

### Post by seataltea on 2009-09-22
> **P4man said:**
> A "lock" icon afaik, wouldnt prevent you from copying. It means you cant write to those files or folders. If you don't have read permission though, try opening the file manager as root. Press alt+F2 and type "gksudo nautilus". That should open the file manager with root permission.

edit btw, in the karmic testing thread there is a sticky post that explains how to solve the problem you had with karmic.

It seems to be working, 5GB of this years photos appear to be moving now, fingers crossed.............

---

### Post by Arup on 2009-09-22
Next time don't do beta software with important stuff like that. I have a seperate partition for Data which doesn't have to be touched in case the OS is hosed.

---

### Post by seataltea on 2009-09-22
Well it appeared to work using the gksudo nautilus command. The file transfer took place and it transferred the data but on trying to view the contents of the individual months files with the main 2009 folder Jan Feb etc there was no visible content despite the properties indicating data was present.

The 2009 laptop file is unlocked (no lock icon), I can view, Gimp and save copies of the photographs on the laptop and save copies individually onto the external HD.

So I had another go at transferring the entire 2009 file again using the above command but get the permission denied pop up again.

Even to me it seems a little bizarre being able to access individual photos but seemingly not being able to copy them over to an external HD.

I'm puzzled and will have a go at recovering karmic from the thread, there's a lesson in here.

---

