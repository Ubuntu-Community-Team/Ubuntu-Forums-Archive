---
title: "Install LibreOffice 3.6.1 in 12.04.1?"
date: 2012-09-27
forum: General Help
---

### Post by AleveSicofante on 2012-09-27
I've read the latest LibreOffice incarnation does have native support for the global menu and it's currently available in 12.10 beta.

Is there any way I can install that version in 12.04.1?

---

### Post by Sonsum on 2012-09-27
> **AleveSicofante said:**
> I've read the latest LibreOffice incarnation does have native support for the global menu and it's currently available in 12.10 beta.

Is there any way I can install that version in 12.04.1?

I installed it on my 12.04.1 install using [this ppa]("https://launchpad.net/~libreoffice/+archive/ppa")

---

### Post by snowpine on 2012-09-27
You can always find the latest Libreoffice, for any operating system, here: [http://www.libreoffice.org/](http://www.libreoffice.org/)

However, a better way (in my opinion, because it will be added to your software sources and you'll get updates through your update manager) is to install it through a PPA as described here: [https://launchpad.net/~libreoffice/+archive/ppa](https://launchpad.net/~libreoffice/+archive/ppa)

Looking at this page I see that they do indeed have 3.6.1 packaged for 12.04. :)

---

### Post by AleveSicofante on 2012-09-27
Installing from the official download page is out of the question. It doesn't download a simple .deb, it downloads a thousand of them and there's a complex procedure to do the installation (I don't quite understand why, but that's how it is).

I'm using the PPA, but even when its webpage says the latest version is 3.6.1-rc2 (meaning NOT the final version anyway), I only get 3.6.02 via Synaptic. :confused:

@Somsun: can you please check in Help->About what's your installed version?

---

### Post by snowpine on 2012-09-27
> **AleveSicofante said:**
> Installing from the official download page is out of the question. It doesn't download a simple .deb, it downloads a thousand of them and there's a complex procedure to do the installation (I don't quite understand why, but that's how it is).

In my opinion, you need to outgrow this "Windows way" of thinking. Linux is "open source" which means we always have the freedom to download and compile an application from its developers. Yes, this requires that you learn new software tools and commands, but it is so worth it in the long run, because it means you, the user, will have complete freedom and control over your system.

Now, that being said, I agree the PPA method is easier, which is why I recommended it for you. If you check the link I posted above, you can see for yourself that the latest for Precise is 1:3.6.1~rc2-1ubuntu3~precise1 uploaded Sept. 3rd. You can also check this on your computer with:

```
apt-cache policy libreoffice
```

This command will show you which version you have installed, compared with the version(s) available in your repos.

---

### Post by Sonsum on 2012-09-27
> **AleveSicofante said:**
> Installing from the official download page is out of the question. It doesn't download a simple .deb, it downloads a thousand of them and there's a complex procedure to do the installation (I don't quite understand why, but that's how it is).

I'm using the PPA, but even when its webpage says the latest version is 3.6.1-rc2 (meaning NOT the final version anyway), I only get 3.6.02 via Synaptic. :confused:

@Somsun: can you please check in Help->About what's your installed version?

I also have 3.6.02. It's the most updated version I've found. I thought it had the default app menu, but you still might need to install "libreoffice-gtk3", because I have that installed too.

---

### Post by AleveSicofante on 2012-09-27
I'm not turning this into a discussion of how good or bad open source vs windows is, etc., etc., etc. I said installing from the download page is out of the question for good reasons, so please don't insist. (Compiling is like lightyears away out of the question).

Here's the output of the command you suggested:

```
aleve@MacBook:~$ apt-cache policy libreoffice
libreoffice:
  Instalados: (ninguno)
  Candidato:  1:3.6.0~rc4-0ubuntu3~ppa1~precise1
  Tabla de versión:
     1:3.6.0~rc4-0ubuntu3~ppa1~precise1 0
        500 http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ precise/main i386 Packages
     1:3.5.4-0ubuntu1.1 0
        500 http://es.archive.ubuntu.com/ubuntu/ precise-updates/main i386 Packages
        500 http://security.ubuntu.com/ubuntu/ precise-security/main i386 Packages
     1:3.5.2-2ubuntu1 0
        500 http://es.archive.ubuntu.com/ubuntu/ precise/main i386 Packages
aleve@MacBook:~$ 

```

I'm in Spain, hence the es.archive.ubuntu.com and the Spanish language output.

I'm running Ubuntu on a MacbookPro1,1 (that's 32 bits only, just in case this means something).

