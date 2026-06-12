---
title: "Problems with Function keys need help :S"
date: 2010-08-08
forum: General Help
---

### Post by Hybridgreen on 2010-08-08
Hey guys, i'm new here. Yesterday i  downloaded Ubuntu onto my Toshiba Satellite Pro L300 system. I have got  everything working besides the function keys. I'm no tech wiz so could  you explain to me the best way you can fix this problem. When i use the key combinations which would usually work in Windows Vista it doesn't do nothing.

                                                          Thanks in advance,
Blake.

---

### Post by webtechquery on 2010-08-08
what do u mean by Function Keys ?

---

### Post by Hybridgreen on 2010-08-08
F1,F2 etc etc. I hear some people call them short cut keys too.

---

### Post by Hybridgreen on 2010-08-08
BUMP! I need an answer to this badly guys.

---

### Post by DeMus on 2010-08-08
> **Hybridgreen said:**
> BUMP! I need an answer to this badly guys.

Open menu System - Preferences - Keyboard Shortcuts
In there choose what you want to do on the left and press the key you want to do it with,so it will appear on the right.
Close the program and use the keys.

---

### Post by Hybridgreen on 2010-08-08
It doesn't have a brightness option.

---

### Post by Hybridgreen on 2010-08-08
Okay, im using a laptop. When i use the key combinations on my laptop it doesn't work.

---

### Post by webtechquery on 2010-08-08
If you are using Toshiba Satellite laptop, then why dont you use the brightness thingy from the keyboard, by pressing and holding function (**fn key**) and then f6 for low and f7 for high.

---

### Post by Hybridgreen on 2010-08-08
Hey guys, i'm new here. Yesterday i  downloaded Ubuntu onto my Toshiba  Satellite Pro L300 system. I have got  everything working besides the  function keys. I'm no tech wiz so could  you explain to me the best way  you can fix this problem. When i use the key combinations which would  usually work in Windows Vista it doesn't do nothing.

                                                          Thanks in advance,
Blake.

---

### Post by Unknown-Demon on 2010-08-08
Posting the same thread again doesn't really help.

---

### Post by DeMus on 2010-08-08
I can understand your frustration but you see, here on the forum are all sorts of people: experts who use Linux (Ubuntu) for a long time already, and new comers like yourself.
Not everyone has the answer you are looking for. One more thing, on an international forum like this one (English spoken forum) people are not always on-line, sometimes they sleep, work, or whatever. There is the matter of time difference with the place on earth where you are.
So please be patient, the answer will come.

---

### Post by simosx on 2010-08-08
> **Hybridgreen said:**
> Hey guys, i'm new here. Yesterday i  downloaded Ubuntu onto my Toshiba Satellite Pro L300 system. I have got  everything working besides the function keys. I'm no tech wiz so could  you explain to me the best way you can fix this problem. When i use the key combinations which would usually work in Windows Vista it doesn't do nothing.

                                                          Thanks in advance,
Blake.

You say 'Function keys' but what you actually mean are the special Fn+Fx, where x=1 to 10, keys. These are not called function keys but **hotkeys**.

The reason why some of them do not work has to do with those keys not being reported properly. The 'udev' project keeps track of these keys, and how they should work for each laptop configuration.

The place where these keys are configured is 
/lib/udev/keymaps/ and you can see three Toshiba models already there.

Find documentation at [https://wiki.ubuntu.com/Hotkeys/](https://wiki.ubuntu.com/Hotkeys/)

I guess for your case you would need to add a single configuration line in /lib/udev/rules.d/95-keymap.rules and you will be OK.

Good luck! :popcorn:

---

### Post by Hybridgreen on 2010-08-14
Hey guys, i'm new here. Yesterday i downloaded Ubuntu onto my Toshiba Satellite Pro L300 system. I have got everything working besides the hotkeys. I'm no tech wiz so could you explain to me the best way you can fix this problem. When i use the key combinations which would usually work in Windows Vista it doesn't do nothing. I need a straight answer to this, i posted this 5 days ago and still haven't gotten an answer. I am getting quite frustrated and i will possibly be switching back to windows if this problem doesn't get fixed. And please explain this properly! :D

Thanks in advance,
Blake.

---

### Post by labinnsw on 2010-08-15
I was able to manage this problem by;
1. Installing keytouch and keytouch editor.
2. Use keytouch editor to map any unmapped keys
3. Use keytouch to select keyboard configuration
4. Use Gnome keyboard shortcuts to assign actions to keys or key combinations. (System >> Administration >> Preferences >> Keyboard shortcuts.)

Keytouch comes with a comprehensive manual.

---

### Post by Iowan on 2010-08-15
From Code of Conduct:
> Please do not cross post, or post the same thing in multiple locations.
I merged your three threads. Posting the same thing multiple times won't get you better responses, it just confuses (and annoys?) those trying to help you. :-k

---

