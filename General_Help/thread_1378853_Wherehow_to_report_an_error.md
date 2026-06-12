---
title: "Where/how to report an error?"
date: 2010-01-11
forum: General Help
---

### Post by Silvernail on 2010-01-11
I need to report this error but can not find where to do this.```
Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Problem parsing dependency Recommends, E:Error occurred while processing webcamstudio (NewVersion1), E:Problem with MergeList /var/lib/apt/lists/apt.dolphinaura.studenthotspot.net_dists_jaunty_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'
```

I seem to remember a distribution or 2 ago an error reporting app, but 9.10 doesn't seem to have it.

---

### Post by Ocxic on 2010-01-11
seems to just be a corrupt package, try "sudo apt-get clean" then "sudo apt-get update" or re-run your last apt-get command when you got this error.

---

### Post by iponeverything on 2010-01-11
> **Silvernail said:**
> 
[..]
I seem to remember a distribution or 2 ago an error reporting app, but 9.10 doesn't seem to have it.

The tool is still there, it's apport:

[https://wiki.ubuntu.com/Apport](https://wiki.ubuntu.com/Apport)

I agree with Ocxic on the cause of your issue..

---

### Post by Silvernail on 2010-01-12
The 'clean' 'update' thingy works. Thanks.

I tried to remove 'webcamstudio' with the snyptic package manager and got same error as when I tried to call it.
> 
'E:Problem parsing dependency Recommends, E:Error occurred while processing webcamstudio (NewVersion1), E:Problem with MergeList /var/lib/apt/lists/apt.dolphinaura.studenthotspot.net_dists_jaunty_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

Then I tried:
> 
dave@dave:~$ sudo apt-get purge webcamstudio
[sudo] password for dave: 
Reading package lists... Error!
E: Problem parsing dependency Recommends
E: Error occurred while processing webcamstudio (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/apt.dolphinaura.studenthotspot.net_dists_jaunty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
dave@dave:~$ 


Thanks again guys

---

