---
title: "Removing languages from Firefox spellcheck menu"
date: 2010-07-08
forum: General Help
---

### Post by Struwelpeter on 2010-07-08
Is there a way to remove languages from the "languages" item of the Mozilla Firefox "Right Click" menu? I must have some 50 languages options listed there, making it difficult to browse among the ones I really need.

Thanks!

S.p.

---

### Post by lovinglinux on 2010-07-09
I think the entries on that list depends on the dictionaries you have installed in Ubuntu. So check if you don't have unnecessary dictionaries installed.

---

### Post by Struwelpeter on 2010-07-10
Thanks for the reply, but I tried that! I already uninstalled unnecessary dictionaries.
The problem with the Firefox menu is not only that it's showing some dictionaries that I do not have: it is also showing two or three entries for the same languages...

---

### Post by lovinglinux on 2010-07-10
> **Struwelpeter said:**
> Thanks for the reply, but I tried that! I already uninstalled unnecessary dictionaries.
The problem with the Firefox menu is not only that it's showing some dictionaries that I do not have: it is also showing two or three entries for the same languages...

Sorry, I forgot to look into the preferences. This is something I never had to change :)

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=162998&stc=1&d=1278779257[/IMG]

---

### Post by Struwelpeter on 2010-07-11
Thanks for your reply. But what I am experiencing is actually a different issue. I have only five languages installed in the menu displayed by your screenshot: English, Portuguese, French, Spanish, German. But when I right-click on any piece of text, to select the spellchecking dictionary, what I get can be seen in my attachment.

I want to get rid of the extra languages, as they make it hard to find and select the useful ones. Apparently, this is a common issue but I have failed to find solutions for it.

Cheers,

S.p.

---

### Post by lovinglinux on 2010-07-16
> **Struwelpeter said:**
> Thanks for your reply. But what I am experiencing is actually a different issue. I have only five languages installed in the menu displayed by your screenshot: English, Portuguese, French, Spanish, German. But when I right-click on any piece of text, to select the spellchecking dictionary, what I get can be seen in my attachment.

I want to get rid of the extra languages, as they make it hard to find and select the useful ones. Apparently, this is a common issue but I have failed to find solutions for it.

Cheers,

S.p.

Go to "Tools >> Add-ons >> Languages" in Firefox menu and check if you only have those 5 languages there or more.

---

### Post by Struwelpeter on 2010-07-17
> **lovinglinux said:**
> Go to "Tools >> Add-ons >> Languages" in Firefox menu and check if you only have those 5 languages there or more.

Only the five languages I mentioned are listed there.

---

### Post by egalvan on 2010-07-17
Might the list come from the "locale" languages that Linux can use on start-up?

i used a "locale purge" applet when I installed Hardy, and only have English variants...

---

### Post by Struwelpeter on 2010-07-17
What exactly does "locale purge" do?

---

### Post by egalvan on 2010-07-17
> **Struwelpeter said:**
> What exactly does "locale purge" do?

It TOTALLY removes un-wanted/un-needed languages.

You pick what you want/need to keep,
it does the rest.

it worked perfectly for me. 
Left me with English/Spanish/Italian, just what I wanted.

---

### Post by leonbravo on 2011-06-18
Just to make it clearer.... yes, there is an application called localepurge. It'd make the work of cleaning up locale files that you don't need, provided that you select the ones you want to keep.

You can install it from synaptic or sudo apt-get install localepurge. Immediately the installation is done, you will be asked to configure and thereafter, it will be ready to be run.

:guitar:

---

