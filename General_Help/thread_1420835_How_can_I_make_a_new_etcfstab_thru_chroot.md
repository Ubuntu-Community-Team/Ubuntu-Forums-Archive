---
title: "How can I make a new etc/fstab thru chroot?"
date: 2010-03-03
forum: General Help
---

### Post by kansasnoob on 2010-03-03
OK I goofed :(

I was setting up new separate /home/username/Download and /home/username/Document partitions to be shared by several operating systems. I'd succeeded with Lucid, Jaunty, Hardy, and Mint Gloria, but when I got to Karmic I flubbed! I forgot to "cp" it's fstab (eg: sudo cp /etc/fstab /etc/fstab_old).

I did however make a text document of all the OS's fstabs and other pertinent files before beginning. So I have the info but there is no fstab to copy it into.

I also know how to mount and chroot Karmic, that's not a problem. Where my lack of knowledge comes into play is creating a file/document via cli. I know if it's a directory I can "mkdir' but I have no idea how to "make file" through the cli.

I guess I just never had to do it before so don't laugh too loud (unless you roll on the floor while doing so), but what I need to do is "make /etc/fstab" in my chroot and then use nano to put in the fstab text.

I just don't know how to "make file", if I can "mkdir" I should be able to "make file" if I knew how :D

---

### Post by geirha on 2010-03-03
```
sudo nano /etc/fstab
```

It'll open as an empty file. When you save, the file will be created, with the new information you put in.

---

### Post by kansasnoob on 2010-03-03
> **geirha said:**
> ```
sudo nano /etc/fstab
```

It'll open as an empty file. When you save, the file will be created, with the new information you put in.

That easy?

I just used ls and saw I had none and thought "oh crap". I'll be back when I try that ;)

---

### Post by sisco311 on 2010-03-03
You can run GUI apps in the chroot.
[list=a]
[*]allow your user to connect to the X server & run the GUI app:

outside the chroot type:
```
xhost +SI:localuser:**username**
```
inside the chroot run the app:
```
sudo -i gedit
```

OR


[*]run the application(s) in a separate window:
outside the chroot type:
```
Xnest -ac :2
```
inside the chroot type:
```
export DISPLAY=127.0.0.1:2.0
```
start a window manager:
```
metacity &
```
run an application, i.e the panels:
```
gnome-panel &> /dev/null &
```
[/list]

---

### Post by kansasnoob on 2010-03-03
Awesome!

That worked perfectly. I was a bit worried, that was one of those "repetition" goofs :redface:

It was also awesome to see that the Lucid fstab entries for the new Documents and Download partitions worked in Karmic. That's a first except for Jaunty and Mint Gloria.

Changes in each new release seem to effect how partitions mount, whether or not auto mounted partitions show up on the Desktop, etc. Naturally I don't want the automounted stuff to show up like if I've manually mounted something.

Many, many thanks :D

---

### Post by kansasnoob on 2010-03-03
> **sisco311 said:**
> You can use GUI apps in the chroot.
[list=a]
[*]allow your user to connect to the X server & run the GUI app:

outside the chroot type:
```
xhost +SI:localuser:**username**
```
inside the chroot run the app:
```
sudo -i gedit
```

OR


[*]run the application(s) in a separate window:
outside the chroot type:
```
Xnest -ac :2
```
inside the chroot type:
```
export DISPLAY=127.0.0.1:2.0
```
start a window manager:
```
metacity &
```
run an application, i.e the panels:
```
gnome-panel &> /dev/null &
```
[/list]

Regarding Karmic I'd rather not because Karmic's X causes "hard crashes" on my hardware requiring a hard reset. I only keep Karmic on my box to monitor changes that might effect grub2.

Hard resets play hell on hardware :)

---

### Post by sisco311 on 2010-03-03
> **kansasnoob said:**
> Regarding Karmic I'd rather not because Karmic's X causes "hard crashes" on my hardware requiring a hard reset. I only keep Karmic on my box to monitor changes that might effect grub2.

Hard resets play hell on hardware :)

But, the X server runs on the host OS, you only allow the apps from the guest (Karmic) to connect to it.

---

### Post by kansasnoob on 2010-03-03
> **sisco311 said:**
> But, the X server runs on the host OS, you only allow the apps from the guest (Karmic) to connect to it.

Cool I'll try that in the future.

---