Latest kernel update (3.2.0-31-generic-pae) doesn't boot, so I'm booting from 3.2.0-29-generic-pae.

---

### Post by Sonsum on 2012-09-27
> **snowpine said:**
> In my opinion, you need to outgrow this "Windows way" of thinking. Linux is "open source" which means we always have the freedom to download and compile an application from its developers. Yes, this requires that you learn new software tools and commands, but it is so worth it in the long run, because it means you, the user, will have complete freedom and control over your system.

Now, that being said, I agree the PPA method is easier, which is why I recommended it for you. If you check the link I posted above, you can see for yourself that the latest for Precise is 1:3.6.1~rc2-1ubuntu3~precise1 uploaded Sept. 3rd. You can also check this on your computer with:

```
apt-cache policy libreoffice
```

This command will show you which version you have installed, compared with the version(s) available in your repos.

1:3.6.1~rc2-1ubuntu3~precise1 is listed as the latest version, but if you look, it says that libreoffice failed to build on AMD64. 64 bit users (like me) still only get 3.6.0-rc4

EDIT: It also appears that the i386 build was cancelled if you view the package details for libreoffice. That would explain 32 and 64 bit both having the problem.

---

### Post by snowpine on 2012-09-27
> **Sonsum said:**
> 1:3.6.1~rc2-1ubuntu3~precise1 is listed as the latest version, but if you look, it says that libreoffice failed to build on AMD64. 64 bit users (like me) still only get 3.6.0-rc4

Thanks for the clarification (I didn't read that far) so I guess that answers the OP's question. :)

---

### Post by snowpine on 2012-09-27
> **AleveSicofante said:**
> I'm not turning this into a discussion of how good or bad open source vs windows is, etc., etc., etc. I said installing from the download page is out of the question for good reasons, so please don't insist. (Compiling is like lightyears away out of the question).

Then you will have to wait for someone (PPA maintainers, perhaps?) to do it for you. Sorry but if you don't want to learn new skills, that's the best answer I can give you.

---

### Post by vasa1 on 2012-09-27
> **snowpine said:**
> ... Yes, this requires that you learn new software tools and commands, but it is so worth it in the long run, because it means you, the user, will have complete freedom and control over your system.
...
In this specific instance, there really aren't any new tools involved. The readmes that come with the archived package are fairly straightforward. But I don't think that the version from the official download site will have the global menu and other integration with Unity that the ppa will provide.

If OP intends to upgrade to 12.10 in just a month's time, LibreOffice 3.6 will be part of the upgrade.

---

### Post by snowpine on 2012-09-27
Not a Unity user so I completely missed that part of the question, I'm going to stop talking now before I embarrass myself further. :)

---

### Post by Sonsum on 2012-09-27
If I remember right, installing the debs from the site isn't too bad, but everything is branded like "3.6-libreoffice", preventing the possibility of future ubuntu repo updates. 

Unless I'm wrong, compiling might do the same.

---

### Post by snowpine on 2012-09-27
It's been years since I did it (I'm not a "latest & greatest" type of guy) but IIRC it's as simple as:

```
sudo dpkg -i ~/Downloads/libreoffice/*.deb
```

---

### Post by vasa1 on 2012-09-27
> **Sonsum said:**
> If I remember right, installing the debs from the site isn't too bad, but everything is branded like "3.6-libreoffice", preventing the possibility of future ubuntu repo updates. 

