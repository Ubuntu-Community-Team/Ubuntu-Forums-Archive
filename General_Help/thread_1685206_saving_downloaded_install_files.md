---
title: "saving downloaded install files"
date: 2011-02-10
forum: General Help
---

### Post by op3studios on 2011-02-10
hello,

I just switched to a faster isp with monthly usage limits.

when I install a program using Synaptic, where are the install files stored?

I'd like to save them for future use.

also, I'm downloading Conky right now to monitor usage.  if there's something better, please suggest.


thanks!

Jim

---

### Post by Frogs Hair on 2011-02-10
I used to save some .deb packages from the application/s website to a folder for future use . The problem I ran into was the packages often would  no longer work when the next version of ubuntu came out because I update to the latest version. If you are using LTS version this may work better.
 
Do search for an Ubuntu offline repository , I have a link but am not home right now . You will still have to download and make the repository . If you are planning to update to 11.04 it may not be worth the effort.

---

### Post by grahammechanical on 2011-02-10
Synaptic Package Manager and the Ubuntu Software Centre do two basic things: 1) Download the program; 2) Install it for you. The program files are spread into the appropriate folders in the file system and the Home folder.

It is possible to create your own repository of programs on a CD and tell Synaptic to download from there. I cannot tell you how to do this. But remember, These files will be old by the time you will need to re-install from CD. There my have been security updates or improvements to the programs that will involve a download of the complete program. So, you may find that you are still downloading several megabytes to bring the program up to date.

For example, today I received notification of an update to the Wine program. It is a download of the complete program, about 11MB. I shall wait until after midnight when my ISP allows downloads without adding them to the download limit.

Regards.

---

### Post by vat with tux on 2011-02-10
The .deb packages  are stored on this directory:
/var/cache/apt/archives

---

### Post by op3studios on 2011-02-10
thanks for the replies.

I understand about things going out of date,
but I'm mostly interested in downloading once
for my several computers instead of each one at a time
which replicates downloads and ups usage.

does synaptic download and store package files?
or are they downloaded to a temp file and then deleted after install?

I like synaptic, just want to preserve downloads for immediate use on my laptop.

and recently I had to nuke my system partition and restore a backup image that did not include the most recent programs I installed.   so I'm downloading/installing them again.
if I had the files from the initial install I wouldn't need to download anything.

JHS

Jim

---

### Post by mcduck on 2011-02-10
Just like vat with tux said above, the package management caches all installed packages into */var/cache/apt/archives*.

So you'll find the .deb files there. Regardless if you use apt-get, Synaptic, Software Center. They are all just different interfaces for the same package management system.

There are many ways you can use the packages on another system. The simplest ones, that require no configuration or installation of any additional tools, are just copying all cached packages to /var/cache /apt/archives on another computer. The package manager on that system will then find them and use them instead of downloading the packages from the repositories (at least unless there's an updated version of the same package available, in which case that's downloaded and used instead). And the other way is to simply dump all the files into one directory and running "*sudo dpkg -i *.deb*" to install them all at once.

---

### Post by gmargo on 2011-02-10
Install the **apt-cacher-ng** package, the "caching proxy server for software repositories".  Configure all of your machines to point through it, and let it preserve the files.

---

### Post by op3studios on 2011-02-10
just what I wanted,
meat *and* potatoes!

I've been meaning to build a repository I can carry on a bootable usb medium.
I'll get started with your suggestions...

thanks!

---

### Post by Habitual on 2011-02-10
> **op3studios said:**
> just what I wanted,
meat *and* potatoes!...

I admire your enthusiasm!
+1

Peep these 'taters
[http://askubuntu.com/](http://askubuntu.com/)

That's where the rubber hits the road. You may never come back here again.

Peace.

---

