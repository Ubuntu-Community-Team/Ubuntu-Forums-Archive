---
title: "Unable to perform a complete update, two packages not updated"
date: 2011-12-07
forum: General Help
---

### Post by veroslav on 2011-12-07
Hi,

I am running Ubuntu 11.10, 64-bit, and since a few days back, I am experiencing the following problem when performing an update from within the Update Manager:

All of the packages suggested for update are updated with the exception of these two:

**language-pack-gnome-sv** and **language-pack-sv**

I am using English as the main language but use Swedish for the currency and time formatting. I've attached a screenshot of the update manager after a successfull update, but where I can't select the two packages above for update.

Nothing happens when I try to select them with the mouse. I also tried running

**sudo apt-get update** and **sudo apt-get upgrade** from the terminal; **sudo apt-get upgrade** gives the following output:

```
user@user-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  language-pack-gnome-sv language-pack-sv
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
user@user-desktop:~$ 
```Could somebody help me update these two packages? Also, my father is running Xubuntu 11.10 and he is experiencing exactly the same issue on the fresh install.

Thank you in advance.

Kind Regards,
Veroslav

---

### Post by westie457 on 2011-12-07
Hi what happens if you try   sudo apt-get install <package name>

---

### Post by snowpine on 2011-12-07
Check the boxes in Update Manager and click Install Updates.

---

### Post by veroslav on 2011-12-07
Hi,

thank you for your reply. I get the following:
```

user@user-desktop:~$ sudo apt-get install language-pack-gnome-sv
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 language-pack-gnome-sv : Depends: language-pack-gnome-sv-base (>= 1:11.10+20111025) but 1:11.10+20111006 is to be installed
                          Depends: language-pack-sv-base (>= 1:11.10+20111025) but 1:11.10+20111006 is to be installed
E: Unable to correct problems, you have held broken packages.
user@user-desktop:~$ 
```and

```
user@user-desktop:~$ sudo apt-get install language-pack-sv
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 language-pack-sv : Depends: language-pack-sv-base (>= 1:11.10+20111025) but 1:11.10+20111006 is to be installed
E: Unable to correct problems, you have held broken packages.
user@user-desktop:~$ 
```I haven't messed with these packages at all, so I don't really understand why the packages are broken.

Regards,
Veroslav

---

### Post by veroslav on 2011-12-07
HI [snowpine]("http://ubuntuforums.org/member.php?u=479885"),

unfortunately, that is the problem, it wont let me! Nothing happens when I do that :(

---

### Post by Cibban on 2011-12-14
Using aptitude instead of apt-get/synaptic solved this exact issue for me in Ubuntu lucid after removing the "sv" packages that wouldn't update.

$ sudo aptitude
Ctrl+T -> Resolver
Apply solution
Ctrl+T Install/remove packages

This article was a great help: [http://pthree.org/2007/08/12/aptitude-vs-apt-get/](http://pthree.org/2007/08/12/aptitude-vs-apt-get/)

I will never use anything but aptitude again.

//Cibban

---

