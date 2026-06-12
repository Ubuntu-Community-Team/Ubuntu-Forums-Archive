---
title: "using subversion to download files in bulk"
date: 2010-01-01
forum: General Help
---

### Post by HiImTye on 2010-01-01
Hi, I was wondering if there was an easy way to download files using SVN. I use a bazillion WoW mods and was hoping to find a script or something to automate updates to addons using the [WoWInterface SVN]("http://svn.wowinterface.com/"). I've never used Subversion before and quite frankly its a little foreign to me

any help would be greatly appreciated :D

---

### Post by dhillonv10 on 2010-01-01
I assume one thing you could do is tell svn to download the entire branch that you need, that can easily help you checkout the whole thing. Then you can use a cron script to automate the checkout with something like svn update. A simple google search on cron would really help you.

---

### Post by HiImTye on 2010-01-02
well, I was thinking more a script that would show me what to tell subversion so I could add it to cron

I don't mind adding each mod one by one (in fact, I expected it) but all the documentation I found on google is for uploading files to an svn site

---

### Post by HiImTye on 2010-01-08
bump

---

