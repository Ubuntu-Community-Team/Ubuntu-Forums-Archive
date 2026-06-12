---
title: "Uninstall Ubuntu bloat"
date: 2011-05-24
forum: General Help
---

### Post by .psd on 2011-05-24
Is there a way to uninstall all the bloat without breaking ubuntu? It seems like some things (banshee, the calendar, ubuntu one) are integrated with the notifcations and probably other areas too. I think last time I uninstalled them, the calendar was still there in the notifications but clicking a date did nothing, and I'm sure there were other leftover goodies that I didn't take time to find before re-fresh-installing ubuntu. I think ubuntu has a lot of potential as a linux distro, but I'm not interested in their promoted software (i.e. libreoffice)

Another question: when you install an application in windows and then uninstall it, there remain uninstalled changes to your system (leftover icons, links, shortcuts, folders, files, registry entries) like the uninstaller was drunk on the job. Is this fixed in ubuntu or are there remnants of everything you uninstall?

Also comments welcome on what you consider both bloat *and* safe to uninstall.

---

### Post by 3Miro on 2011-05-24
Some things cannot be uninstalled without breaking the system. Use Synaptic Package manager to remove things that you don't like, but keep an eye on what else is being removed.

Ubuntu removes things with either "remove" or "purge". Remove leaves the settings files, purge removes those too. In windows, all applications rely on the registry database to run, if the database gets loaded with too many entries, the entire system slows down. In Linux, all settings are kept in separate text files, so there is no slowing down if you leave the files behind (the settings files are also too small to make a difference).

My definition of "bloat" is something that I don't use AND it runs in the background slowing things down. From that perspective Ubuntu has virtually no bloat.

Some people call bloat programs that are installed and are not used. In either case, "bloat" is completely subjective and it depends on exactly what is it that you want to do.

Look at the installed programs and then look at Synaptic Package Manager for what can be removed.

---

### Post by Rubi1200 on 2011-05-24
I have another suggestion; rather than working from the top down, with the high risk of breaking something, why not work from the bottom up?

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)
This link explains how you can install a minimal base system which you can then build up to only include the desktop environment and packages you want and need.

For example, in a test install this is what I got:

base install + desktop environment (not Gnome or KDE) + login manager + browser = less than 1.5GB total install.

I am only giving rough figures here because I played around with openbox, fluxbox, xfce, and lxde and didn't write the exact figures down, but those were my results.

---

### Post by .psd on 2011-05-24
The computer I'm running is top of the line so I'm not as worried that bloat will hog my live resource needs as much as the fact I'm a picky minimalist :) Leftovers from an incomplete uinstall might not bog down the system, but they're in my periphs lol, always in the back of my mind haunting me.

That said, I knew GNU/Linux was a much more efficient OS, so how do I ensure that all my uinstalls are Purges and not Removes? And is it safe to say that anything I uninstall via Ubuntu Software Center which doesn't give me a warning about the things it will break, will therefore not break things? Does USC uninstall using Remove or Purge methods?

Coming from windows, synaptec manager is complete gibberish to me... The way I uninstalled things last time was through Ubuntu Software Center's "Installed Software". Is the result similar to what Synaptec accomplishes? Are there other popular programs to manage what's installed?

@Rubi1200 That would have been ideal! The Ubuntu experience seems to be primarily a learning experience though, so I naturally started without knowledge of that process :( and now I'm too invested in my setup to feel like starting over yet again. For now at least...:D:D

---

### Post by sidzen on 2011-05-24
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
may help, and I'd stick with 10.04, but that's just me -- in a *minimal* minority!

---

### Post by idoitprone on 2011-05-24
if you are ok with using and editing files at the command line. try arch linux. They have pretty good doc to set up a system. Beware, installer is simple but not easy to understand. Configuring your system your first time will practically take whole day. I saying this to throw in variety of distro in the mixture. Trying new things is learning

tip: when you are installing pacakges and you only use wifi. Remeber to add the wireless-tools in the mixture.

---

### Post by .psd on 2011-05-24
> **Rubi1200 said:**
> I have another suggestion; rather than working  from the top down, with the high risk of breaking something, why not  work from the bottom up?

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)
This link explains how you can install a minimal base system which you  can then build up to only include the desktop environment and packages  you want and need.

For example, in a test install this is what I got:

base install + desktop environment (not Gnome or KDE) + login manager + browser = less than 1.5GB total install.

