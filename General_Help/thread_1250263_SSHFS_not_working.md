---
title: "SSHFS not working"
date: 2009-08-26
forum: General Help
---

### Post by jfreak53 on 2009-08-26
Ok so I have this server that I can connect just fine to using ssh, no probs.  I even emptied my known-hosts file then re-did ssh connection to fill it again.  SSH connection works fine.  The problem is when I try to use sshfs, it gives me:

> read: Connection reset by peer

So I checked my /etc/ssh/sshd_config and it seems to be fine with:

> Subsystem sftp /usr/lib/openssh/sftp-server

Is there something missing here?  Why am I getting this error?  This is my sshfs connection string:

> sudo sshfs [email]adminusername@www.server.com[/email]:/ /mnt/cortijo -p 23

---

### Post by moore.bryan on 2009-08-26
I've usually found that message when I was trying to access a blocked port...

---

### Post by jfreak53 on 2009-08-26
Well I know the port works because I use the same port to connect with SSH and it works just fine:

> ssh -l adminuser -p 23 [www.servername.com](www.servername.com)

---

### Post by moore.bryan on 2009-08-26
Hmm... is there any particular reason you're using sudo for sshfs?

---

### Post by jfreak53 on 2009-08-26
Because of the directory it's mounting it to, I only want access by root to this dir.  The problem is this worked fine 2 weeks ago, everything.  The only thing that has changed is that I had to re-install said server and crash everything on server.  So config is new.  Could there be something missing?

I just tried it as a regular user and the same thing happens.

---

### Post by moore.bryan on 2009-08-26
Okay; let me get my head wrapped around this... all of the following is true, yes?

[LIST]
[*]you **can** ssh into the box via ```
sudo ssh -p 23 [EMAIL="adminusername@www.server.com"]adminusername@www.server.com[/EMAIL]
```
[*]you **cannot** mount the box via ```
sudo sshfs -p 23 [EMAIL="adminusername@www.server.com"]adminusername@www.server.com[/EMAIL]:/ /mnt/cortijo
```
[/LIST]

Have you tried either/both with the -vv switch?

---

### Post by jfreak53 on 2009-08-26
Don't quite know what that switch does but no, no change, I just tried it with both.

Sorry, yes you are correct in your assumptions.

---

### Post by moore.bryan on 2009-08-26
The switch just makes things a little more "verbose," so we might be able to see any errors. Could you run it with that switch, if not -vvvv?

---

### Post by jfreak53 on 2009-08-26
Ok so sshfs won't display anything when I do -vvvv or -vv but ssh spits out a lot on -vvvv, here it is:

