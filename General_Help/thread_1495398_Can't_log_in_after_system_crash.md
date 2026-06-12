---
title: "Can't log in after system crash"
date: 2010-05-28
forum: General Help
---

### Post by miststlkr on 2010-05-28
My system [a fresh Mythbuntu 9.10 install as of last month or so with almost nothing changed or added since other than trying to build my myth db and playing with the jamu.py config file] was down when I got home from work today and when I try to log in now I immediately get booted back to the login screen.  Something flashes past but too fast to read; I think it said "no protocol specified", which is splattered all over tty2.  I was able to log in on tty1 and pulled this out of the x errors log in my ~/ but it's greek to me.  If it makes any difference, I had previously not needed to log in; then, despite what the login settings pane said, I had to log in the last couple times I rebooted, now I can't even do that.  I don't now if that is relevant or helpful, but thought I would throw it out there.  

Any ideas why this may have happened and/or how to make it un-happen would be greatly appreciated.  I can't think of any packages that I added since the last reboot.  The only thing new that I can think of that I did this last uptime cycle that I didn't do previously was that I ran x11vnc which had been installed already so I'm not thinking that would be the issue, but who knows.

[http://pastebin.ubuntu.com/440717/](http://pastebin.ubuntu.com/440717/)

[EDIT]  It may also help to know that I was able to create a new user on tty1 and ran ***startX -- :1*** from that user account; X loaded fine that way.[/EDIT]

---

