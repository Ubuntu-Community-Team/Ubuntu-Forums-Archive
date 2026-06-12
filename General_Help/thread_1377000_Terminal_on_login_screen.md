---
title: "Terminal on login screen"
date: 2010-01-09
forum: General Help
---

### Post by Jackzor on 2010-01-09
I can't get it to come up anymore? Help? 

I don't even know where to start.

I hit control-alt-f1 OR f2

Neither bring up the log in. Just a black screen with a courser

---

### Post by NoaHall on 2010-01-09
Try ```
sudo service gdm start
```

---

### Post by Jackzor on 2010-01-09
> **NoaHall said:**
> Try ```
sudo service gdm start
```

Where should I type that. I can't type on the black screen?

---

### Post by NoaHall on 2010-01-09
> **Jackzor said:**
> Where should I type that. I can't type on the black screen?

Oh, I see. I thought you said terminal on login screen. Hm. Have you done anything strange recently?

---

### Post by Jackzor on 2010-01-09
Nothing I can think of. Other than messing with grub. But my grub is perfectly fine and all

---

### Post by NoaHall on 2010-01-09
> **Jackzor said:**
> Nothing I can think of. Other than messing with grub. But my grub is perfectly fine and all

What graphics card do you have?

---

### Post by Jackzor on 2010-01-09
Um.. NVIDIA Geforce 8400M GS?

I used to be able to get terminall to come up just fine. Just.. All of a sudden

---

### Post by NoaHall on 2010-01-09
> **Jackzor said:**
> Um.. NVIDIA Geforce 8400M GS?

I used to be able to get terminall to come up just fine. Just.. All of a sudden

Oh, I see. You can get to the login screen, but not then to tty1 or tty2?

---

### Post by Jackzor on 2010-01-09
> **NoaHall said:**
> Oh, I see. You can get to the login screen, but not then to tty1 or tty2?

My whole computer works fine. I can login in and everything. I'm using it right now. I'm just trying to change the background of my login screen and in order for me to do that I need to get into terminal while on the login screen and login in through the terminal and use the commands

export DISPLAY=0.0
sudo -u gdm gnome-control-center 


BUT the terminal never comes up.  No login or anything. I end up having to hit alt-f7 to go back the the normal login screen and I can't change the background like I want...

---

### Post by NoaHall on 2010-01-09
> **Jackzor said:**
> My whole computer works fine. I can login in and everything. I'm using it right now. I'm just trying to change the background of my login screen and in order for me to do that I need to get into terminal while on the login screen and login in through the terminal and use the commands

export DISPLAY=0.0
sudo -u gdm gnome-control-center 


BUT the terminal never comes up.  No login or anything. I end up having to hit alt-f7 to go back the the normal login screen and I can't change the background like I want...

Ah. Hm. I suggest trying to reinstall nvidia drivers.

---

### Post by Jackzor on 2010-01-09
I don't think it was a driver issue but I did reinstall and no change

---

### Post by Jackzor on 2010-01-09
?Help?

---

### Post by Jackzor on 2010-01-09
Bump :(

---

### Post by spiderbatdad on 2010-01-09
How about try to stop gdm?
```
sudo /etc/init.d/gdm stop
```
This should present you with a login prompt where you will enter user name and password...then export DISPLAY=0.0, etc. Restart your session with startx.

---

### Post by Jackzor on 2010-01-09
> **spiderbatdad said:**
> How about try to stop gdm?
```
sudo /etc/init.d/gdm stop
```
This should present you with a login prompt where you will enter user name and password...then export DISPLAY=0.0, etc. Restart your session with startx.

I ran that and it dumped me to the black screen that I get when I try ctrl+alt+f1

Now I am starting to feel like that may be a major problem. I think it happened after I ran an update a few hours ago... How can I go backwards with the updates?...Lol I'll be glad to try that also.

---

### Post by CharlesA on 2010-01-09
Was it a kernel upgrade? You can go back to the previous kernel from the grub menu.

---

### Post by Jackzor on 2010-01-09
All I did was the upgrade manager...

---

### Post by Jackzor on 2010-01-10
Anyone?

---

### Post by handydan918 on 2010-01-10
Reboot and select the previous kernel from the grub menu. If it works, great. If not, post back.

---

### Post by Jackzor on 2010-01-10
No go. Just messed up the graphics. But thats under control.

---

### Post by Jackzor on 2010-01-10
bump

---

### Post by Jackzor on 2010-01-10
...?

Where is the support. I have been at this all day.

---

### Post by DaithiF on 2010-01-10
sounds like your tty1 ... 6 are not running.

In a regular gnome-terminal window (ie. Applications->Accessories->Terminal) do:
```
sudo start tty1
```

then try switching to tty1 using ctrl+alt+f1 and see if you get a login prompt.

also, i think you have a small typo in the commands you listed, you will need a semi-colon in this line:
```
export DISPLAY=:0.0
```

---

### Post by Jackzor on 2010-01-10
> **DaithiF said:**
> sounds like your tty1 ... 6 are not running.

In a regular gnome-terminal window (ie. Applications->Accessories->Terminal) do:
```
sudo start tty1
```

then try switching to tty1 using ctrl+alt+f1 and see if you get a login prompt.

also, i think you have a small typo in the commands you listed, you will need a semi-colon in this line:
```
export DISPLAY=:0.0
```

Its still not working here is the result:

```
nicholas@nicholas-laptop:~$ sudo start tty1
[sudo] password for nicholas: 
start: Job is already running: tty1
```

Thank you for the correction, though.

---

### Post by Jackzor on 2010-01-10
Bumppp...:(:(:(:(

---

### Post by Jackzor on 2010-01-10
Can someone point me towards some ubuntu forums that may help out a little more?

---

### Post by jusitndm on 2010-01-10
I'm not sure but i think i had a problem like that after changing the hostname in the gui without updating /etc/hostname or /etc/hosts so if you changed the hostname in the gui updating these files could help.

---

