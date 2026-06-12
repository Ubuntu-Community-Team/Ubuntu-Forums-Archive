---
title: "Link in Thunderbird won't launch Firefox"
date: 2012-08-05
forum: General Help
---

### Post by pierrep on 2012-08-05
Hi, I was working with Chromium since a year or more without any problem. As Chromium is not updated in the ppa since version 18 I have removed it and switched back to Firefox. 
I made Firefox the default browser but clicking a ling inside email (thunderbird) continues to launch Chromium. So I removed Chromium, and now  when I click a url link from inside Thunderbird it does not launch nothing at all ... no reaction at all. Of course I can copy and paste the link manually to Firefox and it works, but it's a pain.

I have already check the following:
- Firefox IS the default browser. It is set both in Firefox and in Gnome applications setting
- In:   ~/.local/share/applications/mimeapps.list ,  firefox is well configured
- Also in:  /usr/share/applications/defaults.list

I use Ubuntu 12.04.
The same occurs either I login with Unity or Gnome 3
I discovered this with Firefox 14.01 (did not used it before, so I don't know if it would work ok with previous versions). Now I have updated to Firefox 15 from the ppa beta channel... no change in the behaviour.

Thanks for any help...

---

### Post by jobsworth on 2012-08-30
Thunderbird>Edit>Preferences>Attachments>Incoming

says: http Use Firefox Web Browser (default)
and the same for https

only of course it does not!

Change to http Use other...

then browse to File System>usr>bin>firefox

and do the same for https

and voila links in Thunderbird point to firefox!

Why could not that be the default in Thunderbird?
like it is in Debian.

---

