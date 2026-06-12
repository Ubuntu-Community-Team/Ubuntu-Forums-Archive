---
title: "I thought I could trust the repositories - is OpenOffice.org an exception?"
date: 2010-10-26
forum: General Help
---

### Post by matteosistisette on 2010-10-26
Hi,

When I want to install a program, usually the first thing I do is to check if I find it in the Synaptic Package Manager, and if I do (which happens 99.99% of the times) I install it from there.

I always thought that, **if** a given program is available through one of the most common repositories, **then **that would certainly be the best source for getting the latest stable version for Ubuntu. I guess that some (probably few) software developers *may *not bother distributing their software through the repositories and would just make their package available for download through their web site. But if so, then I wouldn't find their software in Synaptic at all. If it *is* there, then I can't imagine that the version available from the repository is not the latest and most "official" one.

Also, doing so I felt sure that as soon as an update would be available, I would get it automatically.

Now, some days ago I run into a bug of OpenOffice.org and reported it in their bugtracker. They told me they couldn't reproduce it and advised me to use the latest version (which to my great surprise was not the one I was using) and to make sure I would download it from their site and **not** use a version that came with my linux distribution.

So I did a little bit of checking and I found out the first strange thing. OpenOffice had come installed with Ubuntu, but in Synaptic Package Manager it didn't appear as installed.

I installed it again from Synaptic, but it was the same version that I already had, 3.2.0.

Then I looked at the OpenOffice official site and downloaded OpenOffice from there, a tar-gzipped deb package, and that is version 3.2.1.


So,

1) Why, if OpenOffice is included in the set of packages that are already installed when you install Ubuntu, it is not marked as installed in the Synaptic Package Manager??

2) If there is a 3.2.1 version available for download, why isn't it in the repository?? 

3) Is OpenOffice an isolated case, or should I stop "trusting" the repositories and always prefer installing things from packages I download from the authors' web sites?

thanks
m.

---

### Post by mike555 on 2010-10-26
The repositors use "Tested" versions and it takes time to test versions, plus the version of open office that comes with Ubuntu is slightly different , I understand it is from Go OO ...
  The next version of Ubuntu will have "LibreOffice" a brach of Open Office that should be better ...

[http://www.documentfoundation.org/download/](http://www.documentfoundation.org/download/)

---

### Post by 3Miro on 2010-10-26
This is a loaded question, I suggest you real more about packaging and distribution of software under Linux distributions. The short answer to your question is something like this.

Software developers almost never make packages for Ubuntu or any distribution. The people that make the packages in Synaptic are the Ubuntu developers and/or the community. The software that you can get from Synaptic always lags behind the "latest" software, thought it is usually only by a little bit. This depends of course. The reason for the lag is that people want to test the software before they put it out there officially. Openoffice is a "special" case because it is supported by the Ubuntu developers themselves (as opposed to the community). If you have a problem with Openoffice, you have to report the bug to Ubuntu, if it is a bug with Ubuntu, then they will fix it, if it is with the original OO, then they will report it "upstream".

There are a number of unofficial repositories that you can add to Synaptic and get newer software, however, those have not been tested as much and are usually less stable. Also, be careful about where you get the repository, you can get malware software from an "unofficial" repository just like any other random program that you download from the internet. (there are plenty of clean repos, just do a step of research first)

As for OO not appearing as "installed" in Synaptic, this is because all software in Linux is broken into packages (components), the one that you added was a "meta" package, which means that it doesn't do anything by itself. It only installs other packages and then it can be removed.

>  I always thought that, if a given program is available through one of the most common repositories, then that would certainly be the best source for getting the <b>latest stable version for Ubuntu.</b> 
That is 100% true.

---

### Post by coffeecat on 2010-10-26
> **matteosistisette said:**
> 1) Why, if OpenOffice is included in the set of packages that are already installed when you install Ubuntu, it is not marked as installed in the Synaptic Package Manager??

Had you scrolled down a little bit in Synaptic you would have found the several components of Open Office that are pre-installed. As 3Miro points out, the package openoffice.org is merely a meta-package that would pull in a few less commonly needed OO components if you already have the default install.

And, yes, the version of OO in Ubuntu is the Go-OO one, so if you find a bug you need to report it on Ubuntu's Launchpad, not on the OO bugtracker.

---

### Post by matteosistisette on 2010-10-26
> **coffeecat said:**
> Had you scrolled down a little bit in Synaptic you would have found the several components of Open Office that are pre-installed. 

No. I did scroll a little bit and I did see a lot of other "openoffice-something" packages, most of them with a red ubuntu logo; but none of them was marked as installed - or almost none (and I did have openoffice and regularly used write and spreadsheet at least).

That's what I found strange.

---

### Post by psusi on 2010-10-26
I don't know where you got the notion that the repositories contain the latest and greatest, but it is time you were disabused of it.  The repository contains the software belonging to that release, meaning whatever it was on the day of release.  After release, only critical bug fixes, like security holes, are fixed.  You want new software, you need to upgrade to the new release.

---

### Post by coffeecat on 2010-10-26
> **matteosistisette said:**
> but none of them was marked as installed - or almost none

