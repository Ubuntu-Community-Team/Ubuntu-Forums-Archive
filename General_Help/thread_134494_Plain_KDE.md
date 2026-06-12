---
title: "Plain KDE"
date: 2006-02-22
forum: General Help
---

### Post by gspr on 2006-02-22
Hi. I've recently started experimenting with Ubuntu/Kubuntu after several years as a Gentoo-only user. Things are beginning to look up for Ubuntu, but I'm still wondering about a few things, one of these being:

How can I get a plain, default KDE? By that I mean the KDE shipped by the KDE team, with the default KDE menus, default KDM style, etc. The stuff installed by Kubuntu is nice enough, but I'd really like the power to have plain (non-Ubuntu/Kubuntu-branded) versions of applications installed.

Thanks!

---

### Post by abhaysahai on 2006-02-22
Easy way is install from source. 
The Konstruct ( [http://developer.kde.org/build/konstruct/](http://developer.kde.org/build/konstruct/)) build toolset can help you downloading and installing KDE from source.

Check the compilation requirement here : "http://kde.org/info/requirements/3.5.php"

---

### Post by codejunkie on 2006-02-22
[QUOTE=gspr]Hi. I've recently started experimenting with Ubuntu/Kubuntu after several years as a Gentoo-only user. Things are beginning to look up for Ubuntu, but I'm still wondering about a few things, one of these being:

How can I get a plain, default KDE? By that I mean the KDE shipped by the KDE team, with the default KDE menus, default KDM style, etc. The stuff installed by Kubuntu is nice enough, but I'd really like the power to have plain (non-Ubuntu/Kubuntu-branded) versions of applications installed.

Thanks![/QUOTE]
on a clean system enable the multiverse and universe repos in your sources.lst file and enter ```
sudo apt-get install kde
```if you've already installed kubuntu you must completly remove all of the kubuntu specific packages in synaptic first this should give you a plain kde install.

---

### Post by abhaysahai on 2006-02-22
[QUOTE=codejunkie]on a clean system enable the multiverse and universe repos in your sources.lst file and enter ```
sudo apt-get install kde
```if you've already installed kubuntu you must completly remove all of the kubuntu specific packages in synaptic first this should give you a plain kde install.[/QUOTE]

Does kubuntu archives not contain kubuntu costomized KDE. 
He is from gentoo community so would not like any modifications, and installing from source will be a cake walk for him.

---

### Post by codejunkie on 2006-02-22
[QUOTE=abhaysahai]Does kubuntu archives not contain kubuntu costomized KDE. 
He is from gentoo community so would not like any modifications, and installing from source will be a cake walk for him.[/QUOTE]
if you install the kubuntu packages such as kubuntu-desktop etc, yes then you'll be getting there customised version of kde. if you install the kde meta package that i mentioned eariler you will get the basic kde install without any of the kubuntu tweaks.

---

### Post by Jeffery Mewtamer on 2006-02-22
Question:

In Synaptic:
Is right-clicking => remove completely on Kubuntu-Desktop suffient to remove Ubuntu's Customized KDE? Or is there other packages that need to be remove individually?

---

### Post by codejunkie on 2006-02-22
[QUOTE=Jeffery Mewtamer]Question:

In Synaptic:
Is right-clicking => remove completely on Kubuntu-Desktop suffient to remove Ubuntu's Customized KDE? Or is there other packages that need to be remove individually?[/QUOTE]
no just removing the kubuntu-desktop meta package will not remove all the packages it installs, there's a thread on here showing how to complelety remove it when i find the link i'll post it here.

---

### Post by Jucato on 2006-02-22
Or you could also do a server install so that no GUI would be installed, and then apt-get kde. I might try that out myself if I find reason to.

OT: what do you mean by power that KDE has that Kubuntu doesn't? I'm really curious about this.

---

