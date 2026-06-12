---
title: "From where to download kde 4.3 .deb s"
date: 2009-08-15
forum: General Help
---

### Post by praveesh on 2009-08-15
In download.kde.org and in the mirrors, I found only binary packages for the suse and for mandriva(and the source). From where can I download the binary packages for Ubuntu?

---

### Post by Screwdriver0815 on 2009-08-15
you have to enable a Launchpad ppa:

deb [http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu) jaunty main

and after that verify the keyring:

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 8AC93F7A  
```

then you do

```
sudo apt-get update
```

and 

```
sudo apt-get dist-upgrade
```

if you already have installed KDE 4.2

But note: if you have any third-party widgets or similar programs which are connected to the desktop system, it is most likely that you run into trouble with this update.

If you have Gnome, you first have to install the kubunut-desktop and after that enable the ppa and do the update. But in this case I don't know how it works or if there are any obstacles you might face.

---

### Post by praveesh on 2009-08-15
Thanks for the reply.Iam having Ubuntu jaunty without kde. I don't have internet on this computer. If I download packages individually from the kUbuntu backport ppa , will it work fine? I think installing kUbuntu-desktop will include the softwares like kpackagekit and kUbuntu boot splash . Can I get the kde alone?

---

### Post by Screwdriver0815 on 2009-08-15
> **praveesh said:**
> Thanks for the reply.Iam having Ubuntu jaunty without kde. I don't have internet on this computer. If I download packages individually from the kUbuntu backport ppa , will it work fine? I think installing kUbuntu-desktop will include the softwares like kpackagekit and kUbuntu boot splash . Can I get the kde alone?
I don't think that this works because in the ppa you only have the upgrade-files which should be installed through the packagemanager. There is no .deb file which can be executed.

maybe you find what you are looking for on [http://www.kde.org/download/](http://www.kde.org/download/)

---

### Post by Bachstelze on 2009-08-15
> **Screwdriver0815 said:**
> I don't think that this works because in the ppa you only have the upgrade-files which should be installed through the packagemanager. There is no .deb file which can be executed.

[ORLY?]("http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu/pool/main/k/kdebase/")

@praveesh: it is possible, but it could be quite complicated. You could try to move the repo on a CD using [APTonCD]("https://help.ubuntu.com/community/APTonCD").

---

### Post by praveesh on 2009-08-15
> **HymnToLife said:**
> [ORLY?]("http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu/pool/main/k/kdebase/")
@praveesh: it is possible, but it could be quite complicated. You could try to move the repo on a CD using [APTonCD]("https://help.ubuntu.com/community/APTonCD").
Thanks . I shall try to download debs from the backport.

---

### Post by Screwdriver0815 on 2009-08-15
> **HymnToLife said:**
> [ORLY?]("http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu/pool/main/k/kdebase/")

@praveesh: it is possible, but it could be quite complicated. You could try to move the repo on a CD using [APTonCD]("https://help.ubuntu.com/community/APTonCD").
upps I didn't see it... sorry

---

