---
title: "Pidgin Annoyance"
date: 2009-09-03
forum: General Help
---

### Post by s3a on 2009-09-03
Every time pidgin launches, I always get two pop up windows saying "Buddy list synchronization issue in [email]myemailaddress@hotmail.com[/email] (MSN)." and tells me that it is not on the server list but every time I try to add by clicking "Yes," it makes the windows temporarily vanish for an undetermined amount of time then I see the same windows again and have to reclick "Yes."

How do I fix this?

Any help would greatly appreciated!
Thanks in advance!

---

### Post by jaxxstorm on 2009-09-03
> **s3a said:**
> Every time pidgin launches, I always get two pop up windows saying "Buddy list synchronization issue in [email]myemailaddress@hotmail.com[/email] (MSN)." and tells me that it is not on the server list but every time I try to add by clicking "Yes," it makes the windows temporarily vanish for an undetermined amount of time then I see the same windows again and have to reclick "Yes."

How do I fix this?

Any help would greatly appreciated!
Thanks in advance!

If you remove the file ~/.purple/blist.xml it'll probably fix it. Make sure you make a backup first though

```

sudo mv ~/.purple/blist.xml ~/.purple/blist.xml.bak

```

Will do it in one go.

EDIT: This will remove your buddy list, you'll have to set it up again, but the annoyance will stop once its syncronised.

---

### Post by s3a on 2009-09-03
Are you saying I would have to re-add hundreds of people with that method?!

---

### Post by falconindy on 2009-09-03
> **s3a said:**
> Are you saying I would have to re-add hundreds of people with that method?!
Buddy lists themselves are always stored server side. Deleting that xml file isn't going to remove your list of contacts. It will, however, destroy the grouping you have setup, as well as any aliases and buddy list based preferences.

This is why you should make a backup, and not just delete it.

---

