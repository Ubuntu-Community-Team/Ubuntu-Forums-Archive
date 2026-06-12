---
title: "How to lock or at least hide files"
date: 2010-05-28
forum: General Help
---

### Post by titanicmusic14 on 2010-05-28
I use a Mac at work. Attached to it is an external hard drive (personal) that I would like to either encrypt or either make invisible to the Mac. I have ubuntu on my personal laptop. Could I make it ext4 and unviewable by Mac or PC or something along those lines so that nobody just goes through my (personal) stuff by just logging in and going on the desktop? I'm looking for something that will still allow me to access them fairly easily such as file permissions or something. I don't wanna put it into a zip file or a password protected rar file.  I know nothing is 100% but I at least want a layer of security. Thanks

---

### Post by aysiu on 2010-05-28
I think making it Ext4 is a good way to go if you don't want real security but just a prevention of casual snooping. Mac OS X cannot read Ext4, as far as I know (there is a tool to read Ext2, but even that you have to install first--it's not a standard part of OS X).

Is there any particular reason you need a personal external drive at work? I would think if it's something work-related your workplace might spring for your own work hard drive, and if it's not work-related... does it really need to be at work?

---

### Post by titanicmusic14 on 2010-05-28
> **aysiu said:**
> I think making it Ext4 is a good way to go if you don't want real security but just a prevention of casual snooping. Mac OS X cannot read Ext4, as far as I know (there is a tool to read Ext2, but even that you have to install first--it's not a standard part of OS X).

Is there any particular reason you need a personal external drive at work? I would think if it's something work-related your workplace might spring for your own work hard drive, and if it's not work-related... does it really need to be at work?

Its competitive here. I don't want anyone taking my good ideas as there own. thanks though.

---

### Post by aysiu on 2010-05-28
> **titanicmusic14 said:**
> Its competitive here. I don't want anyone taking my good ideas as there own. thanks though.
If it's that competitive, I would advise using a TrueCrypt hidden volume:
[http://www.truecrypt.org/docs/?s=hidden-volume](http://www.truecrypt.org/docs/?s=hidden-volume)

---

### Post by colorlessprism on 2010-05-28
+1 truecrypt, i use it to keep my financial info and passwords on my computer. you can have a keyfile on your personal computer and hide the volume container, even if they have truecrypt installed AND know the password without the keyfile it cannot open...truecrypt is incredible powerful and is one of those programs that make you proud of open source

---

