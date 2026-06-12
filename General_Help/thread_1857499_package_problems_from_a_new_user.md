---
title: "package problems from a new user"
date: 2011-10-10
forum: General Help
---

### Post by Wesics on 2011-10-10
Hi, all! I am a brand new linux user. I have had ubuntu 11.04 installed for about two weeks now, and all was great until I started getting the following error message when trying to download software: 
          E: dpkg was interrupted, you must manually run 'sudo          
         dpkg-- configure-a' to correct the problem.
         E:_cache->open() failed, please report.
Now I cannot install any new software, I have tried to run the command from the error but it says it is an unknown command. Please help I really was liking Ubuntu before this, and I really don't want to have to go back to Windows

Thank fr any assistance,
-wesics

---

### Post by WasMeHere on 2011-10-10
Try again from the terminal window to run the command (cut and paste)!
```
sudo dpkg --configure -a
```
This should configure all packages (that are not already configured).

Run also 
```
sudo apt-get update
sudo apt-get upgrade
```
and repeat these 3 command lines!

If still no luck, don't quit, come back with a new post, because there are many of us here to help you.

Good luck discovering Ubuntu :-)
Olle

---

### Post by Wesics on 2011-10-10
Olle,
Thank you for your help, I tried the command you posted but this is the error that I got:

dpkg: error: unknown option --configure-a

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !

Does this make sense, how should I proceed?

Thanks again
-Wesics

PS I copied and pasted exactly as you posted.

---

### Post by WasMeHere on 2011-10-10
Sorry: typo; run
```
sudo dpkg --configure -a
```
with a *space* between configure and -a

---

### Post by Wesics on 2011-10-10
Olle,

i ran the command and this time it executed, however I dont think that it fixed the problem. The following is what is displayed:
dpkg: dependency problems prevent configuration of openjdk-6-jre-lib:
 openjdk-6-jre-lib depends on openjdk-6-jre-headless (>= 6b17); however:
  Package openjdk-6-jre-headless is not installed.
dpkg: error processing openjdk-6-jre-lib (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 openjdk-6-jre-lib

I'm not sure what this means, but I can open synaptic package manager now, but it gives an error stating that there is a broken package. I still cannot install new software Also here is the error that I get from the software center:
 There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks.

---

### Post by WasMeHere on 2011-10-10
Try to remove openjdk-6-jre-lib

```
sudo apt-get remove openjdk-6-jre-lib
```

And then repeat all 3 command in my previous post?
```
sudo update
sudo upgrade
sudo dpkg --configure -a

sudo update
sudo upgrade
sudo dpkg --configure -a

```
Finally reinstall openjdk:
```
sudo apt-get install openjdk-6-jre-lib
```

---

### Post by Wesics on 2011-10-10
Olle,

I was able to remove the file that seemed to be causing the problem. I can now install software, thank you so much for the assistance.

-Wesics

---

### Post by WasMeHere on 2011-10-10
Please mark the thread SOLVED
have fun
Olle

---

