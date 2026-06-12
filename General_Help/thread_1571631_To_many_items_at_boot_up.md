---
title: "To many items at boot up"
date: 2010-09-09
forum: General Help
---

### Post by waltwin on 2010-09-09
[SIZE=2][COLOR=black]I have asked this question several times but I think that I am not asking it correctly. 

I have umbutu 9.04  and Windows 7.0 on my C: drive. When I start my machine I have approximately 9 or 10 items on my boot list and I would like to have 2.

It has been suggested that I determine what version of grub I am using and I am using /boot/vmlinuz-2.6.28-19 generic. I have no idea what that means.

It has been suggested that I install some various items of software and I am sure that it would solve my problem but to me it would be like looking down a cows throat. 

Please, don't get me wrong, I really appreciate the input but its like when you go to the doctor you kind of wonder "just what the heck is he talking about". Maybe someone could just tell me how to accomplish what I want to do so I can understand!

My daughter uses this machine and she goes to places that I didn't know I had. Thank you for your understanding and your help.

waltwin 
[/COLOR][/SIZE]

---

### Post by drs305 on 2010-09-09
You are running Jaunty. You can confirm this by typing this in a terminal (Applications, Accessories, Terminal):
```
lsb_release -a
```

The easiest thing for you to do is to install Startup-Manager - which will work for you. It is a GUI app and it will allow you to tweak your Grub settings, including how many options you see. Believe me, it is much easier than looking down a cow's throat (I would imagine)!  ;-)

I wrote a guide about reducing the number of kernels displayed in the menu, then expanded it to include StartUp-Manager. Here is the link:
[HOWTO: StartUp Manager & Kernel Display Options]("http://ubuntuforums.org/showthread.php?t=818177")

I think this will be easy enough to understand. If not, just come back and ask your questions.

The guide also tells you how to uninstall all those extra kernels that are accumulating on your machine, if you wish to delete them. If you want to remove kernels, be sure to read the section about Ubuntu Tweak.

---

### Post by waltwin on 2010-09-10
> **drs305 said:**
> You are running Jaunty. You can confirm this by typing this in a terminal (Applications, Accessories, Terminal):
```
lsb_release -a
```The easiest thing for you to do is to install Startup-Manager - which will work for you. It is a GUI app and it will allow you to tweak your Grub settings, including how many options you see. Believe me, it is much easier than looking down a cow's throat (I would imagine)!  ;-)

I wrote a guide about reducing the number of kernels displayed in the menu, then expanded it to include StartUp-Manager. Here is the link:
[HOWTO: StartUp Manager & Kernel Display Options]("http://ubuntuforums.org/showthread.php?t=818177")

I think this will be easy enough to understand. If not, just come back and ask your questions.

The guide also tells you how to uninstall all those extra kernels that are accumulating on your machine, if you wish to delete them. If you want to remove kernels, be sure to read the section about Ubuntu Tweak.

I have been unable to download ubuntu-tweak. I get an error message as follows,

ERROR: Dependency is not satisfied: policy-1-gonome|policykit-1 qt  I have been searching to find what that means but no joy. It has been suggested that I go to Synsptic Package Manageer and enter Policykit-1-gnome which I tried. Policykit gnome is already installed so that did not work. I entered Policykit-1-gnome in the search box but it does not seem to exist!

Any ideas?

---

### Post by wilee-nilee on 2010-09-10
I think there is no support for 9.04 any more if I read this web page correctly.
[http://www.techspikes.com/2010/02/ubuntu-tweak-app-centre/](http://www.techspikes.com/2010/02/ubuntu-tweak-app-centre/)

Jaunty is about a month from no support as well.
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Can I interest you in a dual boot that would also be a upgrade? Wubi is mainly for trying out a distro not long term use.

---

### Post by drs305 on 2010-09-10
waltwin,

*wilee-nilee* is correct that Jaunty is just about at it's EOL. After that, the repositories will be moved and no longer updated. He is also correct in suggesting you upgrade to a newer release and changing to a full installation if you like Ubuntu.

As for Jaunty, older versions  of Ubuntu Tweak are still available from the following site. You should be able to select one of the versions, download and double-click on it to install. Otherwise, use the command "sudo dpkg -i <packagename>" in the folder which contains the download.

[http://code.google.com/p/ubuntu-tweak/downloads/list]("http://code.google.com/p/ubuntu-tweak/downloads/list")

---

### Post by waltwin on 2010-09-10
> **drs305 said:**
> waltwin,

*wilee-nilee* is correct that Jaunty is just about at it's EOL. After that, the repositories will be moved and no longer updated. He is also correct in suggesting you upgrade to a newer release and changing to a full installation if you like Ubuntu.

As for Jaunty, older versions  of Ubuntu Tweak are still available from the following site. You should be able to select one of the versions, download and double-click on it to install. Otherwise, use the command "sudo dpkg -i <packagename>" in the folder which contains the download.

[http://code.google.com/p/ubuntu-tweak/downloads/list](http://code.google.com/p/ubuntu-tweak/downloads/list)

Thank you for the response. I do like ubuntu even though I run into these problems. I keep windows to do many things just in case. I understand that version 10 is out but since I am such a novice I wonder if it is to new for me. What would you recommend that I upgrade to.

---

### Post by drs305 on 2010-09-10
> **waltwin said:**
> Thank you for the response. I do like ubuntu even though I run into these problems. I keep windows to do many things just in case. I understand that version 10 is out but since I am such a novice I wonder if it is to new for me. What would you recommend that I upgrade to.

I would recommend Lucid, 10.04. It's a long term release so it will be around for a long time. Maverick will be out next month but things have settled down with Lucid and it's been a good release for most users. 

You can read about the [new features in Maverick]("http://www.ubuntu.com/testing/maverick/beta#New%20features%20in%20Maverick") to see if there is something you really want or need in it, but you can also easily upgrade from Lucid to Maverick in a few months if you feel the need. I would strongly urge you not to try the Maverick beta. Go with Lucid. If you feel you need Maverick wait a few weeks after it's official release next month before installing or upgrading to it.

Happy Ubuntu-ing!

---

### Post by Kir_B on 2010-09-10
I echo the comment about wubi being only for trying out a distribution, as we had numerous problems with it, even once leading to re-installing our Windows, which is a circumstance I wouldn't wish upon anyone, well just about anyone.

Do your research before setting up a dual boot. There are lots of good HowTo's out there.

Good luck. Kirby

---

