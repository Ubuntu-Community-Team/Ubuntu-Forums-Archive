---
title: "GoogleearthLinux.bin file not working"
date: 2009-09-19
forum: General Help
---

### Post by vamper on 2009-09-19
I downloaded Google earth to my desktop as a .bin file, opened the terminal window and get the following response
```
ironhead@ironhead-desktop:~$ chmod +x GoogleEarthLinux.bin 
chmod: cannot access `GoogleEarthLinux.bin': No such file or directory

```
If i try using a sudo command line I still get the same thing, It's like the file is non existent.

---

### Post by chriskin on 2009-09-19
is the file called GoogleEarthLinux or GoogleearthLinux?

i think that it's case sensitive, you have to write it exactly as it is

by the way, why do you want to install it from there?
you can install it via the ppa and have updates come to you from the update manager and it's easier to install as well

ubuntu tweak can get you google earth's ppa and the application installed and running in less than 10 clicks

---

### Post by dcstar on 2009-09-19
> **vamper said:**
> I downloaded Google earth to my desktop as a .bin file, opened the terminal window and get the following response
```
ironhead@ironhead-desktop:~$ chmod +x GoogleEarthLinux.bin 
chmod: cannot access `GoogleEarthLinux.bin': No such file or directory

```
If i try using a sudo command line I still get the same thing, It's like the file is non existent.

Of course not, Linux does not default to running programs in a directory like DOS/Windows, use specific references for binaries not in the PATH variable:

```
chmod +x ./GoogleEarthLinux.bin
./GoogleEarthLinux.bin
```

---

### Post by Soley on 2009-09-19
Silly question. In the terminal are you cd'ed to your Desktop folder? i.e. ```
cd ~/Desktop
```

Yeah, I just downloaded Google Earth to my desktop, typed 
```
cd ~/Desktop
chmod +x GoogleEarthLinux.bin
./GoogleEarthLinux.bin
```

And it worked fine.

---

### Post by Cavsfan on 2009-11-02
I guess Google Earth is not ready for Ubuntu 9.10 64 bit.
I downloaded the GoogleEarthLinux.bin file from [http://earth.google.com/download-earth.html](http://earth.google.com/download-earth.html)
Version 5.0 and tried the above commands and got the following:

```
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 5.1.3509.4636...............................................................
./setup.sh: 284: setup.data/bin/Linux/amd64/setup.gtk2: not found
./setup.sh: 299: setup.data/bin/Linux/amd64/setup.gtk: not found
The setup program seems to have failed on amd64

Fatal error, installer failed to run at all!
```Or am I doing something wrong?

---

### Post by chriskin on 2009-11-02
> **Cavsfan said:**
> I guess Google Earth is not ready for Ubuntu 9.10 64 bit.
I downloaded the GoogleEarthLinux.bin file from [http://earth.google.com/download-earth.html](http://earth.google.com/download-earth.html)
Version 5.0 and tried the above commands and got the following:

```
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 5.1.3509.4636...............................................................
./setup.sh: 284: setup.data/bin/Linux/amd64/setup.gtk2: not found
./setup.sh: 299: setup.data/bin/Linux/amd64/setup.gtk: not found
The setup program seems to have failed on amd64

Fatal error, installer failed to run at all!
```Or am I doing something wrong?


why would you install it that way? it is on the official repositories of google (or is it on medibuntu?). add them through ubuntu tweak or by yourself and install it from there :)

---

### Post by Cavsfan on 2009-11-03
I guess because I am too much of a noob! I had updated to 9.10 too early I believe.
Back to Jaunty for me. I had everything working real well on Jaunty!
At least I am learning though. Thank God ignorance doesn't usually last forever!
Thanks though!

---

