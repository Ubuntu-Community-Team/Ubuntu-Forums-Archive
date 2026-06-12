---
title: "zsh history"
date: 2012-10-13
forum: General Help
---

### Post by Fulgur on 2012-10-13
Hi guys,

I am having a little problem with zsh here. I got all my zsh files from my fedora install. In fedora zsh does single command history. E.g. I type "sud", press the up-arrow and it completes it to "sudo apt-get update" eventhough I didn't use that command for a while. In ubuntu this doesn't work. I looked through all my config files and I can't find it. I would really like to know how to get it working because this is a feature i really love about zsh. Any ideas?

Greets

---

### Post by conradin on 2012-10-14
Is this what youre looking for?
[http://manpages.ubuntu.com/manpages/precise/man1/zshexpn.1.html](http://manpages.ubuntu.com/manpages/precise/man1/zshexpn.1.html)
source
[https://launchpad.net/ubuntu/precise/+package/zsh](https://launchpad.net/ubuntu/precise/+package/zsh)

---

### Post by spjackson on 2012-10-15
If you install the zsh package and then run zsh without any personalization, it prompts you and lets you accept the default system configuration. This generates the attached .zshrc and the feature you described is enabled by this.

I hope that by comparing this with what you have, you should be able to get it working.

---

### Post by Fulgur on 2012-10-16
Thanks, guys. Got it working!

---

