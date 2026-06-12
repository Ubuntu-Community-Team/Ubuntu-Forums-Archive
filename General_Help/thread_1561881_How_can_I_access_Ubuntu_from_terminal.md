---
title: "How can I access Ubuntu from terminal?"
date: 2010-08-26
forum: General Help
---

### Post by {Gray-Fox} on 2010-08-26
Hello everyone!
I have a serious problem! I can not access ubuntu!
I wanted to **customize the login window**, and went on "System  -> Administration -> Login Window" and I click "unlock" and I changed something (I do not remember), then I restarted the computer and all was well, but it appeared a black screen with two lines written, but it is too fast, I can not read what is written, and then pop the login screen, and when I put my login and password and click on enter I released a screen "[COLOR=Red]**terminal**[/COLOR]" at the top right.

Please help me!!!!:confused:


[COLOR=DarkRed]*ps. sorry for my bad english*[/COLOR]

---

### Post by {Gray-Fox} on 2010-08-26
**[SIZE=3]help me!![/SIZE]**

---

### Post by alphacrucis2 on 2010-08-26
> **{Gray-Fox} said:**
> **[SIZE=3]help me!![/SIZE]**

Try typing:

```
startx
```

and hit Enter


Edit forget that. I tried reproducing what you had done myself. Appears you set it to start only xterm with no gnome. Probably just have to run the right program from there to change it back. Will see if I can figure it out

---

### Post by {Gray-Fox} on 2010-08-26
I tried to typing:

```
startx
```
and gives me the following response
```
x user not authorized to run the x server aborting
```


I asked around and they told me to put this code:
```
/etc/init.d/gdm stop
```
and gives me the following response

```

Since the script you are attempting to invoke has been converted to an Upstart job, you may also use the stop(8) utility, e.g. stop gdm stop: Rejected send message, 1 matched rules, type="method_call", sender=":1.34" (uid=1000 pid=1310 comm="stop) interface="com.ubuntu.Upstart0_6.job" member="stop" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbim/init"))

```

---

### Post by pytheas22 on 2010-08-26
Try:
```

**sudo** /etc/init.d/gdm stop
```

If it doesn't start the graphical session, please post any output here.

---

### Post by {Gray-Fox} on 2010-08-26
gives me a black screen with 5 written above (pulseaudio, ecc..) and to the right there is [ok]

---

### Post by alphacrucis2 on 2010-08-26
I have managed to sort out the issue on my test machine. First I tried just typing in gdmsetup from the xterm window but for some reason the unlock button doesn't work. So nothing for it but to read the documentation on gdmsetup to find out what it does. I solved the problem by doing the following from xterm.

sudo gedit /etc/gdm/custom.conf

It should open a file that includes this line:

```
DefaultSession=xterm
```

Under gedit change that line to read:

```
DefaultSession=gnome.desktop
```

Save and exit gedit.

In xterm type command:

```
sudo shutdown -r now
```

When it reboots back to the login prompt, login as normal and you should find all is well.

---

### Post by alphacrucis2 on 2010-08-26
Ha Ha - found an easier way to sort the problem. Just delete the custom.conf file. I noticed on my other machine that there is no /etc/gdm/custom.conf file so that file gets created when you make any changes via System - Administration - Login Screen. By deleting /etc/gdm/custom.conf, gdm reverts to its' default behaviour which to start gnome. This is probably specified in another file somewhere in usr/share/gdm. Hence from the xterm window:

```
sudo rm /etc/gdm/custom.conf
```

Then restart as per my previous post.

---

### Post by {Gray-Fox} on 2010-08-26
thanks thanks thanks a lot .. you're a genius..

---

