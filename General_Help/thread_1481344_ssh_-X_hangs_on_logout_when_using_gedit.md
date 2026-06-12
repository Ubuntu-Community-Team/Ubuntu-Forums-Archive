---
title: "ssh -X hangs on logout when using gedit"
date: 2010-05-12
forum: General Help
---

### Post by archknight on 2010-05-12
I am using Lucid and am having a problem logging out of a ssh -X connection after I had forwarded an X window during it. I don't know if this is the proper place to be posting such a problem but I can think of nowhere else. Please feel free to redirect me elsewhere. 

At google's suggestion, I tried redirecting the pipes but that didn't help. I am not sure this helps but I did a verbose output of an example ssh session. I login, open a window, close it without doing anything, and then attempt to logout. It hangs which forces me to use ^c on it. What is going on here? How can I fix this?

bash-3.00$ ssh -v username@host_address
Sun_SSH_1.1, SSH protocols 1.5/2.0, OpenSSL 0x0090704f
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Rhosts Authentication disabled, originating port will not be trusted.
debug1: ssh_connect: needpriv 0
debug1: Connecting to host_address [host_address] port 22.
debug1: Connection established.
debug1: identity file /home/dbjohns1/.ssh/identity type -1
debug1: identity file /home/dbjohns1/.ssh/id_rsa type -1
debug1: identity file /home/dbjohns1/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.3p1 Debian-3ubuntu3
debug1: match: OpenSSH_5.3p1 Debian-3ubuntu3 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-Sun_SSH_1.1
debug1: Failed to acquire GSS-API credentials for any mechanisms (No credentials were supplied, or the credentials were unavailable or inaccessible
Unknown code 0
)
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5 none
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: Peer sent proposed langtags, ctos: 
debug1: Peer sent proposed langtags, stoc: 
debug1: We proposed langtags, ctos: i-default
debug1: We proposed langtags, stoc: i-default
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: dh_gen_key: priv key bits set: 126/256
debug1: bits set: 1034/2048
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'host_address' is known and matches the RSA host key.
debug1: Found key in /home/username/.ssh/known_hosts:4
debug1: bits set: 1027/2048
debug1: ssh_rsa_verify: signature correct
debug1: newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: done: ssh_kex2.
debug1: send SSH2_MSG_SERVICE_REQUEST
debug1: got SSH2_MSG_SERVICE_ACCEPT
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /home/username/.ssh/identity
debug1: Trying private key: /home/username/.ssh/id_rsa
debug1: Trying private key: /home/username/.ssh/id_dsa
debug1: Next authentication method: password
username@host_address's password: 
debug1: Authentication succeeded (password)
debug1: channel 0: new [client-session]
debug1: send channel open 0
debug1: Entering interactive session.
debug1: ssh_session2_setup: id 0
debug1: channel request 0: pty-req
debug1: Requesting X11 forwarding with authentication spoofing.
debug1: channel request 0: x11-req
debug1: channel request 0: shell
debug1: fd 6 setting TCP_NODELAY
debug1: channel 0: open confirm rwindow 0 rmax 32768
Linux host 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 x86_64 GNU/Linux
Ubuntu 10.04 LTS

Welcome to Ubuntu!
 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

username@host:~$ gedit 1> /dev/null 2> /dev/null 0< /dev/null &
debug1: client_input_channel_open: ctype x11 rchan 3 win 65536 max 16384
debug1: client_request_x11: request from 127.0.0.1 47400
debug1: fd 10 setting TCP_NODELAY
debug1: fd 10 setting O_NONBLOCK
debug1: channel 1: new [x11]
debug1: confirm x11

