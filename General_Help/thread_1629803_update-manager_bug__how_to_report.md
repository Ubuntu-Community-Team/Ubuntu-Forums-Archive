---
title: "update-manager bug / how to report?"
date: 2010-11-24
forum: General Help
---

### Post by Indian Summer on 2010-11-24
Hi,

I was going to try and upgrade my Lucid Lynx laptop to Maverick Meerkat. Yesterday I upgraded to Lucid Lunx from Karmic Koala, and that worked well. So today I ran the update manger as usual, clicked on the "Upgrade" button etc. After a relatively short time I got a pop-up error message that said:

> Invalid package information

After your package information was updated the essential package 'ubuntu-minimal' can not be found anymore.
This indicates a serious error, please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report.

Now, I wanted to report it, but it seems ubuntu-bug is not going to cooperate as it claims it can't connect to the bug database. I am behind a proxy, but I have the environment variable http_proxy set, and wget works fine etc, so I don't understand why ubuntu-bug won't work. (I also have [System -> Preferences -> Network proxy] preferences set up correctly, although I haven't clicked the "Apply System-wide" button because last time I did that it messed up my Evolution so much I spent days trying to revert and repair it.)

Anyway, I'd be very grateful for any help with either problem - the update-manager bug and/or the bug reporting problem.

---

### Post by Indian Summer on 2010-11-25
Ok, I solved one problem: I managed to report the bug using ubuntu-bug after I got the bright idea of temporarily switching over to our visitors network which is not behind a proxy like the staff network is.

---

