---
title: "Help Setting up Samba File Sharing in 11.10"
date: 2011-10-31
forum: General Help
---

### Post by carleton on 2011-10-31
Hey guys,

I know there's a lot of samba threads out there already. I've tried  to tried following a lot of them, but I can't seem to get any of them to help me. I can't seem to get filesharing to work at all on my 11.10 setup. 

I've tried to share several folders from nautilus (right clicking an going to sharing options) From an XP box I also have I can see my server in "Network Places" however when I try to open it I get an error message that looks like [_this_]("http://i.imgur.com/VwY3o.png")

My smb.conf looks like [_this_]("http://pastebin.com/raw.php?i=0FyjeDij") (should be the default)


Any help would be much appreciated. I've been going bonkers over this!:confused:

---

### Post by ballantony on 2011-10-31
I can't see what shares you have set up, if any.  Have you tried this

[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/FastStart.html](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/FastStart.html)

It's a good place to begin...

---

### Post by carleton on 2011-10-31
Thanks for the reply. I tried adding the following to my smb.conf, but they didn't seem to change anything, even after a restart. Any other ideas?

[vids]
path = /media/MEDIA/videos
writeable = yes
; browseable = yes
guest ok = yes

[public]
path = /home/Public
writeable = yes
; browseable = yes
guest ok = yes

---

### Post by Devi1903 on 2011-10-31
you need to remove the
```
;
```
from in front of browseable. The ; comments this out which means with your current setup the share is not browseable and therefore you get that error when you try opening it.

Remove this and restart your samba server and it should all work.

---

### Post by carleton on 2011-10-31
Thanks for the tip. I tried that and restarted but am Still getting the same error. I even tried on two other devices so I know it's not my xp box. Is there any way to test that the server's working from my own computer?

---

### Post by Morbius1 on 2011-10-31
Add the following line to the [global] section of smb.conf ( right under the workgoup line would be my choice ) :
```
netbios name = something
```Change "something" to anything you want as long as it's 15 characters or less in length ( as opposed to Dr-Grandmas-moustache which is 21 ).
Then restart samba

---

### Post by Devi1903 on 2011-10-31
can you post the samba log from the computer you are trying to access the share on?

---

### Post by carleton on 2011-10-31
Hey guys, thanks again. I tried adding the netbious line, but it sadly didn't change anything. Is there maybe some software I need to install? I didn't add anything other than when Nautilus asked If I wanted to install Samba.

Here's my latest log.smbd 

