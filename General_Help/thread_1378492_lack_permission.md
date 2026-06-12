---
title: "lack permission"
date: 2010-01-11
forum: General Help
---

### Post by amber_lux on 2010-01-11
Can somebody explain to me [COLOR="Blue"]how somebody can be prevented[/COLOR] from opening, reading, or moving a file on a disk when [COLOR="Red"]all[/COLOR][COLOR="SeaGreen"] folders and files[/COLOR] on that disk have permissions set to [COLOR="Red"]"777"[/COLOR]?

Amber

Wind Under Thy Wings

---

### Post by SuperSonic4 on 2010-01-11
It could be because that file is not meant to be touched directly. /etc/sudoers is an example

---

### Post by Jackzor on 2010-01-11
Have you tried just opening nautilus as a super user?

gksudo nautilus

---

### Post by John Bean on 2010-01-11
Are the ownership and permissions of the* disk *set to allow anyone access to its contents?

---

### Post by t0p on 2010-01-11
> **amber_lux said:**
> Can somebody explain to me [COLOR=Blue]how somebody can be prevented[/COLOR] from opening, reading, or moving a file on a disk when [COLOR=Red]all[/COLOR][COLOR=SeaGreen] folders and files[/COLOR] on that disk have permissions set to [COLOR=Red]"777"[/COLOR]?


Can you please clarify the meaning of your question: are you asking *how is it possible that I was prevented from opening/reading/moving file a file on disk x?* Or are you asking *how can I prevent user y from opening/reading/moving a file on disk x?*

---

### Post by amber_lux on 2010-01-11
> **t0p said:**
> Can you please clarify the meaning of your question: are you asking [i]how is it possible that I was prevented from opening/reading/moving file a file on disk x?

I meant:

How it is possible that I was prevented from opening/reading/moving file a file on disk x?

Using command line "sudo cp file new_location/" came up with the same error message as "cp file new_location/" .


amber

Wind Under they  Wings

---

### Post by J V on 2010-01-11
and I'm guessing the error was file not found eh?

Paste terminal output please...

---

### Post by amber_lux on 2010-01-11
> **J V said:**
> and I'm guessing the error was file not found eh?

Paste terminal output please...

I'm a different system, but the error message was along the lines of "you do not have permission to read this file."  The system the error occurs is not networked. 

amber

Wind Under Thy Wings.

---

### Post by J V on 2010-01-11
so which one is causing it? new_location/ or file?

---

### Post by amber_lux on 2010-01-11
> **J V said:**
> so which one is causing it? new_location/ or file?

I was getting the same error message doing "cat filename" at both locations.

If I didn't mind losing another 1.5 TB of data, I'd simply wipe the drives, and reinstall Ubuntu. 

Amber

Wind Under Thy Wings.

---

### Post by Leppie on 2010-01-11
has another process locked the file?

---

### Post by amber_lux on 2010-01-12
> **Leppie said:**
> has another process locked the file?
Not that I can tell.  Rebooting the system, and trying results in the same error message: 
"You do not have permission to open this file". 
ls -al in that directory is -rwxrwxrwx  1  blah, blah, filenames and all that other stuff.

amber

---

### Post by warfacegod on 2010-01-12
Have you tried to chown the drive the files are on or the files themselves?

---

### Post by doas777 on 2010-01-12
so to clarify, you have 777 on both the source and the destination, right?

---

