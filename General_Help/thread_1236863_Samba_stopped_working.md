---
title: "Samba stopped working"
date: 2009-08-10
forum: General Help
---

### Post by mocka on 2009-08-10
Samba was working great all day, just until I mounted a harddrive to a folder that already was being shared by samba. After that, I have not been able to access the samba shares from my windows boxes.

Here I have provided the Samba log file:

> 
[2009/08/09 01:59:01,  0] smbd/server.c:main(1260)
  smbd version 3.3.2 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2009/08/09 01:59:01,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/09 01:59:01,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/09 02:10:12,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/09 02:10:12,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/09 02:41:27,  0] smbd/server.c:main(1260)
  smbd version 3.3.2 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2009/08/09 02:41:27,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/09 02:41:27,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/09 02:59:35,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/09 02:59:35,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/09 03:06:46,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/09 03:06:46,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/09 03:14:12,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/09 03:14:12,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/09 03:27:23,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/09 03:27:23,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/09 17:57:28,  0] smbd/server.c:main(1260)
  smbd version 3.3.2 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2009/08/09 17:57:28,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/09 17:57:28,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/09 17:58:28,  1] smbd/server.c:open_sockets_smbd(657)
  Reloading services after SIGHUP
[2009/08/09 17:58:28,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/09 17:58:28,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/09 18:05:43,  1] smbd/server.c:open_sockets_smbd(657)
  Reloading services after SIGHUP
[2009/08/09 18:05:43,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/09 18:05:43,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/09 20:41:01,  0] smbd/server.c:main(1260)
  smbd version 3.3.2 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2009/08/09 20:41:01,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/09 20:41:01,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/09 20:42:30,  0] smbd/server.c:main(1260)
  smbd version 3.3.2 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2009/08/09 20:42:30,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/09 20:42:30,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/09 21:22:08,  0] smbd/server.c:main(1260)
  smbd version 3.3.2 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2009/08/09 21:22:08,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/09 21:22:08,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/09 21:22:09,  1] smbd/server.c:open_sockets_smbd(657)
  Reloading services after SIGHUP
[2009/08/09 21:22:09,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/09 21:22:09,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/09 21:28:18,  0] smbd/server.c:main(1260)
  smbd version 3.3.2 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2009/08/09 21:28:18,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/09 21:28:18,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/09 21:28:20,  1] smbd/server.c:open_sockets_smbd(657)
  Reloading services after SIGHUP
[2009/08/09 21:28:20,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/09 21:28:20,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/09 23:13:38,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/09 23:13:38,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/09 23:13:38,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/09 23:13:38,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/09 23:29:31,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/09 23:29:31,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/09 23:45:41,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/09 23:45:41,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/09 23:53:11,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/09 23:53:11,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/10 00:00:29,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/10 00:00:29,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/10 00:17:41,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/10 00:17:41,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/10 00:49:47,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/10 00:49:48,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/10 01:26:37,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/10 01:26:37,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/10 11:28:53,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/10 11:28:53,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/10 11:57:30,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/10 11:57:30,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/10 12:10:34,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/10 12:10:34,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/10 12:42:34,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/10 12:42:34,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/10 12:58:38,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/10 12:58:38,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/10 15:22:35,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/10 15:22:35,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/10 15:54:41,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/10 15:54:41,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/10 16:08:54,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/10 16:08:54,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/10 16:24:24,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/10 16:24:24,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/10 16:46:41,  0] smbd/server.c:main(1260)
  smbd version 3.3.2 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2009/08/10 16:46:41,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/10 16:46:41,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/10 16:46:41,  0] passdb/pdb_interface.c:guest_user_info(253)
  guest_user_info: Unable to locate guest account [guest]!
[2009/08/10 16:46:41,  0] smbd/server.c:main(1389)
  ERROR: failed to setup guest info.
[2009/08/10 17:00:38,  0] smbd/server.c:main(1260)
  smbd version 3.3.2 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2009/08/10 17:00:38,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/10 17:00:38,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/10 17:00:38,  0] passdb/pdb_interface.c:guest_user_info(253)
  guest_user_info: Unable to locate guest account [guest]!
[2009/08/10 17:00:38,  0] smbd/server.c:main(1389)
  ERROR: failed to setup guest info.
