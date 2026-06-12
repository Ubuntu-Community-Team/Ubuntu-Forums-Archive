---
title: "Only half of network works/Need help to edit file"
date: 2012-06-19
forum: General Help
---

### Post by magpie03 on 2012-06-19
Hello all. I am running Ubuntu 12.04 64 bit. This is a dual boot with windows 7 64 bit. Set it up two weeks ago. This is wired directly to the router. Internet works but cannot connect to any other computer on my network. Other computers include Windows XP and Ubuntu 11.10 machines. I have a NAS with a printer attached. 12.04 seen the printer and set it right up. I can log into the NAS admin section thru my web browser. But, I cannot mount the drive. From what I found this is a bug and I need to edit my /ect/smaba/smb.conf file. I am supposed to add the following lines to the bottom of the [global] section:
    client lanman auth = yes
    client ntlmv2 auth = no
So my question is, where excatly is the "bottom" of the [global] section?
From my home folder I get an error when I click on browse network.
Many thanks all.

magpie......

---

### Post by HiImTye on 2012-06-19
the bottom of it would be directly above any shares or other sections, i.e. the very next part that is encased in square brackets, such as [Shared] or [Videos] or w/e
if you lack any of these sections then the bottom of the file will do. easiest way to find it is to use the find function in whatever editor you are using and then search for square brackets, move above the one that follows [Global]

---

### Post by magpie03 on 2012-06-19
Thanks HilmTye. I'll try it out. If it works I'll this as solved.

magpie...........

---

