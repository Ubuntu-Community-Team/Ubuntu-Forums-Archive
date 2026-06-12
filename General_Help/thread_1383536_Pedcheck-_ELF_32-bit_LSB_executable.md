---
title: "Pedcheck- ELF 32-bit LSB executable"
date: 2010-01-17
forum: General Help
---

### Post by LFMZZ on 2010-01-17
Hello!
I am an absolute noob to Linux and Ubuntu. I started following some of the Linux Introduction guide: [http://tille.garrels.be/training/tldp/index.html](http://tille.garrels.be/training/tldp/index.html).
Once I felt more comfortable using the terminal, I decided to try and install the programs I had used on a course, these are mostly programs without a GUI.
So far I have found several problems, but I have been able to find answers using info, man, --help and Google.
I am stuck trying to install a program called pedcheck. The file downloaded and corresponding info is:
lfm@Bunnyfluff:~/Desktop/Genetics/Pedcheck$ file pedcheck_linux_intel 
pedcheck_linux_intel: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.2.5, not stripped

I am using Ubuntu 9.10 karmic
Kernel - Linux Bunnyfluff 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 i686 GNU/Linux

I can't run the file. I read in the forums about users with similar problems and tried getting ia32-libs, but I get the message that its not found (I am not even sure if this applies to my Ubuntu install!). I went to my sources.list and tried enabling all the repositories, as indicated here ([https://help.ubuntu.com/community/Repositories/CommandLine):]("https://help.ubuntu.com/community/Repositories/CommandLine%29:")

[LIST]
[*]*First, save your original sources.list file. **sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup*
[*]*Now make the changes to uncomment all repositories listed in the sources.list file. **sudo sed -i -e "s/# deb/deb/g" /etc/apt/sources.list*
[*]*Make apt aware of the new software repositories by issuing the following command: **sudo apt-get update*
[*]***Done!** The new software repositories should now be available for use.*
[/LIST]
It did not work (I have now replaced the original sources.list file).

So I am running out of ideas, and since I am mostly just repeating motions with limited understanding of what I am doing, I think I better ask for some help.

Anyone?

Cheers,

LFMZZ

Edit: Pedcheck has no installation instructions!

---