[2009/08/10 17:05:50,  0] smbd/server.c:main(1260)
  smbd version 3.3.2 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2009/08/10 17:05:50,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/10 17:05:50,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/10 17:05:50,  0] passdb/pdb_interface.c:guest_user_info(253)
  guest_user_info: Unable to locate guest account [guest]!
[2009/08/10 17:05:50,  0] smbd/server.c:main(1389)
  ERROR: failed to setup guest info.
[2009/08/10 17:20:37,  0] smbd/server.c:main(1260)
  smbd version 3.3.2 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2009/08/10 17:20:37,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/10 17:20:37,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/10 17:20:37,  0] passdb/pdb_interface.c:guest_user_info(253)
  guest_user_info: Unable to locate guest account [guest]!
[2009/08/10 17:20:37,  0] smbd/server.c:main(1389)
  ERROR: failed to setup guest info.
[2009/08/10 18:11:54,  0] smbd/server.c:main(1260)
  smbd version 3.3.2 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2009/08/10 18:11:55,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/10 18:11:55,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/10 18:11:55,  0] passdb/pdb_interface.c:guest_user_info(253)
  guest_user_info: Unable to locate guest account [guest]!
[2009/08/10 18:11:55,  0] smbd/server.c:main(1389)
  ERROR: failed to setup guest info.
[2009/08/10 19:19:41,  0] smbd/server.c:main(1260)
  smbd version 3.3.2 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2009/08/10 19:19:41,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/10 19:19:41,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/10 19:19:42,  0] passdb/pdb_interface.c:guest_user_info(253)
  guest_user_info: Unable to locate guest account [guest]!
[2009/08/10 19:19:42,  0] smbd/server.c:main(1389)
  ERROR: failed to setup guest info.
[2009/08/10 20:20:29,  0] smbd/server.c:main(1260)
  smbd version 3.3.2 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2009/08/10 20:20:29,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/10 20:20:29,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/10 20:20:29,  0] passdb/pdb_interface.c:guest_user_info(253)
  guest_user_info: Unable to locate guest account [guest]!
[2009/08/10 20:20:29,  0] smbd/server.c:main(1389)
  ERROR: failed to setup guest info.
[2009/08/10 21:03:41,  0] smbd/server.c:main(1260)
  smbd version 3.3.2 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2009/08/10 21:03:41,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/10 21:03:41,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/10 21:03:41,  0] passdb/pdb_interface.c:guest_user_info(253)
  guest_user_info: Unable to locate guest account [guest]!
[2009/08/10 21:03:41,  0] smbd/server.c:main(1389)
  ERROR: failed to setup guest info.
[2009/08/10 22:33:28,  0] smbd/server.c:main(1260)
  smbd version 3.3.2 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2009/08/10 22:33:28,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/10 22:33:28,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/10 22:33:28,  0] passdb/pdb_interface.c:guest_user_info(253)
  guest_user_info: Unable to locate guest account [guest]!
[2009/08/10 22:33:28,  0] smbd/server.c:main(1389)
  ERROR: failed to setup guest info.
[2009/08/10 22:34:52,  0] smbd/server.c:main(1260)
  smbd version 3.3.2 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2009/08/10 22:34:52,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/10 22:34:52,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/10 22:34:52,  0] passdb/pdb_interface.c:guest_user_info(253)
  guest_user_info: Unable to locate guest account [guest]!
[2009/08/10 22:34:52,  0] smbd/server.c:main(1389)
  ERROR: failed to setup guest info.
[2009/08/10 23:08:33,  0] smbd/server.c:main(1260)
  smbd version 3.3.2 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2009/08/10 23:08:33,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/10 23:08:33,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/10 23:08:34,  0] passdb/pdb_interface.c:guest_user_info(253)
  guest_user_info: Unable to locate guest account [guest]!
[2009/08/10 23:08:34,  0] smbd/server.c:main(1389)
  ERROR: failed to setup guest info.
[2009/08/10 23:10:26,  0] smbd/server.c:main(1260)
  smbd version 3.3.2 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2009/08/10 23:10:26,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/10 23:10:26,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/08/10 23:10:26,  0] passdb/pdb_interface.c:guest_user_info(253)
  guest_user_info: Unable to locate guest account [guest]!
[2009/08/10 23:10:26,  0] smbd/server.c:main(1389)
  ERROR: failed to setup guest info.


It seems to me that cups might be the problem (I don't think CUPS even is installed).

Does anyone have any suggestions?

By the way; I'm running Ubuntu Server Edition.

---

