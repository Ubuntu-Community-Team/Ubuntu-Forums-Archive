---
title: "/etc/sudoers ownership"
date: 2011-10-01
forum: General Help
---

### Post by valenti on 2011-10-01
Hi!
I have a problem, with sudoers ownership. When i installed ubuntu 11.4 i create Valentiu acc, and later on one more account, and set both as administrators. Since i created second account, i cant use sudo command anymore, even if i deleted second account. I've got constant error 
sudo: /etc/sudoers is owned by uid 1001, should be 0
sudo: no valid sudoers sources found, quitting

---

### Post by WorMzy on 2011-10-01
How did you manage that?

I'm guessing you used chown to change the ownership of some system files; hopefully you only did it on one or two, so the damage won't be too difficult to reverse.

Can you post the output of the following command:
```
ls -l /etc
```

To fix sudoers, follow the first part of this help page to boot into the recovery mode: [http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

Once you've booted into recovery mode, just run

```
chown root:root /etc/sudoers
```

---

### Post by valenti on 2011-10-01
uh omg.. almost all my files are owned by uid 1001-adminu user :s but i havent messed with chown and chmod at all... :s is there a command to repair this? or should i reinstall ubuntu?
[http://www.shrani.si/f/2D/yK/1QtB7fun/screenshot.png](http://www.shrani.si/f/2D/yK/1QtB7fun/screenshot.png)


*Removed image and uploaded as attachment.  Please don't upload full pictures, link a thumbnail or add it as an attachment (as I have done). - 404*

---

### Post by WorMzy on 2011-10-01
Oh dear. If the extent of the problem is that large, the only thing I can recommend is a reinstall. Just make sure you back up your home folder first.

It'd be nice to know how this happened though. Hundreds of files don't just randomly change ownership of their own accord.

---

### Post by valenti on 2011-10-01
well as far as i remember, i created new account, and made it administrator, and right after thath, i change my first account from Custom to Administrator. And i think that was preety it... i make some home folder changing also...

---

### Post by WorMzy on 2011-10-01
Maybe when you were changing the ownership of the home folder, you made a mistake, like you accidentally ran

```
chown -R adminu:adminu / home/adminu
```

(note the space)

or something?

That'd cause the problem, because it'd change the ownership of everything on the partition.

---

### Post by valenti on 2011-10-01
i have never ever typed chown or chmod... i was just installing ftp, and playing with users fot ftp access

---

### Post by valenti on 2011-10-01
ohh, i think i know what i did. i make new user, change its location to "/" and thank checked Make user the owner of the new home directory

so that probably makes the problem

---

### Post by WorMzy on 2011-10-01
I've never used a GUI application to make a new user, but maybe that's what did it.

Chalk it up as a lesson learnt, reinstall, and just be extra careful in the future. :)

---

