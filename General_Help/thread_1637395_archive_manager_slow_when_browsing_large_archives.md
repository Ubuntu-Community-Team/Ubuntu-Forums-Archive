---
title: "archive manager slow when browsing large archives"
date: 2010-12-04
forum: General Help
---

### Post by joham34 on 2010-12-04
Hello everybody. 
I have in my pc (ubuntu 10.10 32 bit)  a folder with about 10.000 files. It is a samba shared folder and so far I could browse fast and easily those files in another old ( Pentium4 1,5Ghz) PC with WinXP. 
I installed ubuntu 10.10 but the browsing now is toooooooo slow , although the old Pc's performance is considerably faster than before (when I had WinXP). 
Is there any idea whats going wrong? Can I do something about it? 
Also, although the old PC's speed is satisfatory now, would it become even faster if I installed an older ubuntu distro? 
Thank you in advance

---

### Post by krishnandu.sarkar on 2010-12-04
Well...as it's network shared folder, I too face this problem when browsing samba shares. I think while accessing samba shares it's common problem.

---

### Post by NightwishFan on 2010-12-04
I doubt an older one would be much faster. To be honest, for some reason Nautilus the default Ubuntu file browser is a bit slow with large directories. I am sure your input in a big report would be valued if you have this issue. To fix nautilus try running this command:
```
sudo su
```
Then:
```
echo "vm.vfs_cache_pressure=50" >> /etc/sysctl.conf
```
Then:
```
sysctl vm.vfs_cache_pressure=50
```
Finally:
```
exit
```

If that does not work well, try using an alternative such as this program:
[https://launchpad.net/pyneighborhood](https://launchpad.net/pyneighborhood)

It is already in the software center to find and install. (Or click below)
[apt://pyneighborhood]("apt://pyneighborhood")

---

### Post by joham34 on 2010-12-04
thank you for your reply 
I tried the change you suggest in systctl.conf but didnt work. I will try the programm you suggest next but before that : 
If I right click main panel, I get "add to panel " where there are various utils. One of them is "search for file" Well, with it the same folder put in a flash drive is browsed rapidly ( with archive manager it is done very slowly ) but cant get this utility browse shared samba folders
Any idea if I could make this utility browse samba folders?

---

### Post by joham34 on 2010-12-05
pyNeighborhood doesnt work. 
May be I should try konqueror or some other browser? 
I am trying to make gnome search tool to browse my samba folder but nothing so far

---

