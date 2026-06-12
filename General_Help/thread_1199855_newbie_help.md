---
title: "newbie help"
date: 2009-06-29
forum: General Help
---

### Post by *Gilly* on 2009-06-29
linux ubutu is totally new to me and i feel a bit lost
im an experienced windows user 

anyway ive downloaded a file avant window navigater 
how do i install it 
and downloaded files in general??

---

### Post by Idefix82 on 2009-06-29
Hello and welcome! Don't worry about everything being new, you will learn quickly.

The way to install most software in Ubuntu is through the so-called Synaptic Package Manager. You will find it under System->Administration. It's a big database of software that was approved by Canonical (the company behind Ubuntu) and that will install without you having to do anything. Just look for the software that you need, click the square next to it and click on "Install". Then click "Apply" on the top bar. It will automatically install all auxiliary packages that it needs as well.

Before you start looking for software, click on the "Reload" button on the top. Then just search for AWN.

There are other ways of installing software, particularly if it's not in the official repositories (the software database) but they take a bit of learning.

Edit: Here is a nice tutorial about installing software: [http://www.psychocats.net/ubuntu/installingsoftware]("http://www.psychocats.net/ubuntu/installingsoftware")

---

### Post by mcduck on 2009-06-29
Like Idefix82 said, in Linux we don't usually download software from random web pages and install manually, instead we use package management tools that handles downloading, installing, updating and uninstalling programs automatically.

You'll definitely want to read this: [Installing software in Ubuntu]("http://www.psychocats.net/ubuntu/installingsoftware")

---

### Post by *Gilly* on 2009-06-29
i feel the same as when i first tried windows 95 omg  ..just for now could you tell me how to get a dock on my desktop and possibly something similar to windows sidebar  thanks

---

### Post by mcduck on 2009-06-29
> ***Gilly* said:**
> i feel the same as when i first tried windows 95 omg  ..just for now could you tell me how to get a dock on my desktop and possibly something similar to windows sidebar  thanks

You have many options for both purposes, but Avant Window Navigator is probably the most popular dock. And for desktop widgets and such you should start with Screenlets.

Both are available in Ubuntu's repositories

---

### Post by decoherence on 2009-06-29
> ***Gilly* said:**
> i feel the same as when i first tried windows 95 omg  ..just for now could you tell me how to get a dock on my desktop and possibly something similar to windows sidebar  thanks

Follow the menus...

Applications > Add/Remove...

In the window that comes up, make sure the "Show:" drop down menu at the top is set to "All available applications" then type "Avant" in the search bar. Click the check-box and click apply. This will get AWN installed for you.

To make it start when you log in, go to

System > Preferences > Startup Applications

In that window, click the Add button. In the window that comes up, the only thing that matters is that you put "awn" as the command. For name and description, just put in sensible values (name: Avant Window Navigator, description: a dock, or whatever you like) click the Add button in that window, make sure there is a check-mark beside Avant Window Navigator (or whatever you named it) and the next time you log in, it should pop up!

As for a Windows sidebar.... I'm not sure what that is. A Vista thing? Maybe try Gdesklets? (also available in the Add/Remove... tool)

---

### Post by chaosdesigner on 2009-06-29
About the dock:

I have found that the 'cairo-dock' is a very good and nice looking programm that is also fairly easy to install.

You could just go to the Synaptic Package Manager and look for the 2 packages that are needed (cairo-dock and cairo-dock-plug-ins) but as you will see in alot of tutorials sometimes its easier to just use the Terminal. So you should probably try to get used to it.

This is how you install the cairo-dock with the Terminal.

First start the Terminal: Accessories -> Terminal

Then you just need to type in:

```
sudo apt-get install cairo-dock cairo-dock-plug-ins 
```

As for Shell commands you should always try to understand them before you just enter them, so thsi right here is a very simple one. You will see the 'sudo' a lot, this just means that you will run this operation as 'root' or admin. This will also ask you for your password. After that the 'apt-get' is the programm that downloads the Packages as already said in this Thread. Instead of 'apt-get' you could also put 'aptitude', which is simply just a different programm. Im guessing you can think what the 'Install' is suppose to mean. If you would for example want to delete packages you could just put 'remove' instead of 'install'. After the action you just need to put the packages, in this case 'cairo-dock' and 'cairo-dock-plug-ins'.

To start the dock after the installation you would just need to put 'cairo-dock' in the Terminal and it would start. Or instead you could just go to Applications -> System Tools -> Cairo Dock. 

If you want this dock to start everytime you boot your pc, you would just have to right click on the dock and i think somewhere there it says something like this. If not, this is how you start a Application on every start:

Go to System -> Preferences -> Startup Applications (or Sessions)

There you need to go to 'add', the you just need to type in the name, which Would be Cairo Dock or whatever you want to put there (doesnt matter), and then the Command, here of course 'cairo-dock'. You can then also put a Comment if you like to. Then save that and your dock should appear everytime you start :). (Of course you can do this with every other application as well).


