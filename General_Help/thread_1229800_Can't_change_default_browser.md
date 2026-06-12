---
title: "Can't change default browser"
date: 2009-08-02
forum: General Help
---

### Post by dvbellamy on 2009-08-02
I'm running 9.04 on a Dell Inspiron 1525 and I'm trying to change the default browser from Firefox to Opera. I initially changed the browser in System-> Preferences-> Preferred Applications to Opera and this setting appears to have "stuck". But launchers to internet addresses still open in Firefox. So I searched here and found the terminal equivalent, which shows an asterisk next to "Opera", although I entered the relevant number anyway. Still no joy, launchers still open in Firefox.
So I removed Firefox using Synaptic Package Manager... and now the launchers on my desktop open in OpenOffice Writer. Grrrr.....

How do I change my default browser?
Thanks
Dave

PS... this was a factory installed Dell Ubuntu machine (7.10) and I've done 3 flawless OS upgrades using the Update Manager.

---

### Post by ZaXdude on 2009-08-04
Same here...
I use opera on ubuntu 9.04 but i cant get it to work as default browser, it is setup on the "System-> Preferences-> Preferred Applications" menu, but everytime a click on a link Firefox opens...  Please help!!!     btw...   I started to use Opera because I upgraded firefox to 3.5 and it crashes everytime after a few seconds...  and its slow.  Opera its working faster, but i cant get it to be as default browser.:(

---

### Post by CatKiller on 2009-08-04
> **dvbellamy said:**
> But launchers to internet addresses still open in Firefox.

What do you mean by "launchers to internet addresses?" Launchers run programs, so if you've got a launcher (on the Desktop, panel or menu) then it will be running a program, which could well be Firefox with a specified URL. You would have to amend a launcher to get it to run a different program.

---

### Post by ZaXdude on 2009-08-04
> **CatKiller said:**
> What do you mean by "launchers to internet addresses?" Launchers run programs, so if you've got a launcher (on the Desktop, panel or menu) then it will be running a program, which could well be Firefox with a specified URL. You would have to amend a launcher to get it to run a different program.

I'm pretty sure he means LINKS with that, it's the same thing that's happening to me.

Please Help!

---

### Post by dvbellamy on 2009-08-04
Well I probably do mean links, although when I created them, I right-clicked on the desktop and chose "Create Launcher". In the "Create Launcher" dialogue box, I changed "Type" from "Application" to "Location", specified the location and hit OK. Nowhere was Firefox specified.
Anyway, it seems bot ZaXdude and I have the same problem. Anyone else?

---

### Post by wojox on 2009-08-04
Does opera show up in the applications menu?

---

### Post by ZaXdude on 2009-08-04
> **wojox said:**
> Does opera show up in the applications menu?

Yes Opera is there, and it's setup as preffered aplicacion for internet browsing but it just wont work. Everything keeps openning in Firefox still.

---

### Post by wojox on 2009-08-04
Ok right click the panel and select +Add to panel
Select Application Launcher
Press Forward
Find it in there and add it
Try to launch new icon and see what it does

---

### Post by CatKiller on 2009-08-04
> **ZaXdude said:**
> Everything keeps openning in Firefox still.

Define "everything." Where are these links that you're clicking on that open Firefox? Thunderbird and gnome-terminal certainly adhere to the Preferred Applications setting, so what is it that you're using?

---

### Post by dvbellamy on 2009-08-04
I think I figured it out...
The link/launcher I created tells me it is a html document if I right click it and select properties. So I created a new, blank html document on my desktop, did properties on that, and on the "Open with" tab I chose Opera.
That appears to have done the trick... if I now click the links/launchers on my desktop, Opera opens them up just fine.

Does that help you at all ZaXdude?

---

### Post by ZaXdude on 2009-08-04
> **CatKiller said:**
> Define "everything." Where are these links that you're clicking on that open Firefox? Thunderbird and gnome-terminal certainly adhere to the Preferred Applications setting, so what is it that you're using?

Links in apps most of all, like clicking on the mail button on Emesene or links on Thwirl (twitter client).  Firefox pops up.

---

### Post by CatKiller on 2009-08-04
> **ZaXdude said:**
> Links in apps most of all, like clicking on the mail button on Emesene or links on Thwirl (twitter client).

I haven't used either of those apps, but perhaps they have their own configuration rather than using the system settings. It's worth having a poke around in their Preferences until someone that has used those applications can comment.

---

### Post by CatKiller on 2009-08-04
> **dvbellamy said:**
> I think I figured it out...

Ah, so it was a document you were opening. Glad you got it figured out.

---

### Post by dvbellamy on 2009-08-04
> **CatKiller said:**
> Ah, so it was a document you were opening. Glad you got it figured out.

Well technically yes I suppose it was, although the Location I specified in the Create Launcher dialogue box was a web address... i.e. "http://www.google.com", which I guess is just a link to an index.html document at the end of the day.

Thanks for your help.

---

