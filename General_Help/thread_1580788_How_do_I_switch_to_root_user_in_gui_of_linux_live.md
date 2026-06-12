---
title: "How do I switch to root user in gui of linux live?"
date: 2010-09-23
forum: General Help
---

### Post by candyman17 on 2010-09-23
I need to access some things in "documents and settings" folders (my windows xp crashed). I believe I need to be root user in linux to do this. I am running a ubuntu linux live (uninstalled) cd. I am new to linux and I do not know if this is even possible. I want to copy some things from documents and settings folder to an external drive (as backup) but I cannot access them as things are now (linux gives me an error when I try) but I would like to do it in gui so I can physically "see" everything and look through it. If it is not possible in gui then could someone tell me the command(s) to copy the whole folder over in the cli (terminal)? Your help is much appreciated.

---

### Post by ST3ALTHPSYCH0 on 2010-09-23
First, you shouldn't need SU privileges to do this. Linux holds no respect (that I've found) for Windows folder permissions. 
Second, if you really need a root file browser:
Alt+F2 to bring up a run dialog
```

gksudo nautilus

```

---

### Post by 7h3d4rk0n3 on 2010-09-23
I believe by default you have root permissions as the live user. I'm pretty sure you can get into your Windows partition.

Otherwise, try going to the folder it is in, opening a terminal and typing:

sudo su

then drag the icon for your Windows partition into the terminal.

---

### Post by CharlesA on 2010-09-23
> **berwald.derik@gmail.com said:**
> I believe by default you have root permissions as the live user. I'm pretty sure you can get into your Windows partition. If not, you can open a terminal and type:

sudo su
/dev/YOUR WINDOWS PARTITION NAME

This should allow you to open your Windows 7 partition as root.

You don't have root permission by default, but sudo won't prompt for the password.

I don't think gksu is installed on the livecd, so just use sudo.

---

### Post by candyman17 on 2010-09-23
Thank you for your answers. What St3alth said makes sense, but I don't know what else to do... there is some issue specifically with the "documents and settings" folder that I cannot access the files in it. I originally posted the question 

"Okay, I am in linux (ubuntu) because my windows crashed (blue screen saying "unmountable_boot_volume", whatever that means) and I am trying to copy all my files to an external drive. I have most of them copied over already, but then I decided to check the documents and settings folder, and sure enough, it didn't copy all of those folders/files. When I go into the documents and settings/my name/desktop folder on the filesystem it will show all the folders and loose files within the desktop folder, but it will tell me "the folder contents could not be displayed" when I try to go into any folder here and I cannot access any of the files also. I have tried to display txt files in here and they are all blank, and when I try to open other files it tells me they do not exist or "no such file or directory". What is even stranger though, is that the .fdf and .pdf files show the text or image that is on their first page in their icons, but they still give me the error I mentioned previously or "input/output error". Can anyone help me with this?!"

on Yahoo!Answers (I know, probably not the best place to ask this) and someone mentioned it could be a permissions issue and I would need to log in as root user. (Should I start a new thread and ask the question above? I'm not quite sure how this works...)

---

### Post by CharlesA on 2010-09-23
Input/Output error usually means it's having problems reading the drive. That would explain the "unmountable boot volume" error.

Linux doesn't care about Windows permissions, so I doubt it's a permission problem. If the drive is encrypted, however, that would be a problem.

---

### Post by anirudhtomer on 2010-09-23
usually I set a root user password to access the root user in ubuntu.

there is of-course a root user in ubuntu but its password is not set initially so you are not able to access it.
by running the above command you set a password and the next time you login via GUI put username as "root" and password as whatever you would have set.:cool:

---

### Post by candyman17 on 2010-09-23
So what would cause it to give the errors I mentioned within that one particular folder (and what causes "unmountable boot volume", for that matter)? Why would it have problems reading the drive? Please don't tell me all the data is corrupted...

---

### Post by CharlesA on 2010-09-23
It's easier just to use **sudo -i**.

Check the page [here]("https://help.ubuntu.com/community/RootSudo") for more info about using sudo.

> **candyman17 said:**
> So what would cause it to give the errors I mentioned within that one particular folder (and what causes "unmountable boot volume", for that matter)? Why would it have problems reading the drive? Please don't tell me all the data is corrupted...

Hard drives have moving parts. They all die eventually. There are a variety of reasons why a file system can become inaccessible or corrupted.

Have you tried booting off a Windows disk and running chkdisk on it?

---

### Post by candyman17 on 2010-09-23
I have been afraid to use chkdsk to fix anything because last time it ran it  deleted some important files that it shouldn't have deleted, and put me  into "extreme default mode" (as I call it) where my screen resolution  and graphics were horrible and had no sound, etc., and it took me  forever to correct these issues. But it looks like this may be my only option at this point, as I looked up some fixes for "unmountable boot volume" and they all suggested the same thing. I have backed up pretty much all the rest of the stuff from the c: drive, I just hope chkdsk doesn't delete the stuff in my "documents and settings" folder...

---

### Post by CharlesA on 2010-09-23
> **candyman17 said:**
> I have been afraid to use chkdsk to fix anything because last time it ran it  deleted some important files that it shouldn't have deleted, and put me  into "extreme default mode" (as I call it) where my screen resolution  and graphics were horrible and had no sound, etc., and it took me  forever to correct these issues. But it looks like this may be my only option at this point, as I looked up some fixes for "unmountable boot volume" and they all suggested the same thing. I have backed up pretty much all the rest of the stuff from the c: drive, I just hope chkdsk doesn't delete the stuff in my "documents and settings" folder...

That sort of thing points to file corruption and a drive that is on it's way out.

If you run chkdisk, you should run it with the /R switch to try to recover data from bad sectors.

Try running chkdisk like so:

```
chkdsk /F /V /R C:
```

I think that's the syntax, I haven't used it in a while.

---

### Post by candyman17 on 2010-09-23
Okay, I'll try that. I think /F is fix, but what is /V? It is a pretty old computer, I was using it because Windows crashed on my laptop (imagine that!) and wouldn't boot. Ironically, I have now reinstalled XP on my laptop, which is what I am typing this on right now. Sorry to turn this into a Windows forum, but I think you answered my original question (and more), so how do I mark this thread as resolved? Thanks a bunch!

---

### Post by CharlesA on 2010-09-23
> **candyman17 said:**
> Okay, I'll try that. I think /F is fix, but what is /V? It is a pretty old computer, I was using it because Windows crashed on my laptop (imagine that!) and wouldn't boot. Ironically, I have now reinstalled XP on my laptop, which is what I am typing this on right now. Sorry to turn this into a Windows forum, but I think you answered my original question (and more), so how do I mark this thread as resolved? Thanks a bunch!

/V is for verbose, so it'll tell you what file it is fixing or something.

You mark the thread as solved from the thread tools menu. :)

---

### Post by ST3ALTHPSYCH0 on 2010-09-24
Also, I have occasionally found that files that won't display in the file manager will still copy if you use the terminal. You're doing right by backing it up, now follow through by running a drive diagnostic from the hard drive manufacturer (you may need a second computer to do this. That will tell you definitively if the drive is dying and whether you should just buy a new drive. It would be a serious waste to take the time to chkdsk the drive only to have it totally fail next week.

---

