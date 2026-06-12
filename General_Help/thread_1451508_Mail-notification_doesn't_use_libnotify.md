---
title: "Mail-notification doesn't use libnotify"
date: 2010-04-10
forum: General Help
---

### Post by muadnu on 2010-04-10
I have mail-notification installed (using Lucid beta) but for some reason it doesn't send notifications using libnotify, but instead shows a standard gtk pop-up. I have the evolution plugin for mail-notification installed, and in fact the issue is not related to evolution, since I tried setting up mail-notification directly for an IMAP account and got the same ugly pop-up. Any ideas?

---

### Post by frogotronic on 2010-05-02
same problem - had it working in Karmic, forgot how to configure it...

---

### Post by muadnu on 2010-05-02
I figured it out...

Go to gconf-editor, then apps->mail-notification->popups and erase everything in actions.

---

### Post by frogotronic on 2010-05-02
Awesome!  That was it.


This is almost a bug, isn't it?  How would a newbie ever figure this out?

- CH

---

### Post by muadnu on 2010-05-02
The ubuntu devs decided that popups cannot have any actions associated, and whenever an application tries to show a popup with actions they revert to the ugly default popups. Since the default way to notify new emails in ubuntu doesn't use mail-notification, I think no one thought of making this the default setting for those of use who do like to use it. So I'm not sure it is a bug, it is in my view one more way in which users lose control of their systems with every new ubuntu version.

---

### Post by frogotronic on 2010-05-02
agreed

---

### Post by bob brazie on 2010-05-19
What/how should I change in this to make the pop-up work?
Thanks in advance.Bob.

---

### Post by muadnu on 2010-05-19
> **bob brazie said:**
> What/how should I change in this to make the pop-up work?
Thanks in advance.Bob.
Mmh, I'm not sure what's going on. In my case I also see a key named "actions", and another named "limit". You could try adding a new key (right click->new key), set the name to "actions", the type to "list", and leave it empty. But I'm not sure it's going to work... BTW, did you install the evolution plugin?

---

### Post by bob brazie on 2010-05-19
Is this what you are speaking of?

Could you attach a screen shot of what your keys look like?

---

### Post by muadnu on 2010-05-19
My screenshot is below. But I'm not running Ubuntu now, and hence I'm using the regular libnotify (without notify-osd). When I was using Ubuntu my keys looked exactly like in the screenshot, but the list next to actions was empty (in fact, I had to remove the four entries to get it to be empty).

About the packages I'm not really sure, I don't remember and I can't check. You can look for a package with a name like "mail-notification-evolution-plugin", but I'm not sure if that's the name in Ubuntu, or whether it is packaged as part of evolution-plugins. To check if you have installed, go to Evolution and then Edit->Plugins and look for the plugin named "Jean-Yves Lefort's Mail Notification Plugin". That's what you need installed.

---

### Post by bob brazie on 2010-05-19
Thanks, where might I find:Jean-Yves Lefort's Mail Notification Plugin.

I looked in the software center and couldn't fine it there.

---

### Post by frogotronic on 2010-05-19
sudo apt-get install evolution-plugins-experimental mail-notification mail-notification-evolution

Enable it under plugins (after restart of evolution)

Then follow this post for the fix: [https://bugs.launchpad.net/ubuntu/+source/mail-notification/+bug/355209](https://bugs.launchpad.net/ubuntu/+source/mail-notification/+bug/355209)

Restart evolution

---

### Post by bob brazie on 2010-05-20
Thanks, I wonder why was this not fixed in 10.04.

---

