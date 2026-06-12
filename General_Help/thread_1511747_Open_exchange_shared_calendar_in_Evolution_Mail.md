---
title: "Open exchange shared calendar in Evolution Mail"
date: 2010-06-17
forum: General Help
---

### Post by RD1945 on 2010-06-17
Hello,

Can someone please help me with this problem?

I would really like to know how to add an extra shared exchange calendar to my account in Evolution.

Evolution adds my own calendar just fine but I don't know how to add the extra one.

I know that in Outlook you can select "Add shared calendar" but I can't find this option in Evolution.

---

### Post by jonaustin on 2010-10-06
Was just looking into this myself.
There is a menu item - File -> Subscribe to Other user's calendar.

However it always gives a "Generic Error".

From looking through forum and mailing list post (from ~2006 to now) -- its apparently _never_ worked -- for anyone far as I can tell.

---

### Post by jonaustin on 2010-10-06
Note: to be clear - this manual solution has nothing to do with Evolution.

Found a manual way to see a shared calendar -- using OWA -- e.g. Web Outlook.

from this page: [http://www.helpdesk.ilstu.edu/kb/index.phtml?kbid=1260](http://www.helpdesk.ilstu.edu/kb/index.phtml?kbid=1260)

basically you just add this to the end of the OWA root link.
<exchange_username>/calendar

So for example:
<exchange_username> = jonaustin
<OWA_URL>           = email.mycompany.com/exchange/

to view my shared calendar:
email.mycompany.com/exchange/jonaustin/calendar

hacky, but it works..

---

### Post by jonaustin on 2010-10-06
This is actually working out better than if it worked in evolution (at least for viewing).

I just added a firefox quick/keyword search bookmark in the form from the previous post.
email.mycompany.com/exchange/%s/calendar

So now if I want to see the shared calendar for username 'jdoe', i just type:
sc jdoe

into firefox and bam, instant view of his shared calendar.

---

### Post by absentcrisis on 2011-09-29
I am also looking for a solution like this. However I'd like mine to open in evolution, because I have to add meetings to the calendars for resources such video conference equipment. Anyone know of a solution?

Thank you,

---

