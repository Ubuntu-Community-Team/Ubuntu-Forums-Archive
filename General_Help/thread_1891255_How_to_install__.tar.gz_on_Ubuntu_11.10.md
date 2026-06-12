---
title: "How to install  .tar.gz on Ubuntu 11.10?"
date: 2011-12-05
forum: General Help
---

### Post by thetrashfactory on 2011-12-05
Hi, 

I'm trying to install a programme onto Ubuntu 11.10, the file ends .tar.gz and when I decompress it, I'm getting just one file which apparently isn't software. Any ideas what I'm doing wrong/ how to get this programme running?

I'm getting it from this website: [https://www.cfa.harvard.edu/~akapadia/pinpointwcs/](https://www.cfa.harvard.edu/~akapadia/pinpointwcs/)

I'd really appreciate any help with this!

Thanks in advance!

(apologies for my lack of computer knowledge)

---

### Post by Lars Noodén on 2011-12-05
There's no package there. That may be the program itself.  Looking at it with [file](http://manpages.ubuntu.com/manpages/precise/en/man1/file.1.html) show the following:

```

$ file PinpointWCS 
PinpointWCS: ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), dynamically linked (uses shared libs), for GNU/Linux 2.6.15, not stripped

```

What happens when you try to run it?

```

./PinpointWCS

```

---

### Post by agillator on 2011-12-05
Check the obvious first - how did you 'unzip' it and what was the name of the file that resulted? If you literally unzipped it, then you ended up with a ----.tar file and need to run tar to get the original file back. If you used tar in the first place, then you got the original file or files back.

In that case check the permissions - you need execute permission for the program file. To do this run ls <filename> or simply ls. File permissions will be shown for three groups: owner, group, and others. An r means permission to read, w means permission to write, x means permission to execute. If there are no permissions to execute you need to change them. I don't know your situation, what you want, but the two most common commands to use would be 'sudo chmod 755 <filename>' which would set world read, owner write, world execute permissions or 'sudo chmod 744 <filename>' which would set world read, owner write and execute permissions.

Then './<filename>' should run the program. It is really a simple process, the instructions just sound complicated. To learn more, 'man chmod'.

---

### Post by Lars Noodén on 2011-12-05
I check in a VM and it seems to be the program itself.   If you're looking for a place to put it, it can go in [font=Courier New]/usr/local/bin[/font].

```

sudo mv PinpointWCS /usr/local/bin/.

```

---

