---
title: "Where should install files be located?"
date: 2011-02-27
forum: General Help
---

### Post by nikkokick on 2011-02-27
Hi.

So new to ubuntu as I am, I've got a question.

I've tried multiple times to install files I've downloaded via the Terminal, but I do get the same error very often (if not always, cant recall if I ever managed to install something thru Terminal).

E: Unable to locate package xxxx
E: Couldn't find any package by regex 'xxxxx'

Example:
E: Unable to locate package install-swiftfox.sh
E: Couldn't find any package by regex 'install-swiftfox.sh'

I have downloaded the file and marked it as executable.


Do I have to store my installationfiles on a special place or do the terminal search thru the whole harddrive?


Sorry if my questions are very noobish or stupid, but I'm here to learn!

thanks in advance

---

### Post by oldos2er on 2011-02-27
A shell script (foo.sh) needs to be run in a terminal ```
./install-swiftfox.sh
``` You need to use "cd" if necessary to change directory to where the script is. Also, you may need to run the script with "sudo" if it needs write access to a directory other than your home directory.

Hope this gets you started.

Also see [https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by nikkokick on 2011-02-27
Thank you but that was just an example of what I'm asking.

What I would like to know is : Are all packades that you try to install from terminal already on your computer or do terminal find them on the internet? If they are on your computer, do they have to be on a particular place so terminal can find them?

Also, could you write a packade I can try to install? Just for the sake of seeing if my terminal works when it comes to install using: "sudo apt-get install X"


Thanks in advance

---

### Post by oldos2er on 2011-02-28
APT saves installed packages to /var/cache/apt/archives; these are downloaded from the repositories, servers available via the internet. It doesn't matter what package manager front-end you use, Synaptic, Software Center, apt-get or aptitude; they all look to the same repos and the same cache.

Use **apt-cache search <program>** to find a package you want to download.

---

