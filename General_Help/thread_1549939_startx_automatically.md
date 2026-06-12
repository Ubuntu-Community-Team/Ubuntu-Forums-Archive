---
title: "startx automatically"
date: 2010-08-10
forum: General Help
---

### Post by Metalclay on 2010-08-10
I've tried googling, and I get tons of results on this, but I can't find one that's like my situation.

When I turn on the pc, it takes me to a black terminal-like screen. It asks for my login, then password, then it tells me welcome to ubuntu. I type in "startx" and it takes me to my desktop.

I used to be able to just turn on the computer and have it take me to my desktop, but for some reason (I think maybe it was one of those update packages), it now takes me to that black screen everytime I want to login.

Is there anyway to fix this? How can I get it to just go to the desktop without having to type in user, password, and startx?

Thank you.

---

### Post by Zorgoth on 2010-08-10
Perhaps something is wrong with your gdm?

---

### Post by Fxy on 2010-08-10
Is there not an option or something within ubuntu itself to disable the graphical login & have only the terminal login :?  If im correct maybe you could just switch the graphical logon back on :-)

Im not 100% on weather im correct or not :?

---

### Post by Fxy on 2010-08-10
You could always use the following piece of code to start gdm...
```
sudo service gdm start
```

I also done a few googles & found that you can have the command startx run automatically, but haven't yet found out how to master this...

---

### Post by Metalclay on 2010-08-10
I tried

 ```
sudo service gdm start
```

when I turned on the computer in place of

```
startx
```

and that also took me to my desktop.

I turned off the pc and turned it on again, but it still boots up into the terminal and asks me to login. I just typed in startx this time because it's shorter. 

Any other ideas?

---

### Post by amac777 on 2010-08-11
I'm having this problem too. It seems to be related to the Nvidia driver. If this is your problem too, there is a bug (with no real fix) about it here:

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/532436](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/532436)

My brute force work around was to add a little script that gets run at boot up after a small delay to start gdm. If it's already started, the script doesn't affect anything, but otherwise, at least GDM gets loaded:

1. Edit your system crontab:

```
sudo nano /etc/crontab
```

add this line to the end:

```
@reboot root /root/gdmstart
```

2. Make the gdmstart script:

```
sudo nano /root/gdmstart
```

with this contents:

```
#!/bin/bash
sleep 6
/usr/sbin/service gdm start
```

3. Make the script executable:

```
sudo chmod u+x /root/gdmstart
```

If that doesn't work, you might need to increase the "sleep 6" to a longer sleep on your computer. On the other hand, if there is a long pause before the graphical login starts, you may need to decrease the sleep number so gdm gets started sooner.

---

### Post by Metalclay on 2010-08-11
Thanks man, that worked a treat. At first I thought it hadn't because it took me to the same terminal login screen, but after about five seconds the screen blinked with all kinds of weird things and just went to my desktop. I don't mind all the blinking, but...will it at least stay this way? Or will it someday just mess up? I thought ubuntu was more stable than windows :(

If someone else comes up with this problem and is more uninformed about ubuntu than I am, after opening up the folder with the first piece of code and pasting in second, you have to save it by pressing ctrl+o in the terminal.

Oh, and yes I do have an integrated nvidia video card (old computer).

---

### Post by amac777 on 2010-08-11
To reduce the delay while at the terminal login screen you can change the sleep delay. It's in seconds so the "sleep 6" means it delays six seconds before loading the graphical stuff. That's ideal for my computer but for yours you could try "sleep 2" or "sleep 3" etc until you get the delay to something almost instant for your computer.

I did those changes on my computer back when Lucid came out and it has continued to work until now. So hopefully it will continue to do so in the future.

---

