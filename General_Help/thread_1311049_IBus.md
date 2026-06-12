---
title: "IBus"
date: 2009-11-02
forum: General Help
---

### Post by BloodIce on 2009-11-02
I have some problem with configuring IBus. How I could add Bulgarian Input Method or alternatively how I could use Bulgarian layout in Ubuntu. I will appreciate any help.

---

### Post by Giblet5 on 2009-11-02
You didn't tell us which version of Ubuntu you're using.

On 9.10, you can click System -> Preferences -> Keyboard. Click the "Layouts" tab. Click "Add...". Select "Bulgaria".

That should provide Bulgarian phonetic input.

Of course you'll also need the Bulgarian language pack and translations for any software you're using.

I haven't tried it because I'm a moron who only understands US English.

---

### Post by BloodIce on 2009-11-02
I am sorry that I forgot to say what kind of system I am using. It is Ubuntu 9.10 indeed. Unfortunately there is no Keyboard program at pointed location. There is Keyboard shortcuts but that is quite different. I am amazed that a different layout could be such a big problem.
P.S. There is nothing like Preferences->Mouse or Preferences->Keyboard on my desktop. I wonder if that was dropped from Ubuntu or my installation was weird.

---

### Post by goldencako on 2009-11-02
Are you sure you are not running Kubuntu?
On Ubuntu, as Giblet5 pointed out, there should be this:

System > Preferences > Keyboard

---

### Post by BloodIce on 2009-11-02
Come on guys ;). It is Ubuntu with the good old Gnome. I wonder what kind of package I could miss. It was pretty much standard installation, I didn't do anything to remove a package (especially if it is named keyboard).

---

### Post by goldencako on 2009-11-02
Ummm that's weird. Anyways, try starting it from shell:

```
gnome-keyboard-properties
```

---

### Post by BloodIce on 2009-11-02
Thank you for invaluable help goldencako. Finally that worked. I agree it is weird not to have it in GUI, but from the terminal it worked (if you know exactly what is the name of the binary). So I am turning down IBus and using standard layout switch through gnome-keyboard. I am quite happy to have my support, but the bug is still there - no keyboard or mouse on the screen.

---

### Post by goldencako on 2009-11-02
It is very odd indeed. Now I am wondering if by some weird reason the menu is actually there but it is not chosen? Try editing the menu top see if the choice is there, unchecked. Sometimes when you upgrade/fresh install, the things that appear on the menu are different... When I upgraded I had a Multimedia Systems Selector under Preferences. Upon fresh install it disappeared. However, on the Edit Menu, it's still there, tough unchecked.

---

### Post by BloodIce on 2009-11-02
Yes, it is there and yes it was unchecked. Very stupid of me, not to check that possibility. Both mouse and keyboard are there. When I checked them, both appeared in the Preference tab. I wonder now what is the difference between gnome-keyboard and IBus. Forgive my ignorance, but what is the advantage of IBus?

---

### Post by goldencako on 2009-11-02
Look at that, mystery solved!

As to the difference between IBus and the standard gnome layout program, I have absolutely no idea. In fact, before I updated to Karmic, I wasn't even aware of the existence of IBus. Maybe Giblet5 knows?

---

### Post by drtvasudevan on 2009-11-03
that is like scim- to use complex layout languages input

---

### Post by wildweathel on 2009-11-03
IBus connects applications to converters for languages that have more characters than easily fit on a keyboard.  For example, if I type [sinkansen]("http://en.wikipedia.org/wiki/Shinkansen") in Firefox, I can use IBus and Anthy to write the Japanese word &#26032;&#24185;&#32218; instead.  If I type a homophone, it will let me pick, e.g. kinou -> &#26152;&#26085; [yesterday] or &#27231;&#33021; [(software/hardware) feature].  Unless you need to type Japanese, Hindi, Chinese, Korean, or something like that, you don't need it.

Could you change the topic to "Missing keyboard preferences" or something like that?

Next thing to try is right-click the applications menu -> Edit Menus.  See if your keyboard preferences is there but hidden.  If not, you could try clicking "Revert" at the bottom of the box, but you'll lose all menu customizations you've made.

---

