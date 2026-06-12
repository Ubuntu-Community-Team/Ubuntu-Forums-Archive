---
title: "No e-mail addresses in kmail"
date: 2010-05-04
forum: General Help
---

### Post by Orval on 2010-05-04
After reinstalling with Kubuntu 10.04 my e-mail addresses stored in Kontact don't show up in the list of e-mail addresses when choosing addresses in a new e-mail. When I open my addressbook I can see all addresses. Is there a way to fix this?

---

### Post by aletroux on 2010-05-05
Same problem here. I can however pin it down a bit more accurately. This happened when I created a "Personal Contacts" list with akonadi, and migrated my contacts from .kde/share/apps/kabc/stdvcf/ to .local/share/contacts/ .

I also have the problem that when I edit contacts, the changes don't appear in the kaddressbook window.

---

### Post by aletroux on 2010-05-06
I've managed to fix the problem by using the instructions [here]("http://userbase.kde.org/KAddressBook#Enabling_Resources") to enable my akonadi addressbook resource. My solution was to add the "akonadi-resource Personal" by hand, and then set it as standard.

---

