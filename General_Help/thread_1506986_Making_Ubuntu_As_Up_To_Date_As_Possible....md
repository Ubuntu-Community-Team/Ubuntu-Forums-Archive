---
title: "Making Ubuntu As Up To Date As Possible..."
date: 2010-06-11
forum: General Help
---

### Post by MrWizard101 on 2010-06-11
Having been back and forth between distros ( rolling and static ) I've ended up coming right back to Ubuntu 10.04 LTS.

The main thing that brought me back is, everything is working with it, as oppose to 1 Rolling Release I was using ( Sabayon ) wouldn't recognize my printer any longer.

Essentially, the point of this post is to ask the following:

What is the best way to make Ubuntu, essentially a type of rolling release?

I know you would add PPA's and enable the backports ( in the update manager ), is there anything I am missing? 

When enabling the Backports, is there anything else to change or remove? ( Example, changing the Long Term Updates only to normal and unchecking everything except leaving backport updates only? )


The perfect solution would be just to install once and just update through the manager of course but I know right now it's not possible with Ubuntu, hence, my question(s) 


Thanks...

---

### Post by PC_load_letter on 2010-06-11
AFAIK, Ubuntu is not a rolling release. If you want to keep all the software you use up to date, I'm afraid this means you'll have to do this yourself by: Adding the software PPA (if any exists), install the deb file (if available), or by downloading the source and compile it. But then you'll have to deal with any problems that could be a result of this update process. Don't get any ideas like adding Lucid's repos to Karmic's. It's an invitation to chaos and is highly discouraged. 

No one I know does this, and I don't see the point in rolling releases "IF" by having that, one would loose the stability of the system. 

All that I do, is to make sure the update manager runs regularly, and I always install the security and recommended updates, but nothing else, i.e. I do not install the experimental updates on any machine that I rely on to run problem-free. 

Hope that helps.

---

### Post by MrWizard101 on 2010-06-11
> **PC_load_letter said:**
> AFAIK, Ubuntu is not a rolling release. If you want to keep all the software you use up to date, I'm afraid this means you'll have to do this yourself by: Adding the software PPA (if any exists), install the deb file (if available), or by downloading the source and compile it. But then you'll have to deal with any problems that could be a result of this update process. Don't get any ideas like adding Lucid's repos to Karmic's. It's an invitation to chaos and is highly discouraged. 

No one I know does this, and I don't see the point in rolling releases "IF" by having that, one would loose the stability of the system. 

All that I do, is to make sure the update manager runs regularly, and I always install the security and recommended updates, but nothing else, i.e. I do not install the experimental updates on any machine that I rely on to run problem-free. 

Hope that helps.

I don't know if you read what I posted clearly, I said that I knew it wasn't a rolling release but what is the best way to keep the applications "updated" is basically what I asked ):P


Adding Lucid to Karmic would be a problem of course because the Kernels and basic system are different, but the applications are the same, just updated ( this is the point )

Average users don't care for the Kernels and things they don't see, they only care to keep the applications running on their system up to date.

I know about the PPA and the Backports but wanted to know if there was anything else that could be done or if by choosing Backports to be enabled, should the other updating methods be unchecked and the Long Term Releases be changed to Normal or what...
;)

Thanks for the reply :D

---

### Post by PC_load_letter on 2010-06-11
I knew that you wanted to keep your apps updated, but which apps? All the apps? And at what price? You'll have to ask yourself is it worth it to spend all this time compiling and/or dealing w/ unstability problems? I keep GIMP updated thru a PPA, and many of the scripts that were working in 2.6, stopped working or give me an error message in the latest 2.6.7 on Karmic. I'm sure there are solutions and workarounds, but I don't have the time to keep track.

Aside from the usual settings of the update manager, and as I mentioned in my reply, the only ways I know to update an application to the latest release are:
1- Adding the PPA repo, if such one exists. IN Karmic & Lucid you do this by ```
sudo add-apt-repository ...
``` where you replace the ... by the PPA name you get from the launchpad web page.  
For Jaunty and prior versions you'll have to manually add the PPA entry to the /etc/apt/sources.list then you'll have to import the encryption keys. 

2- Install from a deb file, that you download from the devs web page, if such one is available, or use 'alien' to transform an rpm package to a deb package. 

3- The last resort is to compile from source, which in most cases is fine, but not in others. It took me over 2.5 hours to compile SAGE ([www.sagemath.org](www.sagemath.org)) on my Thinkpad T43. 

So, it's your choice really, what "I" do is download and install the latest security and important updates from Update Manager, and have a few PPAs for the applications that I like to maintain at the latest version, e.g. Wine.

---

### Post by snowpine on 2010-06-11
Ubuntu is not rolling release. The best way to keep your applications current is to regularly upgrade to the new releases every 6 months. Trying to make Ubuntu something it is not might make your system less stable and certainly is unsupported by Canonical.

Have you considered Debian Sid? It is the rolling release distro on which Ubuntu is based.

---

