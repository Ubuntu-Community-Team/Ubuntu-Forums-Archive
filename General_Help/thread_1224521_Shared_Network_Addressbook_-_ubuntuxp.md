---
title: "Shared Network Addressbook - ubuntu/xp"
date: 2009-07-27
forum: General Help
---

### Post by frone on 2009-07-27
Been looking for the best way to get a three CPU network with one Jaunty and two xp machines sharing and updating an address book.  Have looked through a lot of options. LDAP almost looked like a great solution until finding that updating would be an issue.  I'm curious if anyone has a better solution.  I currently am deploying Thunderbird, but am not married to it - as even a separate address book application would be an acceptable solution.  If it helps, the xp machines are using outlook for e-mail currently - but any app that would let these three machines share and update an address book over the network would score the points.

I figure a plan 'B' might be to get the three address books doing a nightly sync - which would likely be fine as well.  Just curious if anyone has found and implemented a good solution for this...

Thanks!!!

---

### Post by t4thfavor on 2009-07-27
Yep, its called exchange.... OK, all jokes aside, an IMAP server of some kind should be able to do shared calendaring, and as a bonus you may even get email services out of it.


[http://ubuntuforums.org/archive/index.php/t-1074352.html](http://ubuntuforums.org/archive/index.php/t-1074352.html)

---

### Post by frone on 2009-07-27
Thanks for the quick reply.  I agree - Exchange would be a nice solution, but the guys just can't afford it.  I looked over all of the IMAP options and they really are offering some nice options (we've wanted to implement shared calendering down the road), but I keep finding the one doesn't allow for Thunderbird updates of the main address book (OpenExchange) or something else keeping me from my main goal.  I'm still looking at the Citadel, which might do what I want - but I think I might be looking for something a bit less 'heavy'.

I'm hoping there has to be something between 'full-blown commercial server' and shared notepad/vi text file...

Thanks again...

---

