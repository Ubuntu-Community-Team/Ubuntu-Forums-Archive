---
title: "i made a backup iso of my bioshock cd a while ago and it wont mount"
date: 2010-02-14
forum: General Help
---

### Post by Espryon on 2010-02-14
i have this iso and i lost my cd but when i mount this the folder is empty but when i look inside the iso there is the install files

---

### Post by Espryon on 2010-02-14
.

---

### Post by Ahadiel on 2010-02-14
> **Espryon said:**
> i have this iso and i lost my cd but when i mount this the folder is empty but when i look inside the iso there is the install files

How did you create the iso? What command are you using to mount it?

---

### Post by Espryon on 2010-02-14
i dont remember is was a while ago but i am using furious iso mount to mount it

---

### Post by Ahadiel on 2010-02-14
> **Espryon said:**
> i dont remember is was a while ago but i am using furious iso mount to mount it

You might want to try mounting it from a terminal.
```
sudo mount /path/to/iso -o loop /place/to/mount
```

---

### Post by Espryon on 2010-02-14
i always have trouble manually mounting it is it like home/nameofuser/Desktop/ untitled\ folder\

---

### Post by Ahadiel on 2010-02-14
> **Espryon said:**
> i always have trouble manually mounting it is it like home/nameofuser/Desktop/ untitled\ folder\

Instead of escaping spaces/special characters, you can just enclose the path in "quotes".

---

### Post by pbrane on 2010-02-14
An easy way to duplicate a DVD/CD is with dd.
```

dd if=/dev/dvd of=filename.iso

```

This will create an iso image of the DVD or CD.

'if' is the input file(device), e.g., /dev/dvd or /dev/cdrom of /dev/sr0, etc
'of' is the output file, e.g., /home/user/dvdbackup/mydvdbackup.iso

Run this in a terminal. Type 'mount' to see where your DVD or CD is mounted.

---

### Post by Espryon on 2010-02-14
is this right sudo mount /home/sev/Desktop/untitled/folder/ 2 -o -loop /home/sev
?

---

### Post by Ahadiel on 2010-02-14
> **Espryon said:**
> is this right sudo mount /home/sev/Desktop/untitled/folder/ 2 -o -loop /home/sev
?

No.
```
sudo mount /path/to/foo.iso -o loop /folder/to/mount/it/to
```

---

### Post by Espryon on 2010-02-14
it doesnt work doing this  sudo mount /home/sev/Desktop/untitled folder 2/bioshock.iso -o loop /home/sev/Desktop

---

### Post by Ahadiel on 2010-02-14
> **Espryon said:**
> it doesnt work doing this  sudo mount /home/sev/Desktop/untitled folder 2/bioshock.iso -o loop /home/sev/Desktop

Try this:
```
mkdir /home/sev/Desktop/Bioshock
sudo mount "/home/sev/Desktop/untitled folder 2/bioshock.iso" -o loop /home/sev/Desktop/Bioshock
```

---

### Post by pbrane on 2010-02-14
or- 
```

sudo mount -o loop "/home/sev/Desktop/untitled folder 2/bioshock.iso" /home/sev/Desktop/Bioshock

```
make sure you mount to an existing directory. I have ~/mnt for that purpose.

If you cd to Desktop the command line is easier,
```

sudo mount -o loop "untitled folder 2/bioshock.iso" Bioshock

```

look at *man mount* for mount options and command syntax

---

### Post by sisco311 on 2010-02-14
> **Espryon said:**
> it doesnt work doing this  sudo mount /home/sev/Desktop/untitled folder 2/bioshock.iso -o loop /home/sev/Desktop

Use your file manager to create a new directory (mount point) where you want to mount the .iso file.

In a terminal type:
```
sudo mount -o loop
```
type a space & drag the .iso file in the terminal window, type another space and drag the directory you created earlier (the mount point) in the terminal & press Enter. Type in your password & press Enter.

---

