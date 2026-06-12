---
title: "How to use an email client like Alpine to read my imported email?"
date: 2011-02-24
forum: General Help
---

### Post by lkrubner on 2011-02-24
So, we had a server with Hostway, and it was running ubuntu. The server also had Plesk installed, which did some funny things. We had several websites on that server, and many email addresses. 

Then we changed servers. Now we have a server through Rackspace and it is also running Ubuntu. It also has Virtualmin installed, which generally does not impose as many unconventional changes on Ubuntu as Plesk did. 

Rather than using Thunderbird to download my email (which is what I used to do) I've decided I'll start reading my email on the server. So I will ssh to the server and then use some email client, such as Alpine, to read the email. So I installed Alpine. 

Here is the issue:

I have an email account for "lawrence". The email address is lawrence @ krubner . com. 

Currently, when mail arrives for that account, it is stored here:

/home/krubner/homes/lawrence/Maildir/new

and then it is transferred to hear: 

/home/krubner/homes/lawrence/Maildir/cur

When I start Alpine, while logged in as lawrence, Alpine automatically sets up an inbox for me here: 

/home/lawrence/mail/

How do I get Alpine (or any other client) to read from the correct folder?

I'm fairly sure the email package (the MTA) at work on this new server is Postfix. As near as I can tell, my email is held for 24 hours in this folder: 


/home/krubner/homes/lawrence/Maildir/new

and then it gets transferred here:


/home/krubner/homes/lawrence/Maildir/cur

Alpine only lets me set one path for my Inbox, so I'm not sure what path I should set. If I use "cur" I will see all email 1 day late, but if I use "new" then I will miss email if I go a day without checking.

---

### Post by lkrubner on 2011-02-25
I was hoping to do this without downloading the email. Perhaps that is not possible? Anyway, I got Alpine working for me as a simple POP3 client. I was assuming that it could read the mail straight from where the mail was stored on the server, but I guess not.

---

### Post by marshag63 on 2011-02-26
I know Mutt can be setup to read gmail - at least it can in a distro called INX (live cd) :  [http://inx.maincontent.net/devel/unstable/lucid-inx/inx-lucid-alpha-2.iso](http://inx.maincontent.net/devel/unstable/lucid-inx/inx-lucid-alpha-2.iso)  (this link is for lucid base).  

It has a tutorial on using mutt and will help you access gmail via the live cd and if you like it, you can figure out the settings you need.

Hope this helps :)

MDG

---

