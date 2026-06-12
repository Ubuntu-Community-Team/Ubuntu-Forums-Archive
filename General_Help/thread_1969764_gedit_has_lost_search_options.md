---
title: "gedit has lost search options"
date: 2012-04-30
forum: General Help
---

### Post by Paddy Landau on 2012-04-30
Fresh installation of 12.04 (fully updated).

The previous version of gedit (I had 11.04) had various search options, including specifying case-sensitivity and whole-word-only searching.

The new version does not.

This makes it impossible to search for certain strings that occur within words, or where case is important, in large text documents.

How can I resurrect those settings?

---

### Post by uylug on 2012-04-30
If you're careful enough, you should be able to get the same functionalty by using the "Replace" dialog, and carefully clicking on "Find".

It's not that it's lost it, it's just that the 99% of users don't need such functionality, and since a dialog isn't necesary most of the time, the functionality can only be achieved by following the steps I've described above.

---

### Post by pqwoerituytrueiwoq on 2012-04-30
you could use pluma (mate-text-editor)
[FONT=monospace]
[/FONT]```
sudo add-apt-repository "deb http://packages.mate-desktop.org/repo/ubuntu precise main";sudo apt-get update;sudo apt-get install mate-archive-keyring;sudo apt-get update
```then you can install it
```
sudo apt-get install mate-text-editor
```there is a chance it may want to pull the entire mate DE with it (not sure if you want the mate de (gnome2 fork) installed or not)

there are other text editors like mousepad and leafpad

---

### Post by Paddy Landau on 2012-04-30
> **uylug said:**
> If you're careful enough, you should be able to get the same functionalty by using the "Replace" dialog, and carefully clicking on "Find".
Thank you, that will do it. :)

> **pqwoerituytrueiwoq said:**
> there are other text editors like mousepad and leafpad
Thanks -- I've used those, but gedit works best for me.

I'm marking this as solved.

---

### Post by bmeakings on 2012-05-17
I don't know if this is too late a reply, but the advanced search settings are available, you need to right-click in the search field to get them.

---

### Post by Paddy Landau on 2012-05-17
> **bmeakings said:**
> I don't know if this is too late a reply, but the advanced search settings are available, you need to right-click in the search field to get them.
Not too late! Whoever could have guessed that! There should be a button.

Thank you for letting us know.

---

### Post by bmeakings on 2012-05-17
Glad to have helped :) It took me a while to figure it out myself. I still miss the old Find dialogue box and the ability to use the scroll wheel to move between tabs.

The GNOME devs move in mysterious ways ;)

---

### Post by MestreLion on 2012-05-17
> **bmeakings said:**
> I don't know if this is too late a reply, but the advanced search settings are available, you need to right-click in the search field to get them.

OMG, you're my HERO!!!

I'm using Precise for a few hours, and was very concerned about the new find in gedit.

My 2 cents now:

- You can browse all matches using UP and DOWN arrows. No need to use CTRL+G

---

### Post by Paddy Landau on 2012-05-17
> **MestreLion said:**
> You can browse all matches using UP and DOWN arrows. No need to use CTRL+G
On the other hand, Ctrl-G doesn't work unless you first press Enter.

---

