---
title: "Typo in add-apt-repo... how to remove repo again?"
date: 2011-01-18
forum: General Help
---

### Post by paxsali on 2011-01-18
Hi everybody, just a quick one...

I wanted to try out unity-2d for ubuntu 10.10 by adding it's repo first via add-apt-repository <repo>. However, on the first try I mistyped <repo>. Now everytime I run apt-get update it updates all repos correctly, but gives an error (repo <rpeo> not found, "rpeo" is the way I mistyped it...).

How can I remove-apt-repository?

I looked into /etc/apt/sources.list first, but couldnt find none of the (correctly/accidentally) added repos from add-apt-repos.

Could anyone give me a hint?

Thanks, bye.

---

### Post by nothingspecial on 2011-01-18
Look in

```
/etc/apt/sources.list.d/
```

notice the .d at the end. That`s where apt-add-repository puts it`s sources. It`b be nice if they told you that wouldn`t it ;)

---

### Post by David006 on 2011-10-18
> **paxsali said:**
> How can I remove-apt-repository?

Either syntax will work:

  sudo add-apt-repository --remove ppa:coolcodebase/ppa
  sudo add-apt-repository -r ppa:coolcodebase/ppa

NOTE: Erroneously prompts with '.. about to **add** the following ..', which you can safely ignore.

---

