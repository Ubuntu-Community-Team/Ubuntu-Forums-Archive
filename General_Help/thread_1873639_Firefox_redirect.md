---
title: "Firefox redirect"
date: 2011-11-01
forum: General Help
---

### Post by nethompson on 2011-11-01
I need some help. Firefox redirects me to searchdiscovered.com when I try to go to eppicard.com. I am able to get to the site from other computers on my network so it is a local machine issue. I could really use some help. This is driving me crazy. I have purged Firefox and reinstalled it and still the same thing. I have restarted DNS, cleared the cookies and history in Firefox.

---

### Post by Tamlynmac on 2011-11-01
I had a similar problem with a different site and installed this Firefox extension which eliminated the issue.

[Redirect Remover]("https://addons.mozilla.org/en-US/firefox/addon/redirect-remover/?src=search")

Good Luck & hope this helps.

---

### Post by sammiev on 2011-11-01
> **Tamlynmac said:**
> I had a similar problem with a different site and installed this Firefox extension which eliminated the issue.

[Redirect Remover]("https://addons.mozilla.org/en-US/firefox/addon/redirect-remover/?src=search")

Good Luck & hope this helps.

+1 added it a while back and had no troubles to date. :)

---

### Post by pqwoerituytrueiwoq on 2011-11-01
search for "searchdiscovered.com" in [about:config]("http://kb.mozillazine.org/About%3Cb%3E%3C/b%3E:config")
reset anything that comes up and check your addons

---

### Post by nethompson on 2011-11-02
I have tried both suggestions and still nothing. Redirect remover did not work and there was nothing about searchdiscovered in about:config. I even removed all of my addons.

---

### Post by SparTacux on 2011-11-03
Try creating a new desktop user account and run firefox from there and see what happens.

---

### Post by nethompson on 2011-11-03
Alright! I figured out the issue. It was my nsswitch.conf file. It seems that with "wins" placed in the "hosts:" location, it won't work correctly. I'm not sure why but I took out wins and now it works. Does anyone have any insight on why wins is preventing certain sites from loading?

---