[1] 19443
dbj@physdawg:~$ 
debug1: client_input_channel_open: ctype x11 rchan 4 win 65536 max 16384
debug1: client_request_x11: request from 127.0.0.1 47401
debug1: fd 11 setting TCP_NODELAY
debug1: fd 11 setting O_NONBLOCK
debug1: channel 2: new [x11]
debug1: confirm x11
debug1: client_input_channel_open: ctype x11 rchan 5 win 65536 max 16384
debug1: client_request_x11: request from 127.0.0.1 47402
debug1: fd 12 setting TCP_NODELAY
debug1: fd 12 setting O_NONBLOCK
debug1: channel 3: new [x11]
debug1: confirm x11
debug1: channel 1: rcvd eof
debug1: channel 1: output open -> drain
debug1: channel 1: obuf empty
debug1: channel 1: close_write
debug1: channel 1: output drain -> closed
debug1: channel 1: FORCE input drain
debug1: channel 1: ibuf empty
debug1: channel 1: send eof
debug1: channel 1: input drain -> closed
debug1: channel 1: send close
debug1: channel 1: rcvd close
debug1: channel 1: is dead
debug1: channel 1: garbage collecting
debug1: channel_free: channel 1: x11, nchannels 4

[1]+  Done                    gedit > /dev/null 2> /dev/null < /dev/null
username@host:~$ logout
debug1: client_input_channel_req: channel 0 rtype exit-status reply 0
debug1: channel 0: rcvd eof
debug1: channel 0: output open -> drain
debug1: channel 0: rcvd close
debug1: channel 0: close_read
debug1: channel 0: input open -> closed
debug1: channel 0: obuf empty
debug1: channel 0: close_write
debug1: channel 0: output drain -> closed
debug1: channel 0: almost dead
debug1: channel 0: gc: notify user
debug1: channel 0: gc: user detached
debug1: channel 0: send close
debug1: channel 0: is dead
debug1: channel 0: garbage collecting
debug1: channel_free: channel 0: client-session, nchannels 3

*** It hangs at this point so I do a ctrl + c ***

^Cdebug1: channel_free: channel 2: x11, nchannels 2
debug1: channel_free: channel 3: x11, nchannels 1
Killed by signal 2.
debug1: Calling cleanup 0x806501c(0x0)
debug1: Calling cleanup 0x8070bdc(0x0)

---

### Post by archknight on 2010-05-12
Can I get any help with this problem? Should I post in a different forum or something? Any input would be greatly appreciated. Thanks in advance!

---

### Post by archknight on 2010-05-13
Can I please get some help on this? Perhaps merely a finger pointing in the correct direction? I would appreciate hints, riddles, cryptic clues, treasure maps, or old legends that may possibly pertain to this problem.

---

### Post by archknight on 2010-05-14
*bump*

---

### Post by archknight on 2010-05-15
How many days must this post be up on the forums before somebody posts a reply?

---

### Post by Snow986 on 2010-05-15
I'll give it a whirl... Have you tried using ssh -Y instead of -X.  Could be a security thing.  Also can you check for log messages.  I think they are in /var/log/messages.  Try

```

sudo grep -ir ssh /var/log/messages

```
or
```

sudo cat /var/log/messages | grep ssh 

```

EDIT:  it might be in /var/log/syslog ...

---

### Post by archknight on 2010-05-16
Thank you so much for replying!!! Unfortunately, it doesn't matter if I use -X or -Y, it hangs. I went through both logs and they have no errors in them that I can relate to this problem. What is going on here? It just makes no sense. Am I doing something wrong?

---

### Post by Snow986 on 2010-05-16
You say that you are having the issue with gedit...  A few things I would try.  Try sshing in without X11 and just run terminal emacs and close and exit.  It almost looks like this is a problem on your side and has nothing to do with X11 forwarding (maybe?).  If this works and doesn't hang then try with ssh -X or ssh -Y and try to run a different X program.  The way the debugger is showing, it looks like it is exiting correctly to me and that the problem may be with your ssh config on the local machine.  But first confirm there are no issues without using X forwarding.  Also, how far away is the remote machine.  X11 wasn't designed for far away use. (say intercontinental or even cross country).  Its just too slow.

---

### Post by archknight on 2010-05-17
Thanks again for replying. Actually, the host is behind a firewall so I am unable to access it directly. Instead, I have to connect to another server (server A) that is available outside the firewall and then SSH into the host computer of interest (server B). Server A is a sunOS machine. X forwarding works fine with it (remote into A, open X Window, close it, logout, no problems). So, from server A, I connect to server B, which is running ubuntu. If I don't open up any X windows, it disconnects just fine. Both sever A and server B are on the same network (same subnet even) and are in buildings that are physically right next to each other. 

