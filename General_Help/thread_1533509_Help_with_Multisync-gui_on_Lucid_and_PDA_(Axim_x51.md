---
title: "Help with Multisync-gui on Lucid and PDA (Axim x51v)"
date: 2010-07-18
forum: General Help
---

### Post by plasticspoon on 2010-07-18
Hi all

I've spent the weekend trying to get my Axim to talk to Evolution calendar and task list.
Using the synCE tray icon I've successfully set up a partnership on the Axim (which is running WM6). I've also got multisync-gui (multisynch0.90) up and running with the following plug-ins
[LIST]
[*]synce-opensync-plugin
[*]evo2-sync
[/LIST]

sync fails, saying that it cannot read from one of the members. Terminal output is below


```
tim@X1800:~$ multisync0.90
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
Member 1 of type evo2-sync just sent all changes
Traceback (most recent call last):
  File "/usr/lib/opensync/python-plugins/synce-opensync-plugin-2x.py", line 152, in get_changeinfo
    self._TriggerSync()
  File "/usr/lib/opensync/python-plugins/synce-opensync-plugin-2x.py", line 117, in _TriggerSync
    self.engine.Synchronize()
  File "/usr/lib/pymodules/python2.6/dbus/proxies.py", line 140, in __call__
    **keywords)
  File "/usr/lib/pymodules/python2.6/dbus/connection.py", line 620, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.synce.SyncEngine.Error.NoBoundPartnership: 
Member 2 of type synce-opensync-plugin had an error while getting changes: Error during get_changeinfo() method
DEBUG:SynCE:disconnect() called
Member 1 of type evo2-sync just disconnected
Member 2 of type synce-opensync-plugin just disconnected
All clients have disconnected
The sync failed: Unable to read from one of the members
DEBUG:SynCE:finalize() called
tim@X1800:~$
``` 

None of that means a great deal to me, but one thing I DID pick up on is that the partner ship I created in the PDA is not bound to the sync engine.

I feel I'm pretty close to getting this thing fixed, but I'm stumped. Any suggestions, or perhaps an entirely different method would be gratefully received.

---

### Post by plasticspoon on 2010-07-18
Progress update

I've added the synce PPA from launchpad and updated my packages.
Terminal output now reads as follows.



```
tim@X1800:~$ multisync0.90
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
Member 1 of type evo2-sync just sent all changes
INFO:SynCE:waiting for engine to complete sync
INFO:SynCE:device synchronization complete
INFO:SynCE:initiating prefill
INFO:SynCE:prefill complete
DEBUG:SynCE:requesting remote changes
DEBUG:SynCE:got 2 changesets
DEBUG:SynCE:processing changes for 2 items of item type 0
Traceback (most recent call last):
  File "/usr/lib/opensync/python-plugins/synce-opensync-plugin-2x.py", line 174, in get_changeinfo
    change.uid = array.array('B',guid).tostring() 
  File "/usr/lib/pymodules/python2.6/opensync.py", line 192, in set_uid
    def set_uid(self, *args): return _opensync.OSyncChange_set_uid(self, *args)
TypeError: in method 'OSyncChange_set_uid', argument 1 of type 'OSyncChange *'
Member 2 of type synce-opensync-plugin had an error while getting changes: Error during get_changeinfo() method
DEBUG:SynCE:disconnect() called
Member 1 of type evo2-sync just disconnected
Member 2 of type synce-opensync-plugin just disconnected
All clients have disconnected
The sync failed: Unable to read from one of the members
DEBUG:SynCE:finalize() called
tim@X1800:~$
``` 


I'm getting so close I can almost taste it :P

---

### Post by plasticspoon on 2010-07-26
Gosh, I seem to have this thread all to myself ;)

Anyway, here's a bit of a progress report...

Poking around the interwebs, I discovered that the file opensync.py (1.3.40) was broken. so I replaced it with version 1.3.39. 

The other problem I was having was correctly interpreting the GUI in Multisynch 0.90. When your adding members to a group, there's 5 tick boxes.
[LIST]
[*]contact
[*]todo
[*]data
[*]event
[*]note
[/LIST]

Well, I just assumed you ticked the boxes of the things you wanted to sync, so I ticked event and todo. Of course when you look at the window properly, you see it says, "Disable syncing of object type:" !!!!
So, I unchecked everything, did a sync, and Cowabunga Dude, it actually worked (almost)...
Several of my appointments and tasks dutifully migrated to my trusty PDA, but unfortunately not all :(

I have a recurrent event on Friday, and I just can't seem to sync that one to my PDA. Perhaps it's an Islamic PDA :D

I'll keep you posted

---

### Post by plasticspoon on 2010-07-27
Me again, apparently talking to myself :)

The recurrent appointment on Fridays keeps getting shunted off to Saturday. How weird is that?

---

### Post by rjovec on 2010-08-17
Hi plasticspoon,

I have been facing this problem since I have installed Ubuntu 10.04. Mixing what I have learned in differents forums I have found a solution that works:

It seems to be a problem of the opensync.py file. The latest version (0.40). In the Forums that I found the people were modifying this file:
  
You will have more information here: [http://www.opensync.org/ticket/1131](http://www.opensync.org/ticket/1131) 


But as I do not know anything about python, I found much more easy what is suggested in another forum: just moving to the previous file version, so I just changed my opensync.py (v0.40) by the opensync.py (v0.39). I am attaching the v0.39 file.

lf you want more details: [https://bugs.launchpad.net/ubuntu/+source/opensync/+bug/565137](https://bugs.launchpad.net/ubuntu/+source/opensync/+bug/565137) 

Good luck!!!


Roger

---

