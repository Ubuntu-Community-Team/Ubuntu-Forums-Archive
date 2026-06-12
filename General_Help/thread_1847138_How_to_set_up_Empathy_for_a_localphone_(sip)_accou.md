---
title: "How to set up Empathy for a localphone (sip) account?"
date: 2011-09-20
forum: General Help
---

### Post by FokkerCharlie on 2011-09-20
Hi All

I have a localphone.com account, which works well enough with Linphone- but I'd like to get it working using Empathy via the sip plugin.

I have tried a bunch of settings, but to no avail.  Has anyone had any success?

Thanks in advance for your guidance.

Charlie

---

### Post by Boondoklife on 2011-09-20
Try the following:

For the username, use the username and password that are shown on the localphone site. Check under Services->Internet Phone. If it complains about the username, try the [email]username@localphone.com[/email]

for the proxy use, localphone.com, port 5060 should be fine.

I believe authentication should be your username also as mentioned above.

**NOTE: **The username and password are not the ones used to login to the localphone website, you have to get them from the section mentioned.

---

### Post by FokkerCharlie on 2011-09-22
Thanks for the response, Boondoklife

Unfortunately, I'm still stuck.  I either get 'Network Error' or 'Unspecified error'.

Any further suggestions welcome.

Charlie

---

### Post by Boondoklife on 2011-09-24
Have you tried it with another client, just to ensure it is not a network/firewall issue?

---

### Post by FokkerCharlie on 2011-09-24
Yes, it works OK with Linphone.  Good suggestion, tho.

Charlie

---

### Post by leithon on 2012-03-03
Hi all, thanks for the discussion. I still can not get Linphone working with a localphone.com account, I don't see where to input the password and the registration (sip:***@proxy.localphone.com, where *** is the SIP ID) always fails due to timeout.
Thanks for any information.

---

### Post by FokkerCharlie on 2012-03-03
Hi

Here's the Linphone settings that are working for me on the locaphone account:

Under Manage SIP Accounts / add or edit:
SIP identity:  sip:123456@localphone.com  (substitute your user no!)
SIP Proxy:     sip:proxy.localphone.com
Route:         sip:
Register duration:  3600

Network settings:
All 3 checkboxes unticked.
SIP:  5060,  Audio:  7078, Video: 9078.
Direct connection to the Internet.

Hope that helps.

Charlie

---

### Post by leithon on 2012-03-03
Hi.. Thank you for your prompt reply
So no need to input the password?
I am still getting the same error: registration failed due to timeout...

---

### Post by FokkerCharlie on 2012-03-03
I think you need to enter the passwrod when prompted, when the service tries to log on or make a call.

Not sure why you are not able to connect.  Hmmm.  :(

---

### Post by leithon on 2012-03-03
Hi..
Thanks for replying, this seems to be the problem: [http://jaykhimani.blogspot.com/2010/03/using-smartvoip-on-ubuntu-910-using.html](http://jaykhimani.blogspot.com/2010/03/using-smartvoip-on-ubuntu-910-using.html)

Ports are blocked...

---

