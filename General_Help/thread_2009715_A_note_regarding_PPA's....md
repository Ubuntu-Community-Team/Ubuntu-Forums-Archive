---
title: "A note regarding PPA's..."
date: 2012-06-24
forum: General Help
---

### Post by sgage on 2012-06-24
For New Users of Ubuntu...

You may be tempted to go overboard trying out all sorts of things from various PPA's. But if you install something from a PPA, and decide you don't want it any more, you usually can't simply remove package X and call it day, because a lot of times, installing something from a PPA brings in a whole lot of other upgrades as dependencies.

For example, a lot of people seem to like to try out Rico's Gnome Shell PPA, so they add ppa:ricotz/testing to their repos and install gnome-shell...

But when you installed Gnome Shell from Rico's PPA, you will notice that the version numbers on the Gnome-ish stuff are all 3.5.2...  This is the current in-development version of Gnome (it will become Gnome 3.6 eventually), so basically, to install Rico's GS, you are pulling in a whole new Gnome 3.5.2 stack as dependencies.

You can't then just uninstall Gnome Shell and start over - much of that other stuff would still be installed, ready to create unresolvable dependency conflicts. That's why ppa-purge is the way to go - it will downlevel every package that you installed from a given ppa back to the stock versions, while taking care of all the dependencies and such.

So you've decided you no longer want the development version of GS and want to get back to the official stock version: sudo ppa-purge ppa:ricotz/testing.  Easy peasy! Simple pimple!

In Synaptic, most all of that stuff should show up in "auto-removable", and you could remove it from there. But ppa-purge is really the way to go if you intend to fiddle around with ppa's in future. It's saved the day for me many times...

