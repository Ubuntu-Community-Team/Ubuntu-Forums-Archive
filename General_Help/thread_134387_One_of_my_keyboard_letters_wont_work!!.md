---
title: "One of my keyboard letters wont work!!"
date: 2006-02-21
forum: General Help
---

### Post by Amleto on 2006-02-21
for some reason, the letter:
after 'o' in the **alhabet**
missing from the above bolded word

wont work/dislay!!! :(

I think it haened when I was making some keyboard shortcuts.  First time I tried using 'letter' it was fine, but the second... it now says 0x21 instead of 'letter'


This is quite worrying, and very frustrating!!

ubuntu 5.1
2.6.12-10-amd64-generic

amd64 3800 x2

lease hel me fix it!!


Thanks

---

### Post by mustang on 2006-02-21
I'm not sure you can designate specific letters through Keyboard shortcuts so I doubt that's causing it.

Anyways, did you try

System->Preferences->Keyboard->Layouts tab  

Click on "resets to default"

---

### Post by Amleto on 2006-02-21
Thanks for the swift help.

My problem DOES seem to be dependent on that keyboard shortcut.  When I remove the shortcut alt+p, everything is ok.  Put it back, and problems start again.   Strange.

---

### Post by joehill on 2006-02-25
Ah, just the solution I was looking for.  Thanks for the tip.

For the record, the problem is apparently caused by a bug in the Keyboard Shortcuts dialogue.  I tried to assign something to the combination fn+g and the "fn" [notebook hotkey] wasn't recognized, so it tried to reassign the simple letter "g," and the letter "g" then showed up as something like 0xf6.  I replicated the problem with the letter v.  Reassigning a new shortcut doesn't solve the problem--only resetting the defaults does.

---

### Post by joehill on 2006-02-25
Ok, I just tried reassigning my keys to control rhythmbox again, this time not using the "fn" key, but I had the same problem again using standard keys like Alt and Ctrl.  It seems to happen any time I try to reassign the keys that are supposed to control rhythmbox (skip to previous track, next track, Play (play/pause).  Very strange.  I guess I won't try controlling rhythmbox with the keyboard.  Or better yet, I'll just use Amarok.

---

### Post by Amleto on 2006-02-25
I have configured the rhytmbox wth shortcuts, but they all use ctrl+alt+? ie three keys. maybe that will help?

---

