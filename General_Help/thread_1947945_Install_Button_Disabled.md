---
title: "Install Button Disabled"
date: 2012-03-27
forum: General Help
---

### Post by Eleness on 2012-03-27
I spent all day trying to install build-essential, and now considering seriouslly come back to windows, because if it takes a whole day of searches and tries to install the most basic thing to be installed, I am scared of what comes latter.

Well, I have no access to internet from the PC where ubuntu is installed. Apparently, ubuntu is not made for this situation. After much time, I've found build-essential package for download (a .deb archive). When I open it with Software Center, is says "dependency is not satisfiable", and I have to find another package with some version of g++. I did that, and again, "dependency is not satisfiable", and I had to find another version and so on.

I ended up with "gcc-4.4-base_4.4.4-14ubuntu5.1". Aparently, this is the most basic thing I need on this chain. Opening it, there is no error text, but the install button is disabled.

If I search for this problem on internet, all that appears are synaptic, synaptic... but my ubuntu version (11.10) doesn't have synaptics. There is no single page saying if there is another way to install a deb file without software center or why the button is disabled.

---

### Post by raja.genupula on 2012-03-27
hi you can install .deb files as
```
sudo dpkg -i filename.deb
```

for more information on installing software [https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

---

### Post by Mark Phelps on 2012-03-27
> **Eleness said:**
> I spent all day trying to install build-essential, and now considering seriouslly come back to windows, because if it takes a whole day of searches and tries to install the most basic thing to be installed, I am scared of what comes latter.

The preferred way of installing apps in Ubuntu is using the Software Center.  It is able to figure out all the package dependencies and handle them for you.

After that, the next way is using Synaptic Package Manager and selecting .deb files.

The HARDEST way to install anything in Ubuntu is from source -- which is the path you have probably chosen if you now have to mess around with finding individual packages.

You've have made this hard on yourself -- this is not something that Ubuntu has done to you.

---

### Post by jerome1232 on 2012-03-27
This should help

[http://keryxproject.org/](http://keryxproject.org/)

---

### Post by Eleness on 2012-03-27
Thank you for the replies! I had already tried dpkg, but it gives a dependency problem even with the base gcc file, which was the last on the download list of the site I was using.

I *have* to use the hardest way because don't have internet acess yet.

Keryx has also dependency problems when installing via dpkg... The name "dependency nightmare" is justified! Guess I will have to install an internet so I can properly use ubuntu on that pc...

---

### Post by jerome1232 on 2012-03-27
you install keyrx on the machine with internet access

---

### Post by grahammechanical on 2012-03-27
Perhaps posts 3 and 4 on this forum link will help you.

[http://ubuntuforums.org/showthread.php?t=251602]("http://ubuntuforums.org/showthread.php?t=251602")

I do not think that you are trying to install the most basic thing.

As an experienced Windows user perhaps you could explain to me how I can update Windows 7 on a PC that does not have an internet connection. I need to get the updates over the internet by using another PC. Is this possible?

By the way, Synaptic Package Manager also needs a Internet connection. 

This is why Linux distributions come with all kinds of software on the install CD/DVDs and are installed as standard.

Regards.

---

### Post by Eleness on 2012-03-28
What pissed me off is that in Windows, if I have no internet and want to install something, I simply download the program from another computer, pass to mine with a cd or pen drive and open the setup. Here, I spent hours to install a basic package. Searching, I saw many other people with the same problem, but all the solutions I saw were, effectively. to other versions of ubuntu... It's a little scary;

But now I am connected to internet. Being able to use apt-get and things like that the ubuntu advantages are wonderful.

---

### Post by jerome1232 on 2012-03-28
Then you weren't paying attention, the solution I gave you works on Windows computers.

---