> OpenSSH_5.1p1 Debian-5ubuntu1, OpenSSL 0.9.8g 19 Oct 2007                    
debug1: Reading configuration data /etc/ssh/ssh_config                       
debug1: Applying options for *                                               
debug2: ssh_connect: needpriv 0                                              
debug1: Connecting to [www.servername.com](www.servername.com) [IPAddress] port 23.         
debug1: Connection established.                                              
debug1: identity file /home/joel/.ssh/identity type -1                       
debug1: identity file /home/joel/.ssh/id_rsa type -1                         
debug1: identity file /home/joel/.ssh/id_dsa type -1                         
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.7p1 Debian-8ubuntu1.2
debug1: match: OpenSSH_4.7p1 Debian-8ubuntu1.2 pat OpenSSH_4*                               
debug1: Enabling compatibility mode for protocol 2.0                                        
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-5ubuntu1                          
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
debug2: dh_gen_key: priv key bits set: 124/256                                                                                                   
debug2: bits set: 503/1024                                                                                                                       
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent                                                                                                            
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY                                                                                                      
debug3: put_host_port: [IP Address]:23                                                                                                       
debug3: put_host_port: [[www.servername.com]:23](www.servername.com]:23)                                                                                                 
debug3: check_host_in_hostfile: filename /home/joel/.ssh/known_hosts                                                                             
debug3: check_host_in_hostfile: match line 2                                                                                                     
debug3: check_host_in_hostfile: filename /home/joel/.ssh/known_hosts                                                                             
debug3: check_host_in_hostfile: match line 3                                                                                                     
debug1: Host '[[www.servername.com]:23](www.servername.com]:23)' is known and matches the RSA host key.                                                                  
debug1: Found key in /home/joel/.ssh/known_hosts:2                                                                                               
debug2: bits set: 488/1024                                                                                                                       
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
debug2: key: /home/joel/.ssh/identity ((nil))                                                                                                    
debug2: key: /home/joel/.ssh/id_rsa ((nil))                                                                                                      
debug2: key: /home/joel/.ssh/id_dsa ((nil))                                                                                                      
debug1: Authentications that can continue: publickey,password                                                                                    
debug3: start over, passed a different list publickey,password                                                                                   
debug3: preferred gssapi-keyex,gssapi-with-mic,gssapi,publickey,keyboard-interactive,password                                                    
debug3: authmethod_lookup publickey                                                                                                              
debug3: remaining preferred: keyboard-interactive,password                                                                                       
debug3: authmethod_is_enabled publickey                                                                                                          
debug1: Next authentication method: publickey                                                                                                    
debug1: Trying private key: /home/joel/.ssh/identity                                                                                             
debug3: no such identity: /home/joel/.ssh/identity                                                                                               
debug1: Trying private key: /home/joel/.ssh/id_rsa                                                                                               
debug3: no such identity: /home/joel/.ssh/id_rsa                                                                                                 
debug1: Trying private key: /home/joel/.ssh/id_dsa                                                                                               
debug3: no such identity: /home/joel/.ssh/id_dsa                                                                                                 
debug2: we did not send a packet, disable method                                                                                                 
debug3: authmethod_lookup password                                                                                                               
debug3: remaining preferred: ,password                                                                                                           
debug3: authmethod_is_enabled password                                                                                                           
debug1: Next authentication method: password                                                                                                     
password:                                                                                                          
debug3: packet_send2: adding 64 (len 56 padlen 8 extra_pad 64)                                                                                   
debug2: we sent a password packet, wait for reply                                                                                                
debug1: Authentication succeeded (password).                                                                                                     
debug1: channel 0: new [client-session]                                                                                                          
debug3: ssh_session2_open: channel_new: 0                                                                                                        
debug2: channel 0: send open                                                                                                                     
debug1: Entering interactive session.                                                                                                            
debug2: callback start                                                                                                                           
debug2: client_session2_setup: id 0                                                                                                              
debug2: channel 0: request pty-req confirm 1                                                                                                     
debug3: tty_make_modes: ospeed 38400                                                                                                             
debug3: tty_make_modes: ispeed 38400                                                                                                             
debug1: Sending environment.                                                                                                                     
debug3: Ignored env ORBIT_SOCKETDIR                                                                                                              
debug3: Ignored env SSH_AGENT_PID                                                                                                                
debug3: Ignored env GPG_AGENT_INFO                                                                                                               
debug3: Ignored env TERM                                                                                                                         
debug3: Ignored env DESKTOP_STARTUP_ID                                                                                                           
debug3: Ignored env SHELL                                                                                                                        
debug3: Ignored env XDG_SESSION_COOKIE                                                                                                           
debug3: Ignored env KONSOLE_DBUS_SERVICE                                                                                                         
debug3: Ignored env GTK_RC_FILES                                                                                                                 
debug3: Ignored env WINDOWID                                                                                                                     
debug3: Ignored env GTK_MODULES                                                                                                                  
debug3: Ignored env USER                                                                                                                         
debug3: Ignored env LS_COLORS                                                                                                                    
debug3: Ignored env DESKTOP_AUTOSTART_ID                                                                                                         
debug3: Ignored env SSH_AUTH_SOCK                                                                                                                
debug3: Ignored env GNOME_KEYRING_SOCKET                                                                                                         
debug3: Ignored env SESSION_MANAGER                                                                                                              
debug3: Ignored env USERNAME                                                                                                                     
debug3: Ignored env PATH                                                                                                                         
debug3: Ignored env DESKTOP_SESSION                                                                                                              
debug3: Ignored env GDM_XSERVER_LOCATION                                                                                                         
debug3: Ignored env PWD                                                                                                                          
debug1: Sending env LANG = en_US.UTF-8                                                                                                           
debug2: channel 0: request env confirm 0                                                                                                         
debug3: Ignored env GNOME_KEYRING_PID                                                                                                            
debug3: Ignored env GDM_LANG                                                                                                                     
debug3: Ignored env KONSOLE_DBUS_SESSION                                                                                                         
debug3: Ignored env GDMSESSION                                                                                                                   
debug3: Ignored env HISTCONTROL                                                                                                                  
debug3: Ignored env SHLVL                                                                                                                        
debug3: Ignored env COLORFGBG                                                                                                                    
debug3: Ignored env HOME                                                                                                                         
debug3: Ignored env LANGUAGE                                                                                                                     
debug3: Ignored env GNOME_DESKTOP_SESSION_ID                                                                                                     
debug3: Ignored env LOGNAME                                                                                                                      
debug3: Ignored env XDG_DATA_DIRS                                                                                                                
debug3: Ignored env DBUS_SESSION_BUS_ADDRESS                                                                                                     
debug3: Ignored env LESSOPEN                                                                                                                     
debug3: Ignored env WINDOWPATH                                                                                                                   
debug3: Ignored env PROFILEHOME                                                                                                                  
debug3: Ignored env DISPLAY                                                                                                                      
debug3: Ignored env LESSCLOSE                                                                                                                    
debug3: Ignored env XAUTHORITY                                                                                                                   
debug3: Ignored env _                                                                                                                            
debug3: Ignored env OLDPWD                                                                                                                       
debug2: channel 0: request shell confirm 1
debug2: fd 3 setting TCP_NODELAY
debug2: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768
debug2: channel_input_confirm: type 99 id 0
debug2: PTY allocation request accepted on channel 0
debug2: channel 0: rcvd adjust 2097152
debug2: channel_input_confirm: type 99 id 0
debug2: shell request accepted on channel 0
Linux moodle 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686

