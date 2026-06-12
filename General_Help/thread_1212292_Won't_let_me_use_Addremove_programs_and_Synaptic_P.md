---
title: "Won't let me use Add/remove programs and Synaptic Package Manager"
date: 2009-07-13
forum: General Help
---

### Post by Ryan8524 on 2009-07-13
It will not let me use add/remove programs or Synaptic Package manager.
When I use Add/remove programs this comes up:

> 
This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.> 

When I use Synaptic Package Manger, this comes up:

> E: Type 'sudo' is not known on line 1 in source list /etc/apt/sources.list.d/winff.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.> 

Please help.
Just started with ubuntu....


Thanks.

PS: I'm currently running on genome.(If that helps at all)

---

### Post by snowpine on 2009-07-13
One nice thing about Linux is that the error messages are often actually helpful. :) Please copy and paste the contents of your /etc/apt/sources.list file (Alt+F2, gedit /etc/apt/sources.list), then open a terminal (Applications->Terminal), enter the following commands, and copy and paste the output here:

```
sudo apt-get update
sudo apt-get install -f
```

---

### Post by Ryan8524 on 2009-07-13
Thanks for you help.

I had another problem when i typed in that output in the terminal.
This came up:

E: Type 'sudo' is not known on line 1 in source list /etc/apt/sources.list.d/winff.list



Everytime I type 'sudo' that seems to come up.

Thank you for your help.

---

### Post by snowpine on 2009-07-13
I am sorry; I am not familiar with that error message. :( If you are not able to sudo, you can't make system-wide changes, so I really don't know what advice to give... but there are a lot of smart people on here, so good luck! :)

---

### Post by Celauran on 2009-07-13
> ```
E: Type 'sudo' is not known on line 1 in source list /etc/apt/sources.list.d/winff.list
```
As per your error message, have you checked the contents of /etc/apt/sources.list.d/winff.list?

Sounds like the word 'sudo' is on line 1 and this is what's causing the problems. This doesn't sound like a problem with sudo but with apt-get.

---

### Post by Ryan8524 on 2009-07-13
How would I check the contents of:

/etc/apt/sources.list.d/winff.list


Sorry, I'm really new to ubuntu and I'm trying to get a grasp of everything.

Thanks!

---

### Post by Elfy on 2009-07-13
Please do not post duplicates - this and the issue in [http://ubuntuforums.org/showthread.php?p=7610664](http://ubuntuforums.org/showthread.php?p=7610664) are the same thing.

Thread closed

---

