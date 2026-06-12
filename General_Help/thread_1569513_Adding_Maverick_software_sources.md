---
title: "Adding Maverick software sources"
date: 2010-09-06
forum: General Help
---

### Post by Chethan S on 2010-09-06
I have been reading about new wallpapers and themes in maverick beta release. I use lucid and don't plan to shift to newer one until another LTS release arrives. Therefore I want to know if I can add the official software source to maverick into my lucid software sources. If yes how can i do it?:)

---

### Post by Revolutionary101 on 2010-09-06
I am pretty sure that there is a way to add the Maverick software sources, but I don't know what the source APT line is. Even though you may not be able to find that, you can download the Maverick packages from [here]("http://packages.ubuntu.com/maverick/").

At least that website will give you access to the packages from Maverick. Hope it helps.

---

### Post by plucky on 2010-09-07
> **Chethan S said:**
> I have been reading about new wallpapers and themes in maverick beta release. I use lucid and don't plan to shift to newer one until another LTS release arrives. Therefore I want to know if I can add the official software source to maverick into my lucid software sources. If yes how can i do it?:)

It is not recommended to mix repositories of different releases.

If you add the Maverick repositories,your system will try to upgrade to Maverick,which is not what you want.Better to just download the packages you want.


Good Luck

---

### Post by beew on 2010-09-09
**Revolutionary 101 **

Actually your link leads to instructions to adding Maverick repositories if you try to add some packages. I did that. :) 

**Chethan S**

It is better to find a PPA or download a .deb file to get update programs. If you can't find either and want to add Maverick source, make sure you only install end user programs that don't have a lot of external dependencies that need downloading and upgrading, installing system softwares would probably screw you up in a very bad way. Also disable the Maverick repo after you install the progarms you want by unchecking it from Synaptic > settings > repositories > other softwares. That way you won't get into trouble by upgrading things that you shouldn't (and there are lots of such "upadtes")

Also install Ubuntu Tweak [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/) It has a feature called PPA purge (there is something like that in the Maverick repo, but obviously you can't use it to purge the Maverick repo itself!) If you have installed packages from PPAs that causes problems you can use it to safety downgrade your packages. Should you need to purge the Maverick repo and downgrade the packages you install from it,  enable it by checking the box in Synaptic and reload, then close Synaptoc and purge it from Ubuntu tweak.

Now you can find the Maverick source from Revolutionary's link and you are all set and do it at your own risk. I have to say I felt good after doing that, kind of like tasting forbidden fruit :):)

---