If you have any questions just post them, there are enough people here that youd love to help you :).

---

### Post by *Gilly* on 2009-06-29
> **mcduck said:**
> You have many options for both purposes, but Avant Window Navigator is probably the most popular dock. And for desktop widgets and such you should start with Screenlets.

Both are available in Ubuntu's repositories

is this located in the synaptic package manager? and if so where ?  i havent got a clue what repositories means

---

### Post by mcduck on 2009-06-29
> ***Gilly* said:**
> is this located in the synaptic package manager? and if so where ?  i havent got a clue what repositories means

You should find bot in Synaptic Package Manager, and in the Add/Remove.. -tool found in the Appplications-menu. Which ever tool you use, use the search box to find the package you want..

Or just click the link and you should be prompted to install the programs:

[apt://avant-window-navigator]("apt://avant-window-navigator")
[apt://screenlets]("apt://screenlets")

(repositories are internet servers used to provide software packages for Ubuntu's package management)

---

### Post by *Gilly* on 2009-06-29
> ***Gilly* said:**
> is this located in the synaptic package manager? and if so where ?  i havent got a clue what repositories means

sorry didnt refresh page  To *decoherence*  i followed ure instructions fully   but theres no matches       .........edit.... okay i closed it then reopened it and now its working after downloading updates

---

### Post by Greyfox_75 on 2009-06-29
Repositories is where your package manager gets its software.  Ubuntu has a few different repositories.  

Main is "supported" software that the Ubuntu team tests and tries to fix if there are any problems with compatibility with other Ubuntu packages.

Multiverse is packages that are not licensed very well to go with Ubuntu.  So things like proprietary gfx drivers come out of here because they are closed source.

Universe is packages that may be licensed open source but the Ubuntu team does not officially support these.  If you have any problems with a program from the Universe repo you would have to either look for support from whoever creates the program of check here to see if anyone else is having your problem.

All together these repositories contain tens of thousands of packages for you to install and enjoy.  It can be very hard getting used to this coming from Windows where you have to scour the Internet for what your looking for.  In Ubuntu its just open your package manager and click install.

This repository system of doing things makes your life easier in many ways.  When you update your system you get updates for all of your software too.  In Windows you would have to go to each individual site and redownload each program that you have to get updates for everything.  Also it can help with security.  Each package is signed so that you can be certain that the package is from the Ubuntu server and hasn't been tampered with.  No more worrying about downloading programs from shady web sites.

Welcome to Ubuntu. Enjoy!

---

### Post by mcduck on 2009-06-29
> ***Gilly* said:**
> sorry didnt refresh page  To *decoherence*  i followed ure instructions fully   but theres no matches

In that case you'll have to enable Universe repository first (it contains  software that isn't directly maintained by Ubuntu developers).

Go to System/Administration/Software Sources, and on the Ubuntu Software-tab make sure both "Community-maintained Open Source software (universe)" is enabled.

After that you will definitely be able to find both AWN and Screenlets with any package management tool in Ubuntu.

---

### Post by *Gilly* on 2009-06-29
> **chaosdesigner said:**
> About the dock:

I have found that the 'cairo-dock' is a very good and nice looking programm that is also fairly easy to install.

You could just go to the Synaptic Package Manager and look for the 2 packages that are needed (cairo-dock and cairo-dock-plug-ins) but as you will see in alot of tutorials sometimes its easier to just use the Terminal. So you should probably try to get used to it.

This is how you install the cairo-dock with the Terminal.

First start the Terminal: Accessories -> Terminal

Then you just need to type in:

```
sudo apt-get install cairo-dock cairo-dock-plug-ins 
```As for Shell commands you should always try to understand them before you just enter them, so thsi right here is a very simple one. You will see the 'sudo' a lot, this just means that you will run this operation as 'root' or admin. This will also ask you for your password. After that the 'apt-get' is the programm that downloads the Packages as already said in this Thread. Instead of 'apt-get' you could also put 'aptitude', which is simply just a different programm. Im guessing you can think what the 'Install' is suppose to mean. If you would for example want to delete packages you could just put 'remove' instead of 'install'. After the action you just need to put the packages, in this case 'cairo-dock' and 'cairo-dock-plug-ins'.

To start the dock after the installation you would just need to put 'cairo-dock' in the Terminal and it would start. Or instead you could just go to Applications -> System Tools -> Cairo Dock. 

If you want this dock to start everytime you boot your pc, you would just have to right click on the dock and i think somewhere there it says something like this. If not, this is how you start a Application on every start:

Go to System -> Preferences -> Startup Applications (or Sessions)

There you need to go to 'add', the you just need to type in the name, which Would be Cairo Dock or whatever you want to put there (doesnt matter), and then the Command, here of course 'cairo-dock'. You can then also put a Comment if you like to. Then save that and your dock should appear everytime you start :). (Of course you can do this with every other application as well).


If you have any questions just post them, there are enough people here that youd love to help you :).