Unless I'm wrong, compiling might do the same.

Yes, if one installs from the official site, then one has to continue doing so... or totally uninstall and then get it from the repos.

(I don't know that we need to consider compiling in this particular case.)

---

### Post by AleveSicofante on 2012-09-27
> **snowpine said:**
> Then you will have to wait for someone (PPA maintainers, perhaps?) to do it for you. Sorry but if you don't want to learn new skills, that's the best answer I can give you.

I have all those skills. Don't make assumptions so fast. Just stop lecturing people and stay on topic, will you? Thanks for you understanding.

---

### Post by AleveSicofante on 2012-09-27
> **vasa1 said:**
> If OP intends to upgrade to 12.10 in just a month's time, LibreOffice 3.6 will be part of the upgrade.
No. I'm staying on LTSs. I'm just checking the viability of a consistent Unity experience for my customers in the long term. Having local menus in one of the main apps and global menus on the rest is not acceptable. The global menu is good for my use case.

---

### Post by AleveSicofante on 2012-09-27
> **Sonsum said:**
> I also have 3.6.02. It's the most updated version I've found. I thought it had the default app menu, but you still might need to install "libreoffice-gtk3", because I have that installed too.

Installed that package. Nothing's changed.

So you do have native global menus on 12.04.1 and LO 3.6.02? No lo-menubar installed?

---

### Post by AleveSicofante on 2012-09-27
> **Sonsum said:**
> 1:3.6.1~rc2-1ubuntu3~precise1 is listed as the latest version, but** if you look**, it says that libreoffice failed to build on AMD64. 64 bit users (like me) still only get 3.6.0-rc4

EDIT: It also appears that the i386 build was cancelled if you view the package details for libreoffice. That would explain 32 and 64 bit both having the problem.

Sorry, where do you "look" those explanations about the latest version not compiling?

Just out curiosity, if they don't compile, is there a reason why they are listed at all as available in the PPA?

---

### Post by snowpine on 2012-09-27
> **AleveSicofante said:**
> I have all those skills. Don't make assumptions so fast. Just stop lecturing people and stay on topic, will you? Thanks for you understanding.

I believe my answer "2 possible sources for updated LibreOffice include the Launchpad LibreOffice PPA and/or libreoffice.org" was entirely on topic. Apologies if I underestimated your Linux experience, and as I stated earlier, apologies that I misunderstood part of your question since I am not a Unity user.

To be fair, if you had actually stated your goal ("I'm just checking the viability of a consistent Unity experience for my customers in the long term.") in your first post, perhaps I could have given you a more relevant answer.

---

### Post by AleveSicofante on 2012-09-27
> **snowpine said:**
> To be fair, if you had actually stated your goal ("I'm just checking the viability of a consistent Unity experience for my customers in the long term.") in your first post, perhaps I could have given you a more relevant answer.

Oh, dear... My first post is perfectly clear and states all the relevant issues. Check it again.

---

### Post by snowpine on 2012-09-27
> **AleveSicofante said:**
> Oh, dear... My first post is perfectly clear and states all the relevant issues. Check it again.

I would have given a completely different answer if I'd known you were managing installs for many clients as opposed to just upgrading LibreOffice on your own personal computer. Saying "snowpine, your (seemingly very reasonable) suggestion is completely out of the question (but I won't tell you why)" seems disrespectful considering I am volunteering my time to help you. Perhaps a language barrier and we are simply misunderstanding each other, it was not my intention to "lecture" you. :)

---

### Post by Sonsum on 2012-09-29
> **AleveSicofante said:**
> Installed that package. Nothing's changed.

So you do have native global menus on 12.04.1 and LO 3.6.02? No lo-menubar installed?

Apparently, I do have lo-menubar? Does this come with Ubuntu 12.04.1? I certainly didn't install it myself (I run Gnome Classic).

---

