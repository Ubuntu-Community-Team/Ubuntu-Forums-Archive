---
title: "Can't login (keep getting redirected to login after entering correct login)"
date: 2011-11-05
forum: General Help
---

### Post by THESEXPISTOL on 2011-11-05
Hi guys,

I'm having an issue here, after i enter my correct login info, my screen gets black for 2 seconds and then i'm redirected again to login screen and asked to login again and so on...
I logged in tty and entered 'startx' but i get this error

xauth: error in locking authority file /home/myusername/.Xauthority

Before getting this problem, i had my caps lock on and missed a few times my login on text mode, then i rebooted and this happened.

Can't use the system because of this...

Can someone help me?
Thanks

---

### Post by THESEXPISTOL on 2011-11-05
I've removed .Xauthority and now when i login the login menu gets stuck and a terminal opens in the corner of the screen with my user logged in.

i then type
myusername$ startx

and the output is:

X: user not authorized to run the X server, aborting.


Please help!

---

### Post by THESEXPISTOL on 2011-11-05
Is there some way through ubuntu livecd to reinstall the system without losing the files in home folder?

---

### Post by whiskers751 on 2012-03-11
Try:```
sudo startx
```

---

### Post by serapch on 2012-05-26
If you are with lightdm, try switch to gdm with
```
sudo service lightdm stop
sudo service gdm start
```
It works for me and it's a temporary workaround

---

### Post by steeldriver on 2012-05-26
it sounds like your ~/.Xauthority file ownership or permissions got messed up

go into one of the virtual terminals by hitting Ctrl-Alt-F1 (or Ctrl-Alt-F2 etc), login as your normal user, and type

```
sudo /home/*myusername*/.Xauthority

```or
```
sudo rm ~/.Xauthority

```then

```
exit

```and then Ctrl-Alt-F7 to get back to the GUI login screen, and try to log in normally again.

---

