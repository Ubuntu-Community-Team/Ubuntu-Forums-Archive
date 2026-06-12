---
title: "Opening Thunderbird 3 URLs in Google Chrome"
date: 2010-09-11
forum: General Help
---

### Post by anlag on 2010-09-11
My TB3 insists on opening all URLs in Firefox. I've moved on to Chrome as default browser and would like all my links to open there. 

Have done/checked:

1. 
Chrome is set as my default web browser (Prefs->Preferred Apps)

2. 
The Gnome config seems indeed to be set to use Chrome.
anlag@casper:~$ gconftool-2 -g /desktop/gnome/url-handlers/http/command
/opt/google/chrome/google-chrome %s

(same with https)

3.
Went into TB's about:config and looked for relevant settings, found nothing but another thread on here suggests *network.protocol-handler.app.http* should decide which browser to use. This didn't exist; I tried creating it and using both the full output of gconftool-2 above, and simply "google-chrome" but neither makes a difference.

4.
Went into TB's Preferences->Attachments and looked for settings for http/https, also going on another suggestion on here. I have neither entry in that list (only JPEG) and see no way to add anything.


What can I do? Thanks in advance.

---

### Post by anlag on 2010-09-17
Hate to bump, but this is doing my head in. I can't believe it's such an ordeal to change something as simple as which browser to use to open these links. I assume Thunderbird doesn't care about the system's preferred applications but shouldn't there then be some convenient way to set it inside TB itself? Am I missing something obvious here?

---

### Post by scouser73 on 2010-09-17
Hi anlag, if you go to **Preferences** [COLOR="Red"]**>**[/COLOR] **Preferred Applications** and click the Web Browser drop-down menu and select Google Chrome as the default handler for URLs.  Now when you click on a link in Thunderbird it will open up in Google Chrome.

---

### Post by wilee-nilee on 2010-09-17
> **scouser73 said:**
> Hi anlag, if you go to **Preferences** [COLOR="Red"]**>**[/COLOR] **Preferred Applications** and click the Web Browser drop-down menu and select Google Chrome as the default handler for URLs.  Now when you click on a link in Thunderbird it will open up in Google Chrome.

That works I checked it out.

---

### Post by anlag on 2010-09-17
> **scouser73 said:**
> Hi anlag, if you go to **Preferences** [COLOR="Red"]**>**[/COLOR] **Preferred Applications** and click the Web Browser drop-down menu and select Google Chrome as the default handler for URLs.  Now when you click on a link in Thunderbird it will open up in Google Chrome.

Thanks for the reply. The problem is, that doesn't do it for me. Chrome is selected as default browser in Preferred Applications, but TB still opens links with Firefox. The problem isn't restricted to Chrome though; I've tried picking other preferred browsers such as Opera and Konqueror, with no difference. Links still open in Firefox.

The way I see it there has to be something in Thunderbird that's overriding the default system setting, but I can't for the life of me find where or what it is.

---

### Post by scouser73 on 2010-09-17
Check this link on how to fix it: [http://www.chromeboard.com/showpost.php?p=31314&postcount=10](http://www.chromeboard.com/showpost.php?p=31314&postcount=10)

---

### Post by anlag on 2010-09-17
> **scouser73 said:**
> Check this link on how to fix it: [http://www.chromeboard.com/showpost.php?p=31314&postcount=10](http://www.chromeboard.com/showpost.php?p=31314&postcount=10)

I tried that one before already:

anlag@casper:~$ gconftool-2 -g /desktop/gnome/url-handlers/http/command
/opt/google/chrome/google-chrome %s

Tried to change it from the full path to just 'google-chrome %s' in case it would do anything but no luck. I believe this in fact does the same thing as changing the default in Preferred Applications, and apparently Thunderbird isn't paying attention to that setting.

---

### Post by chielchiel on 2010-11-04
Did you found a way to fix this? I'm also having this problem.

---

### Post by anlag on 2010-11-05
Actually, I did! Meant to get back and post but it appears that I forgot.

The problem occurred for me when I had Thunderbird start automatically as the system booted, which I had done by placing it some mechanism or the other under /etc - can't remember the exact location and that laptop isn't down with hardware failure at the moment. This caused it to run as root, which meant my user level settings for browser preferences etc in Gnome had no effect. Surprisingly it still ran with my user profile and functioned perfectly otherwise with my previously set e-mail accounts, or I would of course have noticed much sooner.

If I start Thunderbird manually, it works fine and opens links in Chrome according to my user preferences ("Preferred Applications"). Similarly before when I had it start in ~/.profile, and I imagine it will do the same when placed in "Startup Applications" which I just discovered a short while ago.

So the bottom line is, my Thunderbird process didn't belong to me but rather to root. Try checking for that yourself, for instance by starting it manually (or doing a 'ps -ef | grep thunderbird' to look for owner) and see if that makes any difference.

Hope that helps!

---

