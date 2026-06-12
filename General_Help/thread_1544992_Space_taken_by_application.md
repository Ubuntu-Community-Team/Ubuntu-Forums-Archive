---
title: "Space taken by application"
date: 2010-08-03
forum: General Help
---

### Post by satish_j on 2010-08-03
Is there any way to find out the space consumed by a particular application??
AFAIK,applications installation are distributed across various directories in Linux(man pages,executable files,etc..)and the very close i can get is to run 'whereis' command which gives me all the paths where the application's files are stored.
Do i have to manually go to each and every such paths and check their sizes??

---

### Post by dino99 on 2010-08-03
an app = core files + a bunch of dependencies : object programming which means lot of shared files

---

### Post by dv3500ea on 2010-08-03
In Synaptic (System -> Administration -> Synaptic Package Manager), you can view the installed size of a package (although this doesn't take into account the installed size of all its dependencies).

---

### Post by satish_j on 2010-08-04
> **dv3500ea said:**
> In Synaptic (System -> Administration -> Synaptic Package Manager), you can view the installed size of a package (although this doesn't take into account the installed size of all its dependencies).

This seems very helpful..:p
will definitely try it later today..from the screenshot,i see an tab 'Installed files' which may show the size of the installed files..

---

### Post by satish_j on 2010-08-06
:(:(
No,synaptic was not of much use.For Gimp,it showed me the size of somewhere around 10MB,which obviously is not the complete package size..
Don't anyone think the usefulness of this feature and that it should be considered for development??Iam really disappointed that such a basic feature is not already considered in Linux distros..

---

### Post by soldier1st on 2010-08-06
when you install an application it will list how much space it needs as well as any dependancies, if you go to your username's folder and enable hidden files you will see the programs folder and locate that and right click on it and click properties and it will list how much space it will take or go to applications/accessories and click on disk usage analyzer and go from there.

---

### Post by satish_j on 2010-08-06
> **soldier1st said:**
> when you install an application it will list how much space it needs as well as any dependancies, if you go to your username's folder and enable hidden files you will see the programs folder and locate that and right click on it and click properties and it will list how much space it will take or go to applications/accessories and click on disk usage analyzer and go from there.

Iam quite sure nobody remembers(or make a note of)the size of a package(and its dependencies)displayed at the time of installation..There should be some mechanism to get the package size anytime...:mad:
Now,Iam curious to know whether the idea is being already suggested in Brainstorm Ubuntu??

---

### Post by PeEllAvaj on 2010-08-06
It seems like the problem is how you define the size.

For example, what is the size of firefox?  If you already have gnome and a bunch of the pacakges installed, it really is only a couple megabytes.  If you don't have them installed, then firefox is going to end up taking a few hundred megabytes to install on your system.

Because lots of packages are shared as dependencies for multiple programs, how would you like to define size?

---

### Post by satish_j on 2010-08-06
> **PeEllAvaj said:**
> It seems like the problem is how you define the size.

For example, what is the size of firefox?  If you already have gnome and a bunch of the pacakges installed, it really is only a couple megabytes.  If you don't have them installed, then firefox is going to end up taking a few hundred megabytes to install on your system.

Because lots of packages are shared as dependencies for multiple programs, how would you like to define size?

That was really an informative reply..
I completely agree with you that package installation in Linux share common dependencies..
So,i suppose there is no other way to check the package size..

---

### Post by satish_j on 2010-08-06
Nevermind...I found an workaround for same..
If i remove any package using 'sudo apt-get remove package',it tells me 'xxxMB size will be freed'..
So,that way,i can get an idea of the size consumed by the package..
what say..:):)

---

