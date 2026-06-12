---
title: "Firefox 4 stable in repos?"
date: 2011-03-22
forum: General Help
---

### Post by nathan28 on 2011-03-22
Is this in a PPA yet? I see a tarball on the Mozilla site but hate tarball installs if I can do it through a package. I just ran the Update Manager and the Firefox (Namoroka) link in my menu is 3.6.x.

I'm running Minefield right now from the bleeding-edge repos and would prefer to switch to FF4 stable... is there an (easy) way to do that and keep my settings and add-ons?

---

### Post by Frogs Hair on 2011-03-22
Right now you have the choice of using Minefield or the package from the Mozilla website.

---

### Post by cjhabs on 2011-03-22
> **nathan28 said:**
> Is this in a PPA yet? I see a tarball on the Mozilla site but hate tarball installs if I can do it through a package. I just ran the Update Manager and the Firefox (Namoroka) link in my menu is 3.6.x.

I'm running Minefield right now from the bleeding-edge repos and would prefer to switch to FF4 stable... is there an (easy) way to do that and keep my settings and add-ons?

See this thread:
[http://ubuntuforums.org/showthread.php?t=1712247](http://ubuntuforums.org/showthread.php?t=1712247)

---

### Post by nathan28 on 2011-03-22
FF4 ppa:

OMG! Ubuntu:[FF4 for 10.04 and 10.10]("http://www.omgubuntu.co.uk/2011/03/firefox-4-ppa-for-ubuntu-10-04-and-10-10-users/")

> 
    sudo add-apt-repository ppa:mozillateam/firefox-stable
    sudo apt-get update && sudo apt-get upgrade


Probably not going to get to this for a day or three. Not sure if this keeps add-ons in place from Minefield, and not sure if this is the 32-bit like the tarball or will grab the 64-bit if you have that.

---

### Post by Vaphell on 2011-03-22
it replaces default 3.6 with 4.0 and in my case it asked which profile it should use (i had both 3.6 and 4.0 daily)
addon compatibility can be a pain, few addons i got used to with 3.6 don't work in 4.0

---

### Post by pqwoerituytrueiwoq on 2011-03-22
```
sudo add-apt-repository ppa:mozillateam/firefox-stable
```source:
[http://www.webupd8.org/2011/03/install-firefox-4-in-ubuntu-1004-1010.html](http://www.webupd8.org/2011/03/install-firefox-4-in-ubuntu-1004-1010.html)

works for me 64bit

---

### Post by Rodu on 2011-03-23
Hi guys, I hope this is not something too much off topic...

I downloaded Firefox 4 stable from mozilla.org web site and I am running it on Ubuntu 10.04.

Well, everything is fine, I really like it and I think it has been improved a lot.

By the way I noticed that running the data stats visualization, (HTML / Javascript)  tracking the FF4 downloads in real time (see it here: [http://glow.mozilla.org/](http://glow.mozilla.org/))  my CPU works a lot and I can ear my fan cooler noise going up a lot.

In particular the processes that require lots of cpu are Firefox and Xorg.

If I open the same page with Google Chrome 10.0.6 the CPU percentage used by Xorg is very low, around 4 to 6% and Chrome usage is around 30%.

Anyone experiencing the same thing?
Can be this determined by video drivers/acceleration?

---

### Post by pqwoerituytrueiwoq on 2011-03-23
> **Rodu said:**
> Hi guys, I hope this is not something too much off topic...

I downloaded Firefox 4 stable from mozilla.org web site and I am running it on Ubuntu 10.04.

Well, everything is fine, I really like it and I think it has been improved a lot.

By the way I noticed that running the data stats visualization, (HTML / Javascript)  tracking the FF4 downloads in real time (see it here: [http://glow.mozilla.org/](http://glow.mozilla.org/))  my CPU works a lot and I can ear my fan cooler noise going up a lot.

In particular the processes that require lots of cpu are Firefox and Xorg.

If I open the same page with Google Chrome 10.0.6 the CPU percentage used by Xorg is very low, around 4 to 6% and Chrome usage is around 30%.

Anyone experiencing the same thing?
Can be this determined by video drivers/acceleration?
chrome is probably using your GPU where firefox is not 
my cpu gives me more fps than my gpu here

---

### Post by Rodu on 2011-03-23
I think you are right pqwoerituytrueiwoq,

actually I am now running the visualisation on the same machine, but booting mac osx, using firefox 4 and the performances are perfect. CPU usage 20%, same machine! :)

Then what's wrong with the ubuntu video driver? Is it something we have to take as it is or it could be solved?

Thanks.

---

### Post by aeronutt on 2011-03-23
> **Vaphell said:**
> it replaces default 3.6 with 4.0 and in my case it asked which profile it should use (i had both 3.6 and 4.0 daily)
addon compatibility can be a pain, few addons i got used to with 3.6 don't work in 4.0

+1, was surprised that adblock plus didn't work in the 4.0 stable release for example. (Even though it worked in the rc release???)

---

