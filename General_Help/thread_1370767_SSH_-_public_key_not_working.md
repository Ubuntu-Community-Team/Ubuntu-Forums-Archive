---
title: "SSH - public key not working"
date: 2010-01-02
forum: General Help
---

### Post by Berduchwal on 2010-01-02
I am trying to connect from one laptop to the PC.

PC to which I try to connect is: Ubuntu 9.10 64-bit
Laptop from which I connect is: Ubuntu 9.10 32-bit

PC: /etc/ssh/sshd_config

```
# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 3434
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 768

# Logging
SyslogFacility AUTH
LogLevel INFO

# Authentication:
LoginGraceTime 120
PermitRootLogin no
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile	/home/marcin/.ssh/authorized_keys

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords yes

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no

# Change to no to disable tunnelled clear text passwords
PasswordAuthentication no

# Kerberos options
#KerberosAuthentication no
#KerberosGetAFSToken no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM no
```

I used on the PC:```
cat id_rsa.pub >> authorized_keys
```

file is: /home/marcin/.ssh/authorized_keys

I used following command to connect: ```
ssh -p 3434 marcin@192.168.1.66 -vvv
```

As a result I got following results: ```
OpenSSH_5.1p1 Debian-6ubuntu2, OpenSSL 0.9.8g 19 Oct 2007 
debug1: Reading configuration data /etc/ssh/ssh_config 
debug1: Applying options for * 
debug2: ssh_connect: needpriv 0 
debug1: Connecting to 192.168.1.66 [192.168.1.66] port 7642. 
debug1: Connection established. 
debug1: identity file /home/marcin/.ssh/identity type -1 
debug3: Not a RSA1 key file /home/marcin/.ssh/id_rsa. 
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
debug1: identity file /home/marcin/.ssh/id_rsa type 1 
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048 
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048 
debug1: identity file /home/marcin/.ssh/id_dsa type -1 
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-6ubuntu2 
debug1: match: OpenSSH_5.1p1 Debian-6ubuntu2 pat OpenSSH* 
debug1: Enabling compatibility mode for protocol 2.0 
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-6ubuntu2 
debug2: fd 3 setting O_NONBLOCK 
debug1: SSH2_MSG_KEXINIT sent 
debug1: SSH2_MSG_KEXINIT received 
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1 
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss 
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr 
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr 
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
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr 
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr 
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96 
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96 
debug2: kex_parse_kexinit: none,zlib@openssh.com 
debug2: kex_parse_kexinit: none,zlib@openssh.com 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: mac_setup: found hmac-md5 
debug1: kex: server->client aes128-cbc hmac-md5 none 
debug2: mac_setup: found hmac-md5 
debug1: kex: client->server aes128-cbc hmac-md5 none 
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent 
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP 
debug2: dh_gen_key: priv key bits set: 119/256 
debug2: bits set: 493/1024 
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent 
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY 
debug3: put_host_port: [192.168.1.66]:7642 
debug3: put_host_port: [192.168.1.66]:7642 
debug3: check_host_in_hostfile: filename /home/marcin/.ssh/known_hosts 
debug3: check_host_in_hostfile: filename /etc/ssh/ssh_known_hosts 
debug3: check_host_in_hostfile: filename /home/marcin/.ssh/known_hosts 
debug3: check_host_in_hostfile: filename /etc/ssh/ssh_known_hosts 
debug1: checking without port identifier 
debug3: check_host_in_hostfile: filename /home/marcin/.ssh/known_hosts 
debug3: check_host_in_hostfile: match line 2 
debug1: Host '192.168.1.66' is known and matches the RSA host key. 
debug1: Found key in /home/marcin/.ssh/known_hosts:2 
debug1: found matching key w/out port 
debug2: bits set: 516/1024 
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
debug2: key: /home/marcin/.ssh/id_rsa (0x2b4fa60) 
debug2: key: /home/marcin/.ssh/identity ((nil)) 
debug2: key: /home/marcin/.ssh/id_dsa ((nil)) 
debug1: Authentications that can continue: publickey 
debug3: start over, passed a different list publickey 
debug3: preferred gssapi-keyex,gssapi-with-mic,gssapi,publickey,keyboard-interactive,password 
debug3: authmethod_lookup publickey 
debug3: remaining preferred: keyboard-interactive,password 
debug3: authmethod_is_enabled publickey 
debug1: Next authentication method: publickey 
debug1: Offering public key: /home/marcin/.ssh/id_rsa 
debug3: send_pubkey_test 
debug2: we sent a publickey packet, wait for reply 
debug1: Authentications that can continue: publickey 
debug1: Trying private key: /home/marcin/.ssh/identity 
debug3: no such identity: /home/marcin/.ssh/identity 
debug1: Trying private key: /home/marcin/.ssh/id_dsa 
debug3: no such identity: /home/marcin/.ssh/id_dsa 
debug2: we did not send a packet, disable method 
debug1: No more authentication methods to try. 
Permission denied (publickey). 
```

Can you please advise how I can find out what is wrong?

---

