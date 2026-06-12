---
title: "Command line program"
date: 2009-07-27
forum: General Help
---

### Post by Robbyx on 2009-07-27
I am trying to run concordance, a command line program. When I do it I see the following results:

> rob@rob-desktop:~$ whereis libconcord
libconcord: /usr/local/lib/libconcord.la /usr/local/lib/libconcord.so /usr/local
rob@rob-desktop:~$ concordance
bash: concordance: command not found

It seems to me that I am in the wrong directory. Could someone please tell me how to run it?

---

### Post by jonobr on 2009-07-27
does 

```
which concordance
```

give a results (im assuming thats the executable?)

if not then

```
sudo find / -name concordance
```

see what it throws back

---

### Post by komputes on 2009-07-27
I don't see concordance as a file in any the ubuntu packages.

You can try to find it
```
find /usr | grep concordance
```
or
```
find /home | grep concordance
```

---

### Post by Robbyx on 2009-07-27
Results:

> rob@rob-desktop:~$ which concordance
rob@rob-desktop:~$ sudo find / -name concordance
[sudo] password for rob: 
/home/rob/source/concordance-0.21/concordance
rob@rob-desktop:~$ 


Concordance is a program that runs the Logitech Harmony remotes.

---

### Post by Yellow Pasque on 2009-07-27
How did you install it? If you use this PPA, the executable will be in /usr/bin
[https://launchpad.net/~mathieu-tl/+archive/ppa](https://launchpad.net/~mathieu-tl/+archive/ppa)

---

### Post by jonobr on 2009-07-28
if you type

```
cd /home/rob/source/concordance-0.21
```

and then 

```
./concordance
```
(above command is dot slash)

What happens

---

### Post by Robbyx on 2009-07-28
> **jonobr said:**
> if you type

```
cd /home/rob/source/concordance-0.21
```

and then 

```
./concordance
```
(above command is dot slash)

What happens

```
rob@rob-desktop:~$ cd /home/rob/source/concordance-0.21
rob@rob-desktop:~/source/concordance-0.21$ ./concordance
bash: ./concordance: is a directory
rob@rob-desktop:~/source/concordance-0.21/concordance$ cd /home/rob/source/concordance-0.21/concordance/
rob@rob-desktop:~/source/concordance-0.21/concordance$ 
rob@rob-desktop:~/source/concordance-0.21/concordance$ dir
aclocal.m4	concordance.c  config.sub    depcomp	    install-sh	     Makefile.am  README
autom4te.cache	config.guess   configure     INSTALL.linux  INSTALL.windows  Makefile.in  win
concordance.1	config.h.in    configure.ac  INSTALL.mac    ltmain.sh	     missing
rob@rob-desktop:~/source/concordance-0.21/concordance$ 


```

---

### Post by nikhilk on 2009-07-28
I would suggest installing from the PPA Temüjin mentioned as you will get the same version and benifit of managing it through the pacakage manager.

Installing any application from source is a mantainance hassle and should always be your last option.

I think that is the source code for concordance and you need to build it first.

You need to follow the typical three steps for installing from source
```
cd /home/rob/source/concordance-0.21/concordance/
./configure
make
sudo make install

```

---

### Post by Robbyx on 2009-07-28
> **jonobr said:**
> if you type

```
cd /home/rob/source/concordance-0.21
```

and then 

```
./concordance
```
(above command is dot slash)

What happens

> **Temüjin said:**
> How did you install it? If you use this PPA, the executable will be in /usr/bin
[https://launchpad.net/~mathieu-tl/+archive/ppa](https://launchpad.net/~mathieu-tl/+archive/ppa)

I did use that PPA, but the string in my software sources was slightly different so I have just changed it to the entry on the site(the PPA in the sources string was not in my original entry). I also added the authentication key which I had not been able to find originally. On exiting the software sources it ran the update with no error messages but under the various bin and sbin directories in my version of ubuntu Intrepid I can not find an executable called concordance(+*).

---

