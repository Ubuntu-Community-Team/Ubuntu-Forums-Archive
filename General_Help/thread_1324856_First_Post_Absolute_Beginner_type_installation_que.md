---
title: "First Post: Absolute Beginner type installation questions to follow..."
date: 2009-11-12
forum: General Help
---

### Post by jeff25624 on 2009-11-12
I do apologize for having to do the following, but I recently decided that what the heck, let's try out Ubuntu and see where that takes me! So yesterday I installed Ubuntu Netbook Remix, or I suppose in technical terms the 9.1 release of Karmic on my Acer Aspire One Netbook.

So far, I have to say I am genuinely impressed. After some installation issues, I was finally able to get everything up and running, and I was shocked at how accessible everything was; there is such a nice GUI that quite frankly, I wasn't expecting.

So in my attempts to get the device all tip top, I managed to get the basics taken care of, like Flash. However, trying to install java has provided me with a problem. I searched around on these forums best I could given the amount of threads, attempted to install the Sun/Java 6 plugin package through Synaptics, where I was informed that the package could be not found. I attempted to repair my cache through the terminal, but that was ineffective as well. I eventually just went to the source and installed the plugin through Java's website, but upon installation was told it was an outdated version, and to install the newer version. Well I followed the instructions provided, but could not get very far because I could not figure out what my root password is.

A secondary problem of a less important nature is my attempts to install Skype; theoretically it is installed just fine, but upon trying to load the program, nothing ever comes up. It tells me Skype is loading, and then returns to the normal screen display. 


I'd appreciate any assistance; I am sure these questions is asked hundreds of hundreds of times, but I have been unable to find a workable solution, probably due to my newbie status with working such an OS....

---

### Post by coldReactive on 2009-11-12
Install icedtea for the first issue.

---

### Post by teonghan on 2009-11-12
Dear jeff25624,

First, welcome to Ubuntu! Well, I am not an expert here but here is a few suggestions I have in mind. The root password is the SAME password you key in during the installations, in other word, your login password. So, any administration job will need that password. To install program using Synaptic, it is always better to enable all those extra repositories, i.e: in Synaptic -> Settings -> Repositories -> Other software -> enable the available repositories there. Then press reload. To install Sun Java, just search Sun Java in Synaptic and install the sun-java6-plugin. To install Skype, I get it from medibuntu repository. Follow the guide at [https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu") and install Skype. It works for me.

---

### Post by coldReactive on 2009-11-12
> **teonghan said:**
> Dear jeff25624,

First, welcome to Ubuntu! Well, I am not an expert here but here is a few suggestions I have in mind. The root password is the SAME password you key in during the installations, in other word, your login password.

Enabling root logon through login screen and trying to login to root with your own password results in password being incorrect.

using sudo and gksudo however is another story, but the op clearly stated they lost the root password. The root password can be edited by the first non-root user you created when you first installed the system.

---

### Post by jeff25624 on 2009-11-12
Indeed I thank those who have responded so far; the problem is that your solutions are items that I have already gone through. The Sun Java solution for example gives me a "Hash Sum Mismatch" and says they have failed to fetch the .deb file for the plugin.As for installing IcedTea, I have done that to no avail. I am still informed to install the latest version, which again brings me to the issue of the rootpassword. The Medibuntu fix, I was able to get it implemented, but I was told the Skype package already exists, and thus nothing was done...

I appreciate the assistance of those so far, I am just unfortunately stuck with these particular problems...

---

### Post by bvandon on 2010-05-26
> **coldReactive said:**
> Enabling root logon through login screen and trying to login to root with your own password results in password being incorrect.

using sudo and gksudo however is another story, but the op clearly stated they lost the root password. The root password can be edited by the first non-root user you created when you first installed the system.


here is what i did:
open terminal and enter

sudo passwd -d root   
<--- (when asked for SUDO password enter your admin account password. SUDO and SU are completely different SUDO is SuperUser Do where SU is telling terminal to log in as Super User is Root) this deletes the current root password not your account password

Then enter
sudo passwd -k root
<--- you will be prompted to enter new UNIX password.

now to test it type " su " in terminal and enter your root password your terminal should now read 

root@yourcompname:~#

---

