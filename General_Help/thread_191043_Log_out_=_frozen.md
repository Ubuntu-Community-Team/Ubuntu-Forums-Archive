---
title: "Log out = frozen"
date: 2006-06-07
forum: General Help
---

### Post by ericesque on 2006-06-07
I did a search because I seem to remember seeing other people with a similar problem a few days before dapper stable was released, but I'm not finding anything now...  

SO

When I log out my computer seems to hang.  It starts to load up the log in but never gets there.  I'm left with an all white screen-- save for the outline for the text box where you usually enter your user name.

any thoughts?  Did other people encounter a similar problem a while back or am I just crazy?

Thanks

---

### Post by caldevil on 2006-06-07
Are you using fglrx? There was an issue with fglrx some time back.

---

### Post by Kilz on 2006-06-07
[QUOTE=caldevil]Are you using fglrx? There was an issue with fglrx some time back.[/QUOTE] Its what the 8.25.18 drivers do to the x series.

---

### Post by joske on 2006-06-07
see [bug 30447]("https://launchpad.net/bugs/30447")

I'm having this too. Setting AlwaysRestartServer=true in gdm.conf fixes this for me, but not for all people...

---

### Post by frodon on 2006-06-07
Do you use composite display ?

---

### Post by ericesque on 2006-06-07
@ caldevil:   yes
@ Kilz:        that's the driver I'm using
@joske:       Do I have to add that line to gdm.config?  I don't see AlwaysRestartServer anywhere in the file.

@frodon:      I feel stupid asking, but what is a composite display?  It's a laptop--and I'm using it's screen if that helps.  I'm assuming the answer is no.

---