So, thinking that it might be an issue with having multiple forwarding, from server A I connect to a 3rd server (server C), which is a red hat server in the same room. I open up a program like gedit on it, it gets forwarded just fine. I close it, log out, and there are no problems. When I try connecting to server A to server C then to server B, when I open an X Window, it hangs when logging out of server B. In fact, there are a bunch of red hat servers that I can reach (servers D-F) and they all work fine no matter how I connect through them. However, when I open up an X window on server B, I cannot log out. Tomorrow, I can try going to the building behind the firewall and connecting directly with a windows PC (XP sp2) using putty and see if that will work but I have feeling that it won't.

---

### Post by Snow986 on 2010-05-17
Yeah, it definitely sounds like there is an issue doing the double X forwarding.  I think you will need physical access to do further debugging.  Are there no other servers that run the same OS as the desired machine that you can ssh into instead of the Sun machine?

---

### Post by archknight on 2010-05-18
Perhaps, I was unclear. I was explaining that the multiple forwarding isn't an issue. I can connect to ten different servers, forwarding X windows through all of them, and then be able to log out without problems. The only problem occurs when I log into the ubuntu machine last. I can open the X Window program easily enough, but it hangs on logout afterward. I physically went down there and hopped onto a nearby Windows XP machine. I logged in with Putty, forwarded the X Windows, opened gedit, had it it open on my computer, closed it, logged out, and it still hanged. There was absolutely ZERO multiple forwarding with that. I can't possibly come up with anymore ways to connect to this computer. It fails no matter how I approach it. So I don't see how it is possible to say it is anything but something weird going on with Ubuntu.

What further debugging do I need to do? I have root access on the Ubuntu machine but not on any of the other servers. I also don't have admin access on the nearby windows machines. I can go to the ubuntu machine itself, but since it was a problem with X Window forwarding, there is nothing I can test by going down there in person.

---

### Post by Snow986 on 2010-05-18
Ahh, I see now.  Yes I agree must be the ubuntu machine.  Maybe try reinstalling X on it?  Have you checked the system logs on the ubuntu machine or just the one you are sshing from?

---

### Post by archknight on 2010-05-18
I have checked the logs on the Ubuntu machine. There is nothing interesting in there. Is there something in particular that I should be looking for? This is a new Ubuntu install so I am doubtful that reinstalling anything will help.

So, before I tried opening firefox and it still hanged on logout. However, recently I tried opening an xterm and it didn't hang on logout. So, I figure I should try a bunch of different programs and see if that mattered. No matter how many times I try it, emacs, ddd, and xterm don't cause it to hang on logout while firefox, gedit, and all gnome programs that I decided to test (gnome-system-monitor, gcalctool, and gnomine) do cause it to hang. It doesn't matter how I redirect pipes or if I use nohup.

---

### Post by Snow986 on 2010-05-18
Do you know what graphics card is in the ubuntu machine?  I ran into an interesting graphics issue with ATI card with my new install of 10.04 on one of my boxes that I use X forwarding on all the time.  Its starting to sound like more of a graphics issue than anything else. Also what version ubuntu is it?

As for the logs, anything with ssh errors or X11 errors may be pertinent.

check /var/log/Xorg.0.log also.

---

### Post by archknight on 2010-05-18
Thanks so much for taking the time to help with this. I really do appreciate it.

Sorry, but I got an nvidia card in there, a Quadro NVS 295. I am running 64bit Ubuntu 10.04 Lucid Lynx. 

I went through the logs again and found nothing related to either of those. This being a new system, there isn't much in them yet.

---

### Post by Snow986 on 2010-05-18
No problem, this has me quite interested as I am always using X forwarding :).  There is one more log you could see if its been created.  It is /home/<username>/.xsession-errors .  Are you using proprietary drivers?  Also could you do an ssh in verbose using -Y and post the output.  Hopefully we can figure this out...  Thanks

---

### Post by archknight on 2010-05-18
Unfortunately, no error file is created in my home directory when I ssh in and have it hang when logging out. Yes, I am using a proprietary nvidia driver for the graphics card but only that one. In my original post, I did a verbose for -X. However, I will do it again with -Y.

