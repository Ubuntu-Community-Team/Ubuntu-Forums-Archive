---
title: "need help installing this program for school"
date: 2011-09-24
forum: General Help
---

### Post by dan0804smith on 2011-09-24
these are the instructions:

To download manually the plug-in on Linux for Netscape 7.1+, or Firefox 1.0+, or Mozilla 1.6+, you will have to download the ALEKS package file and save it on your computer in the "Java VM lib/ext" directory.

For instance, with the Sun Java VM version 1.4.1, this directory is usually:

/usr/java/j2re1.4.1/lib/ext/

or

/usr/local/j2re1.4.1_02/lib/ext/

If you are unsure, please check with your system administrator.

Installation instructions:

   1. Point your mouse at the link below and press down your mouse left button.
          * aleksPack10.jar (6.4M) 

   2. A pop-up window should appear asking you "What should Netscape do with this file?".
   3. In the menu choose the option "Save this file to disk" and click on "OK".

   4. A new window should appear to ask you where you want to save the file.

   5. Save the file in your home directory by clicking on the button "Save" to start the transfer.

   6. Open a terminal and type: (adapt the directory to your own Java VM lib/ext directory)

      > su root
      Password: (Type in the root password)
      > cp aleksPack10.jar /usr/java/j2re1.4.1/lib/ext/
      > exit

   7. Restart Netscape 







whenever i try to run su root i type in my password and it says authentication failed


i tried doing sudo cp aleksPack10.jar /usr/java/j2re1.4.1/lib/ext/

and sudo cp aleksPack10.jar /daniel/java/j2re1.4.1/lib/ex

but both times it read:

 daniel@daniel-laptop:~$  sudo cp aleksPack10.jar /daniel/java/j2re1.4.1/lib/ext
cp: cannot create regular file `/daniel/java/j2re1.4.1/lib/ext': No such file or directory
daniel@daniel-laptop:~$  sudo cp aleksPack10.jar /usr/java/j2re1.4.1/lib/ext/
cp: cannot create regular file `/usr/java/j2re1.4.1/lib/ext/': No such file or directory


file is in the home folder

help... please?

---

### Post by dan0804smith on 2011-09-24
running ubuntu 10.04 lts btw

---

### Post by haqking on 2011-09-24
> **dan0804smith said:**
> these are the instructions:

To download manually the plug-in on Linux for Netscape 7.1+, or Firefox 1.0+, or Mozilla 1.6+, you will have to download the ALEKS package file and save it on your computer in the "Java VM lib/ext" directory.

For instance, with the Sun Java VM version 1.4.1, this directory is usually:

/usr/java/j2re1.4.1/lib/ext/

or

/usr/local/j2re1.4.1_02/lib/ext/

If you are unsure, please check with your system administrator.

Installation instructions:

   1. Point your mouse at the link below and press down your mouse left button.
          * aleksPack10.jar (6.4M) 

   2. A pop-up window should appear asking you "What should Netscape do with this file?".
   3. In the menu choose the option "Save this file to disk" and click on "OK".

   4. A new window should appear to ask you where you want to save the file.

   5. Save the file in your home directory by clicking on the button "Save" to start the transfer.

   6. Open a terminal and type: (adapt the directory to your own Java VM lib/ext directory)

      > su root
      Password: (Type in the root password)
      > cp aleksPack10.jar /usr/java/j2re1.4.1/lib/ext/
      > exit

   7. Restart Netscape 







whenever i try to run su root i type in my password and it says authentication failed


i tried doing sudo cp aleksPack10.jar /usr/java/j2re1.4.1/lib/ext/

and sudo cp aleksPack10.jar /daniel/java/j2re1.4.1/lib/ex

but both times it read:

 daniel@daniel-laptop:~$  sudo cp aleksPack10.jar /daniel/java/j2re1.4.1/lib/ext
cp: cannot create regular file `/daniel/java/j2re1.4.1/lib/ext': No such file or directory
daniel@daniel-laptop:~$  sudo cp aleksPack10.jar /usr/java/j2re1.4.1/lib/ext/
cp: cannot create regular file `/usr/java/j2re1.4.1/lib/ext/': No such file or directory


