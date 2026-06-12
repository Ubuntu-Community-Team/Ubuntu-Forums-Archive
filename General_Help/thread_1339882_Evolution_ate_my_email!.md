---
title: "Evolution ate my email!"
date: 2009-11-28
forum: General Help
---

### Post by dwasifar on 2009-11-28
I recently switched from Thunderbird to Evolution.

Evolution is connecting to the mail server using IMAP-SSL.  The mail server is on the local network and is using a self-signed certificate, which means that the first time I used Evolution on this server, it gave me the certificate security warning, which I approved.  Up until today it has not given me any more certificate warnings.  

There were about 88 emails in the server's inbox, when suddenly Evolution put up another certificate warning saying the server certificate belonged to localhost.  I clicked okay, and Evolution promptly wiped my inbox.  Not just locally, either; the mail was gone from the server.  I had to restore it from backup, and I lost a few that had happened since the backup.

Looking at my Evolution configuration in /home/dwasifar/.evolution, I notice there are two more IMAP mail directories on the machine where this just happened than there are on my laptop (which was not running at the time).  On the laptop I have these directories (domain names are not actual):

/home/dwasifar/.evolution/mail/imap/dwasifar1@domain1.com@mail.domain1.com (4 items)
/home/dwasifar/.evolution/mail/imap/dwasifar2@domain2.com@mail.domain2.com (4 items)
/home/dwasifar/.evolution/mail/imap/dwasifar2@domain1.com@mail.domain1.com (4 items) (this is the one that got hosed)

On the desktop, in addition to the above, I have these:

/home/dwasifar/.evolution/mail/imap/dwasifar2@mail.domain1.com (1 item)
/home/dwasifar/.evolution/mail/imap/dwasifar2@localhost (1 item)

I'm thinking that whatever confused Evolution caused it to create a blank directory, then synced it with IMAP, wiping out the mail on the server.

What happened here?  How could I have prevented this?  For the time being I've set my server to back up the mail directories hourly in case this happens again.

---

### Post by PariahVayne on 2009-11-28
It loves the taste of [IMG]http://treesflowersbirds.files.wordpress.com/2009/05/spam.jpg[/IMG]

---

### Post by dwasifar on 2009-11-28
Gee, thanks for the help.

Jerk.

---

### Post by Barriehie on 2009-11-28
Could be a dumb ? but did you look in /home/*user*/.evolution/mail/local or the same .../imap ???

Barrie

Edit: Never mind!  I reread your post!

---

### Post by PariahVayne on 2009-11-28
> **dwasifar said:**
> Gee, thanks for the help.

Jerk.

Sorry, I was stupid to post that.

I hope you find a fix.

---

### Post by dwasifar on 2009-11-28
> **PariahVayne said:**
> Sorry, I was stupid to post that.

I hope you find a fix.

Yeah, and stupid of me to call you a jerk.  You were just kidding, I know.  Sorry.

---

### Post by dwasifar on 2009-11-28
Curiouser and curiouser.

I thought of switching back to Thunderbird.  Thunderbird was configured to use pop3 and bring the mail to local folders, so I went into ~/.mozilla-thunderbird to see if I could change the config so it wouldn't poll as soon as I started it up.  And I found that Thunderbird's mail directory had a timestamp from right when this problem occurred.  

This sent me to the server mail logs to see what had happened around that time, and sure enough, there was a pop3-ssl login right then.  I changed the mailbox passwords and started Thunderbird, and there in Thunderbird's inbox were the missing emails, all 88 of them.  Thunderbird got them via pop3 and erased them from the server.  The cert warning I got must have been from Thunderbird and not Evolution.

The thing is, I *know* I **did not** start Thunderbird. There are no shortcuts to it that I could have hit accidentally, and anyway if I'd started it, I'd have needed to shut it down. But somehow it polled for mail anyway, or something did, using Thunderbird's configuration.

The only thing I can think of is that Firefox did it.  Firefox's mailto application was set to be Thunderbird.  I don't think I clicked on anything in Firefox that would have activated a mail session - I don't even know how that would happen.  But just to be safe I have changed Firefox's mailto application to Evolution and disabled the Thunderbird profile.

---

### Post by PariahVayne on 2009-11-28
> **dwasifar said:**
> Yeah, and stupid of me to call you a jerk.  You were just kidding, I know.  Sorry.

Forgiven & forgotten.

---

### Post by dwasifar on 2009-11-28
> **PariahVayne said:**
> Forgiven & forgotten.

Likewise.

--

I'm marking the thread Solved because it looks like this is not an Evolution problem after all.

---

