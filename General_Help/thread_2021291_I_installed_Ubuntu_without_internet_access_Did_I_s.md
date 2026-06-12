---
title: "I installed Ubuntu without internet access? Did I set myself up for problems?"
date: 2012-07-09
forum: General Help
---

### Post by fapestar on 2012-07-09
I'm just starting to learn how to use Ubuntu, and linux really.

When unbuntu 12.04 first installs to my hdd it recommends you be on the internet, but I  couldn't get my netgear WNA3100 to work properly (I figured it out buy browsing these forums after the install)

But after the installation, I did some software update after moving and hardwired connecting my computer to the internet, but I still can't get  one single program to install from the terminal.

I can only get them to install from the software manager thing.

I even follow the instructions listed in the install folders exactly.

I make myself a super user and what not, I always get an error,

I can make directories and everything but I don't know. Should I reinstall ubuntu, while on the internet.

Becasue when I installed programs when I was running the live version it  worked fine. When I was on live version, I was on my laptop wifi card was automatically detected. 

Do I have an outdated kernel or something? Because I couldn't not install dswipper or wine from terminal at all. I got as far as making a directory and when I tried to use the "make uninstall" and "make install" I get a stop operation error.

---

### Post by arubislander on 2012-07-09
Welcome to the forums.

It is perfectly OK to install Ubuntu while disconnected from the internet. It is only recommended that you are connected so that you can download and apply the available updates during installation. If you are not connected then the updates can be applied after installation when you do achieve an internet connection. So the difficulties you are experiencing have nothing to do with having installed while not connected to the 'net.

What is happening in your situation is that you are using two ways of installing software: from source and from the repositories. The Software Manager downloads the software from the Ubuntu repositories. The equivalent way to do that from the command line is ```
$ sudo apt-get install [package-name]
``` where [package-name] is the name of the package you want to install, say you wanted to install wine it would be ```
$ sudo apt-get install wine
```

You have probably downloaded the source code of the software you want to install and are following the instructions on the website or in the readme. This is fine if that is what you want to do, but is it what you want to do? If so, maybe start a new thread asking the specific question and also pasting the specific error(s) you are getting.

---

### Post by fapestar on 2012-07-09
> **arubislander said:**
> Welcome to the forums.

It is perfectly OK to install Ubuntu while disconnected from the internet. It is only recommended that you are connected so that you can download and apply the available updates during installation. If you are not connected then the updates can be applied after installation when you do achieve an internet connection. So the difficulties you are experiencing have nothing to do with having installed while not connected to the 'net.

What is happening in your situation is that you are using two ways of installing software: from source and from the repositories. The Software Manager downloads the software from the Ubuntu repositories. The equivalent way to do that from the command line is ```
$ sudo apt-get install [package-name]
``` where [package-name] is the name of the package you want to install, say you wanted to install wine it would be ```
$ sudo apt-get install wine
```You have probably downloaded the source code of the software you want to install and are following the instructions on the website or in the readme. This is fine if that is what you want to do, but is it what you want to do? If so, maybe start a new thread asking the specific question and also pasting the specific error(s) you are getting.

ohh okay. yea, I think that is my problem. Because the installation directions for the apps I got said to untar by tar zvfw (or something like that) the name of the file and then go into the directory created and run make uninstall, then make, and then make install...and I got an error for each command. 

Usually, with the live version I'd just type apt-get. I think I know what's going on now. I still kind of don't understand why my commands didn't work. I even watch youtube videos and tried to follow. 

BTW, what is the proper way of installing those updates. I went to the top right hand corner and clicked on software updates, is that the right place?

---

### Post by MG&amp;TL on 2012-07-09
> **fapestar said:**
> ohh okay. yea, I think that is my problem. Because the installation directions for the apps I got said to untar by tar zvfw (or something like that) the name of the file and then go into the directory created and run make uninstall, then make, and then make install...and I got an error for each command. 

Usually, with the live version I'd just type apt-get. I think I know what's going on now. I still kind of don't understand why my commands didn't work. I even watch youtube videos and tried to follow. 

BTW, what is the proper way of installing those updates. I went to the top right hand corner and clicked on software updates, is that the right place?

You don't usually have to use anything except apt-get (or the software centre!) unless you really need to (obscure program, you want cutting-edge stuff). 'tar xvf', 'make' and 'make install' are all commands to build from source.

That is absolutely the right place, or you can click on 'update manager' in the dash, which brings up an identical dialog.

---

### Post by Cheesehead on 2012-07-09
> **fapestar said:**
> and I got an error for each command.

To get you useful help, we need to know the exact error message.
What are you trying to install?

> **fapestar said:**
> Usually, with the live version I'd just type apt-get.

You can use apt-get offline, too. Synaptic has offline package management, including download scripts. Or apt-get's --simulate flag will tell you exactly which dependencies you need to download. Or the apt-zip package.

> **fapestar said:**
> What is the proper way of installing those updates. I went to the top right hand corner and clicked on software updates, is that the right place? For offline updates? I generally wouldn't bother unless there is a specific fix you seek. If you really want to, the apt-zip package is a great way to automate the process.

---

### Post by mastablasta on 2012-07-09
you need to install tools for to use "make"  and "install" commands. that is to compile the source code by yourself. this is usually not necessaary. 
read here what you need to compile packages from source and also how to do it: [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)
 
also make sure commands are types correctly as per instructions.
 
sometimes dependencies need to be satisfied first (as they don't come with the programme source code but from the repositories).
 
anyway you can mark the text in terminal copy it (righ click on it and select copy) and then paste it here (use the # icon to get the code tags so the formating is easier to read)so we can see the errors you get and can advise further.

---

