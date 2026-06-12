---
title: "langs with accents"
date: 2012-02-15
forum: General Help
---

### Post by oldnik on 2012-02-15
Hello everyone!
I'm using Xubuntu on my desktop & i want to be able to print French letters with accents without using character map, which is too slow for me. I know that "compose key" provides what i'm looking for, but i cannot use it in the way they describe. I simply cannot define it! Also there have been a bug in xfce4 with dropping settings in xfce's language switcher after opening from hybernation/sleep. That is why i use "sudo setxkbmap -layout [...] -options grp:[...]" code for this. I hope, that this bug will be fixed soon. Whatever, how do i need to define compose key and how to use it? I've found the "XKBOPTIONS:ralt" but changing it doesn't make difference.

---

### Post by Ms. Daisy on 2012-02-16
In regards to using ComposeKey, see:

[https://help.ubuntu.com/community/ComposeKey](https://help.ubuntu.com/community/ComposeKey)

---

### Post by oldnik on 2012-02-16
> **Ms. Daisy said:**
> In regards to using ComposeKey, see:

[https://help.ubuntu.com/community/ComposeKey](https://help.ubuntu.com/community/ComposeKey)


As i have mentioned earlier, i had already tried to change the line in */etc/default/console-setup*
"xkboptions: ralt" to other key
BUT it didn't give me any appropriate result. That is why i'm writing here.

---

### Post by LewisTM on 2012-02-16
1) In the Xfce Settings Manager/Keyboard, set your keyboard layout to use system defaults, whatever they are.
2) Add the Keyboards Layouts plugin to your panel. It's in the xfce4-goodies package.
3) Setup your keyboard layouts, compose key, etc. inside the plugin's properties.

Cheers!

Edit: sorry I didn't see you had trouble with the language switcher. Does it forget the config? I think the settings in #1 might help.

---

### Post by oldnik on 2012-02-16
Done that. But still do not understand how to print at least a letter...
For example, 
> depress and release the **Multi_Key** (Shift+[AltGr]("https://help.ubuntu.com/community/AltGr") is default see [ComposeKey]("https://help.ubuntu.com/community/ComposeKey") for options) and then the first, second (and sometimes third) key, from the table belowSo, i push my Shift+Compose_key, release, then ~ and a. And viola! No result.

Later: yep, there is still one bug, but that is not critical, i use 
> sudo setxkbmap -layout us,de -option grp:lwin_toggle
so, it works.

---

### Post by LewisTM on 2012-02-16
Why [FONT="Courier New"]sudo[/FONT]?
Your command should be
```
setxkbmap -layout us,de -option grp:lwin_toggle,compose:ralt
```
to use AltGr as a compose key. 
For instance AltGr,e,' will give you é

---

### Post by oldnik on 2012-02-16
Voilà! :)   Merci!
>  [...] ,compose:ralt
works great! And is much faster than using GUI-based utility!
I can éè, but what about Ê in lower-case? Can't find... I'll try to figure it out.
Thank you !

---

### Post by LewisTM on 2012-02-16
> **oldnik said:**
> Voilà! :)   Merci!

works great! And is much faster than using GUI-based utility!
I can éè, but what about Ê in lower-case? Can't find... I'll try to figure it out.
Thank you !
Compose,e,^(shift-6).

Please mark as SOLVED :)

---

### Post by oldnik on 2012-02-16
Unfortunately, there is no button for "solved partly"  )
i understand that there must be simple explanation, but é è &#553; and Compose+e+shift-6 gives me the ê... damn me... it gives me ê.
ok. solved.
:-D 
Thanks!

One note: ê doesn't work in skype. é è and &#279; ok.

---

