---
title: "Can't set Firefox-3.5 as default browser in Thunderbird"
date: 2009-08-06
forum: General Help
---

### Post by kyfho23 on 2009-08-06
I can't set Firefox 3.5 as the default browser to open links in Thunderbird,or to open links in a running instance of Shiretoko. I have ALREADY tried the following:

Set firefox-3.5 %s as my default browser in /System/Preferences/Preferred Applications
Set firefox-3.5 as my default browser thru the command line using "sudo update-alternatives --config x-www-browser"
Edited Thunderbird's about:config, user.js and pref.js files to network.protocol-handler.app.http, network.protocol-handler.app.https, and network.protocol-handler.app.ftp to "firefox-3.5", "firefox-3.5 %s", "/usr/bin/firefox-3.5", and "/usr/bin/firefox-3.5 %s".
Checked the mozillaZine site for any further ideas.
Tried deleting the network.protocol entries from user..js and prefs.js, closing Thunderbird, running the "update-alternatives" command again, and then reopening Tbird. The about:config entries show /usr/bin/firefox-3.5 .

Note: I can run Shiretoko (Firefox-3.5) from a desktop link or from the command line (using "firefox-3.5"). I can also set Swiftfox as the default browser, editing the user.js or about:config method I mentioned above.

This has really got me stumped. I've been playing with this for a few days now, and I'm really frustrated at my inability to fix this. According to everything I've read, things SHOULD work, especially after editing the network.protocol entries in about:config.

I do get a quick flash of something on the screen Thunderbird is on, something like the extensions dialog, but nothing opens.
I am getting no error messages or any messages, by using the terminal to open Thunderbird.

Any ideas would be gratefully received. I'm using Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.1.3pre) Gecko/20090805 Ubuntu/9.04 (jaunty) Shiretoko/3.5.3pre, from the repository.

[https://bugs.launchpad.net/bugs/409767](https://bugs.launchpad.net/bugs/409767)  has been filed.

---

### Post by lidex on 2009-08-17
Got mine to work simply by inserting "firefox-3.5 %s" in Preferred Applications. Using Thunderbird 2.0.0.22 and Shiretoko 3.5.2 pre. About config in t-bird shows only this for network.protocol.* settings (see attached). Wait, I take that back, I did, very first thing, use "Ubuntu Tweak" to change all file types associated with "Firefox" to "Shiretoko Web Browser" (see other attachment). It did not initially appear in edit window so had to add. Let me know.

BTW, I uninstalled Firefox 3.0 and everything related with synaptic before installing 3.5. I then deleted all firefox folders I could find and selected only firefox 3.5 for install so it's running without ubufox or gnome-support.

---

### Post by lidex on 2009-08-17
Something that might narrow it down - if you have another program that presents clickable links or can install one - if that program opens Shiretoko then it's most likely a t-bird issue. If not, then probably system/Shiretoko problem.

---

