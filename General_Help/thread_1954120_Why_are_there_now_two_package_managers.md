---
title: "Why are there now two package managers?"
date: 2012-04-07
forum: General Help
---

### Post by SeijiSensei on 2012-04-07
Having just responded in the thread about "[12.04 and NFS]("http://ubuntuforums.org/showthread.php?t=1954080")" made me wonder why there are now two package managers in Ubuntu, the "Package Manager" and the "Software Center". 
I rarely use any GUI client to install software preferring to use apt-get from the command line.  When I do want a GUI, I prefer to install synaptic even on my KDE platform.  So I never had occasion to examine the differences between the Software Center and Package Manager applications until today.  

Why isn't there just one single Package Manager application any more that includes all packages available to Ubuntu from all official sources?  (PPAs are obviously an entirely different matter.)   This seems unnecessarily confusing to me and would, I suspect, be even more confusing to a novice user.

---

### Post by raja.genupula on 2012-04-07
[http://askubuntu.com/questions/25724/what-is-the-difference-between-ubuntu-software-centre-and-synaptic-package-manag](http://askubuntu.com/questions/25724/what-is-the-difference-between-ubuntu-software-centre-and-synaptic-package-manag)

---

### Post by codemaniac on 2012-04-07
Software Center is for newbies , just introduced to Ubuntu and its name also guides the user the right way I guess .Where Synaptic is more feature riched and provides the same features as the apt-get command line utility with a GUI front-end based on Gtk+.

---

### Post by coffeecat on 2012-04-07
Your title might have been "why is there now only one package manager?" In Ubuntu, Synaptic and Software Centre (or its predecessor Add/Remove) have co-existed for years. With effect from Oneiric/11.10 only Software Centre of the two come in a default install and you have to install Synaptic (I do) if you want it.

---

### Post by SeijiSensei on 2012-04-07
Kubuntu 12.04 includes both a "Muon Software Center" and a "Muon Package Manager".  The latter is equivalent to the older package managers like synaptic.  The "Software Center" application seems to have a very curtailed list of packages available.  For instance, in the case of the thread I referenced at the top, searching the Software Center for "nfs" only brings up a Java-based FTP client.  Searching the "Package Manager" brings up the usual array of software like nfs-common and nfs-kernel-server.

What do you get if you search the Software Center for "nfs" on a recent vanilla Ubuntu system, say 11.10 or 12.04?  Maybe this is exclusively a problem with Kubuntu?

> **raja.genupula said:**
> [http://askubuntu.com/questions/25724/what-is-the-difference-between-ubuntu-software-centre-and-synaptic-package-manag](http://askubuntu.com/questions/25724/what-is-the-difference-between-ubuntu-software-centre-and-synaptic-package-manag)

I realize that the Software Center is supposed to be an "app store" styled program, but it doesn't seem to include the entire range of packages in the official repositories.  Again, is this only true on Kubuntu?

---

### Post by coffeecat on 2012-04-07
In a fairly well-used Oneiric Ubuntu system, searching for "nfs" in the Software Centre brings up what you can see in the first screenshot. Clicking on "Show 57 technical items" brings up the second and nfs packages are listed there. I can also get the second if I go to "System" in Software Centre and then search for nfs. Perhaps the OP in the thread you linked didn't notice the "Show 57 technical items" link.

I'm just installing today's 12.04 daily to my netbook. I'll see what happens in a fresh install of Pangolin and post back.

---

### Post by SeijiSensei on 2012-04-07
Kubuntu's Muon Software Center doesn't show any "technical items" entry for "nfs" at all.  Browsing the menus and the left-hand navigation pane doesn't show any equivalent entries either.

If I search the list of installed items, I don't see "nfs-common" either, even though it's installed on this machine.

---

### Post by SeijiSensei on 2012-04-07
It appears that the [Muon developers decided to split applications]("http://jontheechidna.wordpress.com/2012/03/04/muon-suite-1-3-0-released/") between the Package Manager and Software Center programs.  The apparent justification for this is to make things easier for naive users who don't care about the kinds of software people like me use every day like, say, NFS!

I'd be okay with this approach if there was some indication of a method to show the entire array of packages like the "technical items" entry coffeecat described.  As it stands now, it's a recipe for confusion for people who expect their systems to be something other than an iPad clone.

I'm going to file a bug for this requesting the addition of an equivalent to the "technical items" feature in vanilla Ubuntu.

---

### Post by coffeecat on 2012-04-07
Interesting. It seems that this is a Kubuntu, not an Ubuntu/gnome issue. You tagged the thread "all variants" - hence my earlier reply. Do you want it tagged Kubuntu? You might get some Kubuntu users commenting. If you can't change the tag yourself, just say and I'll change it for you.

---

### Post by coffeecat on 2012-04-07
Curioser and curioser. My 12.04 installation on the netbook is up and running. A completely vanilla install with just a "sudo apt-get update". I can't find any nfs packages in Software Centre, yet when I install Synaptic with apt-get, there are some nfs packages listed in Synaptic. Perhaps an all variants issue after all. So I can confirm what the OP in your linked thread saw.

---

### Post by SeijiSensei on 2012-04-07
I've filed [this bug](https://bugs.launchpad.net/ubuntu/+source/muon/+bug/976071) against Muon at Launchpad.  Does the 12.04 version of Ubuntu Software Center omit that helpful "technical items" entry you showed us above?

I'll leave it to you to decide whether this is a Kubuntu or an all-variants issue. 

I really hope Ubuntu development isn't going to abandon experienced users out of a desire to focus on the needs of naive users.  My experience with coping with the [resolvconf]("http://ubuntuforums.org/showthread.php?t=1914807") issue hasn't been especially positive either.

---

### Post by coffeecat on 2012-04-07
> **SeijiSensei said:**
>   Does the 12.04 version of Ubuntu Software Center omit that helpful "technical items" entry you showed us above?

Yes it does omit. No link at all.

> **SeijiSensei said:**
> I'll leave it to you to decide whether this is a Kubuntu or an all-variants issue. 

I'll leave it as it seems to be a 12.04 issue. I just noticed that the thread you linked was in Desktop Environments, so I've moved it into the Precise Pangolin testing forum to see if the regular pre-release testing crowd have anything to add.

> **SeijiSensei said:**
> I really hope Ubuntu development isn't going to abandon experienced users out of a desire to focus on the needs of naive users. 

I very much doubt this is so. I'd put this down to a bug until proven otherwise.

---