>ssh -v -Y USER@IP_ADDRESS
OpenSSH_4.3p2, OpenSSL 0.9.8b 04 May 2006
debug1: Reading configuration data /home/USER/.ssh/config
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to IP_ADDRESS [IP_ADDRESS] port 22.
debug1: Connection established.
debug1: identity file /home/USER/.ssh/identity type -1
debug1: identity file /home/USER/.ssh/id_rsa type 1
debug1: identity file /home/USER/.ssh/id_dsa type -1
debug1: loaded 3 keys
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.3p1 Debian-3ubuntu3
debug1: match: OpenSSH_5.3p1 Debian-3ubuntu3 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.3
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'IP_ADDRESS' is known and matches the RSA host key.
debug1: Found key in /home/USER/.ssh/known_hosts:33
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /home/USER/.ssh/identity
debug1: Offering public key: /home/USER/.ssh/id_rsa
debug1: Authentications that can continue: publickey,password
debug1: Trying private key: /home/USER/.ssh/id_dsa
debug1: Next authentication method: password
USER@IP_ADDRESS's password: 
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug1: Entering interactive session.
debug1: Requesting X11 forwarding with authentication spoofing.
debug1: Sending environment.
debug1: Sending env LANG = en_US.UTF-8

Welcome to HOST!

>gcalctool
debug1: client_input_channel_open: ctype x11 rchan 3 win 65536 max 16384
debug1: client_request_x11: request from 127.0.0.1 49307
debug1: channel 1: new [x11]
debug1: confirm x11
debug1: client_input_channel_open: ctype x11 rchan 4 win 65536 max 16384
debug1: client_request_x11: request from 127.0.0.1 49308
debug1: channel 2: new [x11]
debug1: confirm x11
debug1: client_input_channel_open: ctype x11 rchan 5 win 65536 max 16384
debug1: client_request_x11: request from 127.0.0.1 49309
debug1: channel 3: new [x11]
debug1: confirm x11
debug1: channel 3: FORCE input drain
debug1: channel 3: free: x11, nchannels 4
>logout
debug1: client_input_channel_req: channel 0 rtype exit-status reply 0
debug1: channel 0: forcing write
debug1: channel 0: free: client-session, nchannels 3

****Freezes here so I do a ^c

debug1: channel 1: free: x11, nchannels 2
debug1: channel 2: free: x11, nchannels 1
Killed by signal 2.

---

### Post by Snow986 on 2010-05-18
Thanks.  The only thing I see that looks suspicious is here:

```

debug1: channel 0: forcing write

```

Can you increase the verbosity by using multiple -v options.  It looks like max is three according to my man.  Also I am wondering if the process is dying off completely.  Can you try 'ps -U $USER' right before logging out.  If the process is not dying, that would explain the hang.

---

### Post by archknight on 2010-05-18
The process is most certainly dying off. I checked it multiple times before but I include a quick check again in the run below. Here is the super verbose output:

>ssh -v -v -v -Y USER@IP_ADDRESS
OpenSSH_4.3p2, OpenSSL 0.9.8b 04 May 2006
debug1: Reading configuration data /home/USER/.ssh/config
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to IP_ADDRESS [IP_ADDRESS] port 22.
debug1: Connection established.
debug1: identity file /home/USER/.ssh/identity type -1
debug3: Not a RSA1 key file /home/USER/.ssh/id_rsa.
debug2: key_type_from_name: unknown key type '-----BEGIN'
debug3: key_read: missing keytype
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug2: key_type_from_name: unknown key type '-----END'
debug3: key_read: missing keytype
debug1: identity file /home/USER/.ssh/id_rsa type 1
debug1: identity file /home/USER/.ssh/id_dsa type -1
debug1: loaded 3 keys
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.3p1 Debian-3ubuntu3
debug1: match: OpenSSH_5.3p1 Debian-3ubuntu3 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.3
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: mac_init: found hmac-md5
debug1: kex: server->client aes128-cbc hmac-md5 none
debug2: mac_init: found hmac-md5
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug2: dh_gen_key: priv key bits set: 132/256
debug2: bits set: 502/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug3: check_host_in_hostfile: filename /home/USER/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 33
debug1: Host 'IP_ADDRESS' is known and matches the RSA host key.
debug1: Found key in /home/USER/.ssh/known_hosts:33
debug2: bits set: 520/1024
debug1: ssh_rsa_verify: signature correct
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /home/USER/.ssh/identity ((nil))
debug2: key: /home/USER/.ssh/id_rsa (0x5555557b45d0)
debug2: key: /home/USER/.ssh/id_dsa ((nil))
debug1: Authentications that can continue: publickey,password
debug3: start over, passed a different list publickey,password
debug3: preferred gssapi-with-mic,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /home/USER/.ssh/identity
debug3: no such identity: /home/USER/.ssh/identity
debug1: Offering public key: /home/USER/.ssh/id_rsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,password
debug1: Trying private key: /home/USER/.ssh/id_dsa
debug3: no such identity: /home/USER/.ssh/id_dsa
debug2: we did not send a packet, disable method
debug3: authmethod_lookup password
debug3: remaining preferred: ,password
debug3: authmethod_is_enabled password
debug1: Next authentication method: password
USER@IP_ADDRESS's password: 
debug3: packet_send2: adding 48 (len 65 padlen 15 extra_pad 64)
debug2: we sent a password packet, wait for reply
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug3: ssh_session2_open: channel_new: 0
debug2: channel 0: send open
debug1: Entering interactive session.
debug2: callback start
debug2: x11_get_proto: /usr/bin/xauth  list unix:10.0 2>/dev/null
debug1: Requesting X11 forwarding with authentication spoofing.
debug2: channel 0: request x11-req confirm 0
debug2: client_session2_setup: id 0
debug2: channel 0: request pty-req confirm 0
debug3: tty_make_modes: ospeed 38400
debug3: tty_make_modes: ispeed 38400
debug3: tty_make_modes: 1 3
debug3: tty_make_modes: 2 28
debug3: tty_make_modes: 3 127
debug3: tty_make_modes: 4 21
debug3: tty_make_modes: 5 4
debug3: tty_make_modes: 6 0
debug3: tty_make_modes: 7 0
debug3: tty_make_modes: 8 17
debug3: tty_make_modes: 9 19
debug3: tty_make_modes: 10 26
debug3: tty_make_modes: 12 18
debug3: tty_make_modes: 13 23
debug3: tty_make_modes: 14 22
debug3: tty_make_modes: 18 15
debug3: tty_make_modes: 30 0
debug3: tty_make_modes: 31 0
debug3: tty_make_modes: 32 0
debug3: tty_make_modes: 33 0
debug3: tty_make_modes: 34 0
debug3: tty_make_modes: 35 0
debug3: tty_make_modes: 36 1
debug3: tty_make_modes: 37 0
debug3: tty_make_modes: 38 1
debug3: tty_make_modes: 39 0
debug3: tty_make_modes: 40 0
debug3: tty_make_modes: 41 0
debug3: tty_make_modes: 50 1
debug3: tty_make_modes: 51 1
debug3: tty_make_modes: 52 0
debug3: tty_make_modes: 53 1
debug3: tty_make_modes: 54 1
debug3: tty_make_modes: 55 1
debug3: tty_make_modes: 56 0
debug3: tty_make_modes: 57 0
debug3: tty_make_modes: 58 0
debug3: tty_make_modes: 59 1
debug3: tty_make_modes: 60 1
debug3: tty_make_modes: 61 1
debug3: tty_make_modes: 62 0
debug3: tty_make_modes: 70 1
debug3: tty_make_modes: 71 0
debug3: tty_make_modes: 72 1
debug3: tty_make_modes: 73 0
debug3: tty_make_modes: 74 0
debug3: tty_make_modes: 75 0
debug3: tty_make_modes: 90 1
debug3: tty_make_modes: 91 1
debug3: tty_make_modes: 92 0
debug3: tty_make_modes: 93 0
debug1: Sending environment.
debug3: Ignored env HOSTNAME
debug3: Ignored env TERM
debug3: Ignored env SHELL
debug3: Ignored env HISTSIZE
debug3: Ignored env KDE_NO_IPV6
debug3: Ignored env SSH_CLIENT
debug3: Ignored env QTDIR
debug3: Ignored env QTINC
debug3: Ignored env SSH_TTY
debug3: Ignored env USER
debug3: Ignored env LD_LIBRARY_PATH
debug3: Ignored env LS_COLORS
debug3: Ignored env KDEDIR
debug3: Ignored env MAIL
debug3: Ignored env PATH
debug3: Ignored env INPUTRC
debug3: Ignored env PWD
debug1: Sending env LANG = en_US.UTF-8
debug2: channel 0: request env confirm 0
debug3: Ignored env KDE_IS_PRELINKED
debug3: Ignored env SSH_ASKPASS
debug3: Ignored env SHLVL
debug3: Ignored env HOME
debug3: Ignored env PBS_DEFAULT
debug3: Ignored env LOGNAME
debug3: Ignored env QTLIB
debug3: Ignored env CVS_RSH
debug3: Ignored env SSH_CONNECTION
debug3: Ignored env LESSOPEN
debug3: Ignored env DISPLAY
debug3: Ignored env HISTTIMEFORMAT
debug3: Ignored env G_BROKEN_FILENAMES
debug3: Ignored env _
debug2: channel 0: request shell confirm 0
debug2: fd 3 setting TCP_NODELAY
debug2: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768
debug2: channel 0: rcvd adjust 2097152

