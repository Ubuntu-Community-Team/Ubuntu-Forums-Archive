---
title: "Trying to install fluxbox"
date: 2011-03-16
forum: General Help
---

### Post by ppk on 2011-03-16
I'm trying to install fluxbox 1.3.1 on kubuntu 10.10. I downloaded the tarball and when I try to run ./configure, it gives me this error :
[I]
error : fluxbox requires the x window system libraries and headers[/I]

Where do I get these things?

---

### Post by kn0w-b1nary on 2011-03-16
why don't you install fluxbox through synaptic?

---

### Post by ppk on 2011-03-16
Because I figured I was more likely to get the latest version on the fluxbox website. If it makes no difference though, you're right that there's no reason not to apt-get it.

---

### Post by kn0w-b1nary on 2011-03-16
you're right, repository is 1.1.1 and fluxbox site has 1.3.1

you could try installing it through the repository, then upgrading it with the tarball.

---

### Post by ppk on 2011-03-16
How would I do that? Sorry, total noob here.

EDIT : I just installed it through synaptic. What's the next step?

---

### Post by kn0w-b1nary on 2011-03-16
type: ```
sudo apt-get install fluxbox
```This would install fluxbox and its dependencies.

then install the tarball that you got off the web site. this should upgrade fluxbox AFAIK. usually is ./configure, make, sudo make install.

Just read the file in the tarball called "INSTALL"

Though you could just stick with the one in the repository, and wait.

---

### Post by ankspo71 on 2011-03-16
Hi,
Another Tip: Try using the "apt-get build-dep" command to install all of the required packages needed to build Ubuntu's version of fluxbox from source code. This way you have all (or most, in some cases) of the dev packages and header files installed before you begin building the newer version of fluxbox from source code. 
```
sudo apt-get build-dep fluxbox
```
Now you can go back to using the ./configure command

---

### Post by ppk on 2011-03-16
Thank you ankspo, it worked. I installed it with apt-get install fluxbox, then used build-dep, and then ./configure worked for 1.3.1

Great success :popcorn:

---

### Post by ppk on 2011-03-16
Here's a new problem... Fluxbox doesn't seem to have a network manager of it's own. I suppose I must add kde's network thingy to the fluxbox .startup file?

What is the name of the network thingy I'm looking to autostart?

---

### Post by ppk on 2011-03-16
Fixed. I installed knetworkmanager with apt-get and then added it to the startup file.

---

### Post by kn0w-b1nary on 2011-03-17
Note: You may want to edit your previous posts instead of double posting. Keeps things looking neater.

Glad you got it working!

---

