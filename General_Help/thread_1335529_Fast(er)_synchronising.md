---
title: "Fast(er) synchronising"
date: 2009-11-23
forum: General Help
---

### Post by wimmelis on 2009-11-23
Dear all, 


To keep my data sources up to date, I generally use synchronising software, which manages both way synchronising. 
On Ubuntu, I have been using Unison, but find it to be extremely slow for checking the differences. Any folder with a bit of gigabytes in it takes ages (hours actually). 
In my windows days, I remember that that used to go much faster (5 to 10 min.), even for the same size folders. 
Are there any faster alternatives than Unison ? Any options I can set in Unison to improve its performance ?
Thanks, 

WM

---

### Post by leorolla on 2009-11-25
Try adding this to the profile:

times = true
perms = 0
fastcheck = true
pretendwin = true

Sill every time you unplug the device it will have to do a slow one again.

---

### Post by wimmelis on 2009-11-29
Thanks, that is fast like lightning now.

With disconnect you mean the device being disconnected/unmounted ?

---

### Post by leorolla on 2009-11-29
Welcome.

I mean whatever like that... if it is an external USB.

---

