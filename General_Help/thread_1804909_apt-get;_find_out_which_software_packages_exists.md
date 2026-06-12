---
title: "apt-get; find out which software packages exists"
date: 2011-07-15
forum: General Help
---

### Post by Wim Sturkenboom on 2011-07-15
Slowly but surely learning to live without synaptic. How do I find out which packages exists (and what they do) using apt-get?

*man apt-get* does not give the answer or I don't see it in there.

---

### Post by Toz on 2011-07-15
To list all installed packages:
```
dpkg -l
```

To search for a package:
```
apt-cache search <search_term>
```

To show install info about a specific package:
```
apt-cache policy <package>
```

To show more info about each package:
```
apt-cache show <package_name>
```

To show package dependencies:
```
apt-cache depends <package>
```

This link will help: [https://help.ubuntu.com/community/AptGet/Howto]("https://help.ubuntu.com/community/AptGet/Howto")

---

### Post by nothingspecial on 2011-07-15
^^ He copied me :)

---

### Post by oldos2er on 2011-07-15
> **Wim Sturkenboom said:**
> Slowly but surely learning to live without synaptic. 

Why do you have to live without Synaptic?

---

### Post by Wim Sturkenboom on 2011-07-15
Thanks for the replies. More reading to do.

Obviously not 100% clear; I'm looking for the opposite of dpkg -l (showing non-installed packages)

And why? I don't want to have the need for a GUI on a server.

---

### Post by nothingspecial on 2011-07-15
> **Wim Sturkenboom said:**
> I'm looking for the opposite of dpkg -l (showing non-installed packages)


This will show you every package available that isn't installed (I think -- there may be some parts of dpkg I don't fully understand). Be warned, there's 1000's of them.

```
apt-cache pkgnames | sort -d | grep -v "$(dpkg -l | sed 's/^ii  //;s/ .*$//')"
```

The sort -d bit is only necessary if you want the output in alphabetical order.

Be prepared for lib^10000

---

### Post by oldos2er on 2011-07-15
> **Wim Sturkenboom said:**
> And why? I don't want to have the need for a GUI on a server.

Ok, I didn't realize this was for a server. I recommend you learn **aptitude**, which is sort of like a CLI version of Synaptic only more powerful. Also install **aptitude-doc-en** to help you get started.

---

### Post by CatKiller on 2011-07-15
Another vote for aptitude.

```
aptitude show *package-name*
aptitude search *something-interesting*
```

---

### Post by Wim Sturkenboom on 2011-07-16
Ah, the beauty of choice :D Will play with them.

Reason for 'apt-get' in the title was that it is the one that most often comes along in replies. And I just want to learn one properly.

---

