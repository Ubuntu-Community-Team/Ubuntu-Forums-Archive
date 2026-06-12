---
title: "Adding to repository"
date: 2010-05-13
forum: General Help
---

### Post by bigseb on 2010-05-13
I would like to install a program called VariCAD. I downloaded the install file (full file name: varicad2010-en_2.06_amd64.deb) but was wondering if one couldn't somehow do this via the repository, kind of like I did for my nvidia drivers? Is it possible?

---

### Post by kevinatkins on 2010-05-13
Varicad is commercial software, so it won't be in the Ubuntu repositories. You'd need to check the Varicad website to see whether they have an Ubuntu (or Debian) repository for their products, but I doubt it.

It's no problem though - you can just go ahead and install the deb package you downloaded using dpkg -

```
sudo dpkg -i varicad2010-en_2.06_amd64.deb
```

The only downside to installing like this, as opposed to installing from a repository, is that APT won't be aware of any updates to Varicad as they become available.

---

### Post by bigseb on 2010-05-13
> **kevinatkins said:**
> Varicad is commercial software, so it won't be in the Ubuntu repositories. You'd need to check the Varicad website to see whether they have an Ubuntu (or Debian) repository for their products, but I doubt it.

No, they don't.


> **kevinatkins said:**
>  ```
sudo dpkg -i varicad2010-en_2.06_amd64.deb
``` 

I'm a relative newcomer to Linux, code like that always confuses me. Do I type EXACTLY what you've written or what? Where do I put the downloaded .deb? 


> **kevinatkins said:**
> The only downside  to installing like this, as opposed to installing from a repository, is  that APT won't be aware of any updates to Varicad as they become  available.

That's fine as updates need to be purchased, just like the software. I only asked about the repository option as it takes care of the installation for me. Moving stuff and reconfiguring this and that, etc is still abit of a mystery to me :(

Thanks

---

### Post by howefield on 2010-05-13
> **bigseb said:**
> I'm a relative newcomer to Linux, code like that always confuses me. Do I type EXACTLY what you've written or what? Where do I put the downloaded .deb?

Doesn't matter where you have put the file, let's say it is in your Downloads folder.

Open a terminal (Applications > Accessories > Terminal) and type

```
cd Downloads
```

Then enter the command kevinatkins gave, probably easiest to copy and paste to avoid mistakes.

Couple of points to note, linux is case sensitive, so Downloads is different to downloads, and second when you start typing the file name you can press the tab key to auto complete the file name, again can save time and cut down on typos.

Just to add, as a .deb package, you could most likely double click the file to start the install process.

---

### Post by kevinatkins on 2010-05-13
The other option would be to double-click on the downloaded deb package which will open up the graphical GDebi installer if you're not comfortable using the command line.

But if you want to give the command line a try, you can open a terminal (Applications -> Accessories -> Terminal) and enter the command I showed earlier.

---

### Post by bigseb on 2010-05-13
Great stuff guys. Thanks a bunch.

---

### Post by bigseb on 2010-05-13
UPDATE:

The terminal method didn't work (very weird that) but double-clicking the .deb did.

I is sorted!  \\:D/

---

