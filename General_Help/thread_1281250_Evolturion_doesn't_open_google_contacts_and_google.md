---
title: "Evolturion doesn't open google contacts and google calendar"
date: 2009-10-03
forum: General Help
---

### Post by Qwerty_ls on 2009-10-03
Hi to everybody,
I'm a newbie and a no native English speaker so sorry for my errors.
I'm using ubuntu 9.04 with evolution 2.26.1 set up for my google account.
I used to sync evolution with google mail, google contacts and google calendar but after a failed sync between evolution and multisync opening contacts and calendar has become impossible. Every time I try to open them I have to type my password and after this a window appears with the following error:

Error loading address book.

This address book cannot be opened.  This either means that an incorrect URI was entered, or the server is unreachable.

Detailed error message: Other error

This is the debug file:

** (evolution:7352): DEBUG: mailto URL command: evolution %s
** (evolution:7352): DEBUG: mailto URL program: evolution

(evolution:7352): libecal-WARNING **: e-cal.c:320: Unexpected response
** (evolution:7352): DEBUG: EI: SHELL STARTUP
e-data-server-ui-Message: Unable to find password(s) in keyring (Keyring reports: No matching results)
e-data-server-ui-Message: Key file does not have group 'Passwords-google'
e-data-server-ui-Message: Unable to find password(s) in keyring (Keyring reports: No matching results)
e-data-server-ui-Message: Key file does not have group 'Passwords-google'

(evolution:7352): e-data-server-ui-WARNING **: Unable to find password(s) in keyring (Keyring reports: No matching results)

(evolution:7352): calendar-gui-WARNING **: Unable to load the calendar Authentication required

I've searched through several internet pages but I've not found something about it.. :(

Please help me!!

Thank you in advance!!

---

### Post by akakingess on 2009-10-03
Sorry, hate to take it off of subject, but since I don't use Evolution, I wouldn't be able to help, but have you tried to install Thunderbird and do the same?  If it can do it, then we know the problem is with Evolution, but at that point maybe you can just export what you need from Thunderbird and into Evolution and be alright. Also, Thunderbird has a seperate/sister app for calendar called Sunbird, all of these are Mozilla projects (except Evolution of course.)

---

### Post by wojnicki on 2009-10-03
Hi!

I've got the same problem with Evolution now. It used to work (a couple days ago) as a charm. It stopped now. I guess Google changed sth in the communication protocol. 

I suspect that Evolution (It's just my speculation) uses CalDAV access to the Google calendar, and presumably the contacts. It seems that this access method has been changed or disabled by Google. I tried to follow the instructions at Google to get to the CalDAV ([http://www.google.com/support/calendar/bin/answer.py?answer=99358#sunbird](http://www.google.com/support/calendar/bin/answer.py?answer=99358#sunbird)) but it returns the http error 404 - not found.

I also tried the Thunderbird plugin (I guess it's called Google contacts) - it works fine - but it might actually use the Google API instead of DAV - I'm not sure though.

I guess we just need to wait for Google to fix it...

---

### Post by akakingess on 2009-10-03
At least for contacts, you should be able to export from Thunderbird and into Evolution for now, though, right? Unless you choose to stick with Thunderbird (my personal preference :)

---

### Post by Qwerty_ls on 2009-10-03
thanks for your answer!!!
however I'v tried to set a caldav calendar and it works.
I don't think that this malfunction is not related with the google server but with something in my laptop..
I've found this thread [https://bugs.launchpad.net/evolution-data-server/+bug/107974](https://bugs.launchpad.net/evolution-data-server/+bug/107974) but can't understand if they've found a way to fix it!!
could somebody translate it in a simplier way???

---

### Post by rw2308 on 2009-10-06
Have you seen the following thread concerning problems with password stored in keyring?  This may sort your problem.

[http://ubuntuforums.org/showthread.php?t=1107244](http://ubuntuforums.org/showthread.php?t=1107244)

---

### Post by kevinbeard on 2009-10-06
> **rw2308 said:**
> Have you seen the following thread concerning problems with password stored in keyring?  This may sort your problem.

[http://ubuntuforums.org/showthread.php?t=1107244](http://ubuntuforums.org/showthread.php?t=1107244)

I have the same issue.

Delete the password in the keyring fixed the contacts syncing but I still can't sync my calendar

---

### Post by wojnicki on 2009-10-06
I started working! I guess Google fixed sth. It works again without any changes in the evolution config.

---

