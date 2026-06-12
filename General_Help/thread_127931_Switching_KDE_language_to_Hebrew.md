---
title: "Switching KDE language to Hebrew"
date: 2006-02-10
forum: General Help
---

### Post by dotancohen on 2006-02-10
On Kubuntu 5.10, I tried to set the interface language to Hebrew. I opened the System Settings -> Regional and Accessability -> Country/Region and Language. I chose Israel from the list, but the only languages listed in Add Language are US English and British English.

What can I do to have Hebrew added to this list? I know that this is possible because on Fedora Hebrew is there.

Thank you in advance.

Dotan Cohen
[http://technology-sleuth.com/index.php](http://technology-sleuth.com/index.php)

---

### Post by raggamuffin on 2006-02-10
in konsole,

```
sudo apt-get install language-pack-kde-he-base language-pack-kde-he
```

then Hebrew should be an options in the Country/Region and Language menu...

---

### Post by dotancohen on 2006-02-11
Thank you!
I actually found a page in the wiki for making Kubuntu 'speak' Hebrew.

---

