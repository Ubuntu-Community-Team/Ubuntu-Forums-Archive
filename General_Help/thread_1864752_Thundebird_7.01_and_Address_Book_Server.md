---
title: "Thundebird 7.01 and Address Book Server"
date: 2011-10-19
forum: General Help
---

### Post by pmatos on 2011-10-19
Hi all,

As soon as I upgraded to oneiric, my thunderbird upon startup presents me with the very annoying dialog "Adress Book Server Authentication Required". I don't even know which server thunderbird means. And each time I write something in, he asks again (probably he thinks the authentication is wrong).

How can I disable this thing? Might have something to do with LDAP but I have no idea how I go about disabling it.

---

### Post by andorko on 2011-10-20
I received the same error. I keep getting prompted to enter a new password for the LDAP connection to our MS Exchange server. Putting the correct password does no good, Thunderbird just prompts again. Entering an incorrect password shows up in the security log on the MS Exchange server.

It appears that the problem is a new "EDS Contact Integration" extension for Thunderbird. Disabling this plugin did the trick for me.

[http://mozillalabs.com/messaging/eds-contacts-integration-for-thunderbird/](http://mozillalabs.com/messaging/eds-contacts-integration-for-thunderbird/)

---

### Post by pmatos on 2011-10-21
> **andorko said:**
> I received the same error. I keep getting prompted to enter a new password for the LDAP connection to our MS Exchange server. Putting the correct password does no good, Thunderbird just prompts again. Entering an incorrect password shows up in the security log on the MS Exchange server.

It appears that the problem is a new "EDS Contact Integration" extension for Thunderbird. Disabling this plugin did the trick for me.

[http://mozillalabs.com/messaging/eds-contacts-integration-for-thunderbird/](http://mozillalabs.com/messaging/eds-contacts-integration-for-thunderbird/)

Thanks, you're right. That seems to do it.

---

