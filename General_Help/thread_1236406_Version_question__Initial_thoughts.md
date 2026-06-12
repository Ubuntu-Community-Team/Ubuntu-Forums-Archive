---
title: "Version question / Initial thoughts"
date: 2009-08-10
forum: General Help
---

### Post by gmclella on 2009-08-10
So I've been using 8.04 Hardy Heron for about a week now and I have to say that so far I like what I see. Installation was a breeze and I was surprised at how well it played with my home network and my other XP OS. The only thing I had to do was set up my network printer which was fairly intuitive. 
 
I decided to go with 8.04 because I've read that the LTS is the most stable version to go with and noticed that some people were having issues with 8.10 / 9.04. 
 
My biggest gripe so far is that the Synaptic Package Manager doesn't seem to be updated that often. From what I see on the forums it may be some time (or never) for things like Firefox 3.5.2 to become available. This concerns me. As I see it there are two options:
1. Upgrade/Clean Install to 8.10 or 9.04 to get access to the latest and greatest and deal with the known bugs, and of course the unknown. I've read a few testimonials that discourage me from doing this.
2. Mess with 8.04 to get the latest versions of these apps working. In doing so, do I risk making 8.04 unstable?
 
Not sure which route to go. I suppose using VMWare and testing both of the options would probably be wise. I don't mind tinkering but also want a stable environment where I don't want to have to reinstall every month either. 
 
Thoughts?

---

### Post by mikewhatever on 2009-08-10
> **gmclella said:**
> 
 
I decided to go with 8.04 because I've read that the LTS is the most stable version to go with and noticed that some people were having issues with 8.10 / 9.04. 

That's not true. LST is just that. long turm support. and nothing else. A lot of people were having issues with 8.04 when it came out. There used to be a 100 pages long thread titled 'Hardy, the worst release ever' with people whining and ranting like crazy. In fact, Jaunty-9.04 was the only release that hadn't received such a welcome.
 
> My biggest gripe so far is that the Synaptic Package Manager doesn't seem to be updated that often. From what I see on the forums it may be some time (or never) for things like Firefox 3.5.2 to become available. This concerns me. As I see it there are two options:
1. Upgrade/Clean Install to 8.10 or 9.04 to get access to the latest and greatest and deal with the known bugs, and of course the unknown. I've read a few testimonials that discourage me from doing this.
2. Mess with 8.04 to get the latest versions of these apps working. In doing so, do I risk making 8.04 unstable?

That's the way Ubuntu does it. Instead of upgrading individual packages as in a rolling release distro (Arch, PCLinux), new releases are issued every 6 months. I'd suggest using Jaunty, unless you have reasons to stay with Hardy.

---

### Post by snowpine on 2009-08-10
Hi Gmclella, the target audience for an LTS release is someone who wants stability above all else and does not need the latest applications as soon as they come out. In other words someone who thinks FF 3.0.x still works just fine. :) Older versions of applications don`t suddenly stop working as soon as a new version comes out. 8.04 Hardy Heron will be fully supported and functional through April 2011.

That being said, you can get newer versions of selected applications by adding the hardy-backports repository.  

[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports) 

I also encourage you not to be scared of using the current version (9.04). If you are worried it will be buggy, give the Live CD a try and see for yourself...

ps FF 3.5 won`t be the default browser until 9.10 Karmic...

---

### Post by gmclella on 2009-08-10
> **mikewhatever said:**
> That's not true. LST is just that. long turm support. and nothing else. A lot of people were having issues with 8.04 when it came out. There used to be a 100 pages long thread titled 'Hardy, the worst release ever' with people whining and ranting like crazy. In fact, Jaunty-9.04 was the only release that hadn't received such a welcome.
 
Interesting.   I had no idea 8.04 had that reaction.   
 
The reason I thought the LST was more stable was because of the Ubuntu Pocket Guide and Reference book that is linked to somewhere in the forums.  It states that the LTS is " designed to be stable and reliable, so is the logical choice.   Non-LTS releases are used to experiment with new features and software, so can be unpredictable and even buggy."

---

### Post by snowpine on 2009-08-10
> **gmclella said:**
> Interesting.   I had no idea 8.04 had that reaction.   
 
The reason I thought the LST was more stable was because of the Ubuntu Pocket Guide and Reference book that is linked to somewhere in the forums.  It states that the LTS is " designed to be stable and reliable, so is the logical choice.   Non-LTS releases are used to experiment with new features and software, so can be unpredictable and even buggy."

