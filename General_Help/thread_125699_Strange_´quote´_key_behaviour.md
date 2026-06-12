---
title: "Strange ´quote´ key behaviour"
date: 2006-02-04
forum: General Help
---

### Post by vtail on 2006-02-04
Hello guys,

I´ve noticed a very strange behaviour of the quote key (the one left to the colon key on most keyboards):

1. If I press it once, nothing happens
2. If I press it twice, the single quote (´) appears
3. If I press shift+quote twice, the following symbol appears: ¨ But it´s not the usual double-quote - e.g. bash or python produce a error when this symbol is entered.
4. Finally, if I press quote following some character, I receive it´s accented version, e.g. qoute + a produces á.

I think it´s something related to i18n - but I don´t need (I only need to enter Russian character, and I have a special group for it) and it makes impossible any programming (e.g. I still don´t know how can I enter double qoutes).

Could anybody please show me how can I turn off this behaviour?

Many thanks,
Victor.

---

### Post by Zalbor on 2006-02-04
That sounds like what happens on greek keyboards when you press the ; : key. Are you sure your keyboard layout is the one you should use?

Go to System>Preferences>Keyboard, "Layouts" tab, and make sure the one there (or one of them, if you need more than one) is the one that corresponds to your keyboard. Otherwise click "Add", find the one you should use and remove the old one.

---

### Post by vtail on 2006-02-05
The strange thing is that this behaviour is observed in US International keyboard layout. Any more ideas?

---

### Post by Zalbor on 2006-02-10
I just noticed that if I press the relevant key when in a greek layout, then switch to american and press a letter, it produces the accented version. This must have something to do with your problem...
I had this idea: Even though you're in the US, are you sure that your keyboard is a US one? It might have different keymapping so it produces a different input to the computer... Of course I might be way off, just an idea.

---

### Post by vtail on 2006-02-11
No, I don't think it's a hardware problem... I'm observing it with Toshiba notebook bought in US, and all keys worked just fine under Windows...

---

### Post by timbl on 2006-06-28
I was searching for forums for a solution to the same problem and am updating for completeness.

If you select a keyboard layout with dead keys you will get this behaviour. This is what the dead keys are. Here is the link that I found:

[http://www.ellipsix.net/geninfo/charaset/index.php]("http://www.ellipsix.net/geninfo/charaset/index.php")

This is not Linux specific, but does talk about dead keys. I am sure there are better resources out there.

---

### Post by Phrawm48 on 2008-06-10
I had exactly the same problem in Ubuntu 8.04 (Hardy) and resolved it as follows.

1. Choose "System > Preferences > Keyboard", then click the Layouts tab.

2. Click Add to add a new layout.
   - In the Layouts list, choose USA.  The Keyboard utility automatically chooses Default for the Variant attribute.  Leave this value selected.

3. Click Add to save your changes.

4. In the Layout area, click Default next to the new layout.

A single press of the quotation mark key (") or tilde key (~) will now type the character.

Cheers & hope this helps,
Ric
SFO

---

