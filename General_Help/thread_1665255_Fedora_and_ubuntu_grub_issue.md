---
title: "Fedora and ubuntu grub issue"
date: 2011-01-12
forum: General Help
---

### Post by windupclock on 2011-01-12
I have a computer that only runs ubuntu and have decided to put fedora on. I put fedora on the computer and made a new partition for it. When I turn the computer on, it logs straight into fedora not even showing me a grub menu. Is there some way that I can update grub so that it knows that ubuntu is also installed

---

### Post by sikander3786 on 2011-01-12
From Fedora's Terminal, run this command.

```
sudo update-grub
```

If Ubuntu is listed there, you are ready to go. If not, please post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

While posting, click the # icon in post menu and paste your text in between the generated [code] tags.

---

