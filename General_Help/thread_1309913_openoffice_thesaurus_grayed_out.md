---
title: "openoffice thesaurus grayed out"
date: 2009-11-01
forum: General Help
---

### Post by triplesick on 2009-11-01
hi--

downloaded the karmic RC, downloaded updates.

In openoffice, the thesaurus is grayed out.  I checked the language, and I'm using USA English.  Anyone else?  Any ideas?

---

### Post by Hagar Delest on 2009-11-01
Do you see the blue checkmark in front of the language? See [[Troubleshooting] Spell check in OOo 3.x](http://user.services.openoffice.org/en/forum/viewtopic.php?f=74&t=16512).

---

### Post by triplesick on 2009-11-01
i do see it :(.  thank you for the suggestion.

---

### Post by Hagar Delest on 2009-11-02
Do you see the thesaurus module checked in Tools>Options>Language Settings>Writing Aids?

In first post of the tutorial, go to the detailed tutorial and in section 4, try to reinstall the default dictionary extension.

---

### Post by triplesick on 2009-11-04
aha!  no thesaurus module appears!  thank you!  I will attempt to resolve it tomorrow; tonight-->sleep.

---

### Post by triplesick on 2009-11-04
no luck!! :(

--i downloaded a dictionary from the extensions website
--i tried to reinstall the stock dictionaries, but there are literally zero files in my share/extension/install folder
--i completely uninstalled and reinstalled openoffice

no luck.  guess i'll just have to come up with my own words :).  or use windows, ugh.

---

### Post by JohnPta on 2009-11-04
> **triplesick said:**
> no luck!! :(

--i downloaded a dictionary from the extensions website
--i tried to reinstall the stock dictionaries, but there are literally zero files in my share/extension/install folder
--i completely uninstalled and reinstalled openoffice

no luck.  guess i'll just have to come up with my own words :).  or use windows, ugh.

I have exactly the same problem did you solve your thesaurus problem?

---

### Post by Hagar Delest on 2009-11-05
Have you tried to install for the user only, i.e. in the user profile instead of in /share/...? NB: to install in /share, you need to run OOo as root.

---

### Post by triplesick on 2009-11-08
PROBLEM SOLVED!  Here's what I did.  It's a stupid, hacky solution.
1. Installed openoffice 3.1.1 in Windows XP on a different partition.
2. Mounted that partition in linux
3. Via OOo's extension manager, navigated through that partition to the share/extensions/install whatever folder, and added the dictionary/thesaurus.

---

### Post by scouser73 on 2009-11-08
Click **Tools, Options, Languages, Writing Aids** Click **Edit** then click the **Language drop-down menu**, from there de-select all the languages you don't need.

[IMG][[IMG]http://img89.imageshack.us/img89/3523/thesaurusvd8.th.png[/IMG]](http://img89.imageshack.us/my.php?image=thesaurusvd8.png)[/IMG]

---

### Post by triplesick on 2009-11-08
thank you.  i solved the problem, see previous post.  for some reason i think the dictionaries weren't packaged with it at all.  maybe a glitch in one of the 9.10 pre-release builds i downloaded?  who knows.

---

### Post by amano on 2009-11-22
A note for users from Austria:

Only the "German (Germany)" language features a thesaurus. If you set the spelling check to "German (Austria)" the thesaurus checkbox will be greyed out.

Thus it would be a good idea to have "German (Germany)" checked by default.

I am on Karmic, BTW...

---

### Post by thol4u on 2011-02-25
> **triplesick said:**
> PROBLEM SOLVED!  Here's what I did.  It's a stupid, hacky solution.
1. Installed openoffice 3.1.1 in Windows XP on a different partition.
2. Mounted that partition in linux
3. Via OOo's extension manager, navigated through that partition to the share/extensions/install whatever folder, and added the dictionary/thesaurus.

Thank you very much triplesick, I had the same issue in Open Office 3.2 on Ubuntu 10.04 and got it resolved by your steps.

---

### Post by transposia on 2011-07-07
I encountered this same problem. I used synaptic to install the right language pack, but the thesaurus still didn't come up.

Then I marked OOo for reinstallation, and now my thesaurus works. :KS

---

