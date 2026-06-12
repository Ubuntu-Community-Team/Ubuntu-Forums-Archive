---
title: "Saving Synaptic packages"
date: 2010-08-10
forum: General Help
---

### Post by Scott Swinyard on 2010-08-10
I normally use openSUSE but a recent hardware failure caused me to lose my installation. During the period of time that it was being repaired, support for the version I was using came to an end. The next version does not work properly with my proprietary Ati driver and since I like to play 3d games it has prompted me to try to find a substitute. I believe I may have found that in Ubuntu Hardy Heron 8.04 LTS.

 The problem is that I am still going to be stuck with an old computer that will still play ut2004 and Nexuiz for an extended period of time, but Heron will reach it's end of support next April. 

I haven't installed it yet, but before I start I'd like to know if there's a way to make the Synaptic package manager retain the packages it uses to install software after an installation has been completed. This way hopefully in case I have to reinstall the system after Heron reaches it's end of life, I can save these packages and use them to restore it to it's previous state complete with all of the extra programs I will have put in it and updates that will have been made to it up to to the point where it's support ended.

This includes retaining packages for dependencies for what anything I may have installed requires.

I'll also need to know where it saves them so I can pull them out and copy them to some form of removable media or another hard drive.

I am assuming that Synaptic can be configured to use local repositories.


I may be using Hardy for a long time.

Thank you.

---

### Post by drs305 on 2010-08-10
I haven't used it, but do a search on "apt-on-cd".

Another option which should prove useful is to use the repositories located at [http://old-releases.ubuntu.com/ubuntu/dists/]("http://old-releases.ubuntu.com/ubuntu/dists/").

You can modify your sources.list addresses once the day comes when Hardy repositories are no longer supported at their current addresses. At that point, they should be moved to the location above so you can still run an old release and use the repository packages available when support ended.

---

### Post by Scott Swinyard on 2010-08-10
Really? That's really cool. How long do these old release repos last? Are they complete?

One wonders why I was not aware of some similar form of support for openSUSE.

It would still be nice just on general principals to know how to make Synaptic save the packages it uses to install stuff.


Thanks for your help.

---

### Post by drs305 on 2010-08-10
The packages go all the way back to breezy, so you won't have a problem there.

As far as saving the debs, check out 'apt-on-cd'. 

Also, if you didn't know, your downloaded packages reside in /var/cache/apt/archives but are removed after a given time period or if you run the "apt-get clean" command. 

You also can download but not install packages via an option once you have pressed the "apply" icon in Synaptic.

---

