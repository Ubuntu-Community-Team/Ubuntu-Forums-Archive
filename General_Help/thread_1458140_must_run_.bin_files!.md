---
title: "must run .bin files!"
date: 2010-04-19
forum: General Help
---

### Post by thekeymaster on 2010-04-19
I have checked the threads all day and tried the chmod 755 , then the sudo ./ command that seems to work for everone else.
then an erroe bos flashes on the screen saying i do not have the beccesary LSB 3.0 modules. as far as i can tell, the LSB modules are to change and test kernels and such. 
all i need to do is mount a 2 mb executable!

I am using 9.10  Gnomeamd 64 bit distro on an HP pavilion, if thats any help

---

### Post by jerome1232 on 2010-04-19
> **thekeymaster said:**
> I have checked the threads all day and tried the chmod 755 , then the sudo ./ command that seems to work for everone else.
then an erroe bos flashes on the screen saying i do not have the beccesary LSB 3.0 modules. as far as i can tell, the LSB modules are to change and test kernels and such. 
all i need to do is mount a 2 mb executable!

I am using 9.10  Gnomeamd 64 bit distro on an HP pavilion, if thats any help

Can you copy and paste the exact error you get when you attempt to run the .bin file? (ctrl+shift+c to copy out of a terminal) Based off of what you said it sounds like you need to install a dependency for this program.

---

### Post by lensman3 on 2010-04-19
Try "sh ./<bin-file>" (where <bin-file> is the file you want to execute.  If you use "sh", the file doesn't have to be executable. Note the leading ./ , so it will find the file in the current working directory.


Add the dot to the PATH environment variable.  Add it at the end.  Adding the dot to the PATH is a big security hole.

---

### Post by thekeymaster on 2010-04-19
the exact error message (it pops up in a window) is

LSB 3.0 or higher not found.  Please install the appropriate LSB packages.

---

### Post by thekeymaster on 2010-04-19
tried the sh option. exact same error. in addition to the window error, in the terminal it says ''no LSB modules are available''

the .bin file im trying to run is a security agent for a semi-public wifi network, if that helps!

---

### Post by geudrik on 2010-09-30
Hey man, I ran into the same issue. It's really pretty straight forward though - You need the LSB Runtime

Open up a Terminal Window

```

$ wget -c http://ftp.freestandards.org/pub/lsb/bundles/released-3.1.0/testkit/lsb-runtime-tests-3.1.0-3.x86_64.tar.gz
$ tar -xzf lsb-runtime-tests-3.1.0-3.x86_64.tar.gz
$ cd lsb-rt
$ ./install.sh
$ rm -r lsb*

```

Hope this helps (and I do appologize for having such a late reply :s)
I'm running Ubuntu 10.10 and use the damn Bradford Agent on one of the Campus Networks around here (I actually just run it as a friggin' startup command as ~/user/documents/scripts/bradford.bin )

---

