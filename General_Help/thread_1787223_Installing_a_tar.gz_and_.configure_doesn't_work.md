---
title: "Installing a tar.gz and ./configure doesn't work"
date: 2011-06-20
forum: General Help
---

### Post by xxguitarist on 2011-06-20
Attempting to install "hullform" ( [http://www.hullform.com/](http://www.hullform.com/) )
It is available as a tar.gz.
I unarchive this to /usr/local/src, and attempt to ./configure from this location.


```
andrew@andrew-desktop:/usr/local/src$ ./configure
bash: ./configure: No such file or directory

```

I have attempted to ./configure from within the folders shown below.

```
andrew@andrew-desktop:/usr/local/src$ ls
header.dxf  hf9p.tar  hullform      hullstat.cfg  project     template
help        hulldata  hullform.cfg  output        tables.dxf
```

I also have ensured that I have build-essentials installed/up to date.

:confused:

Using 10.04, by the way.

Help appreciated.

---

### Post by haqking on 2011-06-20
> **xxguitarist said:**
> Attempting to install "hullform" ( [http://www.hullform.com/](http://www.hullform.com/) )
It is available as a tar.gz.
I unarchive this to /usr/local/src, and attempt to ./configure from this location.


andrew@andrew-desktop:/usr/local/src$ ./configure
bash: ./configure: No such file or directory


I have attempted to ./configure from within the folders shown below.

andrew@andrew-desktop:/usr/local/src$ ls
header.dxf  hf9p.tar  hullform      hullstat.cfg  project     template
help        hulldata  hullform.cfg  output        tables.dxf

I also have ensured that I have build-essentials installed/up to date.

:confused:

Help appreciated.

sudo ./configure

---

### Post by xxguitarist on 2011-06-20
> **haqking said:**
> sudo ./configure

Thanks, had tried that previously. Double checked just now. 
```
andrew@andrew-desktop:/usr/local/src$ sudo ./configure
[sudo] password for andrew: 
sudo: ./configure: command not found

```

---

### Post by dFlyer on 2011-06-20
It's been a while since I compiled a program. Did you check for the Install readme. It will tell you what you have to do.

---

### Post by xxguitarist on 2011-06-20
> **dFlyer said:**
> It's been a while since I compiled a program. Did you check for the Install readme. It will tell you what you have to do.

Wish there was one.

I dug all around for it.
The "Help" folder shown in the ls, seems to be text docs for loading the help menu for program operation.

---

### Post by haqking on 2011-06-20
> **xxguitarist said:**
> Wish there was one.

I dug all around for it.
The "Help" folder shown in the ls, seems to be text docs for loading the help menu for program operation.


I just looked in the contents of that file and there is no configure file

---

### Post by xxguitarist on 2011-06-20
> **haqking said:**
> I just looked in the contents of that file and there is no configure file

I also looked for configure.asdf files, and did not see any. There were some asdf.cfg files, however. I wasn't sure which were needed.

What is the appropriate install approach, given this?

---

### Post by haqking on 2011-06-20
> **xxguitarist said:**
> I also looked for configure.asdf files, and did not see any. There were some asdf.cfg files, however. I wasn't sure which were needed.

What is the appropriate install approach, given this?


Well the ./configure invokes a script that the developer should proved in the binaries for you to run.

there isnt one there.

mmm im not good enough with compiling to give you an answer im afraid on this one, you could install a virtual machine and run the windows .exe ?

though no configure file would suggest no configure option so you could go straight ahead to make ?

---

### Post by haqking on 2011-06-20
i just played a little, there is a list of shared libraries required on the website.

if you make sure they are present.

then from directory ./hullform 

see if that works

---

### Post by d3v1150m471c on 2011-06-20
while in the extracted folder do:
```

ls

```...then post the results... ./configure might not even exist. does it have a read me file? no source tar is the same, usually similar but not always.

btw, **haqking**, i love that avatar :)

---

### Post by haqking on 2011-06-20
> **d3v1150m471c said:**
> while in the extracted folder do:
```

ls

```...then post the results... ./configure might not even exist. does it have a read me file? no source tar is the same, usually similar but not always.

btw, **haqking**, i love that avatar :)

i downloaded the file and looked at it, there is no configure script.

there is a hullform which can be run if the shared libraries are installed as detailed on the website

oh and yeah i love my avatar ;-)

---

### Post by xxguitarist on 2011-06-20
> **d3v1150m471c said:**
> while in the extracted folder do:
```

ls

```...then post the results... ./configure might not even exist. does it have a read me file? no source tar is the same, usually similar but not always.

btw, **haqking**, i love that avatar :)

This is in the OP. I added code tags to increase visibility.

---

### Post by xxguitarist on 2011-06-20
> **haqking said:**
> i just played a little, there is a list of shared libraries required on the website.

if you make sure they are present.

then from directory ./hullform 

see if that works

Looking around now for the libraries.

./hullform is requesting one, so this may be onto something.

[edit]

libXm.so.3 is needed, and libmotif3 did not seem to provide it.

---

### Post by xxguitarist on 2011-06-20
Runs easily enough in wine. I don't like doing things that way, but it seems it accomplishes the end goal without requiring a reboot into windows at least.

---

