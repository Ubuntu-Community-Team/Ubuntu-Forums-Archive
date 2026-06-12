---
title: "Will 3.1 kernel come to Oneiric??"
date: 2011-10-24
forum: General Help
---

### Post by keithy on 2011-10-24
As 3.1 was released this morning!

Will Oneiric get it automatically at some point??

Or will we have to wait for 12.04 for 'official' support

I'm sure theres a PPA for latest kernel somewhere, but how stable is it to use a PPA for a kernel update ?!?

Thanks for any insight!

---

### Post by zvacet on 2011-10-24
I don´t think you will see kernel upgrade until new version comes.If you find PPA for new kernel version you will still have old ( witch comes with 11.10) so if new kernel is not good for you boot in old one and delete new and PPA you added.

---

### Post by Bobhuber on 2011-10-24
> **keithy said:**
> As 3.1 was released this morning!

Will Oneiric get it automatically at some point??

Or will we have to wait for 12.04 for 'official' support

I'm sure theres a PPA for latest kernel somewhere, but how stable is it to use a PPA for a kernel update ?!?

Thanks for any insight!
I've been using the RC of 3.1 for some time now.Your better of just installing the .deb files if wanted or needed as they become available -  [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by oldtimer7777 on 2011-10-24
> **Bobhuber said:**
> I've been using the RC of 3.1 for some time now.Your better of just installing the .deb files if wanted or needed as they become available -  [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")

Use Mainline. Works great.

---

### Post by oldfred on 2011-10-24
Each release is frozen as far as versions go. Only rarely does any application even get updated (or even  directly available) other than the backports for security. Of course as posted above you can do your own thing, but then you are doing your own testing to verify everything works together.

[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases)

---

### Post by oldtimer7777 on 2011-10-24
> **oldfred said:**
> Each release is frozen as far as versions go. Only rarely does any application even get updated (or even  directly available) other than the backports for security. Of course as posted above you can do your own thing, but then you are doing your own testing to verify everything works together.

[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases)

You can use mainline. Download the deb for the headers and the image you want. You don't need the repositories if all you want to do is update your kernel.

---

### Post by Bucic on 2011-10-25
Are there 3.1 upgrade instructions for U 11.10 x64 somewhere?

---

### Post by lykwydchykyn on 2011-10-25
> **Bucic said:**
> Are there 3.1 upgrade instructions for U 11.10 x64 somewhere?

 - Go here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.1-oneiric/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.1-oneiric/)

 - Download 3 debs to a folder somewhere:
  - linux-headers-<version numbers>-all.deb
  - linux-headers-<version numbers>-amd64.deb
  - linux-image-<version number>-amd64.deb

 - Install the debs with whatever package manager front-end you use (is gdebi still around?), or use these commands:
```

cd /path/to/folder/where/you/put/the/debs
sudo dpkg -i *.deb

```

Now reboot, and experience the magic of Linux 3.1.  Be aware that proprietary drivers may or may not work correctly with an "unofficial" kernel version.

---

### Post by elliotn on 2011-10-25
3.1 works good for me

---

### Post by philinux on 2011-10-25
> **keithy said:**
> As 3.1 was released this morning!

Will Oneiric get it automatically at some point??

Or will we have to wait for 12.04 for 'official' support

I'm sure theres a PPA for latest kernel somewhere, but how stable is it to use a PPA for a kernel update ?!?

Thanks for any insight!

[https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)

[http://people.canonical.com/~ubuntu-archive/pending-sru.html](http://people.canonical.com/~ubuntu-archive/pending-sru.html)

So if a new kernel fixes a lot of bugs it will come via an SRU.

---

### Post by hwttdz on 2011-10-25
```
I'm not sure if this is still convention, but in general .odd 
releases (i.e. .1, .3, .5, .7, .9) are considered more experimental, 
and .even releases (.0, .2, .4, .6, .8) are considered more stable.
```

in code block to kill smilies.

---

### Post by BazookaAce on 2011-10-25
What's changed in 3.1?

---

### Post by BazookaAce on 2011-10-25
Hello! It's a very simple question.

---

### Post by Bucic on 2011-10-25
> **BazookaAce said:**
> Hello! It's a very simple question.
So simple even google can answer... [http://www.h-online.com/open/features/What-s-new-in-Linux-3-1-1347364.html](http://www.h-online.com/open/features/What-s-new-in-Linux-3-1-1347364.html)

---

### Post by keithy on 2011-10-25
Thanks,

everyone for the great replies

I'll give it a go soon

Tx

---

### Post by Bucic on 2011-10-25
> **lykwydchykyn said:**
> - Go here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.1-oneiric/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.1-oneiric/)

 - Download 3 debs to a folder somewhere:.
.
.
.

Thanks a lot!

---

