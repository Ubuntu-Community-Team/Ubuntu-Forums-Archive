---
title: "Can no longer login as me, can only login as guest"
date: 2012-06-29
forum: General Help
---

### Post by Rich_S on 2012-06-29
Not sure what I did, but I was trying to fix the Low Graphics Mode error (which apparently I did).

Now, when I get to the Ubuntu Lightdm login screen, it won't let me login as myself (I enter my password, the screen goes black for a second with some text scrolling by, then it takes me right back to the Lightdm login screen. I can however login as guest.

If I boot to a command line I can login as myself just fine, so it's not my password.

Please help.

---

### Post by steeldriver on 2012-06-29
were you doing stuff like 'sudo startx' from your user account? that can sometimes leave a root-owned ~/.Xauthority in your home dir

log in at the command line or a virtual terminal (Ctrl-Alt-F1... F6) and do a

```
ls -al ~/.*authority
```if either of those is owned by root then 'sudo rm' it

---

### Post by Rich_S on 2012-06-29
> **steeldriver said:**
> were you doing stuff like 'sudo startx' from your user account? that can sometimes leave a root-owned ~/.Xauthority in your home dir

log in at the command line or a virtual terminal (Ctrl-Alt-F1... F6) and do a

```
ls -al ~/.*authority
```if either of those is owned by root then 'sudo rm' it

Yeah, that's exactly what I was doing and you are spot on, .Xauthority ended up being owned by root.

So then I did

```
sudo mv .Xauthority Xauthority.bak 
sudo shutdown -r now
```

and X failed to start

so then I did 

```
chown myusername .Xauthority
shutdown -r now
```

and it rebooted just fine, to my desktop, but it never asked me to login when it rebooted, my desktop just came straight up.

Seriously, WTF???!!!

---

