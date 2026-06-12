---
title: "Apt-get does not &quot;got it&quot; or Fixing a Broken Package Saga"
date: 2011-02-10
forum: General Help
---

### Post by GutsyGibbonMarc on 2011-02-10
So I wonder if my experience is unique.

I install a deb pkg with apt-get. I get about 50 dependencies that need to be installed. No problem. I will just apt-get each dependency until all 50 are installed nd then do a reinstall of the original package. But wait, it appears that the first package that produced the 50 dependencies is in a broken state. No problem.  Let me check the man pages. Oh, lets try apt-get remove. Nope it is still in a broken state. Ok, how about apt-get purge. Nope it is still in a broken state.  Hmmm. How about apt-get -f to "fix" the broken the state. Nope, that did not work either.

Now what is interesting is that apt-get just "pushed" all these files out the file system so WHY can it not just retrieve the same files back?!!!

This is not windows where you can do a reboot and some files might be called and in memory.  They were just pushed out there. So why cannot apt-get just retrieve the files???

So I figured I would try the Snynaptic Package Manager. But guess what? The application will not work because of the broken package.  There is no Ignore. It just quits!  I cannot even run the GUI Package Manager.  It cannot handle the existence of a broken package. Unbelievable!

So after more researching this incredible dilemna, I renamed the files associated with the package install within /var/lib/dpkg/info/--the files that end with .postinst, .postrm, .preinst., and .prerm.  At that point, Meerkat does not think it has a broken package anymore. I install the 50 other dependencies and reinstall the package and everything works smoothly.

So a few questions.

At this point in Ubuntu development, how come we cannot have an apt-get utility with a bit more smarts and firepower so that it can actually remove an application it just partially installed.  If I can manually rename those files, why cant apt-get do the same thing behind the scenes and take care of this?

Why does Synaptic Package Manager built so it quits on a broken package. 

Is everyone else okay with this functionality?

Thanks,

M

---

### Post by snowpine on 2011-02-10
We could give you a better reply if you tell us what "the broken package" is and where you got it. I am guessing it's a .deb you downloaded from a website, rather than from the Ubuntu repositories, is that correct? Installing a tested and trusted package from the repos should not require manual resolution of dependencies.

---

### Post by GutsyGibbonMarc on 2011-02-10
Yep. the package was not part of sources. Its name is Octopussy from [www.8pussy.org](www.8pussy.org).  (Not a joke either). Still, would you think an installer can keep track of where the files are going then reverse it and not necessarily rely on how the package is written no?  Also, why cant Synaptic Package Manager have an ignore feature with respect to broken packages so I can continue to install the dependencies.  

M

---

### Post by snowpine on 2011-02-10
You missed the instructions:

[http://www.8pussy.org/dokuwiki/doku.php?id=install#debian_ubuntu_installation](http://www.8pussy.org/dokuwiki/doku.php?id=install#debian_ubuntu_installation)

Not Ubuntu's fault. ;)

---

### Post by GutsyGibbonMarc on 2011-02-10
I had apache, mysql, and rsyslog installed prior to running the deb package. There are other 50 dependencies that the package required that were not listed on the website and you would not know until you ran dpkg -i package name.

My point is really independent of the instructions. 

1.  If an utility can push out files to a filesystem, why cant it retrieve the same files if the install gets only partically completed. 

2. Why does Synaptic Package Manager break when there is a broken package?

3. Why in this day and age of Meerkat Ubuntu, do I need to go into the dpkg/info/ directory and rename the files so everything can work again.

This is Linux and 2011. No reboots are required in this package deployment. No modules were loaded. No files are are resident in memory. If the utility can push out the files, why cant it retrive them?  Why does Synaptic Package  Manager have to break with this achilles heel type issue?

GGM

---

### Post by snowpine on 2011-02-10
First line of the instructions:

> (tested on Debian 5 & Ubuntu 10.04)

The package is not tested with Ubuntu 10.10 Maverick Meerkat; use at your own risk. 

Supported packages from the Ubuntu repositories should not "break" Synaptic.

---

### Post by oldos2er on 2011-02-10
> **GutsyGibbonMarc said:**
> 2. Why does Synaptic Package Manager break when there is a broken package?


So as not to break the system further.

> I install a deb pkg with apt-get. I get about 50 dependencies that need to be installed. No problem. I will just apt-get each dependency until all 50 are installed nd then do a reinstall of the original package.

apt-get should install all needed dependencies the first time it's run, assuming you have all the necessary repositories enabled, so I don't really understand what you're describing here. Seeing the terminal output might help.

---