### Post by vasa1 on 2012-09-29
> **Sonsum said:**
> Apparently, I do have lo-menubar? Does this come with Ubuntu 12.04.1? I certainly didn't install it myself (I run Gnome Classic).
lo-menubar should no longer be necessary in the LibreOffice 3.6.x / Ubuntu 12.10 (Unity) scenario. I would think that 12.10 or 12.04 with other DEs aren't OP's issue. I feel that lo-menubar has to be installed. I don't think it's there by default.

AFAIK, lo-menubar was buggy and I don't know whether any attention will be paid to fixing it although 12.04 is LTS and a lot of people would benefit.

OP: could you clarify what I feel is an inconsistency? You say that you're setting up LibreOffice for your clients. That I presume is "a production environment". My question: shouldn't you be staying with 3.5.x for a while longer? Or is 3.6.x being recommended for a "production environment"? The last time I looked, it wasn't.

---

### Post by JADAVIA on 2012-11-01
[color=red]> **alevesicofante said:**
> i've read the latest libreoffice :guitar:incarnation does have native support for the global menu and it's currently available in 12.10 beta.

Is there any way i can install that version in 12.04.1?[/color] [color=red]
[/color] ):p

---

### Post by zerubbabel on 2012-12-10
I am puzzled. The web page for the LibreOffice [ppa]("https://launchpad.net/~libreoffice/+archive/ppa") shows that version 3.6.4 has been successfully built, but it's still not available via the Kubuntu package manager, even though I have that ppa included in my software sources. Why is that?

---

### Post by AleveSicofante on 2012-12-11
> **vasa1 said:**
> OP: could you clarify what I feel is an inconsistency? You say that you're setting up LibreOffice for your clients. That I presume is "a production environment". My question: shouldn't you be staying with 3.5.x for a while longer? Or is 3.6.x being recommended for a "production environment"? The last time I looked, it wasn't.

I already explained tha problem with consistency: global menus in most apps, local menus in LibreOffice.

3.6 is ready for production since its first release. Only betas are not ready for production.

We're on 3.6.4 already, which fixes dozens of bugs since 3.6.0, and LTS users are stuck on 3.6.02 at most. And no, 3.5 versions don't have those bugs magically fixed either. There's no point in using old versions of LibreOffice expecting them to me more "stable". New versions exist not just for providing new features, but to fix bugs too. That's why LTS users need the last available version. Besides, the newer features are useful as well. No one can reasonably expect a team of office workers to stay on LibreOffice 3.6.0.2 for five years.

I find it unacceptable that LTS users have to stay on old applications releases, especially such important ones as an office suite. App updates should be independent from system updates. Yes, I know all about shared libraries and whatnot, but I insist: the app management system should be redesigned so users of LTS releases aren't stuck with old versions of apps. (There are more than one packagement solutions out there that completely avoid the shared libraries issue: OS X, Gobolinux and probably others do it the right way.) Again, this is completely unacceptable.

To the maintainers of the PPA: What's so hard about making the  newer versions working with 12.04? What's exactly preventing you guys from keeping 3.6.02+ versions from entering the Precise repository?

---

### Post by snowpine on 2012-12-11
No no no, you understand it backwards. :) Nobody is saying "LTS users have to stay on old applications releases, especially such important ones as an office suite." Rather, we are saying *the community demands that* "The 'LTS' (long term support) designation is a promise from Canonical/Ubuntu that they shall not upgrade applications mid-release, especially such important ones as an office suite."

In other words, there is a **need** for a stable platform with no unscheduled major changes. It is all about giving power back to the user/admin, as opposed to a "top down" structure where a corporate entity dictates which is the "correct" version for all users' needs. :)

---

### Post by AleveSicofante on 2012-12-11
It's you who understands it backwards. No one forces anyone to upgrade apps. It's just Ubuntu who forces LTS users to stay on old apps. You don't have that problem when using Windows or OS X. I'd say this is bug number 1 on Ubuntu.

