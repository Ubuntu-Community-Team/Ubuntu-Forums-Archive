---
title: "how to install stuff"
date: 2011-02-07
forum: General Help
---

### Post by ianma on 2011-02-07
Sorry this is so simple even i cant believe I am asking it but here goes.

I have downloaded the linux version of a software called vmware now inside the package I have now found a file called installer.sh if I right click it I get the option to run  or run in terminal. Whatever option I choose once clicked nothing happens, is there something else I am meant to do this is my first time using Linux so please keep answers simple.

Cheers

---

### Post by matt_symes on 2011-02-07
Hi

First make sure the executable bit is set.

Open a terminal and type

```
chmod 755 /path/to/installer.sh
```

or you can do it from the file browser. Right click on installer.sh and select Properies->permissions tab and and 'make executable' (or something like that).

You will also need to run it as root to install it.

Kind regards

---

### Post by ianma on 2011-02-07
> **matt_symes said:**
> Hi

First make sure the executable bit is set.

Open a terminal and type

```
chmod 755 /path/to/installer.sh
```or you can do it from the file browser. Right click on installer.sh and select Properies->permissions tab and and 'make executable' (or something like that).

You will also need to run it as root to install it.

Kind regards

OK tried the thing with the terminal screen after checking the properties, it was in fact already set to executable dont know if it means anything but there is link a tiny padlock icon on the top right of the main icon for the installer.sh file.

Here was the terminal screen thing dont know what this is all about.

```
manleynet@manleynet-desktop:~$ chmod /home/manleynet/Downloads/ect/vmware/installer.sh
chmod: missing operand after `/home/manleynet/Downloads/ect/vmware/installer.sh'
Try `chmod --help' for more information.
manleynet@manleynet-desktop:~$ 

```

Thanks for the help so far and keeping it simple for me.

Cheers

---

### Post by uRock on 2011-02-07
You need to include the number 755 in the command.
```
chmod [COLOR=Red]755[/COLOR] /path/to/installer.sh
```

---

### Post by markthekdeguy on 2011-02-08
./installer.sh

---

### Post by ianma on 2011-02-08
Linux is not being to kind to me it seems a lot of hassle compared to windows but I will stick with it, I still cant get this to work so save me adding everything I have typed I will add a screenshot hopefully this will make it clearer, I have showed the box thing that shows the path to the file.

Thanks for all help so far
[[IMG]http://img141.imageshack.us/img141/3319/screenshot2ls.png[/IMG]]("http://img141.imageshack.us/i/screenshot2ls.png/")

Uploaded with [ImageShack.us]("http://imageshack.us")

---

### Post by Vaphell on 2011-02-08
first of all - why don't you try to install with software center/package manager first? Look for them in menus.
It's not windows, you don't have to download all apps on your own and go setup.exe on them. There is that thing called repository which streamlines installation of programs to the point of 'tick checkbox, apply'
There is a bunch of vmware stuff. You can try virtualbox too.

If you really really want to run install script
```
cd ~/Downloads/etc/vmware
chmod +x installer.sh
sudo ./installer.sh
```

you don't need to type everything, because it's easier to tap [tab] to autocomplete names after few characters. You avoid typos that way. And names are case sensitive so Downloads and downloads are not the same thing.

---

### Post by uRock on 2011-02-08
Try changing the Directory to get it where the file is. ```
cd ~/Downloads/etc/vmware/

```Then run chmod on the file. ```
chmod +x installer.sh
```Then to run the installer.```
./installer.sh
```

---

### Post by matt_symes on 2011-02-08
Hi

You spelt etc incorrectly. It's not spelt ect.

Kind regards

---

### Post by 3rdalbum on 2011-02-08
I'd highly recommend you look at my article "(Easy) How To Run Files":

[http://www.chrislees.info/ubuntu/easy-run-files.shtml](http://www.chrislees.info/ubuntu/easy-run-files.shtml)

Running executable files on Linux basically involves two steps: making it executable (this is a security feature) and running it - as root, if it's an installer.

It's not much more complicated than Windows, and that extra bit of complication helps prevent the spread of malware.

I'll also point out that, usually, you don't have to do this schmick. You can use Ubuntu Software Center to download and install programs very easily. If what you want is not in the Software Center, you can usually add a new repository or PPA so that your desired software WILL be available in Software Center.

---

