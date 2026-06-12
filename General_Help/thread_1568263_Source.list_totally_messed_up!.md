---
title: "Source.list totally messed up!"
date: 2010-09-04
forum: General Help
---

### Post by GermanGuaimare on 2010-09-04
Hey guys, I really need your help. I changed the source.list text and lost my backup so now I can't update or install anything. I was wondering if you could provide me the default source.list text for ubuntu 10.04.

This is what synaptic manager says:

E: Dynamic MMap corrió fuera de la sala. Incremente el tamaño de APT::Cache-Limit. Valor actual: 25165824. (man 5 apt.conf)
E: Ocurrió un error mientras se procesaba simple-scan (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_lucid-updates_main_binary-amd64_Packages
E: Las listas de paquetes o el archivo de estado no se pueden analizar sintácticamente o abrir.
E: _cache->open() failed, please report.

W: Unable to munmap

Some things are in spanish, I know, but I think the more experienced linux users should recognize some of the problems I'm having.

It looks really complicated and I am not an expert in linux yet. Please guys, help me. Thanks in advance, cheers.

---

### Post by flick on 2010-09-05
#deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100429)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse

---

### Post by GermanGuaimare on 2010-09-05
Wow, thanks for your help flick. The synaptic manager is ok, but now some of the applications in ubuntu software center don't show the "install" button. What can I do? Sorry for all the trouble, I'm just learning to use Ubuntu. Thanks in advance.

Wait, problem solved, just had to change some things in software origin configuration. Thank you for the help. Cheers.

---

### Post by QLee on 2010-09-05
[QUOTE=GermanGuaimare]...
Some things are in spanish, I know, but I think the more experienced linux users should recognize some of the problems I'm having.
...[/QUOTE]
Was this to be some kind of test? ...and why didn't you ask about the cache being out of room?

Since you are new at this I want to tell you that the forum has a very good search feature, most, if not all, questions that an inexperienced user has have been asked previously by other inexperienced users and can be found with a keyword search similar to searching with a search engine like Google.

[LEFT]Edit: Oh yeah, why is a person using a Spanish speaking system using the salutation, "cheers"? :-)
[/LEFT]

---

### Post by GermanGuaimare on 2010-09-07
A test? Why would I test you QLee or any of my fellow ubuntu users? I didn't asked about the cache because I simply didn't understand my problem.

About the "cheers", I'm a Venezuelan with a self instructed english so, i can communicate but I'm really not a expert.

Sorry if this question was asked before, I googled my problem a couple of times but I didn't find a solution.

---

### Post by philinux on 2010-09-07
> **GermanGuaimare said:**
> A test? Why would I test you QLee or any of my fellow ubuntu users? I didn't asked about the cache because I simply didn't understand my problem.

About the "cheers", I'm a Venezuelan with a self instructed english so, i can communicate but I'm really not a expert.

Sorry if this question was asked before, I googled my problem a couple of times but I didn't find a solution.

**Well done for your English.**

If this happens to anyone else here is a good link. It generates a sources list based on the distro.
[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

---

### Post by QLee on 2010-09-08
[QUOTE=GermanGuaimare]A test? Why would I test you QLee or any of my fellow ubuntu users? I didn't asked about the cache because I simply didn't understand my problem.[/QUOTE]

I have no idea why you would do anything.  Because of the way you phrased your statement I asked for clarification. I wondered why someone who wrote so well in English would post an error message in Spanish and then not ask about it.

[QUOTE=GermanGuaimare]Sorry if this question was asked before, I googled my problem a couple of times but I didn't find a solution.[/QUOTE]

I mentioned the search of Ubuntu forums because I saw you were new here and often new members don't yet realise how useful a forum search can be, especially for new users questions. But you don't have to use it.

I have to say, you did a great job learning English, no way I could operate in a Spanish technical forum even half as well as you do here.

---

### Post by GermanGuaimare on 2010-09-08
Thank you so much guys. This is a great community and I'm glad to be a part of it. I hope this thread can help others with this same issue.

Thanks for the comments on my English, I see it worth the time I spent working on it.

---

