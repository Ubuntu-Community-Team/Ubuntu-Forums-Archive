---
title: "Upgrading Lucid to Meerkat"
date: 2010-11-07
forum: General Help
---

### Post by xdeathcorex on 2010-11-07
Hey guys, is it good to just upgrade Ubuntu 10.09 to 10.10 but not clean install?

I've installed so many applications so far in Lucid and if I clean install it, I've been thinking of reinstall all the applications back is a tiring process.

---

### Post by kanishkdudeja on 2010-11-07
i dont think you should upgrade..it sometimes causes problems..

do a clean install..

and if u r worried about downloading packages again..

u can use [aptoncd]("http://aptoncd.sourceforge.net/")..

---

### Post by xdeathcorex on 2010-11-07
> **kanishkdudeja said:**
> i dont think you should upgrade..it sometimes causes problems..

do a clean install..

and if u r worried about downloading packages again..

u can use [aptoncd]("http://aptoncd.sourceforge.net/")..

hey thanks for the suggestion. i'll try it out later.

---

### Post by geoffmcc on 2010-11-07
I installed ubuntu 10.04 server on a old computer and then a day or two after getting it the way i wanted, i decided since not my primary computer might as well put 10.10 beta on.

Anyways. Once it finished downloading and started to install it started giving me all these options to keep old config file or accept new. 

I figured no matter what i did it probably would be the wrong decision and just waste more time i just did a clean install

---

### Post by I'mGeorge on 2010-11-07
> **xdeathcorex said:**
> Hey guys, is it good to just upgrade Ubuntu 10.09 to 10.10 but not clean install?

I've installed so many applications so far in Lucid and if I clean install it, I've been thinking of reinstall all the applications back is a tiring process.

You should try upgrading though to see how it goes.

I would recommend using aptitude safe-upgrade but I've heard aptitude was abolished since Meerkat

---

### Post by geoffmcc on 2010-11-07
> **I'mGeorge said:**
> You should try upgrading though to see how it goes.

I would recommend using aptitude safe-upgrade but I've heard aptitude was abolished since Meerkat

actually to go from one release to the next it would be 

sudo do-release-upgrade

aptitude safe-upgrade would be for installing regular updates


also aptitude is present in meerkat

---

### Post by Quackers on 2010-11-07
I would back up your home folder (with hidden files - ctrl+h) to external media, then try the upgrade and see if it works ok. You can always re-install later if needed.
You can also make an executable list of your currently installed packages and run it afterwards, and replace your files from your backup of /home. see this item

[http://linuxologist.com/1general/howto-fresh-ubuntu-install-without-losing-your-current-settings/](http://linuxologist.com/1general/howto-fresh-ubuntu-install-without-losing-your-current-settings/)

---

### Post by habana on 2010-11-07
Upgrade worked for me as it has since Gutsy.Everything worked straight away without any dramas. Backup your Home Folder first and good luck!

---

### Post by I'mGeorge on 2010-11-07
> **geoffmcc said:**
> actually to go from one release to the next it would be 

sudo do-release-upgrade

aptitude safe-upgrade would be for installing regular updates


also aptitude is present in meerkat

as far as I know it's recommended to use aptitude safe-upgrade in the process of upgrading to a superior version. But it's good it wasn't abolished.

---

