---
title: "share wont show on windows ect"
date: 2009-11-11
forum: General Help
---

### Post by muggisan on 2009-11-11
hi,
first of all I dunno if its the right subforum, but a got a NAS server thats runs a version of ubuntu. Its a Qnap ts-639 Pro, and the qnap forum havnt been any help yet and i'm desperate to find a resolution after almost 2 weeks.
 
 
Ok to make it short (copied form the Qnap forum).
 
"After 2 disk disconnect and 2 rebuild (raid 5) of a newly brought qnap 639, somehow my shares are screwed.
I have used over a week to solve the problem , but no luck so far. 
i'll sum it up here.
 
1. Im not able to save permission in the qnap webbrowers anymore for users, shared folders ect.
Have to do that manually via ssh in the smb.conf.
2. I cant see the shares under windows xp and windows 7 anymore (same goes for 3 version of Linux) . Thats under the homegroup/workgroup.
 
3. I can see the shares via FTP
 
4. The NFS share dosnt work either
 
Here is my smb.conf file that I think is screwed, hope anyone can help.
comment to the smb file, the only share I have shares dir in, is the MD0_data,
i dunno why all the other [FONT=Courier New]<Directory "/share/HDU_DATA"> [/FONT][FONT=Verdana]ect are there.[/FONT]
[FONT=Verdana]Bare with me if im off target in this forum as im a noob.[/FONT]
 
EDIT: so my question is, how do I in ubuntu (what files do i have to edit) manually set up,
so windows can se my shares pr default under "workgroup" ?
 
[FONT=Courier New]> [FONT=Courier New]ServerName "ProFTPD"[/FONT]
[FONT=Courier New]ServerType standalone[/FONT]
[FONT=Courier New]DefaultServer on[/FONT]
[FONT=Courier New]RootLogin on[/FONT]
[FONT=Courier New]Port 21[/FONT]
[FONT=Courier New]MaxInstances 10[/FONT]
[FONT=Courier New]User guest[/FONT]
[FONT=Courier New]Group guest[/FONT]
[FONT=Courier New]DefaultRoot /share[/FONT]
[FONT=Courier New]Umask 000[/FONT]
[FONT=Courier New]ShowSymlinks off[/FONT]
[FONT=Courier New]AllowOverwrite on[/FONT]
[FONT=Courier New]TimesGMT off[/FONT]
[FONT=Courier New]UseReverseDNS off[/FONT]
[FONT=Courier New]WtmpLog off[/FONT]
[FONT=Courier New]AllowStoreRestart on[/FONT]
[FONT=Courier New]TransferLog NONE[/FONT]
[FONT=Courier New]UseReverseDNS off[/FONT]
[FONT=Courier New]IdentLookups off[/FONT]
[FONT=Courier New]DisplayLogin welcome.msg[/FONT]
[FONT=Courier New]CharsetLocal UTF-8[/FONT]
[FONT=Courier New]CharsetRemote ASCII[/FONT]
[FONT=Courier New]UseUTF8 off[/FONT]
[FONT=Courier New]TLSEngine off[/FONT]
[FONT=Courier New]TLSRequired off[/FONT]
[FONT=Courier New]TLSRSACertificateFile /etc/ssl/certs/myhost.crt[/FONT]
[FONT=Courier New]TLSRSACertificateKeyFile /etc/ssl/private/myhost.key[/FONT]
[FONT=Courier New]TLSCACertificateFile /etc/ssl/certs/myrootca.crt[/FONT]
[FONT=Courier New]TLSOptions NoCertRequest[/FONT]
[FONT=Courier New]TLSVerifyClient off[/FONT]
[FONT=Courier New]PassivePorts 55536 56559[/FONT]
[FONT=Courier New]MaxClientsPerUser 2[/FONT]
[FONT=Courier New]EnableUserWanIp off[/FONT]
[FONT=Courier New]AllowForeignAddress on[/FONT]
[FONT=Courier New]<Limit LOGIN>[/FONT]
[FONT=Courier New]DenyGroup "guest"[/FONT]
[FONT=Courier New]DenyUser "guest"[/FONT]
[FONT=Courier New]</Limit>[/FONT]
[FONT=Courier New]<Directory "/share/HDO_DATA">[/FONT]
[FONT=Courier New]<Limit ALL>[/FONT]
[FONT=Courier New]DenyAll[/FONT]
[FONT=Courier New]</Limit>[/FONT]
[FONT=Courier New]</Directory>[/FONT]
 
