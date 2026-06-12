---
title: "Problem with Nokia E-70 phone synchronization with Evolution"
date: 2010-04-19
forum: General Help
---

### Post by Ruben Iskandarjan on 2010-04-19
Hello,
 

 There is a bug while trying to synchronize a Nokia E-70 phone with Evolution program.
 

 I have done everything as described here: [https://help.ubuntu.com/community/NokiaEvolutionSyncing/Opensync](https://help.ubuntu.com/community/NokiaEvolutionSyncing/Opensync),
 but an error returns:
 

 supercat@supercat:~$ msynctool --sync nokia-evo 
 Synchronizing group "nokia-evo"  
 Member 1 of type evo2-sync just connected 
 Member 2 of type syncml-obex-client had an error while connecting: Link Error: 0x0 
 Member 1 of type evo2-sync just disconnected 
 All clients have disconnected 
 The sync failed: Unable to connect one of the members 
 Error while synchronizing: Unable to connect one of the members 
 supercat@supercat:~$  
 

 

 I have noticed that my phone dispalys «Trying to connect» message, but this procedure does not end up correctly and an error returns.


The configuration file is below:


<?xml version="1.0"?>
<config>
  <!-- (Only for bluetooth) The bluetooth address if the bluetooth mode is selected -->
  <bluetooth_address></bluetooth_address>
  
  <!-- (Only for bluetooth) The bluetooth channel to use. `sdptool browse $MAC` to search for the correct channel -->
  <bluetooth_channel></bluetooth_channel>
  
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
  <type>5</type>
  
  <!-- If wbxml is enabled, defines wether the wbxml should use string tables -->
  <usestringtable>1</usestringtable>
  
  <!-- Never send ADD command, but send REPLACE (not needed normally) -->
  <onlyreplace>0</onlyreplace>

  <!-- Workaround around for mobile phones which only use local timestamps and _no_ UTC timestamps! -->
  <onlyLocaltime>0</onlyLocaltime>
  
  <!-- Sets the maximum allowed size in bytes of incoming messages (some device need this option set). Example: 10000 -->
  <recvLimit>10000</recvLimit>
  
  <maxObjSize>10000</maxObjSize>
  
  <!-- The name of the contacts db. Must be the same as the phones sends -->
  <contact_db>Contacts</contact_db>
  
  <!-- The name of the calendar db. Must be the same as the phones sends -->
  <calendar_db>Calendar</calendar_db>
  
  <!-- The name of the note db. Must be the same as the phones sends -->
  <note_db>Notes</note_db>
</config>


The /etc/udev/rules.d/40-nokia-mobiles.rules file is below:



BUS=="usb", SYSFS{idVendor}=="0421", SYSFS{idProduct}=="*", MODE="0660", GROUP="dialout"
# This might work if the above doesn't :-(
# SUBSYSTEM=="usb", ATTR{idVendor}=="0421", ATTR{idProduct}=="*", MODE="0660", GROUP="dialout"

---

