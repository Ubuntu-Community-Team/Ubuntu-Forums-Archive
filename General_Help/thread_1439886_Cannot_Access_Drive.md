---
title: "Cannot Access Drive"
date: 2010-03-26
forum: General Help
---

### Post by Whym on 2010-03-26
Hello, I would like to ask for some help with a problem please.

Ubuntu 9.04 is installed on this laptop, after a couple of forced shutdowns (just pressing and holding the power button), for whatever reason Ubuntu can no longer complete the boot (it drops to text output and says that the target filesystem does not have sbin/init).

This is kind of a side issue though. My problem is how to get at the data.

A Couple of screen shots (From running a Ubuntu 9.04 Live CD) to illustrate the problem are attached to this post. They quickly explain much more than I can.

Maybe someone could tell me how to mount it properly. Running Nautilus as root is about the extent of my expertise on this. And naturally that has done nothing.

Any help, at all, from anyone would be very much appreciated.
Thank you very much in advance.

---

### Post by Whym on 2010-03-26
Sorry, wrong screenshot.
Re-uploaded.

---

### Post by krismatth3 on 2010-03-26
Can you run e2fsck on the device? [http://linux.die.net/man/8/e2fsck]("http://linux.die.net/man/8/e2fsck") 

It sounds like some aspect of that filesystem is in trouble.

---

### Post by Whym on 2010-03-26
Thank you so much for the reply, krism.
Would you be able to tell me how to do that? I don't have the necessary experience to do that properly/safely.

---

### Post by krismatth3 on 2010-03-26
First boot into the live CD, and then open a terminal (gnome menu->accessories->terminal) and run

```

# e2fsck /dev/sda1

```

If it just says filesystem clean, try 
```
# e2fsck -f /dev/sda1
```

Does it show any errors? If so, 
```
# e2fsck -p /dev/sda1
```
might be able to fix the problem.

--
This is my old account. My new account is here: [http://ubuntuforums.org/member.php?u=1043584](http://ubuntuforums.org/member.php?u=1043584)

---

### Post by Whym on 2010-03-26
Thank you.
I will try those.

---

### Post by Whym on 2010-03-27
> **krismatth3 said:**
> might be able to fix the problem.
It did.
Thank you so much.;)

---

