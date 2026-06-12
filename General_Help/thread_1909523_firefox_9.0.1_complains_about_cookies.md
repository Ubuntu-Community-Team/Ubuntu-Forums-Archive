---
title: "firefox 9.0.1 complains about cookies"
date: 2012-01-15
forum: General Help
---

### Post by kurja on 2012-01-15
I have Ubuntu Lucid and Firefox 9.0.1, and every time after I've cleared the Firefox's recent history (tools->clear recent history->Everything, clear now) and I try to log in to say, gmail or facebook, I get a page saying that I can't login because cookies are not enabled. When I try to login again, it'll work. Is anyone else experiencing this?

---

### Post by carl4926 on 2012-01-15
Try renaming .mozilla to .mozilla-old

Start FFox
Test as it is. Report back

---

### Post by kurja on 2012-01-15
where might I find this dot mozilla? ctrl+f search of the entire file system did not come up with anything called that.

---

### Post by carl4926 on 2012-01-15
Ctrl+H
Will view hidden files
It's in /home/youruername*

---

### Post by pqwoerituytrueiwoq on 2012-01-15
edit->preferences->privacy

---

### Post by kurja on 2012-01-15
thanks. tried that, but it behaves the same as before.

---

### Post by kurja on 2012-01-15
both boxes in privacy settings are ticked, accept cookies from sites and accept third-party cookies. no exceptions have been defined.

---

### Post by utnubuuser on 2012-01-15
the esiest way to locate a file is with the "locate" command.

ie:> sudo locate .mozillaor > sudo locate *.mozilla

---

### Post by kurja on 2012-01-15
tank you. I located the folder, renamed it, and restarted firefox, but the problem was not solved by doing so.

---

### Post by carl4926 on 2012-01-15
> **kurja said:**
> tank you. I located the folder, renamed it, and restarted firefox, but the problem was not solved by doing so.
Umm...

An if you try a different browser?
Eg; opera or seamonkey or chromium

---

### Post by kurja on 2012-01-15
I installed chromium just to try this, and the problem appears to be the same. If I go to options and clear all history data, passwords etc and then try to login into gmail or facebook, I get the cookie error message. Then I click back to the login screen, re-enter the password and I get in.

weird....

edit - right after install, I did not get the error message. only after clearing the history.

---

### Post by kurja on 2012-01-16
up - any ideas on what might cause this issue?

---

### Post by carl4926 on 2012-01-16
> **kurja said:**
> up - any ideas on what might cause this issue?

No idea
I never clear cookies so I can't test it

Perhaps a bug report to mozilla is the way to go

---

### Post by spacecheck on 2012-01-16
You wrote earlier, "No exceptions have been defined." Click on Exceptions then click on status, and see if you have inadvertently set the site on the "blocked" list, simply by clicking "deny" on the first cookie from that site, with a check also having been set for "apply to all cookies from this site" (FF retains previously used setting for the subsequent cookie, checked/unchecked). If it is on the list, either with or without "www." you could simply mark the site and click remove it.

Good luck!

---

### Post by Frogs Hair on 2012-01-16
In order to interact with some sites that have saved settings , cookies need to be enabled . If you remove cookies and history at browser close the settings are not remembered . When you go back to the site you will see a cookies need to be enabled message .

Look in cookie an history settings for the browser . In Firefox if "use custom settings for history " is selected exceptions for cookies and history can be added .

---

### Post by kurja on 2012-01-16
> **Frogs Hair said:**
> In order to interact with some sites that have saved settings , cookies need to be enabled . If you remove cookies and history at browser close the settings are not remembered . When you go back to the site you will see a cookies need to be enabled message .

Look in cookie an history settings for the browser . In Firefox if "use custom settings for history " is selected exceptions for cookies and history can be added .

Apparently, the exceptions list gets cleared when the cookies are cleared. hmmmm....

---

### Post by lovinglinux on 2012-01-20
Try [Biscuit](https://addons.mozilla.org/en-US/firefox/addon/biscuit-220876/). It is not a definitive solution, but it allows to protect specific cookies, so when you clear the history and delete the cookies, your Google and Facebook cookies can be preserved.

---