SSH works, but sshfs does not.

---

### Post by moore.bryan on 2009-08-26
Now, let's check your shhfs version:
```
sshfs -V
```

---

### Post by jfreak53 on 2009-08-26
SSHFS version 2.1
FUSE library version: 2.7.4
fusermount version: 2.7.4
using FUSE kernel interface version 7.8

---

### Post by moore.bryan on 2009-08-26
Hmm... that's the latest stable.

This isn't all that's in your /etc/ssh/sshd_config is it?
> Subsystem sftp /usr/lib/openssh/sftp-serve

---

### Post by jfreak53 on 2009-08-26
No this is the complete file read out:

> # Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 22
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
PermitRootLogin yes
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile     %h/.ssh/authorized_keys

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no

# Change to no to disable tunnelled clear text passwords
#PasswordAuthentication yes

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

UsePAM yes


---

### Post by moore.bryan on 2009-08-26
The problem, then, lies with this line:
```
# What ports, IPs and protocols we listen for
Port 22
```
Change this to ```
Port 23
``` and restart the daemon ```
sudo /etc/init.d/sshd restart
```

---

### Post by moore.bryan on 2009-08-26
Double post; sorry.

---

### Post by jfreak53 on 2009-08-26
Well here is the thing, this is correct I think because of this.  That machine hosts it on port 22.  But, that is not the machine that is connected to the net.  The machine that is connected to the net and has the public IP and domain is what I connect to port 23 on, then it routes it to the other machine that is local IP on the network and port 22.  So port there doesn't matter since it is routed through another server to public internet then port 23.

Don't know if I'm right, but if I change port 22 in my config file, won't it break the link between the two servers then not allow me to connect anymore since the link was made to the port 22 on that machine?

---

### Post by moore.bryan on 2009-08-26
Wait, what?
> **jfreak53 said:**
> Well here is the thing, this is correct I think because of this.  That machine hosts it on port 22.  But, that is not the machine that is connected to the net.  The machine that is connected to the net and has the public IP and domain is what I connect to port 23 on, then it routes it to the other machine that is local IP on the network and port 22.  So port there doesn't matter since it is routed through another server to public internet then port 23.

