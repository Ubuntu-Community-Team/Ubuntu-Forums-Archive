---
title: "Mount ISO"
date: 2009-08-13
forum: General Help
---

### Post by KlinerDraken on 2009-08-13
Is there a way to mount an ISO file from the right click context menu?

---

### Post by Revolutionary101 on 2009-08-13
Maybe but I don't know how. Although you can extract the files in an ISO and extract the files from it with Archive Manager by double clicking it.

---

### Post by matthewbpt on 2009-08-13
look here [http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html](http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html)

---

### Post by KlinerDraken on 2009-08-13
> **Revolutionary101 said:**
> No but you can extract the files in an ISO and extract the files from it from Archive Manager.

I would do that, but this is for video DVDs that I want to watch with out extracting or burning to a disk. And I am lazy and don't want to mount from the terminal all the time.

> **matthewbpt said:**
> look here [http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html](http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html)

I've done this but for some reason I can't get Nautilus scripts to run. :confused:

---

### Post by burmanabhay88 on 2009-08-13
there's a software called "G mount iso". It's available in the add-remove programs, in the system tools section.

---

### Post by tgeer43 on 2009-08-13
> I've done this but for some reason I can't get Nautilus scripts to run. :confused:Did you make sure to make the mount and unmount scripts executable? You can use chmod +ax on them or right-click in nautilus and select Properties->Permissions. I can't think of any other good reason why nautilus scripts would not run.

tgeer

---

### Post by KlinerDraken on 2009-08-13
> **burmanabhay88 said:**
> there's a software called "G mount iso". It's available in the add-remove programs, in the system tools section.

Thanks, but not exactly what I am looking for. Just seems a little extreme to have a whole program just to mount an ISO file IMHO.

---

### Post by KlinerDraken on 2009-08-13
> **tgeer43 said:**
> Did you make sure to make the mount and unmount scripts executable? You can use chmod +ax on them or right-click in nautilus and select Properties->Permissions. I can't think of any other good reason why nautilus scripts would not run.

tgeer

[email]ben@UbuntuHome:~/.gnome[/email]2/nautilus-scripts$ ls -l
total 12
-rwxr-xr-x 1 ben ben 201 2009-05-03 20:20 ExtractTo.py
-rwxr-xr-x 1 ben ben 844 2009-08-13 11:30 iso_Mounter
-rwx--x--x 1 ben ben  68 2009-01-11 09:45 Open with gedit(as root)


I can't figure it out either, they were working in 8.10 then when I upgraded to 9.04 the stopped working. I even reinstalled Ubuntu with no change.
Here is the script that I am using if anyone can test to see if it work for them that would be great, idk maybe its a script issue?

```
#!/bin/bash
#
# adapted from: http://ubuntu.wordpress.com/2005/10/24/nautilus-script-to-mount-iso-files/
#
if (/usr/bin/gksudo -u root -k -m "enter your password to gain root privleges" /bin/echo "getting root"); then
for i in `/bin/echo $*`; do
    if (/bin/mount | /bin/grep "$i"); then
    # disk is mounted, umount
        if ! (/usr/bin/sudo /bin/umount /media/"$i" &amp;&amp; /usr/bin/sudo /bin/rmdir /media/"$i"); then
            /usr/bin/zenity -error -text="cant umount /media/$i and/or rmdir /media/$i"
            exit 1
        fi
    else
    # disk isn&#8216;t currently mounted
   if ! (/usr/bin/sudo mkdir /media/"$i" &amp;&amp; /usr/bin/sudo /bin/mount -o ro,loop -t iso9660 "$i" /media/"$i"); then
       /usr/bin/zenity -error -text="can&#8217;t mkdir /media/$i and/or mount $i"
       exit 1
   fi
   fi
done
exit 0
else
exit 1
fi
```

---

### Post by Bonster on 2009-08-13
Best one [http://www.getdeb.net/app/AcetoneISO](http://www.getdeb.net/app/AcetoneISO)

---

### Post by tgeer43 on 2009-08-13
If you even suspect that it may be a script issue then try testing with a very simple script that is known to be error free, like a one-liner that beeps the pc speaker.

tgeer

---

### Post by KlinerDraken on 2009-08-14
> **tgeer43 said:**
> If you even suspect that it may be a script issue then try testing with a very simple script that is known to be error free, like a one-liner that beeps the pc speaker.

tgeer

:confused: I'm not much of a programer, if anyone has a small script that is know to work in Ubuntu 9.04 I would like the code so I can try it on my computer.

---

### Post by tgeer43 on 2009-08-14
I can do you one better. Here are my mount and unmount scripts.
Just copy and paste each one into your favorite text editor and save them to ~/.gnome2/nautilus-scripts.

Here's mount_ISO.sh:

```
#!/bin/bash

# mount
gksudo -k /bin/echo "got r00t?"
BASENAME=`basename $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS .iso`
sudo mkdir "/media/$BASENAME"
zenity --info --title "ISO Mounter" --text "$BASENAME e $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS"
if sudo mount -o loop -t iso9660 $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS "/media/$BASENAME"
then
if zenity --question --title "ISO Mounter" --text "$BASENAME Successfully Mounted. Open Volume?"
then
nautilus /media/"$BASENAME" --no-desktop
fi
exit 0
else
sudo rmdir "/media/$BASENAME"
zenity --error --title "ISO Mounter" --text "Cannot mount $BASENAME!"
exit 1
fi
```And here's unmount_ISO.sh:

```
#!/bin/bash

# unmount
gksudo -k /bin/echo "got r00t?"
BASENAME=`basename $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS .iso`
sudo umount "/media/$BASENAME"
sudo rmdir "/media/$BASENAME"
zenity --info --text "Successfully unmounted /media/$BASENAME"
exit 0
```I've been using them for a while with no issues. After successfully mounting the ISO, it will prompt you and if you answer "Y" it will open it in a new nautilus window. You could modify the script if you don't want any interaction or feedback.

Let us know how it turns out,

tgeer

---

### Post by tgeer43 on 2009-08-20
Well? Don't keep us in suspense. :wink:

---

