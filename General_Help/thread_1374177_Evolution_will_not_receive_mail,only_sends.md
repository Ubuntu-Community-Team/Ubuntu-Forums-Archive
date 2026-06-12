---
title: "Evolution will not receive mail,only sends"
date: 2010-01-06
forum: General Help
---

### Post by Georgia boy on 2010-01-06
Hi. I had removed Evolution before because of not receiving but then reinstalled after reading where it can cause problems if removed. But, still same problems. It comes back saying that error sending password, that error invalid user name or password. Everything is correct. Settings is Pop,my user name for the web server mail, and also the password. It is also set for online. Have been using Thunderbird but still would like to get this working if possible. 

Thanks

Tom

---

### Post by Georgia boy on 2010-01-08
Here is an attachment of what happens when I try to receive mail. I have the settings set right in the receiving as far as I can tell. Still can't receive. Tried again today. About ready just to quit messing with it and stick with Thunderbird and Lightning. Easier to use.

Tom

---

### Post by plucky on 2010-01-08
From what I have read on the [cox.net website](http://support.cox.com/sdccommon/asp/contentredirect.asp?sprt_cid=31c1cc8a-7eed-4cf4-ac66-7e2a2babd8ba),you need to use port 995 and SSL security.

Open evolution and go to **Edit > Preferences > Mail Accounts > Select Account > Edit > Receiving email** and in the server line put ```
pop.west.cox.net:995
``` and select **SSL encryption** in the "Use secure connection" box and tick the remember password box.

Then close the preference windows and select send/receive icon and it will ask you for your password.Enter and see if it now works.

You might have to do something similar for the SMTP server.

Good Luck

---

### Post by Georgia boy on 2010-01-08
Thanks Plucky. Will give that a shot tomorrow when I get a chance to get on again. I'll let you know what happend. Sure appreciate it.

Tom
Hopefully Won't have to do anything with the sending part. So far I've sent emails to myself from Evolution but would have to retrieve using Thunderbird. Wasn't able to use the receiving with Evolution. Give a shot this weekend and post back results.

Again, thanks for the advice.

Tom

---

### Post by Georgia boy on 2010-01-09
Tried the response but still won't log in and receive emails and what I get when trying to receive emails.
Thanks for any more suggestions.

Tom

Decided to give up on this. I had gone to the Online Help of Evolution. Should check out the many problems there on Evolution. Thunderbird and Lightning works for me so I'll just stick with it. I was just trying to get it fixed because it had gotten under the skin. But seems like I've hit a brick wall. So, stick with what works right?
Thanks for the suggestions.

Tom

---

### Post by dcstar on 2010-01-10
> **plucky said:**
> From what I have read on the [cox.net website](http://support.cox.com/sdccommon/asp/contentredirect.asp?sprt_cid=31c1cc8a-7eed-4cf4-ac66-7e2a2babd8ba),you need to use port 995 and SSL security.

Open evolution and go to **Edit > Preferences > Mail Accounts > Select Account > Edit > Receiving email** and in the server line put ```
**pop**.west.cox.net:995
``` and select **SSL encryption** in the "Use secure connection" box and tick the remember password box.
..........

And it also specifically says to use **spop** instead of pop when using SSL.

Type over the prompted password with the correct one if you get that prompt again.

---

### Post by Georgia boy on 2010-01-10
Boy do I feel dumb. Look at the attachment I had included. On the tab for receiving email where it says to put User Name I had put my email address. :oops:
Jazzy_Jeff had suggested that I look and try that again. Sure enough I saw my screw up and fixed it. Then when I sent from Thunderbird I was able to receive in Evolution. Simplest things can really jump up and kick you in the rear can't it? 

Thanks everyone for checking into this and offering suggestions as how to make it work. Can't believe that I kept overlooking that simple thing each time I went back to that tab or looked at the attachments.

Tom

---

