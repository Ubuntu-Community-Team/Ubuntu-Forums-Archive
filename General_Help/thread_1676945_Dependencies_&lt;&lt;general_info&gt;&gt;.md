---
title: "Dependencies &lt;&lt;general info&gt;&gt;"
date: 2011-01-27
forum: General Help
---

### Post by layers on 2011-01-27
I've installing "things" recently, but I always get messages of this sort:

```
ibo@ibo-laptop:~/Downloads$ sudo apt-get install default-jre
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  default-jre: Depends: default-jre-headless (= 1.6-34) but it is not going to be installed
               Depends: openjdk-6-jre (>= 6b14) but it is not going to be installed
  frostwire: Depends: default-jre-headless but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
ibo@ibo-laptop:~/Downloads$ 
```

I couldn't find anything on the web, as in some kind of a definition, like what dependencies are and how are they caused; and most importantly, how are they fixed. Could perhaps, someone explain what this, for instance, means?

---

### Post by James_Lochhead on 2011-01-28
**What a dependency is:**

In Unix it is common for programs to use features contained in other programs. A program that uses the features of another program therefore needs the other program to be installed in order to function.

A dependency is simply any program that program X requires in order to work.

For example, if program X requires programs Y and Z to run, Y and Z would be called the "dependencies".

**A bit more on software management to put it in a better context:**

