---
title: "scp problem"
date: 2010-10-27
forum: General Help
---

### Post by supradave on 2010-10-27
I'm using OpenSSH_5.5p1 Debian-4ubuntu4, OpenSSL 0.9.8o 01 Jun 2010 on Maverick.  I'm trying to scp a file from or to my machine to another machine.  I the the following error:

```
scp localfile server:/directory
Received disconnect from UNKNOWN: 2: Protocol error.
lost connection
```

So, to debug:
```
scp -v localfile server:/directory
debug1: Sending command: scp -v -t -- /directory
Received disconnect from x.x.x.x: 2: Protocol error.
lost connection
```

So, I tried it from my Mac, and did the -v thing and got:
```
debug1: Sending command: scp -v -t /directory/file
```
and successfully scp'd.

Any way to get rid of the double-dash "--"?

If I try to copy from, the -t changes to -f and the -- is still there.

---

### Post by luvshines on 2010-10-27
Can you post the complete logs with -v ?

---

### Post by supradave on 2010-10-27
Here you go.  I'm authenticating.  I can ssh in without problem.

```
scp -v file ns1:/authdnsadmin
Executing: program /usr/bin/ssh host ns1, user (unspecified), command scp -v -t -- /authdnsadmin
OpenSSH_5.5p1 Debian-4ubuntu4, OpenSSL 0.9.8o 01 Jun 2010
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to ns1 [x.x.x.x] port 22.
debug1: Connection established.
debug1: identity file ~/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: identity file ~/.ssh/id_rsa-cert type -1
debug1: identity file ~/.ssh/id_dsa type 2
debug1: Checking blacklist file /usr/share/ssh/blacklist.DSA-1024
debug1: Checking blacklist file /etc/ssh/blacklist.DSA-1024
debug1: identity file ~/.ssh/id_dsa-cert type -1
debug1: Remote protocol version 2.0, remote software version nvn
debug1: no match: nvn
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.5p1 Debian-4ubuntu4
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'ns1.x.com' is known and matches the RSA host key.
debug1: Found key in ~/.ssh/known_hosts:22
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: Roaming not allowed by server
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password,keyboard-interactive
debug1: Next authentication method: publickey
debug1: Offering public key: ~/.ssh/id_dsa
debug1: Server accepts key: pkalg ssh-dss blen 434
Authenticated with partial success.
debug1: Authentications that can continue: publickey,password,keyboard-interactive
debug1: Offering public key: ~/.ssh/id_rsa
debug1: Server accepts key: pkalg ssh-rsa blen 277
Copyright (c) 2003-2010 x Software Corp.
All Rights Reserved
Authorized access only
debug1: Authentication succeeded (publickey).
debug1: channel 0: new [client-session]
debug1: Entering interactive session.
debug1: Sending environment.
debug1: Sending env LANG = en_US.utf8
debug1: Sending command: scp -v -t -- /authdnsadmin
Received disconnect from UNKNOWN: 2: Protocol error.
lost connection
```

---

### Post by supradave on 2010-11-18
Still having this problem and believe it's a Maverick Meercat problem.  I have built from source down to 5.0p1 from openssh.org and get the same results every time.  From Lucid Lynx, no problems.

---

### Post by supradave on 2010-11-18
Here is the conversation with strace.  Somewhere, which I'm not sure where, the -- comes in.  There's a line a few lines above the scp conversation that starts with write.  

