---
title: "Ubuntu 11.04: update error (introducing Ubuntu to a friend)"
date: 2011-07-25
forum: General Help
---

### Post by astrobob.tk on 2011-07-25
Hello,

Last week I installed Ubuntu 11.04 on a friend's laptop (Toshiba Satellite) in dual boot with Win Vista or 7.

Anyways, the thing is that I made the installation in a coffee shop & tried to update the repository (apt-get update) using the shop's wifi connection. Doing so lead to the following error:

```
W: Failed to fetch gzip:/var/lib/apt/lists/partial/lb.archive.ubuntu.com_ubuntu_dists_natty_universe_binary-i386_Packages  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

I promised the guy to check it out & get back to him.

Note: After this error, synaptic notifies of the same error when opened & then simply closes. He (the guy) also told me later after a few days that when he open Ubuntu Software Center, he sees no packages to install.

Any help is appreciated.

Another note: I do not have his laptop at the time being, but your responsible & directed responses would be of great help when I meet him again or in case I direct him what to do by email.
I was reluctant about letting him solve the problem on his own as he doesn't seem to know much about computing.

P.S.: I made the installation from a disc that I've used as a live disc only. This is the first time I use it to install on an HDD. Besides this everything went great.

thanks in advance

---

### Post by 3602 on 2011-07-25
*Might* be possible that the shop's open WiFi is messing with something.
First, in his home,
```
sudo apt-get update
```
If the error persists, tell him to try another server.
Open Update Manager. In Settings, choose the Ubuntu Software tab. Now, from Download From, choose another server, such as the Main Server or a server from another country.
The problem *shouldn't* persist.

---

### Post by XubuRoxMySox on 2011-07-25
Sometimes the repository is just busy, and a retry a few minutes later is all that is needed.

I've been kinda disappointed with the Software Center though. Synaptic, however, is tried-and-true, very reliable. I finally reached a point where I just use Synaptic, and the last time I did I used it to remove the Ubuntu Software Center while I was there and had it open anyway.

-Robin

---

### Post by jamesisin on 2011-07-25
I'm guessing it was just a communication error stemming from insufficient bandwidth at the cafe.  I sometimes see this error when I'm torrenting everything on the Internet at once.

---

### Post by astrobob.tk on 2011-07-25
> **3602 said:**
> *Might* be possible that the shop's open WiFi is messing with something.
First, in his home,
```
sudo apt-get update
```
If the error persists, tell him to try another server.
Open Update Manager. In Settings, choose the Ubuntu Software tab. Now, from Download From, choose another server, such as the Main Server or a server from another country.
The problem *shouldn't* persist.

Thanks for the advice; i guess the main server is the issue as I believe the wifi we were using shoed a US IP when i was doing a personal netowkr scan.

Will get back on what happens.

> **jamesisin said:**
> I'm guessing it was just a communication error stemming from insufficient bandwidth at the cafe.  I sometimes see this error when I'm torrenting everything on the Internet at once.

Indeed, as you say; personally i only tried the software center once or twice but I always use synaptic if not the terminal (in my case i love guake) :D

The thing is that this guy is new & although I did tell him about synaptic, I suggested that he use the software center instead as a start. I think it's "graphically" easier to use for beginners.

thanks

---

### Post by wildmanne39 on 2011-07-26
Hi, you will need to remove the partial list before it will work again.
```
sudo rm /var/lib/apt/lists/partial/*
```
Please use this command exactly as it is written, and do not use with other files or you could wipe out your system. 
```
sudo apt-get update && sudo apt-get upgrade
```
That should fix it if not post the new errors all of them.
Thank you

---