The most common form of software management in Linux is package management. Programs are bundled in to archive files (if you don't know what an archive file is: think .zip file) called packages, then installed using a package management system. 

This is obviously a good way of doing things as it resolves dependencies for the user, meaning that a user is generally shielded from having to install each dependency individually (which is very time consuming).

**Your specific error:**

I think your problem might be that you are trying to install Java in a strange way. The "default-jre" you are trying to install is the openjdk-6-jre.

Try: sudo apt-get install openjdk-6-jre

Although this should be installed by default in 10.04 and 10.10.

The package you were trying to install "default-jre" is a meta package: a package that contains just dependencies and no program, used to install other packages easily.

---

### Post by layers on 2011-01-28
I see. except I don't see how the whole dependency thing being very different than Gates' .dll's, not that anyone cares.

I was trying to install Frostwire and VirtualBox: I just gave that one as an example. Now, since you want to go more specific, can you help me fix these two:

_**Frostwire:**_
```
**ibo@ibo-laptop:~/Downloads$ **sudo dpkg -i frostwire-4.21.3.all.deb 
[sudo] password for ibo: 
Selecting previously deselected package frostwire.
(Reading database ... 135233 files and directories currently installed.)
Unpacking frostwire (from frostwire-4.21.3.all.deb) ...
dpkg: dependency problems prevent configuration of frostwire:
 frostwire depends on default-jre-headless; however:
  Package default-jre-headless is not installed.
 frostwire depends on default-jre; however:
  Package default-jre is not installed.
dpkg: error processing frostwire (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Processing triggers for gnome-icon-theme ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_CA.utf8.cache...
Processing triggers for python-support ...
Errors were encountered while processing:
 frostwire
ibo@ibo-laptop:~/Downloads$ 
```[U][B]VirtualBox:
[/B][/U]```
ibo@ibo-laptop:~/Downloads$ sudo dpkg -i virtualbox-4.0_4.0.2-69518~Ubuntu~lucid_i386.deb 
Selecting previously deselected package virtualbox-4.0.
(Reading database ... 135299 files and directories currently installed.)
Unpacking virtualbox-4.0 (from virtualbox-4.0_4.0.2-69518~Ubuntu~lucid_i386.deb) ...
dpkg: dependency problems prevent configuration of virtualbox-4.0:
 virtualbox-4.0 depends on libqt4-opengl (>= 4:4.5.3); however:
  Package libqt4-opengl is not installed.
dpkg: error processing virtualbox-4.0 (--install):
 dependency problems - leaving unconfigured
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for shared-mime-info ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_CA.utf8.cache...
Processing triggers for hicolor-icon-theme ...
Processing triggers for python-support ...
Errors were encountered while processing:
 virtualbox-4.0
ibo@ibo-laptop:~/Downloads$
```
EDIT: I also went a little deeper into the java dependency error. Does the end signify something?
```
ibo@ibo-laptop:~$ sudo apt-get install openjdk-6-jreReading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  openjdk-6-jre: Depends: openjdk-6-jre-headless (>= 6b18-1.8-0ubuntu1) but it is not going to be installed
E: Broken packages
_**ibo@ibo-laptop:~$**_ sudo apt-get install openjdk-6-jre-headless
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  openjdk-6-jre-headless: Depends: tzdata-java but it is not going to be installed
E: Broken packages
_**ibo@ibo-laptop:~$**_ sudo apt-get install tzdata-java
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  tzdata-java: Depends: tzdata (= 2010i-1) but 2010k-0ubuntu0.10.04 is to be installed
E: Broken packages
ibo@ibo-laptop:~$ 
```

---

### Post by oldos2er on 2011-01-28
Which version of Ubuntu are you using?

The problem with dpkg is that it won't install dependencies for you automatically, like other APT front-ends will (e.g. aptitude, apt-get, or Synaptic Package Manager). There are a couple things you could do; if you're running 10.10, install gdebi ```
sudo apt-get install gdebi
``` then right-click on the *.deb, open with gdebi. It will install any needed dependencies. If you're running 10.04 or earlier, gdebi is already installed.

Or install virtualbox (or frostwire) from the repositories ```
sudo apt-get install virtualbox-ose
``` ```
sudo apt-get install frostwire
```

---

### Post by layers on 2011-01-28
> **oldos2er said:**
> Which version of Ubuntu are you using?

The problem with dpkg is that it won't install dependencies for you automatically, like other APT front-ends will (e.g. aptitude, apt-get, or Synaptic Package Manager). There are a couple things you could do; if you're running 10.10, install gdebi ```
sudo apt-get install gdebi
``` then right-click on the *.deb, open with gdebi. It will install any needed dependencies. If you're running 10.04 or earlier, gdebi is already installed.

Or install virtualbox (or frostwire) from the repositories ```
sudo apt-get install virtualbox-ose
``` ```
sudo apt-get install frostwire
```

1. GDebi gives "Error: Cannot install 'default-jre-headless'" for Frostwire and "Error: Cannot install 'libqt4-opengl'" for Virtual box for Status.

2.In terminal, the repo install version for Frostwire cannot find it, and I need VirtualBox CSE.

PS: It's 10.04

---

### Post by James_Lochhead on 2011-01-28
**Installing the two programs:**

You could try to do it the way the above user is showing you, however...

- Virtual Box 4 is not in the (default) repos.
- I can't seem to find Frostwire in there either.

The simplest way to install these two things is to look for a .deb file on their websites, I have checked and they both have one available.

All you have to know is what version of Ubuntu you are using 32 bit (called i386) or 64 bit (called amd64), pick the right one and download it.

Then simply double click the .debi file and install the program. No fiddling around with dpkg, gdebi or the terminal is required. 

**RE: "I don't see how the whole dependency thing being very different than Gates' .dll's"**

That's because it isn't. Much of dependencies are libraries which is what dll's (dynamic linked _libarary_) are.

To be clear though the two concepts aren't exactly the same because dependencies can be used for other things as well such as meta packages (explained previously), themes etc

---

### Post by layers on 2011-01-28
> **James_Lochhead said:**
> **Installing the two programs:**

You could try to do it the way the above user is showing you, however...

- Virtual Box 4 is not in the (default) repos.
- I can't seem to find Frostwire in there either.

The simplest way to install these two things is to look for a .deb file on their websites, I have checked and they both have one available.

All you have to know is what version of Ubuntu you are using 32 bit (called i386) or 64 bit (called amd64), pick the right one and download it.

Then simply double click the .debi file and install the program. No fiddling around with dpkg, gdebi or the terminal is required. 

**RE: "I don't see how the whole dependency thing being very different than Gates' .dll's"**

That's because it isn't. Much of dependencies are libraries which is what dll's (dynamic linked _libarary_) are.

To be clear though the two concepts aren't exactly the same because dependencies can be used for other things as well such as meta packages (explained previously), themes etc
> **layers said:**
> 1. GDebi gives "Error: Cannot install  'default-jre-headless'" for Frostwire and "Error: Cannot install  'libqt4-opengl'" for Virtual box for Status.

2.In terminal, the repo install version for Frostwire cannot find it, and I need VirtualBox CSE.

PS: It's 10.04.

---

### Post by yetiman64 on 2011-01-28
> I've installing "things" recently, but I always get messages of this sort:<<generally speaking>> if a user messes up dependencies by moving outside the official repos (eg. installing packages for firefox 4 with a PPA for example, which by the looks of [[COLOR=Blue]--this thread--[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1675666") may not have even been necessary re your link to the Mozilla site) then they should fix the problem before moving onto installing anything else (like Virtualbox or Frostwire).

Have you purged that PPA yet?

My <<general advice>> is to fix a problem before moving on and creating even more.

---

### Post by layers on 2011-01-28
> **yetiman64 said:**
> <<generally speaking>> if a user messes up dependencies by moving outside the official repos (eg. installing packages for firefox 4 with a PPA for example, which by the looks of [[COLOR=Blue]--this thread--[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1675666") may not have even been necessary re your link to the Mozilla site) then they should fix the problem before moving onto installing anything else (like Virtualbox or Frostwire).

Have you purged that PPA yet?

My <<general advice>> is to fix a problem before moving on and creating even more.

If you count purging not reading the string "firefox" anywhere in Other Software, then yes - I did remove it, and if you recall, that was one of the two reasons "apt-get -f install" worked. And what exactly makes you call that repo a problem? You mean that in osme strange way, the firefox source is causing the dependency error? (I did normally install Matlab, which I understand has a lot to do with java just today)

---

### Post by yetiman64 on 2011-01-28
Firstly I am posting from firefox4 here as a result of your link (initially, and later from the nightly builds site) **without any PPA in use**. The PPA and the Mozilla source are 2 different ways to get the same result (firefox4). You only needed to use one.

If you install a PPA in your system and do an update it **CAN** change the versions of libraries on your system (read "possible dependency hell in the future"). That is why I asked you to post the name of it for checking.

> If you count purging not reading the string "firefox" anywhere in Other Software, then yes - I did remove it, and if you recall, that was one of the two reasons "apt-get -f install" workedRemoving the lines stopped the update manager trying to do the unnecessary installation of firefox4-core from the ppa and the link though it satisfied the alternatives aspect was probably unnecessary now I look back at it. 

Removing the line in Software Sources DOES NOT revert such version changes mentioned above. PPA-PURGE is required for that. Also ppa-purge will need those lines back to remove the changes totally.

Disabling those lines was a temporary measure to stop a conflict while installing build-essential only, hence my later suggestion for you to purge it and use the manual Mozilla source method only. I was hoping purging the ppa would help you reset your install to a "clean"  state re dependencies.

Finally I'm not sure about Frostwire but Java is likely to rely on shared libraries with a web browser as it is used in web browsers.

This has gotten a bit beyond my normal scope, so I'll leave this to others more experienced and with a fuller picture of your situation, hopefully.

Best of luck to you,
yetiman64

---

### Post by layers on 2011-01-28
> **yetiman64 said:**
> Firstly I am posting from firefox4 here as a result of your link (initially, and later from the nightly builds site) **without any PPA in use**. The PPA and the Mozilla source are 2 different ways to get the same result (firefox4). You only needed to use one.

If you install a PPA in your system and do an update it **CAN** change the versions of libraries on your system (read "possible dependency hell in the future"). That is why I asked you to post the name of it for checking.

Removing the lines stopped the update manager trying to do the unnecessary installation of firefox4-core from the ppa and the link though it satisfied the alternatives aspect was probably unnecessary now I look back at it. 

Removing the line in Software Sources DOES NOT revert such version changes mentioned above. PPA-PURGE is required for that. Also ppa-purge will need those lines back to remove the changes totally.

Disabling those lines was a temporary measure to stop a conflict while installing build-essential only, hence my later suggestion for you to purge it and use the manual Mozilla source method only. I was hoping purging the ppa would help you reset your install to a "clean"  state re dependencies.

Finally I'm not sure about Frostwire but Java is likely to rely on shared libraries with a web browser as it is used in web browsers.

This has gotten a bit beyond my normal scope, so I'll leave this to others more experienced and with a fuller picture of your situation, hopefully.

Best of luck to you,
yetiman64
ppa-purge is not found...

---

### Post by yetiman64 on 2011-01-28
> **layers said:**
> ppa-purge is not found...

Reinstall the ppa and then look for ppa-purge again. It is usually supplied as a result of active ppas being installed and in use.

---

### Post by layers on 2011-01-28
> **yetiman64 said:**
> Reinstall the ppa and then look for ppa-purge again. It is usually supplied as a result of active ppas being installed and in use.
I'm afraid I cannot understand the first 3 words. Can you pretend to be more noobish?

---

### Post by yetiman64 on 2011-01-29
> **layers said:**
> I'm afraid I cannot understand the first 3 words.

You installed the ppa once before, you will need to repeat that again if you have removed it from Software Sources.

> **layers said:**
>  Can you pretend to be more noobish?

Sorry, but no. 

I understand that some of what I'm trying to say is going over your head. This is why I said in post #10,
> This has gotten a bit beyond my normal scope, so I'll leave this to  others more experienced and with a fuller picture of your situation,  hopefully.I only posted here as you had split your situation over 2 threads and ultimately this may impact adversely on you getting the help you need in the current situation.

I will admit openly my style of posting can be a bit involved/longwinded and my apologies if it has caused you any added confusion.

I will withdraw/unsubscribe from both threads now. I hope someone can explain more effectively to you about the use of PPAs and how they can alter and impact your system with regard to dependencies.

Best of luck and goodbye,
yetiman64

---

### Post by layers on 2011-01-29
> **yetiman64 said:**
> You installed the ppa once before, you will need to repeat that again if you have removed it from Software Sources.



Sorry, but no. 

I understand that some of what I'm trying to say is going over your head. This is why I said in post #10,
I only posted here as you had split your situation over 2 threads and ultimately this may impact adversely on you getting the help you need in the current situation.

I will admit openly my style of posting can be a bit involved/longwinded and my apologies if it has caused you any added confusion.

I will withdraw/unsubscribe from both threads now. I hope someone can explain more effectively to you about the use of PPAs and how they can alter and impact your system with regard to dependencies.

Best of luck and goodbye,
yetiman64

Dude, I was only referring to last sentence.For all other posts, your explanations were very helpful and idiot-proof(that's where I come in). You helped me a lot. Thanks!

---

### Post by layers on 2011-01-30
Well, I am still not sure what exactly was causing the problem for sure, but running a full update fixed the dependency errors. I am once again able to install any deb package I want! : )

---

