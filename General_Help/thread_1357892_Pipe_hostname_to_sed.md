---
title: "Pipe hostname to sed"
date: 2009-12-17
forum: General Help
---

### Post by xzased on 2009-12-17
Hi. Im trying to change the hostname section of a file across multiple servers using sed, but I dont know how to pipe the output of hostname to sed. Please help :(

---

### Post by dcstar on 2009-12-17
> **xzased said:**
> Hi. Im trying to change the hostname section of a file across multiple servers using sed, but I dont know how to pipe the output of hostname to sed. Please help :(

```
hostname | sed .......
```

---

### Post by xzased on 2009-12-17
Thanks, just found oput that one :popcorn: but how do you actually replace a word? all I have is:

hostname | sed -i 's/test/${hostname}/g' file

but it replaces "test" for "${hostname}"

---

### Post by bodhi.zazen on 2009-12-17
What are you trying to do exactly ?

sed 's_new-word_old-word_g'

See man sed :lolflag:

---

### Post by xzased on 2009-12-17
I have a file called hostname.txt that I copy across multiple servers, so that file contains the word "test" only, so I would like to replace the word test with the actual hostname of the machine

---

### Post by bodhi.zazen on 2009-12-17
copy the hosts file to /etc/hosts

Then run

```
sudo sed -i -e "s_test_$HOSTNAME_g" /etc/hosts
```

This will change every instance of "test" to the actual hostname

---

### Post by synapsys on 2009-12-17
> **bodhi.zazen said:**
> 
See man sed
.

---

### Post by earthpigg on 2009-12-17
i figured it out!

```
[chris: ~]$ cat file
oldtext
[chris: ~]$ ***sed -i 's/oldtext/'$HOSTNAME'/g' file***
[chris: ~]$ cat file
chris-desktop
[chris: ~]$ 
```

edit:

hrm, quotes are handy...

```
[chris: ~]$ echo "hello" $USER", how are you?"
hello chris, how are you?
[chris: ~]$
```

---

### Post by xzased on 2009-12-17
Got it. Thanks earthpigg and bodhi.zazen. You guys rock :guitar:

---

### Post by bodhi.zazen on 2009-12-17
[s]look ... up ... [/s] Sweet !!! 

:lolflag:

---

### Post by earthpigg on 2009-12-17
> **bodhi.zazen said:**
> [s]look ... up ... [/s] Sweet !!! 

:lolflag:

yeah, you where posting while i was learning :D

---

### Post by bodhi.zazen on 2009-12-17
> **earthpigg said:**
> yeah, you where posting while i was learning :D

Sed is a nice tool , you will find it helpful I am sure.

---

