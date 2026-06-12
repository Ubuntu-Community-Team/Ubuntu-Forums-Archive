---
title: "O bytes on HD - Yikes! Can't Delete Root's Trash."
date: 2012-05-02
forum: General Help
---

### Post by neu5eeCh on 2012-05-02
OK. I was in _Partition B_ trying to make more room. I GKSU'd into Thunar and cleared out my wallpaper folder. That only made matters worse! 

Little did I know that every time I deleted something, it wasn't *really* being deleted. It was merely being _moved_ to a hidden trash folder under root. Emptying trash does little good because it doesn't empty Root's trash!

](*,)

So, I'm now in _Partition A_. I GKSU'd Thunar and navigated to /root/.local/share/Trash/ _on Partition B_. I selected everything in Trash and pressed Delete, but the same thing seems to be happening. :? I just can't seem to clear out the d--m--d Trash!

Help.

---

### Post by collisionystm on 2012-05-02
try to reboot after deleting

that has happened to me before. A reboot cleared it up.

---

### Post by neu5eeCh on 2012-05-02
Ok.

---

### Post by SlugSlug on 2012-05-02
use shift + delete to bypass bin

---

### Post by neu5eeCh on 2012-05-02
> **SlugSlug said:**
> use shift + delete to bypass bin

That's like telling me not to drink the arsenic after I've downed the bottle. :lolflag:

But yes, in the future, I will shift-delete. Thank you. ;-) @ collision. I tried rebooting but no love.

**Edit: **I've emptied root's trash folder (in Partition B) as root (in Partition A) but there's still no space on Partition B. I just can't figure out where all the Trash is squirreled away!

---

### Post by SlugSlug on 2012-05-02
sudo find / -type d -name *Trash*

---

### Post by neu5eeCh on 2012-05-02
> **SlugSlug said:**
> sudo find / -type d -name *Trash*

Great. Found /Trash/ in several locations. What's the equivalent "command line" command for shift-delete? Or is that necessary?

**Edit:** I'm recursively deleting everything in the TRASH folders, but nothing seems to help. The Partition still shows as having 0 bytes. Part of the problem is that I can't 'su'. Ubuntu locks the root password.

---

### Post by CatKiller on 2012-05-02
You don't need to su. Use sudo.

---

### Post by neu5eeCh on 2012-05-02
OK. Solved.

Based on the terminal search recommended by SlugSlug, I found that _**yet** *aNOTHer*_ Trash Folder had been created when I tried to delete _root's_ Trash (in Partition B .root/.local/share/Trash/*) from within _Partition A_. The new Trash folder was:

/.Trash-0

Ha! Every time I deleted one Trash folder, yet another one was created! :rolleyes:

Talk about whack-a-mole!

So, I booted nautilus as root (gksu nautilus), _in Partition A_, and used, by gad, Slugslug's shift-delete to _permanently_ delete the Trash in /.Trash-0. 

No more recycling for me.

Thank you all.:guitar:

**Edit:** I recovered just over 1 Gig of HD space.

---

### Post by neu5eeCh on 2012-05-02
> **CatKiller said:**
> You don't need to su. Use sudo.

I couldn't CD to the Root directory using sudo? Terminal didn't like *sudo cd /~.*

---

### Post by CatKiller on 2012-05-02
You don't need to run *everything* as root. ```
cd /root
sudo bunch of stuff
```

Or ```
sudo -i 
bunch of stuff 
```

if you want to live dangerously.

EDIT: What's with the superfluous /? cd ~ is what you want. cd /~ makes no sense.

---

### Post by neu5eeCh on 2012-05-02
> **CatKiller said:**
> You don't need to run *everything* as root. ```
cd /root
sudo bunch of stuff
```Or ```
sudo -i 
bunch of stuff 
```if you want to live dangerously.

Yeah... I know I don't have to do everything as root. I get that reminder from my wife all the time.

I tried the first option but was told I didn't have rights to access /root. That's why I tried su. When that didn't work, I tried the hail Mary: sudo cd /root/~.

I didn't try sudo -i. I'm only a green belt when it comes to terminal ju-jitsu. And yes, there's something to be said for living dangerously.

---

### Post by CatKiller on 2012-05-02
sudo cd /root/~ doesn't make any sense either (it expands to /root/root, or possibly /root/home/user depending on which environment variables you're using). Be careful what you type, especially as root.

---

### Post by neu5eeCh on 2012-05-02
> **CatKiller said:**
> sudo cd /root/~ doesn't make any sense either (it expands to /root/root, or possibly /root/home/user depending on which environment variables you're using). Be careful what you type, especially as root.

Be careful? Why? What could *possibly* go wrong?

I didn't include the tilde in the command. I was using that as an "etc". Should have just written "etc.".

---

### Post by CatKiller on 2012-05-02
> **VTPoet said:**
> Be careful? Why? What could *possibly* go wrong? 
:lolflag:

---

