---
title: "Go back to using default Thunderbird"
date: 2010-05-23
forum: General Help
---

### Post by MichaëlVD on 2010-05-23
I am a very happy Thunderbird user, but I am a little worried about my current install.

The Thunderbird launcher that I use refers to a version that I installed myself, without using the standard repositories ("/usr/bin/thunderbird-3.0 -> ../lib/thunderbird-3.0.1pre/thunderbird").

I would like to get back to using the default Thunderbird install, which I understand is located here: /usr/bin/thunderbird -> ../lib/thunderbird-3.0.4/thunderbird.sh.

How can I transfer all email and all settings across my various accounts to the default install?

Many thanks!

---

### Post by johngreth on 2010-05-23
Your settings and emails and what not are saved in a randomly named folder in the .mozilla-thunderbird folder in your home folder. (home/<username>/.mozilla-thunderbird/<default gobldygook>/)

after you install the new thunderbird, run "thunderbird -profile-manager" in a terminal and change the default directory to the old settings folder.

---

### Post by MichaëlVD on 2010-05-23
Thanks! I just ran the default Thunderbird, and apparently it noticed that I had a beta built of Thunderbird 3 installed. In the terminal, I received the following message: "Found Beta Participation... keep beta profile." Fantastic!

---

