---
title: "need path to g++"
date: 2011-03-29
forum: General Help
---

### Post by klein de usa on 2011-03-29
hi 
i have installed Netbeans and it is looking for the directory g++ is in, i found the directory for gcc but i can't find where directory g++ is. i'm sure it is some where because i can run g++ first.cpp -o test in a terminal and it will compile i just can't find g++ folder,

---

### Post by Nutria on 2011-03-29
> **klein de usa said:**
> hi 
i have installed Netbeans and it is looking for the directory g++ is in, i found the directory for gcc but i can't find where directory g++ is. i'm sure it is some where because i can run g++ first.cpp -o test in a terminal and it will compile i just can't find g++ folder,

Maybe you haven't installed it?

Open a terminal window and type the command "g++".  (Do I have to mention not to actually type the quotes?)  What happens?

---

### Post by nice_like_rice on 2011-03-29
Type "which g++". If it is installed, it will return the directory where it is installed. If not, sudo apt-get install g++.

---

### Post by klein de usa on 2011-03-29
hi

'which g++' found it i think i did find and that didn't come up with anything . thank you

---

### Post by Nutria on 2011-03-29
> **klein de usa said:**
> 'which g++' found it i think i did find and that didn't come up with anything .

That makes absolutely zero sense.

---

### Post by andrew.46 on 2011-03-30
> **klein de usa said:**
> 'which g++' found it i think i did find and that didn't come up with anything . thank you

Perhaps your 'find' syntax was incorrect? Something like the following should work:

```

sudo find /usr -iname 'g++'

```

although 'find' is not necessarily the best tool for this particular job...

Andrew

---

### Post by deconstrained on 2011-03-30
**sudo apt-get install build-essential**

---

### Post by d3v1150m471c on 2011-03-30
```

locate g++

```

btw, it's in /usr/bin

---

### Post by Hakunka-Matata on 2011-03-30
sind ze klein, oder heisen ze blos klein?  oder viellicht beiden?

---

### Post by Nutria on 2011-03-30
No need for over-complicated gyrations.  Just open a terminal window and type:
```
g++
```

---

