---
title: "About the list option when start computer"
date: 2011-01-29
forum: General Help
---

### Post by nvcnvn on 2011-01-29
I'm using Ubuntu 10.04 LTS and Windows 7 together, Ubuntu for may job and Windows for games..

When I start my computer like everyone I see, like this one:
[IMG]http://gallery.techarena.in/data/519/grub_00.jpeg[/IMG]

but my issue is when I update linux header, i see two more rows in this scren!!
for now I can see in this screeen of my pc about 10 line (linus header version and it recovery mode) (I have update 3-4 time)

Is this ok, because I have get an error when I'm update before (one time - when I'm updateing I open terminal - tasksel and try to install LAMP and do some thing more I not sure!)

Can I stop it, just keep the lasted header option to run my Ubuntu in this screen!?

Sr for my English!
Thanks for your help!

---

### Post by sikander3786 on 2011-01-29
I suspect you've installed Ubuntu inside Windows using the Wubi installer. If yes, I would recommend to apply the Permanent Fix from this page so that updates don't cause you troubles later.

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

Regarding the Grub menu entries, it is advised that you keep at least one older kernel so that if you are unable to boot using the latest one, you can atleast boot using the older one and diagnose/solve the problem.

[http://ubuntuforums.org/showthread.php?t=1587462](http://ubuntuforums.org/showthread.php?t=1587462)

---