I am only giving rough figures here because I played around with  openbox, fluxbox, xfce, and lxde and didn't write the exact figures  down, but those were my results.
> **sidzen said:**
> [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
may help, and I'd stick with 10.04, but that's just me -- in a *minimal* minority!
> **idoitprone said:**
> if you are ok with using and editing files at  the command line. try arch linux. They have pretty good doc to set up a  system. Beware, installer is simple but not easy to understand.  Configuring your system your first time will practically take whole day.  I saying this to throw in variety of distro in the mixture. Trying new  things is learning

tip: when you are installing pacakges and you only use wifi. Remeber to add the wireless-tools in the mixture.

If there's on thing about the ubuntu community, it's that they'll give you a million answers to accomplish something entirely different than what you asked lol. Anyways thanks for the suggestion but it's not particularly relevant... I'm trying to learn about uninstalling, not to learn about ways I could do it better if I start over from scratch.

---

### Post by 3Miro on 2011-05-24
Ubuntu Software Center removes things, it does not purge.

Synaptic Package Manager can purge things and if you say "remove Firefox" it will tell you what else is installed and depends on Firefox (so you have to remove that too). Read carefully on what you uninstall. You don't want to uninstall compiz or Unity or gnome-panel, to name a few.

There are very few things that will seriously break the system. In most cases, you will only lose the graphical environment, which you will not be warned about.

If you lose the graphical environment, then use the command:
```
sudo apt-get install ubuntu-desktop
```
this will revert the graphical things that you may have uninstalled.

From your original post, you said that you wanted to have a system that is clean from "bloat". Installing minimal system and then building it up or using a distribution that lets you be more picky are two good ways of doing this. Although, Arch is somewhat advanced.

---

### Post by .psd on 2011-05-24
That's what I'm talking about 3Miro.

Ok then, looks like Synaptec's uninstall process is what I need with USC's user interface (because Synaptec doesn't make a lick of sense to me and I don't have days to learn how to use it).

It seems like Synaptec is a sort of market and application manager. Awesome! Where can I get a more user friendly manager like Synaptec? In fact, recommendations for some markets/archives/databases for linux apps are welcome. As it stands, I don't know where to find new software, and I don't want *only* officially approved or officially listed apps, which is what it seems like USC or Synaptec provide.

---

### Post by 3Miro on 2011-05-24
> **.psd said:**
> ...markets/archives/databases for linux apps are welcome.

The right word is "repository".

Ubuntu has one of the largest (if not the largest) repository with Linux software. You should be able to find pretty much everything that you need.

In addition, you can find several unofficial repositories, but use those only at your own peril. Most of the unofficial ones are OK, but there is no guarantee.

Medibuntu is a good repository for multimedia (audio/video codecs and such).

[http://medibuntu.org/](http://medibuntu.org/)

Other than that, you have to look at what kind of program you want and then look if it has a Linux version already.

---

### Post by .psd on 2011-05-25
> **3Miro said:**
> The right word is "repository".

Ubuntu has one of the largest (if not the largest) repository with Linux software. You should be able to find pretty much everything that you need.

In addition, you can find several unofficial repositories, but use those only at your own peril. Most of the unofficial ones are OK, but there is no guarantee.

Medibuntu is a good repository for multimedia (audio/video codecs and such).

[http://medibuntu.org/](http://medibuntu.org/)

Other than that, you have to look at what kind of program you want and then look if it has a Linux version already.
How can I access the Ubuntu repository? Is there any user friendly way, like on Windows you would go to something like download.com, compare the results side by side in tabs, download the top few and uninstall the ones you don't want. Ubuntu Software Center seems like it does this, does it have full access to the official Ubuntu repository?

And what are some popular *unofficial* repositories, preferably NOT complicated and uninforming like Synaptec, preferably akin to things like the android market, appbrain.com, download.com, or even the ubuntu software center.

---

### Post by linuxinstalledfromhdd on 2011-05-25
Well you could try Getdeb. It's more like what you are describing. 

[http://www.getdeb.net/welcome/](http://www.getdeb.net/welcome/)

But I have to say, I would recommend you install any software for your system directly from a PPA however.

Reason being, that way you recieve the latest updates all the time. Because if you just install a package from somewhere, it doesn't get updates, unless it is able to update itself independently.  Thats why PPAs are recommended.

---

### Post by .psd on 2011-05-25
Checked out a bunch of markets, softpedia has the most results.

What's a PPA and how can I install that way? Although full featured programs tend to have a built in auto/manual update feature...

---

### Post by linuxinstalledfromhdd on 2011-05-25
Welcome to Linux. :) 

We use repositories to install packages, but you can install them individually. However a PPA will fasciliate the ability to upgrade them along the rest of your normal updates to your system automatically.  Highly recommended too. 

[http://en.wikipedia.org/wiki/Personal_Package_Archive](http://en.wikipedia.org/wiki/Personal_Package_Archive)

---

### Post by cbowman57 on 2011-05-25
> **.psd said:**
> Checked out a bunch of markets, softpedia has the most results.

What's a PPA and how can I install that way? Although full featured programs tend to have a built in auto/manual update feature...

A handy tool to have installed is Ubuntu Tweak.

You can find the .deb & download it or add it from the terminal:

```
sudo add-apt-repository ppa:tualatrix/ppa
sudo apt-get update
sudo apt-get install ubuntu-tweak 
```

The first line is a simple method of adding ppa's.

---

### Post by linuxinstalledfromhdd on 2011-05-25
Don't forget about:

[http://www.webupd8.org/2010/11/y-ppa-manager-easily-search-add-remove.html](http://www.webupd8.org/2010/11/y-ppa-manager-easily-search-add-remove.html)

That a great little application. :)

---

