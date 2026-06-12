---
title: "Form/Submit is logging me out"
date: 2010-05-30
forum: General Help
---

### Post by Matt105 on 2010-05-30
Hi everyone. I don't know much about the technical stuff of Ubuntu, but I have been using it for about a year just for web browsing. I have the newest Ubuntu installed on an old laptop and it is fully updated. On certain websites, when I click a form/submit button, it logs me out. I then have to log back in, and am able to then submit the form (such as posting on a forum, although, it didnt do it for me for this forum).

I have a Thinkpad T42 running Ubuntu 10.04 x86 and it's fully updated.

I also can't figure out how to make it so I don't have to type in a password when booting up and when coming out of sleep mode (from closing the screen). I know I'm sacrificing security, but this is a laptop that I just leave out in my living room for me/friends to use, and it is annoying to have to type in the password anytime someone wants to use it. I went into Administration->Login and told it to auto-login, but it still asks for one and I'm not sure if I'm doing this wrong.

One more thing, it asks for my network key everytime I login (whether from booting or waking up from standby, or just logging out and then back in). is there a way to have it save the key?

Thanks.

---

### Post by Jeroensum on 2010-06-01
It seems you have a problem with your keyring manager. To figure out if this is related to security settings on files or to the keyring manager itself, add a new account, (administration -> user and groups) and make sure you tick the setting 'don't ask for password on login' and make sure you set all the same permissions for it as your current account has.
Especially 'administer the system', this will allow you to use (gk)sudo.

Then reboot, and try again :) If you're satisfied just copy over the files you need from your 'old' account and be done with it.

Please leave a message if all worked out (or not) :)

---

### Post by Matt105 on 2010-06-04
Thanks! It seemed like that worked perfectly to fix all of my problems (to be honest, the logging out thing seemed to have just gone away on its own). :D

---

