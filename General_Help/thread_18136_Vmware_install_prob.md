---
title: "Vmware install prob"
date: 2005-03-04
forum: General Help
---

### Post by kurisutofaa on 2005-03-04
I'm trying to install vmware on my warty ubuntu. I'm using kernel 2.6.8.1-5. When I run vmware-config.pl comes this
> Making sure services for VMware Workstation are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done

Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Workstation is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The path "/usr/src/linux/include" is not an existing directory.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

error is: The path "/usr/src/linux/include" is not an existing directory.
I have read vmware forums and most common solution was that kernel source wasn't installed. I installed them, but doesn't still work (package name was linux-source 2.6.8.1 but version was 2.6.8.1-16.11 while my kernel is 2.6.8.1-5. Is this bad thing? This is the only source I found for this kernel). Then I noticed that even /usr/src/linux doesn't exist. /usr/src includes 
linux-source-2.6.8.1.tar.bz2  
rpm
nvidia-kernel-source.tar.gz

I have no idea how to fix this thing. Please somebody help me. I need your mighty help! 
Thanks

---

### Post by kassetra on 2005-03-04
[QUOTE=kurisutofaa]
error is: The path "/usr/src/linux/include" is not an existing directory.
I have no idea how to fix this thing. Please somebody help me. I need your mighty help! 
Thanks[/QUOTE]

Ok, first here.  You need to make a link:  (I'm a little worried about your versions not matching... but try this)
1. Open a terminal (Applications->System Tools->Terminal)
2. Find your version number by typing this in the command line:
```
ls /usr/src/linux-headers*
``` That will show you the exact directory name you need for the next step  (if you have more than one... pm me)
3. Type this on the line:
 ```
sudo ln -s /usr/src/linux-headers-YOUR VERSION HERE /usr/src/linux
``` 
4. then retry your vmware setup.

---

### Post by kurisutofaa on 2005-03-05
Thank you for your reply, but /usr/src/linux-headers* doesn't exist. Like I said in my first post:  /usr/src contains only the following:
linux-source-2.6.8.1.tar.bz2 
rpm
nvidia-kernel-source.tar.gz

Please help

---

### Post by bored2k on 2005-03-05
[QUOTE=kurisutofaa]Thank you for your reply, but /usr/src/linux-headers* doesn't exist. Like I said in my first post:  /usr/src contains only the following:
linux-source-2.6.8.1.tar.bz2 
rpm
nvidia-kernel-source.tar.gz

Please help[/QUOTE]
 > $apt-cache search linux headers
find yours, after installing them find theyre location, and point them to vmware's . it worked for me on vmware 4.5

---

### Post by kassetra on 2005-03-05
Ok, then the header files you need to install vmware are not installed.  Do this:

1. Open Synaptic (Computer->System Configuration->Synaptic Package Manager) -- enter your password when it asks for a password
2. Click the Search button.
3. Type in linux-image in the box and press enter. The results of this search will tell you what you need to look for in the next search (When I do this search, Synaptic tells me that the *package name* I have installed (it has a green box to the left) is linux-image-2.6-k7).
4. Now that you know the linux-image package name, press the Search button again, and this time type in linux-headers (you will probably have to erase your previous search from the box first) and press enter.
5. Now since you know the linux-image package name, search through the list until you find a linux-headers package name that MATCHES the linux-image package name. (In my case, my matching package name is linux-headers-2.6-k7)
6. Right click on the package name that you have chosen (the one that matches the package name of your linux-image), and then left click on "Mark for Installation" in the little menu that pops up.
7. If you get a popup that says "Mark additonal required changes" click on the "Mark" button.  
8. Click Apply.
9. When it's done, click "close" or whatever the little box says, and then exit Synaptic.  :)
---
Try installing vmware again. If it doesn't find the /usr/src/linux-headers-X, make the link as I told you earlier, and try again. :)

---

### Post by kurisutofaa on 2005-03-06
Allright! thank you guys. You cold have just said simply that I need linux-header packages that maches my kernel. 

Thanks to you!  =D>

---

