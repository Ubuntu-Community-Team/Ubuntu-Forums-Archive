---
title: "Firefox checkCompatibility Work Around"
date: 2009-11-18
forum: General Help
---

### Post by lvleph on 2009-11-18
So if you are like me you like to use near bleeding edge Firefox. And if you are like me you have the extensions.checkCompatibility set to false. Well, most recently they changed this option in about:config to reflect your current version. What this means for the user is that your will have to add a new boolean to about:config every time you update. This is of course an annoyance. Anyway, here is a little hack to get around this annoyance. Now be warned that this could eventually prevent you from using firefox once you update, just like the old checkCompatibility would have. So if firefox is crashing on you start firefox without extensions and then enable them one by one. So what we are going to do is change the install.rdf files to have a later maxVersion. First we will back up all install.rdf files:
```
 for fname in $(find -name install.rdf); cp -f ${fname} ${fname}.bak; done
```

Now let's look for the line and change the maxVersion to 9.9:

```
for fname in $(find -name install.rdf); do sed 's/maxVersion>.\+<\/em/maxVersion>9.9<\/em/g' ${fname} > ${fname}.new && mv -f ${fname}.new ${fname}; done
```

You could change this to any version you like. To remove the bak files use the following, but only do it when you know everything is working.

```
 for fname in $(find -name install.rdf.bak); rm ${fname}; done
```

---

