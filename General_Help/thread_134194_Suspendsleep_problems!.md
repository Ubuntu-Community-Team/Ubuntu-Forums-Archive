---
title: "Suspend/sleep problems!"
date: 2006-02-21
forum: General Help
---

### Post by tappad on 2006-02-21
Hi.
I was trying out some specialkeys on my keyboard.
All of a sudden my computer just shuts off. This is when i press the "My Documents" special key. I'm guessing sleep or suspend mode, but not sure.. It took a couple of seconds until it shuted down, but the screen went black immedeatly. When i started the computer i think it started to the same position that it was before, music started playing as it was..
However, the screen was black, and nothing happened... So i rebooted, pressing the reboot button on the front of the computer.

Now, im experiencing some problems. Firefox wont start my profile becouse it's "in use".. 

Thanks for any help.

---

### Post by AgenT on 2006-02-21
[quote=tappad]Hi.
I was trying out some specialkeys on my keyboard.
All of a sudden my computer just shuts off. This is when i press the "My Documents" special key. I'm guessing sleep or suspend mode, but not sure.. It took a couple of seconds until it shuted down, but the screen went black immedeatly. When i started the computer i think it started to the same position that it was before, music started playing as it was..
However, the screen was black, and nothing happened...[/quote] You will have to find this out yourself. The information you give does not specify which it was. Both will save your session. Sleep saves it to memory, hence it will always use a little power while suspend saves to hard disk and uses no power. Suspend usually has more problems than sleep, but this all depends on your computer. Suspend also takes a lot more time, but it is all relative to your computer. But if you say a few seconds then it sounds more like suspend.

> Now, im experiencing some problems. Firefox wont start my profile becouse it's "in use"..  Remove the lock file in your firefox profile. It is called "lock" and is empty. The file that you want to remove is this:
```
~/.mozilla/firefox/*/lock
```

---

### Post by tappad on 2006-02-21
[QUOTE=AgenT]You will have to find this out yourself. The information you give does not specify which it was. Both will save your session. Sleep saves it to memory, hence it will always use a little power while suspend saves to hard disk and uses no power. Suspend usually has more problems than sleep, but this all depends on your computer. Suspend also takes a lot more time, but it is all relative to your computer. But if you say a few seconds then it sounds more like suspend.

 Remove the lock file in your firefox profile. It is called "lock" and is empty. The file that you want to remove is this:
```
~/.mozilla/firefox/*/lock
```[/QUOTE]

I'm pretty sure that its suspend-mode. Sorry i didnt know what was what.. (Never really use any of them..)
So.. to suspend the computer isnt really safe?
It seemed to restore everything except graphics (black screen).
I's there an easy way to change this special-key?
It does not appear under System->Preferences->Keyboard shortcuts.

Thanks for the reply.

---

