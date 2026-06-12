---
title: "Adding Xubuntu to my system"
date: 2006-06-17
forum: General Help
---

### Post by cobbweb on 2006-06-17
Hi, 
  I am currently using Ubuntu(Dapper) and would like to install XUbuntu also. (Kind of like how I can switch from Xgl to Ubuntu) I have no idea where to start. How can I install XUbuntu on my Ubuntu machine??? 

 Thank you, 
 Cobbweb

---

### Post by adwait on 2006-06-17
Xubuntu = Ubuntu with XFCE instead of GNOME.

Use
```
sudo aptitude install xubuntu-desktop
```

Now when you login, you can click Menu and select the environment you want.

---

### Post by cobbweb on 2006-06-17
your a god and I now worship you... 


 Thanks,
 Cobbweb

---

### Post by scxtt on 2006-06-17
damn, if i hadn't decided to eat 1st, i could have been a "god" ...

:-(

---

### Post by cobbweb on 2006-06-17
ha ha .. well maby you still can, 
  It doesn't show up in my sessions menu.. I also restarted my computer.. If i click my GNOME session, does that now become my XUbuntu Session? 

 Danka, 
 
Cobbweb

---

### Post by aysiu on 2006-06-17
[QUOTE=adwait]Xubuntu = Ubuntu with XFCE instead of GNOME.

Use
```
sudo aptitude install xubuntu-desktop
```

Now when you login, you can click Menu and select the environment you want.[/QUOTE]
To use *aptitude* properly, you should update first: ```
sudo aptitude update
sudo aptitude install xubuntu-desktop
```

---

### Post by cobbweb on 2006-06-17
does XUbuntu work with Xgl??

---

### Post by scxtt on 2006-06-17
[QUOTE=cobbweb]ha ha .. well maby you still can, 
  It doesn't show up in my sessions menu.. I also restarted my computer.. If i click my GNOME session, does that now become my XUbuntu Session?[/QUOTE]no, you should be able to use either Gnome or XFCE (or KDE if you've installed it) - they're all independent of eachother ... if it's not showing up in your menu, i'm sure there's a resolution for that { edit: think i found one if you need it } - i had that happen to me before and i just had to edit a txt file - but that was in Fedora ... it might be specified in the configs for Gnome Display Manager (GDM) ...

Ubuntu = ubuntu w/ Gnome defaul
Kubuntu = ubuntu w/ KDE default
Xubuntu = ubuntu w/ XFCE default

and *ubuntu can be any of the others if you install the corresponding Desktop Environment ...

---

