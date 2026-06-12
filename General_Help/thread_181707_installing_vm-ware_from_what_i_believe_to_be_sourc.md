---
title: "installing vm-ware from what i believe to be source"
date: 2006-05-24
forum: General Help
---

### Post by styven on 2006-05-24
Hi all,

Using this guide, [http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source) , I am attempting to install vm-ware.

I get as far as shown below and no further, i have installed the build-essential as directed...............

styven@edubuntu:~$ cd /home/styven/vmware-player-distrib
styven@edubuntu:~/vmware-player-distrib$ ./configure
bash: ./configure: No such file or directory
styven@edubuntu:~/vmware-player-distrib$ make
make: *** No targets specified and no makefile found.  Stop.
styven@edubuntu:~/vmware-player-distrib$

As far as i can see i am following the instuctions.......any ideas.

Steve

---

### Post by an.echte.trilingue on 2006-05-24
Well, that is how you generally compile software, but 

It would be much easier for us to help you if you told us where you got the package so that we could look at its specific setup.

You really should try to find a .deb.  Then you can install it very easily with this line:

sudo dpkg -i <name of file>

rather than having to comb through ./configure outputs and try to figure out which -packagexyz-dev files you need.

Also, if you do go the source code route, use install and use "checkinstall" rather than "make install" this will create a .deb that you can use again later and it will allow you to uninstall the package with apt and allow the apt database to track it.

Good Luck!

---

### Post by simonn on 2006-05-24
You are doing the wrong thing.

VMware player is not distributed as source - it is a proprietry application and is not Open Source.

Have a read of the following so you can learn the difference between source and binaries/executable code:

[http://en.wikipedia.org/wiki/Source_code](http://en.wikipedia.org/wiki/Source_code)
[http://en.wikipedia.org/wiki/Compiler](http://en.wikipedia.org/wiki/Compiler)


See the section "Using the tar installer" in:

[http://www.vmware.com/pdf/VMwarePlayerManual10.pdf](http://www.vmware.com/pdf/VMwarePlayerManual10.pdf)

The installer will need to compile modules for the kernel you have installed, so you will need to install the linux-headers package for the kernel you are running - if you are not sure what kernel you are running type the following into a terminal and paste the output here:

```

uname -a

```

---

### Post by aysiu on 2006-05-24
When I installed VMWare, it was .tar.gz, but it was not a typical "from source" installation.

I did need the *build-essential* metapackage and all the Linux headers for my kernel, but the command was ```
sudo ./vmware-install.pl
``` or something like that. It wasn't ```
./configure
```

Can you *cd* into the un-tarred VMWare folder and type ```
ls
``` and paste the output back here?

---

### Post by jpepin on 2006-05-24
I'm actually in the process of installing vmware also.  All you have to do is untar the download and run

```
sudo ./vmware-install.pl
```

from the newly created directory.

---

