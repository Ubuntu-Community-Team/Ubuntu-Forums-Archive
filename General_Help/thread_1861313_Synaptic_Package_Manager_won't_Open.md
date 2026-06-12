---
title: "Synaptic Package Manager won't Open"
date: 2011-10-15
forum: General Help
---

### Post by joeturtle on 2011-10-15
Hi. I just updated to Ubuntu 11.10 yesterday from 11.04. But now, Synaptic Package Manager won't stay open. (It'll ask me for my password, open for a split second, then close). When I ran it through the terminal, I got the following error message: 

"terminate called after throwing an instance of 'std::out_of_range'
  what():  vector::_M_range_check"

Do any of you have a solution as to how to fix this? It would be greatly appreciated! Thanks! (And if you need more information, feel free to ask!)

---

### Post by effenberg0x0 on 2011-10-15
Can you run sudo apt-get update && sudo apt-get upgrade at a terminal or do you also receive errors?

Effenberg

---

### Post by joeturtle on 2011-10-15
No. I don't get any errors when I run " sudo apt-get update && sudo apt-get upgrade". It seems to run fine.

---

### Post by effenberg0x0 on 2011-10-15
Please try this workaround:

[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/839219/comments/16](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/839219/comments/16)


Report back. 

Effenberg

---

### Post by Utew on 2011-10-15
@joeturtle,

For what it's worth, I had this same problem with synaptic, when upgrading from 11.04 to 11.10, back when beta 1 was released (of 11.10). The upgrade went fine, with the exception of synaptic not wanting to stay open after entering my password (just like you). Removing and re-installing, purging... nothing helped.

I never was able to diagnose the problem and eventually I did a format and clean install of beta 1, and never did see the problem occur again.

Wish I had a solution for you.. other than a clean install....

---

### Post by joeturtle on 2011-10-15
Thank you, effenberg0x0!
That solution worked perfectly!

---

### Post by jimk9 on 2011-11-18
@effenberg0x0, Thanks!  That gave me the crucial hint.  It's not just screen reader.  In my case it was the onscreen keyboard.  If I have that selected on in Universal Access then Synaptic crashes.  I can however start onboard using a launcher and Synaptic is fine with that.


> **effenberg0x0 said:**
> Please try this workaround:

[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/839219/comments/16](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/839219/comments/16)


Report back. 

Effenberg

---

### Post by Brokenbiker on 2011-12-18
> **effenberg0x0 said:**
> Please try this workaround:

[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/839219/comments/16](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/839219/comments/16)


Report back. 

Effenberg


Worked even though my sceen reader was all ready off. I just cycled it. Thank you much.

---

### Post by bmcm387 on 2012-01-07
[SIZE=2]could you please say what is in that web page ([https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/839219/comments/16](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/839219/comments/16)) because i can't open it and my browser gives me error when i try to open this link.                     :confused:
[/SIZE]

---

### Post by Neobuntu on 2012-01-18
The KDE screen reader was running for me, in Gnome 3.x shell. Once I quit that, Synaptic finally ran! Just FYI.

Thanks for the lead.

---

### Post by jettjunker on 2012-01-30
bmcm387, the link just says to toggle the screen reader on & off again (System Settings->Universal Access->Screen Reader).

That didn't work for me, but fortunately running "sudo apt-get update && sudo apt-get upgrade" did... even though it was only suggested as a diagnostic device.

---

### Post by youngunix on 2012-02-17
> **effenberg0x0 said:**
> Please try this workaround:

[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/839219/comments/16](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/839219/comments/16)


Report back. 

Effenberg

I've had the same issue on Ubuntu 11.10 and try this method beside others and none worked, until I tried "sudo apt-get autoremove". 
To anyone that's having the same issue, try every possible method or solution, "clean install" should be your last hope.

---

### Post by John Coulthard on 2012-04-26
The solution/link from effenberg0x0 worked fine for me. I triggered this by trying the screen reader out of curiousity a few weeks ago.

---

### Post by BlueAZ on 2012-06-11
> **effenberg0x0 said:**
> Please try this workaround:

[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/839219/comments/16](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/839219/comments/16)


Report back. 

Effenberg

Many Thanks!!  I've been struggling w/ this problem.  I just opened System Settings, went to Accessibility, turned Screen Reader on and back off.  Now Synaptic works!! ):P

---

