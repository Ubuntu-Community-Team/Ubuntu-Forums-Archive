---
title: "can't login (kicked back to login screen)"
date: 2011-07-28
forum: General Help
---

### Post by Z500 on 2011-07-28
i swear this is driving me insane. google search after google search has turned up nothing useful.
 
i've been using ubuntu 11.04 64-bit for a while now without any problems. after installing VirtualBox and adding myself to the vboxusers group, i tried to log back in. the screen flashed black with some text before kicking me back to the login screen. same thing if i try to login as root (i enabled my root account)
 
on top of that, i can't figure out for the life of me how to get wireless to work from the console so i can reinstall my desktop with apt-get. my wireless card is recognized and i can get a list of access points, but when i run dhclient it just said "no DHCPOFFERS received" followed by some lines i can't remember, and now it says only "no broadcast interfaces found."
 
some people mentioned that they had uninstalled evolution, causing the desktop to break. i didn't do anything with evolution, but i did try to remove one of those things in the panel up top, the messenger thing i think. i just can't remember for sure.
 
i've been searching and trying solutions for hours, and i'm at the point where i'm too aggravated to actually do anything (seriously, i mashed the keyboard and my P key came flying off). i'm considering just reinstalling, but after the whole mess i went through making Ubuntu use my wireless card, i'm not too keen on that option.
 
for now i'll resign myself to using windows, as much as i despise it. any help you guys can give is GREATLY appreciated

---

### Post by Habitual on 2011-07-29
When you get to the login screen.... don't login.

Press Ctrl+Alt+F1 and login as yourself.
```
mv .config .config.org
mv .gconf .gconf.org
exit
```

Ctrl+Alt+F7 (might be "F8")
then login as yourself.

Let us know....

---

### Post by Z500 on 2011-08-02
nope, still kicks me back to the login screen. oh well, since i'm the only person who uses this computer it's not so bad now that i figured out how to get into my account, but it still bugs me that i can't do it normally.

---

### Post by CatKiller on 2011-08-02
Probably not a login problem. Probably an X problem.

---

### Post by Habitual on 2011-08-02
this might help:
Press Ctrl+Alt+F1 and login as yourself and run ```
sudo dpkg-reconfigure gdm
```

---

### Post by alexlinux on 2011-08-03
I have the same problem too... and I didn't find any help! However I was able to restore some functionality by enter in recovery mode and chose to login as root in a command line. Then:
1. Login in my account and 
2. Enter startx
3. Open a new terminal (Ctrl + Alt + T) 
4. Enter unity

These gave me access to my files and I made a backup. 

Now since I don't kow how to solve this problem I will reinstall Ubuntu! (again...)

P.S. By the way, this happened after I had upgrade the system (mainly samba libs I think!).

---

### Post by Z500 on 2011-08-12
nope, reconfiguring gdm didn't work either. on the upside though, since i got CompizConfig manager and started changing settings (i prettied up my computer with the cube desktop and shift switcher) unity starts up automatically. no more typing /usr/lib/unity/unity-panel-service and unity every single time. hooray, i guess. lol.

---

### Post by westie457 on 2011-08-12
Did you install virtualbox-ose from the repositories? That one to me looks like a 32-bit app not a 64-bit one. Not sure if that would be the cause or the problem. Humour me here and completely remove it to see if it makes any difference.

Besides the -bit difference virtualbox sometimes throws a hissy fit with EXT4 partitions.

If your system is now okay try using virtualbox from [here]("http://www.virtualbox.org/")

---

