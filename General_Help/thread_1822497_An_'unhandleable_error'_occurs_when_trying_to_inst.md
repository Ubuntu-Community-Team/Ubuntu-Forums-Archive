---
title: "An 'unhandleable error' occurs when trying to install/remove apps"
date: 2011-08-10
forum: General Help
---

### Post by Raiast on 2011-08-10
[SIZE=2]Hey there! So first I was messing around trying to be able to download minecraft to my computer (it's very confusing for Linux, and I know nothing about this system!)

Now when I try to install apps in the Software Center I get this error:

                     [/SIZE]            [SIZE=2]There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks.[/SIZE]
[SIZE=2]
[/SIZE] 
[SIZE=2]Traceback (most recent call last): [/SIZE]
[SIZE=2]  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 961, in simulate [/SIZE]
[SIZE=2]    trans.unauthenticated = self._simulate_helper(trans) [/SIZE]
[SIZE=2]  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1085, in _simulate_helper [/SIZE]
[SIZE=2]    return depends, self._cache.required_download, \ [/SIZE]
[SIZE=2]  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 226, in required_download [/SIZE]
[SIZE=2]    pm.get_archives(fetcher, self._list, self._records) [/SIZE]
[SIZE=2]SystemError: E:I wasn't able to locate file for the sun-java6-jre package. This might mean you need to manually fix this package. 
[/SIZE]


[SIZE=2]I've seen a solution that seemed to work for someone else but when I go into the Terminal and type in the commands it asks for my sudo password and I have no idea what that means/is because I never set any kind of password like that.[/SIZE]


[SIZE=2]Any help? Please? This is incredibly frustrating.
[/SIZE]

---

### Post by MG&amp;TL on 2011-08-10
Your 'sudo' password on your computer IF you are the only user or the person who set  it up, is your normal password. :D

This also applies for 'gksu' and 'gksudo' password.

Does 'apt-get' through the terminal work ok? e.g (Mesa-utils is a random application I use to test whether my graphics card is working properly, replace with whatever you like, as long as it's a package.)

```
sudo apt-get install mesa-utils
```

---

### Post by Raiast on 2011-08-10
> **MG&TL said:**
> Your 'sudo' password on your computer IF you are the only user or the person who set  it up, is your normal password. :D

This also applies for 'gksu' and 'gksudo' password.

Does 'apt-get' through the terminal work ok? e.g (Mesa-utils is a random application I use to test whether my graphics card is working properly, replace with whatever you like, as long as it's a package.)

```
sudo apt-get install mesa-utils
```

[SIZE=2]When I try the apt-get command I get this:

[/SIZE]   	 	 	 	 	 	  E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by MG&amp;TL on 2011-08-10
That means something else is trying to install something. Close or stop anything else that is installing or running as root.

Root (slightly dumbed down for clarity) is what happens when you use sudo.

---

### Post by Raiast on 2011-08-10
[SIZE=2]Nothing is running except firefox and terminal... =/[/SIZE]

---

### Post by Raiast on 2011-08-10
I'm going to try restarting my computer and running the apt-get agan... stayed tuned please? Thanks for your help so far.

---

### Post by MG&amp;TL on 2011-08-10
No problem...;)

---

