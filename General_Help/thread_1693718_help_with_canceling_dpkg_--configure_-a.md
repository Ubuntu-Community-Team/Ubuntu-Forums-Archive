---
title: "help with canceling dpkg --configure -a"
date: 2011-02-23
forum: General Help
---

### Post by mashume on 2011-02-23
Hello all, 

I was using synaptic [sp?] package manager to install cltl (common lisp book) when our office internet went down. It had reached a point where it gave the message (in a black back-ground window) that it was "downloading CLTL from the internet. It seemed to have hung at that point in the package installation. When one of my office mates tried to reset the wireless router, he did it by turning off the power strip and killed my computer.

After restarting the machine, I was greeted by the message to run dpkg --configure -a using sudo. which I did. but the terminal still seems to hang saying "DOWNLOADING CLTL FROM THE INTERNET".

Now all I want to do is kill the installation of cltl. How do I do this. I can't use sudo apt-get remove or purge as it says it can't obtain a lock. If I restart, dpkg wants me to run --configure -a again which hangs at the same point.

help.

Thank you.

Running 10.10 Ubuntu 32bit

---

### Post by Habitual on 2011-02-23
"it says it can't obtain a lock."

It should indicate the location of the lock file in that dialog/message.

Please use 
```
sudo rm -f /path/to/lock_file 
```and re-run 
```
dpkg run --configure -a
``` again.

---

### Post by mashume on 2011-02-23
OK, so I can run 'sudo dpkg --configure -a' without any problem. it says:

Setting up cltl (1.0.26)
Downloading CLTL from the Internet

and then nothing happens.

I read this about the package from [http://pkgs.org/ubuntu-10.10/ubuntu-multiverse-i386/cltl_1.0.26_all.deb.html](http://pkgs.org/ubuntu-10.10/ubuntu-multiverse-i386/cltl_1.0.26_all.deb.html)

"This package does not contain the actual HTML files, but rather downloads the HTML archive from the Internet and then installs it."

I'm guessing that the html files are not where the package thinks they are, or can not be reached from my workplace (in China). So how do I cancel the installation of CLTL 1.0.26?

I can't complete the installation, and dpkg hangs every time I run it.

again, thanks for reading  :)

---

### Post by Habitual on 2011-02-23
> **mashume said:**
> I'm guessing that the html files are not where the package thinks they are, or can not be reached from my workplace (in China).

That is my conclusion also.

I do not have an answer,sorry.

Someone else will however, just *be patient* and they will jump in.

But see these posts in the meantime:
[http://askubuntu.com/search?q=remove+a+cached+package](http://askubuntu.com/search?q=remove+a+cached+package)

---

### Post by mashume on 2011-02-23
SOLVED

what I did:

1 download the source for the package
2 extract the url for the download target
3 download through a proxy server
4 place file in /root/temp
5 run dpkg --configure -a again
6 all is well

no idea why
but it is resolved

---

### Post by Habitual on 2011-02-23
Proxy will do it everytime, in China. :)

Glad it worked out.

+1 for fixing it yourself. Good Job.

---

