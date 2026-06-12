---
title: "BDUS program error"
date: 2011-01-13
forum: General Help
---

### Post by akmp on 2011-01-13
Hi All,
 
Pardon me if i am asking some basic stuff..
 
I run the following dbus program on my ubuntu station..
 
#include <stdio.h>
#include <stdlib.h>
#include <dbus.h>
int main(int argc, char **argv) 
{
DBusConnection *conn;
DBusMessage *msg, *reply;
const char *name;
conn = dbus_bus_get(DBUS_BUS_SYSTEM, NULL);
msg = dbus_message_new_method_call(
"org.bluez",
"/org/bluez/hci0",
"org.bluez.Adapter", "GetName");
reply =
dbus_connection_send_with_reply_and_block(
conn, msg, -1, NULL);
dbus_message_get_args(reply, NULL,
DBUS_TYPE_STRING, &name,
DBUS_TYPE_INVALID);
printf("%s\n", name);
dbus_message_unref(msg);
dbus_message_unref(reply);
dbus_connection_close(conn);
return 0;
}
 
it compiles fine and generates the executable..while running the same the following error comes...
 
process 2326: arguments to dbus_message_get_args() were incorrect, assertion "message != NULL" failed in file dbus-message.c line 1840.
This is normally a bug in some application using the D-Bus library.
&#65533;&#65533;[]Í&#65533;&#65533;
process 2326: arguments to dbus_message_unref() were incorrect, assertion "message != NULL" failed in file dbus-message.c line 1546.
This is normally a bug in some application using the D-Bus library.
process 2326: Applications must not close shared connections - see dbus_connection_close() docs. This is a bug in the application.
 
Can some one help me understand what is wrong here..either in the setup or something else...
 
regards
Aji.

---

### Post by bindusun on 2011-03-20
I'm facing the same issue as yours.
I get the same error when I run the executable of a sample basic program of dbus-C or dbus-glib .

Were you able to get your error resolved. If yes, then please do let me know what's the resolution.
I'm new to DBus programming.

---

