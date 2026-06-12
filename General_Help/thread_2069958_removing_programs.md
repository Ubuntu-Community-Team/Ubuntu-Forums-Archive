---
title: "removing programs"
date: 2012-10-11
forum: General Help
---

### Post by unibroker on 2012-10-11
I want to remove Eclipse and Android SDK from my system and then re-install them.  From terminal I executed ```
sudo apt-get purge eclipse
``` but when I go into the Desktop of my Home folder an eclipse file is still there with an executable that still runs the program.  I check Package Manager and it says it's not installed.  I'm confused.

---

### Post by wojox on 2012-10-11
When you purge or remove packages, it won't touch any files in your user directory. You need to delete those yourself if you want them gone.

---

### Post by Rex Bouwense on 2012-10-11
+1
I found out the hard way that those files are still there.  They also sometimes contain old settings that can cause problems with a re-installation.

---

### Post by unibroker on 2012-10-11
> **wojox said:**
> When you purge or remove packages, it won't touch any files in your user directory. You need to delete those yourself if you want them gone.

Thanks.  Can't understand why that is but it worked.

---

### Post by unibroker on 2012-10-11
> **Rex Bouwense said:**
> +1
I found out the hard way that those files are still there.  They also sometimes contain old settings that can cause problems with a re-installation.

Thanks for the heads-up.

---

### Post by mittwit on 2012-10-11
Out of interest did you install eclipse using apt-get?

---

### Post by unibroker on 2012-10-11
> **mittwit said:**
> Out of interest did you install eclipse using apt-get?

I can't remember as it was just after I moved from Windows to Ubuntu late 2011.  I think it was part of a tutorial and usually they are terminal users.

---

