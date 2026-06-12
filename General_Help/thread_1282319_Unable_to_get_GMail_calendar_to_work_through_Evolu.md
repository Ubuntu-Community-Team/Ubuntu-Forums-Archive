---
title: "Unable to get GMail calendar to work through Evolution"
date: 2009-10-04
forum: General Help
---

### Post by spmurphy01 on 2009-10-04
I have inserted my google username, selected the type as google and selected use ssl, but when I click Retrieve List, an error returns cannot read data from google server. connection terminated unexpectedly. The emails from gmail however are working fine.

Many Thanks
Stephen

---

### Post by fsz285 on 2009-10-04
I have a similar problem problem here, although for me, the calendar did work for some time now. google contacts stopped working as well.
Here's some dbug output from trying to refresh the contacts:

impl_GNOME_Evolution_Addressbook_Book_open (0x9335e90)
(evolution-data-server-2.24:8989): libebookbackendgoogle-DEBUG: e_book_backend_google_authenticate_user
(evolution-data-server-2.24:8989): libebookbackendgoogle-DEBUG: google_book_connect_to_google
(evolution-data-server-2.24:8989): libebookbackendgoogle-DEBUG: Authentication failed: Connecting to google failed due to 'Connection terminated unexpectedly' (HTTP code 7)
(evolution-data-server-2.24:8989): libebookbackendgoogle-DEBUG: e_book_backend_google_authenticate_user
(evolution-data-server-2.24:8989): libebookbackendgoogle-DEBUG: google_book_connect_to_google
(evolution-data-server-2.24:8989): libebookbackendgoogle-DEBUG: Authentication failed: Connecting to google failed due to 'Connection terminated unexpectedly' (HTTP code 7)

---

### Post by mattro200 on 2009-10-04
Same problem here. Had google calendar and contacts working fine until about a week ago. Tried to delete and re add the profile, no luck.

---

### Post by spmurphy01 on 2009-10-04
I have just tried the Contacts also and also does not work.

---

### Post by wojnicki on 2009-10-04
Same here. I don't know how to fix it. Perhaps Google changed sth...

---

### Post by spmurphy01 on 2009-10-05
Do we if its a GMail issue or a Evolution issue?
Is anyone's Evolution calendar working with GMail?

---

### Post by spmurphy01 on 2009-10-05
Hi People,

I have managed to get the calendar working changing the type from google to calDAV.

in the URL type in caldv://www.google.com/calendar/dav/user@domain.com/events/ 

username - type in username. [email]user@domain.com[/email]

you will see then in evolution at the left the calDAV entry, maximise to see you google calender.

Thanks
Steve

---

### Post by spmurphy01 on 2009-10-05
i forgot, also select SSL as usual.

---

### Post by nandelbosc on 2009-10-05
The same problem here! I think it's an ubuntu update problem... after upgrade to karmic on my system all work's well withous make changes.

In other computer (where i can't upgrade to karmic) the spmurphy01 solution works fine for calendar but not contacts! It's there a wey to solve this?! thank's!!

when i try to load contacts

---

### Post by spmurphy01 on 2009-10-05
was contacts working ok before?
I only installed Ubuntu a few days ago as newbe to linux so for me it has never worked as yet.

---

### Post by fsz285 on 2009-10-05
For me, contacts and calendars both worked fine until yesterday. I'm using ubuntu 8.10 and evolution 2.24 by the way, but the problem seems to be version independent

---

### Post by nandelbosc on 2009-10-05
> **fsz285 said:**
> For me, contacts and calendars both worked fine until yesterday. I'm using ubuntu 8.10 and evolution 2.24 by the way, but the problem seems to be version independent

The same!

Contacts and calendar worked fine until friday. I use ubuntu Jaunty 9.04 with evolution 2.26.1. After upgrade to karmic koala beta (yesterday), both works fine again with no modifications.

In another system (with ubuntu 9.04 and evolution 2.26.1 too) where for working reasons I can't update, I solve the problem with calendar using spmurphy01 hack...

> I have managed to get the calendar working changing the type from google to calDAV.

in the URL type in caldv://www.google.com/calendar/dav/user@domain.com/events/

username - type in username. [email]user@domain.com[/email]

you will see then in evolution at the left the calDAV entry, maximise to see you google calender.

but NO for contacts.

Any ideas?

---

### Post by fsz285 on 2009-10-06
[https://bugs.launchpad.net/evolution/+bug/385935](https://bugs.launchpad.net/evolution/+bug/385935)

the issue seems to have been fixed in karmic.

---

### Post by nandelbosc on 2009-10-06
thank's fsz285, but for the people who can't upgrade to karmic, is there a solution?

startin evolution in debug mode, every time I click on google contacts, can see this line in the debug output file...

```
ubuntu EABView at present does not support multiple writes on the "source" property.
```

any ideas?

---

### Post by fsz285 on 2009-10-06
i haven't found a solution yet (i also can't upgrade right now).
you can always try to install evolution-2.28 on intrepid, although chances are you'll probably rip the system apart while doing so...

maybe they'll fix the issue for evolution-2.24 as well.

---

### Post by wojnicki on 2009-10-06
It has just started working again - without any change of the evolution config.

---

### Post by m.mannes on 2009-10-06
Just start working today too. Without any config change. Seems it was a Google problem...

---

### Post by nandelbosc on 2009-10-06
> Just start working today too. Without any config change. Seems it was a Google problem... 

Here works too! As you, without any modifications!

Really strange, no? Why in Karmic all works ok? Evolution 2.28 predicts a google error? :popcorn: jeje

---

### Post by Eadster on 2009-10-06
I've had exactly the same problems. Today the calendar is working fine again but my contacts are still not working. Is this related, anyone having similar problems?

---

### Post by inchkape on 2009-10-07
> **Eadster said:**
> I've had exactly the same problems. Today the calendar is working fine again but my contacts are still not working. Is this related, anyone having similar problems?

Same here : Calendar now works fine, contacts still don't, even though both used to work. I guess google are changing things around for some reason - maybe just maintenance. I'll give it a little time to see f things improve.:P

---

### Post by thib on 2009-10-16
I get the same error here in karmic. It worked fine before...

Any idea on what I can do?


Thanks in advance

Bye

---

### Post by thib on 2009-10-16
Got it working back... Nothing done

---

