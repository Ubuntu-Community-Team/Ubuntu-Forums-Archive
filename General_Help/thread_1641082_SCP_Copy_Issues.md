---
title: "SCP Copy Issues"
date: 2010-12-08
forum: General Help
---

### Post by gdonwallace on 2010-12-08
This started today.  I have been trying to SCP a couple files from my Ubuntu 10.10 machine to a Fedora 12 machine.  Before today, did it with out any problems, always worked.  Today however; after the SCP is complete from my machine, the file on the other machine is zero bytes, an empty file.

The only thing I can remember getting changed was the new kernel that was in the update I did today.  But I don't think that would have changed the SCP works.  Any help is appreciated, I need to be able to do this; as this is a major part of my job and without it I am at a stand still.

---

### Post by DaithiF on 2010-12-08
I would start by adding verbose logging and see what turns up:
scp **-vvv** rest of the command

---

### Post by v1ad on 2010-12-08
if you can give us the command that you are using ..

---

### Post by gdonwallace on 2010-12-09
The command I generally use is as follows:

scp nmc_20100101_050838.xml [email]mingw@Dellpre670mp:/home/mingw/nmc_20100101_050838.xml[/email]

When I add -vvv for verbose output, this is what I am getting:

Executing: program /usr/bin/ssh host Dellpre670mp, user mingw, command scp -v -t -- /home/mingw/nmc_20100101_050838.xml
OpenSSH_5.5p1 Debian-4ubuntu4, OpenSSL 0.9.8o 01 Jun 2010
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to Dellpre670mp [192.168.1.166] port 22.
debug1: Connection established.
debug1: identity file /home/mingw/.ssh/id_rsa type -1
debug1: identity file /home/mingw/.ssh/id_rsa-cert type -1
debug1: identity file /home/mingw/.ssh/id_dsa type -1
debug1: identity file /home/mingw/.ssh/id_dsa-cert type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.4
debug1: match: OpenSSH_5.4 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.5p1 Debian-4ubuntu4
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: [email]ssh-rsa-cert-v00@openssh.com,ssh-dss-cert-v00@openssh.com[/email],ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
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
debug2: mac_setup: found hmac-md5
debug1: kex: server->client aes128-ctr hmac-md5 none
debug2: mac_setup: found hmac-md5
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug2: dh_gen_key: priv key bits set: 132/256
debug2: bits set: 528/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug3: check_host_in_hostfile: host dellpre670mp filename /home/mingw/.ssh/known_hosts
debug3: check_host_in_hostfile: host dellpre670mp filename /home/mingw/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 1
debug3: check_host_in_hostfile: host 192.168.1.166 filename /home/mingw/.ssh/known_hosts
debug3: check_host_in_hostfile: host 192.168.1.166 filename /home/mingw/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 2
debug1: Host 'dellpre670mp' is known and matches the RSA host key.
debug1: Found key in /home/mingw/.ssh/known_hosts:1
debug2: bits set: 533/1024
debug1: ssh_rsa_verify: signature correct
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: Roaming not allowed by server
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /home/mingw/.ssh/id_rsa ((nil))
debug2: key: /home/mingw/.ssh/id_dsa ((nil))
debug1: Authentications that can continue: publickey,gssapi-keyex,gssapi-with-mic,password
debug3: start over, passed a different list publickey,gssapi-keyex,gssapi-with-mic,password
debug3: preferred gssapi-keyex,gssapi-with-mic,publickey,keyboard-interactive,password
debug3: authmethod_lookup gssapi-keyex
debug3: remaining preferred: gssapi-with-mic,publickey,keyboard-interactive,password
debug3: authmethod_is_enabled gssapi-keyex
debug1: Next authentication method: gssapi-keyex
debug1: No valid Key exchange context
debug2: we did not send a packet, disable method
debug3: authmethod_lookup gssapi-with-mic
debug3: remaining preferred: publickey,keyboard-interactive,password
debug3: authmethod_is_enabled gssapi-with-mic
debug1: Next authentication method: gssapi-with-mic
debug1: Unspecified GSS failure.  Minor code may provide more information
Credentials cache file '/tmp/krb5cc_1000' not found

debug1: Unspecified GSS failure.  Minor code may provide more information
Credentials cache file '/tmp/krb5cc_1000' not found

debug1: Unspecified GSS failure.  Minor code may provide more information


