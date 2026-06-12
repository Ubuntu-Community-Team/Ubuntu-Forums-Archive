---
title: "Open Office running can't close it"
date: 2010-06-23
forum: General Help
---

### Post by petellgra on 2010-06-23
Hi Have a big problem. when I try to install anything from synaptic, this message pops up :
================
OpenOffice.org is running right now. This can cause problems with (de-)registration of components and extensions.

You should close all running instances of OpenOffice.org (including any currently running Quickstarter) before proceeding with the package upgrade.
=================
How do I close it when it's not running. Can any one help.
Pete

---

### Post by wilee-nilee on 2010-06-23
Look in system monitor to see if it's running. If your trying to update or upgrade open office outside of a standard method, you might want to know that open office is a finicky program. Give a explanation of what your doing in synaptic that causes this warning.

---

### Post by Smart Viking on 2010-06-23
Hi,

run this command

```
ps -e | grep -i openoffice
```

If it gives you any output at all, that means openoffice is on some way running.

I am not sure if it WILL give any output, but if it does, here is how to kill it:

When you runned the first command, every process that had "openoffice" in it, would be displayed. At the very beginning of every line in the output, there will be some numbers:

*23125 ?        00:00:00* <process name>
^ That are the process "ID"

What you want to do, is to run thte following command
Insert the process id of openoffice in this:
```
kill -9 <process ID>
```

That will terminate the process, then you could try to install openoffice after that.

I hope this helps, but if the first command doesn't give any output, then this wont help. :)

---

### Post by mikewhatever on 2010-06-23
Let's see the output of **ps aux | grep -i office**

---

### Post by petellgra on 2010-06-23
What I was doing was using synaptic for was getting rekonq  :

and before that Qtdemo and that came up with this:

> peter@peter-desktop:~$ qtdemo
The program 'qtdemo' is currently not installed.  You can install it by typing:
sudo apt-get install qt4-demos
peter@peter-desktop:~$ sudo apt-get install qt4-demos
[sudo] password for peter: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libautotrace3 libgtkimageview0 autotrace python-rsvg
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  qt4-demos
0 upgraded, 1 newly installed, 0 to remove and 61 not upgraded.
2 not fully installed or removed.
Need to get 6,554kB of archives.
After this operation, 36.9MB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  qt4-demos
Install these packages without verification [y/N]? y
Get:1 [http://76.73.4.58/ubuntu/](http://76.73.4.58/ubuntu/) lucid/main qt4-demos 4:4.6.2-0ubuntu5 [6,554kB]
Fetched 6,554kB in 17s (370kB/s)                                               
Selecting previously deselected package qt4-demos.
(Reading database ... 289490 files and directories currently installed.)
Unpacking qt4-demos (from .../qt4-demos_4%3a4.6.2-0ubuntu5_i386.deb) ...
Setting up openoffice.org-writer2latex (1.0-10ubuntu1) ...
dpkg: error processing openoffice.org-writer2latex (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up openoffice.org-writer2xhtml (1.0-10ubuntu1) ...
dpkg: error processing openoffice.org-writer2xhtml (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up qt4-demos (4:4.6.2-0ubuntu5) ...
Errors were encountered while processing:
 openoffice.org-writer2latex
 openoffice.org-writer2xhtml
E: Sub-process /usr/bin/dpkg returned an error code (1)
peter@peter-desktop:~$ qtdemoI think OpenOffice is configuring OpenOffice.org2Latex on another window. Gawd this is different to windows.
I must admit I got a habit of experimenting maybe not a good idea (hahaha) Only been on linux for a few weeks. I just found another terminal opened it's frozen. I'm going to shutdown then come back and see if we can sort it out then. 

Thanks for the replies 
Pete

---

### Post by wilee-nilee on 2010-06-23
I think the other two peoples post with commands are helpful probably. You also can't install from the terminal when synaptic is open or the software center, they are all independent install devices that can't be run simultaneously. So make sure your only using one at a time. 

I don't see any indication of this other then you reference the OO latex installing, in another window. As I said OO in very finicky you have to be careful with it. The other two installs don't have any direct dependencies with OO but one of them (rekonq) the KDE one has a bunch of lib dependencies. 

If you go to synaptic, and enable the bar in the bottom window from settings-preferences show package properties in main window it is helpful at times to see the dependencies. 

It takes a little while to get the hang of things if this is new to you just be careful with trying to enable and add and remove stuff without knowing what your doing or asking questions.

---

### Post by petellgra on 2010-06-23
Mikewhatever
This the print out of :
ps -e | grep -i openoffice
> peter@peter-desktop:~$ sudo dpkg --configure -a
[sudo] password for peter: 
Setting up openoffice.org-writer2xhtml (1.0-10ubuntu1) ...
dpkg: error processing openoffice.org-writer2xhtml (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up kdebase-data (4:4.4.2-0ubuntu2) ...
Setting up kdebase-bin (4:4.4.2-0ubuntu2) ...
Setting up rekonq (0.4.0-0ubuntu1) ...
Setting up openoffice.org-writer2latex (1.0-10ubuntu1) ...
dpkg: error processing openoffice.org-writer2latex (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 openoffice.org-writer2xhtml
 openoffice.org-writer2latex
peter@peter-desktop:~$ ps aux | grep -i office
docvert   1057  0.0  0.0   1828   540 ?        S    19:29   0:00 /bin/sh /usr/share/docvert/core/config/unix-specific/openoffice.org-server.sh
docvert   1059  0.0  0.0   1828   572 ?        S    19:29   0:00 /bin/sh /usr/bin/soffice -headless -norestore -nologo -norestore -nofirststartwizard -accept=socket,port=2002;urp;
docvert   1096  0.0  0.9 120960 35492 ?        Sl   19:29   0:00 /usr/lib/openoffice/program/soffice.bin -headless -norestore -nologo -norestore -nofirststartwizard -accept=socket,port=2002;urp;
peter     2040  0.0  0.0   4408   924 pts/0    S+   19:57   0:00 grep --color=auto -i office
Hope it helps I don't have anything else running. I shut down and started again. 
Pete

---

### Post by wilee-nilee on 2010-06-23
Did you stop a install in the middle of it, it looks that way, in the terminal
```
sudo apt-get install -f 
```

---

### Post by petellgra on 2010-06-23
wilee-nilee
I don't think so. But at this stage anythings possible. What can I do?
Pete

---

### Post by wilee-nilee on 2010-06-23
> **petellgra said:**
> wilee-nilee
I don't think so. But at this stage anythings possible. What can I do?
Pete

The command I posted along with the sudo dpkg --configure -a clear things up sometimes.

I would also look in synaptic for broken packages, bottom left-custom filters-broken.

Another way to clear up broken, or stuff in general is to reboot and use the 2nd line recovery from the kernel list in grub and fix broken packages.

---

### Post by petellgra on 2010-06-23
wilee-nilee
So you want me to post these together one after the other. 

> sudo apt-get install -f sudo dpkg --configure -a 

Is that what I should do in that order.
Pete

---

### Post by wilee-nilee on 2010-06-23
> **petellgra said:**
> wilee-nilee
So you want me to post these together one after the other. 

Is that what I should do in that order.
Pete

No you ran one of them already the dpkg -a, run the other. These are just to clear up stuff you can post the results of the one I posted if you like.
```
sudo apt-get install -f 
``` 

To be honest here I don't know the problem your having is I'm just suggesting standard commands that clear stuff up.

Both of the commands you stuck together will free up blocked processes, In one of your posts if you look closely you ran the dpkg -a command. These commands are used when a install has been broken or shutdown in the middle of running.

---

### Post by petellgra on 2010-06-23
wilee-nilee
This is the result from : $ sudo dpkg --configure -a

peter@peter-desktop:~$ sudo dpkg --configure -a
[sudo] password for peter: 
dpkg: status database area is locked by another process
peter@peter-desktop:~$ dpkg: status database area is locked by another process
No command 'dpkg:' found, did you mean:
 Command 'dpkg' from package 'dpkg' (main)
dpkg:: command not found
peter@peter-desktop:~$ peter@peter-desktop:~$ 
peter@peter-desktop:~$: command not found
peter@peter-desktop:~$ 
pete

---

### Post by wilee-nilee on 2010-06-23
> **petellgra said:**
> wilee-nilee
This is the result from : $ sudo dpkg --configure -a

peter@peter-desktop:~$ sudo dpkg --configure -a
[sudo] password for peter: [B]
dpkg: status database area is locked by another process[/B]
peter@peter-desktop:~$ dpkg: status database area is locked by another process
No command 'dpkg:' found, did you mean:
 Command 'dpkg' from package 'dpkg' (main)
dpkg:: command not found
peter@peter-desktop:~$ peter@peter-desktop:~$ 
peter@peter-desktop:~$: command not found
peter@peter-desktop:~$ 
pete

The highlighted one makes it seem as something was interrupted, so run the other.
```
sudo apt-get install -f
```

If you get a read out again like this last one that I have highlighted go to synaptic as I described and look for broken packages as I described. 

If this doesn't work reboot the computer and use the recovery 2nd line in kernel list to get to the broken package line and run it. Then hit boot normally top line if it gets you to a command line login and use startx to get to the desktop.

If none of this works run ```
sudo apt-get autoremove
```

Then run ```
sudo apt-get autoclean
```

Do all of this in the order that I have them listed. If you can't get into synaptic in this process then I am just not sure whats up.

---

### Post by petellgra on 2010-06-23
wilee-nilee or whoever
 I just tried to use synaptic to install gimpweb and this is still happening
> OpenOffice.org is running right now. This can cause problems with (de-)registration of components and extensions.

You should close all running instances of OpenOffice.org (including any currently running Quickstarter) before proceeding with the package upgrade.
What's Quickstarter?
Pete

---

### Post by wilee-nilee on 2010-06-23
Your wasting my time by not following any instructions or if you have; you haven't at any point addressed this,] good luck.:confused:](*,)](*,)](*,):confused::mad:

---

### Post by petellgra on 2010-06-23
wilee-nilee,
I apologize if you think I'm wasting your time. But everytime I run any of your commands it comes up that openoffice is running and throws an error. I even tried to uninstall Open office and it threw the same error.
Pete

---

### Post by nerdy_kid on 2010-06-23
ive had this issue before, open system monitor and search for any processes named "ooo" or openoffice something like that (i dont have openoffice installed so dont know for sure.)
quickstarter is a program that basicly preloads openoffice into memory so that it starts faster, and that we are looking for.
kill that process, then close synaptic and run 
```

sudo apt-get update && sudo apt-get upgrade

```


if that still doesnt work, then reboot open a terminal and enter
```

ps -e

```
then paste the output of that command here.  Ill tell you which process needs to die.

---

