---
title: "I need to reinstall adobe flash, but it won't let me."
date: 2009-11-11
forum: General Help
---

### Post by nal13 on 2009-11-11
My adobe flash isn't working, it says I need to reinstall it, but it won't let me. When I go into the synaptic I get prompted this "E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report."

Please help. :D

TIA

---

### Post by bashphoenux on 2009-11-11
open terminal,type
sudo apt-get install flashplugin
and
sudo apt-get install flashplugin-installer
and see if it works

---

### Post by michy99 on 2009-11-12
Go to System->Administration->Software Sources. Click Other Software tab. Make sure the partner repositories are enabled.

---

### Post by nal13 on 2009-11-12
> **bashphoenux said:**
> open terminal,type
sudo apt-get install flashplugin
and
sudo apt-get install flashplugin-installer
and see if it works

I get this:

```

nick@nick-laptop:~$ sudo apt-get install flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
nick@nick-laptop:~$ sudo apt-get install flashplugin-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
nick@nick-laptop:~$ 

```

---

### Post by bashphoenux on 2009-11-12
sudo apt-get remove flashplugin
sudo apt-get remove flashplugin-installer 

and then try running those commands!
and then ensure if this is done :

> **michy99 said:**
> Go to System->Administration->Software Sources. Click Other Software tab. Make sure the partner repositories are enabled.

---

### Post by nal13 on 2009-11-12
> **michy99 said:**
> Go to System->Administration->Software Sources. Click Other Software tab. Make sure the partner repositories are enabled.

I am kind of confused as to what you mean. I go to the software sources and the "Other Software" tab, but should I check all the boxes?

---

### Post by michy99 on 2009-11-12
Check the two lines that have the word 'partner' in them.

---

### Post by bashphoenux on 2009-11-12
enable the check box with
[http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free
[http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free(source codE)

---

### Post by nal13 on 2009-11-12
> **bashphoenux said:**
> enable the check box with
[http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free
[http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free(source codE)

Mine doesn't have that in there, I have:
[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner (source code)
[http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable main

I have all those checked, then I ran the command lines. It looks like it's working then the last thing while installing is this
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by michy99 on 2009-11-12
Run this:```
sudo dpkg --configure -a
```

---

### Post by nal13 on 2009-11-12
> **michy99 said:**
> Run this:```
sudo dpkg --configure -a
```

```

nick@nick-laptop:~$ sudo dpkg --configure -a
dpkg: error processing adobe-flashplugin (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 adobe-flashplugin

```

---

### Post by slakkie on 2009-11-12
Can you run lsb_release -a, so we have a clue which OS you are running. Much appreciated.

---

### Post by michy99 on 2009-11-12
```
sudo apt-get purge adobe-flashplugin
sudo apt-get clean
sudo apt-get install adobe-flashplugin
```

---

### Post by nal13 on 2009-11-12
> **slakkie said:**
> Can you run lsb_release -a, so we have a clue which OS you are running. Much appreciated.

```

nick@nick-laptop:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 9.10
Release:	9.10
Codename:	karmic

```

---

### Post by nal13 on 2009-11-12
> **michy99 said:**
> ```
sudo apt-get purge adobe-flashplugin
sudo apt-get clean
sudo apt-get install adobe-flashplugin
```

That didn't do it either.

---

### Post by bashphoenux on 2009-11-12
> **bashphoenux said:**
> enable the check box with
[http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free
[http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free(source codE)

add these two to the list !!

---

### Post by slakkie on 2009-11-12
> **nal13 said:**
> ```

nick@nick-laptop:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 9.10
Release:	9.10
Codename:	karmic

```

Add the following line to your sources.list:

```

deb http://archive.canonical.com/ubuntu karmic partner

```

sudo aptitude update and install the bugger.

---

### Post by nal13 on 2009-11-12
> **bashphoenux said:**
> add these two to the list !!

I go to add, then type in the line, but it won't let me click "+add source," it won't light up.

---

### Post by slakkie on 2009-11-12
> **bashphoenux said:**
> add these two to the list !!

No, he shouldn't you're posting jaunty sources, he uses karmic.

to add the sources do:

```

sudo nano /etc/apt/sources.list

```

```

deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner
## Medibuntu repositories, check http://www.medibuntu.org/ for more details
deb http://packages.medibuntu.org/ karmic free non-free
#deb-src http://packages.medibuntu.org/ karmic free non-free

```

sudo aptitude update, if you get BADKEY warnings, do this:

```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys KEYID

```

---

### Post by nal13 on 2009-11-12
> **slakkie said:**
> Add the following line to your sources.list:

```

deb http://archive.canonical.com/ubuntu karmic partner

```

sudo aptitude update and install the bugger.

Thanks you! That did it.

Thank you guys so much. :D

---

### Post by slakkie on 2009-11-12
NP :) Keep that repo, it will be handy in future releases as well (for flash ;))

---

### Post by bashphoenux on 2009-11-12
oh yeah sorry mate !! forgot u were using karmic :P
never mind thanks to [slakkie]("http://ubuntuforums.org/member.php?u=116199")
problem resolved :)

---

### Post by nal13 on 2009-11-12
> **slakkie said:**
> NP :) Keep that repo, it will be handy in future releases as well (for flash ;))

Will do! :D

---

### Post by nal13 on 2009-11-12
> **bashphoenux said:**
> oh yeah sorry mate !! forgot u were using karmic :P
never mind thanks to [slakkie]("http://ubuntuforums.org/member.php?u=116199")
problem resolved :)

haha, thanks. :D

---

