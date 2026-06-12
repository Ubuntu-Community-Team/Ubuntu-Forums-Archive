---
title: "moving to new laptop. 32bit -&gt; 64bit"
date: 2011-08-02
forum: General Help
---

### Post by Bashar &quot; on 2011-08-02
Hello,
i just got newer laptop and installed ubuntu 64bit to benefit from the quad core and extra RAM i have.

So i wanted to know whats the best way to migrate things from my older laptop to the new laptop? my most concerns are:
1- thunderbird and its related files/profiles
2- firefox and its related files/profiles

other than that i can install things manually again. speaking of installing things manually, is there a place i can know all installed apps on ubuntu from software center to re-install them on my new laptop?

Thank you

---

### Post by CaptainMark on 2011-08-02
are you referring specifically relating to the change of 32 to 64 bit, because thats not much of a problem these days as long as you install the [64 bit version of flash]("https://launchpad.net/~sevenmachines/+archive/flash")

---

### Post by Bashar &quot; on 2011-08-02
> **CaptainMark said:**
> are you referring specifically relating to the change of 32 to 64 bit, because thats not much of a problem these days as long as you install the [64 bit version of flash]("https://launchpad.net/~sevenmachines/+archive/flash")
thats the only thing i need to care about? no other applications might have problems when copying the profile settings?

thanks

---

### Post by Bashar &quot; on 2011-08-02
also whats the best way to move data? possible to make cross cable and connect both ethernet ports and copy data for fastest way rather than sharing it over WIFI network and copy things over or using flash thumb-drive ?

Thanks

---

### Post by JC Cheloven on 2011-08-02
> **Bashar " said:**
> i just got newer laptop and installed ubuntu 64bit to benefit from the quad core and extra RAM i have.

You should note that installing a 32bit ubuntu with internet conection will download for you a PAE kernel. That means that the ram above ~2.8Gb will be used even though the system is 32 bits. The quad core isn't a problem either AFAIK.
The 32 bit system [is the recommended one]("http://www.ubuntu.com/download/ubuntu/download"). I guess the main reason is adobe having discontinued the 64 bit flash for linux. But also you may want to install some software out there ([example]("http://www.3ds.com/products/draftsight/download-draftsight/")) which is only available for 32 bits linux.

That said, I'm myself using 64 bit ubuntu right now ;)

Ah, for moving data, your router should be the best option, I think.

---

### Post by oldfred on 2011-08-02
I regularly copy my Filefox & Thunderbird profiles from my Desktop to my Laptop when we travel. And back again. A couple of years ago I did the change from 32 to 64 bit and just kept using the same profiles. I have my profiles in a shared NTFS partition with XP and have used them without issue on updates, some not exactly the same time with Ubuntu & XP.

To list applications and then reinstall:
from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

---

