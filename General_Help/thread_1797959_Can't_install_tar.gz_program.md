---
title: "Can't install tar.gz program"
date: 2011-07-05
forum: General Help
---

### Post by zapp7 on 2011-07-05
I downloaded a program called MedINRIA with extension tar.gz. I extracted it using tar, and all there is inside the archive is an executable called MedINRIA. Double-clicking it does nothing, and when I try to run it from the terminal it says MedINRIA: command not found.

I am completely new to Ubuntu so any help would be appreciated.

---

### Post by Archy1987 on 2011-07-05
$ su -
# cd /tmp
# tar -jxvf NAME_OF_YOUR_ARCHIVE.tar.bz2 -C /opt/

This will work, if your archive is located in tmp folder

---

### Post by zapp7 on 2011-07-05
This gave me:

bzip2: (stdin) is not a bzip2 file.
tar: Child returned status 2
tar: Error is not recoverable: exiting now

---

### Post by spiky001 on 2011-07-05
xvzf for a tar.gz

---

### Post by zapp7 on 2011-07-05
Now I get:

./MedINRIA: error while loading shared libraries: libtiff.so.3: cannot open shared object file: No such file or directory

Never thought that running a program would be so difficult lol.

---

### Post by charliewhizbeez on 2011-07-05
You have to install it from source.  I was never very good at it, so google it.  It should work fine.

---

### Post by smurphy_it on 2011-07-05
```
ldd medrina
```

That should list all of the "shared libraries" you need.  Next install apt-file.

```
sudo apt-get install apt-file
sudo apt-file update
```

For any shared libraries, you have a problem with do a search for them with apt-file.

example:

```
sudo apt-file search libtiff.so.3
```

---