### Post by MrWizard101 on 2010-06-11
> **snowpine said:**
> Ubuntu is not rolling release. The best way to keep your applications current is to regularly upgrade to the new releases every 6 months. Trying to make Ubuntu something it is not might make your system less stable and certainly is unsupported by Canonical.

Have you considered Debian Sid? It is the rolling release distro on which Ubuntu is based.


lol I know it's not a rolling release, I said that in my previous posts. I was asking, aside from adding PPAs and changing the updating method, was there another way or anything else to do to keep it updated?

Seems that my method was right so I appreciate the reply.

I tried to install Debian but it wouldn't boot up with the cd for some wierd reason, eh.

But I thank for the reply :)

---

### Post by bodhi.zazen on 2010-06-11
The short answer is no , Ubuntu is not a rolling release, so you can not make it into one.

If you like you can update to the development release as soon as possible, that would be 10.10

```
update-manager -d
```BUT be warned, that means some instability.

What is it you want from a "rolling release" ?

Up to date packages ? For what ?

If you want bleeding edge you need to go to the source. For example Fedora is teh bleeding edge of some packages, so go to fedora.

For the absolute bleeding edge you need to go to source code and download the latest svn / git source and re-compile it. If you are going to that extreme, just go for linux from scratch.

If you can tell us what you want from a "rolling release" we can tell you how to do it.

If the goal is not have to re-install, well, I have an install that has gone from 7.10 -> 8.04 -> 8.10 -> 9.04 -> all the way to 10.04 without ever having to reinstall and no more hassle then Arch. You just do a major update every 6 months or so.

So as I have ranted on and on , it depends on what you want exactly.

Otherwise it seems you all are arguing about semantics, and I do not think you disagree with the semantics either, :lolflag:

---

### Post by MrWizard101 on 2010-06-12
lol I said in my initial post and some of the following ones that "**I know** Ubuntu isn't a rolling release" 

Then I asked on ways to just** "Keep the system up to date, *Applications wise*"**

Then in my 3rd post I said "Average people don't care for what they don't see, so what I would care to know is for application updating, kernels and the other excess are not important for the average"

I brought this up mostly for other people than myself. I've been through the following Rolling Releases:
PCLINUXOS ( problem with the audio )
Sabayon ( printer wasn't being recognized )
Sidux ( had trouble booting on some machines )


Personally, I'm not crazy about KDE, I mention this because the base system for these Rolling releases tend to be KDE based ( I don't want derivatives of a base, I want the base )

Which lead me to go and try Debian Unstable but after reading about Sidux and Debian Sid, Sidux made more sense and is more stable overall ( but Sidux doesn't come with Gnome, hence why I didn't try it.  Although I did try to boot the USB then a CD later and both failed on one machine )

Was going to get crazy and go to Arch but I told myself to slow it down and stick with what just worked from the beginning, Hence, why tonight I put Ubuntu 10.04 LTS on a friends machine and on one of my personal ones.

I added in some info there going through my journey, maybe I should have done that so you guys can get the idea that "I've been around the distros before lol"

---

### Post by bodhi.zazen on 2010-06-12
To update your system use update-manager, it should be automatic.

You can configure automatic updates via synaptic if you wish.

You may use the command line :

```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by Siljrath on 2010-06-14
> **bodhi.zazen said:**
> To update your system use update-manager, it should be automatic.

You can configure automatic updates via synaptic if you wish.

You may use the command line :

```
sudo apt-get update && sudo apt-get dist-upgrade
```

... oh, so (just to confirm i understand this right):```
sudo apt-get update && sudo apt-get dist-upgrade
```will update everything we need, so we're effectively running 10.04, even if we run that from what was once 9.04 when fresh installed?

* tries it out after the installation of upgrade manager finishes *

my issue was mainly about having to fiddle around with updating my sources list.  when i do it manually, it nearly always gets messy. mixing locations for different versions... which i am repeatedly told is risking catastrophic doom.

* tries sudo apt-get update && sudo apt-get dist-upgrade *

---

### Post by bodhi.zazen on 2010-06-14
> **Siljrath said:**
> ... oh, so (just to confirm i understand this right):```
sudo apt-get update && sudo apt-get dist-upgrade
```will update everything we need, so we're effectively running 10.04, even if we run that from what was once 9.04 when fresh installed?

* tries it out after the installation of upgrade manager finishes *

my issue was mainly about having to fiddle around with updating my sources list.  when i do it manually, it nearly always gets messy. mixing locations for different versions... which i am repeatedly told is risking catastrophic doom.

* tries sudo apt-get update && sudo apt-get dist-upgrade *

If you are updating from Ubuntu 9.10 to 10.40 (or any version of Ubuntu) the preferred method is to perform the update via update manager.

[http://www.ubuntu.com/desktop/get-ubuntu/upgrade](http://www.ubuntu.com/desktop/get-ubuntu/upgrade)

Manually editing your /etc/apt/sources.list and running apt-get is NOT advised (as it is messy).

Update-manager will perform the necessary system edits / modifications, including /etc/apt/sources.list automagically.

If you are already running Ubuntu 10.04, all you need to do is use update manager or from the command line

```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

