---
title: "Thunderbird link browswer"
date: 2010-10-13
forum: General Help
---

### Post by Jimmmac1 on 2010-10-13
Hi all

Anyone know where you set the browser preferences for Thunderbird?  I upgraded yesterday and now every time I click a link from an e-mail, it uses Google Chrome browser to bring up the link.  Thanks.

Jim

---

### Post by reobedr on 2010-10-14
IF you go to preferences and attachments tab, you can set what program to use for http and https (and ftp) "files".

Also thunderbird should follow the system wide settings for preferred apps...

---

### Post by Jimmmac1 on 2010-10-14
Hi reobedr

Thanks for your response.  It only had one entry, for MS Word documents.  I don't see any way to add any.  I use mainly Firefox and have all the guards on that, so I would like it to use it.  System wide preferences should be Firefox.  How would I check?  Thanks again.

Jim

---

### Post by reobedr on 2010-10-14
You can check your preferred apps in system, prefs, preferred apps (or use a terminal and type: gnome-default-applications-properties

If you go to the advanced config editor in thunderbird (preferences, advanced, config editor, click I'll be careful I promise and then add a new string with name: 
network.protocol-handler.app.http and value: firefox
Next add another string with name: 
network.protocol-handler.app.https value: firefox

(optional: add one for ftp: network.protocol-handler.app.ftp)

After you did that, there should be new values in the attachment tab of your thunderbird preferences.

---

### Post by Jimmmac1 on 2010-10-14
Hi reobedr

Thanks, that did it.  I went to system, prefs, preferred apps and changed the Internet dropdown from Custom (which I never set) to Firefox.  Now all links are opened in Firefox.  I think the new Ubuntu must have changed it, since I didn't.  Problem solved.  Thanks again.

Jim

---

### Post by reobedr on 2010-10-14
Glad I could help, happy surfin'!

This thread can be marked solved :P

---

