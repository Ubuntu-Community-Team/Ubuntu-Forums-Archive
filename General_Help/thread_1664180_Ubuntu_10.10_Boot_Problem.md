---
title: "Ubuntu 10.10 Boot Problem"
date: 2011-01-10
forum: General Help
---

### Post by joedog96 on 2011-01-10
Hello, I have come across an error. You see, when I first boot up my computer after installing, I had seen the boot. It had Five options, one being my previously installed Windows Vista, two being the memory tests, and one being "Ubuntu, with Linux 10.10.(something) - Generic" and the other being the recovery mode of said OS. I had booted that up, and I went onto my user that was set up. I had noticed one thing - it would NOT connect to my network. I could not connect to anything, automatically or manually. So, I decided to go onto Vista to troubleshoot. I went to the GRUB, and Selected "Windows Vista (loader)", and it went to the Vista boot screen. It had another option, however; I could select either "Windows Vista Home Premium" or "Ubuntu". Not being a retard, I decided this was the obvious choice to delve into. It had 5 selections, like before, and it did not have the "memory test" options, but instead, at the top of the list, had two options - "Ubuntu Linux 10.10.(something)" and the recovery mode. I selected "Ubuntu Linux 10.10.(something)", and sure enough - the installer CONTINUED! So, I let it install, and sure enough it went to the login screen. It had, instead of my username "Josiah (lastname)", "Administrator". THIS, I like. So, I went onto THIS user, and sure enough, it had Internet, and Firefox worked. It quickly prompted the installer, and I let it download, and install. I then let it reboot, because well, 300 MB of installs probably would need to do so. When I selected Vista on the first GRUB, I selected Ubuntu, but instead of going to that other GRUB... (frustrating part)... ALL THE COMPUTER DOES IS REBOOT. 

Woop dee doo.

...Help? :|

---

### Post by joedog96 on 2011-01-10
Glad to see nobody else has had this problem on the forums after searching. I'm just reinstalling.

---

### Post by garvinrick4 on 2011-01-10
Did you try and install WUBI at one time and uninstall and it did not remove wubildr from Vista's BCD? When you try to boot does it go to another boot menu instead? If you still have a problem after reinstalling Ubuntu come back to this thread it has to be deleted
from BCD.

---

### Post by oldfred on 2011-01-10
If you want to reinstall fine.

If you want to know what is installed where:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by joedog96 on 2011-01-10
Hey guys, you were absolutely right, I had uninstalled it and then reinstalled it without removing wubildr. I wiped all Ubuntu related stuff and did a clean install, and voila, I am posting from Ubuntu Firefox. Thanks!

---

### Post by bcbc on 2011-01-10
There's no reason wireless should work from a Wubi Ubuntu install but not a normal Ubuntu install. The networking is unaffected by it being Wubi or not.

But I suspect that your Wubi was release 10.04.1 - because after updates it started rebooting: a current problem with 10.04.1 wubi and not 10.10. So that may be your difference.

If you have the ability to install direct, I recommend it over Wubi. Otherwise, don't update packages grub-pc and grub-common or you'll be back rebooting with the Wubi install again.

---

