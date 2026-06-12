---
title: "Default country change possible?"
date: 2009-10-14
forum: General Help
---

### Post by leeds_shrew on 2009-10-14
Hi all,

New Ubuntu user here.  When I installed Jaunty, I selected my country as Jordan (it is, after all, where I live) but this has had an unforseen side-effect in that any software/website etc which automatically detects my country detects me as being in Jordan and therefore gives me Jordanian-centric search results (Google using Mozilla's search bar) when I'd rather UK-centric results, and more troublingly gives me defaults in Arabic (which I don't understand at all!)

It's generally pretty easily overcome, but still a trouble I don't think I need to have.  Is it possible to change my country to the UK without a reinstall?

Whilst I'm here, is it possible to use google**.co.uk** as the search engine in Mozilla's search bar? Embarrasingly I can easily do this in IE7... haha

---

### Post by mr.ivan on 2009-10-14
hwe you considered chcnging it throught Change country settings util? it is somewhere in System>Preferences>something... /region settings or country settings maybe/

---

### Post by leeds_shrew on 2009-10-14
Thanks Mr Ivan.  I had a good look through all of my menus/installed programs (via add/remove programs) but I couldn't find anything obvious - certainly nothing by the names country or region settings or anything similar. Is it maybe something I have to install?

---

### Post by Kevbert on 2009-10-14
You may be able to do it with this firefox add-on: [[COLOR="Red"]Quick Locale Switcher[/COLOR]]("https://addons.mozilla.org/en-US/firefox/addon/1333"). If not, I'm sure there's an add-on somewhere which will work for you.  You can browse all add-ons and plug-ins via the Firefox Tools menu.

---

### Post by leeds_shrew on 2009-10-14
Thanks Kevbert.  I think that's a pretty useful add-on despite it not quite doing what I want it to do (ie. search google.co.uk rather than google.com).  It has to be said that this is not a huge issue. (A bigger issue is just the fact that this is really easy to set on IE7/8 even though I am generally not a fan at all. An anti-fan. Is that possible? :))

Any ideas for Ubuntu as a whole?

---

### Post by Kevbert on 2009-10-15
If you want to change everything in Ubuntu, you could try going to System - Administration - Language Support. You may find that there is nothing installed (this is what I found even though I'm in the UK and set UK preferences when installing the OS!) Once you've set all things up you'll need to log out and then log back in for the settings to take effect.

---

### Post by P4man on 2009-10-15
I think google derives it from your IP address. it seems to insist I live in the Netherlands even though i don't. Make a google account if you dont have one yet, and set your default language and search options there. It still doesn't quite work for me though, like google news will give my Dutch news no matter what i try, until I change the country by hand.

---

### Post by Kevbert on 2009-10-15
> **P4man said:**
> I think google derives it from your IP address. it seems to insist I live in the Netherlands even though i don't. Make a google account if you dont have one yet, and set your default language and search options there. It still doesn't quite work for me though, like google news will give my Dutch news no matter what i try, until I change the country by hand.

If that's so, then you may be able to hide your public IP address. See [this]("http://compnetworking.about.com/od/workingwithipaddresses/f/hideipaddress.htm") article.
Feeling a bit rough (flu), so may try that later to see if I can get US prices for techy stuff...

Google.com can be used via anonymouse, proxify just gives me google.co.uk every time. I've found that a search in shopping gives a lower price with google.com when compared with the same product for google.co.uk.

---

### Post by leeds_shrew on 2009-10-18
The language support thing didn't do what I want - although all the other suggestions have made it a lot harder to find out if I'm having an effect or not.  Particularly the google options makes everything with blogger/picasa etc a lot better.  It defaults everything to English (although not the UK) at least so I'm not navigating through Arabic all the time!

Ubuntu 9.10 coming up soon: When I upgrade, do I go through all the installation procedure again or does it happen pretty much automatically?

---

### Post by Kevbert on 2009-10-18
> **leeds_shrew said:**
> The language support thing didn't do what I want - although all the other suggestions have made it a lot harder to find out if I'm having an effect or not.  Particularly the google options makes everything with blogger/picasa etc a lot better.  It defaults everything to English (although not the UK) at least so I'm not navigating through Arabic all the time!

Ubuntu 9.10 coming up soon: When I upgrade, do I go through all the installation procedure again or does it happen pretty much automatically?

The easiest ways to update are via System - Admin - Update Manager or via terminal with
```
sudo apt-get dist-update
```
You shouldn't need to re-install from scratch from 9.04 to 9.10.

---

### Post by leeds_shrew on 2010-01-23
Just in case anyone is having similar issues.  I never found a way to change the default search provider in Firefox from google.com to google.co.uk.

My solution was to install Google Chrome and use that as my browser (which I thoroughly recommend anyway).  Chrome keeps a track of all of the search websites you have used then lets you set any of them as your default search when you search through the multibar (or whatever it's called).  All you'd have to do is visit google.co.uk and do a manual search there, then it should appear on the list of providers you can use as your default search.  Just the sort of simplicity I was hoping for from Firefox!

---

### Post by John Bean on 2010-01-23
> **leeds_shrew said:**
> Just in case anyone is having similar issues.  I never found a way to change the default search provider in Firefox from google.com to google.co.uk.


It's rather easy; the search engines are defined in xml format in a folder called "searchplugins" in your Firefox profile. Editing google.xml is as trivial as changing instances of "google,oom" to "google.co.uk".

Similarly Amazon, eBay, ... ;-)

---

### Post by amarendra on 2011-05-26
> **John Bean said:**
> It's rather easy; the search engines are defined in xml format in a folder called "searchplugins" in your Firefox profile. Editing google.xml is as trivial as changing instances of "google,oom" to "google.co.uk".

Similarly Amazon, eBay, ... ;-)
Isn't it lame to go dig into deep folders hunting XMLs each time I installed/updated Firefox or Ubuntu, whereas all other browsers know exactly which country I live in without having to tell them exclusively? And other browsers were not even packaged with Ubuntu!

---

