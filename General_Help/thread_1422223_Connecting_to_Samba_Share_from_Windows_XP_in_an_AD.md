---
title: "Connecting to Samba Share from Windows XP in an AD"
date: 2010-03-05
forum: General Help
---

### Post by davebradford on 2010-03-05
Hello guys,

Got a bit of an issue, can't seem to get my head around it! Thought i might just throw it out there and see what the community can offer up!

I have an Ubuntu server with some shares and a Windows XP client in an active directory, i've created all the right accounts but can't seem to connect my linux box from the XP machine wouldn't the user name box popping up with ACTIVEDIRETORYNAME\username like that? hope that makes sense, the account to access the share is locally created on the linux box?

Hmm what am i doing wrong! 

Many thanks, love this place.

---

### Post by davebradford on 2010-03-05
whoops maybe this should have gone in the Server categories? sorry :(

---

### Post by HermanAB on 2010-03-05
I'm not sure what you are asking, but to connect to Active Directory, you need either Likewise or Samba Winbind.  Read the guides on the Samba web site.

---

### Post by davebradford on 2010-03-05
Hello HermanAB, sorry what i mean't was i've setup a local account on a linux box and configured samba with a share.

I'm trying to connect from a winxp machine in an Active Directory and getting an error and defauling the username to my AD. I cannot seem to connect at all.

Does this make sense? Sorry if i'm not explaining it right?

---

### Post by davebradford on 2010-03-05
Ok so here was my problem after a little digging, now solved!

I had created a local account on the server, but not configured Samba to run with that account simply ran a smbpasswd -a username and set a password.

This now works!

Thanks for for looking, sorry about my mistake!

Love to all!

---

