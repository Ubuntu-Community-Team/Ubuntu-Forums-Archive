---
title: "Need Howto Upgrade Java 1.4.2"
date: 2006-02-23
forum: General Help
---

### Post by ahood on 2006-02-23
Hi All,

I have an old version of Java (1.4.2) that I installed _manually_ quite a while ago (a year?). I would like to upgrade to a newer version of Java (1.5.x). How do I go about doing this?

(a) Uninstall Java 1.4.2 and then install 1.5.x?

(b) Install 1.5.x over 1.4.2 (doubt that this is really an option)?

I prefer not to use Automatix at this time just because my system started as Warty and upgraded via 'dist-upgrade' first to hoary and then again to breezy (definitely not a fresh install).

Plus, it is good if I learn to how to this manually.....

It would be much appreciated if someone can suggest how to do this......

Dr. Hood

---

### Post by knalle on 2006-02-23
since you installed 1.4.2 manually i would recomend you to remove it before you install 1.5.

i have both 1.4.2 and 1.5 running and can switch between them with 

**sudo update-alternatives --config java**

but that doesn't work if you have installed 1.4.2 manually

---

### Post by lamego on 2006-02-23
You should remove the 1.4.x and simply install the 1.5.x as you did for the previous version.

---

### Post by ahood on 2006-02-23
Thanks for the input...

How do I uninstall Java 1.4.2?

It is not clear how this should be done. I have searched the Ubuntu forum, Google, and the Java website, but I don't have a clear procedure.

Any pointers will be greatly appreciated.

Dr. Hood

---

### Post by jbennett on 2006-02-23
[QUOTE=ahood]Thanks for the input...

How do I uninstall Java 1.4.2?

It is not clear how this should be done. I have searched the Ubuntu forum, Google, and the Java website, but I don't have a clear procedure.

Any pointers will be greatly appreciated.

Dr. Hood[/QUOTE]

Read [this thread]("http://ubuntuforums.org/showthread.php?t=76754&page=6").  The original posting is a Howto for installing Java manually, but at the end it explains how to remove it if you ever wanted to (and if you need a refresher on how to install java manually, this howto works wonderfully. Just don't forget to modify the commands to the correct filename, since this howto was written for an older version of java).

---

### Post by ahood on 2006-02-23
Thanks a bunch, everyone has provided great feedback.

It is hugely appreciated.

I will try the suggestions and report my experience.

Dr. Hood

---

### Post by ahood on 2006-02-24
Need a bit more help.

I uninstalled jre1.4.2_05 and installed jre1.5.0_06 using the instructions [**[COLOR="Blue"]HERE[/COLOR]**](http://ubuntuforums.org/showthread.php?t=76754). I followed the instructions exactly.

Java seems to be working, except Firefox still reports that it is using jre1.4.2_05 when I use 'about:plugins'

I have added the libjavaplugins_oji.so that is linked to jre1.5.2_06 to various mozilla/firefox plugin directories (/usr/lib/mozilla/plugins ; /usr/lib/mozilla-firefox/plugins ; /home/alan/.mozilla/plugins

However, the problem persists.

Any ideas on how to get Firefox to report the correct plugin?

Dr. Hood

---

