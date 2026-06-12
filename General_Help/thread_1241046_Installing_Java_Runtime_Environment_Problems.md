---
title: "Installing Java Runtime Environment Problems"
date: 2009-08-15
forum: General Help
---

### Post by izaneartist on 2009-08-15
I hope that this it the correct place to post a thread like this if not I am sorry,but I need some help. I am new to Ubuntu and this was my first attempt to install an application via terminal.:confused:

mark@mark-laptop:~$ sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

That is what pops up when I try to install Java Runtime Environment.
I was using this site as a tutorial for install it. [http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu.html](http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu.html)

---

### Post by credobyte on 2009-08-15
Try:
```
sudo dpkg --configure -a && sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```

---

### Post by michy99 on 2009-08-15
Do as the error message suggests.```
sudo dpkg --configure -a
```

---

### Post by DaithiF on 2009-08-15
Hi,
don't worry, you haven't done anything wrong, this happens occasionally when something interrupts a package being installed and leaves things in an inconsistent state.  The solution is exactly as mentioned in the error message.  In a terminal run:
```
sudo dpkg --configure -a
```

then also run 
```
sudo apt-get update
```
and then try your java install command again

---

### Post by jmszr on 2009-08-15
izaneartist,

In the terminal type (or copy and paste):```
sudo dpkg --configure -a
```

When it asks for your password, type it in (it won't be visible - security). Press Enter - should do it,

It might be simpler for you to go to Applications > Add/Remove > Show: All Available Applications > Search:Ubuntu restricted extras > Apply Changes. When the java EULA comes up hit Tab and then Enter. 

You might want to install this also:[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) .

---

### Post by izaneartist on 2009-08-15
> **credobyte said:**
> Try:
```
sudo dpkg --configure -a && sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```
 
That didn't work Credo this is what popped up when I entered that code.

Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 2 added doc-base file(s)...
Registering documents with scrollkeeper...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  sun-java6-jre: Depends: sun-java6-bin (= 6-14-0ubuntu1.9.04) but it is not going to be installed or
                          ia32-sun-java6-bin (= 6-14-0ubuntu1.9.04) but it is not installable
                 Recommends: gsfonts-x11 but it is not going to be installed
  sun-java6-plugin: Depends: sun-java6-bin (= 6-14-0ubuntu1.9.04) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

### Post by credobyte on 2009-08-15
What if you install sun-java6-bin and try installing JRE again ?

```
sudo apt-get install sun-java6-bin
```

---

### Post by izaneartist on 2009-08-15
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  sun-java6-jre: Depends: sun-java6-bin (= 6-14-0ubuntu1.9.04) but it is not going to be installed or
                          ia32-sun-java6-bin (= 6-14-0ubuntu1.9.04) but it is not installable
                 Recommends: gsfonts-x11 but it is not going to be installed
  sun-java6-plugin: Depends: sun-java6-bin (= 6-14-0ubuntu1.9.04) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

That is what comes up after doing those codes DaithF

---

### Post by izaneartist on 2009-08-15
Credo this is what comes up
mark@mark-laptop:~$ sudo apt-get install sun-java6-bin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  sun-java6-bin: Depends: unixodbc but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
mark@mark-laptop:~$ 

Same thing. :/

---

### Post by izaneartist on 2009-08-15
jmszr, I tired to install medibuntu using the code lower in the page under Any Ubuntu and Keyring box and that same thing come up after reading and loading stuff,
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  sun-java6-jre: Depends: sun-java6-bin (= 6-14-0ubuntu1.9.04) but it is not going to be installed or
                          ia32-sun-java6-bin (= 6-14-0ubuntu1.9.04) but it is not installable
                 Recommends: gsfonts-x11 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

__

---

### Post by jmszr on 2009-08-15
izaneartist,

Have you run (in Terminal)```
sudo apt-get -f install
```?

---

### Post by izaneartist on 2009-08-15
jmszr, No but when I got my update it had to Jave Runtime Enviroment bin files or something and i had to give premission for it to install?

---

### Post by izaneartist on 2009-08-15
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.28-11 linux-headers-2.6.28-11-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

This is what comes up when I used the code jmrzr

---

### Post by michy99 on 2009-08-15
If you are talking about accepting the user agreement, use tab key to select, then enter

---

### Post by izaneartist on 2009-08-15
No, the terminal won't let me get that far.

---

### Post by izaneartist on 2009-08-15
I went to Apps.-Add/Remove- Show:Installed Apps and Sun Java 6 Runtime #-oSo did it install via terminal or when Ubuntu updated for the day? I am so confused.

---

### Post by jmszr on 2009-08-15
izaneartist,

Good question, sounds like update probably, but *shrug* as long as it's there. I suggest that you install "ubuntu-restricted-extras" as it adds a lot of useful things besides java.
You are right, it can get confusing sometimes; but there are a lot of people available on the forums quite willing to lend a hand. Hang in there.

---

### Post by izaneartist on 2009-08-15
Thank you, and everyone else that help me out today with installing Java. Now I should be able to run PCgen :D

---

