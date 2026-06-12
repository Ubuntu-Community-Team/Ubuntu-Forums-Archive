---
title: "How to specify hotkeys that start apps?"
date: 2006-06-18
forum: General Help
---

### Post by Nuld on 2006-06-18
I am looking for a program that allows me to specify hotkeys to start applications. The package "hotkeys" looks good. However, I don't know how to specify key combinations, e.g. <win key> + <b> to start firefox.

Using a single key already works great, e.g. <userdef keycode="115" command="firefox">Firefox</userdef>.

Thanks for your help!

---

### Post by Nuld on 2006-06-19
Come on guys and gals, I am surely not the only one who likes to use hotkeys to start apps. Share your wisdom :p

---

### Post by Johnsie on 2006-06-19
I use System->Preferences->keyboard shortcuts 

but that's quite limited ;-/

---

### Post by Nuld on 2006-06-19
Yes I know that tool, but as you said it's limited. I can't specify custom apps (or can I do this by editing a config file?). And it seems that I can't specify key combinations either, hence no <win key> + <b>. I can't believe that this is so hard, I always thought linux users love to use their keyboard above their mouse :lol:

---

### Post by rjr1049 on 2006-06-19
Go to Applications>System Tools>Configuration Editor.  Locate apps>metacity and there you will find global_keybindings and keybinding_commands.  Use these last two settings to configure keys as you wish.  For example, on my box, <CTR><SHIFT>t launches Mozilla Thunderbird.  You can configure ten keys (I think) in this way.  Hope this helps.

---

### Post by Nuld on 2006-06-19
Super, danke fuer den Tipp.
Man kann auf diese Weise auch mehr als 12 Hotkeys belegen, habe einfach mal versucht selber weitere hinzuzufuegen (run_command_13, ...) und es funktioniert wunderbar :)

---

