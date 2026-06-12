---
title: "secure format gui"
date: 2012-03-04
forum: General Help
---

### Post by hunterkasy on 2012-03-04
Hi, I am looking for a good program with a gui that I can use to do a secure format of a HHD, I would like it to have option for how many overwrites to perform and even a option for final wipe in all 0's 

is their any out their like that?


system mechanics use to have a floppy program that can do what I said above, but who uses floppies anymore, also  I just want to boot from a live Ubuntu cd and install the software and do the format simple as that

---

### Post by winh8r on 2012-03-04
If you enter this in the terminal


```
sudo apt-get install secure-delete
```

and install it 

then run 

```
man srm
```

it will tell you all the options available to do what you need to do.

**goes without saying this is a very powerful tool and should be used with caution****



OR you can use this which works too:

[http://www.dban.org/]("http://www.dban.org/")

Hope these help you.

---

### Post by hunterkasy on 2012-03-04
> **winh8r said:**
> If you enter this in the terminal


```
sudo apt-get install secure-delete
```

and install it 

then run 

```
man srm
```

it will tell you all the options available to do what you need to do.

**goes without saying this is a very powerful tool and should be used with caution****


OR you can use this which works too:

[http://www.dban.org/]("http://www.dban.org/")

Hope these help you.

thanks for your help, the first option isn't good for me, I am not good with commands without allot of help from others, the second option looks good I am reading into it now 

thanks

---

