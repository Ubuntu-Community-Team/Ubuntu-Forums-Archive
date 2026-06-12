---
title: "Prohibitive Installation Times"
date: 2012-01-10
forum: General Help
---

### Post by Trapper on 2012-01-10
I am sure this query has already been made but my searches aren't coming up with anything.

I am having time difficulty with U 11.10 installs. They take an unreasonable amount of time to complete. I can download the iso and burn it to disk in much less time than it's taking me to install.

I know this is an internet problem. Earlier version of U (8 & 9) install easily and quickly but 11 is insistent on downloading language packs and other things from the internet and is taking forever to do so. I realize I have slow DSL. Only 1.5 over wireless but I cannot believe it gets bogged down to the point that it takes close to 2 hours to install 11.10. I really don't know what 11.10 is requiring from the internet but I have 3 different internet download situations that slow down my installs incredibly. I know one is language packs. There's another that downloads 50-60 smaller files earlier in the install. Then, just when I think the install is about to complete something else starts downloading and it may take up to another 30 minutes for just that.

When I install I am positively NOT selecting the option to update to newer available files during the install. I am also NOT selecting the music/multimedia 3rd party files. Uniquely, after installation completes I boot up and do an update for newer files. There are 200 + updates available but they take so much less time to download and install than  the initial install takes.

Uniquely, I never have speed difficulty downloading large iso's or other large amounts of info from completed installs. Because I have slower broadband it does take a while but it's always within reason.

Is there some other way I can lessen my installation time? I don't mind  it taking a while but a couple of hours is way too much. I've tried this  with several machines over a 2 week time period and the results are  always the same.

---

### Post by lukeiamyourfather on 2012-01-10
If I remember correctly the installer asks if you want to skip that step (downloading latest packages), so just skip it. If it doesn't ask then just unplug the network cable. It takes me about ten minutes to install Ubuntu and I typically don't have the network plugged in during install.

---

### Post by pbrane on 2012-01-10
By install I assume you mean fresh install, not an upgrade. I don't know how to shorten your download times for the installation. The operating system and any programs installed have dependencies and they will be installed. 

I usually create a startup disk to a thumb drive. My complete and fresh installs take about 20 mins. It's slower from a CD/DVD, almost twice as long. I'm on a Dell Inspiron 1720.

---

### Post by Trapper on 2012-01-10
> **lukeiamyourfather said:**
> If I remember correctly the installer asks if you want to skip that step (downloading latest packages), so just skip it. If it doesn't ask then just unplug the network cable. It takes me about ten minutes to install Ubuntu and I typically don't have the network plugged in during install.

Yeah, I skip the step to download latest packages. I did just do an install while disconnected from the internet. It took 12 minutes to complete. I haven't booted into the install yet so I don't know what's going to transpire once I do with an internet connection.



[QUOTE=pbrane]By install I assume you mean fresh install, not an upgrade. I don't know  how to shorten your download times for the installation. The operating  system and any programs installed have dependencies and they will be  installed. 
[/QUOTE]

Right pbrane, I am meaning a new install. I stay away from upgrades. I do assume my slow internet does figure into the huge time factor I am referring to. I am just trying to figure out what is taking so long to download from the internet and why it is taking as long as it does. In relation to normal download speeds after an install is completed the installer would have to be downloading 700 + MB of info. I really, really doubt it is requiring that . The download speed during an install just seems to be unreasonably slow in comparison to the download speed of an already installed system.

---

### Post by lukeiamyourfather on 2012-01-10
The slowness might be from the particular mirror of the repository, some are faster than others. No big deal though. When you boot for the first time it should ask if you want to install updates. If it doesn't, or if you want to install them right away run these commands. The first will update the list of packages and the second will install newer packages.

```

sudo apt-get update
sudo apt-get upgrade

```

---

### Post by Trapper on 2012-01-10
> **lukeiamyourfather said:**
> The slowness might be from the particular mirror of the repository, some are faster than others. No big deal though.


Actually it is a big deal when it takes 2 hours to install Ubuntu. :)  I'm not sure the "slow mirror" theory is valid unless I have aways gotten the slow mirror over a couple of weeks. I've tested the install a number of times over that period and it's been basically the same each time.

I am well familar with the apt-get update/upgrade commands. I did a couple of disconnected installs today and also did a disconnected install of Mint. They all installed in less than 15 minutes. All also had 250+ updates. I only install the updates for one. It took about 35 min.

I do save time by doing an offline install so I'll consider this thread as solved. Thanks for your input.

---

