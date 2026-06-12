---
title: "Flash Player &quot;Suggested Packages&quot; -- What do they do?"
date: 2012-06-26
forum: General Help
---

### Post by nrundy on 2012-06-26
When trying to install "flashplugin-installer" I'm presented with "Suggested Packages" that I should install:

x-ttcidfont-conf 
ttf-mscorefonts-installer 
ttf-bitstream-vera 
ttf-dejavu 
ttf-xfree86-nonfree 
xfs

The ttf-mscorefonts-installer I understand. Lord knows why someone would copyright a font. But what about the others? They appear to be all fonts. But what is x-ttcidfont-conf?

Do I really need to install these fonts? What happens if I dont, will Flash Player not present some material correctly?

---

### Post by josephmills on 2012-06-26
in your terminal you can find out all about packages and what they do/are 

```
apt-cache search <name of package>
```
```
apt-cache show <name of package>
```
there are many ways to do this but there are two I am sure that others will show other ways but that is what I do.

---

### Post by nrundy on 2012-06-26
> **josephmills said:**
> in your terminal you can find out all about packages and what they do/are 

```
apt-cache search <name of package>
``````
apt-cache show <name of package>
```there are many ways to do this but there are two I am sure that others will show other ways but that is what I do.

Yes, I have looked these up. But it doesn't really tell me what they are needed for. I was hoping someone might have some more direct experience or knowledge to share about these packages and why they are associated with Flash Player.

---

