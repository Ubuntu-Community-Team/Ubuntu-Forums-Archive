---
title: "Adding Spanish Language Keyboard Layout disables Alt_R on USA layout"
date: 2010-05-29
forum: General Help
---

### Post by rmlrml on 2010-05-29
Running Ubuntu Lucid Lynx, GNOME 2.3

Keyboard Preferences utility

Adding any Spanish language keyboard layout makes my Alt_R not work in ANY layout!  I see that it changes Alt_R to "Iso_L..." for all/both layouts, including USA layout.  When I click "Reset to Defaults"  it's fine again, USA layout shows Alt_R again.  I've tried all the variants of the Latin American layout and the Spain layout and they all do the same thing.

What is "ISO_L..." and what's going on?

i DESPERATELY need my Alt_R to work!  That's how I navigate back and forward on the web!  Alt_R + LEFT or RIGHT

HeLp!1

---

### Post by simosx on 2010-05-30
> **rmlrml said:**
> Running Ubuntu Lucid Lynx, GNOME 2.3

Keyboard Preferences utility

Adding any Spanish language keyboard layout makes my Alt_R not work in ANY layout!  I see that it changes Alt_R to "Iso_L..." for all/both layouts, including USA layout.  When I click "Reset to Defaults"  it's fine again, USA layout shows Alt_R again.  I've tried all the variants of the Latin American layout and the Spain layout and they all do the same thing.

What is "ISO_L..." and what's going on?

i DESPERATELY need my Alt_R to work!  That's how I navigate back and forward on the web!  Alt_R + LEFT or RIGHT

HeLp!1

Alt_R is the default key to choose what is called the 'Third level' (ISO_L...) characters. The Spanish layout has characters such as áé which are produced when you press Alt_R + (some alphabetic character).

How do you solve the problem? You can change the assignment for the key that is used as 'Third level' key. Go to the Keyboard preferences, in Layout, and select Layout options. Then, under "Keys to choose 3rd level", change to another key.

Normally you would use Alt_L with the cursor keys. Why don't you use in your case?

---

### Post by rmlrml on 2010-05-30
> **simosx said:**
> Normally you would use Alt_L with the cursor keys. Why don't you use in your case?

Hmm, well I don't know about "normally".  I've always used Alt_R.  Just seems natural to me, I can back/forward using just my right hand (laptop).

Anyway, it worked!  There was an option "Right Alt key never chooses 3rd level".  Thanks for your help!

---

