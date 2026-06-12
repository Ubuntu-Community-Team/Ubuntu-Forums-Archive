---
title: "newbie: installing new software + java??"
date: 2009-08-21
forum: General Help
---

### Post by peter_kint on 2009-08-21
Hello,
Recently co-installed ubuntu 9.04 besides my windows vista.
Would like to install a the linux version of physics simulation application (i am a HS  physics teacher) which worked quite well under vista.
I downloaded the .bin file (Phet-installer_linux.bin) from
[http://phet.colorado.edu/tech_support/index.php](http://phet.colorado.edu/tech_support/index.php) to my ubuntu desktop.

**Q1: What now? **(clicking it to open gives 'could not display home/peter/desktop/Phet-installer_linux.bin

The application program needs java 1.5 or higher.

**Q2: How can I see if I have java and , if so, which version I have?**
**Q3: How to install the latest/best version of Java in Ubuntu?**

Sorry for my ignorance (it's really very new...)
Thx for reading and maybe also answering.

Peter

---

### Post by P4man on 2009-08-21
Hi and welcome :)

The usual way of installing software on ubuntu is through add/remove programs in the application menu. You will find java there (sun java 6 runtime) although you may need to enable the universe repository first. Change the filter to "show all available apps".

The usual way we tell you how to do it, is through the command line, since you can then copy paste the command in the terminal. So you can also type:

```
sudo apt-get install sun-java6-bin
```

Now that file you downloaded, you will have to change its permissions before its allowed to execute. Just right click it, properties, permissions and check the "allow executing as program". Then you can double click it, and it will hopefully install.

---

### Post by peter_kint on 2009-08-21
> **P4man said:**
> Hi and welcome :)

The usual way of installing software on ubuntu is through add/remove programs in the application menu. You will find java there (sun java 6 runtime) although you may need to enable the universe repository first. Change the filter to "show all available apps".

The usual way we tell you how to do it, is through the command line, since you can then copy paste the command in the terminal. So you can also type:

```
sudo apt-get install sun-java6-bin
```Now that file you downloaded, you will have to change its permissions before its allowed to execute. Just right click it, properties, permissions and check the "allow executing as program". Then you can double click it, and it will hopefully install.

Thx P4man,
The JAVA thing is solved!
As for the phet-installer_linux.bin file: he keeps on saying it is an 'unknown file type'...
Peter

---

### Post by P4man on 2009-08-21
then open a terminal, and cd to the folder where you downloaded it (cd Desktop)
Then type:
```
./Phet-installer_linux.bin
```

Careful, everything is case sensitive in linux. You can however just type the first few letters, then press tab for autocomplete

---

### Post by Operan on 2009-08-21
> **P4man said:**
> then open a terminal, and cd to the folder where you downloaded it (cd Desktop)
Then type:
```
./Phet-installer_linux.bin
```

Careful, everything is case sensitive in linux. You can however just type the first few letters, then press tab for autocomplete

Sure that this file can be excecuted. chmod it to 755 or 777:
> chmod 755 Phet-installer_linux.bin

---

### Post by P4man on 2009-08-21
> **Operan said:**
> chmod it to 755 or 777:

That does the same as right click, permissions, "allow execution".
I know chmod 775 is shorter to type, but lets not freak out the new users all too much :) 

It was just my mistake, I thought .bin files would be executed upon double click once the permissions where set, but not so. That's really something they should solve, something as trivial as downloading an installer and running it shouldn't need a terminal, even if downloading an installer isn't the most common way to install anything on linux.

I suggest everyone votes for this idea here:

[http://brainstorm.ubuntu.com/idea/9591/](http://brainstorm.ubuntu.com/idea/9591/)

---

### Post by peter_kint on 2009-08-22
> **P4man said:**
> That does the same as right click, permissions, "allow execution".
I know chmod 775 is shorter to type, but lets not freak out the new users all too much :) 

It was just my mistake, I thought .bin files would be executed upon double click once the permissions where set, but not so. That's really something they should solve, something as trivial as downloading an installer and running it shouldn't need a terminal, even if downloading an installer isn't the most common way to install anything on linux.

I suggest everyone votes for this idea here:

