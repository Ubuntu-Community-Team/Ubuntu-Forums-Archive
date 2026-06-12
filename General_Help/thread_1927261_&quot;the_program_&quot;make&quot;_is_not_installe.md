---
title: "&quot;the program &quot;make&quot; is not installed&quot;?"
date: 2012-02-17
forum: General Help
---

### Post by grumol on 2012-02-17
i'm trying out lubuntu on one of my partitions, and i already knew from my ubuntu 11.10, that i have to do a little work in terminal to get ralink rt5370sta to work -- ok, but when i get to the command "make", i get a response "the program "make" is not installed", so i apt-get "make", and get "the package "make" is not available" -- i've done this procedure on ubuntu several times(cause it loses wifi when i update), so i know this works 

this is the stable release, installed last night

thanks

---

### Post by jonobr on 2012-02-17
do you get anything from running

```
which make
```

if not then you need to install gcc

---

### Post by m_duck on 2012-02-17
You can probably solve this by installing the package **build-essential** which installs a whole load of tools for compiling software.

---

### Post by jonobr on 2012-02-17
True indeed m_duck,

---

### Post by RRummel on 2012-02-17
Thank for your response i tried them out however the one below is not working. the color does not change the one i have inserted. Kindly advice.#D8D8D8

---

### Post by jonobr on 2012-02-17
Hello


When you run 

```
which make
```

you should get some response, 
please post results of that here.

---

### Post by grumol on 2012-02-17
if you mean to run "which make" in terminal, i did , nothing happens

---

### Post by jonobr on 2012-02-17
then you need to ```
sudo apt-get install build-essential

```

---

### Post by grumol on 2012-02-17
and this is part of the response i get in terminal after entering that command:

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 build-essential : Depends: libc6-dev but it is not installable or
                            libc-dev but it is not installable
                   Depends: gcc (>= 4:4.4.3) but it is not installable
                   Depends: g++ (>= 4:4.4.3) but it is not going to be installed
                   Depends: make but it is not installable
                   Depends: dpkg-dev (>= 1.13.5) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

---

### Post by Rodney9 on 2012-02-17
Go to > Menu - System Tools - Synaptic

Then in Synaptic select > Edit - Fix Broken Packages

When that is successful search for build-essential in Synaptic and install it.



For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by grumol on 2012-02-18
thanks, but i had already done that, with no luck -- for some reason i can run some programs, and not others, as if not all the packages were downloaded -- and i can't get wifi without "make", so i can't download the packages -- even tried aptoncd, from another install, no good 

somethings must be wrong with this install, so i'm burning another cd and re-installing -- thanks for trying

---

### Post by m_duck on 2012-02-18
Ah, so wireless hasn't worked since Ubuntu was installed?

It is the irritating catch 22 with Linux quite often - one needs wireless drivers to get online so that one may download wireless drivers.

If it is possible for you to connect via ethernet, you could do that, get up to date and install the required packages (and deps) through that to enable you to compile your wireless drivers?

---

