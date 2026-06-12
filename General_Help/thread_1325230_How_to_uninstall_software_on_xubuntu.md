---
title: "How to uninstall software on xubuntu?"
date: 2009-11-13
forum: General Help
---

### Post by n0name666 on 2009-11-13
Hi,
I have a question, mainly I have installed polish communicator ( [http://www.tlen.pl/download_linux.php](http://www.tlen.pl/download_linux.php) ) but it stopped connecting and I would like to remove it and install it once again. I was looking for answers for xubuntu and I found rpm and yum packages but I still cant get rid of it. Is there a simpler way ? (there is no entry in add/remove applications)
I'm sorry but I'm new in linux environment.
All the best,
n0name

---

### Post by coldReactive on 2009-11-13
If the bin provided there does not come with an uninstall method via terminal (accessories > terminal under applications menu) then you're sunk.

---

### Post by jollysnowman on 2009-11-13
Open up synaptic and see if you can find the associated packages.

---

### Post by n0name666 on 2009-11-13
Unfortunately there is nothing connected to "tlen" in synaptic :/

---

### Post by 6205 on 2009-11-13
In this case you have to delete it manually from harddrive. I suggest you to search for "tlen" through search files utility and simply delete all related folders/files through nautilus launched in super-user mode ([COLOR="DarkRed"]sudo nautilus[/COLOR] in terminal)

But only if you cannot find it in Synaptic. But propably not, because it was not installed from *.deb file. What is Tlen good for anyway? IMHO Empathy or Skype are much more widely adopted.

---

### Post by coldReactive on 2009-11-13
> **6205 said:**
> In this case you have to delete it manually from harddrive. I suggest you to search for "tlen" through search files utility and simply delete all related folders/files through nautilus launched in super-user mode ([COLOR="DarkRed"]sudo nautilus[/COLOR] in terminal)

But only if you cannot find it in Synaptic. But propably not, because it was not installed from *.deb file. What is Tlen good for anyway?

If you ask me, reinstalling xubuntu is better than doing that and potentially causing boot/package cache issues/etc.

---

### Post by n0name666 on 2009-11-13
I think that I leave it broken then, I'm not sure if I am able to delete those files without causing some serious damage ;) I'm using tlen only because many ppl in Poland is using it, but I've found plugin for pidgin which is working perfectly so I believe that topic is closed ;)
Thank you for your help anyway,
all the best,
n0name

---