Please, think about what your're doing with PPA's, and if you want to roll back something you installed from a PPA, use ppa-purge - available at a repo near you (it's in the stock Ubuntu repos).

[Edited to add:I have also noticed people using PPA's to install things that are already present in the official Ubuntu repos, usually based on some outdated web reference or the other. Check the Ubuntu repos first - you'll be amazed at how comprehensive they are.]

---

### Post by jmfal on 2012-06-24
Do I get a discount for buying in quantity??

Good app.
Eliminates the hassle of trying to do it manually.

---

### Post by bogan on 2012-06-25
Hi!, **Sgag**e,

Thanks for your informative Post.

But, - please excuse my ignorance -, you Posted:>  Check the Ubuntu repos first - you'll be amazed at how comprehensive they are.]How do I do that?

I enter a ppa with:```
sudo apt-add-repository ppa:xyz/abc/testing 
sudo apt-get update 
```Then what do I do,? to check what is available, before I use: ```
sudo apt-get install <newprogpackagename> 
```For example: There are several versions of nvidia-current available from various ppa's, but nothing obvious, until installed, to tell which version will be installed with: ```
sudo apt-get install nvidia-current
```No doubt it is obvious when you know how, but I don't, Please help.

Chao!, and Thanks, **bogan.**

---

### Post by Dave_L on 2012-06-25
> **sgage said:**
> ppa-purge is the way to go

Thanks for the tip. I didn't know about that package.

---

### Post by markbl on 2012-06-25
> **Dave_L said:**
> Thanks for the tip. I didn't know about that package.
Be careful, ppa-purge does not always work reliably. I once ran it without paying attention and it ended up causing all X related software to be uninstalled. I was left with a server install, no X/xorg, no login DM, no Unity or gnome-shell, no graphics programs left at all.

---

### Post by vasa1 on 2012-06-26
> **sgage said:**
> For **New Users of Ubuntu** ...

You may be tempted to go overboard trying out all sorts of things from various PPA's. ...
Very good post. Really, one can't be too careful installing stuff from outside the Ubuntu Software Center.

---

### Post by sgage on 2012-06-26
> **bogan said:**
> Hi!, **Sgag**e,

Thanks for your informative Post.

But, - please excuse my ignorance -, you Posted:How do I do that?

I enter a ppa with:```
sudo apt-add-repository ppa:xyz/abc/testing 
sudo apt-get update 
```Then what do I do,? to check what is available, before I use: ```
sudo apt-get install <newprogpackagename> 
```For example: There are several versions of nvidia-current available from various ppa's, but nothing obvious, until installed, to tell which version will be installed with: ```
sudo apt-get install nvidia-current
```No doubt it is obvious when you know how, but I don't, Please help.

Chao!, and Thanks, **bogan.**

I find the easiest way is the use Synaptic. Its search capability is pretty good, and it tells you exactly what's going on as you apply an installation or removal.

It is no longer included by default in Ubuntu, so:

sudo apt-get synaptic

is the first thing I do after a fresh install.

---

### Post by bogan on 2012-06-26
Hi!, **sgage**,

You Posted:>  I find the easiest way is the use Synaptic. Its search capability is  pretty good, and it tells you exactly what's going on as you apply an  installation or removal.Thanks for the response, but I find Synaptic one of the most opaque and confusing pieces of software I have encountered, in what is a very competitive field.

For example, in the context of my question of how to find out what is available from a ppa, there is an 'Origin' option, but it appears to do precisely nothing.

It occurred to me, shortly after I Posted my query, that the ppa details are themselves an 'http' address, and that if I copy/pasted them into a Firefox address box, I should be able to access the ppa as a site and find out what was offered. 

But it did not work, none of the variations I tried gave me anything at all.

Can you, or anyone, suggest how to find out what a ppa provides, especially the version numbers of what will be downloaded and installed by 'apt-get'.

Chao!, **bogan.**

---

### Post by sgage on 2012-06-26
> **bogan said:**
> Hi!, **sgage**,

You Posted:Thanks for the response, but I find Synaptic one of the most opaque and confusing pieces of software I have encountered, in what is a very competitive field.

For example, in the context of my question of how to find out what is available from a ppa, there is an 'Origin' option, but it appears to do precisely nothing.

It occurred to me, shortly after I Posted my query, that the ppa details are themselves an 'http' address, and that if I copy/pasted them into a Firefox address box, I should be able to access the ppa as a site and find out what was offered. 

But it did not work, none of the variations I tried gave me anything at all.

Can you, or anyone, suggest how to find out what a ppa provides, especially the version numbers of what will be downloaded and installed by 'apt-get'.

Chao!, **bogan.**

I don't know what you're looking at, but When I have a PPA installed, Synaptic shows me, under 'Origin', exactly what it provides. 

The idea of PPA's is not that you go to a website and download stuff - the point is that it is a repo that gets integrated into the apt system so that dependencies are resolved, etc.

Do you have some other filter operative, or something in the search box? The "Origin" filter has always worked perfectly for me in many, many years of using Synaptic.

---

### Post by josephmills on 2012-06-26
```
apt-cache policy <name of package>
```
```
apt-cache dump policy <name of package>
```
```
apt-cache show <name of package>
```

```
apt-cache stats <name of package>
```

```
dpkg-query -l | grep <name of package>
```

There are more. But I hope that this helps for now.

---

### Post by bogan on 2012-06-27
Hi!, **josephmills**,

Thanks for your Post about 'apt-cache' options, I presume it was directed towards my query about how to find out what is available from a 'ppa'.

I was aware of those options from 'man apt-cache', but I cannot see the relevance.

What I was after was how to know what 'ppa' would provide a package that I was searching for, or what packages - especially version numbers - a specific 'ppa' would provide. Not details of what packages were already available from the cache.

@**sgage**,  What I am looking at is the Synaptic display, with "nvidia"in the 'Quick Filter' box, the 'nvidia-settings' entry highlighted, and  I have clicked on 'Origin'. The result is the lefthand sub-window shows a list of all the 'ppa's in my 'sources' list, but none of them are highlighted, so what...... ?????

Thanks for your response. I can only repeat that I find Synaptic obscure and impenetrable.

For instance I am using nvidia 295.53 and 295.59 but though Synaptic lists nvidia-settings 295.53, neither of the drivers are listed, and the nvidia-current listed is the notorious bugged version, 295.40; which apt-get cache policy also lists as 'Candidate'.

I presume they are not listed because they were not installed with dpkg or apt-get, but that is only a guess.

I would like to know -[Edit: -*** how to find out ***-] - whether either 295.53 or 295.59 versions are available from the 'ppa's, and if so , how to get them installed. I am not prepared to find out by using apt-get install, without knowing which version will be supplied, from previous disastrous experiences of the bugged version.

Chao!, **bogan.**

---

### Post by markbl on 2012-06-27
> **bogan said:**
> 
For instance I am using nvidia 295.53 and 295.59 but though Synaptic lists nvidia-settings 295.53, neither of the drivers are listed,
How can you be "using" two different versions of the nvidia driver?

All the package managers (synaptic, apt-get, aptitude, software center, etc) use the apt packages database. If you install random files/scripts outside of the package system (e.g. by running a downloaded nvidia script) then how do you expect the package managers to know about this?

Don't stray outside the package system, especially if you are inexperienced. If you really want/need bleeding edge stuff, then perhaps add a ppa. E.g. for very latest nvidia driver add xorg-edgers ppa then update. At least then you will see all the correct installed and other versions in synaptic.

To check the version first before you install them then just check synaptic after the update but before doing the install. Remove/disable the ppa if you don't like the version. Of just go to the ppa launchpad site and check the versions directly before you do anything (filter by your ubuntu release).

---

### Post by vasa1 on 2012-06-27
> **bogan said:**
> ...
I would like to know -[Edit: -*** how to find out ***-] - whether either 295.53 or 295.59 versions are available from the 'ppa's, and if so , how to get them installed. I am not prepared to find out by using apt-get install, without knowing which version will be supplied, from previous disastrous experiences of the bugged version.
...
In general, you could try apt-get install -s package-name. This does a simulation listing to the screen and doesn't need sudo because nothing is being installed.

---

### Post by bogan on 2012-06-28
Hi!, **vasa**1,

Thanks for your helpful response - at least it is helpful when I already know what the package name is, unfortunately, the nvidia driver seems to come with an infinitely variable package name.

The copy of Synaptic I am looking at lists 13 variations, and that does not include four others that I use or have used recently.

I ran: ```
apt-get install -s nvidia-current 
```and it returns the same bugged version 295.40.

@**markbl,**  thanks for your response; you Posted:>  How can you be "using" two different versions of the nvidia driver? I have two desktops that each have two 12.04 installations, one updated from earlier versions, the other clean installs. I also have 10.04 on one and 11.10 on the other, whilst two Usb installations have 11.10 and 12.04LTS.

So I could - if I so wished - be "using" **eight different** nvidia drivers except that one does not use nvidia at all, but the default Nouveau. > If you install random files/scripts outside of the package system (e.g.  by running a downloaded nvidia script) then how do you expect the  package managers to know about this?I do not know enough about the 'package system' to have any expectations of it, but I assumed the database of installed items would be updated by the "random" nvidia-installer*.*> To check the version first before you install them then just check  synaptic after the update but before doing the install. Remove/disable  the ppa if you don't like the version. This assumes that I already know what 'ppa' to add to the sources list and what the package name is. 
 You seem to have missed the whole point of my query, which is***: " How do I find out how to determine If, and where, a suitable [driver] package is obtainable?, and if so what its package name is".* **>  Of[sic] just go to the ppa launchpad site and check the versions directly before you do anything (filter by your ubuntu release).      If you would explain in detail how I can do that, you would indeed be answering my query. 

I have exhausted my imagination in attempting to do so, but only get 'Server not found' or 'Not available at 'xxxxx' messages'.

Chao!, **bogan.**

---

