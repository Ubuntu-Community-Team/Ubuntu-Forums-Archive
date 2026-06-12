---
title: "Date format"
date: 2009-09-10
forum: General Help
---

### Post by Zeemvel on 2009-09-10
Hi,

I'm using Ubuntu 9.04 with Gnome and would like to use yyyy/mm/dd or mm/dd/yyyy as date format. Unlike every other OS I've used (all Windows versions starting from 3.11, Archlinux with KDE), I didn't find any setting to change regional settings like date format, currency, etc...

But the American date format currently displaying in Thunderbird is very annoying for me and Thunderbird appearantly uses the default system setting (Which I can't find???).

Where is this setting?

Thanks.

---

### Post by dcstar on 2009-09-10
> **Zeemvel said:**
> Hi,

I'm using Ubuntu 9.04 with Gnome and would like to use yyyy/mm/dd or mm/dd/yyyy as date format. Unlike every other OS I've used (all Windows versions starting from 3.11, Archlinux with KDE), I didn't find any setting to change regional settings like date format, currency, etc...

But the American date format currently displaying in Thunderbird is very annoying for me and Thunderbird appearantly uses the default system setting (Which I can't find???).

Where is this setting?

Thanks.

Formats are determined by the System Locale that was set when you installed Ubuntu and selected a timezone.

---

### Post by Zeemvel on 2009-09-10
How can it be changed after installation?

Also, can date format be changed independently from language? I prefer English as language for a computer (not my local language), the US point instead of our comma (,) for decimal numbers, but our local conventions for the rest (currency, date format, ...).

Is that possible?

---

### Post by longtom on 2009-09-10
> **dcstar said:**
> Formats are determined by the System Locale that was set when you installed Ubuntu and selected a timezone.

Aha...any way one can change this?

---

### Post by StuartN on 2009-09-10
Open a terminal and type "locale" to determine which locale is in use on your computer. For instance mine is en_IE. Then edit the locale definition file, "sudo gedit /usr/share/i18n/locales/en_IE", to change the date_fmt. This would affect all applications, and I have no idea if there is a simpler approach.

Alternatively you can set the date and time formats in applications like Nautilus, or change the locale in OpenOffice (which will also affect all applications using the system locale).

---

### Post by XCan on 2009-09-10
Hmm, this I guess should really be something they should fix. Everytime I install Ubuntu on a new computer I always have to dig into some random setting file to get this right, oh and the fact that the first weekday is Sunday... ;)

---

### Post by jasreca on 2010-04-26
It's simply beyond me how a desktop environment that made it so far can lack such a simple setting.

What's more, the web is full of frustrated people trying to find a way to change regional settings and I guess no one on the development team seems to care.

KDE is light years ahead of gnome in that respect....

---

### Post by epolin on 2010-08-26
Same exasperation here: how is it that we have such useless features as graphical themes and no usability themes?

It is all the more crazy that, as for me, I just don't want ANY regional settings: what I want is pure ISO, YYYY-MM-DD HH:mm:ss.xxx (along with metric system, A4, etc.). Why on earth are rational people so much impacted by local, medieval, obscurantist, impractical, incoherent, ambiguous practices???

Plus... the integration with ooffice does not work well: it falls back to the US format when editing with F2, etc.. Allright, this is another story.

Anyway, I hate Windows otherwise, but about this topic it is absolutely perfect (or used to be: I have not used any version since XP, and they tend to break things over time): date format is (was) easy to set independently from the language, and applies(d) to all applications.

---

### Post by jakslev on 2010-09-03
Completely agree! This is ridiculous! Mark - pull your finger out!

---

### Post by jrussell88 on 2010-12-14
That's soooo true - and why does it keep reverting to wrong settings on upgrade? Why can't it keep all those settings?

---

