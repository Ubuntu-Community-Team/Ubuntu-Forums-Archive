---
title: "How to install a theme Ubuntu 11.10 Unity?"
date: 2012-01-08
forum: General Help
---

### Post by bonfire89 on 2012-01-08
I never thought the day would come, I've been an Ubuntu user for over 3 years and here I am asking what has got to be one of the most basic questions I have ever asked in regards to Linux.

I just upgraded to Ubuntu 11.10 and I am running Unity and I can't figure out how to install a third party theme.

I have run gnome shell in the past, and I know the gnome tweak tool, and I know about how you have to enable user themes.

I also know that gnome shell and unity both run on gnome 3.

In fact, I have gnome tweak tool installed but it some how lists far more themes than the ubuntu appearance tool. It appears to display everything listed in /usr/share/themes/

Why are these themes not listed in the appearance window? How do I make them show up in the appearance window?

I figured out that through dconf-tools I can manually type in a theme from /usr/share/themes/ but that is ridiculous. How am I supposed to tell the people I have convinced to switch from windows to ubuntu to do that? They will never understand that, and it is far too big of a hassle for me to deal with. What happened to my ability of being able to drag a tar.gz onto the themes area and have it automatically installed?

Am I missing something?

---

### Post by Derek Karpinski on 2012-01-09
You're not missing anything.  11.10 has taken a huge step back in the settings menu department.  You have to use Ubuntu tweak, or gnome tweak tool, and unzip the theme in the themes folder, then you can select it.  It rather blows.

I hope 12.04 will fix this.

EDIT: [https://docs.google.com/document/d/1ILTJDiDCd25Npt2AmgzF8aOnZZECxTfM0hvsbWT2BxA/edit?hl=en_GB](https://docs.google.com/document/d/1ILTJDiDCd25Npt2AmgzF8aOnZZECxTfM0hvsbWT2BxA/edit?hl=en_GB)

Looks like settings will be fixed for 12.04.

---

### Post by raja.genupula on 2012-01-09
step by step guide for you

[http://www.upubuntu.com/2011/12/how-to-install-gtk3-darko-theme-under.html](http://www.upubuntu.com/2011/12/how-to-install-gtk3-darko-theme-under.html)

---

### Post by kajali on 2012-01-09
thanks, I am also looking for this help

---

### Post by silverhaze06 on 2012-01-09
For me, I did all the steps on this page, [http://news.softpedia.com/news/How-to-Install-GNOME-Themes-in-Ubuntu-11-10-231213.shtml]("http://news.softpedia.com/news/How-to-Install-GNOME-Themes-in-Ubuntu-11-10-231213.shtml") 

Then I downloaded some themes from here, [http://gnome-look.org/index.php?xcontentmode=167&PHPSESSID=e2e485bcec9ddf56d544b26a5e91bad0]("http://gnome-look.org/index.php?xcontentmode=167&PHPSESSID=e2e485bcec9ddf56d544b26a5e91bad0")

For me however, only one of the 6 or so themes I tried worked with my system, (minus the icons that came with it) which was this one here, [http://gnome-look.org/content/show.php/GnomishDark?content=147290]("http://gnome-look.org/content/show.php/GnomishDark?content=147290") I personally love this theme so I dont plan on changing it any time soon.

---

### Post by bonfire89 on 2012-01-09
I'm glad to know I wasn't really missing anything. The Ubuntu tweak tool is cool, I had forgotten about it. Since it isn't a critical app I installed the testing version as per the instructions here [http://www.webupd8.org/2011/12/test-ubuntu-tweak-06-now-with-unity.html](http://www.webupd8.org/2011/12/test-ubuntu-tweak-06-now-with-unity.html) and dropped a theme into ~/.theme/ and then started Ubuntu tweak took and it worked great.

This is a find solution for me but I feel bad for people who will have issues simply uncompressing the theme into ~/.theme/

I hope this changes in 12.04 too, I want to stand by Ubuntu.

Thanks all!

I supppose this counts as solved hehe :P

---

