---
title: "Cannot using sudo apt-get install bulid essential?"
date: 2012-10-01
forum: General Help
---

### Post by NoDS on 2012-10-01
I tried to install g++ via using sudo apt-get install build essential but it not work, it warned me message "Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
". How can i fix it???

---

### Post by cwsnyder on 2012-10-01
That usually means you have Synaptic or the Update Manager open while you are trying to use apt-get.

---

### Post by karthick87 on 2012-10-01
If an APT front-end crashed and your database is locked, try this in a terminal,

```
sudo fuser -vki /var/lib/dpkg/lock
```

```
sudo dpkg --configure -a
```

---

### Post by jerrrys on 2012-10-01
Hi Nods; welcome to the forum :)

Check out [googlubuntu]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Unable+to+lock+the+administration+directory+is+another+process+using+it&as_qdr=all&sa=Google+Search&lang=en")

---

### Post by 2F4U on 2012-10-01
> **NoDS said:**
> I tried to install g++ via using sudo apt-get install build essential but it not work, it warned me message "Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
". How can i fix it???

Did you type in the name of the package as you have given in the post? If yes, thats not the correct name, which is build-essential, so what you would have to type in is

```
sudo apt-get install build-essential
```

---

### Post by jrog on 2012-10-01
> **2F4U said:**
> Did you type in the name of the package as you have given in the post? If yes, thats not the correct name, which is build-essential, so what you would have to type in is

```
sudo apt-get install build-essential
```
While this is true, it wouldn't cause the error message that the OP received. It's likely that the error is caused by one of the things mentioned in the first two replies here.

---

### Post by daslinkard on 2012-10-01
> **2F4U said:**
> Did you type in the name of the package as you have given in the post? If yes, thats not the correct name, which is build-essential, so what you would have to type in is

```
sudo apt-get install build-essential
```

The OP may need to run 

```
sudo apt-get update
```

Prior to running
```

sudo apt-get install build-essential
```

---

### Post by NoDS on 2012-10-02
> **karthick87 said:**
> If an APT front-end crashed and your database is locked, try this in a terminal,

```
sudo fuser -vki /var/lib/dpkg/lock
``````
sudo dpkg --configure -a
```
Thanks!! It worked! I must kill the process to do that

---

### Post by jmore9 on 2012-10-02
I just install synaptic and use it for all that stuff.

autoconf , build-essentials , etc

For me using synaptic is way easier than then the others when i beed to install more than 2 or 3 packages.

---

### Post by daslinkard on 2012-10-02
> **NoDS said:**
> Thanks!! It worked! I must kill the process to do that

Glad this is resolved for you!  Please mark this thread as solved!

---

