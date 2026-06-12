---
title: "Secure Erase Of Hard Drive"
date: 2012-08-23
forum: General Help
---

### Post by alwayscarmen on 2012-08-23
I am using Ubuntu 10.04 LTS and recently deleted a large folder with personal data and then emptied the trash.

Is there a software application that can be used to secure the newly freed up space so that the data cannot be recovered?

Thank you

---

### Post by Stonecold1995 on 2012-08-23
Yes, there are several.  The easiest method is to use DD like this: ```
sudo dd if=/dev/zero of=blanked_space
```.  That will create a file called "blanked_space" that'll fill up all your free hard disk space.  Then simply delete the file and you'll be good.  If you wan't something slightly more secure but slower, replace "/dev/zero" with "/dev/urandom".

While this is able to erase free space so no one can find it, if you are worried about *future* technology which might enable recovery and/or nasty 3-letter acronyms that might (or might not) already have such technology, you can use a program called "sfill".  To install it, do this:
```
sudo apt-get install secure-delete
sudo sfill location/of/directory
```
This is overkill because it overwrites data many times, but it is extremely unlikely new technology will allow anyone to recover the data.  Note that sfill is also very slow, and can take hours to days on a large drive.

Overall, I'd just recommend using dd with either /dev/zero or /dev/urandom, and it'll be plenty secure for modern technology.

If you are using a solid-state drive, DO NOT use any secure deleting methods because it can wear out your drive and cause it to break sooner, plus SSDs have something called "wear-leveling" which prevents this from even working.

---

### Post by coldcritter64 on 2012-08-23
Bleachbit. To install from terminal, copy and paste the command,
```
sudo apt-get install bleachbit
```Run the program from its root launcher, there are 2 launchers, one for root and one for the user. There is a setting that can be checked in the "System" section called "Free disk space".  That should do what you want when it is run.

---

### Post by sandyd on 2012-08-23
> **alwayscarmen said:**
> I am using Ubuntu 10.04 LTS and recently deleted a large folder with personal data and then emptied the trash.

Is there a software application that can be used to secure the newly freed up space so that the data cannot be recovered?

Thank youNext time, try using ```
shred
```
to securely delete files and folders;)

---

### Post by coldcritter64 on 2012-08-23
> **sandyd said:**
> Next time, try using ```
shred
```to securely delete files and folders;)
Yes, shred is good and can be made into a launcher easily to "drag and drop" files onto, including multiple selections. With gnome classic the launcher can be put on the panels and files dragged and dropped onto it (what I use here for convenient "secure" file removal). 

Though I have noted using shred won't remove anything if a folder is dragged and dropped, only files directly. Don't know why that is :confused:

The contents of my shred.desktop file is below, it is stored in ~/.local/share/applications and its icon is stored in ~/.icons. 

```
#!/usr/bin/env xdg-open

[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Exec=shred --force --iterations=8 --zero --remove
Name=File Shredder
Comment=Secure file shredder, drag files onto this icon to remove. Use with CAUTION as files are totally unrecoverable after using this.
Icon=shred.png
NoDisplay=true
```8 passes and a zeroing pass is a bit extreme, 2 passes and a zero pass would probably be better, particularly where larger files are concerned.

---

### Post by Wim Sturkenboom on 2012-08-23
> **sandyd said:**
> Next time, try using ```
shred
```
to securely delete files and folders;)
Does that work on SSDs with wear leveling?

---

### Post by Stonecold1995 on 2012-08-23
> **Wim Sturkenboom said:**
> Does that work on SSDs with wear leveling?

No.  Not only do they not work, but they can damage the drive.  Also, all drives now days use wear leveling.  Using "sudo dd if=/dev/zero of=some_file" or "sudo dd if=/dev/zero of=/dev/sdx" can work if you are trying to blank the *whole* device, but it is also not very good for it.  If you are trying to securely delete specific files from an SSD then you're kind of screwed!

The best way to make sure data on an SSD doesn't get into the wrong hands is to encrypt it.  If the data is encrypted with a strong algorithm like AES or Serpent, then all you have to do is forget the password and the data will be very safe for a very long time.

---

### Post by Wim Sturkenboom on 2012-08-23
> **Stonecold1995 said:**
> No.  Not only do they not work, but they can damage the drive.  Also, all drives now days use wear leveling.  Using "sudo dd if=/dev/zero of=some_file" or "sudo dd if=/dev/zero of=/dev/sdx" can work if you are trying to blank the *whole* device, but it is also not very good for it.
Do you have a link that explains why those two examples are not very good for a SSD? Or can you explain to me?

I know what the effect of wear leveling is, have a slight idea how it works, but that is where it ends. And yes, I understand why 'shred' does not work in this scenario.

---