[FONT=Courier New]<Directory "/share/HDZ_DATA">[/FONT]
[FONT=Courier New]<Limit ALL>[/FONT]
[FONT=Courier New]DenyAll[/FONT]
[FONT=Courier New]</Limit>[/FONT]
[FONT=Courier New]</Directory>[/FONT]
 
[FONT=Courier New]<Directory "/share/HDE_DATA">[/FONT]
[FONT=Courier New]<Limit ALL>[/FONT]
[FONT=Courier New]DenyAll[/FONT]
[FONT=Courier New]</Limit>[/FONT]
[FONT=Courier New]</Directory>[/FONT]
 
[FONT=Courier New]<Directory "/share/HDV_DATA">[/FONT]
[FONT=Courier New]<Limit ALL>[/FONT]
[FONT=Courier New]DenyAll[/FONT]
[FONT=Courier New]</Limit>[/FONT]
[FONT=Courier New]</Directory>[/FONT]
 
[FONT=Courier New]<Directory "/share/HDX_DATA">[/FONT]
[FONT=Courier New]<Limit ALL>[/FONT]
[FONT=Courier New]DenyAll[/FONT]
[FONT=Courier New]</Limit>[/FONT]
[FONT=Courier New]</Directory>[/FONT]
 
[FONT=Courier New]<Directory "/share/HDU_DATA">[/FONT]
[FONT=Courier New]<Limit ALL>[/FONT]
[FONT=Courier New]DenyAll[/FONT]
[FONT=Courier New]</Limit>[/FONT]
[FONT=Courier New]</Directory>[/FONT]
 
[FONT=Courier New]<Directory "/share/HDC_DATA">[/FONT]
[FONT=Courier New]<Limit ALL>[/FONT]
[FONT=Courier New]DenyAll[/FONT]
[FONT=Courier New]</Limit>[/FONT]
[FONT=Courier New]</Directory>[/FONT]
 
[FONT=Courier New]<Directory "/share/HDY_DATA">[/FONT]
[FONT=Courier New]<Limit ALL>[/FONT]
[FONT=Courier New]DenyAll[/FONT]
[FONT=Courier New]</Limit>[/FONT]
[FONT=Courier New]</Directory>[/FONT]
 
[FONT=Courier New]<Directory "/share/HDG_DATA">[/FONT]
[FONT=Courier New]<Limit ALL>[/FONT]
[FONT=Courier New]DenyAll[/FONT]
[FONT=Courier New]</Limit>[/FONT]
[FONT=Courier New]</Directory>[/FONT]
 
[FONT=Courier New]<Directory "/share/HDD_DATA">[/FONT]
[FONT=Courier New]<Limit ALL>[/FONT]
[FONT=Courier New]DenyAll[/FONT]
[FONT=Courier New]</Limit>[/FONT]
[FONT=Courier New]</Directory>[/FONT]
 
[FONT=Courier New]<Directory "/share/HDB_DATA">[/FONT]
[FONT=Courier New]<Limit ALL>[/FONT]
[FONT=Courier New]DenyAll[/FONT]
[FONT=Courier New]</Limit>[/FONT]
[FONT=Courier New]</Directory>[/FONT]
 
[FONT=Courier New]<Directory "/share/HDK_DATA">[/FONT]
[FONT=Courier New]<Limit ALL>[/FONT]
[FONT=Courier New]DenyAll[/FONT]
[FONT=Courier New]</Limit>[/FONT]
[FONT=Courier New]</Directory>[/FONT]
 
[FONT=Courier New]<Directory "/share/HDP_DATA">[/FONT]
[FONT=Courier New]<Limit ALL>[/FONT]
[FONT=Courier New]DenyAll[/FONT]
[FONT=Courier New]</Limit>[/FONT]
[FONT=Courier New]</Directory>[/FONT]
 
[FONT=Courier New]<Directory "/share/HDQ_DATA">[/FONT]
[FONT=Courier New]<Limit ALL>[/FONT]
[FONT=Courier New]DenyAll[/FONT]
[FONT=Courier New]</Limit>[/FONT]
[FONT=Courier New]</Directory>[/FONT]
 
[FONT=Courier New]<Directory "/share/HDL_DATA">[/FONT]
[FONT=Courier New]<Limit ALL>[/FONT]
[FONT=Courier New]DenyAll[/FONT]
[FONT=Courier New]</Limit>[/FONT]
[FONT=Courier New]</Directory>[/FONT]
 
