---
title: "E: dpkg was interrupted..."
date: 2009-10-14
forum: General Help
---

### Post by LasseNC on 2009-10-14
Hi, 

whenever I try to open Synaptics I am getting the following errormessage:

```
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

So I open my terminal and write:

```
sudo dpkg --configure -a
```

Which gives me another errormessage:

```
dpkg: fortolkningsfejl, i filen '/var/lib/dpkg/updates/0000' nær linje 1:
 feltnavn '' skal efterfølges af et kolon

```

Now that is in danish, so here is my translation:

```
dpkg: interpretation error, in file '/var/lib/dpkg/updates/0000' near line 1:
 fieldname '' needs to be followed by a colon
```

What does this mean? And how do I fix it?

---

### Post by sisco311 on 2009-10-14
try:
```
sudo mv /var/lib/dpkg/updates/0000 ~/0000.bak
```
```
sudo dpkg --configure -a
```
```
sudo apt-get update
```

---

### Post by LasseNC on 2009-10-14
I think I might have errors in a line of files:

```
dpkg: fortolkningsfejl, i filen '/var/lib/dpkg/updates/0001' nær linje 1:
 slut-på-fil efter feltnavn '2
```

Which means:

```
dpkg: interpretationerror, in file '/var/lib/dpkg/updates/0001' near line 1:
 end-of-file after fieldname '2
```

---

### Post by LasseNC on 2009-10-15
Still having issues, quite lost, should I just reinstall the system?

---

### Post by kanikilu on 2009-10-15
This thread has some other suggestions: [http://ubuntuforums.org/showthread.php?t=385886](http://ubuntuforums.org/showthread.php?t=385886)

---

### Post by LasseNC on 2009-10-15
They are good ideas, however, I cannot get it to work. 

```
root@doram-laptop:/var/lib# cp -arf dpkg dpkg.bak
root@doram-laptop:/var/lib/dpkg# rm -rf updates/*
root@doram-laptop:/var/lib/dpkg# dpkg --configure -a
```

And then still getting errors.

I don't understand this command, when copying it in to Terminal it looks like this.

```
root@doram-laptop:/var/lib/dpkg# ls available
available      available-old  

```

I simply don't understand how to write the command, which then f ups the rest of the guide.

---

