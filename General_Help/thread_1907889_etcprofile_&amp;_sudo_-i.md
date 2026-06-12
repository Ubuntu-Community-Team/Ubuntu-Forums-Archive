---
title: "/etc/profile &amp; sudo -i"
date: 2012-01-12
forum: General Help
---

### Post by guitou91 on 2012-01-12
Hello,

(first of all, i'm sorry for my poor english)
I 'am using a linux server

I would like to add the line "echo 250 32000 32 200 > /proc/sys/kernel/sem" into the /etc/profile file, to avoid to write this line at each boot of the PC.( it's modify the max number of arrays for semaphore)

BUT, to write this command, I need to be in "sudo -i" ( not just sudo).

I have tried to add at the end of profile file theses lines:

sudo -i
(at this point, I have to write the password)
echo 250 32000 32 200 > /proc/sys/kernel/sem
exit(to exit the sudo -i)

But when the Linux is booting, it's freeze just after theses lines. I have to do CTRL-C on or two times. 
At this point, the terminal writes: ~bash: /proc/sys/kernel/sem : Permission Denied.

but is read the /kernel/sem file, the value of "max number of arrays" is modified. 
But As I has to do some CTRL-C, I'am not connected, I have to write my login and passord for the session.

do you have a idea to modify the profile file, add a sudo -i command,
thank you very much
guitou

---

### Post by Toz on 2012-01-19
Hello and welcome to the forums.

It may be better to add this to the /etc/rc.local file. This file is executed at boot with root privleges so there would be no need to use sudo. Just make sure you append your line above the "exit 0" line so that it is executed. The file would look something like this:
```

...
echo "250 32000 32 200" > /proc/sys/kernel/sem
exit 0

```

---

### Post by guitou91 on 2012-01-20
Thank a lot,

I fixed my problem by changing the /etc/sysctl.conf file,
adding the line kernel.sem=250 32000 32 200

I don't know is the best file to do that, but no sudo is required.

G.

---

### Post by Elfy on 2012-01-20
Hi - your english is fine - much better than my french ;)

Please bear in mind this is an english speaking forum and post in english - there are if you wish to use them french forums available - [http://www.ubuntu.com/support/community/locallanguage#french](http://www.ubuntu.com/support/community/locallanguage#french)

---

### Post by Toz on 2012-01-20
> **guitou91 said:**
> Thank a lot,

I fixed my problem by changing the /etc/sysctl.conf file,
adding the line kernel.sem=250 32000 32 200

I don't know is the best file to do that, but no sudo is required.

G.

Yes, making the change in /etc/sysctl.conf is the preferred method.

---

