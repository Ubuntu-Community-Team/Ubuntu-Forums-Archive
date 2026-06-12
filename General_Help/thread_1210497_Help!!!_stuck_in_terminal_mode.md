---
title: "Help!!! stuck in terminal mode"
date: 2009-07-11
forum: General Help
---

### Post by Daremo_06 on 2009-07-11
system is coming up in terminal mode and when i type startx, i get the following

/usr/bin/x11/x: error while loading shared libraries: libcrypto.so.0.9.8: cannot open shared object file: no such file or directory.
giving up.
xinit: no such file or directory (errno 2): unable to connect to x server
xinit: no such process (errno 3): server error
xauth: error in locking authority file name /home/rob/.xauthority

Already tried dpgk reconfigure -phigh command for xserver no help

also tried reinstalling xserver also no help

---

### Post by ibutho on 2009-07-11
In the command line, try
```
sudo apt-get install libssl0.9.8
```
After that try running "startx".

---

### Post by ajgreeny on 2009-07-11
Just to check if you even have the file the error notes can you please login at the prompt with your username and password (pw will not show on screen) then ```
sudo updatedb
```then ```
locate libcrypto
```You should get a few lines of output, one of which will be the libcrypto.so.0.9.8, which in my case is provided by libssl0.9.8.  If you get no output it looks as if you need to install that so try ```
sudo apt-get install libssl0.9.8
```

---

### Post by Daremo_06 on 2009-07-11
> **ibutho said:**
> In the command line, try
```
sudo apt-get install libssl0.9.8
```
After that try running "startx".

I get this after installing...

Libssl0.9.8 is already newest version.

Startx still does not work.

The errors I am getting are these -

xauth: /home/rob/.xauthority not writable, changes will be ignored
xauth: error in locking authority file /home/rob/.Xauthority (this is repeated 2 more times)

Then the libcrypto error I mentioned in the beginning

Then xinit: server error

and 1 final authority error.

---

### Post by ibutho on 2009-07-11
Try the following
```
mv ~/.Xauthority ~/.Xauthority.backup
startx
```

---

### Post by Daremo_06 on 2009-07-11
> **ibutho said:**
> Try the following
```
mv ~/.Xauthority ~/.Xauthority.backup
startx
```

Ok that got rid of the Xauth errors.

I am still left with

/usr/bin/X11/X: error while loading shared libraries: libcryto.so.0.9.8 cannot open shared object file: No such file or directory
xinit: Server error

---

### Post by ibutho on 2009-07-11
> **Daremo_06 said:**
> Ok that got rid of the Xauth errors.

I am still left with

/usr/bin/X11/X: error while loading shared libraries: libcryto.so.0.9.8 cannot open shared object file: No such file or directory
xinit: Server error

Have you tried the suggestions in post 3?

---

### Post by Daremo_06 on 2009-07-11
> **ibutho said:**
> Have you tried the suggestions in post 3?

Yes, no change...

---

### Post by Daremo_06 on 2009-07-12
I gave up and am re-installing 9.04.

---

### Post by jskandhari on 2009-07-12
try typing "sudo gdm"
i hope it works....

---

