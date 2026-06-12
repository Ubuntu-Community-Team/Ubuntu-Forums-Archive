---
title: "How to block pop ups??"
date: 2009-08-14
forum: General Help
---

### Post by karthick87 on 2009-08-14
While opening  websites,some pop up message is also opening..Its annoying,is there any way to block it??

---

### Post by sasho_zl on 2009-08-14
Try the No Script plugin for firefox.

---

### Post by bear24rw on 2009-08-14
also install AdBlock Plus extension

---

### Post by CatKiller on 2009-08-14
And if you want to go the whole hog, you can add a custom hosts file.

---

### Post by lovinglinux on 2009-08-14
+1 for [Adblock Plus](https://addons.mozilla.org/en-US/firefox/addon/1865) and [NoScript](https://addons.mozilla.org/en-US/firefox/addon/722).

---

### Post by karthick87 on 2009-08-15
How to add a custom host file..

---

### Post by Mardoct909 on 2009-08-15
A custom hosts file is not necessary in most any cases for the average user. The firefox addons are more than enough.

---

### Post by lovinglinux on 2009-08-15
> **Mardoct909 said:**
> A custom hosts file is not necessary in most any cases for the average user. The firefox addons are more than enough.

I agree.

---

### Post by CatKiller on 2009-08-15
> **lovinglinux said:**
> I agree.

I don't. Banner ads use up your bandwidth for things that you don't want to see. Blocked banner ads use up your bandwidth for things you aren't even going to see. Best to just not download them in the first place.

[This]("http://en.wikipedia.org/wiki/Hosts_file") is what a hosts file is.

[This]("http://en.wikipedia.org/wiki/Hosts_file#Internet_resources_blocking") is what you're trying to achieve with it.

[Here]("http://pgl.yoyo.org/adservers/serverlist.php?hostformat=hosts") is a pretty arbitrarily-chosen list of ad servers to use with your hosts file. It is the one that I'm currently using, but that's not a recommendation. A search for "ad block hosts file" will net you many variations to choose from.

All you need to do is open your hosts file as root with ```
gksudo gedit /etc/hosts
```and paste the entries **at the end** of that file. Don't overwrite anything that's already there. You can put the commented stuff in there too if you want to remember where you got the list from. Save and close, and you're done. Your computer will no longer try to contact any of the Internet servers on the list.

---

### Post by karthick87 on 2009-08-15
Fine thank you..

---

