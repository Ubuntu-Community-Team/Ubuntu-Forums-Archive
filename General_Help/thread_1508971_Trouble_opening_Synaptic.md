---
title: "Trouble opening Synaptic"
date: 2010-06-13
forum: General Help
---

### Post by doubleOneg on 2010-06-13
[I]I am new to UBUNTU and mostly to computers. I downloaded cairo dock the other day and shortly after I went into synaptic to install another program and got this error message. E: Type 'usage:' is not known on line 36 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.


I have searched the froum and found some answers but unfortunately alot of the terms used on the froum are above my head. So if anyone could point me in the right direction that would be awesome. Thanks
[/I]

---

### Post by hhoyt on 2010-06-13
You are going to have to look at your sources.list file and possibly temporarily comment out the errant line by putting a pound sign as the first char of the line.

sudo gedit /etc/apt/sources.list

Cheers, Howard

---

### Post by howefield on 2010-06-13
> **hhoyt said:**
> sudo gedit /etc/apt/sources.list

You might want to make that

```
gksudo gedit /etc/apt/sources.list 
```

---

### Post by hhoyt on 2010-06-13
If all else fails
sudo gedit /etc/apt/sources.list
copy sources.list to your clipboard
and paste to this thread so we can see what is
in the list.

Howard

---

### Post by howefield on 2010-06-13
> **hhoyt said:**
> sudo gedit /etc/apt/sources.list

And again.

You might want to make that

```
gksudo gedit /etc/apt/sources.list 
```

Using graphical applications, (gedit in this case) with elevated rights should be done with gksudo, not sudo.

---

### Post by doubleOneg on 2010-06-13
This is what line 36 looks like when I pull up my source list
usage: sudo -h | -K | -k | -L | -V

If this is not correct what should it be and how do I change it?

---

### Post by howefield on 2010-06-14
> **doubleOneg said:**
> This is what line 36 looks like when I pull up my source list

I'd rather see what's around that line as well, but if you put a # sign in front of that line and save the file, then try Synaptic again, it should be ok.

The hash sign comments out the line so it won't be used, you can probably see other lines in your sources.list that start with #. This signifies that the line is a comment rather than a "source" that needs to be read by the application.

---

