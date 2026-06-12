---
title: "How to redirect LPT? (net use on ubuntu?)"
date: 2010-11-23
forum: General Help
---

### Post by micael3000 on 2010-11-23
Hello,

I would like to know how can I redirect my LPT port to a printer... On windows you can use
[COLOR=#000000][FONT=Times New Roman][FONT=verdana]**net use lpt1: \\<computer ip>\printer_name**[/FONT][/FONT][/COLOR]
However it doesn't seem to work on ubuntu.

I have the printer installed on Ubuntu, I can print through it but I also need it working with LPT port (i mean, when i write on LPT1 it redirects to the printer)...


Thanks in advance!

---

### Post by cwa on 2010-11-23
I got a question, do you have the cups running on your system .

---

### Post by micael3000 on 2010-11-23
I don't... I don't even know what is it. (a simple google search made me know that it is a printing system, however i don't know how to use it at all)

---

### Post by cwa on 2010-11-23
I have something you can try. Sorry, not knowing for sure. Let me know if you want to know.

it involves using cups and symlinks.

---

### Post by cwa on 2010-11-23
maybe misunderstaning you a little.

if you can print to the printer, 

/dev/lp0 is the linux eqiv to lpt1  can creating a symlink work?

do you have software that needs to find lpt1?

cwa

---

### Post by efflandt on 2010-11-23
It might be easier to tell you how to do what you are trying to do if we knew "why" you are trying to do that.  Are you running an MS DOS program in an emulator or vm?  What type of printer, and is it directly connected to the network with ethernet or wireless, or a printer on a Windows PC?

Most Linux versions currently use cups for printing by default.  You would typically set that up from System > Administration > Printing (or [http://localhost:631](http://localhost:631) ).  But if it is a Windows shared printer you may need to configure something with samba, and/or if Ubuntu does not find a driver for it automatically, you might need to see if you can find a ppd file for it (unless it understands a common printer language like HP PCL or postscript).

---

### Post by micael3000 on 2010-11-25
The printer is running at a machine with Windows.

I am trying to do that cause where I work we have a software that 'prints' directly at LPT1 to access the printer (when connected to your own computer).
In my case, im developing a part of this software and I have to test it, however I do use a laptop that's why I cant connect LPT here...

---

### Post by dcstar on 2010-11-26
> **micael3000 said:**
> The printer is running at a machine with Windows.

I am trying to do that cause where I work we have a software that 'prints' directly at LPT1 to access the printer (when connected to your own computer).
In my case, im developing a part of this software and I have to test it, however I do use a laptop that's why I cant connect LPT here...

You are not making any sense, Linux does not have LPT whatever so any "software" that requires that is not Linux software, so there is nothing that can be redirected.

If you want to connect a LPT to a shared printer then that is done on the Windows machine and it is irrelevant if the printer is connected to a Linux or Windows box.

---

