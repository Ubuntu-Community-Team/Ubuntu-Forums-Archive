---
title: "application upgrades"
date: 2010-05-20
forum: General Help
---

### Post by dtdave on 2010-05-20
Hi I wanted to know if when you install applications in ubuntu,do you have to add the repository to have them auto update. The reason why I ask is I thought anything in the list of programs that you can install in ubuntu through its repository will get updated automatically when new versions come out. So why when I look at articles on ubuntu-tweak do I see many say you want to add the repository, when it is already in ubuntu's main.

thanks for any info.

---

### Post by sanderd17 on 2010-05-20
Only bugs will be updated. There will be no version updates if you install something via the repo's. The version updating of all apps happens twice a year (when a new version of ubuntu comes out). Working this way has the advantage that there are no major updates that can cause problems. The only problems you can encounter are those when you update ubuntu.

When you want major updates, you can add repo's to do that. That isn't encouraged if you just want to work on your computer.

---

### Post by toolfan2k4 on 2010-05-20
Its pretty easy to do yourself though. Especially through terminal.

```

sudo apt-get update
sudo apt-get upgrade
```

Its usually a pretty good idea to reboot after running updates.

Also, and this is optional. You can upgrade the kernel by running the following.

```

sudo apt-get update
supo apt-get dist-upgrade

```

---

### Post by dtdave on 2010-05-21
so what you are saying sanderd17 is that if I do not add the repo for a specific program, such as ubuntu tweak, I will only get bug fixes for that piece of software through the ubuntu OS updates. But, if I add the repo to ubuntu-tweak, and ubuntu tweak comes out with a new version, I will get the upgrade through the regular updates that come up for the OS when it searches what updates are available. Am I right or wrong here?? thanks!

---

### Post by sanderd17 on 2010-05-22
e.g.: I think you're working with Firefox 3.6.3. If you do nothing special (like upgrading Ubuntu or doing like toolfan2k4 showed) you will get Firefox 3.6.4 when it comes out but you'll never get Firefox 3.7. Of course the version numbers of each program are different, in Firefox they say the third number is used for bug fixes and the first to for major and normal upgrades.

You can see this in synaptic: when you download Firefox, you can chose Firefox 3.0, Firefox 3.5 ... but you don't choose Firefox 3.5.2.

Since the packages in apt don't change you'll never get a higher version of a program without doing something manual.

---

### Post by dtdave on 2010-05-24
thanks for your help!

---

