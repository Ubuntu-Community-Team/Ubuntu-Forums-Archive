---
title: "Getting Thunderbird to open links with Chromium"
date: 2011-01-19
forum: General Help
---

### Post by WebDrake on 2011-01-19
Hello all,

I'm having trouble getting Thunderbird to open links using Chromium (chromium-browser).

The default browser is now set to chromium-browser in KDE system settings.  I've also tweaked the Thunderbird config network.protocol-handler.app.http and https settings to use chromium-browser or /usr/bin/chromium-browser.

Despite this, Thunderbird keeps opening links in Firefox.  I'm bewildered as to why.

One thought is possibly an old GNOME system setting (there are .gconf and .gnome2 directories in my home directory, though I no longer use GNOME or have it installed on my system).  But I don't know and I would have thought the Thunderbird config would have overridden that in any case.

Can anyone advise?

Thanks in advance,

    -- Joe

---

### Post by lithopsian on 2011-01-19
Is your default browser Chrome?  Is there a mime type for http pointing to Firefox?

---

### Post by SlugSlug on 2011-01-19
system > preferences > preferred applications

---

### Post by WebDrake on 2011-01-19
> **lithopsian said:**
> Is your default browser Chrome?  Is there a mime type for http pointing to Firefox?

Chromium is set as default browser in KDE system settings (System Settings > Default Applications > Web Browser).

Don't know about mime type.  Can you advise?

---

### Post by WebDrake on 2011-01-19
> **SlugSlug said:**
> system > preferences > preferred applications

chromium-browser is already set as default browser in KDE System Settings.

---

### Post by SlugSlug on 2011-01-19
edit: sorry didn't read KDE

---

### Post by reobedr on 2011-01-19
in thunderbird-> edit -> preferences -> Attachments
content type: http -> action: use chromium browser
content type: https -> action: use chromium browser

at least: thats what I had to change.

---

### Post by WebDrake on 2011-01-19
> **reobedr said:**
> in thunderbird-> edit -> preferences -> Attachments
content type: http -> action: use chromium browser
content type: https -> action: use chromium browser

at least: thats what I had to change.

Great, works now!  Thank you very much. :KS

---

### Post by Qazzian on 2011-02-10
After following the above advice I still had the problem.

This post [http://forums.mozillazine.org/viewtopic.php?p=9025325&sid=f336078a83f9dfb9462a1656f37a9520#p9025325](http://forums.mozillazine.org/viewtopic.php?p=9025325&sid=f336078a83f9dfb9462a1656f37a9520#p9025325) 

suggested setting [FONT="Lucida Console"][COLOR="Sienna"]network.protocol-handler.warn-external.http=true[/COLOR][/FONT] in about:config. 
I found that it was already set to false so a simple double click sorted it out.

You could also do the same for 
[FONT="Lucida Console"][COLOR="Sienna"]Network.protocol-handler.warn-external.https
Network.protocol-handler.warn-external.ftp[/COLOR][/FONT]

---

### Post by JivanAmara on 2012-03-17
You can also go to Edit->Preferences->Attachments and delete the http content types.  Thunderbird will then use the desktop's default browser.  

I haven't tried this with KDE, but it works for Gnome.

---

### Post by pillarsdotnet on 2012-07-25
After setting the various network.protocol-handler.warn-external.* to true, the next clicked-on link will ask which program to use for opening that kind of link.

Instead of selecting chromium-browser, you should select /usr/bin/kde-open so that kde uses your default browser to open the link.

---

### Post by wildmanne39 on 2012-07-25
Hi, this is an old thread so it has been closed, please do not post in threads that are a year or more old, and thanks for sharing.

---