Don't know if I'm right, but if I change port 22 in my config file, won't it break the link between the two servers then not allow me to connect anymore since the link was made to the port 22 on that machine?
So, you have three machines: one connected to the Internet & running ssh on port 22, one connected to machine one via port 23, and one which you're trying to connect to machine two?

---

### Post by jfreak53 on 2009-08-26
No sorry I think I just made this more difficult.  There are two, but I really don't think the second one matters since the ports are working the way they are for regular SSH, so this should not be a problem as far a ports go.  If the part where it says port 22 was a problem, wouldn't ssh not work at all?

Could the problem be somewhere else or is there something I need to install on the server pc for sshfs to work on a remote pc.  Some sort of ftp sub system or something of the sorts?

---

### Post by moore.bryan on 2009-08-26
I'm just a little confused about your setup, but you are right that ssh *shouldn't* be working if sshfs isn't and your /etc/ssh/sshd_config looks that way. Could you answer this for me, though: you are specifying port 23 in the command, but your /etc/ssh/sshd_config is running on port 22.

---

### Post by jfreak53 on 2009-08-26
Ok got some more light to shed on this thing, here is my log file for sshfs in auth.log:

> Aug 26 15:09:10 pc-ubuntu sudo:     user : TTY=pts/1 ; PWD=/home/**** ; USER=root ; COMMAND=/usr/bin/sshfs [email]adminuser@www.servername.com[/email]:/ /mnt/sshfs -p 23

And here is the attempt I just made to sshfs to the server in there auth.log file under sshd:

> Aug 26 15:09:10 moodle sshd[7900]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
Aug 26 15:09:10 moodle sshd[7900]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
Aug 26 15:09:10 moodle sshd[7900]: PAM adding faulty module: /lib/security/pam_smbpass.so
Aug 26 15:09:13 moodle sshd[7900]: Accepted password for admin1 from 200.12.35.148 port 55986 ssh2
Aug 26 15:09:13 moodle sshd[7903]: pam_unix(sshd:session): session opened for user adminuser by (uid=0)
Aug 26 15:09:14 moodle sshd[7903]: subsystem request for sftp
Aug 26 15:09:14 moodle sshd[7903]: error: subsystem: cannot stat /usr/libexec/openssh/sftp-server: No such file or directory
Aug 26 15:09:14 moodle sshd[7903]: subsystem request for sftp failed, subsystem not found
Aug 26 15:09:14 moodle sshd[7903]: pam_unix(sshd:session): session closed for user adminuser

---

### Post by jfreak53 on 2009-08-26
Ok so on the server if I understand my own log file, sftp file is missing?!!!!???  Ok where do I go from here, now I'm lost.

Ok let me see if I can explain this better.  There is a xubuntu server running from the ISP box with the assigned IP and domain name that brings internet into the office.

Then there is my machine, an ubuntu server running at *.1.250 that is a sub under this internet machine.  My server is sharing ssh, and everything else that on it, ssh is shared on my server at port 22.  But for me to access it under the domain name of the internet server the server admin opened port 23 on that server and sym linked it to my IP and port 22 on my machine.  This is I think because he has sshd open at 22 on the internet machine.

Soooo, my machine on local network is not internet accessible and sshd open at port 22.  The internet machine opens port 23 a links it to my local network ip at port 22 giving me access to my server through domain.

If I'm at the office running under local network I can access my server ssh through my local IP and port 22.

I don't know if I explained it right or not, I hope so.

Thanks for all your help by the way.

---

### Post by jfreak53 on 2009-08-26
Never mind I just got it, the line for sftp was bad.  I changed it from:

> Aug 26 15:09:14 moodle sshd[7903]: error: subsystem: cannot stat /usr/libexec/openssh/sftp-server: No such file or directory

To: /usr/lib/openssh/sftp-server

What I don't understand is this.  I changed that half way through my troubles.  Before it was just lib and it wasn't connecting, so I changed it to libexec to try it.  Not working, so I changed it back.  I just forgot to restart sshd to make the changes take effect the second time.  Hmm oh well it's working now.  Don't know what the problem was the first time before I ever changed it from lib to libexec.  Oh well.

Again thanks for all your help.

---

### Post by moore.bryan on 2009-08-26
That's great news! The restarting the server daemon was the key to the whole mess...

---

### Post by jfreak53 on 2009-08-26
Yeah something that simple for such a long thread.  Sorry about that.  At least I'm getting my post count up :lolflag:

Anyways thanks for all the help.

Say let's see if we can make this thread worth a little more here.  When I mount the remote filesystem it's all fine.  The problem is I cannot edit any files outside of the adminuser's home dir, the user that I login with.  I can navigate the dirs just fine, but cannot edit other than home dir of user.  I would like to be able to edit all system files using either my local user or my local root.  Right now I cannot.

I tried logging in to sshfs using [email]root@www.servername.com[/email], didn't work.  I also tried, this is kind of a stupid try but hey I tried something, I tried [email]su@www.servername.com[/email].

How do I mount it using the root user at the server so I can either, using my user here or my root here, edit the system files?

That is if there is a way, I have searched google and found nothing on this subject.  I have however found a few people who in their sshfs command user root@ and they report that it works fine no quirks.

Is there something that I have to change in my sshd_conf file for root to work?

Thanks.

---

### Post by moore.bryan on 2009-08-26
> **jfreak53 said:**
> Yeah something that simple for such a long thread.  Sorry about that.  At least I'm getting my post count up :lolflag:

Anyways thanks for all the help.
No worries... sometimes just talking/writing it out helps.
> 
Say let's see if we can make this thread worth a little more here.  When I mount the remote filesystem it's all fine.  The problem is I cannot edit any files outside of the adminuser's home dir, the user that I login with.  I can navigate the dirs just fine, but cannot edit other than home dir of user.  I would like to be able to edit all system files using either my local user or my local root.  Right now I cannot.

you could try
```
sshfs -p 23 root@www.servername.com:/ /mnt/somewhere -o allow_root
```

---

### Post by jfreak53 on 2009-08-26
Nop no go, same as before.  Just asks me for my password 3 times then says the same message as before:

> read: Connection reset by peer

The password I know is correct, it's the same as the other one.  If there a command in the conf file that is for about the same as allow_root?

:confused:

Here is the log auth.log:

> Aug 26 18:05:54 moodle sshd[8470]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
Aug 26 18:05:54 moodle sshd[8470]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
Aug 26 18:05:54 moodle sshd[8470]: PAM adding faulty module: /lib/security/pam_smbpass.so
Aug 26 18:05:57 moodle sshd[8470]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=200.12.35.148  user=root
Aug 26 18:05:59 moodle sshd[8470]: Failed password for root from 200.12.35.148 port 41257 ssh2
Aug 26 18:06:10 moodle sshd[8470]: PAM 2 more authentication failures; logname= uid=0 euid=0 tty=ssh ruser= rhost=200.12.35.148  user=root

It looks to me like it says the pass is wrong, but I'm pretty sure the pass is the same, I installed the system and I set it when I set the adminuser pass.

---

### Post by moore.bryan on 2009-08-26
> **jfreak53 said:**
> > Aug 26 18:05:54 moodle sshd[8470]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
Aug 26 18:05:54 moodle sshd[8470]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
Aug 26 18:05:54 moodle sshd[8470]: PAM adding faulty module: /lib/security/pam_smbpass.so
Aug 26 18:05:57 moodle sshd[8470]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=200.12.35.148 user=root
Aug 26 18:05:59 moodle sshd[8470]: Failed password for root from 200.12.35.148 port 41257 ssh2
Aug 26 18:06:10 moodle sshd[8470]: PAM 2 more authentication failures; logname= uid=0 euid=0 tty=ssh ruser= rhost=200.12.35.148 user=rootNow **that** is a little weird... it seems to be looking for your samba password *and* thinks you haven't given the correct root password. Can I assume you can successfully ssh with the same password with which sshfs fails to authenticate?

---

### Post by moore.bryan on 2009-08-26
So, I've been playing with my setup and although it's surely not the same as yours, the following worked for me mounting my iMac running Debian "Squeeze:"
```
sudo sshfs -o allow_root,uid=0,port=23 root@my.server.com:/ /mnt/sshfs
```Or, instead of sudo, you could just make yourself a "superuser" with ```
sudo -s
```

---

### Post by jfreak53 on 2009-08-26
Ok first post, no if I try ssh using root instead of my adminuser it also fails, same thing as sshfs as long as using root user.

I tried yours that works for you and still the same thing happens, no go.

> sudo sshfs -o allow_root,uid=0,port=23 [email]root@www.servername.com[/email]:/ /mnt/cortijo

Of course if I use adminuser instead of root then it works.  But then I cannot edit anything outside of adminusers home dir still.  Is something in the config change samba shares?  There are like 3 windows servers on the network grid, could ubuntu have auto setup somethings on install considering what it might have found on the grid?

I don't know, just grasping at straws here as of right now.

---

### Post by moore.bryan on 2009-08-27
> **jfreak53 said:**
> Ok first post, no if I try ssh using root instead of my adminuser it also fails, same thing as sshfs as long as using root user.
Okay, so what you're saying is you **cannot** ssh into your box with 
```
ssh -o allow_root,uid=0,port=23 root@www.myserver.com
```
>  Of course if I use adminuser instead of root then it works.  But then I cannot edit anything outside of adminusers home dir still.  Is something in the config change samba shares?  There are like 3 windows servers on the network grid, could ubuntu have auto setup somethings on install considering what it might have found on the grid?

I don't know, just grasping at straws here as of right now.
AFAIK, samba and ssh have nothing to do with one another; that's why I thought those authentication messages were weird. With that said, though, I don't use samba, so...

---

### Post by jfreak53 on 2009-08-27
Ok that command doesn't work, it spits out:

> command-line: line 0: Bad configuration option: allow_root,uid

But if I run this:

> ssh -o port=23 [email]root@www.servername.com[/email]

It connects but when I enter password it gives me this exact error:

> root@www.servername.com's password:
Permission denied (publickey,password).

Now from what I understand from the man pages to sshd_config, I have root allowed in my config.  So is there another config for this, maybe a root file somewhere in etc?

---

### Post by moore.bryan on 2009-08-27
That makes sense... it was my mistake; ssh doesn't have a command line *allow_root* option.

Check to see if there's a config file in /root/.ssh on your machine, since that would be the only other config file it would possibly need to read. I don't have one, but like I wrote previously, I have a command that works.

---

### Post by SoftwareExplorer on 2009-08-27
I'm pretty sure how sshfs handles permissions is that if the user you are sshing in as has permission to change the file then sshfs will let you change it. If the user you are sshing in as cant change a file, the sshfs won't let you change it either. Maybe that's your problem?

---

### Post by moore.bryan on 2009-08-27
> **SoftwareExplorer said:**
> I'm pretty sure how sshfs handles permissions is that if the user you are sshing in as has permission to change the file then sshfs will let you change it. If the user you are sshing in as cant change a file, the sshfs won't let you change it either. Maybe that's your problem?
Unfortunately, sshfs usually isn't so straight-forward; that's why you can specify the uid, gid, and umask in the options.

---

### Post by jfreak53 on 2009-08-28
Ok good news, so I got it to log in as the root user finally :P.  Now I can log into using sshfs using this command:

> sshfs -o allow_root,uid=0,port=23 [email]root@www.servername.com[/email]:/ /mnt/cortijo

Works fine let's me log in.  Funny thing is this.  I can edit root files on mount using nano editor in terminal after issuing sudo su.  But if I try to edit them using a gksu gedit command no go.  I suspect because it's as superuser and not root.  Is there any way to get around this and edit things in GUI editors as root using some sort of command?

---

### Post by moore.bryan on 2009-08-28
Excellent! I don't know if there's an easy answer to the root permissions thing... I do know *sudo su* and *sudo -s* basically do the same thing and *gksu* is just the graphical front-end to allow sudo permissions.

Glad to hear it's finally working for you!

---

### Post by alansh on 2010-07-09
I think I may have figured it out I types sshfs -d <host> <local access point>

by putting -d I got the message 'host not found'

so I edited /etc/vhosts

and added

<ip address> <host> 

which then allowed sshfs to work

---