All Ubuntu releases are created more or less equal. The LTS releases *become* more stable because they are `in the wild` receiving security patches and bug fixes for twice as long. In other words, if you choose 8.04 over 9.04, you`re choosing a release that`s been around an extra year. (It also means your application versions are a year older.)

---

### Post by gmclella on 2009-08-10
> **snowpine said:**
> Hi Gmclella, the target audience for an LTS release is someone who wants stability above all else and does not need the latest applications as soon as they come out. In other words someone who thinks FF 3.0.x still works just fine. :) 
I'm starting to realize that I'm not in the target audience!! I don't mind sacrificing some stability for the latest applications. I was already using FF 3.5 on XP and don't like going backwards.
 
> **snowpine said:**
>  
That being said, you can get newer versions of selected applications by adding the hardy-backports repository. 
 
[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports) 
 
Interesting, I'll take a look at this but I think I might also take your suggestion and try 9.04 on Live CD to see how it does on my setup. 
 
> **snowpine said:**
>  ps FF 3.5 won`t be the default browser until 9.10 Karmic...
It won't be the default until 9.10 but isn't a package available as an upgrade in 9.04?

---

### Post by snowpine on 2009-08-10
> **gmclella said:**
> It won't be the default until 9.10 but isn't a package available as an upgrade in 9.04?

Correct: sudo apt-get install firefox-3.5

It is code named Shiretoko.

---

### Post by gmclella on 2009-08-10
Backports seems like a great thing however I looked at the package listing for 8.04 and there seems to be a few nice to haves missing like Open Office 3.0 and Firefox 3.5. 
 
I came across a method to easily upgrade OO to 3.0 and have seen some for FF too, although a bit more complicated. Perhaps Jaunty is calling my name.
 
Maybe this is my old Windows mentality coming through but I tend to be afraid of installing too much. With XP, I remember how fast it seemed after a clean install. I also remember how badly it starts chugging after installing a few basic apps. It just starts to feel so bloated on my setup. 
I think I'm afraid to do the same to my clean install of 8.04 and make it not so hardy.

---

### Post by CatKiller on 2009-08-10
> **gmclella said:**
>  My biggest gripe so far is that the Synaptic Package Manager doesn't seem to be updated that often.

As has been pointed out already, this is policy. Each release will get bugfixes and security updates as long as that release is supported. You're not running out-of-date software, since bugfixes are ported to the stable versions. You don't have to be running Firefox 3.5 to get all the bugfixes that happened between the release of 3.0 and the release of 3.5. They will be applied through the Update Manager regardless.

New updates that add features or change behaviour are excluded. They will come out with the next release so that they may be more thoroughly tested before deployment.

There are some high-profile exceptions, such as Firefox 3.5 being available for Jaunty, but the process I outlined above is the general approach. Even then you can run Firefox 3.0 and Firefox 3.5 side-by-side.

> **gmclella said:**
>  Maybe this is my old Windows mentality coming through but I tend to be afraid of installing too much. With XP, I remember how fast it seemed after a clean install. I also remember how badly it starts chugging after installing a few basic apps. It just starts to feel so bloated on my setup. 

That is entirely your Windows mentality, and is something that you will have to overcome. When you install something in Windows, it will add some entries to the registry, which is a monolithic binary structure.  For every new application that you install, their registry entries take up resources *even if that application isn't running*, since the registry has to be read for any of them.

Ubuntu has nothing like this. Aside from hard drive space, installed applications will only affect resources *while they are running*. I could install a million applications and Ubuntu would run each one just as well as if it were the only application installed, since the others have no impact. If I were to install a million applications in Windows, all of them would suffer from the overhead of the others.

---

### Post by gmclella on 2009-08-10
> **CatKiller said:**
> As has been pointed out already, this is policy. Each release will get bugfixes and security updates as long as that release is supported. You're not running out-of-date software, since bugfixes are ported to the stable versions. You don't have to be running Firefox 3.5 to get all the bugfixes that happened between the release of 3.0 and the release of 3.5. They will be applied through the Update Manager regardless.
I totally understand this. It's not that the software is out of date but it's just not the most recent feature set. What I'm wondering is if I install an application that is not available in the Package Manager does it compromise the system? Is this something I should be concerned about doing or is it highly unlikely installing Open Office 3.0 or Firefox 3.5 for example would FAIL 8.04.  Am I best to just install 9.04 or upgrade if it works on my setup?
 
> **CatKiller said:**
> 
That is entirely your Windows mentality, and is something that you will have to overcome. When you install something in Windows, it will add some entries to the registry, which is a monolithic binary structure. For every new application that you install, their registry entries take up resources *even if that application isn't running*, since the registry has to be read for any of them.
 
Ubuntu has nothing like this. Aside from hard drive space, installed applications will only affect resources *while they are running*. I could install a million applications and Ubuntu would run each one just as well as if it were the only application installed, since the others have no impact. If I were to install a million applications in Windows, all of them would suffer from the overhead of the others.
 
Thanks CatKiller, that's good to know. Makes me feel better about installing things and trying them out. I used to look at the packages available to install and in the back of my mind I could see my resources slipping away or remnants being left behind after uninstalling.

---

### Post by CatKiller on 2009-08-10
> **gmclella said:**
> I totally understand this. It's not that the software is out of date but it's just not the most recent feature set. What I'm wondering is if I install an application that is not available in the Package Manager does it compromise the system? Is this something I should be concerned about doing or is it highly unlikely installing Open Office 3.0 or Firefox 3.5 for example would FAIL 8.04.  Am I best to just install 9.04 or upgrade if it works on my setup?

New features are over-rated :)

It's generally advisable that if you want the latest features that you should run the latest Ubuntu release. The group of packages that are together in each release are tested together as a group after feature-freeze. Upgrading a bunch of things may bring in dependency problems, and newer versions of libraries may cause subtle problems with the older packages.

The LTS releases are for people that don't want things to suddenly break. The software that is working will continue to work for three years, and at some point during those three years they can upgrade to the next LTS. There may need to be some reconfiguration at the point of upgrade, but once it's all working again it will continue to work for another three years.

The intermediate releases are for those that want newer features, but want them to be tested. The software that is working will continue to work for 18 months, and at some point during those 18 months they can upgrade to the next version (some people still ran Feisty for quite some time after Gutsy was released, and some people are still running Intrepid now). There may need to be some reconfiguration at the point of upgrade, and if you're always running the latest version, you may find that you're reconfiguring things every 6 months.

If you absolutely have to have all the features all the time, and you don't want to run a distro that does rolling releases, you can help the community by alpha-testing the new releases. Things will suddenly break, but your pain will prevent other users experiencing the same pain come release day.

As an intermediate step between running the latest release and alpha-testing the next release, you can run backports and project-specific repositories. Backports are versions that will be included in the next version that have been tested for the current version too. It is quite rare for packages to be back-ported and is done by request. This is normally for serious problems with a package from the previous release where the bugfix is tied to new features. The fact that the version of Amarok that shipped with Jaunty failed to scrobble in some cases, with the fix being part of the overhaul of the Last.FM support, is an example of this. The version that's in the jaunty-backports repository has this fix and the new features.

Project-specific repositories are exactly as they sound; a repository maintained by a project for ease of use by users of that project. They may be hosted on servers controlled by that project, or they may be hosted on Launchpad as PPAs. The Wine project, for example, has a repository containing the latest experimental versions for those who don't want to just be running the latest stable version. You can also use third-party repositories for packages that aren't included in the Ubuntu repositories at all, generally because the projects are young and in a state of flux, so the packages don't have the stability required to be included in a release. The AWN plugins are an example of this, as was Kiba dock. The various versions of Compiz counted, too, until everything had settled down. Now they are in a position that they can be included in the official repositories and installed by default.

Personally, I run the latest release and have backports and some selected third-party repositories enabled (Wine and Medibuntu) for newer versions. But that's because I like fixing things even though I don't want everything to break at once. Where a given user's comfort area between stability and newer features resides depends entirely on that user.

Oh, and you should **always** use the package manager. At least, where you can. It is possible to compile your own programs, or to install from scripts, but the package manager is a tremendous labour-saving tool. You should only use another method if you are perfectly comfortable doing it all yourself. Including keeping the software that you've installed yourself up to date.

From what you've said so far, it seems like you'd be most happy running the latest release of Ubuntu, getting the benefit of the alpha testing without having to do it yourself. This gives you a good balance between stability and new features.

There are rolling-release distributions available (some have already been mentioned in this thread), and you may well find that you like that approach. You may also find that you really enjoy doing everything yourself, once you're more experienced, in which case something like [Gentoo]("http://en.wikipedia.org/wiki/Gentoo") might appeal (you have to compile everything yourself, which means you can tweak it to your liking, but there is still package management available. The packages are source code, rather than pre-compiled binaries).

Whichever approach you decide to try, I wish you luck with your efforts.

---

