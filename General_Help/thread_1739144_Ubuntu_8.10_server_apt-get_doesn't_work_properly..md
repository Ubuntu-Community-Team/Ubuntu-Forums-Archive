---
title: "Ubuntu 8.10 server apt-get doesn't work properly."
date: 2011-04-25
forum: General Help
---

### Post by micael3000 on 2011-04-25
Hello,

I am trying to install some packages in a ubuntu 8.10 server, however, apt-get doesn't work (I get several 'not found' errors)...
Is there any way to do that?

I know this version is probably not supported anymore but I can't just format a customer server because it's OS is outdated...
I just can't put my sources.list on it because I am on ubuntu 10.10 and it would download updates for the wrong OS probably causing a huge damage on the old one.

Any help will be welcome :(

Thanks in advance!

---

### Post by lithopsian on 2011-04-25
> I can't just format a customer server because it's OS is outdatedYou don't have a lot of choice.  There are no Ubuntu repositories for this release so you won't be apt-getting very much.

You might be able to find repositories or debs elsewhere but I wouldn't hold your breath.  You might be able to install the packages you need from 8.04 (LTS, still just about supported) or 9.10 (not long now!) but you will probably have a lot of work to do to resolve dependencies.

Edit: I forgot about the archived repositories.  Those should work well if you just need to grab a package.

There is no longer an easy upgrade path from 8.10 and a reinstall would be safest.

---

### Post by snowpine on 2011-04-25
You are correct that all support has ended for the 8.10 release.

My recommendation is to install a currently-supported release (10.04 LTS is a good option) or upgrade using the ["end of life" instructions]("https://help.ubuntu.com/community/EOLUpgrades").

I understand however that this may not be an option if you are working on contract and it is not your server. In this case, you may edit /etc/apt/sources.list and change the mirrors to point to "old-releases" for example change:

```
deb http://archive.ubuntu.com/ubuntu/ intrepid main restricted
```

to:

```
deb http://old-releases.ubuntu.com/ubuntu/ intrepid main restricted
```

Then refresh your package list with "sudo apt-get update". This should allow you to install the appropriate (but no-longer-supported) packages from the end-of-life 8.10 repositories.

---

### Post by micael3000 on 2011-04-25
Allright, that is very, very, very sad... :(

As I have no alternative let me know... When a version reaches it's end (for instance, if 10.10 comes to it's final-day-support) is it updatable to another version?

I mean... Is there any way to update from version to version instead of formatting every time yours is running out of time?

(like 'apt-get install ubuntu-desktop' to turn a server into a desktop)

Thanks again!

---

### Post by lithopsian on 2011-04-25
It is a fairly simple task to upgrade from one version to the next.  Desktop Ubuntu even supplies a button to do this.  Upgrading from one release to anything except the next one is not recommended and not fully tested, hence the special instructions.

---

### Post by micael3000 on 2011-04-25
Ok...
So on servers it _**is**_ possible, right? (With no complication?)

@[snowpine]("http://ubuntuforums.org/member.php?u=479885")
Bingo! It worked out, apt-get now works fine... However, I am still not able to install the software I was looking for ('pcscd' has no installation candidate). I am going to search for deb packages. It shall work, I think...


1- I read [here]("http://www.brunocarlos.com/2008/04/27/como-fazer-upgrade-do-ubuntu-para-a-versao-804-lts/") (sorry it is in portuguese) that is possible to upgrade from versions with the CD of the next version.
So, I am working with the 8.10... Can I upgrade to 9.04 then 9.10, 10.04 and finally 10.10?

2- Will
> sudo do-release-upgrade
work for this version or just mess it all?


Thanks again! :popcorn:

---

### Post by micael3000 on 2011-04-25
bump :|

---

### Post by lithopsian on 2011-04-25
No difference between server and desktop.

You can upgrade relatively safely from one release to the next.  The recommended steps for you would be to change to the 9.04 repositories (archived since it isn't supported either!) and then do a dist-upgrade.  Everything would be upgraded to the 9.04 versions.  Then you can do the same thing to move to 9.10 (supported for a little while) and then again to 10.04.  With all those steps there is a definite chance something would go wrong and maybe need some fixing.

With a CD you don't upgrade, but you can install the Ubuntu release on the CD.  This is a much safer procedure but you won't have the same set of apps as you started with.  For example, if the default mail client in your version was Sylpheed but the mail client in the CD release was Evolution then you'd suddenly have Evolution.  Installing from a CD may also wipe al sorts of configuration changes that you've made to your system.

I wouldn't recommend using do-release-upgrade in your situation because it is non-standard and I don't know what would happen.  Anyway it is just a way to automate the steps of changing to the next repository version and running apt-get dist-upgrade.

Is it your responsibility to upgrade to a supported release?  Does the client want it done?

---

### Post by micael3000 on 2011-04-25
Not exactly... I am the programmer who made module for the system that will need an eToken to run... In order to install this eToken's software pcscd must be installed :P
I forwarded this topic to my superior and we will choose the options that best fit our situation.

Again, thanks [lithopsian]("http://ubuntuforums.org/member.php?u=1207106") and [snowpine]("http://ubuntuforums.org/member.php?u=479885")! GO Ubuntu! :-({|=

(Including for the post below :))

---

### Post by snowpine on 2011-04-25
> **micael3000 said:**
> 
@[snowpine]("http://ubuntuforums.org/member.php?u=479885")
Bingo! It worked out, apt-get now works fine... However, I am still not able to install the software I was looking for ('pcscd' has no installation candidate). I am going to search for deb packages. It shall work, I think...


I think pcscd is provided by pcsc-lite according to

[http://packages.ubuntu.com/source/hardy/pcsc-lite](http://packages.ubuntu.com/source/hardy/pcsc-lite)

---

### Post by low351 on 2012-02-24
@snowpine: Brilliant!  thanks Snowpine.  I needed to create a new install of a server that we have hosted to test changes and this helped immensely!

> **snowpine said:**
> You are correct that all support has ended for the 8.10 release.

My recommendation is to install a currently-supported release (10.04 LTS is a good option) or upgrade using the ["end of life" instructions]("https://help.ubuntu.com/community/EOLUpgrades").

I understand however that this may not be an option if you are working on contract and it is not your server. In this case, you may edit /etc/apt/sources.list and change the mirrors to point to "old-releases" for example change:

```
deb http://archive.ubuntu.com/ubuntu/ intrepid main restricted
```

to:

```
deb http://old-releases.ubuntu.com/ubuntu/ intrepid main restricted
```

Then refresh your package list with "sudo apt-get update". This should allow you to install the appropriate (but no-longer-supported) packages from the end-of-life 8.10 repositories.

---

### Post by lisati on 2012-02-24
Old thread closed: 8.10 has been and gone.

---

