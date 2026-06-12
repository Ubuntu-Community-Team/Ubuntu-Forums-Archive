---
title: "Problem mounting directories with special charachters in fstab"
date: 2011-05-06
forum: General Help
---

### Post by Rody82 on 2011-05-06
I have a directory called "1) Other", which resides on a seperate drive. I want to bind this directory to somewhere in my homedir, so my fstab line looks something like

```

/some_location/1\051\040Other/  /some_other_location/1\051\040Other none rw,bind   0 0

```As I understood from an hour of googling, the special characters " " (space) and ")" should be included via their corresponding octal ascii-codes, as in the example above. 

However: during boot I get the message

```

Error mounting "1\051 Other". Press S to skip mounting or M for manual recovery.

```When I skip and boot, there is suddenly a new directory called "1\051 Other" (which I did not create). When I then type

```

sudo mount -a

```the directory mounts without any hickups to the intended location. Anyone ever encountered a similar problem?

I have Ubuntu 11.04, 2.6.38-8, x86_64

---

### Post by bodhi.zazen on 2011-05-06
It is probably trying to mount the bind too early in the boot process.

I suggest you add the option noauto to fstab and add a command to /etc/rc.local to mount it later in the boot process. You man need a sleep in rc.local

```
sleep 5
mount -a
```

---

### Post by Rody82 on 2011-05-08
Well, using the [FONT="Courier New"]noauto[/FONT] option works (even without using [FONT="Courier New"]sleep[/FONT]), but putting

```

mount -a 

```

in [FONT="Courier New"]/etc/rc.local[/FONT] didn't work; as the [FONT="Courier New"]mount[/FONT] manpage suggests, [FONT="Courier New"]noauto[/FONT] also implies that particular mount will be skipped when using [FONT="Courier New"]mount -a[/FONT]. Instead, I had to use an explicit

```

mount /some_directory/1\)\ Other/ 

```

in [FONT="Courier New"]/etc/rc.local[/FONT] for it to work.

This feels more like a workaround than an actual solution...could you tell me: 

[LIST=1]
[*]why do the \040's appear to work, but not the \051's?
[*]Do we have to go through this trouble just to mount directories with a ")" in them? Is there a more elegant solution to this? 
[/LIST]

---

### Post by bodhi.zazen on 2011-05-08
I do not know a more elegant solution (other then to not use special characters).

Post a bug report on Launchpad or on the mount mailing list as I think it is unlikely anyone here will know the technical details of mount in this detail.

---