Then you didn't look very closely. It's the 'almost none' which are the important packages. I have about 20 OO packages installed out of about 200  available ones. Almost all the ones not installed are for languages that I don't need. The rest are modules not in a default install.

---

### Post by matteosistisette on 2010-10-26
Well, now I can't check but I'm pretty sure that among others the following:

openoffice.org3-writer
openoffice.org3-calc
openoffice.org3-draw
openoffice.org3-base

were not marked as installed


EDIT: ohhhh, ok they weren't even there (these ones are from 3.2.1). And the most important ones as you mentioned were not among the first ones which is why i didn't see them. So the only "strange" thing is that the metapackage was not installed - which is not so strange but I would actually expect it to be.

---

### Post by snowpine on 2010-10-26
You can "trust" the Ubuntu repositories to contain exactly what they say they contain, no more no less. For example:

[http://packages.ubuntu.com/lucid/ubuntu-desktop](http://packages.ubuntu.com/lucid/ubuntu-desktop)

You'll see that if you're using Ubuntu Lucid, only the following OpenOffice components are installed by default (at version 3.2.0):

> openoffice.org-calc
    office productivity suite -- spreadsheet 

openoffice.org-gnome
    office productivity suite -- GNOME integration 

openoffice.org-help-en-us
    office productivity suite -- English_american help 

openoffice.org-impress
    office productivity suite -- presentation 

openoffice.org-math
    office productivity suite -- equation editor 

openoffice.org-style-human
    Human symbol style for OpenOffice.org 

openoffice.org-writer
    office productivity suite -- word processor 

If a new version of OpenOffice (or any other application) has come out since April 2010, it *will not be part of* the 10.04 release (10.04 = April 2010).

Note there are no packages starting with 'openoffice.org3' in a default Ubuntu install.

---

### Post by coffeecat on 2010-10-26
> **matteosistisette said:**
> So the only "strange" thing is that the metapackage was not installed - which is not so strange but I would actually expect it to be.

Not at all. The metapackage is for a more comprehensive install than comes as default. For example, openoffice.org-base is not included by default, but would be drawn in by the metapackage. The default install is limited to the three main modules, plus necessary dependencies, language packs, thesauri, etc, probably for reasons of  space  on the install CD, but the extras are easily installed if you need them.

---

### Post by 3Miro on 2010-10-26
> **snowpine said:**
> 
If a new version of OpenOffice (or any other application) has come out since April 2010, it *will not be part of* the 10.04 release (10.04 = April 2010).


Correct. And also, even if something came out in April or even March, it may not be in the repos at launch time. Depending on the what it is and if there are possible issues, it may be delayed for further testing. This is dependent on the distro, Ubuntu in my opinion is about as balanced between new and stable as it can be. If you want something very cutting edge, then Arch is a good example, however, with Arch, one also understands the meaning of the word "bleeding edge". CentOS on the other hand is probably the worst example of conservatism, they are rock solid in terms of stability, however, pretty much everything they offer is already obsolete.

---

### Post by snowpine on 2010-10-26
> **3Miro said:**
> CentOS on the other hand is probably the worst example of conservatism, they are rock solid in terms of stability, however, pretty much everything they offer is already obsolete.

I use CentOS on my work desktop, so I'd have to respectfully disagree with that statement. :) CentOS 5.5 has Firefox 3.6 and OpenOffice 3.x in its repos, and that's all I really need to get the job done. Anything else I need is available at repositories like RPM Forge, Planet CCRMA, etc. And KDE 3.5 is "rock solid" but definitely not "obsolete"! ;)

Furthermore there is a new CentOS release (based on RHEL6) coming in the next few months that will be on par with Ubuntu 10.04 in terms of age of packages.

---

### Post by Hagar Delest on 2010-10-26
If you want the latest version, you can use the one provided by the team itself, i.e. the OOo web site for OOo, Mozilla web site for FF and TB, ...

Quite easy with FF and TB since they are delivered as tarballs that just need to be extracted and that's all. For OOo, see [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

At worst, you've to compile the application (had to do that for Grisbi in Lucid IIRC).

---

### Post by 3Miro on 2010-10-26
> **snowpine said:**
> I use CentOS on my work desktop, so I'd have to respectfully disagree with that statement. :) CentOS 5.5 has Firefox 3.6 and OpenOffice 3.x in its repos, and that's all I really need to get the job done. Anything else I need is available at repositories like RPM Forge, Planet CCRMA, etc. And KDE 3.5 is "rock solid" but definitely not "obsolete"! ;)


I am surprised by OO and FF. Are those the official repos or something like an unofficial ppa (I don't know what the yum alternative is called). Currently we are at KDE 4.5 and while 3.5 still works, I feel pretty safe in delcaring it obsolete (despite the fact that depending on the hardware 3.5 may work better than 4.5). CentOS kernel is also several iterations behind. I will have to take another look, maybe I have overestimated how behind they are.

I don't mean to bash CentOS, I think they are right in doing what they are doing. They have a specific goal in mind and they are great at achieving it, it is just that I will not put it on a computer that I intend to use for anything other than strict work.

---