Welcome to HOST!

>gedit
debug1: client_input_channel_open: ctype x11 rchan 3 win 65536 max 16384
debug1: client_request_x11: request from 127.0.0.1 59353
debug2: fd 7 setting TCP_NODELAY
debug2: fd 7 setting O_NONBLOCK
debug3: fd 7 is O_NONBLOCK
debug1: channel 1: new [x11]
debug1: confirm x11

debug1: client_input_channel_open: ctype x11 rchan 4 win 65536 max 16384
debug1: client_request_x11: request from 127.0.0.1 59354
debug2: fd 8 setting TCP_NODELAY
debug2: fd 8 setting O_NONBLOCK
debug3: fd 8 is O_NONBLOCK
debug1: channel 2: new [x11]
debug1: confirm x11
debug1: client_input_channel_open: ctype x11 rchan 5 win 65536 max 16384
debug1: client_request_x11: request from 127.0.0.1 59355
debug2: fd 9 setting TCP_NODELAY
debug2: fd 9 setting O_NONBLOCK
debug3: fd 9 is O_NONBLOCK
debug1: channel 3: new [x11]
debug1: confirm x11
debug2: channel 1: window 63144 sent adjust 67928
debug2: channel 1: window 54120 sent adjust 76952
debug2: channel 1: window 61228 sent adjust 69844
debug2: channel 1: rcvd eof
debug2: channel 1: output open -> drain
debug2: channel 1: obuf empty
debug2: channel 1: close_write
debug2: channel 1: output drain -> closed
debug1: channel 1: FORCE input drain
debug2: channel 1: ibuf empty
debug2: channel 1: send eof
debug2: channel 1: input drain -> closed
debug2: channel 1: send close
debug3: channel 1: will not send data after close
debug2: channel 1: rcvd close
debug3: channel 1: will not send data after close
debug2: channel 1: is dead
debug2: channel 1: garbage collecting
debug1: channel 1: free: x11, nchannels 4
debug3: channel 1: status: The following connections are open:
  #0 client-session (t4 r0 i0/0 o0/0 fd 4/5 cfd -1)
  #1 x11 (t4 r3 i3/0 o3/0 fd 7/7 cfd -1)
  #2 x11 (t4 r4 i0/0 o0/0 fd 8/8 cfd -1)
  #3 x11 (t4 r5 i0/0 o0/0 fd 9/9 cfd -1)

debug3: channel 1: close_fds r 7 w 7 e -1 c -1
>ps -U USER | grep gedit
>logout
debug1: client_input_channel_req: channel 0 rtype exit-status reply 0
debug2: channel 0: rcvd eof
debug2: channel 0: output open -> drain
debug2: channel 0: rcvd close
debug2: channel 0: close_read
debug2: channel 0: input open -> closed
debug3: channel 0: will not send data after close
debug1: channel 0: forcing write
debug3: channel 0: will not send data after close
debug2: channel 0: obuf empty
debug2: channel 0: close_write
debug2: channel 0: output drain -> closed
debug2: channel 0: almost dead
debug2: channel 0: gc: notify user
debug2: channel 0: gc: user detached
debug2: channel 0: send close
debug2: channel 0: is dead
debug2: channel 0: garbage collecting
debug1: channel 0: free: client-session, nchannels 3
debug3: channel 0: status: The following connections are open:
  #0 client-session (t4 r0 i3/0 o3/0 fd -1/-1 cfd -1)
  #2 x11 (t4 r4 i0/0 o0/0 fd 8/8 cfd -1)
  #3 x11 (t4 r5 i0/0 o0/0 fd 9/9 cfd -1)

