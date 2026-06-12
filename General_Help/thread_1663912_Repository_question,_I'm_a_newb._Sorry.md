---
title: "Repository question, I'm a newb. Sorry"
date: 2011-01-10
forum: General Help
---

### Post by CP2 on 2011-01-10
So I hear things about software repositories. I looked up some information on what a software repository is, but I'm not quite understanding it. I think it might be because I misunderstood some of what another Ubuntu user said about it. 

So the software repository is a REMOTE site that holds a bunch of approved software right?
So I was under the impression that the repository was something that you have to compile and maintain locally. Is there some truth to this? Do some more advanced user keep their downloaded software in a particular location?  Help me understand more about repositories please.

---

### Post by scottuss on 2011-01-10
A repository is basically like a storage area where a load of programs are kept. The repository is stored on a server somewhere.

The best way to think of it is like the App Store on Android or iPhone or whatever. You can browse the available software, and select what you want to be installed.

Then, the package manager will automatically download the stuff it needs from the repository, and install it exactly where it needs to be. It really is like an App store.

Then, you can start the software from the Applications menu, you don't need to worry where it got installed to or anything like that.

Go to Applications > Ubuntu Software Centre and anything you see in there is stored in a repository.

---

### Post by wojox on 2011-01-10
Repositories are where all the packages are kept after the maintainers have compiled them. You could download just the packages from Synaptic, but it's easier just to update them and install.

---

### Post by CP2 on 2011-01-10
Ok. I see. Someone made me think that a repository was something that they managed locally. So basically i should really be concerned with managing a repository. I just pull from a remote repository then.

---

### Post by Yougo on 2011-01-10
don't apologize for being a newb ;-) thats how we all start out.

what the others said is quite right. note though that just any repository does not necessarily contain 'approved' software.

Ubuntu's standard repositories are well maintained and applications are scrutinized by a whole team of people to make sure there's no bad codes or otherwise malicious things in there.

if you're just starting out in linuxland, riding the ubuntuwagon, the standard repos contain loads of programs to play around/seriously use. these show up in the software center

read all about repositories here:
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by CP2 on 2011-01-10
> **Yougo said:**
> don't apologize for being a newb ;-) thats how we all start out.

what the others said is quite right. note though that just any repository does not necessarily contain 'approved' software.

Ubuntu's standard repositories are well maintained and applications are scrutinized by a whole team of people to make sure there's no bad codes or otherwise malicious things in there.

if you're just starting out in linuxland, riding the ubuntuwagon, the standard repos contain loads of programs to play around/seriously use. these show up in the software center

read all about repositories here:
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Thanks for clearing the repository thing up for me folks. I think i'll be a newb for another year or so. lol.

---

### Post by QLee on 2011-01-10
[QUOTE=CP2]Ok. I see. Someone made me think that a repository was something that they managed locally. So basically i should really be concerned with managing a repository. I just pull from a remote repository then.[/QUOTE]

In the sense of an Ubuntu repository, a repository is a storage area for Ubuntu packages, structured in a specific way so that the package managers can pull the packages necessary for installing pieces of software (we often call programs) with all the necessary dependencies and verify that they are authentic. 
 
Repositories could be local or remote, public (like the standard Ubuntu repositories) or private (like a local company repository for specific software or specific versions).

Someone might be managing a local repository, I for one do, but it is not something that all users need to consider or do. Best bet for most users is to just use official Ubuntu repositories, they have software that can be trusted.

---

