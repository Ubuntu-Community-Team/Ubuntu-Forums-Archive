---
title: "He me with this bash scripting?"
date: 2012-10-02
forum: General Help
---

### Post by karthick87 on 2012-10-02
We run apt-cacher-ng server in our office for installing packages locally. However we are using different versions of ubuntu, and so the sources.list file varies for different distributions, all the source files were kept in the following location say ie.. [http://172.29.39.100/ubuntu/](http://172.29.39.100/ubuntu/)............ and so on. What i need to do is first of all i need to find the ubuntu version using lsb_release -rs and then if the version is i.e 10.10 then the   default sources.list should get replaced using wget from the following location,

If 10.10 then,

```
wget http://172.29.39.100/ubuntu/1010/sources.list

```
If 10.04 then,

```
wget http://172.29.39.100/ubuntu/1004/sources.list
```

How can i automate this task in bash script? Can anyone help me?

---

### Post by Lars Noodén on 2012-10-02
If there are any mistakes, hopefully someone can catch them.  But below is what I would try:

```

#!/bin/sh

VER=$(/usr/bin/lsb_release -sr)

if   [ '10.10' = ${VER} ]; then
 /usr/bin/wget http://172.29.39.100/ubuntu/1010/sources.list

elif [ '10.04' = ${VER} ]; then
 /usr/bin/wget http://172.29.39.100/ubuntu/1004/sources.list

fi


```

You might need to use wget with the -O or --output-document option.

---

### Post by Vaphell on 2012-10-02
how about
```
wget http://172.29.39.100/ubuntu/$( lsb_release -sr | tr -d '.' )/sources.list
```

---

### Post by karthick87 on 2012-10-03
Thankyou  [Vaphell]("http://ubuntuforums.org/member.php?u=347382") & [Lars Noodén]("http://ubuntuforums.org/member.php?u=168643")

---

