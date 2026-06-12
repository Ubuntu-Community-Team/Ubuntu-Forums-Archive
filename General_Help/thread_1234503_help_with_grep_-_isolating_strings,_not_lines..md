---
title: "help with grep - isolating strings, not lines."
date: 2009-08-07
forum: General Help
---

### Post by cbear on 2009-08-07
I am trying to write a script that will scan a an email file/folder where I put all my junk mail.  I want to extract the From: <email addresses> from the file and append them to local.cf (blacklist_from).  I am able to extract the LINES containing the addresses using 

grep From: /home/tbegehr/mail/newspam | grep '>'

this gives me the following output:

From: "Amazon.com" <store-news@amazon.com>
From: "hotels.com" <email@email.hotels.com>
From: "Lone Tree Golf and Event Center" <reply@igmemail.com>
From: Storage Professionals Group Members <group-digests@linkedin.com>
From: "Golf Channel" <listmaster@thegolfchannel.com>
From: "Rebecca Salie" <Rebecca_Salie@mail.vresp.com>

I want to narrow down the output to ONLY the <emailaddress>.

I then will figure out some way to append these addresses to local.cf as blacklist_from....that will be my next project.

thanks in advance for your help :)

---

### Post by asmoore82 on 2009-08-08
```
cat /home/tbegehr/mail/newspam | grep "^From" | grep -o '<[^>]*@[^>]*>'
```
:KS

The "^From" tells grep to only match at the beginning of the line.
The "-o" tells it to only output the match, not the whole line.

That last regex is a little tricky but it can successfully handle multiple
Email addresses on the same line...
<,@,> match literally those characters,
* in a regex means "the previous character repeated as much as possible,"
[^>] matches any character expect a >

I didn't know about grep's -o switch until tonight, went to the manual for that one ;).

---

### Post by cbear on 2009-08-08
thanks....will try that one in a few minutes.  I also tried another way to accomplish my goal of appending the <emailaddresses> to local.cf.

I redirected the output of my previous grep command to a file and then redirect the output into the following spamassassin command for adding to blacklist.  It appears to be adding the addresses, BUT when I look at local.cf, they have not been added.  Where did they get put ? hmmmm.



tbegehr@LINUX03:~$ spamassassin --add-to-blacklist < spam.out

SpamAssassin auto-whitelist: adding address to blacklist: [email]movies@news.fandango.com[/email]
SpamAssassin auto-whitelist: adding address to blacklist: [email]updates@linkedin.com[/email]
SpamAssassin auto-whitelist: adding address to blacklist: [email]1800FLOWERS@e.1800flowers.com[/email]
SpamAssassin auto-whitelist: adding address to blacklist: [email]group-digests@linkedin.com[/email]
SpamAssassin auto-whitelist: adding address to blacklist: [email]Borders@e.borders.com[/email]

---

### Post by cbear on 2009-08-08
thanks asmoore82...that did work like a charm.  My only question is, do I need to omit the < and > from the output ?  The format for blacklist_from in local.cf does not contain < and > ...uses format:

blacklist_from [email]junk@junkmail.com[/email]  

NOT

blacklist_from <junk@junkmail.com>

It seems to me there should be an easier way to append a file with addresses to the blacklist....as I noted in my previous post.  I would think spammassassin --add-to-blacklist  would do the trick, but I cannot figure out where the darn list was written....it aint in local.cf.  Is there another file/location where blacklist data gets written to ?

thanks again :)

---

### Post by asmoore82 on 2009-08-08
I'm not familiar with spamassassin,
but if you need to trim out the <> characters, `tr` could do it:
```
cat /home/tbegehr/mail/newspam | grep "^From" | grep -o '<[^>]*@[^>]*>' | tr -d '<>'
```

at this point, changing the thread title to something about spamassassin might get better attention :P.

---

### Post by cbear on 2009-08-08
changing the subject line since this is a spamassassin question now.

---

### Post by cbear on 2009-08-09
one more questions asmoore82 :)

How can I append a "blacklist_from" to the beginning of each address in this outpout ?  That way I could >> the output to the end of my local.cf file with a nightly cron job.  That would accomplish what I am trying to do.

---

### Post by asmoore82 on 2009-08-10
`sed` could do that:
```
cat /home/tbegehr/mail/newspam | grep "^From" | grep -o '<[^>]*@[^>]*>' | tr -d '<>' | sed 's/^/blacklist_from /'
```

sed's command:
`s` for search and replace;
`^` for beginning of each line.

:KS

---

### Post by cbear on 2009-08-11
thanks...that worked perfect !!

---