```
strace scp -vvv ns1:/authdnsadmin/x.com.zone .
execve("/usr/bin/scp", ["scp", "-vvv", "ns1:/authdnsadmin/x.com.z"..., "."], [/* 39 vars */]) = 0
brk(0)                                  = 0x20366000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap2(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb777d000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=120324, ...}) = 0
mmap2(NULL, 120324, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb775f000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libc.so.6", O_RDONLY)        = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0@n\1\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0755, st_size=1421892, ...}) = 0
mmap2(NULL, 1431976, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x5ec000
mprotect(0x743000, 4096, PROT_NONE)     = 0
mmap2(0x744000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x157) = 0x744000
mmap2(0x747000, 10664, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x747000
close(3)                                = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb775e000
set_thread_area({entry_number:-1 -> 6, base_addr:0xb775e8d0, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}) = 0
mprotect(0x744000, 8192, PROT_READ)     = 0
mprotect(0x131000, 4096, PROT_READ)     = 0
mprotect(0xe21000, 4096, PROT_READ)     = 0
munmap(0xb775f000, 120324)              = 0
open("/dev/null", O_RDWR|O_LARGEFILE)   = 3
close(3)                                = 0
brk(0)                                  = 0x20366000
brk(0x20387000)                         = 0x20387000
getuid32()                              = 1000
socket(PF_FILE, SOCK_STREAM|SOCK_CLOEXEC|SOCK_NONBLOCK, 0) = 3
connect(3, {sa_family=AF_FILE, path="/var/run/nscd/socket"}, 110) = -1 ENOENT (No such file or directory)
close(3)                                = 0
socket(PF_FILE, SOCK_STREAM|SOCK_CLOEXEC|SOCK_NONBLOCK, 0) = 3
connect(3, {sa_family=AF_FILE, path="/var/run/nscd/socket"}, 110) = -1 ENOENT (No such file or directory)
close(3)                                = 0
open("/etc/nsswitch.conf", O_RDONLY)    = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=513, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb777c000
read(3, "# /etc/nsswitch.conf\n#\n# Example"..., 4096) = 513
read(3, "", 4096)                       = 0
close(3)                                = 0
munmap(0xb777c000, 4096)                = 0
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=120324, ...}) = 0
mmap2(NULL, 120324, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb775f000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libnss_compat.so.2", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0000\16\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=30496, ...}) = 0
mmap2(NULL, 29268, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x8cb000
mmap2(0x8d1000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x6) = 0x8d1000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libnsl.so.1", O_RDONLY)      = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\2201\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=79676, ...}) = 0
mmap2(NULL, 92136, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x8f9000
mmap2(0x90c000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x12) = 0x90c000
mmap2(0x90e000, 6120, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x90e000
close(3)                                = 0
mprotect(0x90c000, 4096, PROT_READ)     = 0
mprotect(0x8d1000, 4096, PROT_READ)     = 0
munmap(0xb775f000, 120324)              = 0
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=120324, ...}) = 0
mmap2(NULL, 120324, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb775f000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libnss_nis.so.2", O_RDONLY)  = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0000\31\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=38504, ...}) = 0
mmap2(NULL, 41532, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x277000
mmap2(0x280000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x8) = 0x280000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libnss_files.so.2", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0 \32\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=42572, ...}) = 0
mmap2(NULL, 45772, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xbb1000
mmap2(0xbbb000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x9) = 0xbbb000
close(3)                                = 0
mprotect(0xbbb000, 4096, PROT_READ)     = 0
mprotect(0x280000, 4096, PROT_READ)     = 0
munmap(0xb775f000, 120324)              = 0
open("/etc/passwd", O_RDONLY|O_CLOEXEC) = 3
fcntl64(3, F_GETFD)                     = 0x1 (flags FD_CLOEXEC)
_llseek(3, 0, [0], SEEK_CUR)            = 0
fstat64(3, {st_mode=S_IFREG|0644, st_size=3199, ...}) = 0
mmap2(NULL, 3199, PROT_READ, MAP_SHARED, 3, 0) = 0xb777c000
_llseek(3, 3199, [3199], SEEK_SET)      = 0
munmap(0xb777c000, 3199)                = 0
close(3)                                = 0
ioctl(1, SNDCTL_TMR_TIMEBASE or TCGETS, {B38400 opost isig icanon echo ...}) = 0
rt_sigaction(SIGPIPE, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGPIPE, {0x126af0, [], 0}, NULL, 8) = 0
write(2, "Executing: program /usr/bin/ssh "..., 115Executing: program /usr/bin/ssh host ns1, user (unspecified), command scp -v -f -- /authdnsadmin/x.com.zone
) = 115
pipe([3, 4])                            = 0
pipe([5, 6])                            = 0
pipe([7, 8])                            = 0
close(3)                                = 0
close(4)                                = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb775e938) = 29067
close(5)                                = 0
close(8)                                = 0
rt_sigaction(SIGTERM, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGTERM, {0x126c60, [], 0}, NULL, 8) = 0
rt_sigaction(SIGINT, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGINT, {0x126c60, [], 0}, NULL, 8) = 0
rt_sigaction(SIGHUP, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGHUP, {0x126c60, [], 0}, NULL, 8) = 0
umask(0)                                = 022
umask(022)                              = 0
write(6, "\0", 1)                       = 1
stat64(".", {st_mode=S_IFDIR|0700, st_size=12288, ...}) = 0
read(7, OpenSSH_5.5p1 Debian-4ubuntu4, OpenSSL 0.9.8o 01 Jun 2010
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to ns1 [64.92.220.221] port 22.
debug1: Connection established.
debug3: Not a RSA1 key file /home/dave/.ssh/id_rsa.
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
debug1: identity file /home/dave/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: identity file /home/dave/.ssh/id_rsa-cert type -1
debug3: Not a RSA1 key file /home/dave/.ssh/id_dsa.
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
debug2: key_type_from_name: unknown key type '-----END'
debug3: key_read: missing keytype
debug1: identity file /home/dave/.ssh/id_dsa type 2
debug1: Checking blacklist file /usr/share/ssh/blacklist.DSA-1024
debug1: Checking blacklist file /etc/ssh/blacklist.DSA-1024
debug1: identity file /home/dave/.ssh/id_dsa-cert type -1
debug1: Remote protocol version 2.0, remote software version nvn
debug1: no match: nvn
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.5p1 Debian-4ubuntu4
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa-cert-v00@openssh.com,ssh-dss-cert-v00@openssh.com,ssh-rsa,ssh-dss
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
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,aes192-cbc,aes256-cbc,arcfour
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,aes192-cbc,aes256-cbc,arcfour
debug2: kex_parse_kexinit: hmac-sha1,hmac-md5,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-sha1,hmac-md5,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none
debug2: kex_parse_kexinit: none
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
debug2: dh_gen_key: priv key bits set: 127/256
debug2: bits set: 542/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug3: check_host_in_hostfile: host ns1 filename /home/dave/.ssh/known_hosts
debug3: check_host_in_hostfile: host ns1 filename /home/dave/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 137
debug3: check_host_in_hostfile: host 64.92.220.221 filename /home/dave/.ssh/known_hosts
debug3: check_host_in_hostfile: host 64.92.220.221 filename /home/dave/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 107
debug1: Host 'ns1' is known and matches the RSA host key.
debug1: Found key in /home/dave/.ssh/known_hosts:137
debug2: bits set: 509/1024
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
debug2: key: /home/dave/.ssh/id_rsa (0x20dd05e8)
debug2: key: /home/dave/.ssh/id_dsa (0x20dcb508)
debug1: Authentications that can continue: publickey,password,keyboard-interactive
debug3: start over, passed a different list publickey,password,keyboard-interactive
debug3: preferred gssapi-keyex,gssapi-with-mic,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Offering public key: /home/dave/.ssh/id_rsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Server accepts key: pkalg ssh-rsa blen 277
debug2: input_userauth_pk_ok: fp 49:e6:e9:87:7f:98:0d:e8:9e:09:e2:c7:b3:b2:38:de
debug3: sign_and_send_pubkey
debug3: input_userauth_banner
Copyright (c) 2003-2010 x Software Corp.
All Rights Reserved
Authorized access only
debug1: Authentication succeeded (publickey).
debug2: fd 4 setting O_NONBLOCK
debug2: fd 5 setting O_NONBLOCK
debug1: channel 0: new [client-session]
debug3: ssh_session2_open: channel_new: 0
debug2: channel 0: send open
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
debug3: Ignored env HISTCONTROL
debug3: Ignored env SPEECHD_PORT
debug3: Ignored env HOME
debug3: Ignored env SHLVL
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
debug1: Sending command: scp -v -f -- /authdnsadmin/x.com.zone
debug2: channel 0: request exec confirm 1
debug2: fd 3 setting TCP_NODELAY
debug2: callback done
debug2: channel 0: open confirm rwindow 0 rmax 262144
Received disconnect from 64.92.220.221: 2: Protocol error.
"", 1)                          = 0
--- SIGCHLD (Child exited) @ 0 (0) ---
close(7)                                = 0
waitpid(29067, [{WIFEXITED(s) && WEXITSTATUS(s) == 255}], 0) = 29067
exit_group(1)                           = ?
```

