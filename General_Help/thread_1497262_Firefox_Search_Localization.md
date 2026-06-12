---
title: "Firefox Search Localization"
date: 2010-05-30
forum: General Help
---

### Post by Kevbert on 2010-05-30
I'm using Mozilla Firefox version 3.6.3 (the one that comes with Ubuntu 10.04). If I use the Search box (top right-hand pull-down box) for either Google or Amazon I get the US version of these, but I'm in the UK so would like to use the UK versions of these by default. In previous Firefox/Ubuntu versions I didn't get this problem. Is this a bug ?
I set up 10.04 for UK settings and Language settings are set for English UK (see attached) but I always get Amazon.com (US) and Google.com (US) instead of Amazon.co.uk and Google.co.uk. I have the English Language pack installed (via System-Admin-Language support).

---

### Post by lovinglinux on 2010-05-30
Google is driving me crazy with this, because even if I type [http://www.google.com](http://www.google.com) it redirects me to the local version. This happens in Firefox, Chrome and Opera, so is not a browser issue.

Additionally, Google is redirecting other Google services. For instance, when I access my Google account, it is displayed in Portuguese sometimes, even after setting the account options to use English.

I suspect Google is using ip geolocation. Nevertheless, it's weird since you are located in UK.

Anyway, see if [this](http://kb.mozillazine.org/General.useragent.locale) helps.

Also check the preference **keyword.URL** in **about[noparse]:[/noparse]config**

---

### Post by ajgreeny on 2010-05-30
In your Firefox address bar type **about:config** and in the page that appears if you search for google in the filter, you may find an entry like:-
```
browser.search.defaultenginename    default  string   www.google.co.uk
```but the word **default** in my system says **user set** as I have changed the default to [www.google.co.uk]("http://www.google.co.uk").

Try that edit in your system as well and you may get the search engine you prefer.

---

### Post by lovinglinux on 2010-05-30
> **ajgreeny said:**
> In your Firefox address bar type **about:config** and in the page that appears if you search for google in the filter, you may find an entry like:-
```
browser.search.defaultenginename    default  string   www.google.co.uk
```but the word **default** in my system says **user set** as I have changed the default to [www.google.co.uk]("http://www.google.co.uk").

Try that edit in your system as well and you may get the search engine you prefer.

The preference **browser.search.defaultenginename** controls which search engine is displayed by default in the search bar when you start Firefox and the value is a name corresponding to one of the engines available in the searchbar list, not an URL. Besides, this only works if **browser.search.selectedEngine** is the default value, which means once you select a new engine from the list, Firefox will always  start using that engine, even if the default engine is a different one. Please notice this doesn't affect the default engine of the address bar.

If you want to change what search engine Firefox uses when you type something in the address bar, then you have to modify the preference **keyword.URL**. Nevertheless, Google redirects the query on the server. This redirecting "feature" seems to be inconsistent, since sometimes I get google.com, sometimes I get google.com.br.

If you want to modify the Google search engine on the searchbar, install [Add to Search Bar](https://addons.mozilla.org/en-US/firefox/addon/3682/), then visit [http://www.google.co.uk](http://www.google.co.uk), right-click on the google search field and select "Add to Search Bar". You might want to delete the old one first.

---

### Post by ajgreeny on 2010-05-30
> **lovinglinux said:**
> The preference **browser.search.defaultenginename** controls which search engine is displayed by default in the search bar when you start Firefox and the value is a name corresponding to one of the engines available in the searchbar list, not an URL. Besides, this only works if **browser.search.selectedEngine** is the default value, which means once you select a new engine from the list, Firefox will always  start using that engine, even if the default engine is a different one. Please notice this doesn't affect the default engine of the address bar.

If you want to change what search engine Firefox uses when you type something in the address bar, then you have to modify the preference **keyword.URL**. Nevertheless, Google redirects the query on the server. This redirecting "feature" seems to be inconsistent, since sometimes I get google.com, sometimes I get google.com.br.

If you want to modify the Google search engine on the searchbar, install [Add to Search Bar]("https://addons.mozilla.org/en-US/firefox/addon/3682/"), then visit [http://www.google.co.uk](http://www.google.co.uk), right-click on the google search field and select "Add to Search Bar". You might want to delete the old one first.
Thanks for that info LL, I didn't know, as is obvious from my answer.  I never actually use that search box and have always used the googlebar lite add-on, much better in my opinion, and a lot more configurable according to your needs and wishes.

---

### Post by Kevbert on 2010-05-31
I've checked **general.useragent.locale** and that is set to **en-GB** (by default) and also changed **distribution.searchplugins.defaultLocale** to **en-GB**. I've changed the default search engine to google.co.uk, but with Google (UK) as soon as I click on shopping everything is shown for the US. All other searches are still for US sites.
Thanks for the help so far, but this is a little annoying as it wasn't a problem in earlier versions of Firefox.

---

### Post by Bill_ on 2010-06-28
I've noticed this too here in Australia using Ubuntu 10.04.
Google searches using the search box default to google.com, however on numerous windows computers with Firefox, they all default to google Australia (just like Ubuntu did in previous versions).

---

