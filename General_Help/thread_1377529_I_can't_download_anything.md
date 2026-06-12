---
title: "I can't download anything"
date: 2010-01-10
forum: General Help
---

### Post by arcticmunkii on 2010-01-10
I'm trying to download skype at [www.skype.com/downloads](www.skype.com/downloads) for ubuntu 32-bit and then when it gets to the part where I choose to install package this error comes up 'Error: Dependency is not satisfiable: libqt4-dbus (>= 4.4.3)' please help me -_-   also when I try and download this other program this error message Error: Dependency is not satisfiable: libc-ares2 appears in the package installer

---

### Post by steveneddy on 2010-01-10
You did download the software.

Did you mean that you are having trouble installing?

How are you trying to install?

Is this a .deb file you are trying to install or a .tar.gz ?

libqt4-dbus is a piece of software that Skype "depends" on to run properly, which is why they call it a "dependency".

First make sure that the version you are trying to install is meant for your version of Ubuntu. ( I assume you are using Ubuntu )

Open Synaptic and do a search for libqt4-dbus and if it not installed, install it.

Then try installing Skype.

Post back here with results.

Also - I think skype is in the repos:

```
sudo apt-get install skype
```

---

### Post by arcticmunkii on 2010-01-10
I'm sorry but every time it says something like 'Error: Dependency is not satisfiable: libgnutls13 (>= 2.0.4-0)' I download it and when I download it the install asks for something else, why is ubuntu so complicated you should just be able to download and install something like windows or do you have to spend 24 hours for each program you download???

---

### Post by steveneddy on 2010-01-10
> **arcticmunkii said:**
> I'm sorry but every time it says something like 'Error: Dependency is not satisfiable: libgnutls13 (>= 2.0.4-0)' I download it and when I download it the install asks for something else, why is ubuntu so complicated you should just be able to download and install something like windows or do you have to spend 24 hours for each program you download???

Did you open a terminal and try installing like this:

```
sudo apt-get install skype
```

and the last post here I gave you instructions - did you follow the instructions for the other dependency? If it works for one it will work for the other. 

If software depends on other software and it's not there, you must install the dependency software.

Look, open a terminal and install via the command line method. It's easier.

Ubuntu is not complicated, it is different. Your first post should have asked for advice on installing Skype. lol 

When we say "Skype is in the repos", that means that there is software you are looking for in a repository of safe, approved software that will run on your version of Ubuntu very well.

**Open up Synaptic and look for Skype. Check it there and install it.** This will be the easiest way for you right now.

Look at the links in my sig and start learning a little about the new OS you decided to start using.

You still haven't told us what version of Ubuntu you are using.

Here's a link from my sig that may help you if you read it:

[http://ubuntuguide.org/wiki/Ubuntu:Intrepid#Ubuntu_Package_Installation_and_Updates](http://ubuntuguide.org/wiki/Ubuntu:Intrepid#Ubuntu_Package_Installation_and_Updates)

---

### Post by arcticmunkii on 2010-01-10
Ok thank you ill have a look, and by the way how do I find out what version I have?

---

### Post by arcticmunkii on 2010-01-10
sudo apt-get install skype doesent work so how do I get skype?

---

### Post by steveneddy on 2010-01-10
> **arcticmunkii said:**
> sudo apt-get install skype doesent work so how do I get skype?

OK - <snip>

OK - open 

System --> Administration --> Software Sources

type your password when prompted

See attached pic - check off all of the boxes for main, universe, multiverse and restricted. This will install additional repos from Ubuntu that you will need in the future, so we may as well get it out of the way.

Then in terminal

```
sudo apt-get update
```

then 

```
sudo apt-get upgrade
```

then

```
sudo apt-get install skype
```

Now, that should install Skype according to this:

[http://ubuntuguide.org/wiki/Ubuntu:Intrepid#Skype](http://ubuntuguide.org/wiki/Ubuntu:Intrepid#Skype)

which is from a link in my sig (see why you need to read these?)

More explaination here:

[http://ubuntuguide.org/wiki/Ubuntu:Intrepid#Add_Extra_Ubuntu_Repositories](http://ubuntuguide.org/wiki/Ubuntu:Intrepid#Add_Extra_Ubuntu_Repositories)

If you tell what version of Ubuntu you are using I will hook you up with another, but I need to know if you are using 8.04, 8.10, 9.04 or 9.10.

---

### Post by steveneddy on 2010-01-10
> **arcticmunkii said:**
> Ok thank you ill have a look, and by the way how do I find out what version I have?

System --> About Ubuntu

---

### Post by lotharmat on 2010-01-10
> **steveneddy said:**
> System --> About Ubuntu

or

```
uname -a
```

---

### Post by steveneddy on 2010-01-10
> **lotharmat said:**
> or

```
uname -a
```

```
uname -a
``` 

only gives info about the kernel.

to check the Ubuntu version in terminal it's

```
lsb_release -a
```

---

### Post by lotharmat on 2010-01-10
My bad!

(adds that command to the ever growing list of useful ones!)

---

### Post by arcticmunkii on 2010-01-10
Thank you guys, I've just downloaded something called kismet but I can't find it anywhere any tips?

---

### Post by steveneddy on 2010-01-10
> **arcticmunkii said:**
> Thank you guys, I've just downloaded something called kismet but I can't find it anywhere any tips?

Did you get skype working?

**[SIZE="3"]How did you install kismet?[/SIZE]**

Did you try

```
sudo apt-get install kismet
```

cuz it's in the repos.

To answer your question, where did you tell the browser to put downloaded files?

Another question: Do you have the definition of **download** and **install** confused?

Downloading means receiving data from the internet or another external source to your PC.

Installing means actually installing the software on the machine so that the installed software operates.

This goes back to the name of your thread and your first question.

If you installed it, it's probably in Applications --> Internet

You really need to dig and poke around on your new desktop for a little while so you can figure this stuff out, like where stuff should be after installation.

---

### Post by steveneddy on 2010-01-10
Try this guide:

[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

---

### Post by arcticmunkii on 2010-01-10
Ok yes I downloaded it and installed off of terminal 'sudo apt-get install kismet' I didnt get an option to choose where it went and no it's not in aplications>internet -_-

---

### Post by steveneddy on 2010-01-10
> **arcticmunkii said:**
> Ok yes I downloaded it and installed off of terminal 'sudo apt-get install kismet' I didnt get an option to choose where it went and no it's not in aplications>internet -_-

Open a terminal and type in

```
kismet
```

or if permissions are needed try

```
sudo kismet
```

from this google search:

[http://www.google.com/search?hl=en&source=hp&q=ubuntu+launch+kismet&aq=f&oq=&aqi=](http://www.google.com/search?hl=en&source=hp&q=ubuntu+launch+kismet&aq=f&oq=&aqi=)

Google is your friend.

---

