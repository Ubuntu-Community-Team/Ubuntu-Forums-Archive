---
title: "tar.gz file"
date: 2009-07-15
forum: General Help
---

### Post by cowboy7305 on 2009-07-15
tar -zxvf X-Lite_Install.tar.gz 
this is from the readme file from x-lite softphone ,i have put this into terminal and it does not load tells me the file does not exist.the file is on my desktop,its for using with voip

---

### Post by lisati on 2009-07-15
You need change directory to the directory/folder where you downloaded the file first.

---

### Post by t0p on 2009-07-15
> **lisati said:**
> You need change directory to the directory/folder where you downloaded the file first.

As you said it's in your Desktop directory, you change to it with:

```
cd Desktop
```

or possibly

```
cd ~/Desktop
```

---

### Post by sanderj on 2009-07-15
Or, the GUI-way:

double click on the file in your Firefox download popup windows, and unpack it.

or, another GUI-way:

Use Nautilus (the file browser) to locate / find the file, and then double click on it, and unpack it.

---

### Post by 3rdalbum on 2009-07-15
X-lite is an SIP-based softphone - you could use another SIP-based softphone of which there are a few in the repositories.

If you must get this piece of proprietary software working, then unpack the archive by double-clicking it. You will probably need to switch to root and then run the binary installer (if it installs), so open a terminal after unpacking the archive and do this:

```
sudo su
```

After typing your password, drag the binary installer to the terminal to fill-out the command, and then run it.

---

### Post by cowboy7305 on 2009-07-15
Many thanks for help 
I downloaded ARK and tried that it seems to have done the trick

---

