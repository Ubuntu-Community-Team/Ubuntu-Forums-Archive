---
title: "How do I tell Update Manager to bugger off?"
date: 2011-11-05
forum: General Help
---

### Post by CommuneOfLoon on 2011-11-05
I'm using Ubuntu 10.04. I don't have Empathy installed, but Update Manager keeps prompting me to download security updates for it. I've unchecked and closed, but every time I turn on my computer it pops up. Any idea how to permanently tell it I don't want to download those updates? Thanks.

---

### Post by hwttdz on 2011-11-05
It seems like you should be able to edit your session startup commands and disable update-notifier or

gconftool -s --type bool /apps/update-notifier/auto_launch false

or in gconf-editor browse to apps->update-notifier and uncheck auto_launch.

---

### Post by ubudog on 2011-11-05
Go to System>Administration>Software Sources and click on the Updates tab. 

;)

---

