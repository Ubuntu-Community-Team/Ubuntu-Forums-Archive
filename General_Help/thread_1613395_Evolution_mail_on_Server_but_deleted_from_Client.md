---
title: "Evolution mail on Server but deleted from Client"
date: 2010-11-04
forum: General Help
---

### Post by Terry1080 on 2010-11-04
Hi,
Just set up Evolution to get my emails from 1and1.co.uk and hotmail. I ticked the box 'leave on server'.

Whilst in the mess of trying to configure two email accounts (using rules and folders), I deleted all my 1and1 emails locally. They remain on the server, but I want them now in my client inbox and Evolution seems to ignore those emails. 

Is there any way I can refresh evolution, so that it doesn't treat these emails any differently to new ones that I retrieve?

Thanks

---

### Post by Terry1080 on 2010-11-04
bump... sorry i'm desperate

---

### Post by e79 on 2010-11-04
I don't know about refreshing, but if your mails are still on the server, I'd suggest to delete and recreate the associated account, they should probably all come back in your inbox.

---

### Post by pricetech on 2010-11-04
Another possibility if you don't want to have to recreate the account settings is to access your email using a web browser, assuming your ISP offers web based access, and undelete the emails.

---

### Post by Terry1080 on 2010-11-04
tried that, I even tried uninstalling and reinstalling Evolution, but don't think I did it correctly or there was a remaining config file somewhere that retained all the data and information...

---

### Post by Terry1080 on 2010-11-04
SOLUTION:

recreating the account in Evolution had no effect, somehow it remembered which I had deleted (even though the emails were in my Inbox on the webclient server)

I therefore created the account again based on an IMAP rather than POP, this way Evolution downloaded all the emails, now i'll continue to use the POP account.

---

### Post by dcstar on 2010-11-04
> **Terry1080 said:**
> tried that, I even tried uninstalling and reinstalling Evolution, but don't think I did it correctly or there was **a remaining config file somewhere that retained all the data and information**...

Correct, probably in the **.evolution** folder but account info is also in various .gnome folders as well.

Since you already have solved it using IMAP you do not have to do anything more, but for future reference if you set up a new Ubuntu user and log into that you can configure Evolution there as a totally fresh install.

---

