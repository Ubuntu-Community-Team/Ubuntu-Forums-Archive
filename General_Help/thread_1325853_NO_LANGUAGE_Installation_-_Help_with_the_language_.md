---
title: "NO LANGUAGE Installation - Help with the language packs (Definitions)"
date: 2009-11-13
forum: General Help
---

### Post by nomnex on 2009-11-13
I am an *European*.

I need English language but ISO formats and international measures (e.g. printing default A4 vs. Letter/cm vs. inches, etc.)

During first install: Language Eng. > the OS used US measurement.

I have re-installed and selected NO language > I have got international measures and print output by default. OS is in English by default, so that's fine, however:

System>Administration>Language support : does not open (Since NO language are installed I presume). I need to use Synaptic Package Manager to install the needed language packs.

Please help with the definitions (What does what? What is stand alone and what is complementary) - so many:

[B]1. Language pack
2. Language support
3. Language support writing
4. Language support translation
5. Language pack GNOME[/B]
**6. Language pack - - base**

**My Need:**
English help for all the applications
English thesaurus and spell checking (OpenOffice.org, Evo, etc.)

French thesaurus and spell checking (OpenOffice.org, Evo, etc.)

Japanese thesaurus and spell checking (OpenOffice.org, Evo, etc.)

**I don't need:**
Menus and OS in another language (I assume this is Language Pack?)

---

### Post by Giblet5 on 2009-11-13
You DO know that Japan isn't in Europe. Right?  ;)

What you should probably do is install ALL of them, since it sounds like you want to run every application using a different language.

The default OS language is not English. It is C, which is pretty much US English, but not exactly the same. This dates back to Unix System III.

The gui interfaces you use are the teensy tip of the iceberg that underlies that gui.

The iceberg uses the language packs.

The iceberg's tip (gui) uses the other packages. I'm pretty sure that the language_support packages are glob wrappers that include all of the language packages for that language.

To run one application in English (or C) and another in French will require some menu editing, because you'll need to specify the desired language for that application.


Here is a [beginner's guide to linux internationalization]("http://eyegene.ophthy.med.umich.edu/unicode/") (aka i18n).

---

### Post by nomnex on 2009-11-13
Hi Giblet5

Is there a GUI option to select the language and the localization post installation?

Installing using English forces me to US measurements.

Installing using NO language (as I did) gives me International standard but prevents me from using System>Administration>Language Support (even after installing ALL the language packs from Synaptic. Language Support loads but does not open). Any idea how can I launch AND open Language support?

Both choices have a drawback. I am still sitting on the ice-berg scratching with an old spoon:)

Thanks for the clarification OS default use C vs. English.

---

### Post by nomnex on 2009-11-13
EDIT: Anyone with an English config, please copy and past your conf file.

/etc/default/local for me:

```
LANG="C"
```That could be the reason Language support does not open even after having installed all the language packs.

Is that all to change the default language from NO language to English (US)?

**EDIT*** BINGO

/etc/default/local

```
LANG="en_US.UTF-8"
```Solved the problem. I can now access Language Support.

You gotta love Linux...

---

