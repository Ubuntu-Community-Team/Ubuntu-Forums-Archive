---
title: "Permission denied"
date: 2011-05-11
forum: General Help
---

### Post by cannuck1964 on 2011-05-11
Hi,

I just installed 10.07 and trying to install a license for an editor that I use.  I need to make the file executable.

Opened terminal.

I tried using sudo chmod +x filename.bin

This prompted me for a password.

Entered.

new prompt, so I tried to run the file by using ./filename.bin

This gives an error :

bash: ./filename.bin: Permission denied

sort of stuck until I get this going...

any thoughts?


thanks.

Peter

---

### Post by WorMzy on 2011-05-11
You're trying to install a license? That's different.

Anyway, what architecture are you running, and which architecture is the file designed to be run on?

You can find out by running
```
arch
```
and
```
file /path/to/filename.bin
```

---

### Post by cannuck1964 on 2011-05-11
> **WorMzy said:**
> You're trying to install a license? That's different.

Anyway, what architecture are you running, and which architecture is the file designed to be run on?

You can find out by running
```
arch
```and
```
file /path/to/filename.bin
```


arch =  x86_64


I am in the folder where the file resides, so I used the ./filename.bin

I try to change the permissions and it is not working.  I check the file through dauphin and it shows that the file is not executable.

not sure why...

The script just sets up a code that is read by the editor, their documentation reads as follows:

> 
To install a Permanent license:  
[LIST]
[*]Download the license installer from the page.
[*]Change the permissions on the downloaded file to   allow execution (e.g. `chmod +x   Komodo_<version>_<license#>.bin`)
[*]Run the installer (e.g.   `./Komodo_<version>_<license#>.bin`).
[/LIST]



this was done....just no luck....

---

### Post by WorMzy on 2011-05-11
What does ```
file ./filename.bin
``` show?

Oh, and if the execute permission isn't sticking, then you may have downloaded it to an NTFS or FAT partition; neither of these filesystems support Linux permissions, so copy/move the file to a Linux filesystem and try again.

---

### Post by cannuck1964 on 2011-05-11
> Komodo-IDE-4-Linux-x86-S318B0E0B2.bin: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.2.5, dynamically linked (uses shared libs), stripped  I have installed this before on Ubuntu 64

---

### Post by cannuck1964 on 2011-05-11
> Oh, and if the execute permission isn't sticking, then you may have  downloaded it to an NTFS or FAT partition; neither of these filesystems  support Linux permissions, so copy/move the file to a Linux filesystem  and try again.Thank you, that did the trick :)


cheers

---

### Post by WorMzy on 2011-05-11
If you haven't already done so, you'll probably need ia32-libs before you can run that file.

```
sudo apt-get install ia32-libs
```

EDIT: Oh, looks like it was just the filesystem. Well, glad you got it sorted. :)

---