debug2: we did not send a packet, disable method
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /home/mingw/.ssh/id_rsa
debug3: no such identity: /home/mingw/.ssh/id_rsa
debug1: Trying private key: /home/mingw/.ssh/id_dsa
debug3: no such identity: /home/mingw/.ssh/id_dsa
debug2: we did not send a packet, disable method
debug3: authmethod_lookup password
debug3: remaining preferred: ,password
debug3: authmethod_is_enabled password
debug1: Next authentication method: password
**mingw@dellpre670mp's password: **
debug3: packet_send2: adding 64 (len 57 padlen 7 extra_pad 64)
debug2: we sent a password packet, wait for reply
debug1: Authentication succeeded (password).
debug2: fd 4 setting O_NONBLOCK
debug2: fd 5 setting O_NONBLOCK
debug1: channel 0: new [client-session]
debug3: ssh_session2_open: channel_new: 0
debug2: channel 0: send open
debug1: Requesting [email]no-more-sessions@openssh.com[/email]
debug1: Entering interactive session.
debug2: callback start
debug2: client_session2_setup: id 0
debug1: Sending environment.
debug3: Ignored env ORBIT_SOCKETDIR
debug3: Ignored env SSH_AGENT_PID
debug3: Ignored env TERM
debug3: Ignored env SHELL
debug3: Ignored env XDG_SESSION_COOKIE
debug3: Ignored env WINDOWID
debug3: Ignored env GNOME_KEYRING_CONTROL
debug3: Ignored env GTK_MODULES
debug3: Ignored env USER
debug3: Ignored env LS_COLORS
debug3: Ignored env SSH_AUTH_SOCK
debug3: Ignored env DEFAULTS_PATH
debug3: Ignored env SESSION_MANAGER
debug3: Ignored env USERNAME
debug3: Ignored env XDG_CONFIG_DIRS
debug3: Ignored env DESKTOP_SESSION
debug3: Ignored env PATH
debug3: Ignored env PWD
debug3: Ignored env GDM_KEYBOARD_LAYOUT
debug1: Sending env LANG = en_US.utf8
debug2: channel 0: request env confirm 0
debug3: Ignored env GNOME_KEYRING_PID
debug3: Ignored env MANDATORY_PATH
debug3: Ignored env GDM_LANG
debug3: Ignored env GDMSESSION
debug3: Ignored env SPEECHD_PORT
debug3: Ignored env SHLVL
debug3: Ignored env HOME
debug3: Ignored env GNOME_DESKTOP_SESSION_ID
debug3: Ignored env LOGNAME
debug3: Ignored env XDG_DATA_DIRS
debug3: Ignored env DBUS_SESSION_BUS_ADDRESS
debug3: Ignored env LESSOPEN
debug3: Ignored env WINDOWPATH
debug3: Ignored env DISPLAY
debug3: Ignored env LESSCLOSE
debug3: Ignored env XAUTHORITY
debug3: Ignored env COLORTERM
debug3: Ignored env _
debug3: Ignored env OLDPWD
debug1: Sending command: scp -v -t -- /home/mingw/nmc_20100101_050838.xml
debug2: channel 0: request exec confirm 1
debug2: fd 3 setting TCP_NODELAY
debug2: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768
debug2: channel 0: rcvd adjust 2097152
debug2: channel_input_status_confirm: type 99 id 0
debug2: exec request accepted on channel 0
Sending file modes: C0400 9279424 nmc_20100101_050838.xml
debug2: channel 0: rcvd ext data 44
Sink: C0400 9279424 nmc_20100101_050838.xml
debug2: channel 0: written 44 to efd 6
scp: /home/mingw/nmc_20100101_050838.xml: Permission denied
debug2: channel 0: read<=0 rfd 4 len 0
debug2: channel 0: read failed
debug2: channel 0: close_read
debug2: channel 0: input open -> drain
debug2: channel 0: ibuf empty
debug2: channel 0: send eof
debug2: channel 0: input drain -> closed
debug2: channel 0: rcvd eof
debug2: channel 0: output open -> drain
debug2: channel 0: obuf empty
debug2: channel 0: close_write
debug2: channel 0: output drain -> closed
debug1: client_input_channel_req: channel 0 rtype exit-status reply 0
debug2: channel 0: rcvd close
debug3: channel 0: will not send data after close
debug2: channel 0: almost dead
debug2: channel 0: gc: notify user
debug2: channel 0: gc: user detached
debug2: channel 0: send close
debug2: channel 0: is dead
debug2: channel 0: garbage collecting
debug1: channel 0: free: client-session, nchannels 1
debug3: channel 0: status: The following connections are open:
  #0 client-session (t4 r0 i3/0 o3/0 fd -1/-1 cc -1)

debug3: channel 0: close_fds r -1 w -1 e 6
debug1: fd 0 clearing O_NONBLOCK
debug1: fd 1 clearing O_NONBLOCK
Transferred: sent 1608, received 2120 bytes, in 0.0 seconds
Bytes per second: sent 40154.7, received 52940.3
debug1: Exit status 1

---

### Post by DaithiF on 2010-12-09
spot the obvious error buried in all that output?

[COLOR=Red]scp: /home/mingw/nmc_20100101_050838.xml: Permission denied[/COLOR]so its just a file permissions problem -- the user you are SCP'ing as doesn't have write access to that file.

do an ls -l on that file on your target machine (if its only that specific file that is the problem), or an ls -ld on /home/mingw if all similar transfers are failing.  Are you scp'ing as the correct user / have the files become owned by another user (e.g. root), etc.

---

### Post by gdonwallace on 2010-12-09
I found that after I had a chance to read through the output.

Permissions where initially read for root only, so changed that; still getting the same result; but I also just found another problem.../home on the machine I am copying the file too is 100% so trying to get rid of some old backup files too see if that will help.

Then will try the SCP again.

EDIT: after clearing up about 4 gig in space, SCP is now working again.  Need to clear out a little more.

---