```
[2011/10/31 10:53:32,  0] smbd/server.c:1141(main)
  smbd version 3.5.11 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2010
[2011/10/31 10:53:32.308339,  0] smbd/server.c:1187(main)
  standard input is not a socket, assuming -D option
[2011/10/31 10:56:40.093516,  1] smbd/server.c:282(remove_child_pid)
  Could not find child 9830 -- ignoring
[2011/10/31 11:09:40.459809,  1] smbd/server.c:282(remove_child_pid)
  Could not find child 10270 -- ignoring
[2011/10/31 11:22:40.845673,  1] smbd/server.c:282(remove_child_pid)
  Could not find child 10330 -- ignoring
[2011/10/31 11:30:41.063554,  0] param/loadparm.c:7628(lp_do_parameter)
  Global parameter netbios name found in service section!
[2011/10/31 11:30:41.063621,  0] param/loadparm.c:7628(lp_do_parameter)
  Global parameter lanman auth found in service section!
[2011/10/31 11:30:41.063664,  0] param/loadparm.c:7628(lp_do_parameter)
  Global parameter lm announce found in service section!
[2011/10/31 11:30:41.063698,  0] param/loadparm.c:7628(lp_do_parameter)
  Global parameter min protocol found in service section!
[2011/10/31 11:30:41.063727,  0] param/loadparm.c:7628(lp_do_parameter)
  Global parameter security found in service section!
[2011/10/31 11:30:41.063757,  0] param/loadparm.c:7628(lp_do_parameter)
  Global parameter guest account found in service section!
[2011/10/31 11:30:41.063784,  1] ../lib/util/params.c:350(Parameter)
  params.c:Parameter() - Ignoring badly formed line in configuration file: Guest Share]
[2011/10/31 11:30:41.068800,  1] smbd/server.c:282(remove_child_pid)
  Could not find child 10411 -- ignoring
[2011/10/31 11:30:41,  0] smbd/server.c:1141(main)
  smbd version 3.5.11 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2010
[2011/10/31 11:30:41.323391,  1] ../lib/util/params.c:350(Parameter)
  params.c:Parameter() - Ignoring badly formed line in configuration file: Guest Share]
[2011/10/31 11:30:41.325498,  0] param/loadparm.c:7628(lp_do_parameter)
  Global parameter netbios name found in service section!
[2011/10/31 11:30:41.325584,  0] param/loadparm.c:7628(lp_do_parameter)
  Global parameter lanman auth found in service section!
[2011/10/31 11:30:41.325646,  0] param/loadparm.c:7628(lp_do_parameter)
  Global parameter lm announce found in service section!
[2011/10/31 11:30:41.325695,  0] param/loadparm.c:7628(lp_do_parameter)
  Global parameter min protocol found in service section!
[2011/10/31 11:30:41.325738,  0] param/loadparm.c:7628(lp_do_parameter)
  Global parameter security found in service section!
[2011/10/31 11:30:41.325779,  0] param/loadparm.c:7628(lp_do_parameter)
  Global parameter guest account found in service section!
[2011/10/31 11:30:41.325819,  1] ../lib/util/params.c:350(Parameter)
  params.c:Parameter() - Ignoring badly formed line in configuration file: Guest Share]
[2011/10/31 11:30:41.331744,  0] smbd/server.c:1187(main)
  standard input is not a socket, assuming -D option
[2011/10/31 11:33:41.422151,  1] smbd/server.c:282(remove_child_pid)
  Could not find child 10458 -- ignoring
[2011/10/31 11:40:37,  0] smbd/server.c:1141(main)
  smbd version 3.5.11 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2010
[2011/10/31 11:40:37.547267,  1] ../lib/util/params.c:350(Parameter)
  params.c:Parameter() - Ignoring badly formed line in configuration file: Guest Share]
[2011/10/31 11:40:37.615290,  0] param/loadparm.c:7628(lp_do_parameter)
  Global parameter netbios name found in service section!
[2011/10/31 11:40:37.615346,  0] param/loadparm.c:7628(lp_do_parameter)
  Global parameter lanman auth found in service section!
[2011/10/31 11:40:37.615390,  0] param/loadparm.c:7628(lp_do_parameter)
  Global parameter lm announce found in service section!
[2011/10/31 11:40:37.615424,  0] param/loadparm.c:7628(lp_do_parameter)
  Global parameter min protocol found in service section!
[2011/10/31 11:40:37.615453,  0] param/loadparm.c:7628(lp_do_parameter)
  Global parameter security found in service section!
[2011/10/31 11:40:37.615482,  0] param/loadparm.c:7628(lp_do_parameter)
  Global parameter guest account found in service section!
[2011/10/31 11:40:37.615524,  1] ../lib/util/params.c:350(Parameter)
  params.c:Parameter() - Ignoring badly formed line in configuration file: Guest Share]
[2011/10/31 11:40:37.800739,  0] printing/print_cups.c:109(cups_connect)
  Unable to connect to CUPS server localhost:631 - No such file or directory
[2011/10/31 11:40:37.800987,  0] printing/print_cups.c:468(cups_async_callback)
  failed to retrieve printer list: NT_STATUS_UNSUCCESSFUL
[2011/10/31 11:40:38.102565,  0] smbd/server.c:1187(main)
  standard input is not a socket, assuming -D option
[2011/10/31 11:40:39.057329,  0] smbd/server.c:501(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Address already in use
[2011/10/31 11:40:39.057485,  0] smbd/server.c:501(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Address already in use
[2011/10/31 11:43:39.103356,  1] smbd/server.c:282(remove_child_pid)
  Could not find child 1981 -- ignoring
[2011/10/31 11:56:39.380952,  1] smbd/server.c:282(remove_child_pid)
  Could not find child 2083 -- ignoring
[2011/10/31 12:09:39.626902,  1] smbd/server.c:282(remove_child_pid)
  Could not find child 2093 -- ignoring
[2011/10/31 12:18:37.130686,  1] smbd/server.c:267(remove_child_pid)
  Scheduled cleanup of brl and lock database after unclean shutdown
[2011/10/31 12:18:57.144416,  1] smbd/server.c:240(cleanup_timeout_fn)
  Cleaning up brl and lock database after unclean shutdown
[2011/10/31 12:22:39.879226,  1] smbd/server.c:282(remove_child_pid)
  Could not find child 2433 -- ignoring
[2011/10/31 12:23:39.886699,  1] smbd/server.c:282(remove_child_pid)
  Could not find child 2436 -- ignoring
[2011/10/31 12:35:40.093457,  1] smbd/server.c:282(remove_child_pid)
  Could not find child 3072 -- ignoring
[2011/10/31 12:44:40.399072,  1] smbd/server.c:282(remove_child_pid)
  Could not find child 3337 -- ignoring
[2011/10/31 12:44:41,  0] smbd/server.c:1141(main)
  smbd version 3.5.11 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2010
[2011/10/31 12:44:41.357802,  0] smbd/server.c:1187(main)
  standard input is not a socket, assuming -D option
[2011/10/31 12:47:41.488917,  1] smbd/server.c:282(remove_child_pid)
  Could not find child 3423 -- ignoring
[2011/10/31 12:48:41.519702,  1] smbd/server.c:282(remove_child_pid)
  Could not find child 3436 -- ignoring
[2011/10/31 13:00:41.828410,  1] smbd/server.c:282(remove_child_pid)
  Could not find child 3447 -- ignoring
[2011/10/31 13:13:42.124215,  1] smbd/server.c:282(remove_child_pid)
  Could not find child 3460 -- ignoring
[2011/10/31 13:26:42.386629,  1] smbd/server.c:282(remove_child_pid)
  Could not find child 3484 -- ignoring
[2011/10/31 13:39:42.785244,  1] smbd/server.c:282(remove_child_pid)
  Could not find child 3496 -- ignoring
[2011/10/31 13:52:43.167787,  1] smbd/server.c:282(remove_child_pid)
  Could not find child 3537 -- ignoring
[2011/10/31 13:54:55,  0] smbd/server.c:1141(main)
  smbd version 3.5.11 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2010
[2011/10/31 13:54:55.823231,  0] printing/print_cups.c:109(cups_connect)
  Unable to connect to CUPS server localhost:631 - No such file or directory
[2011/10/31 13:54:55.823938,  0] printing/print_cups.c:468(cups_async_callback)
  failed to retrieve printer list: NT_STATUS_UNSUCCESSFUL
[2011/10/31 13:54:55.825071,  0] smbd/server.c:1187(main)
  standard input is not a socket, assuming -D option
[2011/10/31 13:54:55.897944,  0] smbd/server.c:501(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Address already in use
[2011/10/31 13:54:55.898096,  0] smbd/server.c:501(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Address already in use
[2011/10/31 13:57:55.933474,  1] smbd/server.c:282(remove_child_pid)
  Could not find child 1996 -- ignoring
[2011/10/31 14:10:56.193213,  1] smbd/server.c:282(remove_child_pid)
  Could not find child 2543 -- ignoring
[2011/10/31 14:19:56.568668,  1] smbd/server.c:282(remove_child_pid)
  Could not find child 2869 -- ignoring
[2011/10/31 14:23:56.728482,  1] smbd/server.c:282(remove_child_pid)
  Could not find child 2968 -- ignoring
[2011/10/31 14:24:11.606399,  1] smbd/server.c:267(remove_child_pid)
  Scheduled cleanup of brl and lock database after unclean shutdown
[2011/10/31 14:24:31.624489,  1] smbd/server.c:240(cleanup_timeout_fn)
  Cleaning up brl and lock database after unclean shutdown
[2011/10/31 14:30:56,  0] smbd/server.c:1141(main)
  smbd version 3.5.11 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2010
[2011/10/31 14:30:56.415645,  0] smbd/server.c:1187(main)
  standard input is not a socket, assuming -D option
[2011/10/31 14:32:56,  0] smbd/server.c:1141(main)
  smbd version 3.5.11 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2010
[2011/10/31 14:32:57.273864,  0] printing/print_cups.c:109(cups_connect)
  Unable to connect to CUPS server localhost:631 - No such file or directory
[2011/10/31 14:32:57.274115,  0] printing/print_cups.c:468(cups_async_callback)
  failed to retrieve printer list: NT_STATUS_UNSUCCESSFUL
[2011/10/31 14:32:57.408738,  0] smbd/server.c:1187(main)
  standard input is not a socket, assuming -D option
[2011/10/31 14:32:58.104925,  0] smbd/server.c:501(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Address already in use
[2011/10/31 14:32:58.105090,  0] smbd/server.c:501(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Address already in use
[2011/10/31 14:35:58.247300,  1] smbd/server.c:282(remove_child_pid)
  Could not find child 2045 -- ignoring
[2011/10/31 14:48:58.642403,  1] smbd/server.c:282(remove_child_pid)
  Could not find child 2425 -- ignoring
[2011/10/31 15:00:48.021098,  1] smbd/server.c:267(remove_child_pid)
  Scheduled cleanup of brl and lock database after unclean shutdown
[2011/10/31 15:01:08.028420,  1] smbd/server.c:240(cleanup_timeout_fn)
  Cleaning up brl and lock database after unclean shutdown
[2011/10/31 15:01:58.975096,  1] smbd/server.c:282(remove_child_pid)
  Could not find child 2437 -- ignoring
[2011/10/31 15:14:59.361452,  1] smbd/server.c:282(remove_child_pid)
  Could not find child 2452 -- ignoring
[2011/10/31 15:23:44,  0] smbd/server.c:1141(main)
  smbd version 3.5.11 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2010
[2011/10/31 15:23:44.281797,  0] smbd/server.c:1187(main)
  standard input is not a socket, assuming -D option
[2011/10/31 15:26:44.549121,  1] smbd/server.c:282(remove_child_pid)
  Could not find child 2569 -- ignoring
[2011/10/31 15:34:02,  0] smbd/server.c:1141(main)
  smbd version 3.5.11 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2010
[2011/10/31 15:34:02.858527,  0] smbd/server.c:1187(main)
  standard input is not a socket, assuming -D option
[2011/10/31 15:34:11,  0] smbd/server.c:1141(main)
  smbd version 3.5.11 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2010
[2011/10/31 15:34:11.215790,  0] smbd/server.c:1187(main)
  standard input is not a socket, assuming -D option
[2011/10/31 15:37:11.380312,  1] smbd/server.c:282(remove_child_pid)
  Could not find child 2909 -- ignoring
[2011/10/31 15:40:29,  0] smbd/server.c:1141(main)
  smbd version 3.5.11 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2010
[2011/10/31 15:40:29.364892,  0] smbd/server.c:1187(main)
  standard input is not a socket, assuming -D option
[2011/10/31 15:43:29.497099,  1] smbd/server.c:282(remove_child_pid)
  Could not find child 3434 -- ignoring
[2011/10/31 15:45:37,  0] smbd/server.c:1141(main)
  smbd version 3.5.11 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2010
[2011/10/31 15:45:37.212468,  0] smbd/server.c:1187(main)
  standard input is not a socket, assuming -D option
[2011/10/31 15:48:37.285104,  1] smbd/server.c:282(remove_child_pid)
  Could not find child 3621 -- ignoring
[2011/10/31 15:55:37.429864,  1] smbd/server.c:282(remove_child_pid)
  Could not find child 4114 -- ignoring
[2011/10/31 15:58:37.473792,  1] smbd/server.c:282(remove_child_pid)
  Could not find child 4650 -- ignoring
[2011/10/31 16:00:12,  0] smbd/server.c:1141(main)
  smbd version 3.5.11 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2010
[2011/10/31 16:00:12.403115,  0] smbd/server.c:1187(main)
  standard input is not a socket, assuming -D option
[2011/10/31 16:03:12.489162,  1] smbd/server.c:282(remove_child_pid)
  Could not find child 4730 -- ignoring
```

