---
title: "How Do I log off, kill startx and switch to pure console"
date: 2010-05-03
forum: General Help
---

### Post by kukubau on 2010-05-03
I am testing Lucid right now and I want to log out completely to console so I can delete the ubuntu default user. But whenever I log out I get the welcome "log in " page. How can I have just the console?

Thanks

---

### Post by tornadof3 on 2010-05-03
Try Logging off as normal, ctrl-alt-F1, login to the console and then

```
sudo init 3
```

Does that take you to run level 3 as I would expect?

---

### Post by burton247 on 2010-05-03
I just tried to jump straight to init1 but ubuntu didn't like it lol.

How I did it was reboot, load up recovery mode. Then from there you can drop to root shell, which I think is init 1, not sure why I couldn't get there before. From here you log into a root console. If you want to create another user you can do it all here, then run

```
 init 3 
``` 

to get back to multi-user mode

log in and ```
 startx 
``` and you'll be in unbuntu gui with your new user

---

### Post by burton247 on 2010-05-03
Just done some tests. Logging out and switching to a terminal will be an easier way to do it. However, as far as I know you do not need to switch to init 3, just log in as root. And I think X is still running so you wont be able to come out of by running startx you'll have to go for a reboot.

When I tried to get to init 1 from the console I still couldn't, anyone know why?

---

### Post by Vishal Agarwal on 2010-05-03
it is not advisable to delete the default user. 
Do you just want to login to some other user completely, with out seeing the default user ?

---

### Post by mhgsys on 2010-05-03
> **burton247 said:**
> Just done some tests. Logging out and switching to a terminal will be an easier way to do it. However, as far as I know you do not need to switch to init 3, just log in as root. And I think X is still running so you wont be able to come out of by running startx you'll have to go for a reboot.

When I tried to get to init 1 from the console I still couldn't, anyone know why?

for killing X

in tty; (ctrl + alt + f1) kill x as root.
```
sudo service gdm stop
```
or 
```
sudo /etc/init.d/gdm stop
```

to start it again
type
```
sudo service gdm start
```
or
```
sudo /etc/init.d/gdm start
```

---

### Post by kukubau on 2010-05-04
Does anyone know why in "Login Screen" settings the "Login as .... automatically" is disabled and how can I enable it?

---

### Post by darolu on 2010-05-04
> **burton247 said:**
> I just tried to jump straight to init1 but ubuntu didn't like it lol.

How I did it was reboot, load up recovery mode. Then from there you can drop to root shell, which I think is init 1, not sure why I couldn't get there before. From here you log into a root console. If you want to create another user you can do it all here, then run

```
 init 3 
``` 

to get back to multi-user mode

log in and ```
 startx 
``` and you'll be in unbuntu gui with your new user

Jumping to Init 3 will not do the trick as Ubuntu's default runlevel is runlevel 2; in Debian systems Runlevels 2 to 5 have the same services so it won't make any difference. Runlevel 1 (init 1) is Single-user mode, it doesn't configure network nor start demons.
The method mhgsys suggested should work.

---

### Post by burton247 on 2010-05-04
> **kukubau said:**
> Does anyone know why in "Login Screen" settings the "Login as .... automatically" is disabled and how can I enable it?

You have to go admin --> users and groups and enable it there.



Going from init 1 to 3 then starting x working fine for me. What's wrong with using single user mode to delete a user though? I would have thought it was safer as you can only be logged on as root and not another user

---

### Post by kukubau on 2010-05-06
> **burton247 said:**
> You have to go admin --> users and groups and enable it there.


Even if I login as root, the "Login as" box is disabled.

---

### Post by Shadow12313 on 2010-05-06
Before you login change the session to xterm if you only want the terminal.

---

### Post by kukubau on 2010-05-08
Do you guys know how to autologin as root and not as "ubuntu" user?

It's a pain in the backside to log off and login back again everytime.

---

### Post by burton247 on 2010-05-09
Yeah, I got my wires crossed, I think it used to be under users and groups. It is now under login screen, but you realised that yourself. 

Why would you want to atuologin as root? Why would you even want to log into graphical root? It's really unadvised, you can do everything you'll need to from a normal ubuntu user that has sudo . Even then you can always log into the terminal as root

---

