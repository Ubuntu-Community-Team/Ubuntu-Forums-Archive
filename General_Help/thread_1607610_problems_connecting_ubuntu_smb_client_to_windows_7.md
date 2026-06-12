---
title: "problems connecting ubuntu smb client to windows 7 server"
date: 2010-10-28
forum: General Help
---

### Post by jordanthompson on 2010-10-28
Hi all, I am trying to connect my ubuntu 10.10 client to my windows 7 file/print server.  I can browse to my windows network via places->network.  I can see my windows servers.  When I double click on them, I am prompted with username, domain, and password.  After I enter these, I am continually prompted for my password.  I know that I have my username/domain/password correct (I use them from other windows machines to connect.)

I have also tried to connect to a server with the following:
server: 192.168.1.5
share: Media (I know this exists with the appropriate capitalization)
folder: <blank>
user name: jordan
domain name: THOMPCO
(prompts for a password later, and I enter my password on the server)

Here is what I get from nmblookup:
```

jordan@surfer:~$ nmblookup -A 192.168.1.5
Looking up status of 192.168.1.5
	ANDREA          <00> -         B <ACTIVE> 
	THOMPCO         <00> - <GROUP> B <ACTIVE> 
	ANDREA          <20> -         B <ACTIVE> 
	THOMPCO         <1e> - <GROUP> B <ACTIVE> 

	MAC Address = 00-24-8C-63-5C-BA

```

```

jordan@surfer:~$ nmblookup andrea
querying andrea on 172.16.158.255
querying andrea on 192.168.1.255
192.168.1.5 andrea<00>
192.168.112.1 andrea<00>
192.168.171.1 andrea<00>

```

I made this fix on the windows 7 box (and rebooted it):
[http://ttcshelbyville.wordpress.com/2009/12/17/enable-netbios-over-tcpip/](http://ttcshelbyville.wordpress.com/2009/12/17/enable-netbios-over-tcpip/)

I tried this also:
> 
jordan@surfer:~$ smbclient -L 192.168.1.5 -Ujordan% -WTHOMPCO
Anonymous login successful
Domain=[THOMPCO] OS=[Windows 7 Professional 7600] Server=[Windows 7 Professional 6.1]

	Sharename       Type      Comment
	---------       ----      -------
Error returning browse list: NT_STATUS_ACCESS_DENIED
session request to 192.168.1.5 failed (Called name not present)
session request to 192 failed (Called name not present)
session request to *SMBSERVER failed (Called name not present)
NetBIOS over TCP disabled -- no workgroup available


Any help would be MOST welcome :)
Jordan

---