---

### Post by iponeverything on 2010-11-18
Restart the ssh daemon on ns1 in debug to get more info.

also check the integrity of your binaries to make sure you don't have rootkit.

---

### Post by supradave on 2010-11-18
ns1 is not a *NIX box.  It's a custom built OS and we know it's a problem with it and we're trying to fix it.  The question is how do I change the sending command where it's adding the -v -f -- to the string.  The -- is the problem.  Since I have built from source older versions of ssh, e.g. 5.0 (5.5 is installed in Maverick), it's something to do with Maverick as a Lucid box doesn't have the problem.

---

### Post by kruegerc on 2011-01-21
I, too, am having this issue:

```
...
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug1: Entering interactive session.
debug1: Sending environment.
debug1: Sending env LANG = en_US.UTF-8
debug1: Sending command: scp -v -f -- redacted.pcap
debug1: client_input_channel_req: channel 0 rtype exit-status reply 0
debug1: channel 0: free: client-session, nchannels 1
Sink: Invalid directory "--".
Invalid directory "--".
```

```
[pid 22726] execve("/usr/bin/ssh", ["/usr/bin/ssh", "-x", "-oForwardAgent no", "-oPermitLocalCommand no", "-oClearAllForwardings yes", "-l", "cakruege", "--", "redacted.host.com", "scp -f -- redacted.pcap21"], [/* 38 vars */] <unfinished ...>
```

I'm perplexed.

---

