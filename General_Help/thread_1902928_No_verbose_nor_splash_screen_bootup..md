---
title: "No verbose nor splash screen bootup."
date: 2012-01-01
forum: General Help
---

### Post by birdfoot on 2012-01-01
Hi, I have an Old monitor that is supposed to be "EnergySaver" or something like that. It turns off during boot up of Lubuntu, then turns back on once the desktop is loaded. I'd like to fix this so it has a verbose bootup and splash screen so I can know if anything goes wrong, among other reasons.

Any suggestions?

---

### Post by rsvancara on 2012-01-01
Edit the /etc/default/grub file.

Remove the comment on:

 #GRUB_TERMINAL=console

Hope that helps

-- 
[Know Your Linux?]("http://www.knowyourlinux.com/")

---

