---
title: "Evolution does not sync tasks"
date: 2009-08-19
forum: General Help
---

### Post by acrocephalus on 2009-08-19
Hello,
I've just set up the synchronization with my Samsung Omnia and Ubuntu
Evolution. It syncs well the contacts and calendar, however, it does not
sync the tasks. This is the message I get when I run

```
msynctool --sync synce-sync

Synchronizing group "synce-sync" 
DEBUG:SynCE:Connect() called
Member 1 of type synce-opensync-plugin just connected
Member 2 of type evo2-sync just connected
All clients connected or error
DEBUG:SynCE:get_changeinfo() called
INFO:SynCE:initiating device synchronization
INFO:SynCE:waiting for engine to complete sync
Member 2 of type evo2-sync just sent all changes
INFO:SynCE:device synchronization complete
DEBUG:SynCE:requesting remote changes
DEBUG:SynCE:got 3 changesets
DEBUG:SynCE:no changes for item type 0
DEBUG:SynCE:no changes for item type 1
DEBUG:SynCE:no changes for item type 7
DEBUG:SynCE:reporting success
Member 1 of type synce-opensync-plugin just sent all changes
All clients sent changes or error
Member 2 of type evo2-sync committed all changes.
Member 1 of type synce-opensync-plugin committed all changes.
All clients have written
DEBUG:SynCE:sync_done() called
INFO:SynCE:initiating device synchronization
INFO:SynCE:waiting for engine to complete sync
Member 2 of type evo2-sync just disconnected
INFO:SynCE:device synchronization complete
DEBUG:SynCE:disconnect() called
Member 1 of type synce-opensync-plugin just disconnected
All clients have disconnected
The sync was successful
DEBUG:SynCE:finalize() called
```

This is the result of calling

```
synce-list-partnerships

AVAILABLE DEVICE PARTNERSHIPS
Index   Name    Device          Host         SyncItems
-----   ----    ------          ----         ---------

0	Acrocephalus	SGH-i900	acrocephalus-linux	[Calendar Tasks Contacts ]
```

Any idea on how to solve this?
Best,

Dani

---

### Post by coqboricua on 2010-06-03
Hi there, I am just curious but how on earth did you get your samsung Omnia to sync with ubuntu? what guideline did you use? I have been trying to get this to work for a long time and for some reason I get this....
Synchronizing group "Sync" 
The previous synchronization was unclean. Slow-syncing
DEBUG:SynCE:Connect() called
Member 2 of type synce-opensync-plugin just connected
Member 1 of type evo2-sync just connected
All clients connected or error
DEBUG:SynCE:get_changeinfo() called
DEBUG:SynCE:slow sync requested for Contacts
DEBUG:SynCE:slow sync requested for Calendar
DEBUG:SynCE:slow sync requested for Tasks
INFO:SynCE:initiating device synchronization
INFO:SynCE:waiting for engine to complete sync
Received an entry pas-id-4BFC169E00000000 with data of size 4 from member 1 (evo2-sync). Changetype ADDED
Member 1 of type evo2-sync just sent all changes
INFO:SynCE:device synchronization complete
INFO:SynCE:initiating prefill
INFO:SynCE:prefill complete
DEBUG:SynCE:requesting remote changes
DEBUG:SynCE:got 3 changesets
DEBUG:SynCE:processing changes for 3 items of item type 0
Traceback (most recent call last):
  File "/usr/lib/opensync/python-plugins/synce-opensync-plugin-2x.py", line 174, in get_changeinfo
    change.uid = array.array('B',guid).tostring() 
  File "/usr/lib/pymodules/python2.6/opensync.py", line 192, in set_uid
    def set_uid(self, *args): return _opensync.OSyncChange_set_uid(self, *args)
TypeError: in method 'OSyncChange_set_uid', argument 1 of type 'OSyncChange *'
Member 2 of type synce-opensync-plugin had an error while getting changes: Error during get_changeinfo() method
DEBUG:SynCE:disconnect() called
Member 2 of type synce-opensync-plugin just disconnected
Member 1 of type evo2-sync just disconnected
All clients have disconnected
The sync failed: Unable to read from one of the members
DEBUG:SynCE:finalize() called
Error while synchronizing: Unable to read from one of the members

---

