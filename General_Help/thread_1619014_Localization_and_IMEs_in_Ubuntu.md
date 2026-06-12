---
title: "Localization and IMEs in Ubuntu"
date: 2010-11-11
forum: General Help
---

### Post by awp2513_ on 2010-11-11
Hello,

I'm new to the forum, so maybe this isn't best place to put this. Nothing looked better.

I'm in a somewhat unique position with a system I've been handed. The system is Ubuntu 10.4 Netbook Remix. On boot, grub boots into text mode (proper term?). From here, a windowed Java application is started. 

Once the application is started, I would like to use ibus, scim, or some other IME to allow the user to type in Chinese, Japanese, or Korean characters.

I'm new to Ubuntu in general, so maybe I'm not asking the correct questions but:

1.) do ibus and scim only work when run from GDM or KDE, or can I start them before/after the java application is started? If so, what commands to I need to execute? Can I execute these from the Java application, or do they need to be executed before the application is started?

2.) How do the LANG, LANGUAGE, and other "locale" environment variables play into what language the user can type in (what do ibus or scim look at?)

3.) I need to "switch" the system language, and as such the language the user can type in, when the user chooses to change it. For example, if a user selects "Chinese", I would like the java application to start up, and when the user presses "Ctrl+Space" (for example), the user will be able to type in simplified Chinese, but not Korean or Japanese. What can I do to accomplish this?

I've looked into /etc/default/locale, "im-switch", and locale-gen. I think I'm just missing how everything works together.

Any help would be appreciated. If I can provide additional information that could be useful, please let me know.

Thanks in advance!

---