I don't know about "the community" but I definitely know about "the common sense no-fan-boy admin" for small businesses. Ask them to stay on old applications for five years and they will lough out loud at you.

Let alone simple users who want system stability ALONG with apps stability. It's the terrible idea of sharing libraries in 2012 what prevents secure and stable updates to apps while keeping the most stable system.

The only reason I stay on 12.04 is that they promised they'll keep updating the kernel (so your system will indeed undergo major changes along the way), unlike older LTSs which would stop at a certain kernel version. Now it's time to guarantee stable apps will be kept up to date too.

---

### Post by snowpine on 2012-12-11
> **AleveSicofante said:**
> It's you who understands it backwards. No one forces anyone to upgrade apps. It's just Ubuntu who forces LTS users to stay on old apps. You don't have that problem when using Windows or OS X. I'd say this is bug number 1 on Ubuntu.

I don't know about "the community" but I definitely know about "the common sense no-fan-boy admin" for small businesses. Ask them to stay on old applications for five years and they will lough out loud at you.

Let alone simple users who want system stability ALONG with apps stability. It's the terrible idea of sharing libraries in 2012 what prevents secure and stable updates to apps while keeping the most stable system.

The only reason I stay on 12.04 is that they promised they'll keep updating the kernel (so your system will indeed undergo major changes along the way), unlike older LTSs which would stop at a certain kernel version. Now it's time to guarantee stable apps will be kept up to date too.

Sorry to say you have misunderstood several of Ubuntu's core features (giving **choice** to the user/admin, unified package management, shared libraries, and the LTS release cycle). I completely understand & respect what you are saying, but what you describe has never been Ubuntu's business model. For your specific needs, I think you would be happiest with Windows or a "rolling release" Linux such as Arch.

---

### Post by AleveSicofante on 2012-12-11
Snowpine: really, STOP it. I kindly beg you stay out of this  conversation. Every comment coming from you is simply trying to  "illustrate" us poor ordinary humans about the nature of the glorified  Linux "principles". I know them, most of us know them. And most of us  people from the real world are fed up with them too. Canonical has  understood that and already keeps updating some of the apps in LTSs  (like Firefox and Thunderbird) and now the kernel. It's only logical they keep LibreOffice up to date too.

Canonical is slowly coming to terms  with the real world, which is part of the road to becoming a relevant  desktop operating system. Canonical/Ubuntu is targetting ME, not YOU. You nerds can stay on Gentoo, Slackware and  all that "pureness".

Again: I know where you're coming from and I'm fine with "your world", it's just not most of the population's world. Now, since you're completely unable to understand ordinary people needs, I urge you again to leave the conversation, so it can become constructive and I'm not stuck replying to you the obvious again and again, which is honestly very tiring.

To the rest of the readers: I just asked the LibreOffice PPA team if they plan to update the PPA to take the new versions of LibreOffice to 12.04 AND if they plan a stable 3.6 series PPA like the ones they maintain for 3.4 and 3.5.

---

### Post by AleveSicofante on 2012-12-11
Just to let everybody know, here's a quick briefing of the reply to my question to the LibreOffice PPA team:

"The menubar integration depends on various changes in the unity stack that
are unlikely to be backported to 12.04 in addition."

and


"A 3.6 ppa will be opened soon. It will certainly be there before the first 4.0
backports hit:

 [https://launchpad.net/~libreoffice/+archive/ppa]("https://launchpad.net/%7Elibreoffice/+archive/ppa")

sometime in February 2013. Before 4.0 prereleases will hit:

 [https://launchpad.net/~libreoffice/+archive/libreoffice-prereleases/+packages]("https://launchpad.net/%7Elibreoffice/+archive/libreoffice-prereleases/+packages")

(and the raring development release)."

Whether that PPA will be available to 12.04 users or not, is still an open question. I've been redirected to [email]libreoffice@lists.launchpad.net[/email] where I'll ask more questions about the issue.

---

