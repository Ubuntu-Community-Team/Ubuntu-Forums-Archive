---
title: "Thunderbird help required."
date: 2012-02-06
forum: General Help
---

### Post by ozerus89 on 2012-02-06
Hello all
  Well, I didn't think I was a complete moron but setting up my gmail account in thunderbird is beating the hell out of me, it just claims that I failed authentication I've put it through every possible server combination... And before you ask, I am 1000% certain I've not mis-typed my password because I have been managing to sign in out of google on the browser. any ideas?

Thanks
Rich

---

### Post by mike555 on 2012-02-06
did you enable pop or imap on the gmail site for your account?

---

### Post by Yellow Pasque on 2012-02-06
When I use thunderbird to set up my gmail imap account, it automagically fills in the server settings.

---

### Post by pqwoerituytrueiwoq on 2012-02-06
is imap enabled in your gmail settings?
Settings (top right gear icon) -> Forwarding and POP/IMAP (it is a tab) -> [IMG]http://i.imgur.com/zw2Gf.png[/IMG]
hey look google has a guide [http://support.google.com/mail/bin/answer.py?hl=en&ctx=mail&answer=75726](http://support.google.com/mail/bin/answer.py?hl=en&ctx=mail&answer=75726)

---

### Post by ozerus89 on 2012-02-06
yeah, all of those settings are correct at the point where you config the servers in thunderbird it just keeps telling me ive mis-typed my password. which cant be the case because ive signed out and type the same password into my browser and allowed it. so i genuinely cant see why it wont take it! Much frustration caused! Do we have any other ideas? thanks to those who have helped already

UPDATE: ive changed the password, still no luck, thunderbirds response is "Configuration could not be verified - is the username or password wrong?" it would appear that screaming "NO IT ISN'T!!" doesn't help either, dammit!

Thanks again all who have responded!
Rich

---

### Post by mike555 on 2012-02-06
are you trying to get gmail imap or pop? the settings are different.

for pop they are ; pop.googlemail.com port 995  ssl/tsl normal password

---

### Post by L a r r y on 2012-02-06
> **ozerus89 said:**
> yeah, all of those settings are correct at the point where you config the servers in thunderbird it just keeps telling me ive mis-typed my password......

UPDATE: ive changed the password, still no luck, thunderbirds response is "Configuration could not be verified - is the username or password wrong?" it would appear that screaming "NO IT ISN'T!!" doesn't help either, dammit!

Thanks again all who have responded!
Rich

I just installed Thunderbird and reconfigured my Gmail POP settings (in Gmail) to handle all new mail from this date forward.

Thunderbird auto-configured for IMAP, and I manually configured for POP according to the Gmail configuration instructions, and was met with the incorrect password issue.

Thunderbird says:  "Application-specific password required: **_[http://support.google.com/accounts/bin/answer.py?answer=185833](http://support.google.com/accounts/bin/answer.py?answer=185833)_**"

I will follow-up on that page and report my findings here.

This is different from the Thunderbird setup to use Gmail in the past, where my Google password was what I used in T-Bird.

In your Update, yes I've been there before, tried that.  It doesn't matter how blue the air gets, how loud it is said, the computer just will not pay me any mind!

---

### Post by L a r r y on 2012-02-06
> **L a r r y said:**
> 
Thunderbird auto-configured for IMAP, and I manually configured for POP according to the Gmail configuration instructions, and was met with the incorrect password issue.

Thunderbird says:  "Application-specific password required: **_[http://support.google.com/accounts/bin/answer.py?answer=185833](http://support.google.com/accounts/bin/answer.py?answer=185833)_**"

I will follow-up on that page and report my findings here.



And my follow-up:  I met with success.

Following directions on the page I provided a link to, I had a link to MY password generation page, called my application "Ubuntu Mozilla Thunderbird," hit "Generate Password," and copied the password from the yellow box and hit "Done."

Back to T-Bird, Edit -> Preferences -> Security tab.  There I opened up the saved passwords, removed them all, then closed the Preferences window.

Attempted to get mail, was greeted with the error message again, OK, and then was given an opportunity to enter a new password.  I pasted the previously copied application-specific password that I generated.  Checked the box to remember it.

You may have to revisit that page again and generate a new password from time to time.  Just repeat these steps.

Hope this gets you going!

Be sure to mark your thread as [SOLVED] if you come across a solution! <== Edit

---

### Post by forrestcupp on 2012-02-06
Usually, Thunderbird does a good job of automatically configuring for Gmail. I have had this issue with other types of email, though. For me, it ended up being the username, not the password. You type in your email address, like **username@gmail.com**, but Thunderbird sets your username to only be **username** without the **@gmail.com** on the end, and that is required. 

Try going to the manual setup of your account and see if that's what happened. You may only need to add the **@gmail.com** to the end of your username to get it working. It may not be that, but it's worth checking out.

---

### Post by Krishna Murthy on 2012-02-06
> **ozerus89 said:**
> Hello all
  Well, I didn't think I was a complete moron but setting up my gmail account in thunderbird is beating the hell out of me, it just claims that I failed authentication I've put it through every possible server combination... And before you ask, I am 1000% certain I've not mis-typed my password because I have been managing to sign in out of google on the browser. any ideas?

Thanks
Rich

Go to your account settings, click 2 step verification edit, click manage application specific passwords, enter Thunderbird in the box and hit generate. Paste the password in Thunderbird. Enjoy.

---

### Post by ozerus89 on 2012-02-07
Thank you one and all, 2-step verification solved the problem it went straight through and worked! Thank you all very much for taking the time to post and be genuinely helpful, its most appreciated.

 Thanks again
Rich

---

### Post by jasonrisenburg on 2012-02-07
> **ozerus89 said:**
> Hello all
  Well, I didn't think I was a complete moron but setting up my gmail account in thunderbird is beating the hell out of me, it just claims that I failed authentication I've put it through every possible server combination... And before you ask, I am 1000% certain I've not mis-typed my password because I have been managing to sign in out of google on the browser. any ideas?

Thanks
Rich

Before I got mine to work last year I had to reset my password. I chose a word with 12 letters capts and numbers. Didnt have a problem after.

---

### Post by Cavsfan on 2012-02-09
What version of Thunderbird is the latest? I thought I had version 9 or 10, but today I checked and it is back to version 3.1.18.

Strange! Thanks for any replies!

---

### Post by Krytarik on 2012-02-09
> **Cavsfan said:**
> What version of Thunderbird is the latest? I thought I had version 9 or 10, but today I checked and it is back to version 3.1.18. ... Strange!
That's because the official repos of all current Ubuntu versions - except Oneiric 11.10 - only include the last version of Thunderbird prior to its switch to the rapid release cycle. To upgrade to the current versions of it, which is indeed v10 as of now, the best option is using the "Thunderbird Stable PPA"; please see here for details how:

[http://www.tuxgarage.com/2012/02/thunderbird-10-available-in-stable-ppa.html](http://www.tuxgarage.com/2012/02/thunderbird-10-available-in-stable-ppa.html)

Regards.

---

### Post by Cavsfan on 2012-02-09
> **Krytarik said:**
> That's because the official repos of all current Ubuntu versions - except Oneiric 11.10 - only include the last version of Thunderbird prior to its switch to the rapid release cycle. To upgrade to the current versions of it, which is indeed v10 as of now, the best option is using the "Thunderbird Stable PPA"; please see here for details how:

[http://www.tuxgarage.com/2012/02/thunderbird-10-available-in-stable-ppa.html](http://www.tuxgarage.com/2012/02/thunderbird-10-available-in-stable-ppa.html)

Regards.

Thanks for the link. I'll use it. I just find it ironic that my system updated Thunderbird along with Firefox to the newest 
versions a long time ago. I am on FF 10.0 and was pretty sure that prior to today I was on Thunderbird 10.0 also. I know it wasn't 3.1.18. :confused:
Thanks again for the reply!

I do remember adding the stable ppa for Firefox but, I do not recall adding this one.
Now, I don't remember what I did! I dual boot and have them on both systems. So, I could just be confused! #-o

---

### Post by Cavsfan on 2012-02-09
Worked like a charm Thanks **Krytarik**!!!

---

