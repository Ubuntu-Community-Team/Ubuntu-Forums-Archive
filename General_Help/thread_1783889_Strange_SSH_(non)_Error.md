---
title: "Strange SSH (non) Error"
date: 2011-06-16
forum: General Help
---

### Post by DJNrrd on 2011-06-16
Hi All

I've noticed weird behaviour with ssh when my public key is named id_dsa.pub.  Probably best to show you:

```
djnrrd@TARDIS:~/.ssh$ ls -al
total 24
drwxr-xr-x  2 djnrrd djnrrd 4096 2011-06-16 15:39 .
drwxr-xr-x 67 djnrrd djnrrd 4096 2011-06-16 15:30 ..
-rw-------  1 djnrrd djnrrd  836 2010-05-26 09:23 authorized_keys
-rw-------  1 djnrrd djnrrd  736 2010-05-26 09:23 id_dsa
-rw-------  1 djnrrd djnrrd  596 2011-06-16 15:29 id_dsa.pub
-rw-r--r--  1 djnrrd djnrrd 1326 2011-06-16 14:38 known_hosts
djnrrd@TARDIS:~/.ssh$ ssh 192.168.1.9
key_read: uudecode AAAAB3NzaC1kc3MAAACBAMa+RoSIYMz9+avADzHYfhS5onYy4/sXFfdLahF7vZBEydgjHQp6uCpuN0OWlsZt1sDVJ2UBsYWHYQ12cUlZOuXHiIDVR2x0WCJMSmOH7IxWWhzMcwm3LuOIvuFTkITOVEnNInij7WtrwHgYnj4PbgiYTnFwn41TGX9hj0HgW8HAAAAFQCP5kqDevRUdV8onLe7gV0sJRBOwAAAIEAuxn5wnI0HymnGndu6BW99V50zFlwrgG88W0zRPpwNI1JqDjvQDrU2bTwBgmKImYHmdovdhLQ346YpBFBVuQQfAvPOHlzTjt4sFGtdDYsi0PaeNy+QQmSHhRP+JzUoA1ZGp8cm1g4jclSk6HcwJDyZ3YiEX2Elevy4KY0dsARMAAACAAfngnba8Wg6tTzTe8oIFQFkTa3LzdI3buzxt3cXC2rQmlFoccziAHjpcbFUR7zKcaK1GDKNHxIQwayBp1ZgLDgZTUIKY1BkLqfA8VmOKIoJrqubESqNLaqK+4TGyXh5kGSrXlAJUJQhAoKINRGBW2JwUnH7dQIgSVjDFqo0M2M= djnrrd@pinky failed
Enter passphrase for key '/home/djnrrd/.ssh/id_dsa': 
djnrrd@TheLibrary:~$ Connection to 192.168.1.9 closed.
djnrrd@TARDIS:~/.ssh$ mv id_dsa.pub public_key
djnrrd@TARDIS:~/.ssh$ ssh 192.168.1.9
Enter passphrase for key '/home/djnrrd/.ssh/id_dsa': 
djnrrd@TheLibrary:~$ 

```

Weird, no? I'm still asked for my private key passphrase and log in succesfully. I suppose I could just work around by having the file named public_key, but it's bugging me.

Here's the very very verbose output from ssh:

