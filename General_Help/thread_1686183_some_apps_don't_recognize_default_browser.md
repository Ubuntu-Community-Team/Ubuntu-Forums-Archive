---
title: "some apps don't recognize default browser"
date: 2011-02-11
forum: General Help
---

### Post by rjv23 on 2011-02-11
Hi; problem= some apps will not load requested page links using the default browser (some will).  ubuntu 10.1, default browser is firefox 3.6.16 (ff for ubuntu 1.0).  I have set ff browser to default in preferred app applet, through the terminal in root and in the preferences in ff.  Thunderbird will open links using ff.  Skype and docky gmail docklet will not.  I had chrome installed (ff was set to default) and these apps tried to use chrome browser but could not load the requested page.  I removed chrome from the system.  Now I get an error from Docky gmail saying failed to load chrome, no file exists.  clicking on an active link in skype will not launch any app now.  Tks for your help.

---

### Post by luigi_mb on 2011-02-12
Some applications have Firefox or other browsers hard-coded in.

/luigi

---

### Post by sprinklemeelmo on 2011-03-05
I have the same complaint and I don't think luigi's answer is the answer.  Clicking a link in Evolution launches Firefox (the browser I have set in preferred applications) while clicking on an HTML file with the file browser launches Chrome (the wrong browser).

---

### Post by vlad2005 on 2011-04-29
I have same problem with gmail docklet in docky. First, when install open inbox with firefox browser even chrome it's set as default browser. After remove and reinstall  no longer works either with firefox or with chrome.
I have these problem with ubuntu 11.04. With previous version don't have any kind of trouble.

---

### Post by Oskenso on 2011-04-30
I didn't have this problem in 10.10 but now I do when I upgraded to 11.04. It seems to come from the fact that Google Chrome can't be selected in "Web Browser" under  System->Preferences->Preferred Applications.

---

### Post by VCoolio on 2011-04-30
Using the config for preferred apps points "gnome-open" to the apps you prefer. There is however also the more universal "xdg-open" which I think non-gnome apps like skype would use. You can configure xdg-open using the commandline with "alternatives", but there is also a graphical interface you can install called "galternatives" which is a lot easier. For the browser you'd need to set x-www-browser to firefox. Hope that solves something.

---

### Post by vlad2005 on 2011-04-30
I found a more simply solution for my specific problem.
Go System->Preferences->Preferred Applications and set Google Chrome as default for Web Browser. now work ok.
I don't understand why need to do that if i set google chrome as my default browser. Maybe, settings are different.
Anyway, for other applications maybe help what suggest @VCoolio

---

