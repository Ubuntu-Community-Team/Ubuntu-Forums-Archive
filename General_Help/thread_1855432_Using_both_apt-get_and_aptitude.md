---
title: "Using both apt-get and aptitude"
date: 2011-10-06
forum: General Help
---

### Post by QueenKwong on 2011-10-06
Only today i've read several pages that say it is a mistake to use both aptitude and apt-get - i.e. synaptic - alternatingly.

I don't know anymore which packages I installed with aptitude and which ones using synaptic, but from what I understand, something is probably messed up by now.

I am using Ubuntu 10.04, Netbook remix.
What should I do to resolve any inconsistencies between aptitude and synaptic, or is that not necessary?

Thanks, QueenKwong

edit:
[http://raphaelhertzog.com/2011/06/20/apt-get-aptitude-%E2%80%A6-pick-the-right-debian-package-manager-for-you/]("http://raphaelhertzog.com/2011/06/20/apt-get-aptitude-%E2%80%A6-pick-the-right-debian-package-manager-for-you/")
solved: The problem seems to no longer exist, according to Raphael Hertzog:
" It used to be annoying when apt-get did not track which packages were  automatically installed while aptitude did, but now that both packages  share this list, there&#8217;s no reason to avoid switching back and forth."

---

### Post by CharlesA on 2011-10-06
Hi,

I've moved your post to it's own thread. The original thread you posted in can be found [here]("http://ubuntuforums.org/showthread.php?t=1722843").

apt-get and aptitude are both just frontends for dpkg. I don't think there's any real reason to use one or the other or both.

---

### Post by haqking on 2011-10-06
> **QueenKwong said:**
> Only today i've read several pages that say it is a mistake to use both aptitude and apt-get - i.e. synaptic - alternatingly.

I don't know anymore which packages I installed with aptitude and which ones using synaptic, but from what I understand, something is probably messed up by now.

I am using Ubuntu 10.04, Netbook remix.
What should I do to resolve any inconsistencies between aptitude and synaptic, or is that not necessary?

Thanks, QueenKwong

edit:
[http://raphaelhertzog.com/2011/06/20/apt-get-aptitude-%E2%80%A6-pick-the-right-debian-package-manager-for-you/]("http://raphaelhertzog.com/2011/06/20/apt-get-aptitude-%E2%80%A6-pick-the-right-debian-package-manager-for-you/")
solved: The problem seems to no longer exist, according to Raphael Hertzog:
" It used to be annoying when apt-get did not track which packages were  automatically installed while aptitude did, but now that both packages  share this list, there’s no reason to avoid switching back and forth."

A similar question was raised the other day.

see here [http://ubuntuforums.org/showthread.php?t=1854074](http://ubuntuforums.org/showthread.php?t=1854074)

---

### Post by Lars Noodén on 2011-10-06
As CharlesA mentioned, they are all just front-ends for the same package manager, [dpkg](http://manpages.ubuntu.com/manpages/oneiric/en/man1/dpkg.1.html).  Everything goes into the same database, so there is no problem in switching between the tools.

---

### Post by el_koraco on 2011-10-06
> **QueenKwong said:**
> edit:
[http://raphaelhertzog.com/2011/06/20/apt-get-aptitude-%E2%80%A6-pick-the-right-debian-package-manager-for-you/](http://raphaelhertzog.com/2011/06/20/apt-get-aptitude-%E2%80%A6-pick-the-right-debian-package-manager-for-you/)
solved: The problem seems to no longer exist, according to Raphael Hertzog:
" It used to be annoying when apt-get did not track which packages were  automatically installed while aptitude did, but now that both packages  share this list, there’s no reason to avoid switching back and forth."

Yup, I was just about to link that. RH is the maintainer and developer of dpkg, so you can't get this from a higher authority.

---