```
djnrrd@TARDIS:~/.ssh$ ssh -vvv 192.168.1.9
OpenSSH_5.8p1 Debian-1ubuntu3, OpenSSL 0.9.8o 01 Jun 2010
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.168.1.9 [192.168.1.9] port 22.
debug1: Connection established.
debug1: identity file /home/djnrrd/.ssh/id_rsa type -1
debug1: identity file /home/djnrrd/.ssh/id_rsa-cert type -1
debug3: Incorrect RSA1 identifier
debug3: Could not load "/home/djnrrd/.ssh/id_dsa" as a RSA1 public key
debug2: key_type_from_name: unknown key type '-----BEGIN'
debug3: key_read: missing keytype
debug2: key_type_from_name: unknown key type 'Proc-Type:'
debug3: key_read: missing keytype
debug2: key_type_from_name: unknown key type 'DEK-Info:'
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
debug2: key_type_from_name: unknown key type '-----END'
debug3: key_read: missing keytype
key_read: uudecode AAAAB3NzaC1kc3MAAACBAMa+RoSIYMz9+avADzHYfhS5onYy4/sXFfdLahF7vZBEydgjHQp6uCpuN0OWlsZt1sDVJ2UBsYWHYQ12cUlZOuXHiIDVR2x0WCJMSmOH7IxWWhzMcwm3LuOIvuFTkITOVEnNInij7WtrwHgYnj4PbgiYTnFwn41TGX9hj0HgW8HAAAAFQCP5kqDevRUdV8onLe7gV0sJRBOwAAAIEAuxn5wnI0HymnGndu6BW99V50zFlwrgG88W0zRPpwNI1JqDjvQDrU2bTwBgmKImYHmdovdhLQ346YpBFBVuQQfAvPOHlzTjt4sFGtdDYsi0PaeNy+QQmSHhRP+JzUoA1ZGp8cm1g4jclSk6HcwJDyZ3YiEX2Elevy4KY0dsARMAAACAAfngnba8Wg6tTzTe8oIFQFkTa3LzdI3buzxt3cXC2rQmlFoccziAHjpcbFUR7zKcaK1GDKNHxIQwayBp1ZgLDgZTUIKY1BkLqfA8VmOKIoJrqubESqNLaqK+4TGyXh5kGSrXlAJUJQhAoKINRGBW2JwUnH7dQIgSVjDFqo0M2M= djnrrd@pinky failed
debug1: identity file /home/djnrrd/.ssh/id_dsa type -1
debug1: identity file /home/djnrrd/.ssh/id_dsa-cert type -1
debug1: identity file /home/djnrrd/.ssh/id_ecdsa type -1
debug1: identity file /home/djnrrd/.ssh/id_ecdsa-cert type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.2
debug1: match: OpenSSH_5.2 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.8p1 Debian-1ubuntu3
debug2: fd 3 setting O_NONBLOCK
debug3: load_hostkeys: loading entries for host "192.168.1.9" from file "/home/djnrrd/.ssh/known_hosts"
debug3: load_hostkeys: found key type RSA in file /home/djnrrd/.ssh/known_hosts:3
debug3: load_hostkeys: loaded 1 keys
debug3: order_hostkeyalgs: prefer hostkeyalgs: ssh-rsa-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com,ssh-rsa
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com,ssh-rsa,ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ssh-dss-cert-v01@openssh.com,ssh-dss-cert-v00@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,ssh-dss
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
debug2: dh_gen_key: priv key bits set: 128/256
debug2: bits set: 491/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Server host key: RSA b4:14:d7:06:37:f8:ab:1e:df:16:36:c9:ee:43:b7:0c
debug3: load_hostkeys: loading entries for host "192.168.1.9" from file "/home/djnrrd/.ssh/known_hosts"
debug3: load_hostkeys: found key type RSA in file /home/djnrrd/.ssh/known_hosts:3
debug3: load_hostkeys: loaded 1 keys
debug1: Host '192.168.1.9' is known and matches the RSA host key.
debug1: Found key in /home/djnrrd/.ssh/known_hosts:3
debug2: bits set: 519/1024
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
debug2: key: /home/djnrrd/.ssh/id_rsa ((nil))
debug2: key: /home/djnrrd/.ssh/id_dsa ((nil))
debug2: key: /home/djnrrd/.ssh/id_ecdsa ((nil))
debug1: Authentications that can continue: publickey
debug3: start over, passed a different list publickey
debug3: preferred gssapi-keyex,gssapi-with-mic,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /home/djnrrd/.ssh/id_rsa
debug3: no such identity: /home/djnrrd/.ssh/id_rsa
debug1: Trying private key: /home/djnrrd/.ssh/id_dsa
debug1: key_parse_private_pem: PEM_read_PrivateKey failed
debug1: read PEM private key done: type <unknown>
Enter passphrase for key '/home/djnrrd/.ssh/id_dsa': 
debug1: read PEM private key done: type DSA
debug3: sign_and_send_pubkey: DSA b3:a3:de:4e:89:7d:24:bc:18:c8:9c:7e:dc:00:c3:b1
debug2: we sent a publickey packet, wait for reply
debug1: Authentication succeeded (publickey).
Authenticated to 192.168.1.9 ([192.168.1.9]:22).
debug1: channel 0: new [client-session]
debug3: ssh_session2_open: channel_new: 0
debug2: channel 0: send open
debug1: Requesting no-more-sessions@openssh.com
debug1: Entering interactive session.
debug2: callback start
debug2: client_session2_setup: id 0
debug2: fd 3 setting TCP_NODELAY
debug3: packet_set_tos: set IP_TOS 0x10
debug2: channel 0: request pty-req confirm 1
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
debug3: Ignored env SESSION_MANAGER
debug3: Ignored env USERNAME
debug3: Ignored env DEFAULTS_PATH
debug3: Ignored env XDG_CONFIG_DIRS
debug3: Ignored env PATH
debug3: Ignored env DESKTOP_SESSION
debug3: Ignored env PWD
debug3: Ignored env GDM_KEYBOARD_LAYOUT
debug3: Ignored env GNOME_KEYRING_PID
debug1: Sending env LANG = en_GB.UTF-8
debug2: channel 0: request env confirm 0
debug3: Ignored env GDM_LANG
debug3: Ignored env MANDATORY_PATH
debug3: Ignored env UBUNTU_MENUPROXY
debug3: Ignored env COMPIZ_CONFIG_PROFILE
debug3: Ignored env GDMSESSION
debug3: Ignored env SHLVL
debug3: Ignored env HOME
debug3: Ignored env LANGUAGE
debug3: Ignored env GNOME_DESKTOP_SESSION_ID
debug3: Ignored env LOGNAME
debug3: Ignored env XDG_DATA_DIRS
debug3: Ignored env DBUS_SESSION_BUS_ADDRESS
debug3: Ignored env LESSOPEN
debug3: Ignored env WINDOWPATH
debug3: Ignored env DISPLAY
debug3: Ignored env LESSCLOSE
debug3: Ignored env COLORTERM
debug3: Ignored env XAUTHORITY
debug3: Ignored env _
debug2: channel 0: request shell confirm 1
debug2: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768
debug2: channel_input_status_confirm: type 99 id 0
debug2: PTY allocation request accepted on channel 0
debug2: channel 0: rcvd adjust 2097152
debug2: channel_input_status_confirm: type 99 id 0
debug2: shell request accepted on channel 0
djnrrd@TheLibrary:~$ 

```

