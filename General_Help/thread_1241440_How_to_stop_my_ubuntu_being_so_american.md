---
title: "How to stop my ubuntu being so american?"
date: 2009-08-16
forum: General Help
---

### Post by TygerTung on 2009-08-16
On my previous installation of ubuntu and my current one, I have had a problem.

For some reason ubuntu thinks I am in America, well I think it does because every time I try to print something it tries to print it out in 'letter' size paper, which, I understand is the size of paper which they use in America. Since I live in New Zealand, I have A4 paper, which is the commonly used standard size of paper here, I guess it is a metric size.

It's quite annoying because every time I wanna print something, the printer always comes up with an error, and I have to tell it to print on ISO A4 instead.

Is there any way of getting ubuntu to think I am in New Zealand, and using A4 paper?

Any help would be great,

Cheers,

Sam

---

### Post by Bucky Ball on 2009-08-16
Find 'Language Support' in System->Preferences (or administration) and change to English(UK) or (Aus).

Find 'Printing' in System->Preferences (or administration) and set your printer to A4 as a default paper size.

---

### Post by dcstar on 2009-08-16
> **TygerTung said:**
> 
.......
Is there any way of getting ubuntu to think I am in New Zealand, and using A4 paper?


Selecting the correct timezone on the install screen sets the correct locale.

If you locale is wrong after install then you have to manually change things.

---

### Post by Bucky Ball on 2009-08-16
> **dcstar said:**
> Selecting the correct timezone on the install screen sets the correct locale.

Oh, yea ... and do that! ;-) (thanks for cleaning up after my absent mind, dstar!)

---

### Post by TygerTung on 2009-08-16
Yep, that was all correct, but it still does it, I think the main problem is when I'm trying to print something off firefox.

---

### Post by Bucky Ball on 2009-08-16
Ah, okay. In Firefox, File->Page Setup.

Change it to A4. :)

---

### Post by TygerTung on 2009-08-16
AHA! That must be what is causing all the problems!

---

### Post by lisati on 2009-08-16
> **Bucky Ball said:**
> Find 'Language Support' in System->Preferences (or administration) and change to English(UK) or (Aus).

Find 'Printing' in System->Preferences (or administration) and set your printer to A4 as a default paper size.

There is a "New Zealand" locale under System->Preferences->Language support. That's what mine is set to (Ubuntu 9.04, 64-bit)

---

### Post by Bucky Ball on 2009-08-16
> **lisati said:**
> For your printer a minor variation is for you open up System->Administration->Printing, choose the printer you want to use, click on printer->properties, and then click on printer options to set the page size.

Mentioned that in my first post.

Oh, cool, there is a NZ entry. Thought there might be. :)

---

### Post by lisati on 2009-08-16
> **Bucky Ball said:**
> Mentioned that in my first post.

Oh, cool, there is a NZ entry. Thought there might be. Cool. :)

well spotted - I noticed after I'd posted. I'll go and edit now.

---

