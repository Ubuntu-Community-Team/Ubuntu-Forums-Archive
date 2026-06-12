---
title: "How do I configure the keyboard layout in Jaunty? Do I need to write an fdi file?"
date: 2009-07-31
forum: General Help
---

### Post by luisito on 2009-07-31
I recently updated XUbuntu in my parent's laptop from Hardy to Jaunty.

My mom says she can't write without accents, so I need to set the keyboard layout to intl instead of us. I used to do that in the file xorg.conf, but now it is all commented out and I believe that hal takes care of that automatically. I am guessing I have to add some fdi file in /etc/hal/fdi/policy, but I don't know what file or what to write in it.

Right now I set the keyboard as intl in her user account using the XFCE settings. But as it is well known, this makes the startup of xfce quite a bit slower (a good 30 second delay). That's why I want to set up the keyboard system wide.

---

### Post by oldfred on 2009-07-31
It is in 
system/preferences/keyboard  - the second tab is layout where you can add alternate countries.

Sorry this is gnome I missed the Xubuntu.

---

### Post by michy99 on 2009-07-31
You can type accented letters using the Compose key:

[https://help.ubuntu.com/community/ComposeKey](https://help.ubuntu.com/community/ComposeKey)

---

### Post by luisito on 2009-08-02
Thanks for the answers. I don't think the compose key is what I wanted. But in the same website with instructions on how to set that up I was pointed out to the file /etc/default/console-setup
In that file I could set my keyboard layout to us(intl) by using the following options:
XKBMODEL="pc105"
XKBLAYOUT="us"
XKBVARIANT="intl"
XKBOPTIONS=""

Now all the accents work as I wanted system wide.

---