I did a diff against a vvv output with both id_dsa.pub and public_key and there was no difference except for the error that occurs without verbose output.

My google-fu has failed me, any thoughts anyone?

---

### Post by DJNrrd on 2011-06-16
I appear to have fixed it!

What I didn't mention before was that the id_dsa.pub was pulled with wget from my launchpad account and renamed from +sshkey.

I compared my authorized_keys file (which has 2 public keys in it) and aside from the line for my work key there was also the message "No newline at end of file"

I copied my existing authorized_keys file to id_dsa.pub and deleted the line with my work key in Vim.

```
djnrrd@TARDIS:~/.ssh$ ls -al
total 24
drwxr-xr-x  2 djnrrd djnrrd 4096 2011-06-16 16:17 .
drwxr-xr-x 68 djnrrd djnrrd 4096 2011-06-16 16:10 ..
-rw-------  1 djnrrd djnrrd  836 2010-05-26 09:23 authorized_keys
-rw-------  1 djnrrd djnrrd  736 2010-05-26 09:23 id_dsa
-rw-------  1 djnrrd djnrrd  602 2011-06-16 16:10 id_dsa.pub
-rw-r--r--  1 djnrrd djnrrd 1326 2011-06-16 14:38 known_hosts
djnrrd@TARDIS:~/.ssh$ more id_dsa.pub 
ssh-dss AAAAB3NzaC1kc3MAAACBAMa+RoSIYMz9+avADzHYfhS5onYy4/sXFfdLahF7vZBEydgjHQp6
uCpuN0OWls/Zt1sDVJ2UBsYWHYQ12cUlZOuXHiIDVR2x0WCJMSmOH7IxWWhzMcwm3LuOIvuFTkITOVEn
NInij7WtrwHgYnj4PbgiYTnFwn41TGX9hj0HgW8HAAAAFQCP5kqDevRUd/V8onLe7gV0sJRBOwAAAIEA
uxn5wnI0HymnGndu6BW99V50zFlwrgG88W0zRPpwNI1JqDjvQDrU2bTwBgmKImYHmdovdhLQ346YpBFB
VuQQfAvPOHlzTjt4sFGtdDYsi0PaeNy+QQm/SHhRP+JzUoA1ZGp8cm1g4jclSk6HcwJDy/Z3YiEX2Ele
vy4KY0dsARMAAACAAfngnba8Wg6tTzTe8oIFQFkTa3LzdI3buzxt3cXC2rQmlFoccziAHjpcbFUR7zKc
aK1GDKNHxIQwayBp1ZgLDgZTUIKY1BkLqfA8VmOKIo/JrqubESqNLaqK+4TGyXh5kGSrXlAJUJQhAoKI
NRGBW2JwUnH7dQIgSVjDFqo0M2M= djnrrd@pinky
djnrrd@TARDIS:~/.ssh$ ssh 192.168.1.9
djnrrd@TheLibrary:~$ 

```

As an added bonus Seahorse is now managing the private key/ssh-agent which wasn't happening before

---

