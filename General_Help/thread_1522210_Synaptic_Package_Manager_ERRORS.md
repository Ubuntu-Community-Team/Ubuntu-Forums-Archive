---
title: "Synaptic Package Manager ERRORS"
date: 2010-07-01
forum: General Help
---

### Post by matey3 on 2010-07-01
Hello All:

I was running the Ubuntu Software Center when my machine froze, the mouse stopped moving etc. so I had to hard boot it.

Then I got a lot of errors and it would not boot, I got in as root and ran the fsck and fixed a lot of errors and so finally got to boot into GUI

Then I saw the red error sign which said run the sudo dpkg --configure -a to fix the problem
I did, it didnt?!
It gave me the error 

```
dpkg: failed to open package info file `/var/lib/dpkg/status' for reading: No such file or directory
```

I found the file status-old so I copied it back into status but then I got this error:


```
root@ubuntu:/var/lib/dpkg# sudo dpkg --configure -a
dpkg: parse error, in file '/var/lib/dpkg/updates/0000' near line 0:
 field name `
```

I get this error in the X as well when I run the Synaptic Pkg Mgr:
```

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

```

Any Ideas how to re install the synaptic Pkg Mgr? Or how to get it back to run with no errors please?

Thank you in advance!

---

### Post by plucky on 2010-07-02
> root@ubuntu:/var/lib/dpkg# sudo dpkg --configure -a
dpkg: parse error, in file '/var/lib/dpkg/updates/0000' near line 0:
 field name `

Open a terminal and ```
ls -l /var/lib/dpkg/updates/
``` to see how many files there are.Then delete them with ```
cd /var/lib/dpkg/updates/
ls
sudo rm *
```

The **ls** command is to make sure you are in the correct directory as you are using a "sudo rm" command ,from which there is no going back.

Then run ```
sudo dpkg --configure -a
``` again


Good Luck

---

### Post by matey3 on 2010-07-02
plucky:

Thank You Very Much!
You are da man!

It worked perfectly as you instructed.

I really appreciate it :) I was feeling the pain for the 3rd install after doing all the updates and getting my wireless to finally work (RTL8190SE).

Regards;

---

