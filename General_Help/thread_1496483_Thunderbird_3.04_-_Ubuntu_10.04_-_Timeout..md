---
title: "Thunderbird 3.04 - Ubuntu 10.04 - Timeout."
date: 2010-05-29
forum: General Help
---

### Post by KeithSloan on 2010-05-29
Had to do a fresh install of 10.04 as upgrade went pear shaped. Now I cannot get Thunderbird 3.0.4 to work just keeps timing out trying to access mail server pop.1and1.co.uk.

Had to change some Firefox options to get it to work with any site other than google.

Noticed that ping pop.1and1.co.uk sometimes gave a bad address until I disabled IPv6.

Tried setting up evolution same looking problem.

---

### Post by dunbrokin on 2010-05-30
I have this problem also in both TB and Evolution.

---

### Post by Mickser_52 on 2010-06-07
I am also having a problem with Thuderbird since switching to Ubuntu 10.04. It is taking a very long time to connect to the server. This was not happening with 9.10.

I'm not sure if this is a similar problem with a similar solution or not. But I notice that this thread is a week old now with no suggestions?

---

### Post by Mickser_52 on 2010-06-07
Obviously not the same problem disabling ipv6 has solved my slow connecting problem.

Is your pop server setting set to port 110. When I tried changing this I was getting timing out error?

---

### Post by cnewswanger on 2010-10-28
Getting server timeout error in both Thunderbird and Evolution.
Started happening on October 26th.  Thunderbird timed out after 20 seconds no matter what timeout settings were used. No changes in firewalls, email is accessible through my phone using the same settings.

Loaded Evolution today and got the identical result.:(

---

### Post by Ralph L on 2010-10-28
Don't know if this is of any help, but maybe.  I am running Thunderbird 3.1.4 on lucid 10.04.  I have my POP port set to 995 and my outgoing port set to 465.  My account is on Mediacom (mchsi.com) and I have a cable modem with a wifi router.  I had to use these port settings to get TB to work away from home--in wifi coffee shops, etc.  Although I have had trouble with some extensions in the past, I am having no problems now.  I fixed the extensions problems by starting TB from Terminal with the command "thunderbird -safe-mode" and removing extensions.

Ralph

---

### Post by 99_rover on 2010-10-29
Running Thunderbird 3.0.10 on Lucid - suddenly started timing out for the output server - input is fine (Port 995) tried shifting output port to 465 but still times out.

Any solutions out there?

---

