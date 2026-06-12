---
title: "TSCOKS/Tunneling"
date: 2011-04-20
forum: General Help
---

### Post by Dubslow on 2011-04-20
THE TITLE IS A TYPO: TSOCKS, NOT TSCOKS
TSOCKS, NOT TSCOKS

Hey guys,
I'm at a school with most ports blocked/various other protections on the network. I would like to tunnel to Steam. Our Advanced Computing Association club has multiple servers in a so-called DMZ, with no port blocks and the like. I asked an ACA member how to tunnel, and he said ssh to an ACA server and then use tsocks to send a connection through the tunnel. Currently I do the following:

ssh -D 9999 [email]dubslow@sand5.aca[/email].[hostname] 

in one terminal, which works fine, then Ctrl+Shft+T to another terminal and run

tsocks

which "resets" the terminal, as in runs all the bash startup commands again. From what my friend and the tsocks manual say, that's just tsocks applying its settings. So after 'tsocks' and the terminal resetting, I use


wine C:\\\Program\ Files\\Steam\\Steam.exe

except that it still acts like it's not getting the internet. [COLOR="Red"]I can't think of any way to test the internet[/COLOR], because 'ping' in general does not work on campus, even from the server in the DMZ. [COLOR="Red"]EDIT: I just tried installing elinks via apt-get from the tsocks'ed terminal, and it worked fine, so I think I'm using tsocks wrong.[/COLOR]

In my tsocks.conf, I have the following:

server = 127.0.0.1
server_type = 5
server_port = 9999

All I can think of is that I'm using tsocks wrong, but going through the manual and tsocks.conf manual hasn't helped. I know it's possible because my friend can do it, although I can't ask him for help because he has since rescinded his permission for me tunneling, and doesn't not know that I still am. (I have approval from other ACA members with root to tunnel.)

---

### Post by iponeverything on 2011-04-20
This should be an ACA initiation for acceptance.. Either that or drop the first A ;)

---

### Post by Dubslow on 2011-04-20
I'm not a member, just trying to tap the resources to Steam linux. (Any of the members could easily destroy me computer-wise.) I got the tunnel working fine in Windows with putty and proxifier, but tsocks hates me apparently.

---

### Post by OscarTango on 2011-04-20
Verify that you commented out the Path example in /etc/tsocks.conf and pick a bind port greater than 10000, i.e. 19999. If your syntax still won't work, consider altering it like this:

with-tsocks --server=username@somedomain --forward-port=19999 wine C:\\etc

---

### Post by Dubslow on 2011-04-20
In windows the port is 9999, and my unhelpful friend uses 2000. Admittedly, I hadn't commented out the path example because it was irrelevant. I'll let you know when I test it; I am currently in Windows for Portal 2 :).

---

### Post by Dubslow on 2011-05-03
Still doesn't work. Everything is commented out except 

server = 127.0.0.1
server_type = 5
server_port = 9999

This is the error when I try and run steam:

ERROR: ld.so: object '/usr/lib/libtsocks.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libtsocks.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libtsocks.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libtsocks.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libtsocks.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libtsocks.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libtsocks.so' from LD_PRELOAD cannot be preloaded: ignored.
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:win:RegisterDeviceNotificationA (hwnd=0x129510, filter=0x73e9d4,flags=0x00000001) returns a fake device notification handle!
ERROR: ld.so: object '/usr/lib/libtsocks.so' from LD_PRELOAD cannot be preloaded: ignored.
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:advapi:RegisterEventSourceW ((null),L"Bonjour Service"): stub
ERROR: ld.so: object '/usr/lib/libtsocks.so' from LD_PRELOAD cannot be preloaded: ignored.
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:winsock:WS_setsockopt Unknown IPPROTO_IP optname 0x00000013
fixme:winsock:WSAIoctl SIO_GET_EXTENSION_FUNCTION_POINTER: unimplemented WSARecvMsg
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:winsock:WS_setsockopt Unknown IPPROTO_IPV6 optname 0x00000013
fixme:winsock:WSAIoctl SIO_GET_EXTENSION_FUNCTION_POINTER: unimplemented WSARecvMsg
fixme:winsock:WSAIoctl -> SIO_ADDRESS_LIST_CHANGE request: stub
fixme:service:EnumServicesStatusW 0x12dc18 type=30 state=3 (nil) 0 0x78e7e8 0x78e7f4 0x78e7f0
fixme:advapi:ReportEventA (0xcafe4242,0x0004,0x0000,0x00000064,(nil),0x0001,0x00000000,0x78e5f8,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x00000064,(nil),0x0001,0x00000000,0x129130,(nil)): stub
fixme:netapi32:NetGetJoinInformation Stub (null) 0x78e688 0x78e690
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:winsock:WS_setsockopt Unknown IPPROTO_IP optname 0x00000013
fixme:winsock:WSAIoctl SIO_GET_EXTENSION_FUNCTION_POINTER: unimplemented WSARecvMsg
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:winsock:WS_setsockopt Unknown IPPROTO_IPV6 optname 0x00000013
fixme:winsock:WSAIoctl SIO_GET_EXTENSION_FUNCTION_POINTER: unimplemented WSARecvMsg
ERROR: ld.so: object '/usr/lib/libtsocks.so' from LD_PRELOAD cannot be preloaded: ignored.

Any other ideas?

(Still on maverick)

---

