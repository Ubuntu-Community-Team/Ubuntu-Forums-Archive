---
title: "GNOME Do will not display Thunderbird as a program to run"
date: 2010-08-29
forum: General Help
---

### Post by onamattuphere on 2010-08-29
I installed the latest version of Thunderbird by downloading the tarball and copying the contents to the required folder and just point launchers to the Thunderbird file.
However I cannot get GNOME Do to run Thunderbird. When I type run in Gnome Do, I go through the entire list without having Thunderbird as an option. The only plugin I can find is one that allows you to copy Thunderbird contacts to the clipboard.
I have set Thunderbird to be my default mail client, so when I type an email address I can choose to compose a mail in GNOME Do, but just opening up Thunderbird to check mail is not possible.

Google gives me nothing. Please show me what need to be done.

---

### Post by onamattuphere on 2010-08-29
Bump

---

### Post by onamattuphere on 2010-08-29
From the instructions found in the [FAQ]("http://https://answers.launchpad.net/do/+faq/416"), I learned that I need to make some changes in the ~/.local/share/gnome-do/RemapFile - However I'm not sure what to do if Thunderbird isn't installed in the /usr/bin directory. I tried to enter the following line in the RemapFile ```
thunderbird-bin, ~/thunderbird/thunderbird-bin
``` without any success.

Please help me Ubuntuforum, (...you're my only hope..)

---

### Post by onamattuphere on 2010-08-30
Bump.

---

### Post by flick on 2010-08-30
If it were me, I'd uninstall my locally installed from tarball Thunderbird, then add the Mozilla daily PPA and install the freshest Thunderbird from there through my preferred package management tool, which should put all of Thunderbird's files where other programs such as Gnome-Do expect to find them. 

Mozilla Daily PPA :

[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)

---

### Post by onamattuphere on 2010-08-31
Thanks a lot for that - now my Gnome environment is all good! - sleek and luv'leh!

---

### Post by onamattuphere on 2010-08-31
Damn interweb! - Double post..

---

