---
title: "Accessing Old Profiles In Thunderbird"
date: 2009-08-04
forum: General Help
---

### Post by EmyrB on 2009-08-04
Hi All,

A friend of mine has a couple of old Thunderbird profiles (don't ask me why, he's upgraded Windows a few times and setup different profiles each time) and now he's on Ubuntu with, you've guessed it, a new Thunderbird profile.

Anyway, in one of the old profiles he's got an e-mail from one of his clients that he needs to get it quite quick. What I want to know is there anyway I can get to those e-mails without destroying his current profile? or can I simply import the e-mail from the profiles so they show up in his current profile?

Cheers in advance

EmyrB

---

### Post by nikhilk on 2009-08-04
I have never tried [this]("http://kb.mozillazine.org/Importing_and_exporting_your_mail#Migrating_messages_using_a_mail_server") but it might help.

---

### Post by kellemes on 2009-08-04
from terminal..
```
thunderbird -profilemanager
```

Now you can create a new profile by giving a name and pointing to the folder where the profile-data is..

---

### Post by EmyrB on 2009-08-08
Thanks nikhilk & kellemes for your replies.

I didn't fancy doing it the way your link said, but I got it to work using the thunderbird profilemanager and I managed to rescue his credibility :D

Cheers guys

EmyrB

---

