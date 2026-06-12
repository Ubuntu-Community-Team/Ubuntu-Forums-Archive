---
title: "Want to remove Gimp 2.6 &amp; install 2.8, but....."
date: 2012-08-16
forum: General Help
---

### Post by Buntu Bunny on 2012-08-16
I installed Gimp 2.6 via the Ubuntu Software Center (from one of the Gnome desktops). I'd like to install Gimp 2.8, but thought I should remove 2.6 1st. Since I now run Xubuntu alongside, I attempted to remove Gimp with the Software Center from Xfce. However, when I clicked "remove", a box popped up telling me, 

"To remove GIMP Image Editor, these items must be removed as well: The gnome desktop enfironment, with extra components."

Does that mean what I think it means? If I try to removed Gimp 2.6 via the Software Center it will remove my Gnome desktops as well???

---

### Post by rotave on 2012-08-16
you don't need to uninstall GIMP 2.6 to install 2.8. If you're installing GIMP 2.8 from a PPA then it will just update all packages to the latest version (i.e GIMP 2.6 to GIMP 2.8)

---

### Post by Buntu Bunny on 2012-08-16
> **rotave said:**
> you don't need to uninstall GIMP 2.6 to install 2.8. If you're installing GIMP 2.8 from a PPA then it will just update all packages to the latest version (i.e GIMP 2.6 to GIMP 2.8)

That's good to hear. Gave it a try from nilarimogard/webupd8, but I can only find Gimp 2.6.12 on my 'puter. 

Do I need a different ppa?

---

### Post by GreatDanton on 2012-08-16
As far as I know in 12.04 you have to manually add PPA. Gimp 2.8 is not in the software center. To install Gimp2.8 I am pretty sure this link will help you: [http://www.noobslab.com/2012/04/install-gimp-28-on-ubuntu-1204-precise.html](http://www.noobslab.com/2012/04/install-gimp-28-on-ubuntu-1204-precise.html)

Regards.

---

### Post by 23dornot23d on 2012-08-16
Type this in a terminal ......

lsb_release -a

output will be similar to below ..... 
> 
keith@keith-Aspire-7730ZG:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu quantal (development branch)
Release:        12.10
Codename:       quantal
keith@keith-Aspire-7730ZG:~$


It will show which version of Ubuntu you are currently running ...... * ( post back the result ) just to confirm which version of Ubuntu you are running at this present time.

---

### Post by Buntu Bunny on 2012-08-16
> **GreatDanton said:**
> As far as I know in 12.04 you have to manually add PPA. Gimp 2.8 is not in the software center.

That's correct, it's not in the software center. I attempted to update with this code:

```

sudo add-apt-repository ppa:nilarimogard/webupd8
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install gimp-plugin-registry
```

Obviously not the most uptodate version!

> I am pretty sure this link will help you: [http://www.noobslab.com/2012/04/install-gimp-28-on-ubuntu-1204-precise.html](http://www.noobslab.com/2012/04/install-gimp-28-on-ubuntu-1204-precise.html)

Your link shows a different PPA so I'll give that a try.

---

### Post by Buntu Bunny on 2012-08-16
Well, the first command crashed in terminal. This is the error message:

> ~$ sudo add-apt-repository ppa:otto-kesselgulasch/gimp
You are about to add the following PPA to your system:
 CAUTION!

This PPA could break your installed OS if you use Ubuntu series < Precise. 
There are dependency issues for Oneiric Ocelot (11.10). Only use it if you 
know what you do!

There are no known issues in Precise Pangolin (12.04) and Linux Mint 13 (Maya).

I need a minute or two to process this.

---

### Post by Buntu Bunny on 2012-08-16
> **23dornot23d said:**
> Type this in a terminal ......

lsb_release -a



> leigh@leigh-CM1740:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.1 LTS
Release:	12.04
Codename:	precise


.

---

### Post by GreatDanton on 2012-08-16
Where is the error message? The thing you posted into upper post is not an error message, is just a message to remind you that adding unknown ppa can be harmful. However that ppa is working 100%. Just follow the instructions on that link I gave you and it will be okay.

Regards.

---

### Post by Buntu Bunny on 2012-08-16
> **GreatDanton said:**
> Where is the error message?

The error message was actually a crash report in my notification area, telling me an application had crashed. Since I only had terminal and chrome open (and chrome was still working just fine) I figured it had something to do with terminal. :???:  Apologies if I got the terms wrong. 

>  The thing you posted into upper post is not an error message, is just a message to remind you that adding unknown ppa can be harmful. However that ppa is working 100%. Just follow the instructions on that link I gave you and it will be okay.

It's the first time I've ever received that warning when installing something via terminal. It took me off guard. I see it's telling me it's okay for 12.04, which I have. Just ..... whew.

---

### Post by ads52 on 2012-08-16
You may be disappointed to find that while differences between versions are obvious it may not change your workflow that much:

GIMP 2.8 Release Notes
[http://www.gimp.org/release-notes/gimp-2.8.html](http://www.gimp.org/release-notes/gimp-2.8.html)

I am a big fan of the single window though :).

---

### Post by SeijiSensei on 2012-08-16
I believe the 2.8 version only works with 12.04, so that message is designed to warn people using earlier Ubuntu versions not to try and install 2.8 from that repository.

---

### Post by Buntu Bunny on 2012-08-19
I forgot to come back and mark this thread solved. 

Gimp updated from 2.6 to 2.8 without a hitch, as you all predicted. Noted a few things I needed to get used to but I love the single window feature. 

Everyone's help was much appreciated!

---

