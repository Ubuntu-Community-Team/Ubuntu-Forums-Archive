---
title: "Delete key (map to rm -rf)"
date: 2009-08-21
forum: General Help
---

### Post by Elep.Repu on 2009-08-21
I noticed when I press the delete key (I enabled the delete option in the context menu) it moves the files into a .Trash000 folder in the working directory, even if you had recently deleted the .trash directory.

Is there a way to map the **Delete** key to an actual rm -rf (or something similar).

I've already looked in *Keyboard Shortcuts *under Preferences, and under *Metacity* in Configuration Editor.
I also tried adding <delete> to a custom command, tied to rm -rf, but it didn't work. (Still went to trash.)

---

### Post by tgeer43 on 2009-08-22
Assigning a single key (rather than a key combination) to the rm command sounds like an amazingly bad idea, especially with the -r and -f options.

But you didn't ask if it was a good idea, did you?

Well, I'll give you a semi-answer. Yes, it can be done and a bit of googling will tell you how.

I can just see it now: "I accidentally deleted my entire filesystem..."

tgeer

---

### Post by Elep.Repu on 2009-08-22
> **tgeer43 said:**
> Assigning a single key (rather than a key combination) to the rm command sounds like an amazingly bad idea, especially with the -r and -f options.

But you didn't ask if it was a good idea, did you?

Well, I'll give you a semi-answer. Yes, it can be done and a bit of googling will tell you how.

I can just see it now: "I accidentally deleted my entire filesystem..."

tgeer

Well, within nautilus. yes..

And I said (or similar.) So I'd probably append the -i option if I found out how. Thanks anyway..

> **Johnny B said:**
> if you want to be a jerk, why not tell him to go fsck himself?

I actually laughed at what he said. Although I'm sure he's being condescending. Oh well. I'm happy in my conviction.

Not like I'm hovering over: / with my Delete option..

---

### Post by tgeer43 on 2009-08-22
I'm not being a jerk or condescending, just stating a fact. rm -rf is one of the most potentially dangerous commands you can use and assigning it to an uber-common keystroke like Delete *IS* a bad idea.

You don't see folks lining up to answer the question, do you?

At least I stated that it's possible and gave a clue as to how to find the answer. I just didn't want to feel in any way responsible if something does go awry.

I spend hours and hours per day on this and other forums trying to help people. Read some of my other posts and then come back and tell me if you still think I'm a jerk.

Sheesh...

tgeer

---

### Post by hansdown on 2009-08-22
Sorry to but in, but I think tgeer43 speaks good sense.

tgeer43 did give some help if you choose this path.

---

### Post by kaibob on 2009-08-22
> **Elep.Repu said:**
> I noticed when I press the delete key (I enabled the delete option in the context menu) it moves the files into a .Trash000 folder in the working directory, even if you had recently deleted the .trash directory.

Is there a way to map the **Delete** key to an actual rm -rf (or something similar).

I've already looked in *Keyboard Shortcuts *under Preferences, and under *Metacity* in Configuration Editor.
I also tried adding <delete> to a custom command, tied to rm -rf, but it didn't work. (Still went to trash.)

I don't know of a way to remap the delete key. An alternative is to use shift-delete, which bypasses the trash. Personally, I use the right-click delete option to bypass the trash, but you already know about that.

---

### Post by DeMus on 2009-08-22
How dumb can you be? Here on the forum people warn others to be careful of using that keystrokes, and you want to map it under one key?
There is an easier way to get rid of Ubuntu, just format the disk.
Don't come crying here when you "accidentally" deleted an important file.

---

### Post by Elep.Repu on 2009-08-22
> **kaibob said:**
> I don't know of a way to remap the delete key. An alternative is to use shift-delete, which bypasses the trash. Personally, I use the right-click delete option to bypass the trash, but you already know about that.

Oh, I didn't realize Shift Delete bypassed. That'll do. Thanks.

---

### Post by cariboo on 2009-08-22
You can also enable the delete function in nautilus by going to Places-->Home Foder-->Edit-->Preferences-->Behaviour-->Trash, and enable delete and turn of notification.

---

