---
title: "erroe wrong architecture"
date: 2009-09-26
forum: General Help
---

### Post by denisdobrovoda on 2009-09-26
so i installed ubuntu to my brand new lenovo r500 laptop. everything works fine but as soon as i try installing any kind of programme (tuxguitar, skype, configure trackpoint) simply anything i get an error i386 wrong architecture. i am average when it comes to computers and i tried to look around these forums but didnt really understand what should i do. i really want to keep using ubuntu because i like the philosophy and everything but i need some help. btw i installed 9.04 through wubi. 

many thanks
Denis

---

### Post by MelDJ on 2009-09-26
type this in terminal uname -m. that should tell you what processor you have. i think you have got the wrong software type for your processor.

---

### Post by NoaHall on 2009-09-26
Open a terminal, and put in ->
```
dpkg -i --force-architecture /location/of/file 
```

You will want to download the .deb files with "amd64" in the name. However, you can use the command I gave to force it to install.

---

### Post by denisdobrovoda on 2009-09-26
this may sound very very stupid and i dont know how this happened, but computer is telling me that i am dont have the privilege to do stuff. for example it wouldnt let me open boot etc. the terminal doesnt allow me to do stuff as well

---

### Post by NoaHall on 2009-09-26
Do it like so instead then

```
sudo dpkg -i --force-architecture /location/of/file
```
You'll then have to put in your password, which won't appear on screen, and press enter.

---

### Post by MelDJ on 2009-09-26
> **denisdobrovoda said:**
> this may sound very very stupid and i dont know how this happened, but computer is telling me that i am dont have the privilege to do stuff. for example it wouldnt let me open boot etc. the terminal doesnt allow me to do stuff as well

type sudo before the code. then it will prompt you to give your password. sudo basically means run as root or super user.

---

### Post by dcstar on 2009-09-26
> **denisdobrovoda said:**
> so i installed ubuntu to my brand new lenovo r500 laptop. everything works fine but as soon as i try **installing any kind of programme (tuxguitar, skype, configure trackpoint)** simply anything i get an error i386 wrong architecture. i am average when it comes to computers and i tried to look around these forums but didnt really understand what should i do. i really want to keep using ubuntu because i like the philosophy and everything but i need some help. btw i installed 9.04 through wubi. 

many thanks
Denis

Do not install packages you find on external sites, install packages from the repositories as they are the correct packages for your system.

Installing packages from individual sites is "Windows" thinking, the Linux way is different.

---

### Post by denisdobrovoda on 2009-09-27
all right thank you very much for your answers. i tried doing the forced installation but it didnt work and i cant install tuxguitar even through a repository. i installed ubuntu with wubi so the case probably is that i have a wrong version for my processor. what would you suggest? reinstalling the whole thing?

---

### Post by MelDJ on 2009-09-28
> **denisdobrovoda said:**
> all right thank you very much for your answers. i tried doing the forced installation but it didnt work and i cant install tuxguitar even through a repository. i installed ubuntu with wubi so the case probably is that i have a wrong version for my processor. what would you suggest? reinstalling the whole thing?

could you tell what processor you have? 32 bit or 64 bit? and was the ubuntu you got for 32 bit or 64 bit?

---

### Post by aljoriz on 2009-09-28
go to applications and look for terminal..  type:  uname -m

if you see i386 it means you have installed a 32bit version ubuntu, if you see x86_64 it means you are using the 64bit ubuntu.  

Some applications may not be compatible with 64bit.  If your processor is AMD chances are your CPU is 64bit so it is better to download and install the 64bit version of ubuntu

---

### Post by denisdobrovoda on 2009-09-28
thank you. i have 64bit version of ubuntu. i dont have amd but rather intel core 2 duo. you reckon i should switch to 32bit version of ubuntu?

---

### Post by oldos2er on 2009-09-28
> **denisdobrovoda said:**
> thank you. i have 64bit version of ubuntu. i dont have amd but rather intel core 2 duo. you reckon i should switch to 32bit version of ubuntu?

 Can you run this command in a terminal, and post the output here?
```
sudo apt-get update && sudo apt-get upgrade

```

---

### Post by denisdobrovoda on 2009-09-28
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty Release.gpg
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/main Translation-en_GB [52.6kB]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release       
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/restricted Translation-en_GB [4640B]
Get: 3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/universe Translation-en_GB [35.2kB]
Get: 4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/multiverse Translation-en_GB [47.5kB]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates Release.gpg                    
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/main Translation-en_GB         
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/restricted Translation-en_GB   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty Release            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates Release                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/main Packages                          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/multiverse Sources
Fetched 140kB in 0s (399kB/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


this is what i got

---

### Post by earthpigg on 2009-09-28
and what happens when you try to install tuxguitar, etc, from synaptic or add/remove?

and for proprietary software that isn't in synaptic or add/remove, you will want the 64 bit .deb file.

example: [http://www.skype.com/download/skype/linux/choose/](http://www.skype.com/download/skype/linux/choose/)

you would want the "Ubuntu 8.10+ 64-bit" one.


sometimes, you will come across proprietary software that is ***only available in 32bit***.... but, you can ***repackage it to 64bit*** if you want. 

i had to figure out how so i could install world of goo without the ugly force-architecture method: [http://ubuntuforums.org/showthread.php?t=1070885](http://ubuntuforums.org/showthread.php?t=1070885)

---

### Post by denisdobrovoda on 2009-10-06
i think i understand what is necessary to be done thank you very much. however, sometimes i cant do the force arch thing cause it says i need a superuser privilege. how do i get it???

---

### Post by earthpigg on 2009-10-06
> **denisdobrovoda said:**
> i think i understand what is necessary to be done thank you very much. however, sometimes i cant do the force arch thing cause it says i need a superuser privilege. how do i get it???

preface the command with 'sudo'. needed for any system-wide change to the system.

---

### Post by oldos2er on 2009-10-06
tuxguitar is in the universe repository. It looks like there is one package for all architectures, so it should work.

---

