---
title: "Get &quot;/bin/dbus-launch terminated abnormally&quot; when starting firefox w/ different  user"
date: 2011-04-11
forum: General Help
---

### Post by bengwie on 2011-04-11
Through SSH ('root' user), with $DISPLAY is linked to the Desktop of another user ("User2"), I tried to invoke firefox through 'root' user. Firefox is launched, along with the error message:

"An error occurred while loading or saving configuration information for firefox-bin. Some of your configuration settings may not work properly."

When clicking "Details":
"Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf](http://projects.gnome.org/gconf) for information. (Details - 1: Failed to get connection to session: /bin/dbus-launch terminated abnormally with the following error: EOF in dbus-launch reading address from bus daemon)"

-----------------------------------------------------------------
If I invoked firefox with "User2" --> "su - user2 -c "firefox", it works just fine. My understanding is when I launched firefox with root user, the display is going to "user2" screen because $DISPLAY is mapped to there, but the dbus-launch session is created on the root user, thus "user2" desktop is complaining that it cannot find the dbus-launch for "user2". Any idea of how to fix this issue? I really appreciate any input. 

-Jeff

---

