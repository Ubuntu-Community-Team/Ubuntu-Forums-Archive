---
title: "Sky Webmail ok but password failure with email clients"
date: 2010-10-21
forum: General Help
---

### Post by Original Brownster on 2010-10-21
Hi, 
Just posting this in case someone else has the same problem, it took me a good few hours of head scratching but I resolved it in the end.

I've configured more email clients over the years than I care to mention so I am by no means a newbie at this so when I set up linux for a friend recently (10.10 on a laptop) I came across this problem, the install went wonderfully btw! 

The fix, long story short, if you are a sky broadband customer and are just setting up your email, you'll have a letter informing you of your email address, you log on to sky.com/resetpassword (or similar) enter some credentials and enter a password. 
This worked fine with the webmail, log in no problem, configuring a client (Thunderbird and Evolution) resulted in receiving a login failure with the message similar to 'credential failure' or words to that effect.

So after entering the password again and again, reading and re-reading the sky.com site instructions on setting the correct security settings, checking the correct ports, checking the correct settings to allow an IMAP connection from within the webmail interface and still getting no where I did this:

logged into the webmail interface, then 'mail settings' > 'accounts' > then 'google account settings' then 'change password', this opens a sky.com reset password window. choose the my security question option and use this to enter a new password and this worked.
I suggest not using the 'my email address' and 'send an email with a reset link' option, this was attempted first and resulted in the same issue, new password set for the webmail but still not working with an email client. 

It seems that, and I'll be corrected by anyone who knows for sure, that their software is currently not updating _all the passwords held_ if you use the 'reset password via email link'and neither did the initial setting up of the password work correctly either. 
My best guess is the passwords are going out of sync with their email servers not being updated correctly in all circumstances. 

Once I had reset the password as described it worked first time, so clearly there is something in this.

For info the settings for IMAP:

imap.tools.sky.com  (also found mail.sky.com worked)

username is the full sky email including the @sky.com part

select SSL for encryption (port will change to 993)

outgoing mail settings:

smtp.tools.sky.com

security: use name and password

connection security: use SSL

port should be set to 465

The sky website page seems accurate enough on this info:
[http://tinyurl.com/2vvbuqm]("http://tinyurl.com/2vvbuqm")
Although these instructions are for Outlook 2007 the key information is there.

Hope this helps someone save a few hours of head scratching !!!

---

### Post by BobCots on 2010-12-08
Thanks for this post, I've been trying to get TB to hook up to Sky for the last 3 evenings with nothing but 'invalid credentials' or a time-out.  Sky help is anything but, so I'll try this tonight when I get home.

Bob

---

### Post by Original Brownster on 2010-12-08
Let us know how you get on. I was talking to my Bro. about my theory of the server password databases not being in sync and he confirmed it does happen where he works.

---

### Post by BobCots on 2010-12-09
worked a treat, thanks Wayne.  I followed the instructions in the first post to reset the password and Thunderbird instantly started picking up the mail.  
It sounds as though passwords aren't replicating as I could log into my two Sky email accounts and the customer areas directly, but not access email indirectly with the same password.
We get delays in replicating passwords at work, but that's just a matter of 15 minutes or so, not the 72 hours or more that I'd been struggling for.

I'd report it to Sky except that I ran out of patience running round in circles in their support pages.

Thanks again,
Bop

---

### Post by Original Brownster on 2010-12-09
Great I'm glad it helped you out, I was sure others must have the same problem. 
Ditto contacting Sky support, the thought of spending an hour reporting it to someone (no offence) who's likely level of experience is reading a flow chart of things to try would just about do my head in! 

All the best,
Wayne.

---

### Post by cobaltinfinity on 2011-06-15
Just dropping in to say this also worked for me. The solution seems to lie in resetting one's password as described. 

Using Thunderbird 3.1.10 on Ubuntu 10.10, I initially assumed Thunderbird was trying to connect to the server incorrectly by using the odd-looking address "username@sky.com@imap.tools.sky.com", but this was not the problem. Once I'd reset my password everything worked. 

A belated thanks for your assistance! After faffing around with this for a while last month I had almost given up hope on Thunderbird and had resigned myself to using Sky's webmail interface. :p

---

