---
title: "how do I keep gui from starting"
date: 2010-02-05
forum: General Help
---

### Post by Strongman332 on 2010-02-05
hello i am trying to keep my gui from loading unless i want it to. does any one know how i can go about doing this?

also how do i uninstall the graphical boot

also i have heard that you can add a 3 on to the end of a your kernel line in grub to get a non graphical boot. this also sounds interesting to me

---

### Post by Sef on 2010-02-05
At the start, where you insert your password at the bottom is an option to boot into the command line.  You can set it as the default.

---

### Post by Strongman332 on 2010-02-05
will gdm still load?
i was prefering to not start any gui at all

---

### Post by bluefrog on 2010-02-05
sudo update-rc.d -f gdm remove

---

### Post by anaconda on 2010-02-05
> **bluefrog said:**
> sudo update-rc.d -f gdm remove

that would do the trick.

Just wanted to comment on previous post, where it was recommended to make the recovery mode the default boot option... That works, but it is not a good idea to run the system with root rights, which recovery mode has.

---

### Post by Strongman332 on 2010-02-05
well in that case can i modify the grub entry for the default boot option so it will not start gdm

---

### Post by rnerwein on 2010-02-05
hi
i just have look on my box - and wonder - the commands: who -r and runlevel both gives me -
Runlevel 2 / N 2. i think there is something changed about the runlevel philosophie. i had known only the meaning of runlevels 1,2,3,4,5 and 6.
runlevel 2 and the desktop is up completely ! in runlevel 2 ??? i am running 9.10 karmic koala.
have to read more documentation i think - and you i guess too.
ciao

sorry i forgot to ask you what version you are running

---

### Post by falconindy on 2010-02-05
Runlevels aren't used as intended in Ubuntu. If you want to boot to a TTY, append 'text' to your kernel options in Grub.

> runlevel 2 and the desktop is up completely ! in runlevel 2 ??
Because runlevel 2 isn't defined as being special. Booting anything other than 1 (or single) will result in a GUI. 1 or single brings you to single user mode, which isn't what you want (drops directly to root access). 'text' is the proper option here.

---

### Post by Strongman332 on 2010-02-06
I am running 9.10

also i don't know how to edit 9.10's grub

---

### Post by mushwars on 2010-02-06
> **Strongman332 said:**
> also i don't know how to edit 9.10's grub

```
sudo mount /boot/
sudo nano /boot/grub/grub.conf
```
I dont recommend doing it that way, you should do the rc-update thing. That way it wont start gdm, I am the same way I hate gdm xdm kdm etc, I like logging in, inside a tty


**this**
> **bluefrog said:**
> sudo update-rc.d -f gdm remove

---

### Post by Strongman332 on 2010-02-06
iwas told not to edit anything int grub.conf as it will interfere with grub2 (new grub used in 9.10)

---

