---
title: "Mounting C:\ drive"
date: 2009-07-23
forum: General Help
---

### Post by Kredible on 2009-07-23
I suppose this is a far simpler issue than my other thread regarding the boot. Is it possible so whenever I get into the desktop to have my VISTA partition mounted? For instance, I have a shortcut to my projects folder which I work in (wheather it's ubuntu or vista) but it's pointing to /media/VISTA, and if I launch the shortcut before 'mounting' the VISTA drive (by simply clicking it on 'Local' > 'VISTA' I get an error 'bla bla unable to find...' It's no big deal I know but then all other apps like LAMPP rely that VISTA is mounted, and woops forgot to click the device again!

I believe I have to right click on the drive and then go to mount options, but then...don't know.

Thanks for your time!

---

### Post by DeMus on 2009-07-23
> **Kredible said:**
> I suppose this is a far simpler issue than my other thread regarding the boot. Is it possible so whenever I get into the desktop to have my VISTA partition mounted? For instance, I have a shortcut to my projects folder which I work in (wheather it's ubuntu or vista) but it's pointing to /media/VISTA, and if I launch the shortcut before 'mounting' the VISTA drive (by simply clicking it on 'Local' > 'VISTA' I get an error 'bla bla unable to find...' It's no big deal I know but then all other apps like LAMPP rely that VISTA is mounted, and woops forgot to click the device again!

I believe I have to right click on the drive and then go to mount options, but then...don't know.

Thanks for your time!

Try this:

[COLOR="Red"]**Auto mount Windows disks**[/COLOR]
Fire up a terminal, to do this click Applications > Accessories > Terminal
Then type (or copy/paste) the following - 1 line at a time
```

sudo aptitude update
sudo aptitude install ntfs-config
```
Ok so when that returns you to user@pcname, that should be installed                 

Next, make sure you have NO drives mounted (they'll usually appear on your desktop). If you have disks mounted, right-click the icons (one by one) and choose unmount.
They also appear when opening Nautilus.
Then run the program from System > Administration > NTFS Configuration Tool

Enter your password when prompted - and choose the drives that you want to be automounted. Click Apply.

Now simply make sure that "Enable Write Support for Internal Drives" is checked and click OK.

---

### Post by Kredible on 2009-07-23
Thank you very much! It worked, pretty easy to follow instructions :)

---

