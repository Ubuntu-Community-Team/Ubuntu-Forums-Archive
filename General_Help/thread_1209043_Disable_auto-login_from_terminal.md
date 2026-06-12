---
title: "Disable auto-login from terminal"
date: 2009-07-09
forum: General Help
---

### Post by FireLink on 2009-07-09
Just happened to delete an account, but I was not aware that is was the default auto-login account.

Now, I'm stuck at a empty desktop, without taskbars.

I can access to terminals using Ctrl-Alt-Fx.
I want to know if there is a config file to edit.

Thanks!

---

### Post by nice_like_rice on 2009-07-09
Not 100% sure, but you could try /etc/gdm/gdm.conf I think it's there...

Could you not just start gdm from the console and change stuff from there?

david


//EDIT:

Yes, it is that config file, about 20 lines down or so, "AutomaticLoginEnable" and "AutomaticLogin"?

//EDIT 2 lol :)

Maybe you will need to change /etc/gdm/gdm.conf-custom if it exists, that's the one which defines the automatic user login for me.

---

### Post by FireLink on 2009-07-09
Great! This is working!

...

But I see the same empty desktop. But this time, I am logged as my other account.

---

### Post by mbeach on 2009-07-09
probably looking to comment out the automatic login enable and automatic login lines in 
```
/etc/gdm/gdm.conf-custom
```

edit:
walked away before posting - obviously too slow on the draw - not sure why you wouldn't get any panels though.

---

### Post by FireLink on 2009-07-09
There's nothing customised in 
/etc/gdm/gdm.conf-custom

I'll comment the lines in /etc/gdm/gdm.conf

---

### Post by nice_like_rice on 2009-07-09
try

sudo dpkg-reconfigure xserver-xorg

?

---

### Post by mbeach on 2009-07-09
the only other thing I could think of is going to going to one of the terminal sessions (Ctrl+Alt F6 for example), logging in and running

```
sudo killall gnome-panel
```

and see what happens.

---

### Post by FireLink on 2009-07-09
> **nice_like_rice said:**
> try

sudo dpkg-reconfigure xserver-xorg

?

Do not seems to work...

---

### Post by FireLink on 2009-07-09
> **mbeach said:**
> the only other thing I could think of is going to going to one of the terminal sessions (Ctrl+Alt F6 for example), logging in and running

```
sudo killall gnome-panel
```

and see what happens.

Oups.
Looks like we have a loop-hole here.

There's no gnome-panel running.
When I type
```
sudo gnome-panel
```in terminal session, there's no display avaliable.

How can I access to the tty7 terminal?

---

### Post by mbeach on 2009-07-09
I'm digging around, but can't find an answer for you. What is the exact error you get when you try to start gnome-panel? What happens if you don't use sudo? I'm at a bit of a loss. I thought gnome-panel would automatically default to tty7. Are you using Jaunty?

---

### Post by FireLink on 2009-07-09
> **mbeach said:**
> I'm digging around, but can't find an answer for you. What is the exact error you get when you try to start gnome-panel? What happens if you don't use sudo? I'm at a bit of a loss. I thought gnome-panel would automatically default to tty7. Are you using Jaunty?

```
me@myPC:~$ gnome-panel
Impossible d'ouvrir l'affichage :
```
*Impossible d'ouvrir l'affichage* in english is Impossible to open display.
```
me@myPC:~$ sudo gnome-panel
Impossible d'ouvrir l'affichage :
```
```
me@myPC:~$ gnome-panel --display=:0

** (gnome-panel:5879) WANRING **: Cannot register the panel shell: cannot connect to the session bus.
me@myPC:~$
```

I'm using Ubuntu 9.04 Jaunty Jackalope (Ubuntu Network Remix).

---

### Post by mbeach on 2009-07-10
sorry, I'm at a loss.

Anybody else?

---

### Post by FireLink on 2009-07-10
Thanks for your help Mr. Bleach.

I'll reinstall Ubuntu. Fortunately, this was a fresh install, no data loss.

Thank you again!

---