[FONT=Courier New]<Directory "/share/HDR_DATA">[/FONT]
[FONT=Courier New]<Limit ALL>[/FONT]
[FONT=Courier New]DenyAll[/FONT]
[FONT=Courier New]</Limit>[/FONT]
[FONT=Courier New]</Directory>[/FONT]
 
[FONT=Courier New]<Directory "/share/HDS_DATA">[/FONT]
[FONT=Courier New]<Limit ALL>[/FONT]
[FONT=Courier New]DenyAll[/FONT]
[FONT=Courier New]</Limit>[/FONT]
[FONT=Courier New]</Directory>[/FONT]
 
[FONT=Courier New]<Directory "/share/external">[/FONT]
[FONT=Courier New]<Limit ALL>[/FONT]
[FONT=Courier New]DenyAll[/FONT]
[FONT=Courier New]</Limit>[/FONT]
[FONT=Courier New]</Directory>[/FONT]
 
[FONT=Courier New]<Directory "/share/HDA_DATA">[/FONT]
[FONT=Courier New]<Limit ALL>[/FONT]
[FONT=Courier New]DenyAll[/FONT]
[FONT=Courier New]</Limit>[/FONT]
[FONT=Courier New]</Directory>[/FONT]
 
[FONT=Courier New]<Directory "/share/HDT_DATA">[/FONT]
[FONT=Courier New]<Limit ALL>[/FONT]
[FONT=Courier New]DenyAll[/FONT]
[FONT=Courier New]</Limit>[/FONT]
[FONT=Courier New]</Directory>[/FONT]
 
[FONT=Courier New]<Directory "/share/HDM_DATA">[/FONT]
[FONT=Courier New]<Limit ALL>[/FONT]
[FONT=Courier New]DenyAll[/FONT]
[FONT=Courier New]</Limit>[/FONT]
[FONT=Courier New]</Directory>[/FONT]
 
[FONT=Courier New]<Directory "/share/HDW_DATA">[/FONT]
[FONT=Courier New]<Limit ALL>[/FONT]
[FONT=Courier New]DenyAll[/FONT]
[FONT=Courier New]</Limit>[/FONT]
[FONT=Courier New]</Directory>[/FONT]
 
[FONT=Courier New]<Directory "/share/HDI_DATA">[/FONT]
[FONT=Courier New]<Limit ALL>[/FONT]
[FONT=Courier New]DenyAll[/FONT]
[FONT=Courier New]</Limit>[/FONT]
[FONT=Courier New]</Directory>[/FONT]
 
[FONT=Courier New]<Directory "/share/HDF_DATA">[/FONT]
[FONT=Courier New]<Limit ALL>[/FONT]
[FONT=Courier New]DenyAll[/FONT]
[FONT=Courier New]</Limit>[/FONT]
[FONT=Courier New]</Directory>[/FONT]
 
[FONT=Courier New]<Directory "/share/HDN_DATA">[/FONT]
[FONT=Courier New]<Limit ALL>[/FONT]
[FONT=Courier New]DenyAll[/FONT]
[FONT=Courier New]</Limit>[/FONT]
[FONT=Courier New]</Directory>[/FONT]
 
[FONT=Courier New]<Directory "/share/HDJ_DATA">[/FONT]
[FONT=Courier New]<Limit ALL>[/FONT]
[FONT=Courier New]DenyAll[/FONT]
[FONT=Courier New]</Limit>[/FONT]
[FONT=Courier New]</Directory>[/FONT]
 
[FONT=Courier New]<Directory "/share/HDH_DATA">[/FONT]
[FONT=Courier New]<Limit ALL>[/FONT]
[FONT=Courier New]DenyAll[/FONT]
[FONT=Courier New]</Limit>[/FONT]
[FONT=Courier New]</Directory>[/FONT]
 
[FONT=Courier New]<Directory "/share/MD0_DATA">[/FONT]
[FONT=Courier New]<Limit ALL>[/FONT]
[FONT=Courier New]DenyAll[/FONT]
[FONT=Courier New]</Limit>[/FONT]
[FONT=Courier New]</Directory>[/FONT]
 
