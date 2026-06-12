---
title: "Skype Icon missing in Gnome Panel"
date: 2012-05-07
forum: General Help
---

### Post by bipinkdas on 2012-05-07
Dear All ,

I am using Gnome Panel with effects , Ubuntu 12.04 (fresh install). But when skype starts i cannot see the icon in the gnome panel. How can i display the skype icon in the panel ??

Thanks in advance.

BipinDas.

---

### Post by parajulik on 2012-05-07
Try this command:
```
gsettings set com.canonical.Unity.Panel systray-whitelist "['all']"
```

This will change the systray-whitelist option to allow all applications.

---

### Post by bipinkdas on 2012-05-07
Thanks for your quick answer , but it didnt workout.

---

### Post by Helkaluin on 2012-05-09
Make sure sni-qt is installed.

```
$sudo apt-get install sni-qt
```

And, if you're using a 64-bit install, that the i386 package of sni-qt is installed (as Skype is currently distributed as 32-bit binary only).

```
$sudo apt-get install sni-qt:i386
```

---

### Post by kelvin spratt on 2012-05-09
> **parajulik said:**
> Try this command:
```
gsettings set com.canonical.Unity.Panel systray-whitelist "['all']"
```This will change the systray-whitelist option to allow all applications.
He is using gnome panel not unity

---

### Post by shz1 on 2012-05-09
This happened to me when I installed skype deb from the skype site.  So uninstalled that and reinstalled it through apt-get and now the icon was there.

---

### Post by bipinkdas on 2012-05-28
Thanks Helkaluin ,

Your idea works !!!!

---

### Post by Helkaluin on 2012-05-28
Good!

Now, remember to mark the post as [SOLVED] so that others can benefit from it.

---

### Post by napril on 2013-03-08
> **Helkaluin said:**
> Make sure sni-qt is installed.

```
$sudo apt-get install sni-qt
```

And, if you're using a 64-bit install, that the i386 package of sni-qt is installed (as Skype is currently distributed as 32-bit binary only).

```
$sudo apt-get install sni-qt:i386
```

Thank you Helkaluin, it works for me!

---

### Post by trexgrec on 2013-05-25
Thanks so much! It worked for Ununtu 13.04 64 bit!!!!!

---

### Post by axet2 on 2013-09-05
ubuntu 13.04 helps:

sudo apt-get install sni-qt:i386

---

