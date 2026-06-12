---
title: "How to install asterisk on UBUNTU 8.10 ?"
date: 2009-11-14
forum: General Help
---

### Post by ankurTheKing on 2009-11-14
Hello everybody,
I am pretty familiar with ubuntu. In my home and office, we are using ubuntu, everybody love that.:p
I have a PC for testing purpose, where I have installed ubuntu 8.10

I am interested in installing VOIP server tool called [Asterisk]("http://www.asterisk.org/") but I found some difficulties,
Can anybody tell me from bottom ?

I read the following document
[http://www.asteriskguru.com/tutorials/asterisk_gui.html](http://www.asteriskguru.com/tutorials/asterisk_gui.html)

I have completed step  **_2. Preparation.   _**After that I dont know what to do ?
Any help would be appreciated.:D

---

### Post by Monotoko on 2009-11-14
Hello :)

After the preparation part, yopu must now make, compile and build the program, you will have to do this quite a bit if you are installing from source, but its quite simple when you get the hang of it, you must first cd to the correct directry

```
cd /usr/src/asterisk-gui/
```
(if you downloaded it into /usr/src as it suggested, if not, find where you put it and go there)

one your there, run:
```
sudo make
```
This checks your build environement, if you get an error, you must download the relevant package, as it will be missing a package to make the program.

once that is done without errors, run:
```
sudo make install
```

Then go onto the configuration step :)

---

### Post by ankurTheKing on 2009-11-14
Thanks for you fastest support.
I changed directory.
I had extracted files from ZIP to that dir.
When I enter ```
sudo make
```it gave following error:

```
make: *** No targets specified and no makefile found.  Stop.
```

---

