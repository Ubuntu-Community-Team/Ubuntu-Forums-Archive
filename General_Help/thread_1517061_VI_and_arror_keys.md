---
title: "VI and arror keys"
date: 2010-06-24
forum: General Help
---

### Post by cjtemple on 2010-06-24
I am not sure if this is a result of the compatiblity issue with VMWare or not but when I open a terminal and use VI I can't really use the arrow keys. I get letters instead of the cursor moving
 
Up Arrow -> A
Down Arrow -> B
Right Arrow -> C
Left Arrow -> D
 
Am I totally navigating around in VI the wrong way or is it possibly something else?
 
Configuration:
VMWare Workstation 7.0.1
Host: XP Pro SP3 32-bit
Guest: Ubuntu 10.04 (with VMWare tools installed)
 
Hardware:
Acer Extensa 4620Z
Dual Core Intel T2330 1.60GHz
2GB RAM
 
The VM is configured with 1 Processor, 512MB RAM, and 20GB HDD.

---

### Post by VH-BIL on 2010-06-24
I found a link that might help
[http://linuxblog.pansapiens.com/2007/10/31/fixing-the-arrow-keys-in-vim/](http://linuxblog.pansapiens.com/2007/10/31/fixing-the-arrow-keys-in-vim/)

Basically it says:
> Are your Vim / Vi arrow keys making A,C, B etc characters instead of moving around in insert (’i') mode ?

Try typing this … it fixes it for me:

:set nocompatible

Or, add the line:

set nocompatible

to your ~/.vimrc file.

---

### Post by cjtemple on 2010-06-24
Excellent!!!
 
Thank you.
I ended up creating a .vimrc config file and added a host of options, that I found here:
 
[http://jmcpherson.org/vimrc.html](http://jmcpherson.org/vimrc.html)

---

### Post by SoFl W on 2010-06-24
Wow, I started using vi again tonight and was having this same problem.  Thank you.

---

### Post by VH-BIL on 2010-06-24
Im glad it is fixed. Do you think vi is better then nano?

---

### Post by cjtemple on 2010-06-25
I can't really say that vi is any better than nano. I haven't used nano in years, mostly vi as of late so I have become a little more comfortable with it.

---

### Post by VH-BIL on 2010-06-25
I just thought nano was easier to use. I have not really used vi.

---

### Post by cjtemple on 2010-07-02
I took a look at nano this morning. I remember that I liked how it displayed a menu of options like cut, copy, paste, find. In vi you have to just remember the keys to use. 
 
But one thing I noticed, is it possible to force nano to write to a read only file. In vi I can use the w! and force it to write to a read only file. Which is great for the times that I have to modify a config file.

---