debug3: channel 0: close_fds r -1 w -1 e 6 c -1


*** It freezes here. So, I hit ^c to get it to quit.


debug1: channel 2: free: x11, nchannels 2
debug3: channel 2: status: The following connections are open:
  #2 x11 (t4 r4 i0/0 o0/0 fd 8/8 cfd -1)
  #3 x11 (t4 r5 i0/0 o0/0 fd 9/9 cfd -1)

debug3: channel 2: close_fds r 8 w 8 e -1 c -1
debug1: channel 3: free: x11, nchannels 1
debug3: channel 3: status: The following connections are open:
  #3 x11 (t4 r5 i0/0 o0/0 fd 9/9 cfd -1)

debug3: channel 3: close_fds r 9 w 9 e -1 c -1
Killed by signal 2.

---

### Post by Snow986 on 2010-05-18
Ok so this is the problem:

```

debug3: channel 3: status: The following connections are open:
#3 x11 (t4 r5 i0/0 o0/0 fd 9/9 cfd -1)

```

 It is opening a third channel that is not closing when you try to logout.  It is only dying after ^C it. I'm not sure how to fix it though.  I'll try and figure it out.

---

### Post by Snow986 on 2010-05-18
WOW....  I just reproduced this problem sshing into a 8.04 machine from a mac.  gnome-system-monitor hung exactly how you describe and gives the same 3rd channel not closing.  I'll be asking our admins tomorrow about this and see if he can shed some insight...

It looks like these don't close when I close the gnome-system-monitor

```

 3216 pts/0    00:00:00 gconfd-2
 3224 pts/0    00:00:00 dbus-launch
 3225 ?        00:00:00 dbus-daemon
 3227 ?        00:00:00 gnome-vfs-daemo

```

very interesting.  Anyways if you want a quick fix, just kill these off before you logout.

---

### Post by Snow986 on 2010-05-19
So I just talked to our admin and he said this is new behavior.  The processes used to be run in the background detached from your session.  That way they did not have to be killed off before logging out.  However they would remain until they were killed at some later time.  He guessed this was implemented on purpose so as to kill off unnecessary processes.  If this is true, the implementation seems poor and we're not sure whether this is a gnome thing or OpenSSH.  If there is an expert listening could you clarify whether this is 'on purpose'?

---

### Post by archknight on 2010-05-19
Hey thanks, that worked! However, I only had gconfd-2, dbus-launch, dbus-daemon running, not the last one. Killing them off allowed me to log out. These are the command line used to run each of them.

/bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session
dbus-launch --autolaunch f106301288671b4f55e39e374be45e10 --binary-syntax --close-stderr
usr/lib/libgconf2-4/gconfd-2

So, for now this works. However, I can't be telling all future users of this system to kill off these processes every time.  And I don't think I want to write a script to replace logout that does this automatically. I need a better long term solution.

---

### Post by Snow986 on 2010-05-19
I agree.  You could submit it as a bug to ubuntu as I am pretty sure this is new behavior in the updated libraries for gnome.  This is not 'expected' behavior.  Glad we figured it out though!

---

### Post by archknight on 2010-05-19
Um... Feel free to submit the bug report yourself. I am not really sure how to do such a thing and I rather it be done right. Just me know when they have a solution.

---

### Post by archknight on 2010-05-21
Even though this is a bug and shouldn't be happening, is there anything we can do to deal with it now? I rather not wait until an update since I have no idea when that will come. Is there a way that stops these processes from running when using X forwarding? Or is there a way to start them that tells them to stop automatically? What can I do about this?

---

