---
title: "Lotus Notes 8.5.1 on 9.10"
date: 2009-10-30
forum: General Help
---

### Post by klockej on 2009-10-30
So after 9.10 was officially released I decided to wipe my system and reinstall due the the changes with grub etc. Once this was done I went to set up lotus notes 8.5.1 and the install ran fine, when I launched it I received the License in the terminal window and after that a big nothing. I previously had this running in 9.04 and the 9.10 beta with out any issues. 

I have followed the guides on the following pages but they have not solved the issue either. 

[http://www.browniesblog.com/A55CBC/blog.nsf/dx/26102009193509MBRC42.htm?opendocument&comments#anc1](http://www.browniesblog.com/A55CBC/blog.nsf/dx/26102009193509MBRC42.htm?opendocument&comments#anc1)

[http://www-10.lotus.com/ldd/nd85forum.nsf/5f27803bba85d8e285256bf10054620d/69b50f2db7bb7b0b85257659005ab79e?OpenDocument](http://www-10.lotus.com/ldd/nd85forum.nsf/5f27803bba85d8e285256bf10054620d/69b50f2db7bb7b0b85257659005ab79e?OpenDocument) 
    - the 64bit stuff

I am just wondering if I am the only person that is having this issue or if anyone has solved it, I am pulling my hair out trying to get this working again.

---

### Post by klockej on 2009-10-30
While trying to figure out what the issue is I have found that all of my symphony tools work fine, it is just the lotus notes client that will not run. 

Hopefully someone can figure this out.

---

### Post by magneze on 2009-10-30
Not tried it with Notes yet - am thinking of doing the upgrade on my Notes laptop next week.

---

### Post by klockej on 2009-10-30
Figured this out, after digging around and trying to launch the program from the terminal, I found LN was complaingin about the libgnomeprint and libgnomeprintui not being able to be found. Once i installed the packages that these are apart of the program launched fine.

sudo apt-get install libgnomeprint2.2-0 libgnomeprintui2.2-0

These packages must have been left out of this version of Ubuntu.

---

### Post by magneze on 2009-10-31
Thanks for this - will be useful when I do the upgrade! :)

---

### Post by migraine on 2009-10-31
thanks for the fix.
this worked for me on a fresh 9.10 install.:p

---

### Post by gray380 on 2009-12-04
After last update of Ubuntu 9.10 I have the same problem with LN. I can see only the upper menu.
The libgnomeprint2.2-0 libgnomeprintui2.2-0 are already installed.
Any ideas?

brg,
Serhiy.

---

### Post by Gman3025 on 2009-12-09
It seems we have the same problem, the lotus notes still not working

---

### Post by ondrokm on 2009-12-21
Hi, I have the same problem on Ubuntu 9.10 64bit.
I've tried  
```
http://www-10.lotus.com/ldd/nd85forum.nsf/5f27803bba85d8e285256bf10054620d/69b50f2db7bb7b0b85257659005ab79e?OpenDocument
http://www.browniesblog.com/A55CBC/blog.nsf/dx/26102009193509MBRC42.htm?opendocument&comments#anc1
```
and
```
sudo apt-get install libgnomeprint2.2-0 libgnomeprintui2.2-0
``` nothing helped.
Lotus  notes gives me an error (see an attachment): ```
org.eclipse.swg.broswer.Broswer: /usr/lib/libnspr4.so (/usr/lib/libnspr4.so wrong ELF class: ELFCLASS64
```
Any ideas?

---

### Post by jongudm on 2010-01-05
> **gray380 said:**
> After last update of Ubuntu 9.10 I have the same problem with LN. I can see only the upper menu.
The libgnomeprint2.2-0 libgnomeprintui2.2-0 are already installed.
Any ideas?

brg,
Serhiy.

This looks very similar to the problem I'm having, the program starts, accepts my password but then when I try to open my mailbox I just get an error.  The program can clearly connect to the server but no applications can be opened.

---

### Post by jongudm on 2010-01-05
Forgot to mention, the error message I get is: "CWPCA8522E: Application did not get installed".  Does anyone recognize this?

---

### Post by jensen.allen on 2010-03-04
I think I have it - there is a path problem that I found.  This is sort of a hack, but it works:

 ```
cd /opt/ibm/lotus/notes/jvm/lib/i386
sudo mkdir usr
sudo ln -s /usr/lib32 ./usr/lib
```Makes the libnspr4.so ELF problem go away.    To find out, I used the loader environment variable to generate a trace:

```
 export LD_DEBUG=files
```
This resulted in the following output:

      ```
5126:     file=/usr/lib/libnspr4.so [0];  needed by /opt/ibm/lotus/notes/jvm/lib/i386/libj9prt24.so [0]
5126:
5126:     file=/opt/ibm/lotus/notes/jvm/lib/i386//usr/lib/libnspr4.so [0];  needed by /opt/ibm/lotus/notes/jvm/lib/i386/libj9prt24.so [0]
5126:     file=/opt/ibm/lotus/notes/jvm/lib/i386//usr/lib/libnspr4.so [0];  generating link map
```Not certain exactly where the bug is, but the .../i386//usr/lib.... looks like a bug.

---