### Post by jordanthompson on 2010-10-29
:(

---

### Post by jordanthompson on 2010-10-31
:( :(

---

### Post by HermanAB on 2010-10-31
Howdy,

In my experience, the error messages returned by a Windows server tell you exactly what is wrong, if you can just figure out what exactly they mean...

Anonymous login successful:
Why does the Windows machine think you are logging in as Anonymous?

NT_STATUS_ACCESS_DENIED:
Anonymous does not have permission to access the share.

Sooooooo....
Are you sure that your user name is jordan and not JORDAN or Jordan or some such?


See this:
[http://www.aeronetworks.ca/howtos/LinuxActiveDirectory.html](http://www.aeronetworks.ca/howtos/LinuxActiveDirectory.html)

Note that Ubuntu ships with Likewise, which you can use instead of Samba winbind in the above howto.

---

### Post by Mark Phelps on 2010-10-31
Windows 7 is NOT a server OS, and in my own experience, is the WRONG OS to try to force into that role.

XP machines COULD be used as file servers (I am doing that myself) because they were a lot more flexible in permissions.

Win7, in contrast, has tightened up permissions so much that it is extremely hard to get it to function as a file server.

If you really want a file server, you would do better either (1) going back to XP, of (2) using a REAL server OS.

---

### Post by jordanthompson on 2010-10-31
Hi Herman,
thanks very much for your reply.

I am trying to connect to a windows 7 business machine that happens to be sharing some directories and printers.  I am not trying to connect to a specialized server of any kind.

I tried all of the combinations of my username I could think of, as you suggested.  I still get the same results.

I didn't think that Windows usernames and domains were case sensitive, but they may be on the unix side, for some reason.

If it is a clue, when I remote desktop to this machine, I need to use the machine name (andrea) instead of the workgroup name (thompco) for the domain.  Of course I have tried this :-(

Thanks for your help,
Jordan

---

### Post by jordanthompson on 2010-10-31
Sorry - looks like we doubled.

Unfortunately, that is what I have.  I may eventually change it to be an Ubuntu server, but I need to get my feet a lot more wet with this first ;-)

Windows 7 is fulfilling its role nicely for the other windows clients that communicate with it for now.  So it is what it is for now.

Are you saying that it is impossible for Ubuntu to communicate with Windows 7 in this fashion?

---

### Post by luvshines on 2010-10-31
Hi

Are you trying to list shares from Windows 7 machine anonymously ??
Make sure that you have enabled anonymous listing of shares from 'local security' settings in Win7

---

### Post by jordanthompson on 2010-10-31
No, I am trying to access the share(s) with my windows username/password/workgroup.  I am able to browse to the workgroup and see my server, but when I click on it, it asks for this info (which is what I would want and expect.)  Unfortunately I cannot log into the box with credentials I know are correct (because I use them from other windows boxes.)

I do not want to allow anonymous connections to my windows machines :-)

---

### Post by luvshines on 2010-10-31
Ok :)
I thought of anonymous after seeing this
> 
jordan@surfer:~$ smbclient -L 192.168.1.5 -Ujordan% -WTHOMPCO
Anonymous login successful...


Are you using Windows LIve Messenger on Win7 machine ?

There are bugs related to Windows Live Messenger and Samba
[https://bugs.launchpad.net/ubuntu/+s...ba/+bug/458637](https://bugs.launchpad.net/ubuntu/+s...ba/+bug/458637)
[http://social.technet.microsoft.com/...a-0d79a5597527](http://social.technet.microsoft.com/...a-0d79a5597527)
[https://bugzilla.samba.org/show_bug.cgi?id=7577](https://bugzilla.samba.org/show_bug.cgi?id=7577)

If you are using it, you may want to try accessing by uninstalling that from Win7 machine

---

### Post by marc_e_l on 2010-10-31
Hi,
Was having this same problem since Saturday: User name, workgroup and password but unable to have the shared media files.
Uninstalling Messenger solved for me the problem.
I guess I will have to wait that the Messenger related bug is solved till I can have it back

---

### Post by luvshines on 2010-10-31
> **marc_e_l said:**
> Hi,
Was having this same problem since Saturday: User name, workgroup and password but unable to have the shared media files.
Uninstalling Messenger solved for me the problem.
I guess I will have to wait that the Messenger related bug is solved till I can have it back

Well, Samba's bugzilla links says fixed in 3.5.x and patched in 3.4.x too
My Ubuntu 10.04 says:
```

dpkg -l | grep samba
ii  samba                                 2:3.4.7~dfsg-1ubuntu3.2                         SMB/CIFS file, print, and login server for Uni
ii  samba-common                          2:3.4.7~dfsg-1ubuntu3.2

```

I really don't understand 2:3.4.xx thing. Is Ubuntu still using 2.. something version or is it 3.4.x version

---

### Post by jordanthompson on 2010-10-31
Well... I removed Windows LIve Messenge and it made no difference :-( (I also rebooted the windows box for good measure!)
I still can't connect :-(

---

### Post by luvshines on 2010-10-31
Again going back to smbclient command, what does this say:
```

smbclient -I 192.168.1.5 -L THOMPCO -U<username>%<password>

```

---

### Post by jordanthompson on 2010-10-31
jordan@surfer:~$ smbclient -I 192.168.1.5 -L THOMPCO -Ujordan%mypassword
Connection to THOMPCO failed (Error NT_STATUS_BAD_NETWORK_NAME)
=================================================================
And trying it a little different:
jordan@surfer:~$ smbclient -L 192.168.1.5 -Ujordan% -Wthompco
Anonymous login successful
Domain=[THOMPCO] OS=[Windows 7 Professional 7600] Server=[Windows 7 Professional 6.1]

	Sharename       Type      Comment
	---------       ----      -------
Error returning browse list: NT_STATUS_ACCESS_DENIED
session request to 192.168.1.5 failed (Called name not present)
session request to 192 failed (Called name not present)
session request to *SMBSERVER failed (Called name not present)
NetBIOS over TCP disabled -- no workgroup available

=================================================================
and here is a twist using the netbios name:
jordan@surfer:~$ smbclient -L andrea -Ujordan% -Wthompco
Anonymous login successful
Domain=[THOMPCO] OS=[Windows 7 Professional 7600] Server=[Windows 7 Professional 6.1]

	Sharename       Type      Comment
	---------       ----      -------
Error returning browse list: NT_STATUS_ACCESS_DENIED
Anonymous login successful
Domain=[THOMPCO] OS=[Windows 7 Professional 7600] Server=[Windows 7 Professional 6.1]

	Server               Comment
	---------            -------
	ANDREA               

	Workgroup            Master
	---------            -------
	THOMPCO              ANDREA

=================================================================
Here it is with max debugging:
smbclient -L andrea -Ujordan% -Wthompco -d9
INFO: Current debug levels:
  all: True/9
  tdb: False/0
  printdrivers: False/0
  lanman: False/0
  smb: False/0
  rpc_parse: False/0
  rpc_srv: False/0
  rpc_cli: False/0
  passdb: False/0
  sam: False/0
  auth: False/0
  winbind: False/0
  vfs: False/0
  idmap: False/0
  quota: False/0
  acls: False/0
  locking: False/0
  msdfs: False/0
  dmapi: False/0
  registry: False/0
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
doing parameter workgroup = WORKGROUP
doing parameter server string = %h server (Samba, Ubuntu)
doing parameter dns proxy = no
doing parameter log file = /var/log/samba/log.%m
doing parameter max log size = 1000
doing parameter syslog = 0
doing parameter panic action = /usr/share/samba/panic-action %d
doing parameter encrypt passwords = true
doing parameter passdb backend = tdbsam
doing parameter obey pam restrictions = yes
doing parameter unix password sync = yes
doing parameter passwd program = /usr/bin/passwd %u
doing parameter passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\sp
assword:* %n\n *password\supdated\ssuccessfully* .
doing parameter pam password change = yes
doing parameter map to guest = bad user
doing parameter usershare allow guests = yes
pm_process() returned Yes
lp_servicenumber: couldn't find homes
Attempting to register new charset UCS-2LE
Registered charset UCS-2LE
Attempting to register new charset UTF-16LE
Registered charset UTF-16LE
Attempting to register new charset UCS-2BE
Registered charset UCS-2BE
Attempting to register new charset UTF-16BE
Registered charset UTF-16BE
Attempting to register new charset UTF8
Registered charset UTF8

Attempting to register new charset UTF-8
Registered charset UTF-8
Attempting to register new charset ASCII
Registered charset ASCII
Attempting to register new charset 646
Registered charset 646
Attempting to register new charset ISO-8859-1
Registered charset ISO-8859-1
Attempting to register new charset UCS2-HEX
Registered charset UCS2-HEX
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
added interface eth1 ip=fe80::21f:e1ff:fe8e:ab82%eth1 bcast=fe80::ffff:ffff:ffff
:ffff%eth1 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=fe80::221:70ff:fe7c:c83a%eth0 bcast=fe80::ffff:ffff:ffff
:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface vmnet1 ip=fe80::250:56ff:fec0:1%vmnet1 bcast=fe80::ffff:ffff:fff
f:ffff%vmnet1 netmask=ffff:ffff:ffff:ffff::
added interface vmnet8 ip=fe80::250:56ff:fec0:8%vmnet8 bcast=fe80::ffff:ffff:fff
f:ffff%vmnet8 netmask=ffff:ffff:ffff:ffff::
added interface vmnet1 ip=172.16.158.1 bcast=172.16.158.255 netmask=255.255.255.
0
added interface eth1 ip=192.168.1.109 bcast=192.168.1.255 netmask=255.255.255.0
added interface eth0 ip=192.168.1.111 bcast=192.168.1.255 netmask=255.255.255.0
added interface vmnet8 ip=192.168.206.1 bcast=192.168.206.255 netmask=255.255.25
5.0
Netbios name list:-
my_netbios_names[0]="SURFER"
Client started (version 3.5.4).
Opening cache file at /var/run/samba/gencache.tdb
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Perm
ission denied
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No s
uch file or directory
Attempt to open gencache.tdb has failed.
sitename_fetch: No stored sitename for 
Opening cache file at /var/run/samba/gencache.tdb
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Perm
ission denied
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No s
uch file or directory
Attempt to open gencache.tdb has failed.
no entry for andrea#20 found.

resolve_lmhosts: Attempting lmhosts lookup for name andrea<0x20>
startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file
 or directory
resolve_wins: Attempting wins lookup for name andrea<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name andrea<0x20>
resolve_hosts: getaddrinfo failed for name andrea [No address associated with ho
stname]
name_resolve_bcast: Attempting broadcast lookup for name andrea<0x20>
Socket options:
	SO_KEEPALIVE = 0
	SO_REUSEADDR = 1
	SO_BROADCAST = 1
	Could not test socket option TCP_NODELAY.
	Could not test socket option TCP_KEEPCNT.
	Could not test socket option TCP_KEEPIDLE.
	Could not test socket option TCP_KEEPINTVL.
	IPTOS_LOWDELAY = 0
	IPTOS_THROUGHPUT = 0
	SO_SNDBUF = 126976
	SO_RCVBUF = 126976
	SO_SNDLOWAT = 1
	SO_RCVLOWAT = 1
	SO_SNDTIMEO = 0
	SO_RCVTIMEO = 0
	Could not test socket option TCP_QUICKACK.
Sending a packet of len 50 to (172.16.158.255) on port 137
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No
 such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No
 such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No
 such file or directory
Sending a packet of len 50 to (172.16.158.255) on port 137
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No
 such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No
 such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No
 such file or directory
Sending a packet of len 50 to (172.16.158.255) on port 137
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No
 such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No
 such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No
 such file or directory
Sending a packet of len 50 to (192.168.1.255) on port 137
Received a packet of len 74 from (192.168.1.5) port 137
nmb packet from 192.168.1.5(137) header: id=461 opcode=Query(0) response=Yes
    header: flags: bcast=No rec_avail=No rec_des=Yes trunc=No auth=Yes
    header: rcode=0 qdcount=0 ancount=1 nscount=0 arcount=0
    answers: nmb_name=ANDREA<20> rr_type=32 rr_class=1 ttl=300000
    answers   0 char ..........p.....   hex 0000C0A801050000C0A870010000C0A8
    answers  10 char ..   hex AB01

Got a positive name query response from 192.168.1.5 ( 192.168.1.5 192.168.112.1 
192.168.171.1 )
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No
 such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No
 such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No
 such file or directory
namecache_store: storing 3 addresses for andrea#20: 192.168.1.5,192.168.112.1,19
2.168.171.1
Opening cache file at /var/run/samba/gencache.tdb
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Perm
ission denied
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No s
uch file or directory
Attempt to open gencache.tdb has failed.
Connecting to 192.168.1.5 at port 445
Socket options:
	SO_KEEPALIVE = 0
	SO_REUSEADDR = 0
	SO_BROADCAST = 0
	TCP_NODELAY = 1
	TCP_KEEPCNT = 9
	TCP_KEEPIDLE = 7200
	TCP_KEEPINTVL = 75
	IPTOS_LOWDELAY = 0
	IPTOS_THROUGHPUT = 0
	SO_SNDBUF = 16384
	SO_RCVBUF = 87380
	SO_SNDLOWAT = 1
	SO_RCVLOWAT = 1
	SO_SNDTIMEO = 0
	SO_RCVTIMEO = 0
	TCP_QUICKACK = 1
 session request ok
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Substituting charset 'UTF-8' for LOCALE
Doing spnego session setup (blob length=336)
SPNEGO login failed: Invalid parameter
Domain=[THOMPCO] OS=[Windows 7 Professional 7600] Server=[Windows 7 Professional
 6.1]
 session setup ok
 tconx ok

size=109
smb_com=0x25
smb_rcls=0
smb_reh=0
smb_err=0
smb_flg=8
smb_flg2=51201
smb_tid=2048
smb_pid=4633
smb_uid=2048
smb_mid=5
smt_wct=14
smb_vwv[ 0]=   19 (0x13)
smb_vwv[ 1]=    0 (0x0)
smb_vwv[ 2]= 1024 (0x400)
smb_vwv[ 3]=65504 (0xFFE0)
smb_vwv[ 4]=    0 (0x0)
smb_vwv[ 5]=    0 (0x0)
smb_vwv[ 6]=    0 (0x0)
smb_vwv[ 7]=    0 (0x0)
smb_vwv[ 8]=    0 (0x0)
smb_vwv[ 9]=   19 (0x13)
smb_vwv[10]=   90 (0x5A)
smb_vwv[11]=    0 (0x0)
smb_vwv[12]=  109 (0x6D)
smb_vwv[13]=    0 (0x0)
smb_bcc=46
write_socket(4,113)
write_socket(4,113) wrote 113
size=35
smb_com=0x25
smb_rcls=34
smb_reh=0
smb_err=49152
smb_flg=136
smb_flg2=51201
smb_tid=2048
smb_pid=4633
smb_uid=2048
smb_mid=5
smt_wct=0
smb_bcc=0
size=35
smb_com=0x25
smb_rcls=34
smb_reh=0
smb_err=49152
smb_flg=136
smb_flg2=51201
smb_tid=2048
smb_pid=4633
smb_uid=2048
smb_mid=5
smt_wct=0
smb_bcc=0

NetShareEnum failed
interpret_string_addr_internal: getaddrinfo failed for name andrea [No address a
ssociated with hostname]
interpret_addr: Unknown host. andrea
interpret_string_addr_internal: getaddrinfo failed for name andrea [No address a
ssociated with hostname]
write_socket(4,39)
write_socket(4,39) wrote 39
size=35
smb_com=0x71
smb_rcls=0
smb_reh=0
smb_err=0
smb_flg=136
smb_flg2=51201
smb_tid=2048
smb_pid=4633
smb_uid=2048
smb_mid=6
smt_wct=0
smb_bcc=0
Opening cache file at /var/run/samba/gencache.tdb
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Perm
ission denied
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No s
uch file or directory
Attempt to open gencache.tdb has failed.
sitename_fetch: No stored sitename for 
Opening cache file at /var/run/samba/gencache.tdb
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Perm
ission denied
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No s
uch file or directory
Attempt to open gencache.tdb has failed.
no entry for andrea#20 found.
resolve_lmhosts: Attempting lmhosts lookup for name andrea<0x20>
startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file
 or directory
resolve_wins: Attempting wins lookup for name andrea<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name andrea<0x20>
resolve_hosts: getaddrinfo failed for name andrea [No address associated with ho
stname]
name_resolve_bcast: Attempting broadcast lookup for name andrea<0x20>
Socket options:
	SO_KEEPALIVE = 0
	SO_REUSEADDR = 1
	SO_BROADCAST = 1
	Could not test socket option TCP_NODELAY.
	Could not test socket option TCP_KEEPCNT.
	Could not test socket option TCP_KEEPIDLE.
	Could not test socket option TCP_KEEPINTVL.
	IPTOS_LOWDELAY = 0
	IPTOS_THROUGHPUT = 0
	SO_SNDBUF = 126976

	SO_RCVBUF = 126976
	SO_SNDLOWAT = 1
	SO_RCVLOWAT = 1
	SO_SNDTIMEO = 0
	SO_RCVTIMEO = 0
	Could not test socket option TCP_QUICKACK.
Sending a packet of len 50 to (172.16.158.255) on port 137
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No
 such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No
 such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No
 such file or directory
Sending a packet of len 50 to (172.16.158.255) on port 137
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No
 such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No
 such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No
 such file or directory
Sending a packet of len 50 to (172.16.158.255) on port 137
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No
 such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No
 such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No
 such file or directory
Sending a packet of len 50 to (192.168.1.255) on port 137
Received a packet of len 74 from (192.168.1.5) port 137
nmb packet from 192.168.1.5(137) header: id=1310 opcode=Query(0) response=Yes
    header: flags: bcast=No rec_avail=No rec_des=Yes trunc=No auth=Yes
    header: rcode=0 qdcount=0 ancount=1 nscount=0 arcount=0
    answers: nmb_name=ANDREA<20> rr_type=32 rr_class=1 ttl=300000
    answers   0 char ..........p.....   hex 0000C0A801050000C0A870010000C0A8
    answers  10 char ..   hex AB01
Got a positive name query response from 192.168.1.5 ( 192.168.1.5 192.168.112.1 
192.168.171.1 )
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No
 such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No
 such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No
 such file or directory
namecache_store: storing 3 addresses for andrea#20: 192.168.1.5,192.168.112.1,19
2.168.171.1
Opening cache file at /var/run/samba/gencache.tdb
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Perm
ission denied
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No s
uch file or directory
Attempt to open gencache.tdb has failed.
Connecting to 192.168.1.5 at port 139
Socket options:
	SO_KEEPALIVE = 0
	SO_REUSEADDR = 0

	SO_BROADCAST = 0
	TCP_NODELAY = 1
	TCP_KEEPCNT = 9
	TCP_KEEPIDLE = 7200
	TCP_KEEPINTVL = 75
	IPTOS_LOWDELAY = 0
	IPTOS_THROUGHPUT = 0
	SO_SNDBUF = 16384
	SO_RCVBUF = 87380
	SO_SNDLOWAT = 1
	SO_RCVLOWAT = 1
	SO_SNDTIMEO = 0
	SO_RCVTIMEO = 0
	TCP_QUICKACK = 1
write_socket(4,72)
write_socket(4,72) wrote 72
Sent session request
size=0
smb_com=0x0
smb_rcls=0
smb_reh=0
smb_err=0
smb_flg=0
smb_flg2=0
smb_tid=0
smb_pid=0
smb_uid=0
smb_mid=0
smt_wct=0
smb_bcc=0
 session request ok
Doing spnego session setup (blob length=336)
SPNEGO login failed: Invalid parameter
Domain=[THOMPCO] OS=[Windows 7 Professional 7600] Server=[Windows 7 Professional
 6.1]
 session setup ok
 tconx ok
size=124
smb_com=0x25
smb_rcls=0
smb_reh=0
smb_err=0
smb_flg=8
smb_flg2=51201
smb_tid=2048
smb_pid=4633
smb_uid=2048
smb_mid=5
smt_wct=14
smb_vwv[ 0]=   34 (0x22)
smb_vwv[ 1]=    0 (0x0)
smb_vwv[ 2]=    8 (0x8)
smb_vwv[ 3]=65535 (0xFFFF)
smb_vwv[ 4]=    0 (0x0)
smb_vwv[ 5]=    0 (0x0)

smb_vwv[ 6]=    0 (0x0)
smb_vwv[ 7]=    0 (0x0)
smb_vwv[ 8]=    0 (0x0)
smb_vwv[ 9]=   34 (0x22)
smb_vwv[10]=   90 (0x5A)
smb_vwv[11]=    0 (0x0)
smb_vwv[12]=  124 (0x7C)
smb_vwv[13]=    0 (0x0)
smb_bcc=61
write_socket(4,128)
write_socket(4,128) wrote 128
size=91
smb_com=0x25
smb_rcls=0
smb_reh=0
smb_err=0
smb_flg=136
smb_flg2=51201
smb_tid=2048
smb_pid=4633
smb_uid=2048
smb_mid=5
smt_wct=10
smb_vwv[ 0]=    8 (0x8)
smb_vwv[ 1]=   27 (0x1B)
smb_vwv[ 2]=    0 (0x0)
smb_vwv[ 3]=    8 (0x8)
smb_vwv[ 4]=   56 (0x38)
smb_vwv[ 5]=    0 (0x0)
smb_vwv[ 6]=   27 (0x1B)
smb_vwv[ 7]=   64 (0x40)
smb_vwv[ 8]=    0 (0x0)
smb_vwv[ 9]=    0 (0x0)
smb_bcc=36
size=91
smb_com=0x25
smb_rcls=0
smb_reh=0
smb_err=0
smb_flg=136
smb_flg2=51201
smb_tid=2048
smb_pid=4633
smb_uid=2048
smb_mid=5
smt_wct=10
smb_vwv[ 0]=    8 (0x8)
smb_vwv[ 1]=   27 (0x1B)
smb_vwv[ 2]=    0 (0x0)
smb_vwv[ 3]=    8 (0x8)
smb_vwv[ 4]=   56 (0x38)
smb_vwv[ 5]=    0 (0x0)
smb_vwv[ 6]=   27 (0x1B)
smb_vwv[ 7]=   64 (0x40)
smb_vwv[ 8]=    0 (0x0)

smb_vwv[ 9]=    0 (0x0)
smb_bcc=36
size=124
smb_com=0x25
smb_rcls=0
smb_reh=0
smb_err=0
smb_flg=8
smb_flg2=51201
smb_tid=2048
smb_pid=4633
smb_uid=2048
smb_mid=6
smt_wct=14
smb_vwv[ 0]=   34 (0x22)
smb_vwv[ 1]=    0 (0x0)
smb_vwv[ 2]=    8 (0x8)
smb_vwv[ 3]=65535 (0xFFFF)
smb_vwv[ 4]=    0 (0x0)
smb_vwv[ 5]=    0 (0x0)
smb_vwv[ 6]=    0 (0x0)
smb_vwv[ 7]=    0 (0x0)
smb_vwv[ 8]=    0 (0x0)
smb_vwv[ 9]=   34 (0x22)
smb_vwv[10]=   90 (0x5A)
smb_vwv[11]=    0 (0x0)
smb_vwv[12]=  124 (0x7C)
smb_vwv[13]=    0 (0x0)
smb_bcc=61
write_socket(4,128)
write_socket(4,128) wrote 128
size=97
smb_com=0x25
smb_rcls=0
smb_reh=0
smb_err=0
smb_flg=136
smb_flg2=51201
smb_tid=2048
smb_pid=4633
smb_uid=2048
smb_mid=6
smt_wct=10
smb_vwv[ 0]=    8 (0x8)
smb_vwv[ 1]=   33 (0x21)
smb_vwv[ 2]=    0 (0x0)
smb_vwv[ 3]=    8 (0x8)
smb_vwv[ 4]=   56 (0x38)
smb_vwv[ 5]=    0 (0x0)
smb_vwv[ 6]=   33 (0x21)
smb_vwv[ 7]=   64 (0x40)
smb_vwv[ 8]=    0 (0x0)
smb_vwv[ 9]=    0 (0x0)
smb_bcc=42
size=97

smb_com=0x25
smb_rcls=0
smb_reh=0
smb_err=0
smb_flg=136
smb_flg2=51201
smb_tid=2048
smb_pid=4633
smb_uid=2048
smb_mid=6
smt_wct=10
smb_vwv[ 0]=    8 (0x8)
smb_vwv[ 1]=   33 (0x21)
smb_vwv[ 2]=    0 (0x0)
smb_vwv[ 3]=    8 (0x8)
smb_vwv[ 4]=   56 (0x38)
smb_vwv[ 5]=    0 (0x0)
smb_vwv[ 6]=   33 (0x21)
smb_vwv[ 7]=   64 (0x40)
smb_vwv[ 8]=    0 (0x0)
smb_vwv[ 9]=    0 (0x0)
smb_bcc=42
write_socket(4,39)
write_socket(4,39) wrote 39
size=35
smb_com=0x71
smb_rcls=0
smb_reh=0
smb_err=0
smb_flg=136
smb_flg2=51201
smb_tid=2048
smb_pid=4633
smb_uid=2048
smb_mid=7
smt_wct=0
smb_bcc=0
Anonymous login successful

	Sharename       Type      Comment
	---------       ----      -------
Error returning browse list: NT_STATUS_ACCESS_DENIED
Anonymous login successful

	Server               Comment
	---------            -------
	ANDREA               

	Workgroup            Master
	---------            -------
	THOMPCO              ANDREA

---

### Post by luvshines on 2010-11-01
Oh, OK!!

When you are using, smbclient -L andrea -Ujordan% -WTHOMPCO, you are not providing password after % and it goes for anonymous listing. If you provide password after %, see if you can list the shares

---

### Post by jordanthompson on 2010-11-01
And when I add a password I get this:
jordan@surfer:~$ smbclient -L andrea -Ujordan%myPassword -WTHOMPCO
session setup failed: SUCCESS - 0

---

### Post by jordanthompson on 2010-11-02
:( :( :(

---

### Post by luvshines on 2010-11-03
Maybe something is wrong with the password.
Can you reset the samba password for that user
```

smbpasswd <user-name>

```

---

### Post by jordanthompson on 2010-11-03
I tried several variations of smbpasswd (the first one makes sense because I am not sharing any smb shares):
jordan@surfer:~$ smbpasswd 
Old SMB password:
New SMB password:
Retype new SMB password:
Could not connect to machine 127.0.0.1: NT_STATUS_NO_SUCH_DOMAIN

==============================================================
jordan@surfer:~$ smbpasswd jordan
When run by root:
    smbpasswd [options] [username]
otherwise:
    smbpasswd [options]

options:
  -L                   local mode (must be first option)
  -h                   print this usage message
  -s                   use stdin for password prompt
  -c smb.conf file     Use the given path to the smb.conf file
  -D LEVEL             debug level
  -r MACHINE           remote machine
  -U USER              remote username
extra options when run by root or in local mode:
  -a                   add user
  -d                   disable user
  -e                   enable user
  -i                   interdomain trust account
  -m                   machine trust account
  -n                   set no password
  -W                   use stdin ldap admin password
  -w PASSWORD          ldap admin password
  -x                   delete user
  -R ORDER             name resolve order


==============================================================
jordan@surfer:~$ smbpasswd -r andrea
Old SMB password:
New SMB password:
Retype new SMB password:
Could not connect to machine andrea: SUCCESS - 0

==============================================================
jordan@surfer:~$ smbpasswd -r 192.168.1.5
Old SMB password:
New SMB password:
Retype new SMB password:
Could not connect to machine 192.168.1.5: SUCCESS - 0

==============================================================

I really appreciate your help and time...
Jordan

---

### Post by luvshines on 2010-11-03
Oops!! I totally forgot that it is Windows on the other side :)
smbpasswd won't run

Just as a sanity check, are you able to access Win7 share from the same windows machine with this username and password  ?

---

### Post by jordanthompson on 2010-11-03
Yup!  I can access the share(s) from other windows 7/Vista machines using the same username/password.  I was  curious why the connection window was filling in workgroup with "WORKGROUP" (which I would always change to "THOMPCO").  
I have changed the smb.cnf file so that the default workgroup is now "THOMPCO" so the window now automatically fills it in correctly (this was just an asside :-))

---

### Post by MarkHSte on 2010-11-04
I'm having a similar problem, we have a number of windows 7 PCs on our network, about half I can connect to and half I can't which would suggest a setting on windows 7, I've turned of the firewall and UAC and matched up the local security settings but still no luck, I've currently worked around the problem by using autofs to automatically mount the share.

---

### Post by luvshines on 2010-11-04
> **jordanthompson said:**
> And when I add a password I get this:
jordan@surfer:~$ smbclient -L andrea -Ujordan%myPassword -WTHOMPCO
session setup failed: SUCCESS - 0

:(, should not fail with password when it is successful without it.
Stumped !!
Can you run it with debug level 10 with password ?

---

### Post by MarkHSte on 2010-11-04
My PC was one of the Windows 7 PC's that was working, today windows update installed Windows Live Essentials 2011 and that stopped it from working, removing messanger didn't resolve the problem I had to remove all of the Live Essential pakages before linux would connect to my machine.

---

### Post by Mark Phelps on 2010-11-04
> **MarkHSte said:**
> ... I had to remove all of the Live Essential pakages before linux would connect to my machine.

Do you WANT the Win7 machines to become infested with malware and viruses?  You've essentially disabled everything in Win7 that prevents that very thing from happening!

---

### Post by MarkHSte on 2010-11-04
> **Mark Phelps said:**
> Do you WANT the Win7 machines to become infested with malware and viruses? You've essentially disabled everything in Win7 that prevents that very thing from happening!
 
No I haven't windows live essentials 2011 includes the following packages 
 
messenger, photo gallery, movie maker, windows live mesh, writer, family safty, mail, messenger companion, bing bar, outlook connector pack and silverlight.
 
[http://explore.live.com/windows-live-essentials?os=other](http://explore.live.com/windows-live-essentials?os=other)
 
 
none of these stop viruses or spyware and even if they did I've still got my none ms antivirus package to protect me.

---

### Post by Drisanna on 2010-11-04
I too had to remove Live Essentials 2011 to be able to access my shared Win7 drives/directories from my Ubuntu to machine.  Prior to the release of the 2011 version, it was possible to just uninstall some little sub-part about "login assistant" or some such, and the rest of the Essentials would work fine.  

Sadly, this no longer seems to be the case.

---

### Post by jordanthompson on 2010-11-04
**[COLOR="Red"]Yeah baby[/COLOR]**!  That did it!  I can now easily access my windoze 7 files and printers.  Thanks a bunch!:P:P:P

---

### Post by luvshines on 2010-11-05
> **jordanthompson said:**
> **[COLOR="Red"]Yeah baby[/COLOR]**!  That did it!  I can now easily access my windoze 7 files and printers.  Thanks a bunch!:P:P:P

Glad that your issue is resolved :)

Don't know why Win7 is installing more and more s/w's which is breaking Samba sharing

---

### Post by seahag on 2010-11-08
I have a Win7 PC that was working find when samba used print command to Win7 PC.   After installing Microsoft Live Essential it stopped working.
I uninstall the entire package, rebooted and it now works!

What is Windows Live doing that would cause this conflict?

---

### Post by luvshines on 2010-11-08
> **seahag said:**
> I have a Win7 PC that was working find when samba used print command to Win7 PC.   After installing Microsoft Live Essential it stopped working.
I uninstall the entire package, rebooted and it now works!

What is Windows Live doing that would cause this conflict?

There are bugs related to Windows Live Messenger and Samba
[https://bugs.launchpad.net/ubuntu/+s...ba/+bug/458637](https://bugs.launchpad.net/ubuntu/+s...ba/+bug/458637)
[http://social.technet.microsoft.com/...a-0d79a5597527](http://social.technet.microsoft.com/...a-0d79a5597527)
[https://bugzilla.samba.org/show_bug.cgi?id=7577](https://bugzilla.samba.org/show_bug.cgi?id=7577)

---

### Post by xmasm1 on 2011-08-30
In my case I gave up, guys, with trying to access default shares C$ etc. I have got always 
tree connect failed: NT_STATUS_ACCESS_DENIED
Even with valid administrator username and password and no errors in smbclient -d9 debug mode. 

After set up share on Windows with another name - e.g. "C" together with default "C$" finally I am able to access the whole disk and BackupPC can backup this freeking Windows 7.

Life would be so sweet without killing time with bugs and incompatibilities like this one.

---

