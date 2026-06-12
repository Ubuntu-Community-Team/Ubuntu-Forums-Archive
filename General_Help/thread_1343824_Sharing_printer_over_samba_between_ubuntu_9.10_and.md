---
title: "Sharing printer over samba between ubuntu 9.10 and windows 7 (x64)"
date: 2009-12-02
forum: General Help
---

### Post by keepitsimple2 on 2009-12-02
Greetings all!

First I apologize if this is the wrong forum. I did not see a printing error forum.

I can not make the printer, hp laserjet 1020, print over the network. I can print locally. I can print from a networked mac (albeit it is the wrong driver for the mac so it looks bad). I can not print from my laptop (windows 7 (x64). Everything is connected with a wireless router. I have set the internal ips to static ips of my choice.

Samba file sharing works. I can see the printer when browsing to the samba share. When I choose to connect to it in the samba share or add printer in "printer and devices" I get a msg: Access denied.

Here is my smb.conf:
```

[global]
    ; General server settings
    netbios name = ubuntu
    server string = Samba %v on %L
    workgroup = LILLATORGET
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    guest account = visitor
    null passwords = true
    name resolve order = hosts wins bcast
    
    wins support = no

    printing = CUPS
    printcap name = CUPS
    load printers = yes
    log level = 3


[printers]
    path = /var/spool/samba
    printable = yes
    guest ok = yes
    browseable = no
    use client driver = yes


[MyFiles]
    path = /media/samba/
    browseable = yes
    read only = yes
    guest ok = no
    create mask = 0644
    directory mask = 0755


```Here is my cupsd.conf:
```

LogLevel debug
AccessLogLevel all

MaxLogSize 0
SystemGroup lpadmin
# Allow remote access
Port 631
Listen /var/run/cups/cups.sock
# Share local printers on the local network.
Browsing On
BrowseOrder allow,deny
BrowseRemoteProtocols
BrowseAddress @LOCAL
BrowseLocalProtocols CUPS dnssd
DefaultAuthType Basic
<Location />
  # Allow shared printing...
  Order allow,deny
  Allow @LOCAL
</Location>
<Location /admin>
  # Restrict access to the admin pages...
  Order allow,deny
</Location>
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  # Restrict access to the configuration files...
  Order allow,deny
</Location>
<Policy default>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job CUPS-Get-Document>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default CUPS-Get-Devices>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Cancel-Job CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit All>
    Order deny,allow
  </Limit>
</Policy>
<Policy authenticated>
  <Limit Create-Job Print-Job Print-URI>
  AuthType Default
  Order deny,allow
</Limit>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job CUPS-Get-Document>
AuthType Default
Require user @OWNER @SYSTEM
Order deny,allow
  </Limit>
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
  AuthType Default
  Require user @SYSTEM
  Order deny,allow
    </Limit>
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
      </Limit>
  <Limit Cancel-Job CUPS-Authenticate-Job>
      AuthType Default
      Require user @OWNER @SYSTEM
      Order deny,allow
        </Limit>
  <Limit All>
        Order deny,allow
          </Limit>
</Policy>

```Here are the logs when doing an access try. First log.smbd:
```

[2009/12/02 14:24:13,  3] smbd/oplock.c:911(init_oplocks)
  init_oplocks: initializing messages.
[2009/12/02 14:24:13,  3] smbd/oplock_linux.c:219(linux_init_kernel_oplocks)
  Linux kernel oplocks enabled
[2009/12/02 14:24:13,  3] smbd/process.c:1453(process_smb)
  Transaction 0 of length 137 (0 toread)
[2009/12/02 14:24:13,  3] smbd/process.c:1272(switch_message)
  switch message SMBnegprot (pid 2958) conn 0x0
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2009/12/02 14:24:13,  3] smbd/negprot.c:567(reply_negprot)
  Requested protocol [PC NETWORK PROGRAM 1.0]
[2009/12/02 14:24:13,  3] smbd/negprot.c:567(reply_negprot)
  Requested protocol [LANMAN1.0]
[2009/12/02 14:24:13,  3] smbd/negprot.c:567(reply_negprot)
  Requested protocol [Windows for Workgroups 3.1a]
[2009/12/02 14:24:13,  3] smbd/negprot.c:567(reply_negprot)
  Requested protocol [LM1.2X002]
[2009/12/02 14:24:13,  3] smbd/negprot.c:567(reply_negprot)
  Requested protocol [LANMAN2.1]
[2009/12/02 14:24:13,  3] smbd/negprot.c:567(reply_negprot)
  Requested protocol [NT LM 0.12]
[2009/12/02 14:24:13,  3] smbd/negprot.c:387(reply_nt1)
  using SPNEGO
[2009/12/02 14:24:13,  3] smbd/negprot.c:672(reply_negprot)
  Selected protocol NT LM 0.12
[2009/12/02 14:24:13,  3] smbd/process.c:1453(process_smb)
  Transaction 1 of length 142 (0 toread)
[2009/12/02 14:24:13,  3] smbd/process.c:1272(switch_message)
  switch message SMBsesssetupX (pid 2958) conn 0x0
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2009/12/02 14:24:13,  3] smbd/sesssetup.c:1404(reply_sesssetup_and_X)
  wct=12 flg2=0xc807
[2009/12/02 14:24:13,  2] smbd/sesssetup.c:1360(setup_new_vc_session)
  setup_new_vc_session: New VC == 0, if NT4.x compatible we would close all old resources.
[2009/12/02 14:24:13,  3] smbd/sesssetup.c:1160(reply_sesssetup_and_X_spnego)
  Doing spnego session setup
[2009/12/02 14:24:13,  3] smbd/sesssetup.c:1202(reply_sesssetup_and_X_spnego)
  NativeOS=[] NativeLanMan=[] PrimaryDomain=[]
[2009/12/02 14:24:13,  3] smbd/sesssetup.c:786(reply_spnego_negotiate)
  reply_spnego_negotiate: Got secblob of size 40
[2009/12/02 14:24:13,  3] libsmb/ntlmssp.c:62(debug_ntlmssp_flags)
  Got NTLMSSP neg_flags=0xe2088297
[2009/12/02 14:24:13,  3] smbd/process.c:1453(process_smb)
  Transaction 2 of length 270 (0 toread)
[2009/12/02 14:24:13,  3] smbd/process.c:1272(switch_message)
  switch message SMBsesssetupX (pid 2958) conn 0x0
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2009/12/02 14:24:13,  3] smbd/sesssetup.c:1404(reply_sesssetup_and_X)
  wct=12 flg2=0xc807
[2009/12/02 14:24:13,  2] smbd/sesssetup.c:1360(setup_new_vc_session)
  setup_new_vc_session: New VC == 0, if NT4.x compatible we would close all old resources.
[2009/12/02 14:24:13,  3] smbd/sesssetup.c:1160(reply_sesssetup_and_X_spnego)
  Doing spnego session setup
[2009/12/02 14:24:13,  3] smbd/sesssetup.c:1202(reply_sesssetup_and_X_spnego)
  NativeOS=[] NativeLanMan=[] PrimaryDomain=[]
[2009/12/02 14:24:13,  3] libsmb/ntlmssp.c:745(ntlmssp_server_auth)
  Got user=[tveit] domain=[WINDOWS] workstation=[WINDOWS] len1=24 len2=24
[2009/12/02 14:24:13,  3] auth/auth.c:222(check_ntlm_password)
  check_ntlm_password:  Checking password for unmapped user [WINDOWS]\[tveit]@[WINDOWS] with the new password interface
[2009/12/02 14:24:13,  3] auth/auth.c:225(check_ntlm_password)
  check_ntlm_password:  mapped user is: [UBUNTU]\[tveit]@[WINDOWS]
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 2
[2009/12/02 14:24:13,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 2
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 2
[2009/12/02 14:24:13,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 2
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 2
[2009/12/02 14:24:13,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 2
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 2
[2009/12/02 14:24:13,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 2
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 2
[2009/12/02 14:24:13,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 2
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2009/12/02 14:24:13,  3] auth/auth.c:271(check_ntlm_password)
  check_ntlm_password: sam authentication for user [tveit] succeeded
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2009/12/02 14:24:13,  2] auth/auth.c:310(check_ntlm_password)
  check_ntlm_password:  authentication for user [tveit] -> [tveit] -> [tveit] succeeded
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 2
[2009/12/02 14:24:13,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 2
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 2
[2009/12/02 14:24:13,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 2
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2009/12/02 14:24:13,  3] lib/privileges.c:63(get_privileges)
  get_privileges: No privileges assigned to SID [S-1-5-21-4221726675-3625467457-3209274841-1002]
[2009/12/02 14:24:13,  3] lib/privileges.c:63(get_privileges)
  get_privileges: No privileges assigned to SID [S-1-22-2-1002]
[2009/12/02 14:24:13,  3] lib/privileges.c:63(get_privileges)
  get_privileges: No privileges assigned to SID [S-1-5-2]
[2009/12/02 14:24:13,  3] lib/privileges.c:63(get_privileges)
  get_privileges: No privileges assigned to SID [S-1-5-11]
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2009/12/02 14:24:13,  3] libsmb/ntlmssp_sign.c:342(ntlmssp_sign_init)
  NTLMSSP Sign/Seal - Initialising with flags:
[2009/12/02 14:24:13,  3] libsmb/ntlmssp.c:62(debug_ntlmssp_flags)
  Got NTLMSSP neg_flags=0xe2088215
[2009/12/02 14:24:13,  3] smbd/password.c:269(register_existing_vuid)
  register_existing_vuid: User name: tveit    Real name: 
[2009/12/02 14:24:13,  3] smbd/password.c:279(register_existing_vuid)
  register_existing_vuid: UNIX uid 1002 is UNIX user tveit, and will be vuid 100
[2009/12/02 14:24:13,  3] smbd/password.c:211(register_homes_share)
  Adding homes service for user 'tveit' using home directory: '/home/tveit'
[2009/12/02 14:24:13,  3] smbd/process.c:1453(process_smb)
  Transaction 3 of length 82 (0 toread)
[2009/12/02 14:24:13,  3] smbd/process.c:1272(switch_message)
  switch message SMBtconX (pid 2958) conn 0x0
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2009/12/02 14:24:13,  3] smbd/service.c:807(make_connection_snum)
  Connect path is '/tmp' for service [IPC$]
[2009/12/02 14:24:13,  3] smbd/vfs.c:95(vfs_init_default)
  Initialising default vfs hooks
[2009/12/02 14:24:13,  3] smbd/vfs.c:129(vfs_init_custom)
  Initialising custom vfs hooks from [/[Default VFS]/]
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (1002, 1002) - sec_ctx_stack_ndx = 0
[2009/12/02 14:24:13,  3] smbd/service.c:1047(make_connection_snum)
  windows (::ffff:192.168.1.65) connect to service IPC$ initially as user tveit (uid=1002, gid=1002) (pid 2958)
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2009/12/02 14:24:13,  3] smbd/reply.c:754(reply_tcon_and_X)
  tconX service=IPC$ 
[2009/12/02 14:24:13,  3] smbd/process.c:1453(process_smb)
  Transaction 4 of length 106 (0 toread)
[2009/12/02 14:24:13,  3] smbd/process.c:1272(switch_message)
  switch message SMBntcreateX (pid 2958) conn 0x2b87050
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (1002, 1002) - sec_ctx_stack_ndx = 0
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(1002, 1002) : sec_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(100) : conn_ctx_stack_ndx = 0
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (1002, 1002) - sec_ctx_stack_ndx = 0
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(1002, 1002) : sec_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(100) : conn_ctx_stack_ndx = 0
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (1002, 1002) - sec_ctx_stack_ndx = 0
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(1002, 1002) : sec_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(100) : conn_ctx_stack_ndx = 0
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (1002, 1002) - sec_ctx_stack_ndx = 0
[2009/12/02 14:24:13,  3] smbd/process.c:1453(process_smb)
  Transaction 5 of length 76 (0 toread)
[2009/12/02 14:24:13,  3] smbd/process.c:1272(switch_message)
  switch message SMBtrans2 (pid 2958) conn 0x2b87050
[2009/12/02 14:24:13,  3] smbd/process.c:1453(process_smb)
  Transaction 6 of length 228 (0 toread)
[2009/12/02 14:24:13,  3] smbd/process.c:1272(switch_message)
  switch message SMBwriteX (pid 2958) conn 0x2b87050
[2009/12/02 14:24:13,  3] rpc_server/srv_pipe.c:1584(api_pipe_bind_req)
  api_pipe_bind_req: \PIPE\spoolss -> \PIPE\spoolss
[2009/12/02 14:24:13,  3] rpc_server/srv_pipe.c:960(check_bind_req)
  check_bind_req for \spoolss
[2009/12/02 14:24:13,  3] smbd/pipes.c:325(pipe_write_andx_done)
  writeX-IPC nwritten=160
[2009/12/02 14:24:13,  3] smbd/process.c:1453(process_smb)
  Transaction 7 of length 63 (0 toread)
[2009/12/02 14:24:13,  3] smbd/process.c:1272(switch_message)
  switch message SMBreadX (pid 2958) conn 0x2b87050
[2009/12/02 14:24:13,  3] smbd/pipes.c:430(pipe_read_andx_done)
  readX-IPC min=1024 max=1024 nread=68
[2009/12/02 14:24:13,  3] smbd/process.c:1453(process_smb)
  Transaction 8 of length 304 (0 toread)
[2009/12/02 14:24:13,  3] smbd/process.c:1272(switch_message)
  switch message SMBtrans (pid 2958) conn 0x2b87050
[2009/12/02 14:24:13,  3] smbd/ipc.c:536(handle_trans)
  trans <\PIPE\> data=216 params=0 setup=2
[2009/12/02 14:24:13,  3] smbd/ipc.c:487(named_pipe)
  named pipe command on <> name
[2009/12/02 14:24:13,  3] smbd/ipc.c:451(api_fd_reply)
  Got API command 0x26 on pipe "spoolss" (pnum 11f3)
[2009/12/02 14:24:13,  3] rpc_server/srv_pipe_hnd.c:343(free_pipe_context)
  free_pipe_context: destroying talloc pool of size 168
[2009/12/02 14:24:13,  3] rpc_server/srv_pipe.c:2308(api_rpcTNP)
  api_rpcTNP: rpc command: SPOOLSS_OPENPRINTEREX
  checking name: \\UBUNTU\HP_LaserJet_1020
[2009/12/02 14:24:13,  3] rpc_server/srv_spoolss_nt.c:392(set_printer_hnd_printertype)
  Setting printer type=\\UBUNTU\HP_LaserJet_1020
[2009/12/02 14:24:13,  3] rpc_server/srv_pipe_hnd.c:343(free_pipe_context)
  free_pipe_context: destroying talloc pool of size 0
[2009/12/02 14:24:13,  3] smbd/process.c:1453(process_smb)
  Transaction 9 of length 106 (0 toread)
[2009/12/02 14:24:13,  3] smbd/process.c:1272(switch_message)
  switch message SMBntcreateX (pid 2958) conn 0x2b87050
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(1002, 1002) : sec_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(100) : conn_ctx_stack_ndx = 0
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (1002, 1002) - sec_ctx_stack_ndx = 0
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(1002, 1002) : sec_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(100) : conn_ctx_stack_ndx = 0
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (1002, 1002) - sec_ctx_stack_ndx = 0
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(1002, 1002) : sec_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(100) : conn_ctx_stack_ndx = 0
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (1002, 1002) - sec_ctx_stack_ndx = 0
[2009/12/02 14:24:13,  3] smbd/process.c:1453(process_smb)
  Transaction 10 of length 228 (0 toread)
[2009/12/02 14:24:13,  3] smbd/process.c:1272(switch_message)
  switch message SMBwriteX (pid 2958) conn 0x2b87050
[2009/12/02 14:24:13,  3] rpc_server/srv_pipe.c:1584(api_pipe_bind_req)
  api_pipe_bind_req: \PIPE\spoolss -> \PIPE\spoolss
[2009/12/02 14:24:13,  3] rpc_server/srv_pipe.c:960(check_bind_req)
  check_bind_req for \spoolss
[2009/12/02 14:24:13,  3] smbd/pipes.c:325(pipe_write_andx_done)
  writeX-IPC nwritten=160
[2009/12/02 14:24:13,  3] smbd/process.c:1453(process_smb)
  Transaction 11 of length 63 (0 toread)
[2009/12/02 14:24:13,  3] smbd/process.c:1272(switch_message)
  switch message SMBreadX (pid 2958) conn 0x2b87050
[2009/12/02 14:24:13,  3] smbd/pipes.c:430(pipe_read_andx_done)
  readX-IPC min=1024 max=1024 nread=68
[2009/12/02 14:24:13,  3] smbd/process.c:1453(process_smb)
  Transaction 12 of length 272 (0 toread)
[2009/12/02 14:24:13,  3] smbd/process.c:1272(switch_message)
  switch message SMBtrans (pid 2958) conn 0x2b87050
[2009/12/02 14:24:13,  3] smbd/ipc.c:536(handle_trans)
  trans <\PIPE\> data=184 params=0 setup=2
[2009/12/02 14:24:13,  3] smbd/ipc.c:487(named_pipe)
  named pipe command on <> name
[2009/12/02 14:24:13,  3] smbd/ipc.c:451(api_fd_reply)
  Got API command 0x26 on pipe "spoolss" (pnum 11f4)
[2009/12/02 14:24:13,  3] rpc_server/srv_pipe_hnd.c:343(free_pipe_context)
  free_pipe_context: destroying talloc pool of size 168
[2009/12/02 14:24:13,  3] rpc_server/srv_pipe.c:2308(api_rpcTNP)
  api_rpcTNP: rpc command: SPOOLSS_OPENPRINTEREX
  checking name: \\UBUNTU
[2009/12/02 14:24:13,  3] rpc_server/srv_spoolss_nt.c:392(set_printer_hnd_printertype)
  Setting printer type=\\UBUNTU
[2009/12/02 14:24:13,  3] rpc_server/srv_pipe_hnd.c:343(free_pipe_context)
  free_pipe_context: destroying talloc pool of size 0
[2009/12/02 14:24:13,  3] smbd/process.c:1453(process_smb)
  Transaction 13 of length 168 (0 toread)
[2009/12/02 14:24:13,  3] smbd/process.c:1272(switch_message)
  switch message SMBtrans (pid 2958) conn 0x2b87050
[2009/12/02 14:24:13,  3] smbd/ipc.c:536(handle_trans)
  trans <\PIPE\> data=80 params=0 setup=2
[2009/12/02 14:24:13,  3] smbd/ipc.c:487(named_pipe)
  named pipe command on <> name
[2009/12/02 14:24:13,  3] smbd/ipc.c:451(api_fd_reply)
  Got API command 0x26 on pipe "spoolss" (pnum 11f4)
[2009/12/02 14:24:13,  3] rpc_server/srv_pipe_hnd.c:343(free_pipe_context)
  free_pipe_context: destroying talloc pool of size 0
[2009/12/02 14:24:13,  3] rpc_server/srv_pipe.c:2308(api_rpcTNP)
  api_rpcTNP: rpc command: SPOOLSS_GETPRINTERDATA
[2009/12/02 14:24:13,  3] rpc_server/srv_pipe_hnd.c:343(free_pipe_context)
  free_pipe_context: destroying talloc pool of size 1024
[2009/12/02 14:24:13,  3] smbd/process.c:1453(process_smb)
  Transaction 14 of length 132 (0 toread)
[2009/12/02 14:24:13,  3] smbd/process.c:1272(switch_message)
  switch message SMBtrans (pid 2958) conn 0x2b87050
[2009/12/02 14:24:13,  3] smbd/ipc.c:536(handle_trans)
  trans <\PIPE\> data=44 params=0 setup=2
[2009/12/02 14:24:13,  3] smbd/ipc.c:487(named_pipe)
  named pipe command on <> name
[2009/12/02 14:24:13,  3] smbd/ipc.c:451(api_fd_reply)
  Got API command 0x26 on pipe "spoolss" (pnum 11f4)
[2009/12/02 14:24:13,  3] rpc_server/srv_pipe_hnd.c:343(free_pipe_context)
  free_pipe_context: destroying talloc pool of size 0
[2009/12/02 14:24:13,  3] rpc_server/srv_pipe.c:2308(api_rpcTNP)
  api_rpcTNP: rpc command: SPOOLSS_CLOSEPRINTER
[2009/12/02 14:24:13,  3] rpc_server/srv_lsa_hnd.c:218(close_policy_hnd)
  Closed policy
[2009/12/02 14:24:13,  3] rpc_server/srv_pipe_hnd.c:343(free_pipe_context)
  free_pipe_context: destroying talloc pool of size 0
[2009/12/02 14:24:13,  3] smbd/process.c:1453(process_smb)
  Transaction 15 of length 45 (0 toread)
[2009/12/02 14:24:13,  3] smbd/process.c:1272(switch_message)
  switch message SMBclose (pid 2958) conn 0x2b87050
[2009/12/02 14:24:13,  3] smbd/reply.c:4454(reply_close)
  close fd=-1 fnum=4596 (numopen=2)
[2009/12/02 14:24:13,  3] smbd/process.c:1453(process_smb)
  Transaction 16 of length 132 (0 toread)
[2009/12/02 14:24:13,  3] smbd/process.c:1272(switch_message)
  switch message SMBtrans (pid 2958) conn 0x2b87050
[2009/12/02 14:24:13,  3] smbd/ipc.c:536(handle_trans)
  trans <\PIPE\> data=44 params=0 setup=2
[2009/12/02 14:24:13,  3] smbd/ipc.c:487(named_pipe)
  named pipe command on <> name
[2009/12/02 14:24:13,  3] smbd/ipc.c:451(api_fd_reply)
  Got API command 0x26 on pipe "spoolss" (pnum 11f3)
[2009/12/02 14:24:13,  3] rpc_server/srv_pipe_hnd.c:343(free_pipe_context)
  free_pipe_context: destroying talloc pool of size 0
[2009/12/02 14:24:13,  3] rpc_server/srv_pipe.c:2308(api_rpcTNP)
  api_rpcTNP: rpc command: SPOOLSS_CLOSEPRINTER
[2009/12/02 14:24:13,  3] rpc_server/srv_lsa_hnd.c:218(close_policy_hnd)
  Closed policy
[2009/12/02 14:24:13,  3] rpc_server/srv_pipe_hnd.c:343(free_pipe_context)
  free_pipe_context: destroying talloc pool of size 0
[2009/12/02 14:24:13,  3] smbd/process.c:1453(process_smb)
  Transaction 17 of length 45 (0 toread)
[2009/12/02 14:24:13,  3] smbd/process.c:1272(switch_message)
  switch message SMBclose (pid 2958) conn 0x2b87050
[2009/12/02 14:24:13,  3] smbd/reply.c:4454(reply_close)
  close fd=-1 fnum=4595 (numopen=1)
[2009/12/02 14:24:13,  3] smbd/process.c:1453(process_smb)
  Transaction 18 of length 106 (0 toread)
[2009/12/02 14:24:13,  3] smbd/process.c:1272(switch_message)
  switch message SMBntcreateX (pid 2958) conn 0x2b87050
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(1002, 1002) : sec_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(100) : conn_ctx_stack_ndx = 0
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (1002, 1002) - sec_ctx_stack_ndx = 0
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(1002, 1002) : sec_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(100) : conn_ctx_stack_ndx = 0
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (1002, 1002) - sec_ctx_stack_ndx = 0
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(1002, 1002) : sec_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(100) : conn_ctx_stack_ndx = 0
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (1002, 1002) - sec_ctx_stack_ndx = 0
[2009/12/02 14:24:13,  3] smbd/process.c:1453(process_smb)
  Transaction 19 of length 76 (0 toread)
[2009/12/02 14:24:13,  3] smbd/process.c:1272(switch_message)
  switch message SMBtrans2 (pid 2958) conn 0x2b87050
[2009/12/02 14:24:13,  3] smbd/process.c:1453(process_smb)
  Transaction 20 of length 228 (0 toread)
[2009/12/02 14:24:13,  3] smbd/process.c:1272(switch_message)
  switch message SMBwriteX (pid 2958) conn 0x2b87050
[2009/12/02 14:24:13,  3] rpc_server/srv_pipe.c:1584(api_pipe_bind_req)
  api_pipe_bind_req: \PIPE\spoolss -> \PIPE\spoolss
[2009/12/02 14:24:13,  3] rpc_server/srv_pipe.c:960(check_bind_req)
  check_bind_req for \spoolss
[2009/12/02 14:24:13,  3] smbd/pipes.c:325(pipe_write_andx_done)
  writeX-IPC nwritten=160
[2009/12/02 14:24:13,  3] smbd/process.c:1453(process_smb)
  Transaction 21 of length 63 (0 toread)
[2009/12/02 14:24:13,  3] smbd/process.c:1272(switch_message)
  switch message SMBreadX (pid 2958) conn 0x2b87050
[2009/12/02 14:24:13,  3] smbd/pipes.c:430(pipe_read_andx_done)
  readX-IPC min=1024 max=1024 nread=68
[2009/12/02 14:24:13,  3] smbd/process.c:1453(process_smb)
  Transaction 22 of length 304 (0 toread)
[2009/12/02 14:24:13,  3] smbd/process.c:1272(switch_message)
  switch message SMBtrans (pid 2958) conn 0x2b87050
[2009/12/02 14:24:13,  3] smbd/ipc.c:536(handle_trans)
  trans <\PIPE\> data=216 params=0 setup=2
[2009/12/02 14:24:13,  3] smbd/ipc.c:487(named_pipe)
  named pipe command on <> name
[2009/12/02 14:24:13,  3] smbd/ipc.c:451(api_fd_reply)
  Got API command 0x26 on pipe "spoolss" (pnum 11f5)
[2009/12/02 14:24:13,  3] rpc_server/srv_pipe_hnd.c:343(free_pipe_context)
  free_pipe_context: destroying talloc pool of size 168
[2009/12/02 14:24:13,  3] rpc_server/srv_pipe.c:2308(api_rpcTNP)
  api_rpcTNP: rpc command: SPOOLSS_OPENPRINTEREX
  checking name: \\UBUNTU\HP_LaserJet_1020
[2009/12/02 14:24:13,  3] rpc_server/srv_spoolss_nt.c:392(set_printer_hnd_printertype)
  Setting printer type=\\UBUNTU\HP_LaserJet_1020
[2009/12/02 14:24:13,  3] rpc_server/srv_pipe_hnd.c:343(free_pipe_context)
  free_pipe_context: destroying talloc pool of size 0
[2009/12/02 14:24:13,  3] smbd/process.c:1453(process_smb)
  Transaction 23 of length 144 (0 toread)
[2009/12/02 14:24:13,  3] smbd/process.c:1272(switch_message)
  switch message SMBtrans (pid 2958) conn 0x2b87050
[2009/12/02 14:24:13,  3] smbd/ipc.c:536(handle_trans)
  trans <\PIPE\> data=56 params=0 setup=2
[2009/12/02 14:24:13,  3] smbd/ipc.c:487(named_pipe)
  named pipe command on <> name
[2009/12/02 14:24:13,  3] smbd/ipc.c:451(api_fd_reply)
  Got API command 0x26 on pipe "spoolss" (pnum 11f5)
[2009/12/02 14:24:13,  3] rpc_server/srv_pipe_hnd.c:343(free_pipe_context)
  free_pipe_context: destroying talloc pool of size 0
[2009/12/02 14:24:13,  3] rpc_server/srv_pipe.c:2308(api_rpcTNP)
  api_rpcTNP: rpc command: SPOOLSS_GETPRINTER
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(1002, 1002) : sec_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(100) : conn_ctx_stack_ndx = 0
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (1002, 1002) - sec_ctx_stack_ndx = 0
[2009/12/02 14:24:13,  3] rpc_server/srv_pipe_hnd.c:343(free_pipe_context)
  free_pipe_context: destroying talloc pool of size 774
[2009/12/02 14:24:13,  3] printing/printing.c:1156(print_queue_update_internal)
  print_queue_update_internal: 0 jobs in queue for HP_LaserJet_1020
[2009/12/02 14:24:13,  3] smbd/process.c:1453(process_smb)
  Transaction 24 of length 1156 (0 toread)
[2009/12/02 14:24:13,  3] smbd/process.c:1272(switch_message)
  switch message SMBtrans (pid 2958) conn 0x2b87050
[2009/12/02 14:24:13,  3] smbd/ipc.c:536(handle_trans)
  trans <\PIPE\> data=1068 params=0 setup=2
[2009/12/02 14:24:13,  3] smbd/ipc.c:487(named_pipe)
  named pipe command on <> name
[2009/12/02 14:24:13,  3] smbd/ipc.c:451(api_fd_reply)
  Got API command 0x26 on pipe "spoolss" (pnum 11f5)
[2009/12/02 14:24:13,  3] rpc_server/srv_pipe_hnd.c:343(free_pipe_context)
  free_pipe_context: destroying talloc pool of size 0
[2009/12/02 14:24:13,  3] rpc_server/srv_pipe.c:2308(api_rpcTNP)
  api_rpcTNP: rpc command: SPOOLSS_GETPRINTER
[2009/12/02 14:24:13,  3] rpc_server/srv_pipe_hnd.c:343(free_pipe_context)
  free_pipe_context: destroying talloc pool of size 774
[2009/12/02 14:24:13,  3] smbd/error.c:60(error_packet_set)
  error packet at smbd/ipc.c(132) cmd=37 (SMBtrans) STATUS_BUFFER_OVERFLOW
[2009/12/02 14:24:13,  3] smbd/process.c:1453(process_smb)
  Transaction 25 of length 63 (0 toread)
[2009/12/02 14:24:13,  3] smbd/process.c:1272(switch_message)
  switch message SMBreadX (pid 2958) conn 0x2b87050
[2009/12/02 14:24:13,  3] smbd/pipes.c:430(pipe_read_andx_done)
  readX-IPC min=24 max=24 nread=24
[2009/12/02 14:24:13,  3] smbd/process.c:1453(process_smb)
  Transaction 26 of length 132 (0 toread)
[2009/12/02 14:24:13,  3] smbd/process.c:1272(switch_message)
  switch message SMBtrans (pid 2958) conn 0x2b87050
[2009/12/02 14:24:13,  3] smbd/ipc.c:536(handle_trans)
  trans <\PIPE\> data=44 params=0 setup=2
[2009/12/02 14:24:13,  3] smbd/ipc.c:487(named_pipe)
  named pipe command on <> name
[2009/12/02 14:24:13,  3] smbd/ipc.c:451(api_fd_reply)
  Got API command 0x26 on pipe "spoolss" (pnum 11f5)
[2009/12/02 14:24:13,  3] rpc_server/srv_pipe_hnd.c:343(free_pipe_context)
  free_pipe_context: destroying talloc pool of size 0
[2009/12/02 14:24:13,  3] rpc_server/srv_pipe.c:2308(api_rpcTNP)
  api_rpcTNP: rpc command: SPOOLSS_CLOSEPRINTER
[2009/12/02 14:24:13,  3] rpc_server/srv_lsa_hnd.c:218(close_policy_hnd)
  Closed policy
[2009/12/02 14:24:13,  3] rpc_server/srv_pipe_hnd.c:343(free_pipe_context)
  free_pipe_context: destroying talloc pool of size 0
[2009/12/02 14:24:13,  3] smbd/process.c:1453(process_smb)
  Transaction 27 of length 45 (0 toread)
[2009/12/02 14:24:13,  3] smbd/process.c:1272(switch_message)
  switch message SMBclose (pid 2958) conn 0x2b87050
[2009/12/02 14:24:13,  3] smbd/reply.c:4454(reply_close)
  close fd=-1 fnum=4597 (numopen=1)
[2009/12/02 14:24:13,  3] smbd/process.c:1453(process_smb)
  Transaction 28 of length 106 (0 toread)
[2009/12/02 14:24:13,  3] smbd/process.c:1272(switch_message)
  switch message SMBntcreateX (pid 2958) conn 0x2b87050
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(1002, 1002) : sec_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(100) : conn_ctx_stack_ndx = 0
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (1002, 1002) - sec_ctx_stack_ndx = 0
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(1002, 1002) : sec_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(100) : conn_ctx_stack_ndx = 0
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (1002, 1002) - sec_ctx_stack_ndx = 0
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(1002, 1002) : sec_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(100) : conn_ctx_stack_ndx = 0
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2009/12/02 14:24:13,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (1002, 1002) - sec_ctx_stack_ndx = 0
[2009/12/02 14:24:13,  3] smbd/process.c:1453(process_smb)
  Transaction 29 of length 76 (0 toread)
[2009/12/02 14:24:13,  3] smbd/process.c:1272(switch_message)
  switch message SMBtrans2 (pid 2958) conn 0x2b87050
[2009/12/02 14:24:13,  3] smbd/process.c:1453(process_smb)
  Transaction 30 of length 228 (0 toread)
[2009/12/02 14:24:13,  3] smbd/process.c:1272(switch_message)
  switch message SMBwriteX (pid 2958) conn 0x2b87050
[2009/12/02 14:24:13,  3] rpc_server/srv_pipe.c:1584(api_pipe_bind_req)
  api_pipe_bind_req: \PIPE\spoolss -> \PIPE\spoolss
[2009/12/02 14:24:13,  3] rpc_server/srv_pipe.c:960(check_bind_req)
  check_bind_req for \spoolss
[2009/12/02 14:24:13,  3] smbd/pipes.c:325(pipe_write_andx_done)
  writeX-IPC nwritten=160
[2009/12/02 14:24:14,  3] smbd/process.c:1453(process_smb)
  Transaction 31 of length 63 (0 toread)
[2009/12/02 14:24:14,  3] smbd/process.c:1272(switch_message)
  switch message SMBreadX (pid 2958) conn 0x2b87050
[2009/12/02 14:24:14,  3] smbd/pipes.c:430(pipe_read_andx_done)
  readX-IPC min=1024 max=1024 nread=68
[2009/12/02 14:24:14,  3] smbd/process.c:1453(process_smb)
  Transaction 32 of length 304 (0 toread)
[2009/12/02 14:24:14,  3] smbd/process.c:1272(switch_message)
  switch message SMBtrans (pid 2958) conn 0x2b87050
[2009/12/02 14:24:14,  3] smbd/ipc.c:536(handle_trans)
  trans <\PIPE\> data=216 params=0 setup=2
[2009/12/02 14:24:14,  3] smbd/ipc.c:487(named_pipe)
  named pipe command on <> name
[2009/12/02 14:24:14,  3] smbd/ipc.c:451(api_fd_reply)
  Got API command 0x26 on pipe "spoolss" (pnum 11f6)
[2009/12/02 14:24:14,  3] rpc_server/srv_pipe_hnd.c:343(free_pipe_context)
  free_pipe_context: destroying talloc pool of size 168
[2009/12/02 14:24:14,  3] rpc_server/srv_pipe.c:2308(api_rpcTNP)
  api_rpcTNP: rpc command: SPOOLSS_OPENPRINTEREX
  checking name: \\UBUNTU\HP_LaserJet_1020
[2009/12/02 14:24:14,  3] rpc_server/srv_spoolss_nt.c:392(set_printer_hnd_printertype)
  Setting printer type=\\UBUNTU\HP_LaserJet_1020
[2009/12/02 14:24:14,  3] rpc_server/srv_pipe_hnd.c:343(free_pipe_context)
  free_pipe_context: destroying talloc pool of size 0
[2009/12/02 14:24:14,  3] smbd/process.c:1453(process_smb)
  Transaction 33 of length 4244 (0 toread)
[2009/12/02 14:24:14,  3] smbd/process.c:1272(switch_message)
  switch message SMBtrans (pid 2958) conn 0x2b87050
[2009/12/02 14:24:14,  3] smbd/ipc.c:536(handle_trans)
  trans <\PIPE\> data=4156 params=0 setup=2
[2009/12/02 14:24:14,  3] smbd/ipc.c:487(named_pipe)
  named pipe command on <> name
[2009/12/02 14:24:14,  3] smbd/ipc.c:451(api_fd_reply)
  Got API command 0x26 on pipe "spoolss" (pnum 11f6)
[2009/12/02 14:24:14,  3] rpc_server/srv_pipe_hnd.c:343(free_pipe_context)
  free_pipe_context: destroying talloc pool of size 0
[2009/12/02 14:24:14,  3] rpc_server/srv_pipe.c:2308(api_rpcTNP)
  api_rpcTNP: rpc command: SPOOLSS_GETPRINTER
[2009/12/02 14:24:14,  3] rpc_server/srv_pipe_hnd.c:343(free_pipe_context)
  free_pipe_context: destroying talloc pool of size 774
[2009/12/02 14:24:14,  3] smbd/error.c:60(error_packet_set)
  error packet at smbd/ipc.c(132) cmd=37 (SMBtrans) STATUS_BUFFER_OVERFLOW
[2009/12/02 14:24:14,  3] smbd/process.c:1453(process_smb)
  Transaction 34 of length 63 (0 toread)
[2009/12/02 14:24:14,  3] smbd/process.c:1272(switch_message)
  switch message SMBreadX (pid 2958) conn 0x2b87050
[2009/12/02 14:24:14,  3] smbd/pipes.c:430(pipe_read_andx_done)
  readX-IPC min=3112 max=3112 nread=3112
[2009/12/02 14:24:14,  3] smbd/process.c:1453(process_smb)
  Transaction 35 of length 132 (0 toread)
[2009/12/02 14:24:14,  3] smbd/process.c:1272(switch_message)
  switch message SMBtrans (pid 2958) conn 0x2b87050
[2009/12/02 14:24:14,  3] smbd/ipc.c:536(handle_trans)
  trans <\PIPE\> data=44 params=0 setup=2
[2009/12/02 14:24:14,  3] smbd/ipc.c:487(named_pipe)
  named pipe command on <> name
[2009/12/02 14:24:14,  3] smbd/ipc.c:451(api_fd_reply)
  Got API command 0x26 on pipe "spoolss" (pnum 11f6)
[2009/12/02 14:24:14,  3] rpc_server/srv_pipe_hnd.c:343(free_pipe_context)
  free_pipe_context: destroying talloc pool of size 0
[2009/12/02 14:24:14,  3] rpc_server/srv_pipe.c:2308(api_rpcTNP)
  api_rpcTNP: rpc command: SPOOLSS_CLOSEPRINTER
[2009/12/02 14:24:14,  3] rpc_server/srv_lsa_hnd.c:218(close_policy_hnd)
  Closed policy
[2009/12/02 14:24:14,  3] rpc_server/srv_pipe_hnd.c:343(free_pipe_context)
  free_pipe_context: destroying talloc pool of size 0
[2009/12/02 14:24:14,  3] smbd/process.c:1453(process_smb)
  Transaction 36 of length 45 (0 toread)
[2009/12/02 14:24:14,  3] smbd/process.c:1272(switch_message)
  switch message SMBclose (pid 2958) conn 0x2b87050
[2009/12/02 14:24:14,  3] smbd/reply.c:4454(reply_close)
  close fd=-1 fnum=4598 (numopen=1)
[2009/12/02 14:24:14,  3] smbd/process.c:1453(process_smb)
  Transaction 37 of length 106 (0 toread)
[2009/12/02 14:24:14,  3] smbd/process.c:1272(switch_message)
  switch message SMBntcreateX (pid 2958) conn 0x2b87050
[2009/12/02 14:24:14,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(1002, 1002) : sec_ctx_stack_ndx = 1
[2009/12/02 14:24:14,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(100) : conn_ctx_stack_ndx = 0
[2009/12/02 14:24:14,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2009/12/02 14:24:14,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (1002, 1002) - sec_ctx_stack_ndx = 0
[2009/12/02 14:24:14,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(1002, 1002) : sec_ctx_stack_ndx = 1
[2009/12/02 14:24:14,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(100) : conn_ctx_stack_ndx = 0
[2009/12/02 14:24:14,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2009/12/02 14:24:14,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (1002, 1002) - sec_ctx_stack_ndx = 0
[2009/12/02 14:24:14,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(1002, 1002) : sec_ctx_stack_ndx = 1
[2009/12/02 14:24:14,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(100) : conn_ctx_stack_ndx = 0
[2009/12/02 14:24:14,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2009/12/02 14:24:14,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (1002, 1002) - sec_ctx_stack_ndx = 0
[2009/12/02 14:24:14,  3] smbd/process.c:1453(process_smb)
  Transaction 38 of length 76 (0 toread)
[2009/12/02 14:24:14,  3] smbd/process.c:1272(switch_message)
  switch message SMBtrans2 (pid 2958) conn 0x2b87050
[2009/12/02 14:24:14,  3] smbd/process.c:1453(process_smb)
  Transaction 39 of length 228 (0 toread)
[2009/12/02 14:24:14,  3] smbd/process.c:1272(switch_message)
  switch message SMBwriteX (pid 2958) conn 0x2b87050
[2009/12/02 14:24:14,  3] rpc_server/srv_pipe.c:1584(api_pipe_bind_req)
  api_pipe_bind_req: \PIPE\spoolss -> \PIPE\spoolss
[2009/12/02 14:24:14,  3] rpc_server/srv_pipe.c:960(check_bind_req)
  check_bind_req for \spoolss
[2009/12/02 14:24:14,  3] smbd/pipes.c:325(pipe_write_andx_done)
  writeX-IPC nwritten=160
[2009/12/02 14:24:14,  3] smbd/process.c:1453(process_smb)
  Transaction 40 of length 63 (0 toread)
[2009/12/02 14:24:14,  3] smbd/process.c:1272(switch_message)
  switch message SMBreadX (pid 2958) conn 0x2b87050
[2009/12/02 14:24:14,  3] smbd/pipes.c:430(pipe_read_andx_done)
  readX-IPC min=1024 max=1024 nread=68
[2009/12/02 14:24:14,  3] smbd/process.c:1453(process_smb)
  Transaction 41 of length 304 (0 toread)
[2009/12/02 14:24:14,  3] smbd/process.c:1272(switch_message)
  switch message SMBtrans (pid 2958) conn 0x2b87050
[2009/12/02 14:24:14,  3] smbd/ipc.c:536(handle_trans)
  trans <\PIPE\> data=216 params=0 setup=2
[2009/12/02 14:24:14,  3] smbd/ipc.c:487(named_pipe)
  named pipe command on <> name
[2009/12/02 14:24:14,  3] smbd/ipc.c:451(api_fd_reply)
  Got API command 0x26 on pipe "spoolss" (pnum 11f7)
[2009/12/02 14:24:14,  3] rpc_server/srv_pipe_hnd.c:343(free_pipe_context)
  free_pipe_context: destroying talloc pool of size 168
[2009/12/02 14:24:14,  3] rpc_server/srv_pipe.c:2308(api_rpcTNP)
  api_rpcTNP: rpc command: SPOOLSS_OPENPRINTEREX
  checking name: \\UBUNTU\HP_LaserJet_1020
[2009/12/02 14:24:14,  3] rpc_server/srv_spoolss_nt.c:392(set_printer_hnd_printertype)
  Setting printer type=\\UBUNTU\HP_LaserJet_1020
[2009/12/02 14:24:14,  3] rpc_server/srv_pipe_hnd.c:343(free_pipe_context)
  free_pipe_context: destroying talloc pool of size 0
[2009/12/02 14:24:14,  3] smbd/process.c:1453(process_smb)
  Transaction 42 of length 4244 (0 toread)
[2009/12/02 14:24:14,  3] smbd/process.c:1272(switch_message)
  switch message SMBtrans (pid 2958) conn 0x2b87050
[2009/12/02 14:24:14,  3] smbd/ipc.c:536(handle_trans)
  trans <\PIPE\> data=4156 params=0 setup=2
[2009/12/02 14:24:14,  3] smbd/ipc.c:487(named_pipe)
  named pipe command on <> name
[2009/12/02 14:24:14,  3] smbd/ipc.c:451(api_fd_reply)
  Got API command 0x26 on pipe "spoolss" (pnum 11f7)
[2009/12/02 14:24:14,  3] rpc_server/srv_pipe_hnd.c:343(free_pipe_context)
  free_pipe_context: destroying talloc pool of size 0
[2009/12/02 14:24:14,  3] rpc_server/srv_pipe.c:2308(api_rpcTNP)
  api_rpcTNP: rpc command: SPOOLSS_GETPRINTER
[2009/12/02 14:24:14,  3] rpc_server/srv_pipe_hnd.c:343(free_pipe_context)
  free_pipe_context: destroying talloc pool of size 774
[2009/12/02 14:24:14,  3] smbd/error.c:60(error_packet_set)
  error packet at smbd/ipc.c(132) cmd=37 (SMBtrans) STATUS_BUFFER_OVERFLOW
[2009/12/02 14:24:14,  3] smbd/process.c:1453(process_smb)
  Transaction 43 of length 63 (0 toread)
[2009/12/02 14:24:14,  3] smbd/process.c:1272(switch_message)
  switch message SMBreadX (pid 2958) conn 0x2b87050
[2009/12/02 14:24:14,  3] smbd/pipes.c:430(pipe_read_andx_done)
  readX-IPC min=3112 max=3112 nread=3112
[2009/12/02 14:24:14,  3] smbd/process.c:1453(process_smb)
  Transaction 44 of length 132 (0 toread)
[2009/12/02 14:24:14,  3] smbd/process.c:1272(switch_message)
  switch message SMBtrans (pid 2958) conn 0x2b87050
[2009/12/02 14:24:14,  3] smbd/ipc.c:536(handle_trans)
  trans <\PIPE\> data=44 params=0 setup=2
[2009/12/02 14:24:14,  3] smbd/ipc.c:487(named_pipe)
  named pipe command on <> name
[2009/12/02 14:24:14,  3] smbd/ipc.c:451(api_fd_reply)
  Got API command 0x26 on pipe "spoolss" (pnum 11f7)
[2009/12/02 14:24:14,  3] rpc_server/srv_pipe_hnd.c:343(free_pipe_context)
  free_pipe_context: destroying talloc pool of size 0
[2009/12/02 14:24:14,  3] rpc_server/srv_pipe.c:2308(api_rpcTNP)
  api_rpcTNP: rpc command: SPOOLSS_CLOSEPRINTER
[2009/12/02 14:24:14,  3] rpc_server/srv_lsa_hnd.c:218(close_policy_hnd)
  Closed policy
[2009/12/02 14:24:14,  3] rpc_server/srv_pipe_hnd.c:343(free_pipe_context)
  free_pipe_context: destroying talloc pool of size 0
[2009/12/02 14:24:14,  3] smbd/process.c:1453(process_smb)
  Transaction 45 of length 45 (0 toread)
[2009/12/02 14:24:14,  3] smbd/process.c:1272(switch_message)
  switch message SMBclose (pid 2958) conn 0x2b87050
[2009/12/02 14:24:14,  3] smbd/reply.c:4454(reply_close)
  close fd=-1 fnum=4599 (numopen=1)
[2009/12/02 14:24:28,  3] smbd/process.c:1453(process_smb)
  Transaction 46 of length 39 (0 toread)
[2009/12/02 14:24:28,  3] smbd/process.c:1272(switch_message)
  switch message SMBtdis (pid 2958) conn 0x2b87050
[2009/12/02 14:24:28,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2009/12/02 14:24:28,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2009/12/02 14:24:28,  3] smbd/service.c:1226(close_cnum)
  windows (::ffff:192.168.1.65) closed connection to service IPC$
[2009/12/02 14:24:28,  3] smbd/connection.c:31(yield_connection)
  Yielding connection to IPC$
[2009/12/02 14:24:28,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0

```And for error_log (cups)
```

[02/Dec/2009:14:24:13 +0100] cupsdAcceptClient: 12 from localhost (Domain)
D [02/Dec/2009:14:24:13 +0100] cupsdReadClient: 12 WAITING Closing on EOF
D [02/Dec/2009:14:24:13 +0100] cupsdCloseClient: 12
D [02/Dec/2009:14:24:13 +0100] cupsdAcceptClient: 12 from localhost (Domain)
D [02/Dec/2009:14:24:13 +0100] cupsdAcceptClient: 14 from localhost (Domain)
D [02/Dec/2009:14:24:13 +0100] cupsdReadClient: 12 WAITING Closing on EOF
D [02/Dec/2009:14:24:13 +0100] cupsdCloseClient: 12
D [02/Dec/2009:14:24:13 +0100] cupsdReadClient: 14 POST / HTTP/1.1
D [02/Dec/2009:14:24:13 +0100] cupsdSetBusyState: Active clients
D [02/Dec/2009:14:24:13 +0100] cupsdAuthorize: No authentication data provided.
D [02/Dec/2009:14:24:13 +0100] cupsdReadClient: 14 1.1 Get-Jobs 1
D [02/Dec/2009:14:24:13 +0100] Get-Jobs ipp://localhost/printers/HP_LaserJet_1020
D [02/Dec/2009:14:24:13 +0100] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/HP_LaserJet_1020) from localhost
D [02/Dec/2009:14:24:13 +0100] cupsdSetBusyState: Not busy
D [02/Dec/2009:14:24:13 +0100] cupsdReadClient: 14 POST / HTTP/1.1
D [02/Dec/2009:14:24:13 +0100] cupsdSetBusyState: Active clients
D [02/Dec/2009:14:24:13 +0100] cupsdAuthorize: No authentication data provided.
D [02/Dec/2009:14:24:13 +0100] cupsdReadClient: 14 1.1 Get-Printer-Attributes 1
D [02/Dec/2009:14:24:13 +0100] Get-Printer-Attributes ipp://localhost/printers/HP_LaserJet_1020
D [02/Dec/2009:14:24:13 +0100] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/HP_LaserJet_1020) from localhost
D [02/Dec/2009:14:24:13 +0100] cupsdSetBusyState: Not busy
D [02/Dec/2009:14:24:13 +0100] cupsdReadClient: 14 WAITING Closing on EOF
D [02/Dec/2009:14:24:13 +0100] cupsdCloseClient: 14
D [02/Dec/2009:14:24:13 +0100] cupsdAcceptClient: 12 from localhost (Domain)
D [02/Dec/2009:14:24:13 +0100] cupsdReadClient: 12 WAITING Closing on EOF
D [02/Dec/2009:14:24:13 +0100] cupsdCloseClient: 12
D [02/Dec/2009:14:24:13 +0100] cupsdAcceptClient: 12 from localhost (Domain)
D [02/Dec/2009:14:24:13 +0100] cupsdReadClient: 12 WAITING Closing on EOF
D [02/Dec/2009:14:24:13 +0100] cupsdCloseClient: 12
D [02/Dec/2009:14:24:14 +0100] cupsdAcceptClient: 12 from localhost (Domain)
D [02/Dec/2009:14:24:14 +0100] cupsdReadClient: 12 WAITING Closing on EOF
D [02/Dec/2009:14:24:14 +0100] cupsdCloseClient: 12
D [02/Dec/2009:14:24:14 +0100] cupsdAcceptClient: 12 from localhost (Domain)
D [02/Dec/2009:14:24:14 +0100] cupsdReadClient: 12 WAITING Closing on EOF
D [02/Dec/2009:14:24:14 +0100] cupsdCloseClient: 12
D [02/Dec/2009:14:24:14 +0100] cupsdAcceptClient: 12 from localhost (Domain)
D [02/Dec/2009:14:24:14 +0100] cupsdReadClient: 12 WAITING Closing on EOF
D [02/Dec/2009:14:24:14 +0100] cupsdCloseClient: 12
D [02/Dec/2009:14:24:14 +0100] cupsdAcceptClient: 12 from localhost (Domain)
D [02/Dec/2009:14:24:14 +0100] cupsdReadClient: 12 WAITING Closing on EOF
D [02/Dec/2009:14:24:14 +0100] cupsdCloseClient: 12
D [02/Dec/2009:14:24:19 +0100] cupsdNetIFUpdate: "lo" = localhost:631
D [02/Dec/2009:14:24:19 +0100] cupsdNetIFUpdate: "wlan0" = 192.168.1.66:631
D [02/Dec/2009:14:24:19 +0100] cupsdNetIFUpdate: "lo" = localhost:631
D [02/Dec/2009:14:24:19 +0100] cupsdNetIFUpdate: "wlan0" = fe80::215:afff:fe03:5c1b%wlan0:631
D [02/Dec/2009:14:24:19 +0100] Report: clients=0
D [02/Dec/2009:14:24:19 +0100] Report: jobs=9
D [02/Dec/2009:14:24:19 +0100] Report: jobs-active=0
D [02/Dec/2009:14:24:19 +0100] Report: printers=1
D [02/Dec/2009:14:24:19 +0100] Report: printers-implicit=0
D [02/Dec/2009:14:24:19 +0100] Report: stringpool-string-count=293
D [02/Dec/2009:14:24:19 +0100] Report: stringpool-alloc-bytes=6592
D [02/Dec/2009:14:24:19 +0100] Report: stringpool-total-bytes=6608
D [02/Dec/2009:14:25:21 +0100] cupsdNetIFUpdate: "lo" = localhost:631
D [02/Dec/2009:14:25:21 +0100] cupsdNetIFUpdate: "wlan0" = 192.168.1.66:631
D [02/Dec/2009:14:25:21 +0100] cupsdNetIFUpdate: "lo" = localhost:631
D [02/Dec/2009:14:25:21 +0100] cupsdNetIFUpdate: "wlan0" = fe80::215:afff:fe03:5c1b%wlan0:631
D [02/Dec/2009:14:25:21 +0100] Report: clients=0
D [02/Dec/2009:14:25:21 +0100] Report: jobs=9
D [02/Dec/2009:14:25:21 +0100] Report: jobs-active=0
D [02/Dec/2009:14:25:21 +0100] Report: printers=1
D [02/Dec/2009:14:25:21 +0100] Report: printers-implicit=0
D [02/Dec/2009:14:25:21 +0100] Report: stringpool-string-count=293
D [02/Dec/2009:14:25:21 +0100] Report: stringpool-alloc-bytes=6592
D [02/Dec/2009:14:25:21 +0100] Report: stringpool-total-bytes=6608
D [02/Dec/2009:14:26:23 +0100] cupsdNetIFUpdate: "lo" = localhost:631
D [02/Dec/2009:14:26:23 +0100] cupsdNetIFUpdate: "wlan0" = 192.168.1.66:631
D [02/Dec/2009:14:26:23 +0100] cupsdNetIFUpdate: "lo" = localhost:631
D [02/Dec/2009:14:26:23 +0100] cupsdNetIFUpdate: "wlan0" = fe80::215:afff:fe03:5c1b%wlan0:631
D [02/Dec/2009:14:26:23 +0100] Report: clients=0
D [02/Dec/2009:14:26:23 +0100] Report: jobs=9
D [02/Dec/2009:14:26:23 +0100] Report: jobs-active=0
D [02/Dec/2009:14:26:23 +0100] Report: printers=1
D [02/Dec/2009:14:26:23 +0100] Report: printers-implicit=0
D [02/Dec/2009:14:26:23 +0100] Report: stringpool-string-count=293
D [02/Dec/2009:14:26:23 +0100] Report: stringpool-alloc-bytes=6592
D [02/Dec/2009:14:26:23 +0100] Report: stringpool-total-bytes=6608

```Thanks for reading!! :) 

If you need any other logs/settings let me know.

---

### Post by keepitsimple2 on 2009-12-04
partly solved. As I said before. I can see the printer in the samba share (Its not there when samba is down so its not cups broadcastin g.). I could however not connect to it. I solved it by adding the printer as a local! port (in windows 7) and the port name to \\servername\printername (in my case \\ubuntu\HP_Laserjet_1020). Extremely strange. Right now it is working about 1/2. I wonder if it has anything to do with the printer needs firmware with every print since its internal memory is too small (or so I read somewhere).

---

### Post by keepitsimple2 on 2009-12-07
Seems like I am unable to install the printer for mac. Is it possible to automate the printing in some way to make the server print instead of the mac like this.

Print from mac => Sending printfile to server  => User on the server prints.

Maybe something like automatically convert everything to pdf that is printed and then use lpr file.pdf?

---

