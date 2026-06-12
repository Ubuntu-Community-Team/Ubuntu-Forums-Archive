---
title: "Ubuntu and Mac OS X"
date: 2006-05-04
forum: General Help
---

### Post by Black.Solaris on 2006-05-04
Well, I just picked up a new Mac iBook G4 yesterday, and I was wondering how in the world I can network it with my Ubuntu box.  I'm kind of a network newbie, so please go slow!  I was able to transfer some files to my laptop by accessing it via FTP, but I would like to be able to trade files back to my Ubuntu box, and something faster than FTP would be nice.

Thanks!

---

### Post by louis_nichols on 2006-05-04
Well... it seems ironic that in sharing files between a Linux box and a Mac box, the best way to go seems to be the windows file-sharing technology. This is implemented both in Linux and mac via a package called samba.

[Here]("https://wiki.ubuntu.com/SettingUpSamba?highlight=%28samba%29") is how you set it up in Ubuntu. A quick google for "mac osx samba" (without quotes) also returned this: [http://homepage.mac.com/william_white/smbdoc.html](http://homepage.mac.com/william_white/smbdoc.html)

---

### Post by Black.Solaris on 2006-05-05
With a little bit of playing around, I was able to access my iBook from Ubuntu using Samba; however, whenever I try to access Ubuntu from my iBook, Finder simply stops responding.  Any ideas?

Thanks.

---

### Post by louis_nichols on 2006-05-05
Sorry, I've never used samba, either on Linux or Mac (I've actually never seen a Mac). I just know it should work, quite well, even. I read it on forums.

Try googling for howtos, tutorials, for keywords of the same symtoms you are getting. You are certainly not the first to have such a problem, so somewhere on a forum or a discussion list (or more of them) you should find solutions.

---

### Post by Black.Solaris on 2006-05-05
Alright, will do.  Thanks for your help.

---

### Post by louis_nichols on 2006-05-05
[QUOTE=Black.Solaris]Alright, will do.  Thanks for your help.[/QUOTE]

you're quite wellcome! Please let us know how this works out!

---

### Post by intel on 2006-05-05
On Mac
Click Go>Connect to server
(from the top menubar)

put in

smb://a.b.c.d/

a.b.c.d is the machine (linux) you are trying to connect to

intel

---

### Post by z_diver on 2006-05-05
[quote=Black.Solaris]With a little bit of playing around, I was able to access my iBook from Ubuntu using Samba; however, whenever I try to access Ubuntu from my iBook, Finder simply stops responding.  Any ideas?
[/quote] 
Have you setup Samba server on your Ubuntu machine?  The Shared Folders applet under System > Administration is OK for some tasks but, at least on Breezy, it does not allow you to setup passwords.  The guide below should provide this "howto" and more. I'd recommend bookmarking the main page - it has a ton of handy Ubuntu tricks. :D

[http://easylinux.info/wiki/Ubuntu#Samba_Server]("http://easylinux.info/wiki/Ubuntu#Samba_Server")

Edit: [COLOR=Green]Helpful hint-- Highlight the commands given on that webpage and then paste them into the terminal using center click.  Makes short work of even difficult tasks.[/COLOR]

---

### Post by mcook2 on 2007-05-06
I had various problems with this, but seem to have resolved them as follows:

1) Environment is as follows:

- Samba on Ubuntu Desktop 7.04 "Feisty Faun"
- OSX 10.4.9 with latest security fix as of 2007-05-05

I didn't have any problems accessing my OSX shares from Ubuntu.  In fact when browsing the Windows network from Ubuntu I seem to get an extra folder with the name of the OSX host and it contains the entire contents of the OSX HD!  

2) First, as with Windows file sharing generally, I find I need to be using the same usernames and passwords on both systems, so I made sure this was so.

3) Examination of the sample /etc/smb.conf file reveals that Samba/Ubuntu-Feisty wants to use smbpasswd, so you have to run this one time to create the smbpasswd file.  As root:

```
mksmbpasswd /bin/cat /etc/passwd  |  /usr/sbin/mksmbpasswd  > /etc/samba/smbpasswd
```

3) This disables all the users in the target file, so enable the user(s) you want to be able to access shares. As root, run:

```
smbpasswd -e username
```

Users can run smbpasswd themselves to update their passwords from here on. 

4) By this time you have set up a Ubuntu share, say /tmp/Public. I also set up my smb.conf to share home directories, and my working smb.conf file is either listed at the end of this post or you can find it at [http://skyprod.net/~mcook/Ubuntu/smb.conf.txt]("http://skyprod.net/~mcook/Ubuntu/smb.conf.txt"). For completeness, I put the OSX file here: [http://skyprod.net/~mcook/OSX/smb.conf.txt]("http://skyprod.net/~mcook/OSX/smb.conf.txt")

5) The things I seem to have changed in Ubuntu Desktop's default smb.conf are as follows:

In sections Global and Networking:

- added "allow hosts = "...
- changed workgroup name (Vista now uses "Workgroup" instead of MSHOME, by the way)
- added "wins support = yes" (I also removed a line "wins support = no" that I found way down the file).
- notice that I forgot to uncomment my modified "interfaces" line but the default should be fine in most cases.  

