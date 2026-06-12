---
title: "midori version"
date: 2010-01-10
forum: General Help
---

### Post by michiduta07 on 2010-01-10
Hello and sorry if it's in the wrong forum section.

I wanted to ask if you could update midori and related packages in the ubuntu repositories. 
Also if the repositories are different for each version of Ubuntu (Ubuntu, Kubuntu, Xubuntu, etc) could you update the packages for all versions? I am currently using Xubuntu 9.10.

Just to be sure I don't get misunderstood I am referring to being able to update to latest version of midori (currently 0.2.2) and related webkit and gtk using update manager. 

Thank you for reading this.

---

### Post by Praxicoide on 2010-01-11
The repositories are the same between the different flavors of Ubuntu. So regardless of which one you use, you will still have the same verion of Midori (currently at 0.19 in the Universe repositories).

If you want to get the latest verion, then you will need to add the ppa for midori and for webkit.

You need to open a terminal, and then enter the following commands:

First you add the ppas

```
sudo add-apt-repository ppa:midori

sudo add-apt-repository ppa:webkit-team
```

And then you update:

```
sudo apt-get update

sudo apt-get upgrade
```

You might have to reinstall webkit

```
sudo apt-get install webkit
```

If you get problems with the new repositories, you probably need to sign them:

```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2D9A3C5B

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com A69241F1
```

Followed by the update.

Hope this helps.

---

### Post by michiduta07 on 2010-01-11
Thx for your quick answer. ;)

---

