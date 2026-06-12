---
title: "Need to reconstruct corrupted /var/lib/dkg directory structure"
date: 2011-04-18
forum: General Help
---

### Post by sergiodlc on 2011-04-18
Hi:

I have a Xen box where I host my website. It runs Ubuntu 10.04. I realized today that I can't upgrade or install packages because pretty much everything in /var/lib/dpkg is missing. I have googled this and found [[COLOR="DarkRed"]this thread[/COLOR]]("https://answers.launchpad.net/ubuntu/+source/synaptic/+question/12093") that suggests a script to reconstruct the directory structure. However, I'm not very sure about it since I don't know how up to date the script.

I read [[COLOR="DarkRed"]this guide[/COLOR]]("http://qref.sourceforge.net/Debian/reference/ch-package.en.html#s-rescue-var") where is said that finding a compressed [FONT="Courier New"]/var[/FONT] directory from a clean install I could solve my problems.

I'm not sure of what to do and I'm afraid of corrupting my system even more. Can you help me, please?

Anybody?

---

### Post by sergiodlc on 2011-04-25
Unfortunately I didn't get any response for my question. After several hours looking for a solution I read [this thread on how to regenerate the /var/lib/dkg]("https://answers.launchpad.net/ubuntu/+question/5435"). The comments of Dennis P. Nikolaenko were the key to solve my problem.

I tried what he suggested there but it failed. Then I realized that my /var/lib/dpkg/info/ directory was missing so I manually created it (sudo mkdir /var/lib/dpkg/info/) and then repeated Nikolaenko's instructions. After that everything worked like a charm... almost.

I was allowed to install any package but every time I ran apt-get it complained about some trouble with the gnupg-curl package. I removed that package and manually deleted the files in /usr/lib/gnupg/ and reinstalled the package afterwards. Everything begun to work again without issues.

---

### Post by fdrake on 2011-04-25
so did you solve your problem? if yes i am glad for you

---

