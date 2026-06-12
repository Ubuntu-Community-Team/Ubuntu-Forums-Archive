---
title: "Preferred Applications has no custom option for internet apps"
date: 2011-06-05
forum: General Help
---

### Post by adempewolff on 2011-06-05
I reported this bug to launchpad ([793212]("https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/793212")), but I wanted to post it on the forum too so others could try and reproduce it.  It should be really easy and quick to reproduce so please take a minute, try it, and indicate if it also affects you at launchpad.  This bug takes out a really neat piece of functionality for those who want to use gmail or owa for their default email (and those who want to use and email or browser client not auto-detected by Ubuntu).

Here is the text of the bug (including instructions to reproduce):

> One used to be able to use a custom application (or run a custom script) for email in the Preferred Applications gui (gnome-default-applications-properties). For example see this tutorial: [http://www.linux-geek.co.nz/2011/06/04/set-gmail-as-default-mail-client-in-ubuntu/](http://www.linux-geek.co.nz/2011/06/04/set-gmail-as-default-mail-client-in-ubuntu/), or bugs filed against this functionality, such as this one: [https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/252253](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/252253).

However, in 11.04 the custom item is no longer present in the drop-down menu. The custom option is still present in the menus for the applications in the other tabs (Multimedia, System, and Accessibility), but it is not present in the two drop-down menus in the Internet tab.

The ability to choose custom default mail and web applications is vital for those who use applications that are not automatically detected by Ubuntu. Furthermore, for those who prefer to use a browser-based email client such as Gmail or Outlook Web App, we need to be able to run a custom script to launch a browser.

As I don't believe I've made any modifications to this part of the OS, this bug should be reproducible by anyone using Natty Narwhale by going to 'System Settings' in the power-menu, then clicking 'Preferred Applications', and then clicking on either of the two drop-down menus in the Internet tab. This GUI can also be accessed by pressing alt-F2, then typing 'gnome-default-applications-properties', or searching for 'Preferred Applications' using Unity.

Email drop-down menu:
[IMG]https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/793212/+attachment/2156104/+files/Screenshot-Preferred%20Applications.png[/IMG]

Browser drop-down menu:
[IMG]https://launchpadlibrarian.net/73036786/Screenshot-Preferred%20Applications-1.png[/IMG]

Custom option in multimedia-tab:
[IMG]https://launchpadlibrarian.net/73036789/Screenshot-Preferred%20Applications-2.png[/IMG]

Old custom option in email menu:
[IMG]http://www.howtogeek.com/wp-content/uploads/2007/05/WindowsLiveWriter/SetGmailasDefaultMailClientinUbuntu_404D/1005200711788098554383499833.png[/IMG]
source: [http://www.linux-geek.co.nz/2011/06/04/set-gmail-as-default-mail-client-in-ubuntu/](http://www.linux-geek.co.nz/2011/06/04/set-gmail-as-default-mail-client-in-ubuntu/)

---

### Post by glowplug19 on 2011-06-20
I am having the same problem. This is really annoying. Why drop something like this?

---

### Post by Automat2 on 2011-06-29
This is several times reported to Launchpad. 

Here are a couple:

[https://bugs.launchpad.net/ubuntu/natty/+source/gnome-control-center/+bug/708382](https://bugs.launchpad.net/ubuntu/natty/+source/gnome-control-center/+bug/708382)

[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/729603](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/729603)

There are some workarounds there but nothing like a permanent and universal solution -such as restoring the *custom* option to the menu.

---

### Post by rlamsfuss on 2011-08-02
Just installed 11.04 Natty and having same problem, really annoying as I use Thunderbird 5 (not included in Ubuntu) and Firefox 7.02a

---

