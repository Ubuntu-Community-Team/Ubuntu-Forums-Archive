---
title: "Help removing Hamachi"
date: 2006-06-24
forum: General Help
---

### Post by stengah on 2006-06-24
I've installed Himachi using the breezy guidelines in this tutorial:
[http://ubuntuforums.org/showthread.php?t=135036&highlight=howto+hamachi](http://ubuntuforums.org/showthread.php?t=135036&highlight=howto+hamachi)

As it turns out Hamachi doesn't do it for me quite the way I expected. So I want it removed... problem is that I'm only used to do command-line removals (sudo apt-get remove) and this evidently doesn't work with not - aptitude thingies.

Question 1:

Can please anybody tell me how to get rid of Himachi - I'd like to keep my system tidy??? 

Quoestion 2: 

Has anybody got a guide to slimserver installation (and uninstall - haha ](*,) )

---

### Post by stengah on 2006-06-25
Bump

It's probably the fact that I'm relatively inexperienced with linux... but I'm eager to learn more... unfortunately cannot find any relevant threads here or on the Himachi forum.

ANY help would be highly appreciated! :-? 

Cheers!

---

### Post by incubus on 2006-06-25
steangah,

Yeah, that's why I love the Debian package system.  Next time you install Hamachi try using "checkinstall". It converts the installation into a deb which you can dpkg -i or dpkg -r.

But back to your question, what comes to my mind is this: install it again. It will show which files are being copied, if I remember correctly. Take note of those files and delete them manually.

I can try it here if you need help.

incubus

---

### Post by incubus on 2006-06-25
Here's what it says (you don't need to do it):

```

Copying hamachi into /usr/bin ..
Creating hamachi-init symlink ..
Compiling tuncfg ..
Copying tuncfg into /sbin ..

Hamachi is installed. See README for what to do next.

```

So you have:
```

/usr/bin/hamachi
/usr/bin/hamachi-init
/sbin/tuncfg

```

And I think there is a directory ~/.hamachi too.

best,
incubus

---

### Post by stengah on 2006-06-25
Incubus,

Thanks a lot for helping me out here. I did'nt know about the debian way, but it makes good sense. I have only tried ubuntu. Know it's vebian based but not that it handled packages differently.

Thank you for your helpfull efforts once again. Its very useful with specific guidelines. I now know exactly what to do... for a change :D

---

### Post by incubus on 2006-06-25
stengah,

It's good to be helpful.
Back to the package thing, actually Ubuntu shares the same system as Debian.  apt-get, dpkg, and their front-ends, such as synaptic and adept, all work the same way. Many packages are also identical, but many others were modified by Ubuntu developers (that's why we use our own repositories).

This little program, checkinstall, will install a program in the Debian/Ubuntu way, by creating a .deb package, allowing you to remove it easiliy later. Plus, you can keep it somewhere for future use (say you want to install it again).

Check its website:
[http://asic-linux.com.mx/~izto/checkinstall/index.php](http://asic-linux.com.mx/~izto/checkinstall/index.php)

best,
incubus

---

### Post by stengah on 2006-06-26
Thanks Incubus,

These forums are the best!:D

---

### Post by fakie_flip on 2007-06-30
You could look at the make file for hamachi and then remove all of the files that it installed.

---

