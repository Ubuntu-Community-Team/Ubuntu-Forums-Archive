---
title: "Depency Hell"
date: 2010-03-29
forum: General Help
---

### Post by qemqemqem on 2010-03-29
I think I am having "dependency hell".  I don't know how to resolve it, although I think the answer must be simple.

I need to install package "gnome".  But I get this error

>   gnome: Depends: epiphany-extensions but it is not going to be installed

Installing epiphany-extensions uninstalls swfdec-mozilla, so that when I try again to install gnome, I get:

>   gnome: Depends: swfdec-mozilla but it is not going to be installed

Installing swfdec-mozilla uninstalls epiphany-extensions.

I am using Gnome on Lucid, although this problem has existed since Karmic.  I can post anything to help diagnose the problem.  I've tried using apt-get, dpkg, aptitude, and synaptic, but I have had no luck.  Does anyone know of a command that would fix this?

---

### Post by nothingspecial on 2010-03-29
I don`t know how to fix this but when I found myself in a similar, albeit, different situation (mine was each package depending on the other).

The solution was to download both .debs from packages.ubuntu.com and doing a ```
sudo dpkg -i *.deb
```

Worth a go.

---

### Post by andre_merzky on 2010-05-22
Alas, force-installing both conflicting .deb packages does not help - the package managers still complain when later trying to install gnome.  According to 'dpkg -redepends', gnome directly depends on the epiphany-extensions *AND* swfdec-mozilla, which seem not be able to coexist.

I find it very frustrating that kubuntu, as direct derivate of ubuntu, is not able to install gnome...  That should have been one of the first regression tests...

If anybody finds a solution to this, which does not include downloading/installing all gnome packages manually, i'd be interested to hear that...

Thanks, A.

---

### Post by warfacegod on 2010-05-22
```
sudo apt-get install ubuntu-desktop
```

That should get you gnome if anything will.

---

### Post by QLee on 2010-05-22
Edit:  Big oops, I didn't check the date of OP and didn't notice that andre_merzky hijacked the thread with a question about Kubuntu, thus my answer to the OP is likely useless.


[QUOTE=qemqemqem]I think I am having "dependency hell".  I don't know how to resolve it, although I think the answer must be simple.

I need to install package "gnome".  But I get this error



Installing epiphany-extensions uninstalls swfdec-mozilla, so that when I try again to install gnome, I get:



Installing swfdec-mozilla uninstalls epiphany-extensions.

I am using Gnome on Lucid, although this problem has existed since Karmic.  I can post anything to help diagnose the problem.  I've tried using apt-get, dpkg, aptitude, and synaptic, but I have had no luck.  Does anyone know of a command that would fix this?[/QUOTE]

I don't follow what you are trying to accomplish. You wrote that you are using GNOME, but stated that you can't install the gnome package. Since the gnome package is a meta package to install standard distribution GNOME desktop environment to Debian and you are already using GNOME it isn't clear to me what purpose for trying that.

However, if you choose one of the available package managers which handles dependencies for you, you should be able to avoid "dependency  purgatory" You mentioned that you have tried all those package managers, perhaps it is time to post a step-by-step of the commands you entered and the errors encountered for one of them say, Synaptic, that way someone here may be able to point you in the right direction.

---

### Post by deertan on 2010-06-28
It's a bug reported here...

[https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/542404](https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/542404)

Which says it's resolved, but it's not, at least not in Ubuntu.  That might be a Debian bug report.


I used Synaptics to attempt to install the package "gnome" from KDE, and I get the same dependency problems described by OP.

I can and did install gnome-desktop-environment without problems, but that's just the base install of Gnome I think.

I want to be able to install Gnome with optional components, but cannot from Synaptic due to the following errors...

When attempting to install Gnome I get:


gnome:
 Depends: swfdec-mozilla but it is not going to be installed


So I manually install swfdec-mozilla.

Now I try to install Gnome with the following result...


gnome:
 Depends: epiphany-extensions but it is not going to be installed


So I manually install epiphany-extensions, which gets me this...


To be removed
   swfdec-mozilla

To be installed
   epiphany-browser


And if I say Okey Dokey, and then try to install gnome, I get...


gnome:
 Depends: swfdec-mozilla but it is not going to be installed


And that's dependency hell.  :)

---

### Post by phyzome on 2010-07-06
> **deertan said:**
> It's a bug reported here...

[https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/542404](https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/542404)

Which says it's resolved, but it's not, at least not in Ubuntu.  That might be a Debian bug report.

From the bug thread:

> Robert Wall  wrote on 2010-05-26:

This bug is fixed in the upstream Debian metapackage, which removed the swfdec depend and added a mozilla-plugin-gnash recommend.

It sounds like a fix has been committed, but not yet released to the repos.

---

### Post by phyzome on 2010-07-06
I grabbed the latest from here:

[https://launchpad.net/ubuntu/lucid/amd64/gnome/1:2.28+1ubuntu3](https://launchpad.net/ubuntu/lucid/amd64/gnome/1:2.28+1ubuntu3)

and used this script to alter the .deb:

[http://ubuntuforums.org/showpost.php?p=5585977&postcount=4](http://ubuntuforums.org/showpost.php?p=5585977&postcount=4)

I removed the swfdec-mozilla Depends and added the mozilla-plugin-gnash Recommends, as noted in the bug report.

Seems to work.

---

### Post by Lolpanda on 2010-07-06
I have no idae if this will work, and unfortunately I dont have an ubuntu machine around to test to see if that package exists

But try doing gnome-desktop-environment through synpatic, and then doing gnome-extras

Worth a shot if nothing else

---

### Post by blitux on 2010-07-27
It's still not solved. But doing:

```
sudo apt-get install ubuntu-desktop
``` 

...solved the issue. Now I have a fully functional ubuntu with gnome and stuff...

I was moving from xubuntu to ubuntu on the same pc.

---

### Post by josefnpat on 2011-03-23
Got this same problem. Easy workaround for me was to install the gnome-core package instead of gnome.

---

### Post by g2geo94 on 2012-08-27
(Mods, hear me out, I'm adding closure here)

Had a similar problem just now where I wanted to install up from 8.10 (quirky BIOS with crazy CD Drive means newer OS install disks won't load) so I installed 8.10 and followed the Update Manager to 10.10 with a rather, well, *broken* gnome install. Completing the steps here seems to have solved my problem, so I think it might be wise to mark this as solved so that others may find this thread and realize it is actually helpful and not just another lost hope.

Steps I used to solve my problem:
First, I of course went to the Synaptic Package Manager after finding I don't have all of the gnome tools, and simply typed "gnome". That gave the package by the same name. Tried installing, and here I am, in this "Dependency Hell". I look around on this thread, and here is how I solve the problem.

First, I tried installing gnome-desktop-environment, as suggested by Lolpanda. Didn't change much on appearance side, but did give me some of the missing tools.
Reboot.
Then I went down to blitux, tried his idea of > **blitux said:**
> ```
sudo apt-get install ubuntu-desktop
``` 

Reboot.
Log in and finally I have a full desktop environment.

This seems to be the needed solution.
-Geoffrey

---

