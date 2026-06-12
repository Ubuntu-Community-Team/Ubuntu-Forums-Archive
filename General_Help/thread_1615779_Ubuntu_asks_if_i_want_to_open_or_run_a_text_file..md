---
title: "Ubuntu asks if i want to open or run a text file."
date: 2010-11-07
forum: General Help
---

### Post by kniwor on 2010-11-07
I do not want the prompt. If I wanted to execute the file, I would do so in the terminal. If I double-click the file, I just want to view and edit it's contents in a text editor of my choice. This happens with almost all text files, whatever the extension. How do I get ubuntu to display the files directly when I double click on them, rather than show this prompt:

[IMG]http://img829.imageshack.us/img829/3361/screenshotlw.png[/IMG]

---

### Post by dino99 on 2010-11-07
you might try to find this weird "executable txt file" with nautilus then delete it if you are not sure about what it is.

run clamav (into synaptic repo) to check about virus

---

### Post by viktorzk on 2010-11-07
You should only get this prompt when the file you are opening is marked  as executable. If you right click on it and select 'Properties', then  'Permissions', there is an 'Allow executing file as program' checkbox. Untick it, and the file will become a normal text file - but you won't be able to execute it from terminal either.

Files created in Windows are normally marked as executable by default.

---

### Post by Jetro on 2010-11-07
*delete*

---

### Post by kniwor on 2010-11-07
Let us forget about the virus issue for a bit, these are my own self generated files.

Ther files are mostly files created in windows, and now that I am moving to Ubuntu full time, this is being a bit of a pain. I already tried unckecking the "Allow executing file as program", it doesn't allow me to do that. Also I tried
```
chmod -x exp_repeated_sample.R
chmod 555 exp_repeated_sample.R
```

Doesn't change anything, "ls -al" shows me the same file permissions. Now I must remind you that the files are on a NTFS partition.

---

### Post by oldfred on 2010-11-07
NTFS does not support Linux file permissions or ownership.

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

I had to modify the settings on my NTFS partiton:
defaults,[COLOR=Red]noexec[/COLOR],nosuid,locale=en_US.UTF-8

---

### Post by viktorzk on 2010-11-07
post deleted

---

### Post by mc4man on 2010-11-07
Open File management and adjust under behavior

one of several ways to open - from terminal
```
nautilus-file-management-properties
```

Edit; for whatever nonsense reason File management is not enabled in the System - preferences menu by default. Being quite useful you can do so thru Edit Menus (or "Main Menu" in system- preferences

---

### Post by gandaran on 2010-11-07
> **kniwor said:**
> I do not want the prompt. If I wanted to execute the file, I would do so in the terminal. If I double-click the file, I just want to view and edit it's contents in a text editor of my choice. This happens with almost all text files, whatever the extension. How do I get ubuntu to display the files directly when I double click on them, rather than show this prompt:

[IMG]http://img829.imageshack.us/img829/3361/screenshotlw.png[/IMG]
easy, just go to nautilus » edit » preferences » 'second tab' 
on executable text files change the option to view files.

---

### Post by kniwor on 2010-11-07
@mc4man and gandaran
Exactly the answer I was looking for, thanks. 

@oldfred
Thank you for the info, that helps me further.

---

