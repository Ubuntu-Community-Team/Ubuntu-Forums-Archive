---
title: "UK Keyboard"
date: 2012-06-10
forum: General Help
---

### Post by payneardo on 2012-06-10
I have just installed 12.04 and it is set to the US keyboard I have gone through every setting I can find and it is all set to UK, yet the keyboard doesn't change

I am a newbie with ubuntu but I went to settings,language support, the regional formats tab, selected English(United Kingdom) in the drop down box and then Click on Apply system-wide, it then asked my password and said it needed a reboot but after a reboot the keyboard is still set to US even though it says UK ??

Hope somebody can help

Cheers

payneardo

---

### Post by CatKiller on 2012-06-10
It's the keyboard layout that you need to change rather than the language. I don't know if they've changed the name for Precise, but in previous versions the tool was simply called Keyboard.

---

### Post by HarryTorry on 2012-06-10
If you hit the Dash Home (Alt + F1, then enter); Then type keyboard layout and choose that option, you'll be able to change the layout in that setting. If not, putting this into console should do the trick.
```
setxkbmap -layout gb
```

---

### Post by payneardo on 2012-06-10
> **HarryTorry said:**
> If you hit the Dash Home (Alt + F1, then enter); Then type keyboard layout and choose that option, you'll be able to change the layout in that setting. If not, putting this into console should do the trick.
```
setxkbmap -layout gb
```

Cheers that did the trick no matter what else I did worked :(  But thanks very much HarryTorry :KS

---

