---
title: "Help with commands?"
date: 2011-05-04
forum: General Help
---

### Post by mattintc10 on 2011-05-04
i am on this this thread for my network device. I am unsure how to enter some of the commands such as how to get it to go to the file name and what not. Any help would be much appreciated

This is the thread and the 3rd one down is what im following and confused with 

[http://forum1.netgear.com/showthread.php?t=35739](http://forum1.netgear.com/showthread.php?t=35739)

---

### Post by seawolf167 on 2011-05-04
I would start reading the commands [here]("http://linuxcommand.org/index.php") to familiarise yourself with the basic commands before you get started like cd, ls, cat, etc.

change directory
```
cd
```

list contents
```
ls
```

---

### Post by mattintc10 on 2011-05-04
> **seawolf167 said:**
> I would start reading the commands [here]("http://linuxcommand.org/index.php") to familiarise yourself with the basic commands before you get started like cd, ls, cat, etc.

change directory
```
cd
```list contents
```
ls
```

You guys are always so great with help and what not you have no idea how much i appreciate it.

---

### Post by Dr. Nick on 2011-05-04
Have you downloaded the drivers they linked yet? Ndiswrapper basically uses windows drivers in linux, so make sure its installed from apt-get. I will post my changes in bold.

```
a) sudo ndiswrapper -i /home/percy/downloads/netgear/mrv8335.inf

**installs the .inf file from where you saved it, if you dont want to type the path this way then you can CD into the directory from the terminal and just use "sudo ndiswrapper -i mrv8335.inf"**

b) sudo ndiswrapper -l [which produced this line on screen: 'mrv8335 : driver installed | device (11AB:1FAA) present']

**checks to make sure card was detected**

c) sudo ndiswrapper -m

d) sudo gedit /etc/modules [where I added 'ndiswrapper' as the last line to the file and saved it.]
**loads ndiswrapper at boot so card works when computer boots**
```

If all else fails I believe ndis-gtk will work and let you do it all in a gui, but what fun is that.

---

### Post by mattintc10 on 2011-05-04
> **Dr. Nick said:**
> Have you downloaded the drivers they linked yet? Ndiswrapper basically uses windows drivers in linux, so make sure its installed from apt-get. I will post my changes in bold.

```
a) sudo ndiswrapper -i /home/percy/downloads/netgear/mrv8335.inf

**installs the .inf file from where you saved it, if you dont want to type the path this way then you can CD into the directory from the terminal and just use "sudo ndiswrapper -i mrv8335.inf"**

b) sudo ndiswrapper -l [which produced this line on screen: 'mrv8335 : driver installed | device (11AB:1FAA) present']

**checks to make sure card was detected**

c) sudo ndiswrapper -m

d) sudo gedit /etc/modules [where I added 'ndiswrapper' as the last line to the file and saved it.]
**loads ndiswrapper at boot so card works when computer boots**
```If all else fails I believe ndis-gtk will work and let you do it all in a gui, but what fun is that.

Im so confused im in xubuntu 11.04 in its terminal and trying to do everything possible and its in a folder named " matthew " in another folder " MRV " with the four files they said to download.

---

### Post by seawolf167 on 2011-05-04
It the folder hierarchy is:

```
/home
           MRV
                      matthew
```

then when you open a terminal (it'll start at /home), use the following commands to navigate to the "matthew" folder

```
cd MRV
cd matthew
```You can put the cd command as one entry, but I figured this way would be easiest to understand

---

### Post by Dr. Nick on 2011-05-04
If you are really struggling to find the directory the inf file is in for the first command type this in the terminal

**locate mrv8335.inf**

That should give you the full path, locate command is case sensitive so be aware of that.

---

### Post by mattintc10 on 2011-05-04
> **seawolf167 said:**
> It the folder hierarchy is:

```
/home
           MRV
                      matthew
```then when you open a terminal (it'll start at /home), use the following commands to navigate to the "matthew" folder

```
cd MRV
cd matthew
```You can put the cd command as one entry, but I figured this way would be easiest to understand

Thanks man! So i just have to figure out how to navigate from matthew to MRV then to the file name?

---

### Post by mattintc10 on 2011-05-04
> **Dr. Nick said:**
> If you are really struggling to find the directory the inf file is in for the first command type this in the terminal

**locate mrv8335.inf**

That should give you the full path, locate command is case sensitive so be aware of that.

It wont find it it just goes to another line and waits for another command.

---

### Post by seawolf167 on 2011-05-04
> **mattintc10 said:**
> Thanks man! So i just have to figure out how to navigate from matthew to MRV then to the file name?

I think the easiest way to do this for you (without using the *locate* command posted above) would be to find the file via nautilus (i.e. the GUI file browser), then look at the address in the location bar, then simply use *cd* commands to navigate to that location

Once there, you can list the contents with the *ls* command

---

### Post by seawolf167 on 2011-05-04
> **mattintc10 said:**
> It wont find it it just goes to another line and waits for another command.

This means that there is no file with the *exact* name. You can use wildcards if you aren't exactly sure. You can also use the -i switch so case-sensitivity isn't an issue

```
locate -i some*
```would find everything starting with any case-sensitivy of ***some*** with *any* characters after it

---

### Post by mattintc10 on 2011-05-04
> **seawolf167 said:**
> This means that there is no file with the *exact* name. You can use wildcards if you aren't exactly sure. You can also use the -i switch so case-sensitivity isn't an issue

```
locate -i some*
```would find everything starting with any case-sensitivy of ***some*** with *any* characters after it

I need to play around with this and see if i can get it to work properly and what not.

---

### Post by Dr. Nick on 2011-05-04
> **seawolf167 said:**
> I think the easiest way to do this for you (without using the *locate* command posted above) would be to find the file via nautilus (i.e. the GUI file browser), then look at the address in the location bar, then simply use *cd* commands to navigate to that location

Once there, you can list the contents with the *ls* command

I am not using xubuntu so I am not sure of the default behavior, but if the address does not show up in the location bar you can use ctrl+l to see it

---

### Post by seawolf167 on 2011-05-04
Easy way to slowly narrow the results down, start with say

```
locate -i mrv*
```

then if it spits out a lot of results, modify like so

```
locate -i mrv8*
```

and so on, and you can keep narrowing it down while still seeing what the computer is able to find and where the files are located

---

### Post by mattintc10 on 2011-05-04
> **seawolf167 said:**
> Easy way to slowly narrow the results down, start with say

```
locate -i mrv*
```then if it spits out a lot of results, modify like so

```
locate -i mrv8*
```and so on, and you can keep narrowing it down while still seeing what the computer is able to find and where the files are located

it came up with some results and then after the locate mrv8 it doesnt find nuttin

EDIT: it wont find jack in my MRV folder ima try to move it and see if that clears anything up.

And it did not clear nothing up....

---

### Post by Dr. Nick on 2011-05-04
I would try to re-download the files then and pay special attention to where they are saving too. Try right clicking on them in the browser and clicking "save target as" or similar so you can choose where to save them

---

### Post by mattintc10 on 2011-05-04
> **Dr. Nick said:**
> I would try to re-download the files then and pay special attention to where they are saving too. Try right clicking on them in the browser and clicking "save target as" or similar so you can choose where to save them


They where saved to a USB stick and then cut and pasted into another folder. thats the only way i can do it.

---

### Post by sisco311 on 2011-05-04
You can simply drag & drop a file (or sirectory) into the terminal window to get its full path.

---

### Post by mattintc10 on 2011-05-04
> **sisco311 said:**
> You can simply drag & drop a file (or sirectory) into the terminal window to get its full path.

you can?! well lets try that!

---

### Post by mattintc10 on 2011-05-04
> **sisco311 said:**
> You can simply drag & drop a file (or sirectory) into the terminal window to get its full path.

Tried that and it says " sudo: ndiswrapper: command not found.

---

### Post by sisco311 on 2011-05-04
> **mattintc10 said:**
> Tried that and it says " sudo: ndiswrapper: command not found.

ndiswrapper is not installed by default, You have to install the ndiswrapper-common package. You can install ti via Ubuntu Software Center, Synaptic or via the terminal:
```
sudo apt-get install ndiswrapper-common
```

---

### Post by mattintc10 on 2011-05-04
> **sisco311 said:**
> ndiswrapper is not installed by default, You have to install the ndiswrapper-common package. You can install ti via Ubuntu Software Center, Synaptic or via the terminal:
```
sudo apt-get install ndiswrapper-common
```

E: Unable to locate package ndiswrapper-common

---