### Post by Snow986 on 2010-05-21
There might be a couple of things you can do.  Is this a multi user machine or is it just you using it?  If it is just you, you could alias logout to execute a simple script that uses killall to kill the remaining processes. But if this is multi user you don't want to do that because it will kill others processes also (most likely).  Using ^C to kill the ssh session will not break anything so that is probably the quickest, easiest thing to do.

---

### Post by archknight on 2010-05-21
Yes, I am setting this computer up to be a multi-user system. I can easily kill off the processes myself every time I use an X Window. However, I can't be telling everyone else that they need to do that.

---

### Post by archknight on 2010-05-23
I can set up a script that will kill any of these processes on logout if they are running. However, people could be logged in with multiple connections and have any combination of windows open. In fact, I do that all of the time. I think such a script would interfere with that and so isn't really a viable solution.

---

### Post by Snow986 on 2010-05-23
If it was me, I would create a system wide alias that ^D or exit or logout echos something like "If your ssh logout hangs, use control C to kill it" and have it wait 10 sec so people can read it.  Then if the people didn't know what to do, they will now.  A script will be an issue since it will interfere with multiple user's processes.

---

### Post by archknight on 2010-05-23
Having the users use control C was always the original solution. The goal here was to hide this issue from them or resolve it somehow. I think adding a delay to the logout is a very bad idea. Also, this doesn't address the problem of these background processes being created and left behind. We don't want them to be piling up.

---

### Post by Snow986 on 2010-05-24
They are not left behind.  The reason the ssh session hangs is because they must be killed off one way or another. The old way would have them piling up, this new "feature" makes sure they don't.

---

### Post by archknight on 2010-05-24
I swear, just before I posted that message, I experimented to see if these processes are left behind after a control C. And they were! However, I try it again and it seems that they are not. I must have been mistaken. Either way, I was willing to periodically look for these processes and remove them myself. So, that wasn't a big issue (though, it would have been annoying).

So, we are still back to square one. Control C always worked but I am not going to put up a message telling users that at times they can't log out and so they much kill the ssh session when that happens. Imagine being an admin on a windows system and setting up a script that delayed a person from logging out to say that if it freezes, you have to hit ctrl+alt+del in order to get it to continue. It is sort of ridiculous when you think about it. I am looking for some alternatives.  In fact, I will do almost anything besides put up such a message, even if sloppy or hard to accomplish. 

By the way, thanks again for all the help!

---

### Post by Alexqw on 2010-12-03
Hey, did you ever come up with a fix or a workaround for this?  I found [the bug]("https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/592434") on launchpad, but there doesn't seem to be much work on it (it is low priority, which makes sense).
  This isn't a huge deal; it is just an annoyance.

---Alex

---

### Post by dn1 on 2012-03-17
Try to exit using ~. (SSH escape sequence)

More info at [http://www.slac.stanford.edu/comp/unix/ssh_faq.html#logoff_hangs](http://www.slac.stanford.edu/comp/unix/ssh_faq.html#logoff_hangs)

---

### Post by archknight on 2012-06-04
> **dn1 said:**
> Try to exit using ~. (SSH escape sequence)
 
More info at [http://www.slac.stanford.edu/comp/unix/ssh_faq.html#logoff_hangs](http://www.slac.stanford.edu/comp/unix/ssh_faq.html#logoff_hangs)
 
I don't need to do anything special to exit the ssh session, ctrl+c is working just fine. I would just prefer if I didn't have to do that every time I use gedit via x window forwarding.
 
> **Alexqw said:**
> Hey, did you ever come up with a fix or a workaround for this? I found [the bug]("https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/592434") on launchpad, but there doesn't seem to be much work on it (it is low priority, which makes sense).
This isn't a huge deal; it is just an annoyance.

---Alex

No, unfortunately I never found a fix or a workaround. I have done a fresh install of the latest version of Ubuntu, precise, but the same thing happens, which is odd since gedit is so very different this time around.

---

### Post by mdizzle on 2012-06-08
> **archknight said:**
> ...the same thing happens, which is odd since gedit is so very different this time around.

The bug isn't with gedit, so I wouldn't expect anything different :)

I've been experiencing this bug with X Forwarding for quite some time, and it's still broken.. and still annoying.

---

