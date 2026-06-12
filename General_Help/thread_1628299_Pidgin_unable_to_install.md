---
title: "Pidgin unable to install"
date: 2010-11-22
forum: General Help
---

### Post by Tellyviision on 2010-11-22
I had to remove pidgin because I thought it would fix the annoying SSL error.

But now, when I try to re-install it.

[http://icanhasimage.com/images/f5f1i2wvu2k829mr26tm.png](http://icanhasimage.com/images/f5f1i2wvu2k829mr26tm.png)

Any help? I'm using Ubuntu 10.10 btw

---

### Post by Tellyviision on 2010-11-22
i just tried to install it in Synaptic, and in Ubuntu Tweak

no luck :(

---

### Post by Soul-Sing on 2010-11-22
Do you get an errormessage? Example after ```
sudo apt-get install pidgin
```
Copy-paste the errors on the forum please
[COLOR="Red"]but first[/COLOR] ```
sudo apt-get purge pidgin
```

---

### Post by Soul-Sing on 2010-11-22
for SSL problem pidgin.  solution:
1) [http://developer.pidgin.im/wiki/MSNCertIssue](http://developer.pidgin.im/wiki/MSNCertIssue)
2) or disable SSL in pidgin

---

### Post by Tellyviision on 2010-11-22
laptop@ubuntu:~$ sudo apt-get install pidgin
[sudo] password for laptop: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 pidgin : Depends: pidgin-data (< 1:2.7.3-z) but 1:2.7.5-1ubuntu2+pidgin1.10.10 is to be installed
E: Broken packages

---

### Post by Soul-Sing on 2010-11-22
try this to install the package you need: [https://launchpad.net/ubuntu/maverick/i386/pidgin/1:2.7.3-1ubuntu3.1](https://launchpad.net/ubuntu/maverick/i386/pidgin/1:2.7.3-1ubuntu3.1) and remove the other via synaptic packagemanager.

---

### Post by Soul-Sing on 2010-11-22
on the other hand a newer version will not perse solve your SSL pidgin problem. It is a simple certificate change problem.....

---

### Post by Tellyviision on 2010-11-22
That download didn't work either.

And I understand it won't fix it now, however I cannot run pidgin at all right now.

---

### Post by Tellyviision on 2010-11-22
I fixed the problem, I just needed to go into ubuntu tweak and delete pidgin.data

and everything is good now ;)

---

### Post by Soul-Sing on 2010-11-23
> **Tellyviision said:**
> I fixed the problem, I just needed to go into ubuntu tweak and delete pidgin.data

and everything is good now ;)

Ok, good job!

---