done that but getting this message 

-laptop:~$ sudo apt-get install cairo-dock cairo-dock-plug-ins
Reading package lists... Done
Building dependency tree       
Reading state information... Done
cairo-dock is already the newest version.
cairo-dock set to manually installed.
E: Couldn't find package cairo-dock-plug-ins
-laptop:~$ 


any idea whats wrong??

---

### Post by Tyke91 on 2009-06-29
you don't have all the ubuntu repositories enabled.

scroll up :)


Basically - apt is a program that accesses software from huge online repositories. Canonical (the company behind ubuntu) maintains some of these repositories. Apt will search for the correct package, find its dependencies and install software all without the user having to browse to any website. There are 2 main GUI frontends to apt, the Add/Remove application and Synaptic (a more powerful version). 

AWN is in the universe repository, so you will have to enable that repository in the "Administration>Sofware Sources" menu. It's pretty easy to use, just make sure that every repository has a check mark next to it, and that the CD repository is turned off.


then you can use Add/Remove or Synaptic, or Type apt-get into a terminal.

---

### Post by *Gilly* on 2009-06-29
> **Tyke91 said:**
> you don't have all the ubuntu repositories enabled.

scroll up :)


Basically - apt is a program that accesses software from huge online repositories. Canonical (the company behind ubuntu) maintains some of these repositories. Apt will search for the correct package, find its dependencies and install software all without the user having to browse to any website. There are 2 main GUI frontends to apt, the Add/Remove application and Synaptic (a more powerful version). 

AWN is in the universe repository, so you will have to enable that repository in the "Administration>Sofware Sources" menu. It's pretty easy to use, just make sure that every repository has a check mark next to it, and that the CD repository is turned off.


then you can use Add/Remove or Synaptic, or Type apt-get into a terminal.
it was already in my accessories getting it from synatic thing but only just spotted it thanks for the help 

ive got a few more questions what would be better suited in this thread rather than creating new threads constantly too ask new questions 

so ill fire some of and im sure you linux veterens can tell me easily 


1, when booting up how to just make you type just the password rather than user name then the password

2, how to get the laptops webcam working (Dell Inspiron 1545)

more linux nOOb questions to come no doubt;);):lolflag:

---

### Post by *Gilly* on 2009-06-29
> ***Gilly* said:**
> it was already in my accessories getting it from synatic thing but only just spotted it thanks for the help 

ive got a few more questions what would be better suited in this thread rather than creating new threads constantly too ask new questions 

so ill fire some of and im sure you linux veterens can tell me easily 


1, when booting up how to just make you type just the password rather than user name then the password

2, how to get the laptops webcam working (Dell Inspiron 1545)

more linux nOOb questions to come no doubt;);):lolflag:
bump bump

---

