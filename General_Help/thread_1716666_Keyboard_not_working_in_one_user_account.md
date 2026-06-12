---
title: "Keyboard not working in one user account"
date: 2011-03-28
forum: General Help
---

### Post by Gene_J on 2011-03-28
One of my friends that I installed Ubuntu 10.04 for, is having a keyboard problem. On his account (admin) the PS2 keyboard works fine. On his wifes account (desktop user) the keyboard does not work. She can apparently use the keyboard until login is finished. A search here shows other people having keyboard problems, but no solutions. Should I try a USB mouse? Delete her account and add her back in a new one? Is there a fix someone here knows about? Thanks for the assistance.

---

### Post by blueridgedog on 2011-03-28
If you place her in the admin group, is the issue resolved?

---

### Post by Gene_J on 2011-03-29
Thanks for the reply, blueridgedog. When I go to their house in a day or so, I will try that, although it won't solve the problem. Since the children use the mother's account, they have it as a desktop user account for parental control reasons. I will also try a USB mouse and reinstalling the account. This appears to be an ongoing bug and I was hoping for a permanent fix. I shall try to get more info on the computer see if it is a hardware/chipset problem.

---

### Post by blueridgedog on 2011-03-29
I am mostly looking for definitive proof that it is permissions related, if it is, then we can guess as to solutions.

---

### Post by Gene_J on 2011-03-29
> **blueridgedog said:**
> I am mostly looking for definitive proof that it is permissions related, if it is, then we can guess as to solutions.

I called the folks with your request. It will be a day or so before I hear back whether changing permissions solves the issue. Thanks for your help blueridgedog.

---

### Post by Gene_J on 2011-03-31
Well, they tried setting the wife's account as administrator and rolling back to an earlier kernel to no avail. I am guessing the kids hit the keystrokes to disable the keyboard. I shall reinstall Ubuntu 10.04 and send it out again. Thanks for reading this thread and helping.

---

### Post by Krytarik on 2011-03-31
Hey, not so fast! ;-) It may be, that the "Keyboard -> Accessibility" option "Slow Keys" is enabled, check it.
You can run those command to make sure that it isn't:
```
gconftool-2 /desktop/gnome/accessibility/keyboard/slowkeys_enable --type bool --set false
```Greetings.

---

### Post by Gene_J on 2011-04-01
> **Krytarik said:**
> Hey, not so fast! ;-) It may be, that the "Keyboard -> Accessibility" option "Slow Keys" is enabled, check it.
You can run those command to make sure that it isn't:
```
gconftool-2 /desktop/gnome/accessibility/keyboard/slowkeys_enable --type bool --set false
```Greetings.

Thanks for the tip. I ran into this once before. My memory is not getting any better as I age. I shall check that out tomorrow when I gain access to that computer.

---

### Post by Gene_J on 2011-04-01
Now that I have the computer in my hands, I can see that, yes indeed "Slow Keys" was enabled. The customer was saying the keyboard was non-functional, but it was working, just weirdly. With all the threads here that talk about the "Slow Keys" problem, I should have figured it out earlier. Thanks for all the help.

Problem solved!

---

### Post by Krytarik on 2011-04-01
> **Gene_J said:**
> With all the threads here that talk about the "Slow Keys" problem, I should have figured it out earlier.
No problem, I just recently didn't mind those too, when I was helping another member with multiple GDM issues. ;-)

---

### Post by washakie on 2011-07-17
Thanks for this post! Sheesh... what an odd thing to happen, I had the same problem! Solved. ;)

---

