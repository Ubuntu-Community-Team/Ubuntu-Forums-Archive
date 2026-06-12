---
title: "Missing desktop, No right click, Can't open folder HELP!!"
date: 2010-02-08
forum: General Help
---

### Post by jman24 on 2010-02-08
Hi im running ubuntu 9.1 Karmic Koala and basically these are the symptoms my computer is having

All my desktop icons are gone.
I can right click in firefox but not anywhere on my desktop.
When I go to Places--->Home Folder or any other folder it will fail to open.
Firefox and other applications are running but not any of the folders found under places.

Any input would be appreciated...thanks

---

### Post by jman24 on 2010-02-12
bump..

---

### Post by jman24 on 2010-02-12
Anyone...? I can't access any of my previous files, I would really appreciate any input

---

### Post by Post Monkeh on 2010-02-12
hit alt & f2, hopefully you should get the run application dialogue.

enter gnome-terminal into it and hit enter, then in the terminal type ls and press enter, and see if it lists your files in your home folder.

---

### Post by jman24 on 2010-02-12
I did what you said and this is what I got
user@user-laptop:~$ ls
AAA.abw                Link to Folder
AAA.abw.bak~           list
adf.odt                movie
chem1boctb15.abw       Music
dec7~                  Nov18.odt
Desktop                Pictures
doc                    Public
Documents              Songbird
do it                  Songbird_1.2.0-1146_linux-i686.tar.gz
dothis.odt             Templates
dwhelper               todo
examples.desktop       to read
Firefox_wallpaper.png  to read~
Folder                 Ubuntu One
hs_err_pid10967.log    Unsaved Document 1
hs_err_pid11284.log    Videos
hs_err_pid11374.log    wget-log
hs_err_pid14404.log    wmv.full
hs_err_pid4610.log

Is there anyway I can access the files?

---

### Post by jman24 on 2010-02-12
I get this error when trying to open any folder except for word documents

user@user-laptop:~$ gnome-open Desktop
user@user-laptop:~$ 
(nautilus:3010): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

** (nautilus:3010): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:3010): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:3010): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Initializing nautilus-gdu extension

---

### Post by jman24 on 2010-02-13
I've looked through tons of posts but can't find much on this, is a fresh install the only option? I had a lot of files that I needed to keep :(

---

### Post by lenoirrichelieu on 2010-02-13
Open a terminal, enter in your home directory and there use
 
ls -a
 
This way you should see all files and folders including hidden ones. And give the results here.
 
If you want to be sure about files make a directory somewhere and copy all files there using
 
cp -r *.* /thebackupfolder

---

### Post by Chromagnum on 2010-02-13
Hit alt+F2 and type: nautilus, hit run and wait. It happens all the time with me if I kill nautilus on purpose: can't right click and desktop icons simply gone. 

I hope this one do the trick.

Regards,
Chromagnum

---

### Post by Post Monkeh on 2010-02-13
at least your files are still there by the looks of it. 

we're all presuming here that you have rebooted right?

---

### Post by jman24 on 2010-02-14
I tried ls -a and creating a back up folder suggested by lenoir and although I was able to see my files with ls -a creating a back up folder gave me this problem

cp: cannot create regular file `/home/Songbird_1.2.0-1146_linux-i686.tar.gz': Permission denied
cp: cannot create regular file `/home/wmv.full': Permission denied

Chromagnum suggested running nautilus and it still didn't change anything, I also tried running it in terminal and I got the error message in Post #5.

I haven't rebooted it yet, because I'm still hoping theres a chance that I can fix this and save those files.

Thanks for all the help :)

---

### Post by Surkow on 2010-02-14
If you want to backup your files you can always boot into a live cd and copy your files to a usb device. Just reboot to see if it works again. You won't lose your files from rebooting.

---

### Post by Chromagnum on 2010-02-15
I'm not an expert here. Been using Ubuntu for only about two months plus. But it seems to me your nautilus still running only with some errors.

How about this—just a little bit trial and error. First, "killall nautilus" and then call it back again.

---

### Post by Post Monkeh on 2010-02-15
> **jman24 said:**
> I tried ls -a and creating a back up folder suggested by lenoir and although I was able to see my files with ls -a creating a back up folder gave me this problem

cp: cannot create regular file `/home/Songbird_1.2.0-1146_linux-i686.tar.gz': Permission denied
cp: cannot create regular file `/home/wmv.full': Permission denied

Chromagnum suggested running nautilus and it still didn't change anything, I also tried running it in terminal and I got the error message in Post #5.

I haven't rebooted it yet, because I'm still hoping theres a chance that I can fix this and save those files.

Thanks for all the help :)

reboot. your files are on your hard drive, not in memory, you won't lose them by rebooting, and chances are you'll fiund a lot of your problems disappear after a reboot and getting your files will be easier

---

### Post by anoop999 on 2010-02-15
Does it work now?

---

### Post by jman24 on 2010-02-17
Well what I did was create a new user and oddly, the user was able to access all the folders and everything was working well. So I transferred my entire desktop and folders to the new username, the old profile is still damaged.

---

### Post by ChristopherB on 2010-02-18
> **jman24 said:**
> Well what I did was create a new user and oddly, the user was able to access all the folders and everything was working well. So I transferred my entire desktop and folders to the new username, the old profile is still damaged.

Once when I had trouble with certain features in Ubuntu I used the live CD go into your /home/**username** folder making sure that hidden files are visable.

Rename the file ".ICEauthority" to ".ICEauthority.bak" and then reboot.

Log-in as old user:

The system will recreate a new ".ICEauthority" file and then please let us know that you can now access the places necessary.

Christopher :)

---