In section Authentication:

- uncommented "security = user"
- note that "encrypt passwords = true" is the default 
- added my "valid users = " ...

In section Share Definitions:

- uncommented the [homes] section and modified it the way I usually want it (browsable, writable, and so on).  You might want to tweak create and directory masks.
- added my [Public] section.

6) Exciting error message I encountered along the way:

- the OSX "delete alias" symptom at various times
- on OSX, the expected messages that you do not have permission while smbpasswd is not yet set up on Ubuntu. 
- "file item not found" on OSX  when trying to connect to a share that was defined in smb.conf on the Ubuntu system but didn't actually exist ;-)

Most of the useful error messages were in Ubuntu's nmbd log, for example:  

[2007/05/05 00:03:37, 0] nmbd/nmbd_namequery.c:query_name_response(109)
  query_name_response: Multiple (2) responses received for a query on subnet 192.168.2.107 for name WORKGROUP<1d>.
  This response was from IP 192.168.2.106, reporting an IP address of 192.168.2.100.

             -- I had left my Airport turned on by mistake 

[2007/05/05 01:28:14, 0] nmbd/nmbd_workgroupdb.c:dump_workgroups(282)
  dump_workgroups()
   dump workgroup on subnet   192.168.2.107: netmask=  255.255.255.0:
        WORKGROUP(1) current master browser = MONA
                BERTHA 40819a03 (bertha server (Samba, Ubuntu))
                MONA 40049a03 (mona)
[2007/05/05 01:28:14, 0] nmbd/nmbd_browsesync.c:collect_all_workgroup_names_from_wins_server(586)
  collect_all_workgroup_names_from_wins_server:
  Cannot find my workgroup WORKGROUP on subnet UNICAST_SUBNET.

		- Not sure what happened above

[2007/05/05 01:28:33, 0] lib/util.c:smb_panic(1599)
  PANIC (pid 6347): internal error
[2007/05/05 01:28:33, 0] lib/util.c:log_stack_trace(1706)
  BACKTRACE: 9 stack frames:
   #0 nmbd(log_stack_trace+0x1a) [0x497d2a]
   #1 nmbd(smb_panic+0x34) [0x497e04]
   #2 nmbd [0x48678b]
   #3 /lib/libc.so.6 [0x2b447d049d40]
   #4 nmbd(tdb_traverse+0x17) [0x4abd87]
   #5 nmbd(initiate_wins_processing+0x5a) [0x43a03a]
   #6 nmbd(main+0x756) [0x425cf6]
   #7 /lib/libc.so.6(__libc_start_main+0xf4) [0x2b447d0368e4]
   #8 nmbd [0x424579]
[2007/05/05 01:28:33, 0] lib/util.c:smb_panic(1607)
  smb_panic(): calling panic action [/usr/share/samba/panic-action 6347]
[2007/05/05 01:28:33, 0] lib/util.c:smb_panic(1615)
  smb_panic(): action returned status 0
[2007/05/05 01:28:33, 0] lib/fault.c:dump_core(173)
  dumping core in /var/log/samba/cores/nmbd

		- Above from trying to run smbpasswd on user guest while logged in as user mcook

From Ubuntu's Samba log for the OSX host: 

[2007/05/05 22:04:19, 0] smbd/service.c:make_connection_snum(849)
  Can't become connected user!

[2007/05/06 00:05:58, 0] smbd/service.c:make_connection_snum(920)
  '/tmp/Public' does not exist or permission denied when connecting to [Public] Error was No such file or directory

First indication it was working for OSX was when I got this on OSX:

mona:~ mcook$ smbclient -NL 192.168.2.107
Anonymous login successful
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.0.24]

        Sharename       Type      Comment
        ---------       ----      -------
        IPC$            IPC       IPC Service (bertha server (Samba, Ubuntu))
        Public          Disk      
        print$          Disk      Printer Drivers
        homes           Disk      Home Directories
Anonymous login successful
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.0.24]

        Server               Comment
        ---------            -------
        BERTHA               bertha server (Samba, Ubuntu)
        MONA                 mona

        Workgroup            Master
        ---------            -------
        WORKGROUP            MONA

I still need to fine-tune my create and directory masks in smb.conf.

7) I find short Applescripts such as the following are useful when working on this on OSX:

To mount shares:

```
mount volume "cifs://WORKGROUP;MCOOK@BERTHA/PUBLIC"
```

or:

```
mount volume "smb://WORKGROUP;MCOOK@BERTHA/HOMES"
```

To unmount a share after checking folder names in /Volumes on OSX:

```
tell application "Finder"
	if exists (disk "ALOISE-U-PUBLIC") then eject "ALOISE-U-PUBLIC"
end tell
```

This illustrates one reason why share names that include the hostname are more useful.

[The End]

---

### Post by ign on 2007-08-26
i'm trying the same kind of thing and was able to make it work by carefully reading this how to:
[http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/1](http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/1)
i hope it works for you.

edit: there is another howto here [http://rubbervir.us/projects/ubuntu_media_server/](http://rubbervir.us/projects/ubuntu_media_server/)

---

