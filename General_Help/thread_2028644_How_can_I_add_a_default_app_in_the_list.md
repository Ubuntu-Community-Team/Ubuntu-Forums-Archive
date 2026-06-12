---
title: "How can I add a default app in the list?"
date: 2012-07-18
forum: General Help
---

### Post by Colar on 2012-07-18
I'm searching for this answer since 12.04. A picture is worth a thousand words, so here are two:

[IMG]http://i.imgur.com/EdQyu.png[/IMG]

[IMG]http://i.imgur.com/YD8fK.png[/IMG]

Looks legit? Not at all. As browsers, I also have Chromium, Google Chrome, Opera, Arora, Galeon, elinks,... Don't appear in the list. Not to mention Thunderbird.

So : how can I tell to my Ubuntu that I got plenty of browsers and I want to see them in this list and change the default at will. How? :(

Please help.

Also: I'm not fluent in english so excuse my french :)

---

### Post by Colar on 2012-07-19
Bump.

---

### Post by Colar on 2012-07-20
Really? No one?

---

### Post by Colar on 2012-07-21
Halp please.

---

### Post by mc4man on 2012-07-21
Sorta surprising, at least as far as Chromium, Google Chrome, Opera which all should register as handling x-scheme-handler/http & x-scheme-handler/https which is what the 'default' is about.

What do these 2 commands show?
```
cat /usr/share/applications/mimeinfo.cache |grep x-scheme-handler/http
```
```
cat /usr/local/share/applications/mimeinfo.cache |grep x-scheme-handler/http
```

Ex. here where FF, G-C, Chromium & Opera are installed & all show in the 'Default' dropdown

> $ cat /usr/share/applications/mimeinfo.cache |grep x-scheme-handler/http
x-scheme-handler/http=firefox.desktop;chromium-browser.desktop;opera-browser.desktop;
x-scheme-handler/https=firefox.desktop;chromium-browser.desktop;opera-browser.desktop;

doug@doug-XPS-M1330:~$ cat /usr/local/share/applications/mimeinfo.cache |grep x-scheme-handler/http
x-scheme-handler/http=google-chrome.desktop;
x-scheme-handler/https=google-chrome.desktop;

---

### Post by Colar on 2012-07-22
Wow thank you for taking some time to help me :)

Here are the results:

> colar@fgsfds:~$ cat /usr/share/applications/mimeinfo.cache |grep x-scheme-handler/http
x-scheme-handler/http=epiphany-newtab.desktop;chromium-browser.desktop;firefox.desktop;midori.desktop;
x-scheme-handler/https=epiphany-newtab.desktop;chromium-browser.desktop;firefox.desktop;midori.desktop;

> colar@fgsfds:~$ cat /usr/local/share/applications/mimeinfo.cache |grep x-scheme-handler/http
x-scheme-handler/http=google-chrome.desktop;
x-scheme-handler/https=google-chrome.desktop;

I don't know if that matters, but I changed ~/.local/share/applications/mimeapps.list to replace every occurence of firefox with google-chrome. I googled a lot before posting here and it was a suggested solution. But didn't work.

---

