---
title: "Web Browser-User Profile I don't get it. Help!"
date: 2009-07-26
forum: General Help
---

### Post by AmericanPrincess109 on 2009-07-26
When ever I try to start up Web Browser it says that to choose a user profile. 
I created a user profile and picked a folder to save it in and I figured that everything was okay.

But...when I open Web Browser it says
[I]Could not initialize the application's security component. The most likely cause is problems with files in your application's profile directory. Please check that this directory has no read/write restrictions and your hard disk is not full or close to full. It is recommended that you exit the application and fix the problem...

[/I]I have no idea what that means. I've been trying all day to free up some space on my hard drive, but that has been unsuccessful. I don't know what to do! Please help me!!:confused:

---

### Post by mike555 on 2009-07-26
a little more info would help, but your profile is in your home folder , it is hidden so check "show hidden files" in the view , if your talking about Firefox it would be in " .Mozilla ".......

---

### Post by wanye on 2009-10-06
i fixed it just now by deleting the certificate stuff in my firefox profile folder:

**cd ~/.mozilla/firefox**

find your profile folder:

[email]wmanye@babydweezil:~/.mozill[/email]a/firefox$ ls
ml6hc1vu.default  profiles.ini

go into the profile folder and view files:

[email]wanye@babydweezil:~/.mozill[/email]a/ffbackup$ **cd ml6hc1vu.default/**
[email]wanye@babydweezil:~/.mozilla/ffbackup/ml6hc1vu.defaul[/email]t$ **ls**
blocklist.xml         extensions.cache          search.sqlite
bookmarkbackups       extensions.ini            secmod.db
bookmarks.html        extensions.rdf            sessionmanager.dat
Cache                 formhistory.sqlite        sessions
**cert8.db  **            Google Gears for Firefox  sessionstore.bak
**cert_override.txt**     key3.db                   sessionstore.js
chrome                localstore.rdf            signons3.txt
compatibility.ini     mimeTypes.rdf             urlclassifier3.sqlite
compreg.dat           OfflineCache              urlclassifierkey3.txt
content-prefs.sqlite  permissions.sqlite        webappsstore.sqlite
cookies.sqlite        places.sqlite             XPC.mfasl
downloads.sqlite      pluginreg.dat             xpti.dat
extensions            prefs.js                  XUL.mfasl

delete the certificate files:

[email]wanye@babydweezil:~/.mozilla/ffbackup/ml6hc1vu.defaul[/email]t$ **rm cert8.db**
[email]wanye@babydweezil:~/.mozilla/ffbackup/ml6hc1vu.defaul[/email]t$ **rm cert_override.txt**

restart firefox. job done!

HTH

---

