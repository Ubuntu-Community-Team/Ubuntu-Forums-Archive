---
title: "Help with installing Unreal Tournament 2004"
date: 2010-10-28
forum: General Help
---

### Post by DirtyPC on 2010-10-28
Hi all, theres loads of other threads here with the same problem, but none solved properly so....
I want to know how to install unreal 2k4 from a virtual iso, not a disc, not with wine.. with the linux-installer.sh. I copied it from my iso and put it into the desktop, opened up terminal, but everything i've tried just says no permissions, but when i overcame that problem it just says insert proper disc, and obvioulsy i cant because its and ISO i need help before i kill myself!!!

---

### Post by janpol on 2010-10-28
Maybe if you try to mount it?

A nice tool to do that with the GUI is gmountiso 

```
sudo apt-get install gmountiso 
```

---

### Post by DirtyPC on 2010-10-28
> **janpol said:**
> Maybe if you try to mount it?

A nice tool to do that with the GUI is gmountiso 

```
sudo apt-get install gmountiso 
```
Yes.. I am using FuriusISO

but thanks anyway

---

### Post by sikander3786 on 2010-10-28
You don't need to open it up in terminal. Just mount it as suggested in the above post. You can search for 'disc mount' in Software Center for more results but the one's that work for me are gmountiso and acetone-iso.

You'll find gmountiso under Applications > System Tools. Not difficult to use it from there.

Once the image is mounted, navigate to the setup.exe file and double click it. It should open up in wine and let you install as if you were installing on Windows.

If double clicking gives any errors, right click the file > Properties > Permissions and tick Allow executing as program and you are done.

---

### Post by DirtyPC on 2010-10-28
> **sikander3786 said:**
> You don't need to open it up in terminal. Just mount it as suggested in the above post. You can search for 'disc mount' in Software Center for more results but the one's that work for me are gmountiso and acetone-iso.

You'll find gmountiso under Applications > System Tools. Not difficult to use it from there.

Once the image is mounted, navigate to the setup.exe file and double click it. It should open up in wine and let you install as if you were installing on Windows.

If double clicking gives any errors, right click the file > Properties > Permissions and tick Allow executing as program and you are done.
It would be easier if you just read the thread first.

---

### Post by sikander3786 on 2010-10-28
> it just says insert proper disc

If thats the case, you need a licensed disc to play it.

---

### Post by DirtyPC on 2010-10-28
> **sikander3786 said:**
> If thats the case, you need a licensed disc to play it.
No I don't, i've seen it done somewhere, probably youtube
I did it myself using the terminal command with sudo sh running the linux-installer.sh file located within the ISO

---

### Post by janpol on 2010-10-28
> **harrylucas1 said:**
> ... with the linux-installer.sh. **_I copied it from my iso_** and put it into the desktop, opened up terminal, but everything i've tried just says no permissions, but when i overcame that problem it just says insert proper disc.....
Just to be shure, did you copied the linux-installer.sh to your desktop and tried to open it from there?

Have you tried to run it from the mount point?

Also, be shure to give the apropiate permissions to the mounted files.

If that doesn't work, maybe the script is trying to look for the files in the default folder for mounting the cdrom. Try to mount your ISO in that folder.

---

### Post by janpol on 2010-10-28
I've found a guide in Spanish that might help:  [http://ociolinux.blogspot.com/2008/01/instalar-unreal-tournament-2004-en.html]("http://ociolinux.blogspot.com/2008/01/instalar-unreal-tournament-2004-en.html")

Here are the main instructions:

1. Mount the ISO

2. Run the following:

```
sudo export SETUP_CDROM=/iso_mount_point
```

Where iso_mount_point is the path to the folder you used to mount the iso.

3. Copy linux-installer.sh to your personal folder

4. Give it the apropiate permissions and run:

```
sudo sh ./linux-instaler.sh
```

Hope it helps!

---

### Post by DirtyPC on 2010-10-28
Thanks, its been solved now, but giving it the permissions was the part that was giving me trouble..

---

