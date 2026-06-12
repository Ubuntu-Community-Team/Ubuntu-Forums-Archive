---
title: "Downloading the pkgs from repositories without installing them"
date: 2010-02-02
forum: General Help
---

### Post by madmax.santana on 2010-02-02
Guys we all know that packages in repositories are particularly most reliable and secure.
What I want to do is,download the packages from repositories and keep'em. If you know what I mean. I have two machines running Ubuntu and I don't want to download packages by apt-get separately. I want to apt-get install for one machine and then copy the downloaded packages into the hard drives of other machine and execute the deb files. Is that possible? Keeping the packages after they have been installed?

---

### Post by wojox on 2010-02-02
Take a look in /var/cache/apt/archives/ that's were it puts them.

---

### Post by Leppie on 2010-02-02
as long as you don't issue the apt-get clean command, they should be in that folder.

---

### Post by bodhi.zazen on 2010-02-02
I suggest looking at Aptoncd

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

Or you could configure a local repository, but that may be more hassle then you want.

To download a deb, without installing it , use the -d flag

```
sudo apt-get install -d foo
```

[http://linux.die.net/man/8/apt-get](http://linux.die.net/man/8/apt-get)

---

### Post by madmax.santana on 2010-02-04
Thanks pals. That was really some help.

One more thing. I am dual booting windows. And I am using a very good download manager in Windows. If I wanted to download the deb files in Windows through the download manager, just like I do for other files, (I look for a direct download link and then click on it ;)), would there be a website or could I download from repos like that?

---

### Post by Leppie on 2010-02-04
you can download all official ubuntu packages from here: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

