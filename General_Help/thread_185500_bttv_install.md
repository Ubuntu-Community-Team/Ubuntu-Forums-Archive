---
title: "bttv install"
date: 2006-05-31
forum: General Help
---

### Post by swordsaint on 2006-05-31
I am trying to install bttv on breazy but i dont know how. C an some on e help me :confused

---

### Post by mattkenn4545 on 2006-05-31
For me I downloaded the source tarball compiled did a ./configure make make install then I copied the firmware to the /lib/firmware/'uname -r'/

I'll try to find the walk through that I used

Note did this in dapper.

---

### Post by mattkenn4545 on 2006-05-31
here is the URL

[http://ivtvdriver.org/index.php/Howto](http://ivtvdriver.org/index.php/Howto)

Just follow that and you should be golden

Just remember that the firmware location is 
/lib/firmware/'uname -r'/

Also note I tried the Ubuntu walkthrough but it didn't work at all(and is more complex I feel)

---

### Post by swordsaint on 2006-06-01
i downloaded bttv and when i do make && make install i get this message 

[COLOR="Blue"]root@leon:/home/leon/bttv-0.9.15# make && make install
make -C /lib/modules/2.6.12/build SUBDIRS=/home/leon/bttv-0.9.15 modules
make: *** /lib/modules/2.6.12/build: No such file or directory.  Stop.
make: *** [default] Error 2[/COLOR]
:confused:

---

### Post by awakatanka on 2006-06-01
[http://www.abarbaccia.com/](http://www.abarbaccia.com/)

That site will have dapper howto soon,

---

### Post by speedsix on 2006-06-02
bttv driver is an included module isn't it? Was in breezy.

ivtv is not bttv either.

---

### Post by Kross on 2006-12-07
> **speedsix said:**
> bttv driver is an included module isn't it? Was in breezy.

ivtv is not bttv either.



Yes It is.....

Try This 
[http://ubuntuforums.org/showthread.php?t=300228&highlight=bttv]("http://ubuntuforums.org/showthread.php?t=300228&highlight=bttv")

It work for me..
Let Me know if it works for you..

<=Kross=>

---

