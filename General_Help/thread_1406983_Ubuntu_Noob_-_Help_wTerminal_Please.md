---
title: "Ubuntu Noob - Help w/Terminal Please?"
date: 2010-02-14
forum: General Help
---

### Post by formengr on 2010-02-14
hiya. 1st post here. this is probably pretty rudimentary...

I have .sit files to decompress and found [this]("http://ubuntuforums.org/showthread.php?t=47226") apparently useful thread and am clueless about how to actually run this software.  i tried to copy/paste the "sudo cp unstuff /usr/bin" command into a terminal (which i only moments ago figured out how to open a terminal!) after dl'ing the proggy, but it gives me this response: "No such file or directory". the unstuff file is on my desktop. the .sit files are on a separate, accessible drive.  help? the more descriptive, the better.  :)  thanks!

--> edited  the response i got (pasted the wrong thing)...

---

### Post by bruno9779 on 2010-02-14
ok, first navigate to /usr/bin and make sure that unstuff is there.

now you should be able to unstuff by :

```
unstuff /path/to/file.sit
```

it seems like you cannot unstuff .sitX

---

### Post by formengr on 2010-02-14
> **bruno9779 said:**
> ok, first navigate to /usr/bin and make sure that unstuff is there.

now you should be able to unstuff by :

```
unstuff /path/to/file.sit
```

it seems like you cannot unstuff .sitX
files are .sit. i typed "/usr/bin" in the terminal and get this response: "bash: /usr/bin: is a directory" and i donot know if that's good or bad... how do i make sure that "unstuff is there". again the unstuff file is on the desktop.

again, not to be a pain, but the more detail as to what i need to do the better. i am a total noob to this and have no idea how to assure things are where they should be.  thanks!

---

### Post by mechro on 2010-02-14
Copy the unstuff binary file directly in to your Desktop then the command should be...

/home/username/Desktop/unstuff /path/to/file.sit

---

### Post by Surkow on 2010-02-14
You can graphically navigate to "/usr/bin" and search for "unstuff" with nautilus (the file manager).

---

### Post by mechro on 2010-02-14
You could copy the unstuff binary to it's "preferred" location (/usr/bin) with Nautilus...

In a Terminal do **gksudo nautilus**

After you've entered your password, Nautilus will open with root privileges and you can copy the unstuff binary from your Desktop to the /usr/bin/ directory.

---

### Post by tekkidd on 2010-02-14
> **bruno9779 said:**
> ok, first navigate to /usr/bin and make sure that unstuff is there.

now you should be able to unstuff by :

```
unstuff /path/to/file.sit
```

it seems like you cannot unstuff .sitX

thats exactly how you do it

---

