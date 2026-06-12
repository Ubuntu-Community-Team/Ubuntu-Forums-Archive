---
title: "VHCS and Breezy"
date: 2006-03-28
forum: General Help
---

### Post by guysmiley on 2006-03-28
Is anyone out there using VHCS and Breezy?  If so, did you have any errors on installation?  Is it running smoothly?  Was the config a beast?

I'm looking at installing it on a test server for some clients...

gs

---

### Post by John.Michael.Kane on 2006-03-28
[http://www.ubuntuforums.org/showthread.php?t=25722](http://www.ubuntuforums.org/showthread.php?t=25722)
[http://www.debianhelp.co.uk/vhcs.htm](http://www.debianhelp.co.uk/vhcs.htm)
[http://www.debianhelp.co.uk/vhcsdeb.htm](http://www.debianhelp.co.uk/vhcsdeb.htm)
[http://www.debianhelp.co.uk/vhcs2.4.7.htm](http://www.debianhelp.co.uk/vhcs2.4.7.htm)
[http://www.debianhelp.co.uk/updatevhcs.htm](http://www.debianhelp.co.uk/updatevhcs.htm)

---

### Post by guysmiley on 2006-03-28
Hey SD,

Yes, I've done a fair bit of research as to how the install proceeds and what the sysop/client will be exposed to ;), but I was really more interested in how Ubuntu users are finding things.  I've checked around the forums and noticed many users having difficulty with the install and the Gandalf's server is currently down causing some ppl to really struggle with the setup of things.

So, how are ppl finding vhcs functioning on a Ubuntu install?

gs

---

### Post by rawoo on 2006-03-29
[QUOTE=guysmiley]Hey SD,

Yes, I've done a fair bit of research as to how the install proceeds and what the sysop/client will be exposed to ;), but I was really more interested in how Ubuntu users are finding things.  I've checked around the forums and noticed many users having difficulty with the install and the Gandalf's server is currently down causing some ppl to really struggle with the setup of things.

So, how are ppl finding vhcs functioning on a Ubuntu install?

gs[/QUOTE]


Hi, using the script at [http://sol.cs.uwindsor.ca/~anas/vhcs/vhcs](http://sol.cs.uwindsor.ca/~anas/vhcs/vhcs) made the installation almost painfree. I installed vhcs on a fresh installation of Breezy and found the whole process very straight forward. Even the actually use of this panel, although severely lacking in formal documentation, is not difficult after trying the various options available to the admin, reseller and user. Getting the email to work has been a little difficult though. I can send but not receive email through vhcs. As a total newbie to linux, this is truly a learning experience, but if I can get vhcs installed on Breezy without have the second guess the auto script, anyone with a bit more experience should do just fine.:D

---

### Post by heislord5 on 2006-04-12
Hi,

I setup server with no problems...lol...was easier than setting up my wireless card! I get the default page for my website. I use zoneedit. Server has internal ip from router. Apparently all that is working fine. I have ddclient or whatever it is called to update the ip address. No problem getting to my website [www.predestine.org](www.predestine.org).

Can get to webmail after fixing the before mentioned Header on multiple lines problem.

Can send myself mail in mock account: [email]random@predestine.org[/email].
I receive it from my own account.
Do not receive email from other accounts. Emails sent to other accounts do not arrive.

dnsreport says:


> Getting MX record for predestine.org (from local DNS server, may be cached)... Got it!

Host Preference IP(s) [Country]
mail.predestine.org. 0 [No IP found]

help please? I really appreciate it.

---

### Post by heislord5 on 2006-04-12
any ideas?

---

### Post by heislord5 on 2006-04-12
when I set zoneedit to use mailserver with settings:
mail.predestine.org &
predestine.org

That may be why the ip is not being found, but how do I fix that?  Assuming it was static, how would I change the settings in zoneedit to find it?  Now what do I do since it is dynamic

Thanks,
heislord5

---

### Post by heislord5 on 2006-04-12
I added:

mail.predestine.org

to the "IP Addresses (A)" section with the same IP address as the [www.predestine.org](www.predestine.org) section.

In the (MX) record I added:
mailserver: mail.predestine.org
maildestination: predestine.org

am I missing something....it is still not working.

---

### Post by heislord5 on 2006-04-12
Had to delete the MX record and add the A record for:

mail.predestine.org

on the zoneedit.com website

---

### Post by heislord5 on 2006-04-12
Added MX record back in at zoneedit help's request...it seems to find everything now at dnsreport.com.  Don't know why it didn't before...but oh well.  So now have both A and MX record for mail.predestine.org

---