file is in the home folder

help... please?

First of all root is locked by default in Ubuntu so su root wont work.  We use sudo for admin actions if you enabled the root account then there was no need and not recommended.

as for your copy commands i cant quite understand them.

where is the file ? in your home correct ?

where is the file supposed to be going to ?

Does the java dir exist in your /usr ?

---

### Post by dan0804smith on 2011-09-24
perhaps i could download the windows version and run in wine?

---

### Post by haqking on 2011-09-24
> **dan0804smith said:**
> perhaps i could download the windows version and run in wine?

no idea, i dont know what the app is ?

or use virtualisation [www.virtualbox.org](www.virtualbox.org)

---

### Post by oldos2er on 2011-09-24
> **dan0804smith said:**
> 
i tried doing sudo cp aleksPack10.jar /usr/java/j2re1.4.1/lib/ext/

and sudo cp aleksPack10.jar /daniel/java/j2re1.4.1/lib/ex

but both times it read:

 daniel@daniel-laptop:~$  sudo cp aleksPack10.jar /daniel/java/j2re1.4.1/lib/ext
cp: cannot create regular file `/daniel/java/j2re1.4.1/lib/ext': No such file or directory
daniel@daniel-laptop:~$  sudo cp aleksPack10.jar /usr/java/j2re1.4.1/lib/ext/
cp: cannot create regular file `/usr/java/j2re1.4.1/lib/ext/': No such file or directory


file is in the home folder

The path to your home folder is /home/daniel/ rather than /daniel.

---

### Post by haqking on 2011-09-24
> **oldos2er said:**
> The path to your home folder is /home/daniel/ rather than /daniel.

yeah i was gonna say that first but i saw in his second command:

daniel@daniel-laptop:~$ sudo cp aleksPack10.jar /usr/java/j2re1.4.1/lib/ext/

he was in home already and he said the file was in there

---

### Post by dan0804smith on 2011-09-24
its just a jar file.  is there a easy way to run that?

---

### Post by haqking on 2011-09-24
> **dan0804smith said:**
> its just a jar file.  is there a easy way to run that?

There page says only for Windows or MacOSX [http://www.aleks.com/support/system_requirements](http://www.aleks.com/support/system_requirements)

If you cant get it to work then i suggest using virtualisation maybe. or possibly wine, i dont know much about using wine though you will need to look at that.
Cheers

---

### Post by dan0804smith on 2011-09-24
> **haqking said:**
> There page says only for Windows or MacOSX [http://www.aleks.com/support/system_requirements](http://www.aleks.com/support/system_requirements)

If you cant get it to work then i suggest using virtualisation maybe. or possibly wine, i dont know much about using wine though you will need to look at that.
Cheers

at the bottom of that it says Linux "Experts" only: How can I use ALEKS on Linux anyway?

---

### Post by haqking on 2011-09-24
> **dan0804smith said:**
> at the bottom of that it says Linux "Experts" only: How can I use ALEKS on Linux anyway?

i cant see that anywwhere ? thought it is late at night here.

the only reference i can see to Unix/Linux is here [http://www.aleks.com/support/troubleshooting](http://www.aleks.com/support/troubleshooting)

---

### Post by Hakunka-Matata on 2011-09-24
[http://www.aleks.com/downloads/linux_jvm](http://www.aleks.com/downloads/linux_jvm)

---

### Post by haqking on 2011-09-25
> **Hakunka-Matata said:**
> [http://www.aleks.com/downloads/linux_jvm](http://www.aleks.com/downloads/linux_jvm)

ahhh nice, i couldnt find that anywhere last night, way too late..LOL

so yeah to OP

do not su root (as root should be locked by default)

Download to home under your own account then from terminal:

```
sudo cp aleksPack10.jar /usr/java/j2re1.4.1/lib/ext/
```

presuming that aleksPack10.jar exists in your home and that the /usr/java/xxx exists.

can you not

```
java -jar aleksPack10.jar
```

?

---