Thanks again everyone!

---

### Post by Morbius1 on 2011-10-31
Need more info I'm afraid. Post the output of these commands:
```
smbtree
ls -al /media/Media
ls -dl /home/Public
net usershare info --long
```

---

### Post by carleton on 2011-10-31
Alright here you go. 

smbtree
```


	\\DR-GRANDMAS-MOUS		Dr-Grandmas-Moustache server (Samba, Ubuntu)


cli_start_connection: failed to connect to DR-GRANDMAS-MOUS<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
	\\DELLTOP        		
cli_start_connection: failed to connect to DELLTOP<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
	\\BOXEEBOX       		Samba 3.0.37
cli_start_connection: failed to connect to BOXEEBOX<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
```

ls -al /media/Media
This is a long one. I'm actually just after the videos folder being shared
```

-rwxr-xr-x    1 carleton carleton    594432 2007-01-24 16:22 zsnesw.exe
```


ls -dl /home/Public
```
drwxrwxrwx 2 carleton carleton 4096 2011-10-31 12:26 Public
```


net usershare info --long
```
[public]
path=/home/carleton/Public
comment=
usershare_acl=Everyone:F,
guest_ok=y
```

Thanks again

---

### Post by Morbius1 on 2011-10-31
**[1] You need to fix the netbios name as I suggested above.**

** [2] You need to add this line to the [global] section:**
```
name resolve order = bcast host lmhosts wins
```Someone else on this forum takes this one step furter and changes it to:
```
name resolve order = bcast host
```**[3] No one except carleton can access anything on /media/Media ( I suspect this is an NTFS partition ) so make everyone look like carleton in your share definition.**

Change this:
> [vids]
path = /media/MEDIA/videos
writeable = yes
; browseable = yes
guest ok = yesTo this:
> [vids]
path = /media/MEDIA/videos
writeable = yes
; browseable = yes
[COLOR=Blue]**force user = carleton**[/COLOR]
guest ok = yesThen restart samba:
```
sudo service smbd restart
```

---

### Post by carleton on 2011-10-31
Ahh, that did it. Many many thanks. I'm not sure why it wasn't working before, but I'm glad it is now.

---

### Post by dalban on 2012-03-08
Thanks. It worked for me.

**Systems:** Ubuntu 11.04  <--> Ubuntu 10.04 LTS

**On both systems:**
**sudo apt-get install smbfs**
[reboot the PC]

**I then followed the above advice:**
[add net bios name]
[add name resolve order]
[service restart]

I didn't have to force the user. Maybe because all the files were world readable.

---

