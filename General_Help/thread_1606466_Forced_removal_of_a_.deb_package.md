---
title: "Forced removal of a .deb package?"
date: 2010-10-26
forum: General Help
---

### Post by casbahdk on 2010-10-26
I have installed the newest version of Peppermint Ice (Ubuntu derivative) on my Eee PC 701's internal HD and would like to get some more space on the drive (2GB total) by removeing packages like hunspell-en-ca, but synaptic warns me that language-support-writing-en will be removed. How can I force removal of this and similar packages like myspell-en-au, without uninstalling English language support?

---

### Post by NertSkull on 2010-10-26
So this may get you in trouble, so I would probably read up on it before using it.

But I believe you can use the --force-yes switch to make it do stuff.

There's a section on it in the apt-get manual (man apt-get).

May do what you want. 

Or, may destroy your system.

Or maybe it will do nothing at all

There may be a better way to do what you want, thats the best I have at this point.

---

### Post by casbahdk on 2010-10-27
> **NertSkull said:**
> So this may get you in trouble, so I would probably read up on it before using it.

But I believe you can use the --force-yes switch to make it do stuff.

There's a section on it in the apt-get manual (man apt-get).

May do what you want. 

Or, may destroy your system.

Or maybe it will do nothing at all

There may be a better way to do what you want, thats the best I have at this point.

Cheers. I'll take a look at the apt-get manual. I have seen some postings mentioning dpkg, but that seems to be when a package that has been installed manually, isn't behaving. Is dpkg a possibility as well for my situation?

It seems weird to me that users are forced to have Australian or other versions of English on their system, when they don't use them. Linux is about choice.

---

