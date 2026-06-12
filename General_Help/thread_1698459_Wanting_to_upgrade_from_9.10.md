---
title: "Wanting to upgrade from 9.10"
date: 2011-03-02
forum: General Help
---

### Post by rva1945 on 2011-03-02
Which is the current and stable Ubuntu? Lucid?

Where do I download the ISO for creating a Live (Lucid?) CD?

Is there (I bet YES) any tool in Ubuntu to create that Live CD?

Thanks

---

### Post by Rubi1200 on 2011-03-02
1. download the Ubuntu iso: [http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)

2. check the integrity: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

3. burn to CD at the lowest speed: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

6. try as a LiveCD first to see that everything work as it should (don't forget to set BIOS to boot from the CD drive first)

7. backup all important data

8. install

Good luck!

---

### Post by rva1945 on 2011-03-02
> **Rubi1200 said:**
> 1. download the Ubuntu iso: [http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)
 
2. check the integrity: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
 
3. burn to CD at the lowest speed: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
 
6. try as a LiveCD first to see that everything work as it should (don't forget to set BIOS to boot from the CD drive first)
 
7. backup all important data
 
8. install
 
Good luck!
 
 
A year befoe, I had successfully created the 9.10 image used it as a Live CD, then installed it after a couple of days. Now I've just created the Maverick (skipped Lucid) live CD, having previously checked md5sum integrity of the ISO file. Now, how can I check the CD integrity in Windows? Otherwise, can I check it from my 9.10 Linux?
 
Can I upgrade my 9.10 to 10.10 without having to wipe it out?
 
Thanks

---

### Post by seawolf167 on 2011-03-02
> **rva1945 said:**
> Can I upgrade my 9.10 to 10.10 without having to wipe it out?

You should do a fresh install.

[*You can directly upgrade to Ubuntu 10.10 ("Maverick Meerkat") from Ubuntu 10.04 LTS ("Lucid Lynx") only*]("https://help.ubuntu.com/community/MaverickUpgrades")

To MD5Sum from Windows - I don't know of any programs off the top of my head, but a google search for MD5Sum Windows gives a lot of promising looking results.

---

### Post by rva1945 on 2011-03-02
> **seawolf167 said:**
> You should do a fresh install.

[*You can directly upgrade to Ubuntu 10.10 ("Maverick Meerkat") from Ubuntu 10.04 LTS ("Lucid Lynx") only*]("https://help.ubuntu.com/community/MaverickUpgrades")

To MD5Sum from Windows - I don't know of any programs off the top of my head, but a google search for MD5Sum Windows gives a lot of promising looking results.


CouldI upgrade 9.10 to Lucid 10.04 then Lucid to 10.10 Mav?

---

### Post by seawolf167 on 2011-03-02
Here is the [official response]("https://help.ubuntu.com/community/LucidUpgrades")

You really can upgrade from any version to any version, but depending on what changed and how drastically, it may or may not be a good idea. If you have compiled your own programs from source, installed external .debs, etc., there are bound to be incompatibilities which could cause major headaches.

Personally, I just stay with the LTS versions and reinstall every two years, but you can stay with the 6 month release cycle, just be prepared to spend time working out problems after each dist-upgrade.

---

### Post by rva1945 on 2011-03-02
> **seawolf167 said:**
> Here is the [official response]("https://help.ubuntu.com/community/LucidUpgrades")

You really can upgrade from any version to any version, but depending on what changed and how drastically, it may or may not be a good idea. If you have compiled your own programs from source, installed external .debs, etc., there are bound to be incompatibilities which could cause major headaches.

Personally, I just stay with the LTS versions and reinstall every two years, but you can stay with the 6 month release cycle, just be prepared to spend time working out problems after each dist-upgrade.


Well, I have never compiled any program of my own. I just accepted some updates, installed some packages.

---

### Post by holycow131415 on 2011-03-02
its always better to do clean installs for any OS

---

### Post by Bitrate on 2011-03-02
> **holycow131415 said:**
> its always better to do clean installs for any OS

I wish people would stop making blanket statements like this.

Many Operating Systems can be upgraded to newer versions without doing a complete re-installation. FreeBSD is a good example of how an OS upgrade can work very seamlessly.

---

