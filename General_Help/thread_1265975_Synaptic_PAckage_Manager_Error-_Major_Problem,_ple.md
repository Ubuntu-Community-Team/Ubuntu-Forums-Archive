---
title: "Synaptic PAckage Manager Error- Major Problem, pleaase help"
date: 2009-09-14
forum: General Help
---

### Post by gordong11 on 2009-09-14
I tried to install "ia32libs" via synaptic package manager and got a major error. Now I can't use the SPM at all, I tried to reboot and still get the same error:

E: Malformed line 269 in source list /etc/apt.sources.list


Please see screenshot

Line 269 in sources.list says:

268: # cassandra nosql db
269: deb [http://people.apache.org/~eevans/debian](http://people.apache.org/~eevans/debian) cassandra/-i386

Pleease help I cant use the synaptic package manager

Well I deleted both those lines, and I can use the package manager now, but I have no idea if I needed those.

---

### Post by P4man on 2009-09-14
If you want to use that apache repository, change the line to:
```
deb http://people.apache.org/~eevans/debian cassandra/
```

If you need it or not, is for you to decide. 
edit: its for cassandra.. dont even know what that is :)

---

### Post by gordong11 on 2009-09-14
Thanks for the help pman!!!

---

### Post by 3rdalbum on 2009-09-14
You installed the "ia32-apt-get" package, which duplicated all your repositories and added the "-i386" to all the copies. Remove that package; it's not something you want to use.

TIP: You could have put a # symbol before all the lines in question; it's known as "commenting-out". It tells the computer to ignore that line, but it still exists so you can uncomment it if you need it later.

---

