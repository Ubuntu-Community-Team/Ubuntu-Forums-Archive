---
title: "msynctool: sync Evolution-Nokia E65 fails with ERROR 415 - unable to commit change"
date: 2010-06-15
forum: General Help
---

### Post by dona.net on 2010-06-15
I'm trying to sync Evolution with a Nokia E65 over bluetooth using msynctool. I'm on Ubuntu 10.04 on a 64bit pc.

Packages used (I had to manually install some, as opensync-plugin-syncml isn't in repository now):
[LIST]
[*]opensync-plugin-evolution 0.22-2ubuntu2
[*]opensync-plugin-syncml 0.22-2
[*]multisync-tools 0.92.0~svn355-2
[*]libopensync0 0.22-4
[*]libsoup2.2-8 2.2.105-4ubuntu1
[*]evolution 2.28.3-0ubuntu9
[/LIST]

Here the trace containing the error when trying do sync:

```
$ msynctool --sync nokia
Synchronizing group "nokia" 
The previous synchronization was unclean. Slow-syncing
Member 1 of type evo2-sync just connected
received contact dsession
Member 2 of type syncml-obex-client just connected
All clients connected or error
Received an entry pas-id-4C16B82200000002 with data of size 8 from member 1 (evo2-sync). Changetype ADDED
Member 1 of type evo2-sync just sent all changes
Received an reply to our Alert
Going to receive 0 changes
Member 2 of type syncml-obex-client just sent all changes
All clients sent changes or error
All conflicts have been reported
Member 1 of type evo2-sync committed all changes.
Received an reply to our sync
Error writing entry pas-id-4C16B82200000002 to member 2 (syncml-obex-client): Unable to commit change. Error 415
Mapping Write Error: Unable to commit change. Error 415
Member 2 of type syncml-obex-client committed all changes.
All clients have written
Member 1 of type evo2-sync just disconnected
Member 2 of type syncml-obex-client just disconnected
All clients have disconnected
The sync failed: Unable to write one or more objects
Error while synchronizing: Unable to write one or more objects
```


Here my syncml-obex-client configuration:

```
<?xml version="1.0"?>
<config>
  <!-- (Only for bluetooth) The bluetooth address if the bluetooth mode is selected -->
  <bluetooth_address>XX:XX:.......</bluetooth_address>
  
  <!-- (Only for bluetooth) The bluetooth channel to use. `sdptool browse $MAC` to search for the correct channel -->
  <bluetooth_channel>10</bluetooth_channel>
  
  <!-- (Only for USB) The usb interface number of the SYNCML-SYNC target. use syncml-obex-client -u (you will need access to the USB raw device) to find it. -->
  <interface>0</interface>
  
  <!-- The string that the plugin will use to identify itself. Some devices need a special string here. -->
  <identifier>PC Suite</identifier>
  
  <!-- The syncml version to use: 0 for 1.0, 1 for 1.1 and 2 for 1.2 -->
  <version>1</version>
  
  <!-- if the plugin should use wbxml -->
  <wbxml>1</wbxml>
  
  <!-- The username to use. Leave empty to not require a username -->
  <username></username>
  
  <!-- the password for the username -->
  <password></password>
  
  <!-- sets the connection type to use. 5 means obex over usb, 2 means obex over bluetooth -->
  <type>2</type>
  
  <!-- If wbxml is enabled, defines wether the wbxml should use string tables -->
  <usestringtable>1</usestringtable>
  
  <!-- Never send ADD command, but send REPLACE (not needed normally) -->
  <onlyreplace>0</onlyreplace>

  <!-- Workaround around for mobile phones which only use local timestamps and _no_ UTC timestamps! -->
  <onlyLocaltime>1</onlyLocaltime>
  
  <!-- Sets the maximum allowed size in bytes of incoming messages (some device need this option set). Example: 10000 -->
  <recvLimit>0</recvLimit>
  
  <maxObjSize>0</maxObjSize>
  
  <!-- The name of the contacts db. Must be the same as the phones sends -->
  <contact_db>Contacts</contact_db>
  
  <!-- The name of the calendar db. Must be the same as the phones sends -->
  <calendar_db>Calendar</calendar_db>
  
  <!-- The name of the note db. Must be the same as the phones sends -->
  <note_db>Notes</note_db>
</config>
```


I'm testing with one contact only. And I've disable calendar and notes sync for isolating the problem. The sync nokia->evolution works, but the sync evolution->nokia gives error 415, and no updates are seen on Nokia.

Please, why it happens and how to fix it? I've googled a lot, but no solution found... Thank you!

---

### Post by mfin on 2010-06-19
This is exactly the same problem I have encountered here.

---

