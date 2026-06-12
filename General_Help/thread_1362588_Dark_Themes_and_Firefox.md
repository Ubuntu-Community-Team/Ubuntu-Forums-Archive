---
title: "Dark Themes and Firefox"
date: 2009-12-23
forum: General Help
---

### Post by Tamale on 2009-12-23
I am tired of this problem. Using ubuntu's default settings, not installing anything else, I switch to a nice dark theme from the appearance menu and this is what google.com looks like in firefox, regardless of the firefox theme I'm using at the time. **Note that I've typed a lot of stuff into the google input bar already, but it's completely invisible because it's black text:**

[IMG]http://img690.imageshack.us/img690/1812/darkthemes1.png[/IMG]

I've tried so many things to fix this it isn't funny.. including:

editing the userContent / userChrome files in firefox.
hand-editing the GTK themes
using the stylish extension to firefox - this kinda worked for one firefox version - 3.5.5 - then immediately broke after the upgrade to 3.5.6 and now  doesn't work again and I can't get it to work again.

The simple problem here is that there doesn't appear to be a way to tell GTK to stop changing things in my browser. Why isn't this an esaily-selectable switch in the appearance menu?  I could understand a few people wanting some consistency between their desktop look and their webpage look, but ultimately, webpages are written by someone else, and shouldn't be subjected to your own design whims.

this whole integration of looks and themes between the stuff on my own computer vs. the webpages on the entire internet doesn't make any sense to me.

Please, someone fix this critical bug. I've all but switched to google chrome on ubuntu simply because it does the right thing - it doesn't care what I do to my gtk theme.. webpages look right.

---

### Post by synapsys on 2009-12-23
Have you tried changing colors in gnome color chooser?

---

### Post by orlox on 2009-12-23
This must be configured in firefox

edit->preferences->content

Choose Colors... in the Font & Colors section.

Uncheck "Use system colors" and check "Allow pages to choose...(etc...)"

---

### Post by Tamale on 2009-12-23
> **orlox said:**
> This must be configured in firefox

edit->preferences->content

Choose Colors... in the Font & Colors section.

Uncheck "Use system colors" and check "Allow pages to choose...(etc...)"

"use system colors" is unchecked, and "allow pages to choose" is checked by default.  this does nothing to resolve the problem.

---

### Post by Tamale on 2009-12-23
> **synapsys said:**
> Have you tried changing colors in gnome color chooser?

yes. this can potentially fix problems in web pages, but then renders the UI unusable in actual gnome elements.

the proper solution is to figure out how to tell GTK to stop affecting firefox completely... I want to know how to do this and I'd like to know why this isn't an easily-selectable option in appearance.

---

### Post by Tamale on 2010-01-03
bump!

please someone help me get a proper feature request added into the appearance menu that stops GTK themes from changing webpage elements. This can't be that hard to do.

---

### Post by warfacegod on 2010-01-03
This seems more like a problem with the firefox theme you are using. I've had several dark f.f. themes do the same thing to me in fresh installs of ubuntu before I ever changed my system themes

---

### Post by ean5533 on 2010-01-03
> **warfacegod said:**
> This seems more like a problem with the firefox theme you are using. I've had several dark f.f. themes do the same thing to me in fresh installs of ubuntu before I ever changed my system themes

Agreed. I'm using the "New Wave" theme, a very dark grayscale theme, and Firefox's rendering is unaffected. "Dust" also looks fine.

---

