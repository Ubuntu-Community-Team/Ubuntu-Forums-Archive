---
title: "how to copy"
date: 2011-02-03
forum: General Help
---

### Post by L Style on 2011-02-03
I got a file "singlsish.mim", I want to copy this file to /usr/share/m17n this folder, I can't copy this, when I tried to copy this file. this message displayed 

Error while moving "singlish.mim".
There was an error moving the file into /usr/share/m17n.
Error moving file: Permission denied

how can I copy this file

---

### Post by piquat on 2011-02-03
> **L Style said:**
> I got a file "singlsish.mim", I want to copy this file to /usr/share/m17n this folder, I can't copy this, when I tried to copy this file. this message displayed 

Error while moving "singlish.mim".
There was an error moving the file into /usr/share/m17n.
Error moving file: Permission denied

how can I copy this file

You'd have to have root permissions to write to /usr/share.

You can get those by prefacing your commands with sudo in the terminal.

```
sudo mkdir /usr/share/m17n
```That would create the directory.

```
sudo mv /originating/directory/singlsish.mim /usr/share/m17n
```That would move the file.  When asked for a password, use your own.  Of course, replace "/originating/directory/" with the location of the file.  I have no idea where you have it on your machine...

Hope this helps.

---

### Post by matt_symes on 2011-02-03
Hi

You can also do this using nautilus file manager if you don't like the command line (but both will work)

Press the ALT and F2 keys together and enter

```
gksudo nautilus
```

and enter your password as normal. This will open nautilus with root permissions so you have to be _very_ careful as you can do almost anything to the hard drive including deleting important system files.

Create the new directory in /usr/share as you would in your home directory. Navigate to the file's directory and copy the file as normal. Right click->copy. Move to the new directory and right click->paste to paste the file.

Close nautilus as soon as you have finished so you don't inadvertently damage your system files. *this is important*

Kind regards

---

### Post by L Style on 2011-02-03
> **piquat said:**
> You'd have to have root permissions to write to /usr/share.

You can get those by prefacing your commands with sudo in the terminal.

```
sudo mkdir /usr/share/m17n
```That would create the directory.

```
sudo mv /originating/directory/singlsish.mim /usr/share/m17n
```That would move the file.  When asked for a password, use your own.  Of course, replace "/originating/directory/" with the location of the file.  I have no idea where you have it on your machine...

Hope this helps.

thnx bro, It's solved

---

