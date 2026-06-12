---
title: "Thunderbird: Bad key or directory name"
date: 2012-09-13
forum: General Help
---

### Post by Dave_L on 2012-09-13
[Using thunderbird 15.0 on Ubuntu 10.04.4]

I've received a few emails, from a googlegroups.com mailing list to which I subscribe, which produce a popup error dialog when viewed:

> An error occurred while loading or saving configuration information for thunderbird. Some of your configuration settings may not work properly.

When I click the "Details" button, the following text is displayed:

> Bad key or directory name: "/desktop/gnome/url-handlers/UTC+09/command": `+' is an invalid character in key/directory names
Bad key or directory name: "/desktop/gnome/url-handlers/UTC+09/command": `+' is an invalid character in key/directory names

After I dismiss the dialog, I can view the email message, and there are no obvious problems.

Any ideas on why the error occurs?

---

### Post by Bobhuber on 2012-09-13
> **Dave_L said:**
> [Using thunderbird 15.0 on Ubuntu 10.04.4]

I've received a few emails, from a googlegroups.com mailing list to which I subscribe, which produce a popup error dialog when viewed:



When I click the "Details" button, the following text is displayed:



After I dismiss the dialog, I can view the email message, and there are no obvious problems.

Any ideas on why the error occurs?
You might look at this.
[http://kb.mozillazine.org/Transferring_data_to_a_new_profile_-_Thunderbird](http://kb.mozillazine.org/Transferring_data_to_a_new_profile_-_Thunderbird)

---

### Post by Dave_L on 2012-09-13
Thanks for the reply, but that article doesn't answer my question.

---

### Post by quxtilf on 2013-04-12
Error from a email caused this, in my case.
Just deleting this email draft, it's Okay.

---

### Post by houstonbofh on 2013-06-14
Just for the folks that still come across this in a search, it is an old bug from 2010 that no one will fix.  It is because Thunderbird and gconf devs argued about who was supposed to fix it, and it is not found in newer versions.  The bug report and a patch can be found here. [https://bugzilla.mozilla.org/show_bug.cgi?id=541130](https://bugzilla.mozilla.org/show_bug.cgi?id=541130)

---