[http://brainstorm.ubuntu.com/idea/9591/](http://brainstorm.ubuntu.com/idea/9591/)

Thx guys, but it doesn't work. This is my terminal screen:

peter@peter-desktop:~$ cd Desktop
peter@peter-desktop:~/Desktop$ ./PhET-Installer_linux.bin
Installer payload initialization failed. This is likely due to an incomplete or corrupt downloaded file.
peter@peter-desktop:~/Desktop$ chmod 755 PhET-Installer_linux.bin 
peter@peter-desktop:~/Desktop$ chmod 777 PhET-Installer_linux.bin
peter@peter-desktop:~/Desktop$ chmod 775 PhET-Installer_linux.bin
peter@peter-desktop:~/Desktop$ 

 (I downloaded it again, but everything is the same)
Maybe the downloaded file is corrupt indeed.
**Q1: But then it is strange that the chmod thing doesn't say anything?**

Other issue (should I start a new thread for this?)
**Q2: JAVA PROBLEM? **: I can run Java-applets. But when I visit some websites, the applets simply don't pop-up. Is this something to do with the interaction between JAVA and FIREFOX?
This is the website with the apllets: [http://www.walter-fendt.de/ph14e/](http://www.walter-fendt.de/ph14e/)
When I boot in Windows Vista -Firefox the applets work fine

---

### Post by P4man on 2009-08-22
> **peter_kint said:**
> Thx guys, but it doesn't work. This is my terminal screen:

peter@peter-desktop:~$ cd Desktop
peter@peter-desktop:~/Desktop$ ./PhET-Installer_linux.bin
Installer payload initialization failed. This is likely due to an incomplete or corrupt downloaded file.
peter@peter-desktop:~/Desktop$ chmod 755 PhET-Installer_linux.bin 
peter@peter-desktop:~/Desktop$ chmod 777 PhET-Installer_linux.bin
peter@peter-desktop:~/Desktop$ chmod 775 PhET-Installer_linux.bin
peter@peter-desktop:~/Desktop$ 

 (I downloaded it again, but everything is the same)
Maybe the downloaded file is corrupt indeed.

**Q1: But then it is strange that the chmod thing doesn't say anything?**

Hmm.. I downloaded that file the first time you had problems with it to try it out, I had no such issues here? It installed just fine (except its not making any menu items which is kinda annoying). But chmod wouldn't know the file is corrupt though, it just sets some attributes.

can you download the file from somewhere else?

> Other issue (should I start a new thread for this?)
**Q2: JAVA PROBLEM? **: I can run Java-applets. But when I visit some websites, the applets simply don't pop-up. Is this something to do with the interaction between JAVA and FIREFOX?
This is the website with the apllets: [http://www.walter-fendt.de/ph14e/](http://www.walter-fendt.de/ph14e/)
When I boot in Windows Vista -Firefox the applets work fine


Maybe  you didnt install the java plugin, only the JRE. 

```
sudo apt-get install sun-java6-plugin
```

restart firefox.

---

### Post by P4man on 2009-08-22
FWIW, check the file size. Here is what i get:

```
bob@bob-desktop:~/Desktop$ ls -l PhET-Installer_linux.bin 
-rwxr-xr-x 1 bob bob **83004743** 2009-08-21 17:27 PhET-Installer_linux.bin
bob@bob-desktop:~/Desktop$ 
```

---

### Post by peter_kint on 2009-08-29
> **P4man said:**
> FWIW, check the file size. Here is what i get:

```
bob@bob-desktop:~/Desktop$ ls -l PhET-Installer_linux.bin 
-rwxr-xr-x 1 bob bob **83004743** 2009-08-21 17:27 PhET-Installer_linux.bin
bob@bob-desktop:~/Desktop$ 
```

That's weird...
I get:

peter@peter-desktop:~$ cd Desktop
peter@peter-desktop:~/Desktop$ ls -l PhET-Installer_linux.bin
-rwxrwxr-x 1 peter peter** 83005072** 2009-08-21 17:18 PhET-Installer_linux.bin
peter@peter-desktop:~/Desktop$ 

I've got a few bytes more ??
I did it all over again with the same result.

---

### Post by 3rdalbum on 2009-08-29
It's perfectly normal that chmod doesn't say anything. If it couldn't find the file, or if you didn't own the file, then it would give an error message; otherwise, it says nothing.

---

### Post by P4man on 2009-08-29
Heh thats bizarre. I did recover that file from my trash, but I kind fail to see how that would add some bytes? Ill try again tomorrow, but first tell me, are you using 32 or 64 bit ubuntu ? if you're unsure, post the output of "uname -a"

---

