---
title: "Questions about Remastersys"
date: 2011-10-07
forum: General Help
---

### Post by erbad on 2011-10-07
I noticed that Remastersys is no longer being offered and I had two questions about it.

1.  I have a copy of Remastersys installed on one of my computers running Ubuntu.  Is there a way to copy it to the new computer that I just installed Ubuntu on?

2.  If it is not possible, are there any easy alternatives to Remastersys so that I can make a full backup of my new Ubuntu install with all of its custom settings?

---

### Post by blueridgedog on 2011-10-07
You can download the .deb file from a variety of places and install it:

Here is the original:

[http://www.geekconnection.org/remastersys/repository/ubuntu/](http://www.geekconnection.org/remastersys/repository/ubuntu/)

It appears to still work.

---

### Post by Frogs Hair on 2011-10-07
There is Remastersys fork .  [http://re-linux.sourceforge.net/](http://re-linux.sourceforge.net/)

---

### Post by blueridgedog on 2011-10-07
+1 for fork...could not find it with a short search.

---

### Post by erbad on 2011-10-07
> **blueridgedog said:**
> You can download the .deb file from a variety of places and install it:

Here is the original:

[http://www.geekconnection.org/remastersys/repository/ubuntu/](http://www.geekconnection.org/remastersys/repository/ubuntu/)

It appears to still work.

I downloaded remastersys_2.0.12-1.deb and when I double click on it, I get the error message "dependency is not satisfiable: grub"

Any thoughts on how to get around this?

---

### Post by bodhi.zazen on 2011-10-07
> **erbad said:**
> If it is not possible, are there any easy alternatives to Remastersys so that I can make a full backup of my new Ubuntu install with all of its custom settings?

IMO I tis much much easier to simply tar your home directory and copy your package list.

[http://www.ubuntu-unleashed.com/2008/04/howto-restore-all-installed-packages-in.html](http://www.ubuntu-unleashed.com/2008/04/howto-restore-all-installed-packages-in.html)

---

### Post by erbad on 2011-10-08
> **bodhi.zazen said:**
> IMO I tis much much easier to simply tar your home directory and copy your package list.

[http://www.ubuntu-unleashed.com/2008/04/howto-restore-all-installed-packages-in.html](http://www.ubuntu-unleashed.com/2008/04/howto-restore-all-installed-packages-in.html)

The reason I want to use Remastersys is to make a LiveCD

---

### Post by bodhi.zazen on 2011-10-08
> **erbad said:**
> The reason I want to use Remastersys is to make a LiveCD

If you wish to make a live CD, use the debian live scripts, they are in the repos, are easier to use, easier to customize, and give a better end result.

---

### Post by erbad on 2011-10-08
> **bodhi.zazen said:**
> If you wish to make a live CD, use the debian live scripts, they are in the repos, are easier to use, easier to customize, and give a better end result.

Thank you for your suggestion.

I did manage to find the deb file for remastersys and downloaded it and installed it.  This got me going for now at least because I'm familiar with this method.

However, I would like to learn more about the debian live scripts moving forward.  I know you said they are in the repos.  Would you know what they would be called in Synaptic Package Manger?

I did find one in there called devscripts - scripts to make the life of a debian package maintainer easier, but I'm not sure if that is the one you are referring to.

---

### Post by bodhi.zazen on 2011-10-08
> **erbad said:**
> Thank you for your suggestion.

I did manage to find the deb file for remastersys and downloaded it and installed it.  This got me going for now at least because I'm familiar with this method.

However, I would like to learn more about the debian live scripts moving forward.  I know you said they are in the repos.  Would you know what they would be called in Synaptic Package Manger?

I did find one in there called devscripts - scripts to make the life of a debian package maintainer easier, but I'm not sure if that is the one you are referring to.

Aye Remastersys is an "OK" "easy" tool, but it is rapidly not so easy once you want to make any kind of customizations ;)

See

[http://live.debian.net/](http://live.debian.net/)

[http://live.debian.net/manual/en/html/live-manual.html](http://live.debian.net/manual/en/html/live-manual.html)

The Ubuntu package is live-build

[http://manpages.ubuntu.com/manpages/natty/en/man7/live-helper.7.html](http://manpages.ubuntu.com/manpages/natty/en/man7/live-helper.7.html)

---

### Post by inameiname on 2011-10-14
> **bodhi.zazen said:**
> Aye Remastersys is an "OK" "easy" tool, but it is rapidly not so easy once you want to make any kind of customizations ;)

See

[http://live.debian.net/](http://live.debian.net/)

[http://live.debian.net/manual/en/html/live-manual.html](http://live.debian.net/manual/en/html/live-manual.html)

The Ubuntu package is live-build

[http://manpages.ubuntu.com/manpages/natty/en/man7/live-helper.7.html](http://manpages.ubuntu.com/manpages/natty/en/man7/live-helper.7.html)


Personally, after doing a fresh install of Ubuntu, and then heavily customizing it to my liking, remastersys has never failed me in backing up my custom Ubuntu-derivatived system. And when I mean customizing it, I really do mean customizing it to a great degree (remove Unity, install classic gnome desktop, add/remove a lot of packages, change a lot of the settings, new themes, new fonts, new splash screens, new all sorts of things).

I guess it depends on just what sort of customizations you are doing as to the success rate of remastersys.

Regardless, unfortunately remastersys has recently become a dead project. Fortunately, though, a fork of it exists, called relinux. It is coming along fairly well. A lot of issues have been  addressed just in the past few days, with plans to address/fix many  more. It is looking to be a good replacement for the now dead remastersys, a greatly-missed program for many of us.

Here is an article about it from the developer:

[http://lkubuntu.wordpress.com/2011/1...f-your-system/]("http://lkubuntu.wordpress.com/2011/10/10/relinux-a-way-to-create-a-bootable-iso-out-of-your-system/")

Also, here is another thread on here about it:

[http://ubuntuforums.org/showthread.p...hlight=relinux]("http://ubuntuforums.org/showthread.php?t=1857376&highlight=relinux")

---

