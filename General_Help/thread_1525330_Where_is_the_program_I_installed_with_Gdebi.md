---
title: "Where is the program I installed with Gdebi?"
date: 2010-07-06
forum: General Help
---

### Post by baxna on 2010-07-06
Hello,

I tried searching this & other forums for similar posts but couldn't find what I'm looking for. Maybe you can help?

I installed The Gimp a week ago via the Ubuntu Software Center (very easy to use) and the program works great. Then today I came across GimpShop ([http://www.gimpshop.com/](http://www.gimpshop.com/)), which is apparently very similar to Adobe Photoshop Elements.

So I downloaded the .deb file and double-clicked on it. Gdebi came up and supposedly installed it with no problems. However I can't find a reference to the program in my /usr/bin folder, and there's nothing new in my Applications menu. Any ideas? Do I have to uninstall The Gimp (original one) first?

Oh and one other thing, running ```
zcat -f /var/log/dpkg.log* | grep "\ install\ " | sort
``` confirms it's installed, it returns "2010-07-06 11:55:09 install gimpshop <none> 2.2.11-1"

Thanks very much!

---

### Post by sinichiro on 2010-07-06
Maybe [http://ubuntuforums.org/archive/index.php/t-1168995.html](http://ubuntuforums.org/archive/index.php/t-1168995.html) will help.

---

### Post by Yarui on 2010-07-06
In synaptic package manager you can right click a package and go to "properties > Installed Files" to get a list of files that the package installed.  If you do this for the GIMP shop package you may be able to find the file you are looking for.

---

### Post by ajgreeny on 2010-07-06
> **Yarui said:**
> In synaptic package manager you can right click a package and go to "properties > Installed Files" to get a list of files that the package installed.  If you do this for the GIMP shop package you may be able to find the file you are looking for.
+1
Synaptic is very good at showing all packages installed, even if they were installed manually by other means, so a search for gimp should show gimpshop along with the original, always assuming they can both exist side by side.

---