[FONT=Courier New]<Directory "/share/Qmultimedia">[/FONT]
[FONT=Courier New]<Limit READ DIRS>[/FONT]
[FONT=Courier New]Order Deny, Allow[/FONT]
[FONT=Courier New]AllowGroup "everyone"[/FONT]
[FONT=Courier New]AllowUser "admin"[/FONT]
[FONT=Courier New]DenyUser "guest"[/FONT]
[FONT=Courier New]</Limit>[/FONT]
[FONT=Courier New]<Limit ALL>[/FONT]
[FONT=Courier New]Order Deny, Allow[/FONT]
[FONT=Courier New]AllowUser "a[global][/FONT]
[FONT=Courier New]socket options = TCP_NODELAY SO_KEEPALIVE SO_SNDBUF=65536 SO_RCVBUF=65536[/FONT]
[FONT=Courier New][global][/FONT]
[FONT=Courier New]null passwords = yes[/FONT]
[FONT=Courier New]use sendfile = yes[/FONT]
[FONT=Courier New]oplocks = yes[/FONT]
[FONT=Courier New]case sensitive = auto[/FONT]
[FONT=Courier New]deadtime = 10[/FONT]
[FONT=Courier New]username level = 0[/FONT]
[FONT=Courier New]display charset = UTF8[/FONT]
[FONT=Courier New]unix extensions = no[/FONT]
[FONT=Courier New]veto files = /.AppleDB/.AppleDouble/.AppleDesktop/:2eDS_Store/Network Trash Folder/Temporary Items/TheVolumeSettingsFolder/.@__thumb/.@__desc/[/FONT]
[FONT=Courier New]socket options = TCP_NODELAY SO_KEEPALIVE SO_SNDBUF=65536 SO_RCVBUF=65536[/FONT]
[FONT=Courier New]wins support = no[/FONT]
[FONT=Courier New]workgroup = BELKIN[/FONT]
[FONT=Courier New]security = USER[/FONT]
[FONT=Courier New]server string = NAS Server[/FONT]
[FONT=Courier New][Qmultimedia][/FONT]
[FONT=Courier New]comment = System default share[/FONT]
[FONT=Courier New]path = /share/MD0_DATA/Qmultimedia[/FONT]
[FONT=Courier New]browsable = yes[/FONT]
[FONT=Courier New]oplocks = yes[/FONT]
[FONT=Courier New]ftp write only = no[/FONT]
[FONT=Courier New]public = yes[/FONT]
[FONT=Courier New]invalid users = guest[/FONT]
[FONT=Courier New]read list = @"everyone"[/FONT]
[FONT=Courier New]write list = admin[/FONT]
[FONT=Courier New]valid users = root,@"everyone",admin[/FONT]
[FONT=Courier New]inherit permissions = yes[/FONT]
[FONT=Courier New][Qdownload][/FONT]
[FONT=Courier New]comment = System default share[/FONT]
[FONT=Courier New]path = /share/MD0_DATA/Qdownload[/FONT]
[FONT=Courier New]browsable = yes[/FONT]
[FONT=Courier New]oplocks = yes[/FONT]
[FONT=Courier New]ftp write only = no[/FONT]
[FONT=Courier New]public = yes[/FONT]
[FONT=Courier New]invalid users = guest[/FONT]
[FONT=Courier New]read list = @"everyone"[/FONT]
[FONT=Courier New]write list = admin[/FONT]
[FONT=Courier New]valid users = root,@"everyone",admin[/FONT]
[FONT=Courier New]inherit permissions = yes[/FONT]
[FONT=Courier New][Qrecordings][/FONT]
[FONT=Courier New]comment = System default share[/FONT]
[FONT=Courier New]path = /share/MD0_DATA/Qrecordings[/FONT]
[FONT=Courier New]browsable = yes[/FONT]
[FONT=Courier New]oplocks = yes[/FONT]
[FONT=Courier New]ftp write only = no[/FONT]
[FONT=Courier New]public = yes[/FONT]
[FONT=Courier New]invalid users = guest[/FONT]
[FONT=Courier New]read list = @"everyone"[/FONT]
[FONT=Courier New]write list = admin[/FONT]
[FONT=Courier New]valid users = root,@"everyone",admin[/FONT]
[FONT=Courier New]inherit permissions = yes[/FONT]
[FONT=Courier New][Qweb][/FONT]
[FONT=Courier New]comment = System default share[/FONT]
[FONT=Courier New]path = /share/MD0_DATA/Qweb[/FONT]
[FONT=Courier New]browsable = yes[/FONT]
[FONT=Courier New]oplocks = yes[/FONT]
[FONT=Courier New]ftp write only = no[/FONT]
[FONT=Courier New]public = yes[/FONT]
[FONT=Courier New]invalid users = guest[/FONT]
[FONT=Courier New]read list = @"everyone"[/FONT]
[FONT=Courier New]write list = admin[/FONT]
[FONT=Courier New]valid users = root,@"everyone",admin[/FONT]
[FONT=Courier New]inherit permissions = yes[/FONT]
[FONT=Courier New][Qusb][/FONT]
[FONT=Courier New]comment = System default share[/FONT]
[FONT=Courier New]path = /share/MD0_DATA/Qusb[/FONT]
[FONT=Courier New]browsable = yes[/FONT]
[FONT=Courier New]oplocks = yes[/FONT]
[FONT=Courier New]ftp write only = no[/FONT]
[FONT=Courier New]public = yes[/FONT]
[FONT=Courier New]invalid users = guest[/FONT]
[FONT=Courier New]read list = @"everyone"[/FONT]
[FONT=Courier New]write list = admin[/FONT]
[FONT=Courier New]valid users = root,@"everyone",admin[/FONT]
[FONT=Courier New]inherit permissions = yes[/FONT]
[FONT=Courier New][Public][/FONT]
[FONT=Courier New]comment = System default share[/FONT]
[FONT=Courier New]path = /share/MD0_DATA/Public[/FONT]
[FONT=Courier New]browsable = yes[/FONT]
[FONT=Courier New]oplocks = yes[/FONT]
[FONT=Courier New]ftp write only = no[/FONT]
[FONT=Courier New]public = yes[/FONT]
[FONT=Courier New]invalid users = [/FONT]
[FONT=Courier New]read list = [/FONT]
[FONT=Courier New]write list = admin,@"everyone",guest[/FONT]
[FONT=Courier New]valid users = root,admin,@"everyone",guest[/FONT]
[FONT=Courier New]inherit permissions = yes[/FONT]
[FONT=Courier New][Network Recycle Bin 1][/FONT]
[FONT=Courier New]comment = [RAID5 Disk Volume: Drive 1 2 3 4 5 6][/FONT]
[FONT=Courier New]path = /share/MD0_DATA/Network Recycle Bin[/FONT]
[FONT=Courier New]browsable = yes[/FONT]
[FONT=Courier New]oplocks = yes[/FONT]
[FONT=Courier New]ftp write only = no[/FONT]
[FONT=Courier New]public = yes[/FONT]
[FONT=Courier New]invalid users = guest[/FONT]
[FONT=Courier New]read list = @"everyone"[/FONT]
[FONT=Courier New]write list = admin[/FONT]
[FONT=Courier New]valid users = root,@"everyone",admin[/FONT]
[FONT=Courier New]inherit permissions = yes[/FONT]
[FONT=Courier New][x264][/FONT]
[FONT=Courier New]comment = [/FONT]
[FONT=Courier New]path = /share/MD0_DATA/X264[/FONT]
[FONT=Courier New]browsable = yes[/FONT]
[FONT=Courier New]oplocks = yes[/FONT]
[FONT=Courier New]ftp write only = no[/FONT]
[FONT=Courier New]public = yes[/FONT]
[FONT=Courier New]invalid users = [/FONT]
[FONT=Courier New]read list = [/FONT]
[FONT=Courier New]write list = admin,@"everyone",guest[/FONT]
[FONT=Courier New]valid users = root,admin,@"everyone",guest[/FONT]
[FONT=Courier New]inherit permissions = yes[/FONT]
[FONT=Courier New][Movies][/FONT]
[FONT=Courier New]comment = user made share[/FONT]
[FONT=Courier New]path = /share/MD0_DATA/Movies[/FONT]
[FONT=Courier New]browsable = yes[/FONT]
[FONT=Courier New]oplocks = no[/FONT]
[FONT=Courier New]ftp write only = no[/FONT]
[FONT=Courier New]public = yes[/FONT]
[FONT=Courier New]invalid users = [/FONT]
[FONT=Courier New]read list = [/FONT]
[FONT=Courier New]write list = admin,@"everyone",guest[/FONT]
[FONT=Courier New]valid users = root,admin,@"everyone",guest[/FONT]
[FONT=Courier New]inherit permissions = yes[/FONT]
[FONT=Courier New][muggi][/FONT]
[FONT=Courier New]comment = [/FONT]
[FONT=Courier New]path = /share/MD0_DATA/muggi[/FONT]
[FONT=Courier New]browsable = yes[/FONT]
[FONT=Courier New]oplocks = yes[/FONT]
[FONT=Courier New]ftp write only = no[/FONT]
[FONT=Courier New]public = yes[/FONT]
[FONT=Courier New]invalid users = [/FONT]
[FONT=Courier New]read list = [/FONT]
[FONT=Courier New]write list = muggi[/FONT]
[FONT=Courier New]valid users = root,muggi[/FONT]
[FONT=Courier New]inherit permissions = yes[/FONT][/FONT]

