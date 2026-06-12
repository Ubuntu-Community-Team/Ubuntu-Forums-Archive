---
title: "Want to install Sun Java 6 plugin - why is Firefox 3.0 part of the package ?????"
date: 2009-08-07
forum: General Help
---

### Post by brjoon1021 on 2009-08-07
I have Swiftfox 3.5 installed and no instance of Firefox. I just want Java, why do I have to install Firefox 3.0 and 3.0 branding to get it ?

B.

---

### Post by burmanabhay88 on 2009-08-07
How are you trying to install the plugin. From the website or using Add Remove or Synaptic????

---

### Post by brjoon1021 on 2009-08-07
synaptic. I have tried before and am unable to install from Sun, too geeky.

---

### Post by burmanabhay88 on 2009-08-07
I wanted to advice the site... but I guess that's out.
There's one more thing you can do.
Install Sun Java Plugin from the add remove applications.
That should do it.
If it doesn't work, then you'll need to add a symbolic link.

---

### Post by brjoon1021 on 2009-08-07
Thanks for your help, but it is even worse. Add/remove programs makes absolutely no mention at any time about installing Firefox 3.0, BUT surprise ! it does. Is Debian like this - you can't install a lot of things unless they are part of huge metapackages ?

I want to install openoffice, it installs some kind of Java with it. Will that get it done ? Would that cover the same bases that the sun java 6 plugin covers ?

---

### Post by burmanabhay88 on 2009-08-07
> **brjoon1021 said:**
> Thanks for your help, but it is even worse. Add/remove programs makes absolutely no mention at any time about installing Firefox 3.0, BUT surprise ! it does. Is Debian like this - you can't install a lot of things unless they are part of huge metapackages ?

I want to install openoffice, it installs some kind of Java with it. Will that get it done ? Would that cover the same bases that the sun java 6 plugin covers ?

NO... :P. You make debian sound like the devil. Umm.... In lay man terms...See, there are somethings known as dependencies. If you are installing a plugin, it assumes that you need the main software as well.

Sorry couldn't help you out with your problem though.

---

### Post by burmanabhay88 on 2009-08-07
> **brjoon1021 said:**
>  I want to install openoffice, it installs some kind of Java with it. Will that get it done ? Would that cover the same bases that the sun java 6 plugin covers ?

Open office requires Java Runtime Environment, which is a different thing all together. Open office is written in JAVA, so it needs a JRE.

---

### Post by CatKiller on 2009-08-07
> **brjoon1021 said:**
> I have Swiftfox 3.5 installed and no instance of Firefox. I just want Java, why do I have to install Firefox 3.0 and 3.0 branding to get it ?

A browser plugin needs a browser to be installed. It doesn't have to be Firefox, it could be IceWeasel, IceApe, Mozilla, Epiphany or Galeon. Swiftfox might just be a faster Firefox, but unless the package says "provides: firefox" then the package manager has no way of knowing that.

> **brjoon1021 said:**
> Add/remove programs makes absolutely no mention at any time about installing Firefox 3.0

Why would it? Add/Remove is not the tool for complex dependency-management. It's a tool for beginners whose only function is to allow the user to say, "I want this thing. Make it happen."

---

### Post by burmanabhay88 on 2009-08-07
catkiller's put it very aptly... I guess that puts some light on how things work, but still doesn't solve your problem.

---

### Post by brjoon1021 on 2009-08-07
"Swiftfox might just be a faster Firefox, but unless the package says "provides: firefox" then the package manager has no way of knowing that."

Is there some tricky way of fooling the package manager by editing some code somewhere ?

Or,

Have you seen an EASY and especially complete tutorial on installing the Java plugin for Firefox from the Sun download? Easier and clearer than the Sun directions, which assume some terminal skills. It always assumes more Linux knowledge than I have... I've never been able to get it done.

B.

---

### Post by CatKiller on 2009-08-08
> **brjoon1021 said:**
>  Is there some tricky way of fooling the package manager by editing some code somewhere ?

Not that I know of. I know that it is possible to change the handling of "recommended" packages, but installing packages that another package depends on is pretty fundamental to what a package manager does. There might be some way of doing it with *dpkg* (the back-end to the back-end of the package management system) using some kind of force option, but I've not ever tried anything like that.

If sun-java6-plugin actually works with swiftfox (I don't know for sure that it does, although it might well) then you could file a bug report against the sun-java6-plugin package to get them to add a dependency to swiftfox as well as the others or, if the plugin is sufficiently abstract, to www-browser. Since swiftfox isn't included in the Ubuntu repositories, I don't know that such a fix would make it into the Ubuntu package, though.

> 
Have you seen an EASY and especially complete tutorial on installing the Java plugin for Firefox from the Sun download? Easier and clearer than the Sun directions, which assume some terminal skills. It always assumes more Linux knowledge than I have... I've never been able to get it done.

I haven't looked into it at all, I'm afraid. Normally command-line instructions can just be copied-and-pasted.

---

### Post by martinbaselier on 2009-08-09
Which package are your trying to install ?

I just did a dependency check on sun-java5-jre and sun-java6-jre and I don't see firefox anywhere as a dependency.

---

### Post by Mark76 on 2009-08-09
He's trying to install the sun-java6-plugin

It's in the repos

---

