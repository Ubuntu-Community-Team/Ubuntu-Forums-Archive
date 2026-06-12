---
title: "Software Package Manager Troubling me a lot"
date: 2011-10-26
forum: General Help
---

### Post by nevinalex1234 on 2011-10-26
Its been under 2 week since i installed Ubuntu 11.10. 
I was very happy with the GUI and the appearance. But right now, its not even allowing me to install an application from either the Software Center or the terminal
for ex :
"
nevin@nevin-HP-Pavilion-dv6700-Notebook-PC:~$ sudo apt-get install texlive
[sudo] password for nevin: 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
" ....
I get the above error when i try to install something (in this case Latex) from terminal

When i try from the Ubuntu Software centre, they start to install, but abrupty end by saying
A WINDOW POPS UP SAYING
"
an unhandleable error occured
There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks.

details : Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 968, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1092, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 235, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate a file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.
"...

This kind of error pops up for all things i try to do by Ubuntu Software Manager.
PLEASEEEEEEEE HELP 
Else i will have to downgrade back to 9.04 coz i have to install a lot of sofwares to kick start my work.
PLEASEEEEEEEEEEEEEEEEEEEEEE

---

### Post by Bobhuber on 2011-10-26
> **nevinalex1234 said:**
> Its been under 2 week since i installed Ubuntu 11.10. 
I was very happy with the GUI and the appearance. But right now, its not even allowing me to install an application from either the Software Center or the terminal
for ex :
"
nevin@nevin-HP-Pavilion-dv6700-Notebook-PC:~$ sudo apt-get install texlive
[sudo] password for nevin: 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
" ....
I get the above error when i try to install something (in this case Latex) from terminal

When i try from the Ubuntu Software centre, they start to install, but abrupty end by saying
A WINDOW POPS UP SAYING
"
an unhandleable error occured
There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks.

details : Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 968, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1092, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 235, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate a file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.
"...

This kind of error pops up for all things i try to do by Ubuntu Software Manager.
PLEASEEEEEEEE HELP 
Else i will have to downgrade back to 9.04 coz i have to install a lot of sofwares to kick start my work.
PLEASEEEEEEEEEEEEEEEEEEEEEE

Open up a terminal and do exactly what it is telling you to do
sudo dpkg --configure -a

---

### Post by collisionystm on 2011-10-26
> **Bobhuber said:**
> Open up a terminal and do exactly what it is telling you to do
sudo dpkg --configure -a


Took the words right out of my keyboard!

---

### Post by nevinalex1234 on 2011-10-26
> **Bobhuber said:**
> Open up a terminal and do exactly what it is telling you to do
sudo dpkg --configure -a

I am able to proceed with my Terminal installation
But my UbunTU sOfware CEntre problem still remains

---

### Post by plucky on 2011-10-27
> But my UbunTU sOfware CEntre problem still remains 

Try ```
sudo apt-get install -f
```

Or check in Synaptic Package Manager for broken package > SystemError: E:I wasn't able to locate a file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.

Good Luck

---

### Post by astalkinglion on 2011-12-15
Synaptic wasn't on the menu search at all, thankfully sudo apt-get install -f fixed the broken package, at which point I could continue with my install. Thank you, I registered expressly to state this worked for me. There is a real void of help in most Linux communities, I have to say luckily there's been an answer from an expert on all these issues, it's sad they continue to be problems though, perhaps they should be autorunning the package fixer at this point....

---

