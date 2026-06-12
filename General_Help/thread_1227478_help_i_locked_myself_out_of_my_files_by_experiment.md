---
title: "help: i locked myself out of my files by experimenting with distros"
date: 2009-07-30
forum: General Help
---

### Post by w.g.hanna on 2009-07-30
i got a new netbook so i started using my lap top as a spare.  i have a seperate home partition from my os.  so i just started messing around.  fedora for a couple days.  pc-bsd.  solaris.  mandriva.  pclinuxos.  debian lenny.  crunchbang.  fedora.  zenwalk.  mint.  

at some point, the computer stopped letting me log into my home folder.  the os worked fine - but when i would try to log on, an error screen would pop up, and it would send be back to square one.   

so i reinstalled, and i just created a new user name and everything was fine and usable.  there is still a folder for my orriginal user name, and it appears from the disk usage as if there are still files inside.  unfortauntely, i can't get in the folder because i lack permission - and can't change permissions because i can't log on. 

i even tried using a live cd to access the folder - and still i lacked permission.  

any ideas on how to get at the files?

---

### Post by michy99 on 2009-07-30
```
gksudo nautilus
```

---

### Post by HappyFeet on 2009-07-30
Or if you are using the ubuntu live cd, do
```
sudo su
```
then
```
nautilus
```

---

### Post by sdlynx on 2009-07-30
agreed, if its permissions you want just use root

---

