---
title: "How can I disable Alt+Space shortcut in 12.04?"
date: 2012-05-18
forum: General Help
---

### Post by loopum on 2012-05-18
Hi all,

I tried "keyboard->shortcut" but didn't work. 
It seems this particular Alt+space(window menu) cannot be disabled.
I'm an emacs user and have been using alt+space for set-mark years. 
I want to force-disable it at any cost.

I will greatly appreciate it if someone can give me some help/hints on this!

---

### Post by lukeiamyourfather on 2012-05-18
Sounds like it might be from Compiz. To edit the Compiz configuration there's a neat utility.

```
sudo apt-get install compizconfig-settings-manager
```

Though if you don't know what a particular feature does, probably best to leave it alone and just look for the Alt + Space shortcut.

---

### Post by loopum on 2012-05-18
Thank you! I have installed that. But it seems there are too many categories and I can't find the shortcut configuration. Could you tell me where is the shortcut thing located?

---

### Post by loopum on 2012-05-18
I disabled all the shortcuts in the Ubuntu Unity Plugin section of Compizconfig.
But the alt+space still prompts window menu. Nothing changed.

---

### Post by loopum on 2012-05-18
YES! IT's in CompizConfig->general options->key bindings: window menu!
I killed it. so happy!
Thank you so much!

---

