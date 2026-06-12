---
title: "I can't change anything in usr/"
date: 2011-12-04
forum: General Help
---

### Post by chris42259 on 2011-12-04
When I try to add another cursor theme to usr/shared/icons/ I get a message saying I don't have permission.

How do I get permission?

I do not want to use the command line.

SOLVED:  I wasn't able to find a solution that didn't involve the command line :(  

But thanks to oldos2er I was able to use  'sudo -i pcmanfm'.

Thanks to everyone who helped.  Really enjoying Ubuntu now.

---

### Post by mike555 on 2011-12-04
You need to be root, if you don't want to use terminal, install "nautilus-gksu" .......

---

### Post by oldtimer7777 on 2011-12-04
> **chris42259 said:**
> When I try to add another cursor theme to usr/shared/icons/ I get a message saying I don't have permission.

How do I get permission?

I do not want to use the command line.

You can install PCMANFM, because that is what I use, and you can set that to operate at root level privilages, and you can literally drag and drop anything anywhere want just like you could in windows.  No having to use the command line.

In terminal just cut and paste this:

sudo apt-get install pcmanfm

do a search for 'file manager'

In pcmanfm file manager 

Select:   Edit >> Preferences >> Advanced  

Then cut and paste this command in Switch User Command:

gksu %s

Then simply click on Tools >> Open Current Folder as Root. 

Then you will be able to Open Current Folder as Root in GUI to copy and paste files anywhere you like.

Sometimes this is helpful for new users to Linux because they are not familiar with the command line instructions or how to do this in natulus as easily.

---

### Post by chris42259 on 2011-12-04
Thanks Mike and OldTimer.

Mike: I followed your instructions, but nothing has changed.  I don't see nautilus in my system.

Oldtimer:  When you say 'do a search for file manager' what exactly do you mean?  Do a text search of my entire system?

Thanks again to both of you for your help.

---

### Post by chris42259 on 2011-12-04
Isn't there a way that I can log in as root, to make the changes that I need?

---

### Post by chris42259 on 2011-12-04
I'm not new to Linux BTW, I'm coming from PCLinuxOS, where I would just log in as root.

---

### Post by lisati on 2011-12-04
> **chris42259 said:**
> Isn't there a way that I can log in as root, to make the changes that I need?

Have a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by chris42259 on 2011-12-04
NEW STRATEGY:  OK, I'll use the command line.  Can anyone tell me how to do this?  

I just tried 'sudo pcmanfm' only to get a permission denied error after my password was accepted.

Any ideas on how to do simple file work as root in Lubuntu?

---

### Post by oldos2er on 2011-12-04
```
sudo -i
``` will give you a persistent root shell. Type **exit** when done.

---

### Post by mike555 on 2011-12-14
> **chris42259 said:**
> Thanks Mike and OldTimer.

Mike: I followed your instructions, but nothing has changed.  I don't see nautilus in my system.

.

    Sorry , I thought you were using Ubuntu ,which has Nautilus installed by default ...

---

### Post by MartijnNL on 2011-12-14
> **mike555 said:**
> Sorry , I thought you were using Ubuntu ,which has Nautilus installed by default ...

He is. He just used PCLinux before.

A simple Alt+F2 and then running "gksu nautilus" would also have done the trick.

chris42259 can you mark this thread as solved in the Thread Tools on top?

---

### Post by nothingspecial on 2011-12-14
> **MartijnNL said:**
> He is. He just used PCLinux before.

A simple Alt+F2 and then running "gksu nautilus" would also have done the trick.



No it wouldn't

> **chris42259 said:**
> 

Any ideas on how to do simple file work as root in Lubuntu?

---

### Post by MartijnNL on 2011-12-15
> **nothingspecial said:**
> No it wouldn't

I read the thread, but missed the reference to Lubuntu. I checked the first post:

> Really enjoying Ubuntu now

And assumed he was using Ubuntu itself. But I guess he used Ubuntu as a generic name for all *buntus.

---

