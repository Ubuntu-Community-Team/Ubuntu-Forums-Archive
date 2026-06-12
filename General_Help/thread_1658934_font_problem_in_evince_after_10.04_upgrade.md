---
title: "font problem in evince after 10.04 upgrade"
date: 2011-01-03
forum: General Help
---

### Post by PapaNerd on 2011-01-03
Following upgrades to v10.04 on two systems, pdf files no longer open properly in evince.  While the files do open, only some graphics are shown, and usually no text.  The same files formerly worked properly in Evince at both v9.04 and v9.10, and currently open properly using ePDFViewer v0.1.7.  

For example, opening the OpenOffice v3.3.0 Installation Guide (in the /tmp directory) shows only underlines on the second page.  Running evince from the command line produces the following messages:

```

# evince

(evince:10203): EggSMClient-WARNING **: Failed to connect to the session manager: None of the authentication protocols specified are supported

** (evince:10203): WARNING **: Failed to connect to the session bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

** (evince:10203): WARNING **: Error connection to DBus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

** (evince:10203): WARNING **: Error connecting to D-Bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

** (evince:10203): WARNING **: Setting attribute metadata::evince::sidebar_visibility not supported
Error: Couldn't create temporary font file
some font thing failed
Error: Couldn't create temporary font file
some font thing failed
Error: Couldn't create temporary font file
some font thing failed
Error: Couldn't create temporary font file
some font thing failed
Error: Couldn't create temporary font file
some font thing failed
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
Error: Couldn't create temporary font file
some font thing failed

```
These last two lines were repeated 306 times.

The setup of the two systems differ from the previous configurations in that both the /home directory and the /tmp directory are located on a LUKS partition.

Anyone have any ideas on how to get evince working?

5 Jan 2011 update:  A reinstall of evince failed to resolve the problem.

---

### Post by PapaNerd on 2011-01-05
This problem occurs under both:
2.30.3-0ubuntu1.1
2.30.3-0ubuntu1.2

---

