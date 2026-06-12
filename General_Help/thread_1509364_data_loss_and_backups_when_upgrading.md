---
title: "data loss and backups when upgrading"
date: 2010-06-14
forum: General Help
---

### Post by surrealillusions on 2010-06-14
Hi all,

I installed Ubuntu 10.04 on the laptop and it looks pretty good. I currently run 9.10 on the main desktop and would like to upgrade to 10.04, by pressing "upgrade" in the update manager, but I have some questions before I do, namely about data loss.

If I upgrade, will stuff like Thunderbird keep my emails, FF keep its profile (cookies, bookmarks, addons etc..), the documents keep all the documents, I have an apache server installed with a few websites - will they still be there after an upgrade? I also have a virtual machine with windoze on, what about all the stuff in there and VMware itself?

Or, will I need to back everything up onto an external hard drive (not sure how to backup Thunderbird and FF), and then reinstall everything, and transfer all the documents, websites etc.. back over again??

Is there anything else I should be concerned about?

Thanks
:)

---

### Post by Ryan Dwyer on 2010-06-14
All the stuff you mentioned should be fine. The worst case scenario is that your machine will not boot after the upgrade, however in this case you will still be able to access your data if you boot from a live CD.

Just do it.

EDIT: Actually, make sure you have a live CD (karmic/9.10) or later before you do.

---

### Post by bruno9779 on 2010-06-14
All your personal data and settings is in your /home folder.

It is a very very good practice to have /home on a separate partition, so If anything goes wrong with the OS your data is safe on a different partition.

I have just upgraded 2 machines from 9.10 to 10.04, one went well, the other one didn't. Since my /home was separate, I have just popped in the live CD and selected manually the patitions.
Here I have checked that "format partition" was NOT ticked on /home, and off you go. Reinstalled in a flash.

NOTE: while all your data and config will be restored, you'll have to reinstall all your programs. Most of them will use your config files, and will look just as you left them before reinstalling.

Here goes a great tutorial to move home

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by surrealillusions on 2010-06-14
Ah, brilliant.

Will makeup backups anyway of the data as much as I can (as much as I love technology, I dont trust it 100%).

Thanks

:)

---

