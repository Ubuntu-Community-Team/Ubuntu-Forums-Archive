---
title: "youtube advanced uploader - noone has this working in real life?"
date: 2010-12-10
forum: General Help
---

### Post by branscombe_richmond on 2010-12-10
[quote=youtube]You do not have Java installed or enabled. You can learn more about enabling Java, or go back and try the standard upload page.


[/quote]

i have seen this error message all over the internet about ubuntu and youtube.  whats the deal?  do people in the real world out there really not get advanced uploading with ubuntu?


how far behind the modern times is ubuntu, i sometimes wonder.  it has so much potential and yet there are still so many holes.  why have a 6 month update release when what we are given is generally not up to par one hundred percent?



anyway, enough thinking out loud - please disregard that as the main-stay of your reply, the real issue is:  does anyone out there have youtube advanced uploading capabilities, and if so - how?


before you ask, yes i have java installed, and as many other people, when i test my java here [ [http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml) ] it works.




```
ubuntu info:
You are using Ubuntu 10.04 LTS - the Lucid Lynx - released in April 2010 and supported until April 2013.



```

---

### Post by wewa on 2010-12-10
> For anyone playing with the new Ubuntu 10.04, you may be as surprised as I was to find that the sun-java6 packages are no longer included in the default repositories. The proprietary packages from Sun Oracle have been swapped out for the open source openjdk implementation. After stumbling around in the dark for a bit, I managed to figure out that the installation is quite simple:

sudo apt-get install openjdk-6-jre icedtea6-plugin

After installation, be sure to restart Firefox and double-check that the plugin has been installed by going to “about:plugins” in the address bar. You can search for “java” to make sure the plugin exists.

[source]("http://whatan00b.com/firefox-java-plugin-on-ubuntu-10-04")

---

### Post by JOHNNYG713 on 2010-12-10
There are various up-loaders available here is one ! [http://gnome-look.org/content/show.php/YouTube+Uploader?content=135863](http://gnome-look.org/content/show.php/YouTube+Uploader?content=135863)

Users of Firefox have but to search add-ons to find the uploaders of there choice !
[URL="http://gnome-look.org/content/show.php/YouTube+Uploader?content=135863"]
[/URL]

---

### Post by branscombe_richmond on 2010-12-10
i'm using chrome, as well, having to use a 3rd party option seems rather dismal in terms of overall development.  is it that hard to bring ubuntu up to the same level as, i don't know - properly executing java for all pages?

why the need for so many addons, these, and those?



as well, if anyone has any more information on how whether ubuntu does support the youtube advanced uploading **as well as** facebook advanced (regular now) uploader (without having to use the "classic" 5 files at a time uploader) please help.

---

### Post by branscombe_richmond on 2010-12-10
> **wewa said:**
> [source]("http://whatan00b.com/firefox-java-plugin-on-ubuntu-10-04")



please see also:
[quote=branscomeb_richmond]before you ask, yes i have java installed, and as many other people, when i test my java here [ [http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml) ] it works.


[/quote]




```
death@death-desktop:~$ sudo apt-get install openjdk-6-jre icedtea6-plugin
[sudo] password for death: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
openjdk-6-jre is already the newest version.
openjdk-6-jre set to manually installed.
icedtea6-plugin is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
death@death-desktop:~$


```

---

### Post by wewa on 2010-12-11
After installing icedtea and restarting, I get a 'Loading...' message now in youtube, but the bottom status of firefox says:
Applet: Not started.

Now what? :(

---

### Post by lexen on 2011-02-24
Has there been any progress getting this to work?

---

### Post by slim_pickins on 2011-05-24
does ubuntu yet support the full select multiple files upload capability on facebook yet?

has the youtube advanced uploader been worked on yet?

---

### Post by lexen on 2011-05-25
I haven't been able to get either of them to work.

---

