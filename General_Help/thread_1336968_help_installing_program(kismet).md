---
title: "help installing program(kismet)"
date: 2009-11-25
forum: General Help
---

### Post by TheLazyGenius on 2009-11-25
when i configure this program it messes up.

configure: error: Failed to find libcurses or libncurses.  Install them or disable building the Kismet client with --disable-client.  Disabling the client is probably not something you want to do normally.


a true ubuntu beginner, so an informative to do list is appreciated. thank you

---

### Post by raktarok on 2009-11-25
You need to install the libncurses package. I am assuming that you know all about the handy apt-get tool, so do this:
```
sudo apt-get install libncurses5
```
(5 is the version available on my computer, and it should be the same in yours too, assuming that you have not changed your software sources drastically)

But after doing this, you may encounter other dependency problems similar to this. So the best way to go about would probably be installing 'auto-apt'. This automatically handles the configure process and saves a lot of hassle.
```
sudo apt-get install auto-apt
```

These two steps may take some time, depending on your internet speed.
```
sudo auto-apt update
sudo auto-apt updatedb && sudo auto-apt update-local 
```

Now go to the directory containing kismet source code and do this:
```
sudo auto-apt run ./configure
```

This will try to find the packages on which kismet depends, and installs them for you. But sometimes, auto-apt may fail, and in that case you will have to search for the relevant package manually. 

Why are you trying to build it from the source anyway? Just install it from the repositories (if you don't need the latest version of kismet) That should be the laziest way of doing things :)

---

### Post by TheLazyGenius on 2009-11-25
wow, thanks. how would i get it form the repositories. I looked in add/delete programs....


like sudo apt-get install kismet????


and are you the -c that has written articles for phrack?

---

### Post by jacobs444 on 2009-11-25
go to system>administration>synaptic and search for what you are looking for, and using apt-get,  you did get it from the repos, add remove is the dumbed down version of synaptic.

---

### Post by TheLazyGenius on 2009-11-25
thanks

---

### Post by Halc10n_z3r0 on 2009-12-17
> **raktarok said:**
> You need to install the libncurses package. I am assuming that you know all about the handy apt-get tool, so do this:
```
sudo apt-get install libncurses5
```(5 is the version available on my computer, and it should be the same in yours too, assuming that you have not changed your software sources drastically)

But after doing this, you may encounter other dependency problems similar to this. So the best way to go about would probably be installing 'auto-apt'. This automatically handles the configure process and saves a lot of hassle.
```
sudo apt-get install auto-apt
```These two steps may take some time, depending on your internet speed.
```
sudo auto-apt update
sudo auto-apt updatedb && sudo auto-apt update-local 
```Now go to the directory containing kismet source code and do this:
```
sudo auto-apt run ./configure
```This will try to find the packages on which kismet depends, and installs them for you. But sometimes, auto-apt may fail, and in that case you will have to search for the relevant package manually. 

Why are you trying to build it from the source anyway? Just install it from the repositories (if you don't need the latest version of kismet) That should be the laziest way of doing things :)


Wow thanks for this! It finally helped me to install Kismet correctly, and I even used auto-apt to get Hydra to correctly install. Great advice :)

---

