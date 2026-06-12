---
title: "can't install anything"
date: 2011-12-19
forum: General Help
---

### Post by desire123 on 2011-12-19
i'm using 11.10version and when i try to install something i always get a messege


installArchives() failed: dpkg: error: configuration error: /etc/dpkg/dpkg.cfg.d/multiarch:1: unknown option 'popcorn'
Error in function: 



how can i fix this?????????

---

### Post by dabl on 2011-12-19
Close your software center, open a terminal window, and enter this:

```
sudo dpkg --configure -a
```

Tell about any errors that you see.

---

### Post by desire123 on 2011-12-20
dpkg: error: configuration error: /etc/dpkg/dpkg.cfg.d/multiarch:1: unknown option 'popcorn'

---

### Post by dabl on 2011-12-20
Is your system 32-bit or 64-bit?

Can you open a terminal, issue this command, and post the output?

```
cat /etc/dpkg/dpkg.cfg.d/multiarch
```

---

### Post by desire123 on 2011-12-20
output: ```
popcorn
```
and system i am running is 32bit

---

### Post by matt_symes on 2011-12-20
Hi

> **desire123 said:**
> output: popcorn
and system i am running is 32bit

@desire123. 

Can i recommend that you copy and paste your output from the terminal into your posts.

You can do this by highlighting the text and selecting copy. You can paste this into you next post. It will help people to diagnose your problems quicker.

Here's an example of how i was able to replicate your problem.
```

matthew@matthew-Aspire-7540:~$ echo "popcorn" | sudo tee /etc/dpkg/dpkg.cfg.d/multiarch
popcorn
matthew@matthew-Aspire-7540:~$ cat !$
cat /etc/dpkg/dpkg.cfg.d/multiarch
popcorn
matthew@matthew-Aspire-7540:~$ sudo apt-get install lynx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  lynx-cur
The following NEW packages will be installed
  lynx lynx-cur
0 upgraded, 2 newly installed, 0 to remove and 16 not upgraded.
Need to get 0 B/1,030 kB of archives.
After this operation, 2,458 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: error: configuration error: /etc/dpkg/dpkg.cfg.d/multiarch:1: unknown option 'popcorn'
E: Sub-process /usr/bin/dpkg returned an error code (2)
matthew@matthew-Aspire-7540:~$ 
```You can see what the person has typed and see the exact response from the terminal.

Just a helpful tip :)

@dabl. Hopefully not stepping on your toes here.

Kind regards

---

### Post by dabl on 2011-12-20
> **matt_symes said:**
> Hi

@dabl. Hopefully not stepping on your toes here.



No problem -- it is preferable to see the entered command, as well as the output.

@desire123, can you open your editor in super-user mode, with Alt-F2 "gksudo gedit", and then open the file /etc/dpkg/dpkg.cfg.d/multiarch for editing?  If so, I want you simply insert a "#" hash mark in front of the word "popcorn", so it reads

#popcorn

Then do File > Save, and exit gedit.  Then run the command that I gave you in my first post, and let's see what happens.

---

### Post by desire123 on 2011-12-20
Thx a lot, it works. You saved my life. :popcorn::KS:P:D

---

### Post by dabl on 2011-12-20
Great!  :popcorn:

Now, please open your original post, and edit the title, and insert the work "SOLVED" at the beginning, so if another person has the same problem, they can find the solution here.  Thanks!

---

