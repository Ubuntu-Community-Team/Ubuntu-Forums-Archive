---
title: "reinstalling gdm"
date: 2010-01-01
forum: General Help
---

### Post by Twiggeh on 2010-01-01
Earlier today i tried to install SLiM, but i didnt feel all comfortable with it so now i would like to revert back to gdm.
I still have it installed, but i dont know how to activate it.. and since i uninstalled slim i dont have any login manager.. i just login through cli and use startx manually atm and its really bugging me..

---

### Post by spiderbatdad on 2010-01-01
have you tried sudo /etc/init.d/gdm restart

---

### Post by Twiggeh on 2010-01-01
> **spiderbatdad said:**
> have you tried sudo /etc/init.d/gdm restart

Yeah, this is what happens then :
[img]http://img683.imageshack.us/img683/2180/screenshot1w.png[/img]

---

### Post by spiderbatdad on 2010-01-01
sorry. how about:
```
sudo service gdm start
```

---

### Post by Groundswell on 2010-01-01
can't he just change session to gnome at login? then set it to default?

---

### Post by Twiggeh on 2010-01-01
> **spiderbatdad said:**
> sorry. how about:
```
sudo service gdm start
```

Nope, gdm still didnt start on bootup =/

---

### Post by spiderbatdad on 2010-01-01
> **Groundswell said:**
> can't he just change session to gnome at login? then set it to default?

I don't know. Was under the impression there is currently no graphical login manager. Haven't tried xubuntu for some time; just realized that is environment. If x session is running, maybe can set gdm under System.

---

### Post by spiderbatdad on 2010-01-01
maybe run ```
xfce4-session
```

---

### Post by dcstar on 2010-01-01
> **Twiggeh said:**
> Earlier today i tried to install SLiM, but i didnt feel all comfortable with it so now i would like to revert back to gdm.
I still have it installed, but i dont know how to activate it.. and since i uninstalled slim i dont have any login manager.. i just login through cli and use startx manually atm and its really bugging me..

What is in /etc/X11/default-display-manager?

It should contain:
```
/usr/sbin/gdm
```

---

### Post by Groundswell on 2010-01-01
> **spiderbatdad said:**
> I don't know. Was under the impression there is currently no graphical login manager. Haven't tried xubuntu for some time; just realized that is environment. If x session is running, maybe can set gdm under System.


yeah me neither :-s and all i remember from it was a cute little mouse, haha

---

