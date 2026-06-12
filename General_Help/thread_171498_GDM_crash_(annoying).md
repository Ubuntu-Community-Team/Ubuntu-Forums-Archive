---
title: "GDM crash (annoying)"
date: 2006-05-06
forum: General Help
---

### Post by Trajan on 2006-05-06
Hello all,

    i'm having an issue with gdm everytime I try to open it and login it shows up for about a second and dissapears. Is anyone getting this error  ? It's a bit annoying since it was working a couple of days ago. Now I can't seem to change the login splash screen at all, it stays on the default ubuntu splash. 
Any suggestions ?

```

sudo gdmsetup
"segmentation fault"

```

---

### Post by az on 2006-05-06
Are you up-to-date?

---

### Post by Trajan on 2006-05-08
[QUOTE=azz]Are you up-to-date?[/QUOTE]
Sure am but no idea why this is happening. Perhaps it's due to the nvidia script ?

---

### Post by iomud on 2006-05-08
Same problem here. gdmsetup starts and then poof! Gone.

---

### Post by ComplexNumber on 2006-05-08
[quote=Trajan]Hello all,

    i'm having an issue with gdm everytime I try to open it and login it shows up for about a second and dissapears. Is anyone getting this error  ? It's a bit annoying since it was working a couple of days ago. Now I can't seem to change the login splash screen at all, it stays on the default ubuntu splash. 
Any suggestions ?

```

sudo gdmsetup
"segmentation fault"

```[/quote]
have you changed your login theme? if so, to which theme?

---

### Post by Trajan on 2006-05-20
I haven't.The packages were updated then the default Ubuntu Splash Login was being displayed and will not let me change it to a customizde GDM theme that i had before. LoginWindow launches (to change the gdm theme) but it crashes instantly. Could it be my nvidia script that's messing up ? or the dapper packages ? since i've lost my lock screen section (it ends up within logout & when selected it just restarts the the system instead of locking screen. I think some packages may have some bits and pieces to get fixed.)

---

### Post by tseliot on 2006-05-20
[QUOTE=Trajan]I haven't.The packages were updated then the default Ubuntu Splash Login was being displayed and will not let me change it to a customizde GDM theme that i had before. LoginWindow launches (to change the gdm theme) but it crashes instantly. Could it be my nvidia script that's messing up ? or the dapper packages ? since i've lost my lock screen section (it ends up within logout & when selected it just restarts the the system instead of locking screen. I think some packages may have some bits and pieces to get fixed.)[/QUOTE]
I'm on Dapper and I'm using my nvidia script but I don't have that problem.

Are you using XGL?

---

### Post by gio on 2006-05-25
Same problem. System update today.

---

### Post by brownrl on 2006-06-11
I get the same this is the gdb output if that helps. There is a conversation in the bugtracker about it. Something to do with Xubuntu and Ubuntu desktops trying to looking for some xml file that is not there or simular.


[New Thread -1225966672 (LWP 5669)]
[New Thread -1237972048 (LWP 5682)]
[New Thread -1246762064 (LWP 5683)]

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread -1218660672 (LWP 5614)]
0xb7867749 in g_str_hash () from /usr/lib/libglib-2.0.so.0
(gdb) quit

---

### Post by chollis888 on 2006-06-14
Same problem here I started getting this after aptitude remove half of xubuntu-desktop because it had'nt been used. I installed to play around with and just never got to. Now when I try to open the login window service so I can get back my cool gdm theme it just flops after about a sec. And I'm stuck with the xubuntu splash in gdm. Anyone solved this yet? I'll just fully remove X-desktop and if that fixes it I'll let you guys know.

---

### Post by chollis888 on 2006-06-16
okay found a solution, just do a search for files "gdm.conf" is what your looking for. I had two of these one in /etc/gdm and one in /etc/xdg/something/something. The problem was on specified the Human theme and the other the xubuntu theme.
I just copied unwanted to backup and deleted it, restarted no me problems.
Goodluck

---

### Post by chollis888 on 2006-06-16
found something else there's a "gdm-cdd.conf" file in my /etc/gdm dir. Properties show that this is the link to the /etc/xdg/xubuntu/gdm/gdm.conf file I have a feeling this is the true culprit. Copying to back up and removing. And maybe removing the entire /etc/xdg dir?

---

