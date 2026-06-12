---
title: "Ubuntu -&gt; Kubuntu"
date: 2006-03-14
forum: General Help
---

### Post by GoodPanos on 2006-03-14
I mostly use Ubuntu and just recently installed the KDE interface (Kubuntu) and I'm beginning to like Kubuntu (KDE). There is a whole bunch of applications that I installed on the Ubuntu side which I would also like to appear on the Kubuntu side i.e. Firefox. Is there a way to do that without having to install the complete application again?

---

### Post by jetpeach on 2006-03-14
Hmm, I've done the same thing you have a while ago, and I believe my applications just showed up under the KDE menu.  If they haven't, you might try  using the menu editor (right click the bottom left K button) to add any programs.  You definitely do NOT have to reinstall the applications.

---

### Post by zexoc on 2006-03-14
i'd like to try the same, do you mind going through the steps involved?

i've tried: 

```
sudo apt-get update
sudo apt-get install kubuntu-desktop
```

but get a 'cant find package error'

---

### Post by ElijahLofgren on 2006-03-14
[QUOTE=zexoc]i'd like to try the same, do you mind going through the steps involved?

i've tried: 

```
sudo apt-get update
sudo apt-get install kubuntu-desktop
```

but get a 'cant find package error'[/QUOTE]

Are you sure you type kubuntu-desktop right? Because it works fine for me.

---

### Post by aysiu on 2006-03-14
Maybe your repositories list is empty.

Follow these instructions:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Then try to install *kubuntu-desktop*.

---

