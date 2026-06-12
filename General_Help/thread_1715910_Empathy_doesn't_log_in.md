---
title: "Empathy doesn't log in"
date: 2011-03-27
forum: General Help
---

### Post by carega on 2011-03-27
Hello there!

I'm having trouble with Empathy logging in. It doesn't happen all the time, which is what makes it strange. Sometimes it works perfectly and other times it announces me there was a network error and I get something like this in the debug screen (debug = depurar?):

```
 mcd-DEBUG: 27/03/11 14:56:01.542798: mcd_account_changed_property: called: ConnectionErrorDetails
mcd-DEBUG: 27/03/11 14:56:01.542809: mcd_account_thaw_properties: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0
mcd-DEBUG: 27/03/11 14:56:01.542813: emit_property_changed: called
mcd-WARNING: 27/03/11 14:56:01.542628: request_connection_cb: RequestConnection failed: org.freedesktop.DBus.Python.KeyError: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.6/dist-packages/telepathy/server/connmgr.py", line 69, in RequestConnection
    conn = self._protos[proto](self, parameters)
  File "/usr/lib/python2.6/dist-packages/butterfly/connection.py", line 115, in __init__
    telepathy.server.Connection.__init__(self, 'msn', account, 'butterfly')
  File "/usr/lib/python2.6/dist-packages/telepathy/server/conn.py", line 82, in __init__
    _Connection.__init__(self, bus_name, object_path)
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 480, in __init__
    self.add_to_connection(conn, object_path)
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 571, in add_to_connection
    self._fallback)
KeyError: "Can't register the object-path handler for '/org/freedesktop/Telepathy/Connection/butterfly/msn/rega_5fcarlos_40hotmail_2ecom': there is already a handler"
mcd-DEBUG: 27/03/11 14:56:02.50944: account_reconnect: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0
mcd-DEBUG: 27/03/11 14:56:02.50962: _mcd_connection_release_tp_connection: 0x9a68d58
mcd-DEBUG: 27/03/11 14:56:02.50997: _mcd_account_set_connection_status: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0: 2 because 1
mcd-DEBUG: 27/03/11 14:56:02.51003: mcd_account_freeze_properties: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0
mcd-DEBUG: 27/03/11 14:56:02.51012: _mcd_account_set_connection_status: changing connection status reason from 2 to 1
mcd-DEBUG: 27/03/11 14:56:02.51023: mcd_account_changed_property: called: Connection
mcd-DEBUG: 27/03/11 14:56:02.51029: mcd_account_changed_property: First changed property
mcd-DEBUG: 27/03/11 14:56:02.51192: mcd_account_changed_property: called: ConnectionStatus
mcd-DEBUG: 27/03/11 14:56:02.51233: mcd_account_changed_property: called: ConnectionStatusReason
mcd-DEBUG: 27/03/11 14:56:02.51242: mcd_account_changed_property: called: ConnectionError
mcd-DEBUG: 27/03/11 14:56:02.51270: mcd_account_changed_property: called: ConnectionErrorDetails
mcd-DEBUG: 27/03/11 14:56:02.51289: mcd_account_thaw_properties: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0
mcd-DEBUG: 27/03/11 14:56:02.51295: emit_property_changed: called
mcd-DEBUG: 27/03/11 14:56:02.51543: _mcd_operation_abort: Operation abort received, aborting all children
mcd-DEBUG: 27/03/11 14:56:02.51554: on_connection_abort: called (0x9a68d58, account butterfly/msn/rega_5fcarlos_40hotmail_2ecom0)
mcd-DEBUG: 27/03/11 14:56:02.51585: _mcd_mission_set_parent: child = 0x9a68d58, parent = (nil)
mcd-DEBUG: 27/03/11 14:56:02.51600: _mcd_operation_remove_mission: removing mission: 0x9a68d58
mcd-DEBUG: 27/03/11 14:56:02.51613: _mcd_connection_dispose: called for object 0x9a68d58
mcd-DEBUG: 27/03/11 14:56:02.51620: _mcd_connection_release_tp_connection: 0x9a68d58
mcd-DEBUG: 27/03/11 14:56:02.51636: _mcd_operation_dispose: operation disposed
mcd-DEBUG: 27/03/11 14:56:02.51646: _mcd_mission_dispose: mission disposed 0x9a68d58
mcd-DEBUG: 27/03/11 14:56:02.51661: _mcd_mission_finalize: mission finalized 0x9a68d58
mcd-DEBUG: 27/03/11 14:56:02.51672: _mcd_account_dup_parameters: called
mcd-DEBUG: 27/03/11 14:56:02.51908: _mcd_mission_set_parent: child = 0x9a68cf0, parent = 0x9a73860
mcd-DEBUG: 27/03/11 14:56:02.51933: mcd_manager_create_connection: Created a connection 0x9a68cf0 for account: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0
mcd-DEBUG: 27/03/11 14:56:02.51940: _mcd_connection_connect: called for 0x9a68cf0, account butterfly/msn/rega_5fcarlos_40hotmail_2ecom0
mcd-DEBUG: 27/03/11 14:56:02.51949: _mcd_connection_connect_with_params: Trying connect account: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0
mcd-DEBUG: 27/03/11 14:56:02.51961: _mcd_account_set_connection_status: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0: 1 because 1
mcd-DEBUG: 27/03/11 14:56:02.51968: mcd_account_freeze_properties: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0
mcd-DEBUG: 27/03/11 14:56:02.51975: _mcd_account_set_connection_status: changing connection status from 2 to 1
mcd-DEBUG: 27/03/11 14:56:02.51983: mcd_account_changed_property: called: Connection
mcd-DEBUG: 27/03/11 14:56:02.51987: mcd_account_changed_property: First changed property
mcd-DEBUG: 27/03/11 14:56:02.52059: mcd_account_changed_property: called: ConnectionStatus
mcd-DEBUG: 27/03/11 14:56:02.52068: mcd_account_changed_property: called: ConnectionStatusReason
mcd-DEBUG: 27/03/11 14:56:02.52077: mcd_account_changed_property: called: ConnectionError
mcd-DEBUG: 27/03/11 14:56:02.52093: mcd_account_changed_property: called: ConnectionErrorDetails
mcd-DEBUG: 27/03/11 14:56:02.52109: mcd_account_thaw_properties: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0
mcd-DEBUG: 27/03/11 14:56:02.52114: emit_property_changed: called
mcd-DEBUG: 27/03/11 14:56:02.173207: _mcd_account_set_connection_status: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0: 2 because 2
mcd-DEBUG: 27/03/11 14:56:02.173213: mcd_account_freeze_properties: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0
mcd-DEBUG: 27/03/11 14:56:02.173218: _mcd_account_set_connection_status: changing connection status from 1 to 2
mcd-DEBUG: 27/03/11 14:56:02.173223: _mcd_account_set_connection_status: changing connection status reason from 1 to 2
mcd-DEBUG: 27/03/11 14:56:02.173228: mcd_account_changed_property: called: Connection
mcd-DEBUG: 27/03/11 14:56:02.173232: mcd_account_changed_property: First changed property
mcd-DEBUG: 27/03/11 14:56:02.173325: mcd_account_changed_property: called: ConnectionStatus
mcd-DEBUG: 27/03/11 14:56:02.173330: mcd_account_changed_property: called: ConnectionStatusReason
mcd-DEBUG: 27/03/11 14:56:02.173335: mcd_account_changed_property: called: ConnectionError
mcd-DEBUG: 27/03/11 14:56:02.173351: mcd_account_changed_property: called: ConnectionErrorDetails
mcd-DEBUG: 27/03/11 14:56:02.173360: mcd_account_thaw_properties: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0
mcd-DEBUG: 27/03/11 14:56:02.173363: emit_property_changed: called
mcd-WARNING: 27/03/11 14:56:02.173180: request_connection_cb: RequestConnection failed: org.freedesktop.DBus.Python.KeyError: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.6/dist-packages/telepathy/server/connmgr.py", line 69, in RequestConnection
    conn = self._protos[proto](self, parameters)
  File "/usr/lib/python2.6/dist-packages/butterfly/connection.py", line 115, in __init__
    telepathy.server.Connection.__init__(self, 'msn', account, 'butterfly')
  File "/usr/lib/python2.6/dist-packages/telepathy/server/conn.py", line 82, in __init__
    _Connection.__init__(self, bus_name, object_path)
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 480, in __init__
    self.add_to_connection(conn, object_path)
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 571, in add_to_connection
    self._fallback)
KeyError: "Can't register the object-path handler for '/org/freedesktop/Telepathy/Connection/butterfly/msn/rega_5fcarlos_40hotmail_2ecom': there is already a handler"
mcd-DEBUG: 27/03/11 14:56:02.535720: account_reconnect: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0
mcd-DEBUG: 27/03/11 14:56:02.535739: _mcd_connection_release_tp_connection: 0x9a68cf0
mcd-DEBUG: 27/03/11 14:56:02.535774: _mcd_account_set_connection_status: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0: 2 because 1
mcd-DEBUG: 27/03/11 14:56:02.535782: mcd_account_freeze_properties: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0
mcd-DEBUG: 27/03/11 14:56:02.535790: _mcd_account_set_connection_status: changing connection status reason from 2 to 1
mcd-DEBUG: 27/03/11 14:56:02.535801: mcd_account_changed_property: called: Connection
mcd-DEBUG: 27/03/11 14:56:02.535809: mcd_account_changed_property: First changed property
mcd-DEBUG: 27/03/11 14:56:02.535965: mcd_account_changed_property: called: ConnectionStatus
mcd-DEBUG: 27/03/11 14:56:02.535974: mcd_account_changed_property: called: ConnectionStatusReason
mcd-DEBUG: 27/03/11 14:56:02.535984: mcd_account_changed_property: called: ConnectionError
mcd-DEBUG: 27/03/11 14:56:02.536011: mcd_account_changed_property: called: ConnectionErrorDetails
mcd-DEBUG: 27/03/11 14:56:02.536030: mcd_account_thaw_properties: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0
mcd-DEBUG: 27/03/11 14:56:02.536036: emit_property_changed: called
mcd-DEBUG: 27/03/11 14:56:02.536286: _mcd_operation_abort: Operation abort received, aborting all children
mcd-DEBUG: 27/03/11 14:56:02.536297: on_connection_abort: called (0x9a68cf0, account butterfly/msn/rega_5fcarlos_40hotmail_2ecom0)
mcd-DEBUG: 27/03/11 14:56:02.536328: _mcd_mission_set_parent: child = 0x9a68cf0, parent = (nil)
mcd-DEBUG: 27/03/11 14:56:02.536341: _mcd_operation_remove_mission: removing mission: 0x9a68cf0
mcd-DEBUG: 27/03/11 14:56:02.536354: _mcd_connection_dispose: called for object 0x9a68cf0
mcd-DEBUG: 27/03/11 14:56:02.536361: _mcd_connection_release_tp_connection: 0x9a68cf0
mcd-DEBUG: 27/03/11 14:56:02.536376: _mcd_operation_dispose: operation disposed
mcd-DEBUG: 27/03/11 14:56:02.536386: _mcd_mission_dispose: mission disposed 0x9a68cf0
mcd-DEBUG: 27/03/11 14:56:02.536402: _mcd_mission_finalize: mission finalized 0x9a68cf0
mcd-DEBUG: 27/03/11 14:56:02.536413: _mcd_account_dup_parameters: called
mcd-DEBUG: 27/03/11 14:56:02.536645: _mcd_mission_set_parent: child = 0x9a68cf0, parent = 0x9a73860
mcd-DEBUG: 27/03/11 14:56:02.536670: mcd_manager_create_connection: Created a connection 0x9a68cf0 for account: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0
mcd-DEBUG: 27/03/11 14:56:02.536678: _mcd_connection_connect: called for 0x9a68cf0, account butterfly/msn/rega_5fcarlos_40hotmail_2ecom0
mcd-DEBUG: 27/03/11 14:56:02.536685: _mcd_connection_connect_with_params: Trying connect account: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0
mcd-DEBUG: 27/03/11 14:56:02.536698: _mcd_account_set_connection_status: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0: 1 because 1
mcd-DEBUG: 27/03/11 14:56:02.536704: mcd_account_freeze_properties: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0
mcd-DEBUG: 27/03/11 14:56:02.536710: _mcd_account_set_connection_status: changing connection status from 2 to 1
mcd-DEBUG: 27/03/11 14:56:02.536717: mcd_account_changed_property: called: Connection
mcd-DEBUG: 27/03/11 14:56:02.536722: mcd_account_changed_property: First changed property
mcd-DEBUG: 27/03/11 14:56:02.536793: mcd_account_changed_property: called: ConnectionStatus
mcd-DEBUG: 27/03/11 14:56:02.536802: mcd_account_changed_property: called: ConnectionStatusReason
mcd-DEBUG: 27/03/11 14:56:02.536809: mcd_account_changed_property: called: ConnectionError
mcd-DEBUG: 27/03/11 14:56:02.536825: mcd_account_changed_property: called: ConnectionErrorDetails
mcd-DEBUG: 27/03/11 14:56:02.536840: mcd_account_thaw_properties: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0
mcd-DEBUG: 27/03/11 14:56:02.536847: emit_property_changed: called
mcd-DEBUG: 27/03/11 14:56:02.659662: _mcd_account_set_connection_status: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0: 2 because 2
mcd-DEBUG: 27/03/11 14:56:02.659670: mcd_account_freeze_properties: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0
mcd-DEBUG: 27/03/11 14:56:02.659674: _mcd_account_set_connection_status: changing connection status from 1 to 2
mcd-DEBUG: 27/03/11 14:56:02.659677: _mcd_account_set_connection_status: changing connection status reason from 1 to 2
mcd-DEBUG: 27/03/11 14:56:02.659683: mcd_account_changed_property: called: Connection
mcd-DEBUG: 27/03/11 14:56:02.659687: mcd_account_changed_property: First changed property
mcd-DEBUG: 27/03/11 14:56:02.659778: mcd_account_changed_property: called: ConnectionStatus
mcd-DEBUG: 27/03/11 14:56:02.659782: mcd_account_changed_property: called: ConnectionStatusReason
mcd-DEBUG: 27/03/11 14:56:02.659787: mcd_account_changed_property: called: ConnectionError
mcd-DEBUG: 27/03/11 14:56:02.659804: mcd_account_changed_property: called: ConnectionErrorDetails
mcd-DEBUG: 27/03/11 14:56:02.659813: mcd_account_thaw_properties: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0
mcd-DEBUG: 27/03/11 14:56:02.659816: emit_property_changed: called
mcd-WARNING: 27/03/11 14:56:02.659636: request_connection_cb: RequestConnection failed: org.freedesktop.DBus.Python.KeyError: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.6/dist-packages/telepathy/server/connmgr.py", line 69, in RequestConnection
    conn = self._protos[proto](self, parameters)
  File "/usr/lib/python2.6/dist-packages/butterfly/connection.py", line 115, in __init__
    telepathy.server.Connection.__init__(self, 'msn', account, 'butterfly')
  File "/usr/lib/python2.6/dist-packages/telepathy/server/conn.py", line 82, in __init__
    _Connection.__init__(self, bus_name, object_path)
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 480, in __init__
    self.add_to_connection(conn, object_path)
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 571, in add_to_connection
    self._fallback)
KeyError: "Can't register the object-path handler for '/org/freedesktop/Telepathy/Connection/butterfly/msn/rega_5fcarlos_40hotmail_2ecom': there is already a handler"
mcd-DEBUG: 27/03/11 14:56:02.919893: account_reconnect: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0
mcd-DEBUG: 27/03/11 14:56:02.919912: _mcd_connection_release_tp_connection: 0x9a68cf0
mcd-DEBUG: 27/03/11 14:56:02.919945: _mcd_account_set_connection_status: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0: 2 because 1
mcd-DEBUG: 27/03/11 14:56:02.919953: mcd_account_freeze_properties: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0
mcd-DEBUG: 27/03/11 14:56:02.919961: _mcd_account_set_connection_status: changing connection status reason from 2 to 1
mcd-DEBUG: 27/03/11 14:56:02.919972: mcd_account_changed_property: called: Connection
mcd-DEBUG: 27/03/11 14:56:02.919980: mcd_account_changed_property: First changed property
mcd-DEBUG: 27/03/11 14:56:02.920131: mcd_account_changed_property: called: ConnectionStatus
mcd-DEBUG: 27/03/11 14:56:02.920140: mcd_account_changed_property: called: ConnectionStatusReason
mcd-DEBUG: 27/03/11 14:56:02.920150: mcd_account_changed_property: called: ConnectionError
mcd-DEBUG: 27/03/11 14:56:02.920178: mcd_account_changed_property: called: ConnectionErrorDetails
mcd-DEBUG: 27/03/11 14:56:02.920196: mcd_account_thaw_properties: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0
mcd-DEBUG: 27/03/11 14:56:02.920202: emit_property_changed: called
mcd-DEBUG: 27/03/11 14:56:02.920452: _mcd_operation_abort: Operation abort received, aborting all children
mcd-DEBUG: 27/03/11 14:56:02.920463: on_connection_abort: called (0x9a68cf0, account butterfly/msn/rega_5fcarlos_40hotmail_2ecom0)
mcd-DEBUG: 27/03/11 14:56:02.920495: _mcd_mission_set_parent: child = 0x9a68cf0, parent = (nil)
mcd-DEBUG: 27/03/11 14:56:02.920511: _mcd_operation_remove_mission: removing mission: 0x9a68cf0
mcd-DEBUG: 27/03/11 14:56:02.920521: _mcd_connection_dispose: called for object 0x9a68cf0
mcd-DEBUG: 27/03/11 14:56:02.920530: _mcd_connection_release_tp_connection: 0x9a68cf0
mcd-DEBUG: 27/03/11 14:56:02.920545: _mcd_operation_dispose: operation disposed
mcd-DEBUG: 27/03/11 14:56:02.920556: _mcd_mission_dispose: mission disposed 0x9a68cf0
mcd-DEBUG: 27/03/11 14:56:02.920572: _mcd_mission_finalize: mission finalized 0x9a68cf0
mcd-DEBUG: 27/03/11 14:56:02.920583: _mcd_account_dup_parameters: called
mcd-DEBUG: 27/03/11 14:56:02.920809: _mcd_mission_set_parent: child = 0x9a68d58, parent = 0x9a73860
mcd-DEBUG: 27/03/11 14:56:02.920834: mcd_manager_create_connection: Created a connection 0x9a68d58 for account: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0
mcd-DEBUG: 27/03/11 14:56:02.920841: _mcd_connection_connect: called for 0x9a68d58, account butterfly/msn/rega_5fcarlos_40hotmail_2ecom0
mcd-DEBUG: 27/03/11 14:56:02.920850: _mcd_connection_connect_with_params: Trying connect account: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0
mcd-DEBUG: 27/03/11 14:56:02.920862: _mcd_account_set_connection_status: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0: 1 because 1
mcd-DEBUG: 27/03/11 14:56:02.920869: mcd_account_freeze_properties: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0
mcd-DEBUG: 27/03/11 14:56:02.920876: _mcd_account_set_connection_status: changing connection status from 2 to 1
mcd-DEBUG: 27/03/11 14:56:02.920882: mcd_account_changed_property: called: Connection
mcd-DEBUG: 27/03/11 14:56:02.920887: mcd_account_changed_property: First changed property
mcd-DEBUG: 27/03/11 14:56:02.920958: mcd_account_changed_property: called: ConnectionStatus
mcd-DEBUG: 27/03/11 14:56:02.920967: mcd_account_changed_property: called: ConnectionStatusReason
mcd-DEBUG: 27/03/11 14:56:02.920974: mcd_account_changed_property: called: ConnectionError
mcd-DEBUG: 27/03/11 14:56:02.920990: mcd_account_changed_property: called: ConnectionErrorDetails
mcd-DEBUG: 27/03/11 14:56:02.921008: mcd_account_thaw_properties: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0
mcd-DEBUG: 27/03/11 14:56:02.921014: emit_property_changed: called
mcd-DEBUG: 27/03/11 14:56:03.43674: _mcd_account_set_connection_status: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0: 2 because 2
mcd-DEBUG: 27/03/11 14:56:03.43680: mcd_account_freeze_properties: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0
mcd-DEBUG: 27/03/11 14:56:03.43687: _mcd_account_set_connection_status: changing connection status from 1 to 2
mcd-DEBUG: 27/03/11 14:56:03.43689: _mcd_account_set_connection_status: changing connection status reason from 1 to 2
mcd-DEBUG: 27/03/11 14:56:03.43695: mcd_account_changed_property: called: Connection
mcd-DEBUG: 27/03/11 14:56:03.43699: mcd_account_changed_property: First changed property
mcd-DEBUG: 27/03/11 14:56:03.43792: mcd_account_changed_property: called: ConnectionStatus
mcd-DEBUG: 27/03/11 14:56:03.43797: mcd_account_changed_property: called: ConnectionStatusReason
mcd-DEBUG: 27/03/11 14:56:03.43802: mcd_account_changed_property: called: ConnectionError
mcd-DEBUG: 27/03/11 14:56:03.43819: mcd_account_changed_property: called: ConnectionErrorDetails
mcd-DEBUG: 27/03/11 14:56:03.43829: mcd_account_thaw_properties: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0
mcd-DEBUG: 27/03/11 14:56:03.43833: emit_property_changed: called
mcd-WARNING: 27/03/11 14:56:03.43647: request_connection_cb: RequestConnection failed: org.freedesktop.DBus.Python.KeyError: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.6/dist-packages/telepathy/server/connmgr.py", line 69, in RequestConnection
    conn = self._protos[proto](self, parameters)
  File "/usr/lib/python2.6/dist-packages/butterfly/connection.py", line 115, in __init__
    telepathy.server.Connection.__init__(self, 'msn', account, 'butterfly')
  File "/usr/lib/python2.6/dist-packages/telepathy/server/conn.py", line 82, in __init__
    _Connection.__init__(self, bus_name, object_path)
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 480, in __init__
    self.add_to_connection(conn, object_path)
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 571, in add_to_connection
    self._fallback)
KeyError: "Can't register the object-path handler for '/org/freedesktop/Telepathy/Connection/butterfly/msn/rega_5fcarlos_40hotmail_2ecom': there is already a handler"
mcd-DEBUG: 27/03/11 14:56:03.302845: account_reconnect: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0
mcd-DEBUG: 27/03/11 14:56:03.302864: _mcd_connection_release_tp_connection: 0x9a68d58
mcd-DEBUG: 27/03/11 14:56:03.302897: _mcd_account_set_connection_status: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0: 2 because 1
mcd-DEBUG: 27/03/11 14:56:03.302905: mcd_account_freeze_properties: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0
mcd-DEBUG: 27/03/11 14:56:03.302913: _mcd_account_set_connection_status: changing connection status reason from 2 to 1
mcd-DEBUG: 27/03/11 14:56:03.302925: mcd_account_changed_property: called: Connection
mcd-DEBUG: 27/03/11 14:56:03.302931: mcd_account_changed_property: First changed property
mcd-DEBUG: 27/03/11 14:56:03.303082: mcd_account_changed_property: called: ConnectionStatus
mcd-DEBUG: 27/03/11 14:56:03.303092: mcd_account_changed_property: called: ConnectionStatusReason
mcd-DEBUG: 27/03/11 14:56:03.303101: mcd_account_changed_property: called: ConnectionError
mcd-DEBUG: 27/03/11 14:56:03.303128: mcd_account_changed_property: called: ConnectionErrorDetails
mcd-DEBUG: 27/03/11 14:56:03.303147: mcd_account_thaw_properties: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0
mcd-DEBUG: 27/03/11 14:56:03.303153: emit_property_changed: called
mcd-DEBUG: 27/03/11 14:56:03.303448: _mcd_operation_abort: Operation abort received, aborting all children
mcd-DEBUG: 27/03/11 14:56:03.303459: on_connection_abort: called (0x9a68d58, account butterfly/msn/rega_5fcarlos_40hotmail_2ecom0)
mcd-DEBUG: 27/03/11 14:56:03.303492: _mcd_mission_set_parent: child = 0x9a68d58, parent = (nil)
mcd-DEBUG: 27/03/11 14:56:03.303505: _mcd_operation_remove_mission: removing mission: 0x9a68d58
mcd-DEBUG: 27/03/11 14:56:03.303518: _mcd_connection_dispose: called for object 0x9a68d58
mcd-DEBUG: 27/03/11 14:56:03.303525: _mcd_connection_release_tp_connection: 0x9a68d58
mcd-DEBUG: 27/03/11 14:56:03.303541: _mcd_operation_dispose: operation disposed
mcd-DEBUG: 27/03/11 14:56:03.303553: _mcd_mission_dispose: mission disposed 0x9a68d58
mcd-DEBUG: 27/03/11 14:56:03.303569: _mcd_mission_finalize: mission finalized 0x9a68d58
mcd-DEBUG: 27/03/11 14:56:03.303580: _mcd_account_dup_parameters: called
mcd-DEBUG: 27/03/11 14:56:03.303808: _mcd_mission_set_parent: child = 0x9a68dc0, parent = 0x9a73860
mcd-DEBUG: 27/03/11 14:56:03.303833: mcd_manager_create_connection: Created a connection 0x9a68dc0 for account: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0
mcd-DEBUG: 27/03/11 14:56:03.303839: _mcd_connection_connect: called for 0x9a68dc0, account butterfly/msn/rega_5fcarlos_40hotmail_2ecom0
mcd-DEBUG: 27/03/11 14:56:03.303848: _mcd_connection_connect_with_params: Trying connect account: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0
mcd-DEBUG: 27/03/11 14:56:03.303859: _mcd_account_set_connection_status: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0: 1 because 1
mcd-DEBUG: 27/03/11 14:56:03.303865: mcd_account_freeze_properties: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0
mcd-DEBUG: 27/03/11 14:56:03.303873: _mcd_account_set_connection_status: changing connection status from 2 to 1
mcd-DEBUG: 27/03/11 14:56:03.303880: mcd_account_changed_property: called: Connection
mcd-DEBUG: 27/03/11 14:56:03.303886: mcd_account_changed_property: First changed property
mcd-DEBUG: 27/03/11 14:56:03.303956: mcd_account_changed_property: called: ConnectionStatus
mcd-DEBUG: 27/03/11 14:56:03.303965: mcd_account_changed_property: called: ConnectionStatusReason
mcd-DEBUG: 27/03/11 14:56:03.303972: mcd_account_changed_property: called: ConnectionError
mcd-DEBUG: 27/03/11 14:56:03.303989: mcd_account_changed_property: called: ConnectionErrorDetails
mcd-DEBUG: 27/03/11 14:56:03.304006: mcd_account_thaw_properties: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0
mcd-DEBUG: 27/03/11 14:56:03.304012: emit_property_changed: called
mcd-DEBUG: 27/03/11 14:56:03.427799: _mcd_account_set_connection_status: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0: 2 because 2
mcd-DEBUG: 27/03/11 14:56:03.427805: mcd_account_freeze_properties: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0
mcd-DEBUG: 27/03/11 14:56:03.427812: _mcd_account_set_connection_status: changing connection status from 1 to 2
mcd-DEBUG: 27/03/11 14:56:03.427815: _mcd_account_set_connection_status: changing connection status reason from 1 to 2
mcd-DEBUG: 27/03/11 14:56:03.427822: mcd_account_changed_property: called: Connection
mcd-DEBUG: 27/03/11 14:56:03.427824: mcd_account_changed_property: First changed property
mcd-DEBUG: 27/03/11 14:56:03.427917: mcd_account_changed_property: called: ConnectionStatus
mcd-DEBUG: 27/03/11 14:56:03.427922: mcd_account_changed_property: called: ConnectionStatusReason
mcd-DEBUG: 27/03/11 14:56:03.427927: mcd_account_changed_property: called: ConnectionError
mcd-DEBUG: 27/03/11 14:56:03.427944: mcd_account_changed_property: called: ConnectionErrorDetails
mcd-DEBUG: 27/03/11 14:56:03.427953: mcd_account_thaw_properties: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0
mcd-DEBUG: 27/03/11 14:56:03.427958: emit_property_changed: called
mcd-WARNING: 27/03/11 14:56:03.427772: request_connection_cb: RequestConnection failed: org.freedesktop.DBus.Python.KeyError: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.6/dist-packages/telepathy/server/connmgr.py", line 69, in RequestConnection
    conn = self._protos[proto](self, parameters)
  File "/usr/lib/python2.6/dist-packages/butterfly/connection.py", line 115, in __init__
    telepathy.server.Connection.__init__(self, 'msn', account, 'butterfly')
  File "/usr/lib/python2.6/dist-packages/telepathy/server/conn.py", line 82, in __init__
    _Connection.__init__(self, bus_name, object_path)
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 480, in __init__
    self.add_to_connection(conn, object_path)
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 571, in add_to_connection
    self._fallback)
KeyError: "Can't register the object-path handler for '/org/freedesktop/Telepathy/Connection/butterfly/msn/rega_5fcarlos_40hotmail_2ecom': there is already a handler"

mcd-DEBUG: 27/03/11 19:16:06.522876: account_reconnect: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0
mcd-DEBUG: 27/03/11 19:16:06.522890: _mcd_connection_release_tp_connection: 0x9a69090
mcd-DEBUG: 27/03/11 19:16:06.522911: _mcd_account_set_connection_status: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0: 2 because 1
mcd-DEBUG: 27/03/11 19:16:06.522914: mcd_account_freeze_properties: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0
mcd-DEBUG: 27/03/11 19:16:06.522921: _mcd_account_set_connection_status: changing connection status reason from 2 to 1
mcd-DEBUG: 27/03/11 19:16:06.522927: mcd_account_changed_property: called: Connection
mcd-DEBUG: 27/03/11 19:16:06.522931: mcd_account_changed_property: First changed property
mcd-DEBUG: 27/03/11 19:16:06.523030: mcd_account_changed_property: called: ConnectionStatus
mcd-DEBUG: 27/03/11 19:16:06.523035: mcd_account_changed_property: called: ConnectionStatusReason
mcd-DEBUG: 27/03/11 19:16:06.523040: mcd_account_changed_property: called: ConnectionError
mcd-DEBUG: 27/03/11 19:16:06.523056: mcd_account_changed_property: called: ConnectionErrorDetails
mcd-DEBUG: 27/03/11 19:16:06.523066: mcd_account_thaw_properties: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0
mcd-DEBUG: 27/03/11 19:16:06.523071: emit_property_changed: called
mcd-DEBUG: 27/03/11 19:16:06.523238: _mcd_operation_abort: Operation abort received, aborting all children
mcd-DEBUG: 27/03/11 19:16:06.523245: on_connection_abort: called (0x9a69090, account butterfly/msn/rega_5fcarlos_40hotmail_2ecom0)
mcd-DEBUG: 27/03/11 19:16:06.523263: _mcd_mission_set_parent: child = 0x9a69090, parent = (nil)
mcd-DEBUG: 27/03/11 19:16:06.523272: _mcd_operation_remove_mission: removing mission: 0x9a69090
mcd-DEBUG: 27/03/11 19:16:06.523279: _mcd_connection_dispose: called for object 0x9a69090
mcd-DEBUG: 27/03/11 19:16:06.523284: _mcd_connection_release_tp_connection: 0x9a69090
mcd-DEBUG: 27/03/11 19:16:06.523293: _mcd_operation_dispose: operation disposed
mcd-DEBUG: 27/03/11 19:16:06.523298: _mcd_mission_dispose: mission disposed 0x9a69090
mcd-DEBUG: 27/03/11 19:16:06.523308: _mcd_mission_finalize: mission finalized 0x9a69090
mcd-DEBUG: 27/03/11 19:16:06.523315: _mcd_account_dup_parameters: called
mcd-DEBUG: 27/03/11 19:16:06.523446: _mcd_mission_set_parent: child = 0x9a690f8, parent = 0x9a73860
mcd-DEBUG: 27/03/11 19:16:06.523458: mcd_manager_create_connection: Created a connection 0x9a690f8 for account: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0
mcd-DEBUG: 27/03/11 19:16:06.523463: _mcd_connection_connect: called for 0x9a690f8, account butterfly/msn/rega_5fcarlos_40hotmail_2ecom0
mcd-DEBUG: 27/03/11 19:16:06.523468: _mcd_connection_connect_with_params: Trying connect account: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0
mcd-DEBUG: 27/03/11 19:16:06.523473: _mcd_account_set_connection_status: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0: 1 because 1
mcd-DEBUG: 27/03/11 19:16:06.523478: mcd_account_freeze_properties: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0
mcd-DEBUG: 27/03/11 19:16:06.523480: _mcd_account_set_connection_status: changing connection status from 2 to 1
mcd-DEBUG: 27/03/11 19:16:06.523484: mcd_account_changed_property: called: Connection
mcd-DEBUG: 27/03/11 19:16:06.523488: mcd_account_changed_property: First changed property
mcd-DEBUG: 27/03/11 19:16:06.523523: mcd_account_changed_property: called: ConnectionStatus
mcd-DEBUG: 27/03/11 19:16:06.523528: mcd_account_changed_property: called: ConnectionStatusReason
mcd-DEBUG: 27/03/11 19:16:06.523531: mcd_account_changed_property: called: ConnectionError
mcd-DEBUG: 27/03/11 19:16:06.523540: mcd_account_changed_property: called: ConnectionErrorDetails
mcd-DEBUG: 27/03/11 19:16:06.523547: mcd_account_thaw_properties: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0
mcd-DEBUG: 27/03/11 19:16:06.523550: emit_property_changed: called
mcd-DEBUG: 27/03/11 19:16:06.664083: _mcd_account_set_connection_status: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0: 2 because 2
mcd-DEBUG: 27/03/11 19:16:06.664089: mcd_account_freeze_properties: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0
mcd-DEBUG: 27/03/11 19:16:06.664094: _mcd_account_set_connection_status: changing connection status from 1 to 2
mcd-DEBUG: 27/03/11 19:16:06.664098: _mcd_account_set_connection_status: changing connection status reason from 1 to 2
mcd-DEBUG: 27/03/11 19:16:06.664104: mcd_account_changed_property: called: Connection
mcd-DEBUG: 27/03/11 19:16:06.664108: mcd_account_changed_property: First changed property
mcd-DEBUG: 27/03/11 19:16:06.664201: mcd_account_changed_property: called: ConnectionStatus
mcd-DEBUG: 27/03/11 19:16:06.664206: mcd_account_changed_property: called: ConnectionStatusReason
mcd-DEBUG: 27/03/11 19:16:06.664212: mcd_account_changed_property: called: ConnectionError
mcd-DEBUG: 27/03/11 19:16:06.664228: mcd_account_changed_property: called: ConnectionErrorDetails
mcd-DEBUG: 27/03/11 19:16:06.664238: mcd_account_thaw_properties: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0
mcd-DEBUG: 27/03/11 19:16:06.664242: emit_property_changed: called
mcd-WARNING: 27/03/11 19:16:06.664055: request_connection_cb: RequestConnection failed: org.freedesktop.DBus.Python.KeyError: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.6/dist-packages/telepathy/server/connmgr.py", line 69, in RequestConnection
    conn = self._protos[proto](self, parameters)
  File "/usr/lib/python2.6/dist-packages/butterfly/connection.py", line 115, in __init__
    telepathy.server.Connection.__init__(self, 'msn', account, 'butterfly')
  File "/usr/lib/python2.6/dist-packages/telepathy/server/conn.py", line 82, in __init__
    _Connection.__init__(self, bus_name, object_path)
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 480, in __init__
    self.add_to_connection(conn, object_path)
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 571, in add_to_connection
    self._fallback)
KeyError: "Can't register the object-path handler for '/org/freedesktop/Telepathy/Connection/butterfly/msn/rega_5fcarlos_40hotmail_2ecom': there is already a handler"
mcd-DEBUG: 27/03/11 19:16:10.955250: dbusprop_get_all: org.freedesktop.Telepathy.AccountManager
mcd-DEBUG: 27/03/11 19:16:10.955262: get_valid_accounts: called
mcd-DEBUG: 27/03/11 19:16:10.955285: get_invalid_accounts: called
mcd-DEBUG: 27/03/11 19:16:10.955291: mcd_dbus_get_interfaces: called
mcd-DEBUG: 27/03/11 19:16:10.957710: dbusprop_get_all: org.freedesktop.Telepathy.Account
mcd-DEBUG: 27/03/11 19:16:10.957721: mcd_dbus_get_interfaces: called
mcd-DEBUG: 27/03/11 19:16:10.957772: _mcd_account_dup_parameters: called
mcd-DEBUG: 27/03/11 19:16:10.957870: get_connect_automatically: called for butterfly/msn/rega_5fcarlos_40hotmail_2ecom0
mcd-DEBUG: 27/03/11 19:16:10.958686: dbusprop_get_all: org.freedesktop.Telepathy.Account
mcd-DEBUG: 27/03/11 19:16:10.958695: mcd_dbus_get_interfaces: called
mcd-DEBUG: 27/03/11 19:16:10.958739: _mcd_account_dup_parameters: called
mcd-DEBUG: 27/03/11 19:16:10.958832: get_connect_automatically: called for butterfly/msn/rega_5fcarlos_40hotmail_2ecom0
mcd-DEBUG: 27/03/11 19:16:53.811920: account_reconnect: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0
mcd-DEBUG: 27/03/11 19:16:53.811942: _mcd_connection_release_tp_connection: 0x9a690f8
mcd-DEBUG: 27/03/11 19:16:53.811975: _mcd_account_set_connection_status: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0: 2 because 1
mcd-DEBUG: 27/03/11 19:16:53.811984: mcd_account_freeze_properties: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0
mcd-DEBUG: 27/03/11 19:16:53.811991: _mcd_account_set_connection_status: changing connection status reason from 2 to 1
mcd-DEBUG: 27/03/11 19:16:53.812002: mcd_account_changed_property: called: Connection
mcd-DEBUG: 27/03/11 19:16:53.812009: mcd_account_changed_property: First changed property
mcd-DEBUG: 27/03/11 19:16:53.812180: mcd_account_changed_property: called: ConnectionStatus
mcd-DEBUG: 27/03/11 19:16:53.812191: mcd_account_changed_property: called: ConnectionStatusReason
mcd-DEBUG: 27/03/11 19:16:53.812200: mcd_account_changed_property: called: ConnectionError
mcd-DEBUG: 27/03/11 19:16:53.812227: mcd_account_changed_property: called: ConnectionErrorDetails
mcd-DEBUG: 27/03/11 19:16:53.812246: mcd_account_thaw_properties: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0
mcd-DEBUG: 27/03/11 19:16:53.812252: emit_property_changed: called
mcd-DEBUG: 27/03/11 19:16:53.812505: _mcd_operation_abort: Operation abort received, aborting all children
mcd-DEBUG: 27/03/11 19:16:53.812515: on_connection_abort: called (0x9a690f8, account butterfly/msn/rega_5fcarlos_40hotmail_2ecom0)
mcd-DEBUG: 27/03/11 19:16:53.812546: _mcd_mission_set_parent: child = 0x9a690f8, parent = (nil)
mcd-DEBUG: 27/03/11 19:16:53.812562: _mcd_operation_remove_mission: removing mission: 0x9a690f8
mcd-DEBUG: 27/03/11 19:16:53.812575: _mcd_connection_dispose: called for object 0x9a690f8
mcd-DEBUG: 27/03/11 19:16:53.812582: _mcd_connection_release_tp_connection: 0x9a690f8
mcd-DEBUG: 27/03/11 19:16:53.812597: _mcd_operation_dispose: operation disposed
mcd-DEBUG: 27/03/11 19:16:53.812608: _mcd_mission_dispose: mission disposed 0x9a690f8
mcd-DEBUG: 27/03/11 19:16:53.812623: _mcd_mission_finalize: mission finalized 0x9a690f8
mcd-DEBUG: 27/03/11 19:16:53.812635: _mcd_account_dup_parameters: called
mcd-DEBUG: 27/03/11 19:16:53.812858: _mcd_mission_set_parent: child = 0x9a69160, parent = 0x9a73860
mcd-DEBUG: 27/03/11 19:16:53.812880: mcd_manager_create_connection: Created a connection 0x9a69160 for account: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0
mcd-DEBUG: 27/03/11 19:16:53.812890: _mcd_connection_connect: called for 0x9a69160, account butterfly/msn/rega_5fcarlos_40hotmail_2ecom0
mcd-DEBUG: 27/03/11 19:16:53.812896: _mcd_connection_connect_with_params: Trying connect account: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0
mcd-DEBUG: 27/03/11 19:16:53.812910: _mcd_account_set_connection_status: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0: 1 because 1
mcd-DEBUG: 27/03/11 19:16:53.812916: mcd_account_freeze_properties: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0
mcd-DEBUG: 27/03/11 19:16:53.812922: _mcd_account_set_connection_status: changing connection status from 2 to 1
mcd-DEBUG: 27/03/11 19:16:53.812930: mcd_account_changed_property: called: Connection
mcd-DEBUG: 27/03/11 19:16:53.812936: mcd_account_changed_property: First changed property
mcd-DEBUG: 27/03/11 19:16:53.813002: mcd_account_changed_property: called: ConnectionStatus
mcd-DEBUG: 27/03/11 19:16:53.813009: mcd_account_changed_property: called: ConnectionStatusReason
mcd-DEBUG: 27/03/11 19:16:53.813018: mcd_account_changed_property: called: ConnectionError
mcd-DEBUG: 27/03/11 19:16:53.813034: mcd_account_changed_property: called: ConnectionErrorDetails
mcd-DEBUG: 27/03/11 19:16:53.813049: mcd_account_thaw_properties: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0
mcd-DEBUG: 27/03/11 19:16:53.813055: emit_property_changed: called
mcd-DEBUG: 27/03/11 19:16:53.973109: _mcd_account_set_connection_status: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0: 2 because 2
mcd-DEBUG: 27/03/11 19:16:53.973115: mcd_account_freeze_properties: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0
mcd-DEBUG: 27/03/11 19:16:53.973120: _mcd_account_set_connection_status: changing connection status from 1 to 2
mcd-DEBUG: 27/03/11 19:16:53.973124: _mcd_account_set_connection_status: changing connection status reason from 1 to 2
mcd-DEBUG: 27/03/11 19:16:53.973130: mcd_account_changed_property: called: Connection
mcd-DEBUG: 27/03/11 19:16:53.973134: mcd_account_changed_property: First changed property
mcd-DEBUG: 27/03/11 19:16:53.973226: mcd_account_changed_property: called: ConnectionStatus
mcd-DEBUG: 27/03/11 19:16:53.973231: mcd_account_changed_property: called: ConnectionStatusReason
mcd-DEBUG: 27/03/11 19:16:53.973236: mcd_account_changed_property: called: ConnectionError
mcd-DEBUG: 27/03/11 19:16:53.973253: mcd_account_changed_property: called: ConnectionErrorDetails
mcd-DEBUG: 27/03/11 19:16:53.973263: mcd_account_thaw_properties: butterfly/msn/rega_5fcarlos_40hotmail_2ecom0
mcd-DEBUG: 27/03/11 19:16:53.973265: emit_property_changed: called
mcd-WARNING: 27/03/11 19:16:53.973082: request_connection_cb: RequestConnection failed: org.freedesktop.DBus.Python.KeyError: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.6/dist-packages/telepathy/server/connmgr.py", line 69, in RequestConnection
    conn = self._protos[proto](self, parameters)
  File "/usr/lib/python2.6/dist-packages/butterfly/connection.py", line 115, in __init__
    telepathy.server.Connection.__init__(self, 'msn', account, 'butterfly')
  File "/usr/lib/python2.6/dist-packages/telepathy/server/conn.py", line 82, in __init__
    _Connection.__init__(self, bus_name, object_path)
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 480, in __init__
    self.add_to_connection(conn, object_path)
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 571, in add_to_connection
    self._fallback)
KeyError: "Can't register the object-path handler for '/org/freedesktop/Telepathy/Connection/butterfly/msn/rega_5fcarlos_40hotmail_2ecom': there is already a handler"
mcd-DEBUG: 27/03/11 19:16:56.408406: dbusprop_get_all: org.freedesktop.Telepathy.AccountManager
mcd-DEBUG: 27/03/11 19:16:56.408420: get_valid_accounts: called
mcd-DEBUG: 27/03/11 19:16:56.408441: get_invalid_accounts: called
mcd-DEBUG: 27/03/11 19:16:56.408447: mcd_dbus_get_interfaces: called
mcd-DEBUG: 27/03/11 19:16:56.410851: dbusprop_get_all: org.freedesktop.Telepathy.Account
mcd-DEBUG: 27/03/11 19:16:56.410862: mcd_dbus_get_interfaces: called
mcd-DEBUG: 27/03/11 19:16:56.410913: _mcd_account_dup_parameters: called
mcd-DEBUG: 27/03/11 19:16:56.411011: get_connect_automatically: called for butterfly/msn/rega_5fcarlos_40hotmail_2ecom0
mcd-DEBUG: 27/03/11 19:16:56.411861: dbusprop_get_all: org.freedesktop.Telepathy.Account
mcd-DEBUG: 27/03/11 19:16:56.411871: mcd_dbus_get_interfaces: called
mcd-DEBUG: 27/03/11 19:16:56.411916: _mcd_account_dup_parameters: called
mcd-DEBUG: 27/03/11 19:16:56.412009: get_connect_automatically: called for butterfly/msn/rega_5fcarlos_40hotmail_2ecom0 
```

If I try logging on amsn it works perfectly, so I don't know what could be the problem. Thanks!

---