---

### Post by muggisan on 2009-11-15
hi, seems like my problem is solved, the smb.conf file was totally messed up, and i was able to replace it with an earlier versin of smb.conf.
 
There is amongst problems with the GLOBAL part in the old file
 
 
```

[global]
workgroup = NAS 
security=user
server string=NAS Server
encrypt passwords = Yes
username level = 0
map to guest = Bad User
null passwords = yes
max log size = 10
name resolve order = bcast wins
socket options = TCP_NODELAY SO_KEEPALIVE SO_SNDBUF=65536 SO_RCVBUF=65536
os level = 32
preferred master = Yes
dns proxy = No
config file = /etc/config/smb.conf
smb passwd file=/etc/config/smbpasswd 
username map = /etc/config/smbusers
guest account = guest
directory mask = 0777
create mask = 0777
oplocks = yes
locking = yes
disable spoolss = yes
load printers = no
dos charset = UTF8
display charset = UTF8
force directory security mode = 0000
template shell = /bin/sh
veto files = /.AppleDB/.AppleDouble/.AppleDesktop/:2eDS_Store/Network Trash Folder/Temporary Items/TheVolumeSettingsFolder/.@__thumb/.@__desc/
delete veto files = yes
map archive = yes
map system = yes
map hidden = yes
map read only = yes
deadtime = 10
use sendfile = yes
case sensitive = auto
unix extensions = no
[Qmultimedia]
comment = System default share
path = /share/MD0_DATA/Qmultimedia
browsable = yes
oplocks = yes
ftp write only = no
public = yes
invalid users = guest
read list = @"everyone",muggi
write list = admin
valid users = root,@"everyone",admin,muggi
inherit permissions = yes
[Qdownload]
comment = System default share
path = /share/MD0_DATA/Qdownload
browsable = yes
oplocks = yes
ftp write only = no
public = yes
invalid users = guest
read list = @"everyone",muggi
write list = admin
valid users = root,@"everyone",admin,muggi
inherit permissions = yes
[Qrecordings]
comment = System default share
path = /share/MD0_DATA/Qrecordings
browsable = yes
oplocks = yes
ftp write only = no
public = yes
invalid users = guest
read list = @"everyone",muggi
write list = admin
valid users = root,@"everyone",admin,muggi
inherit permissions = yes
[Qweb]
comment = System default share
path = /share/MD0_DATA/Qweb
browsable = yes
oplocks = yes
ftp write only = no
public = yes
invalid users = guest
read list = @"everyone",muggi
write list = admin
valid users = root,@"everyone",admin,muggi
inherit permissions = yes
[Qusb]
comment = System default share
path = /share/MD0_DATA/Qusb
browsable = yes
oplocks = yes
ftp write only = no
public = yes
invalid users = guest
read list = @"everyone",muggi
write list = admin
valid users = root,@"everyone",admin,muggi
inherit permissions = yes
[Public]
comment = System default share
path = /share/MD0_DATA/Public
browsable = yes
oplocks = yes
ftp write only = no
public = yes
invalid users = 
read list = muggi
write list = admin,@"everyone",guest
valid users = root,admin,@"everyone",guest,muggi
inherit permissions = yes
[Network Recycle Bin 1]
comment = [RAID5 Disk Volume: Drive 1 2 3 4 5 6]
path = /share/MD0_DATA/Network Recycle Bin
browsable = yes
oplocks = yes
ftp write only = no
public = yes
invalid users = guest
read list = @"everyone"
write list = admin
valid users = root,@"everyone",admin
inherit permissions = yes
[X264]
comment = 
path = /share/MD0_DATA/X264
browsable = yes
oplocks = yes
ftp write only = no
public = yes
invalid users = 
read list = muggi
write list = admin
valid users = root,muggi,admin
inherit permissions = yes
[eSATADisk1]
comment = eSATA storage share
path = /share/external/sdy1
browsable = yes
oplocks = yes
ftp write only = no
public = yes
invalid users = guest
read list = @"everyone",muggi
write list = admin
valid users = root,admin,@"everyone",muggi
inherit permissions = yes
map hidden = no

```

---

