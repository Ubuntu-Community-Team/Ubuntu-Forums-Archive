---
title: "Evolution message filter issues"
date: 2010-05-21
forum: General Help
---

### Post by David Battley on 2010-05-21
Dear all,

I have had a search for this problem, but have not found a match: undoubtedly it is so straightforward that no-one has needed to ask it before:

I have two accounts in Evolution, work and gmail.  I would like my work email (which I check via IMAP) to be copied locally as it comes in so that I can file it properly, but also kept on the server so that I can access through my laptop.

I have set a message filter which does the following:
```

IF
status   is not   read
THEN
set status   read
copy to folder   Inbox
Stop processing

```

The filter works (if I apply manually then it goes) AND I have set the preferences to apply filters automatically, but no joy when a new email arrives.

Any ideas?

---

### Post by dcstar on 2010-05-21
> **David Battley said:**
> Dear all,

I have had a search for this problem, but have not found a match: undoubtedly it is so straightforward that no-one has needed to ask it before:

I have two accounts in Evolution, work and gmail.  I would like my work email (which I check via IMAP) to be copied locally as it comes in so that I can file it properly, but also kept on the server so that I can access through my laptop.

I have set a message filter which does the following:
```

IF
status   is not   read
THEN
set status   read
copy to folder   Inbox
Stop processing

```

The filter works (if I apply manually then it goes) AND I have set the preferences to apply filters automatically, but no joy when a new email arrives.

Any ideas?

Did you set the IMAP account to process filters?

---

### Post by David Battley on 2010-05-21
If you mean edit -> prefs -> #account -> apply filters on this server, then the answer is yes.

Is there a lag on filters being applied, or should they apply immediately?  Perhaps I am just being impatient...

---

### Post by dcstar on 2010-05-22
> **David Battley said:**
> If you mean edit -> prefs -> #account -> apply filters on this server, then the answer is yes.

Is there a lag on filters being applied, or should they apply immediately?  Perhaps I am just being impatient...

No you are not, it seems this is an old bug with Evolution systems using profiles upgraded along the way:

[https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/215541](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/215541)

Feel free to add yourself to the list of affected users.....

Addendum:

It actually does work - **after** you close Evolution and restart it!

I changed the IMAP "Apply filters to new messages" setting, but the change only takes effect after you restart the Evolution client.

---

### Post by David Battley on 2010-05-24
Thanks very much - that looks like it.  I'll look into adding myself to the bug report.

---

