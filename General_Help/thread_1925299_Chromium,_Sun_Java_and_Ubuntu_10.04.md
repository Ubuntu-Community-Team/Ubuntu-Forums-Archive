---
title: "Chromium, Sun Java and Ubuntu 10.04"
date: 2012-02-14
forum: General Help
---

### Post by AChampion on 2012-02-14
Hi all

I'm new to being an administrator for linux systems, have previously just been a user.

I'm using Google Chromium (16.0.912.77) on Ubuntu 10.04 32-bit. I'm trying to get Sun's Java plugin to work on Chromium, I need the Sun plugin to use with the juniper network VPN.

I've installed the plugin:

/usr/lib/jvm/java-6-sun-1.6.0.26/jre/plugin/i386/ns7-gcc29/libjavaplugin_oji.so

I've created a symbolic link to this file in the Chromium plugin directory, which contains nothing else:

/usr/lib/chromium-browser/plugins

Checking about://plugins in Chromium it points to this file, and is enabled. However when I test the java plugin (via Sun's page) it states: No plug-in available to display this content

I've searched various solutions with no avail. I've checked:

sudo update-alternatives --config java

And it states that there is only one alternative in link group java. None of the other solutions I've found have helped. Can anyone suggest other things I should check/try?

Thanks

---

