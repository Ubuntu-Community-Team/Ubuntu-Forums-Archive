---
title: "Karmic: Brother Printer installation"
date: 2010-02-04
forum: General Help
---

### Post by Robbyx on 2010-02-04
Does any one recognise why I am getting the following error messages:

```
rob@rob-desktop:~$ cd /root
rob@rob-desktop:/root$ sudo dpkg -i --force-all wrap
[sudo] password for rob: 
dpkg: error processing wrap (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 wrap

```

If I click on the wrap.deb it opens normally in the deb file opener. Brother have told me not to do it that way, because I am having problems with the colour. I want black and white, I choose greyscale and it comes out colour. They helped me uninstall the drivers and then said I have to use the command line approach with them supplying the parameters as used. They could not see why I was getting the error message. They suggested I put their two drivers in the root directory.

---

### Post by hawthornso23 on 2010-02-04
Try doing it in  /  instead of  /root

Root directory is usually  /  on linux systems as it is the root of the file structure. 

Ubuntu also has a directory called /root .  This is confusing.

---

### Post by Robbyx on 2010-02-04
Still I have the problem. In fact I do not have my printer working.

I have also tried the following:

Changing the permissions to read write and the owner to me rather than root.
For convenience  I have changed the name of the file. The file path is a result of copying the directory entry so it is correct. Here is the latest attempt:


> rob@rob-desktop:~$ sudo dpkg -i --force-all file:///root/lpr1.deb 
[sudo] password for rob: 
dpkg: error processing file:///root/lpr1.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 file:///root/lpr1.deb
rob@rob-desktop:~$ 


I spent a lot of time with Brother support and in effect they gave up so I am grateful for any help.

---

### Post by plucky on 2010-02-04
> Still I have the problem. In fact I do not have my printer working.



It would be useful to know the model number of the printer you are trying to install,and what install guide you are following?

I have never heard of the wrap.deb you are trying to install and where did you get it from?

---

### Post by hawthornso23 on 2010-02-04
```
rob@rob-desktop:~$ sudo dpkg -i --force-all [COLOR=Red]file:///root[/COLOR]/lpr1.deb 
[sudo] password for rob: 
dpkg: error processing [COLOR=Red]file:///root[/COLOR]/lpr1.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 [COLOR=Red]file:///root/[/COLOR]lpr1.deb
rob@rob-desktop:~$  			 		
```

Looks like you still have it in /root and not in / . At least that is where you are trying to install it from. Also I'm not convinced you need to have that file://  on the front. 

Try moving it into /

```

sudo mv /root/lpr1.deb /

```

Checking ownership and permissions,
and then fiddling with variations on

```

cd /
 sudo dpkg -i --force-all  lpr1.deb 

```

I suspect it might just be a simple syntax problem.

---

### Post by Robbyx on 2010-02-04
Thank you very much for your help.

I sorted it by following the advice at [http://www.uluga.ubuntuforums.org/showthread.php?t=590793](http://www.uluga.ubuntuforums.org/showthread.php?t=590793). I followed it down to the level of moving the deb files to the desktop and it installed ok. Sadly what started all this has not cleared up. I have set the printer to greyscale but it prints colour.

---

