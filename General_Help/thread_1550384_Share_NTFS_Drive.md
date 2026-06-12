---
title: "Share NTFS Drive"
date: 2010-08-11
forum: General Help
---

### Post by n8nt on 2010-08-11
I have a strange situaion. I installed my ubuntu 10.04 on my old windows 7 box. That box had a 160gb hard drive (which I replaced and put ubuntu on) and a 1 terabyte drive with a bunch of data on it which was a share drive for 5 other computers in my house.
 
I would like to continue to use that drive as a shared drive between the other computers (all are windows). 
 
I have been able to mount the two ntfs drives on the ubuntu and I can view the folders and files from the ubuntu.
 
I have not been able to figure out what I need to install in my windows 7 boxes that will let me use that ntfs drive on the network. Maybe that isn't possible but if so I'd like to try something before I give up. Anyone have any ideas?
 
All of the places I've searched on this forum seem to indicate how to setup the samba on the ubuntu to access an ntfs file system somewhere, but I haven't been successful in finding anything that talks about accessing the ntfs drives that I have mounted on the Ubuntu system from another Windows 7 box on the same network. If I can't figure this out soon I'll have to give up and remove the 1-terabyte drive from my ubuntu box and place it into one of the Windows boxes.
 
Here's hoping....[IMG]http://ubuntuforums.org/images/icons/icon5.gif[/IMG]
 
Bob

---

### Post by cj.surrusco on 2010-08-11
You should be able to find the Samba shares very easily by looking in the Network Places in Windows, assuming that you set them up correctly on the Ubuntu end.

As a second option, you could use FTP with [vsftpd]("http://vsftpd.beasts.org/") or proftp, but I recommend vsftpd.

---

### Post by n8nt on 2010-08-11
I'm only assuming I set them up correctly on the Ubuntu end. I am able to see the NTFS drive fine from the Ubuntu computer.
 
Unfortunately at the moment I am away from home and my internet apparently died at home as I cannot remotely connect to anything there so I cannot get a copy of my smb.conf file.
 
Perhaps you can give an example of what the section should look like for an ntfs entry.
 
Thanks,

---

### Post by Morbius1 on 2010-08-11
Accessing an NTFS partition remotely is no different from any other formatted partition. CIFS doesn't care and doesn't know what the format of the target folder is. What is important is that Samba authentication is in sync with Linux file permissions on the Ubuntu server.

So the first question is: How are you mounting the NTFS partition?
DO you mount it through places or do you have an entry in fstab?

The second question is what method of samba are you using? There are 2:
Nautilus-share ( Nautilus > Right click > Sharing Options) 
Or Classic-share.

Posting the output of these commands will tell us what's up:
```
net usershare info
testparm -s
cat /etc/fstab
mount
```

---

### Post by n8nt on 2010-08-12
I have a lot to learn!
 
On the question of type of samba being used, which is better? I don't know which one I am using but perhaps my answers to your questions will help..
 
In answer to your questions I executed the commands and got the results:
 
(One thing I see is that maybe I need to create a folder for the usershares. - I will try that.) 
 
[EMAIL="bob@sts-ubuntu2:~$"]bob@sts-ubuntu2:~$[/EMAIL] sudo** *net usershare info***
[sudo] password for bob: 
net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


[EMAIL="bob@sts-ubuntu2:~$"]bob@sts-ubuntu2:~$[/EMAIL] sudo[B][I] testparm -s
[/I][/B]Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
params.c:Parameter() - Ignoring badly formed line in configuration file: hosts allow 192.168.1
Processing section "[homes]"
Processing section "[printers]"
Processing section "[print$]"
Processing section "[share1]"
Processing section "[share2]"
Loaded services file OK.
ERROR: lock directory /var/run/samba does not exist
ERROR: pid directory /var/run/samba does not exist
Server role: ROLE_STANDALONE
[global]
 workgroup = STARLIGHT
 server string = %h server (Samba, Ubuntu)
 interfaces = lo, etho0
 bind interfaces only = Yes
 security = SHARE
 map to guest = Bad User
 obey pam restrictions = Yes
 pam password change = Yes
 passwd program = /usr/bin/passwd %u
 passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
 unix password sync = Yes
 syslog = 0
 log file = /var/log/samba/log.%m
 max log size = 1000
 local master = No
 domain master = No
 dns proxy = No
 usershare allow guests = Yes
 panic action = /usr/share/samba/panic-action %d
[homes]
[printers]
 comment = All Printers
 path = /var/spool/samba
 create mask = 0700
 printable = Yes
 browseable = No
 browsable = No
[print$]
 comment = Printer Drivers
 path = /var/lib/samba/printers
[share1]
 path = /media/sdb1
 read only = No
 guest ok = Yes
[share2]
 path = media/sdb2
 read only = No
 guest ok = Yes
 

[EMAIL="bob@sts-ubuntu2:~$"]bob@sts-ubuntu2:~$[/EMAIL] sudo [B][I]mount
[/I][/B]/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sdb1 on /media/sdb1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb2 on /media/sdb2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/bob/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=bob)
[EMAIL="bob@sts-ubuntu2:~$"]bob@sts-ubuntu2:~$[/EMAIL] 
 
 
[EMAIL="bob@sts-ubuntu2:~$"]bob@sts-ubuntu2:~$[/EMAIL] ***cat /etc/fstab***
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=f1a5f30d-cc5b-4a54-9b5c-30095d94f359 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f802ac82-0446-4de6-b1fe-1f0fdc89e741 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb1 /media/sdb1 ntfs defaults,nls=uf8,umask=007,gid=46 0 1
/dev/sdb2 /media/sdb2 ntfs defaults,nls=uf8,umask=007,gid=46 0 1
[EMAIL="bob@sts-ubuntu2:~$"]bob@sts-ubuntu2:~$[/EMAIL]

---

### Post by Morbius1 on 2010-08-12
(1) You're using Classic-shares because your share definitions are in smb.conf. You don't need to use Nautilus-shares since you're already using the other method. It's best to use only one method at a time.

(2) You have an unnecessarily complicated smb.conf file considering you're only creating two guest shares. You do have one error:
>   interfaces = lo, etho0I think that should read:
>   interfaces = lo, [COLOR=Blue]eth0[/COLOR][COLOR=Blue]EDIT: You have another error:[/COLOR]
> params.c:razz:arameter() - Ignoring badly formed line in configuration file: hosts allow 192.168.1Chack the syntax of the line in smb.conf. It should read something like this:
> hosts allow = 192.168.1.Dont forget the trailing period after the "1"

(3) You do have a fundamental problem with your mount's however and goes back to the Samba authorization / linux file permissions thing I talked about above. You created these shares:
> [share1]
 path = /media/sdb1
 read only = No
 [COLOR=Blue]guest ok = Yes[/COLOR]
[share2]
 path = media/sdb2
 read only = No
 [COLOR=Blue]guest ok = Yes[/COLOR]Both of these shares allow write access to remote guests. But you mounted the partitions this way:
> /dev/sdb1 /media/sdb1 ntfs defaults,nls=uf8,[COLOR=Blue]umask=007[/COLOR],gid=46 0 1
/dev/sdb2 /media/sdb2 ntfs defaults,nls=uf8,[COLOR=Blue]umask=007[/COLOR],gid=46 0 1The umask=007 will allow read / write access to root and members of the gid=46 group ( which includes all local login users ) but no access at all ( the "7" part ) to anyone else. The Samba "guest" is "everyone else". You need to modify your fstab entries and change umask to 000 so that the two lines look like this:
> /dev/sdb1 /media/sdb1 ntfs defaults,nls=uf8,[COLOR=Blue]umask=000[/COLOR],gid=46 0 1
/dev/sdb2 /media/sdb2 ntfs defaults,nls=uf8,[COLOR=Blue]umask=000[/COLOR],gid=46 0 1(4) testparm is throwing you other errors:
> ERROR: lock directory /var/run/samba does not exist
ERROR: pid directory /var/run/samba does not existYou also are using "security = share" instead of the default "security = user" but considering these are only guest shares I suppose that's OK. 

We may need the full printout of the smb.conf file to see what's going on :
```
cat /etc/samba/smb.conf
```But before you do that make the changes I suggested and restart samba:
```
sudo service smbd restart
```See how far you can get with these few changes.

---

### Post by n8nt on 2010-08-12
Thanks.
I tried the changes but when I tried to restart samba it said there was no "smbd" so maybe I never installed it. I thought I did. So I figured I'd just restart the machine.
 
The bad thing now is that I'm not at home and so I tried to restart the ubuntu but for some reason it is not letting me remote in now. I have it set to boot up and auto log on my original account. It has been working so I'm assuming I messed something up so that it is not starting. I'll have to wait until tonight.
 
If I want to allow specific users instead of just guest (I'd prefer to have specific users) I assume I could create a user on ubuntu and create the same user on my windows boxes with the same user name and password. Would that be correct? My main user is me on the windows and my logon name there is "Bob T" - with a space - and ubuntu did not seem to like having a space in the user name. Is that correct? If so that means I'd have to create a new user like "bobt" - that right?
 
Thanks. I'll get back to this when I get back to home tonight.

---

### Post by Morbius1 on 2010-08-12
>  it said there was no "smbd" so maybe I never installed it.If the error message was:
> restart: Unknown instance:Then samba wasn't started to begin with. You need to start it with:
```
sudo service smbd start
```If the error messaage was:
> smbd: unrecognized serviceThen you are either not running 10.04 but an earlier version in which case the command is:
```
sudo service samba restart
```OR something is really hosed up with your system.

> I assume I could create a user on ubuntu and create the same user on my  windows boxes with the same user name and password. Would that be  correct? My main user is me on the windows and my logon name there is  "Bob T" - with a space - and ubuntu did not seem to like having a space  in the user name. Is that correct? If so that means I'd have to create a  new user like "bobt" - that right?The login names and passwords on the Windows box don't have to match the samba names on the linux box despite what every HowTo tells you. It may be more convenient but it's not a requirement. That would be a violation of privacy / security if the server user in a peer-to-peer network knew the actual local login name and password of every client. 

Let's take the "Bob T" example. Leave the Windows user name alone and create a Linux user named "bobt", then create an smbpasswd for "bobt". When "Bob T" tries to access an authenticated share and is asked for credentials he would enter bobt with the smbpasswd.

---

### Post by n8nt on 2010-08-12
My system started back up.
I used the system monitor to verify that I am running 10.04.
I did not see any samba service running in the process list.
I then checked for uninstalled and installed packages in the Synaptic Package manager; there were two in the uninstalled, but there a version numbers of 4.0 (there is a samba4) and there is one just labled samba and it shows a latest version of 2:3.4.7. There are also a number of packages starting with samba4 and say that latest version is 4.0.0~alpha8+git20090912-1. Should I install samba or samba4?
 
I also see in the installed list of smbclient, samba-common, samba-common-bin and others. 
 
So it seems like some parts of samba are installed but I don't see a way to start them.
 
I'll keep looking...
 
I typed "smbd" on the terminal and it said samba was not installed and that I should type "sudo apt-get install samba" so I did that and it comes back saying it can't get a lock.
Here's what I typed and what it said... I then looked for the lock file and found it...
 
[EMAIL="bob@sts-ubuntu2:~$"]bob@sts-ubuntu2:~$[/EMAIL] smbd
The program 'smbd' is currently not installed.  You can install it by typing:
sudo apt-get install samba
[EMAIL="bob@sts-ubuntu2:~$"]bob@sts-ubuntu2:~$[/EMAIL] sudo apt-get install samba
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
[EMAIL="bob@sts-ubuntu2:~$"]bob@sts-ubuntu2:~$[/EMAIL] cd /var/lib
[EMAIL="bob@sts-ubuntu2:/var/lib$"]bob@sts-ubuntu2:/var/lib$[/EMAIL] ls dpkg
alternatives   cmethopt        info   statoverride      status-old
available      diversions      lock   statoverride-old  triggers
available-old  diversions-old  parts  status            updates
[EMAIL="bob@sts-ubuntu2:/var/lib$"]bob@sts-ubuntu2:/var/lib$[/EMAIL] cd dpkg
[EMAIL="bob@sts-ubuntu2:/var/lib/dpkg$"]bob@sts-ubuntu2:/var/lib/dpkg$[/EMAIL] ks
ks: command not found
[EMAIL="bob@sts-ubuntu2:/var/lib/dpkg$"]bob@sts-ubuntu2:/var/lib/dpkg$[/EMAIL] ls
alternatives   cmethopt        info   statoverride      status-old
available      diversions      lock   statoverride-old  triggers
available-old  diversions-old  parts  status            updates
[EMAIL="bob@sts-ubuntu2:/var/lib/dpkg$"]bob@sts-ubuntu2:/var/lib/dpkg$[/EMAIL] cd lock
bash: cd: lock: Not a directory
[EMAIL="bob@sts-ubuntu2:/var/lib/dpkg$"]bob@sts-ubuntu2:/var/lib/dpkg$[/EMAIL] ls lock
lock
[EMAIL="bob@sts-ubuntu2:/var/lib/dpkg$"]bob@sts-ubuntu2:/var/lib/dpkg$[/EMAIL] sudo apt-get install samba
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
[EMAIL="bob@sts-ubuntu2:/var/lib/dpkg$"]bob@sts-ubuntu2:/var/lib/dpkg$[/EMAIL]

---

### Post by Morbius1 on 2010-08-12
I've never seen that error message before:
>  E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable) 
so anything I would recommend would be a guess. I would use google to do a search on that exact message in quotes to find an answer.

---

### Post by n8nt on 2010-08-12
Well turns out I did have a package manager running - although I didn't know that at first because when I ran SystemMonitor it was only showing my processes. It is difficult for me to run some of these commands from the GUI because I can't figure out how to run them as root - so when I finally figured out I could do "sudo gnome-system-monitor" I was able to see all of the running processes. 
 
However, I didn't figure this out until I just did a "sudo rm /var/lib/dpkg/lock" and then I was able to install.
 
Now I get different errors when I try to map a drive from windows. I looked in the log file and found a log.192.168.1.54 which is the ip of my windows box. IN there I found the following:
 
[2010/08/12 13:22:24,  0] param/loadparm.c:8768(load_usershare_service)
  load_usershare_service: stat of /var/lib/samba/usershares failed. No such file
 or directory
[2010/08/12 13:22:24,  0] param/loadparm.c:8768(load_usershare_service)
  load_usershare_service: stat of /var/lib/samba/usershares failed. No such file
 or directory
[2010/08/12 13:22:24,  0] smbd/service.c:1202(make_connection)
  192.168.1.54 (192.168.1.54) couldn't find service media
[2010/08/12 13:22:38,  0] lib/util_sock.c:539(read_fd_with_timeout)
[2010/08/12 13:22:38,  0] lib/util_sock.c:1491(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  read_fd_with_timeout: client 0.0.0.0 read error = Connection reset by peer.
[EMAIL="bob@sts-ubuntu2:/var/log/samba$"]bob@sts-ubuntu2:/var/log/samba$[/EMAIL] 

I'll keep going...

---

### Post by Morbius1 on 2010-08-12
From the "Command Prompt" of Windows run the following command and post the output:
```
net view //Ubuntu_server_name/share1
```[COLOR=Blue]Sorry, wrong syntax:[/COLOR]
```
 net view \\Ubuntu_server_name\share1
```

---

### Post by n8nt on 2010-08-13
Still not having any luck. I did as you last asked with the net view command, but I think that command works differently. Below is the result.
 
I also re-installed and shortened my smb.conf file as you mentioned earlier that it was kind of long.  Still looks like some kind of permission problem and also looks like maybe I need to do something about the connection. See my logs at the bottom of this.
 
Thanks so much for your help. I hope it will not be in vain, but it has been a long day and No success. I just came in from looking for shooting stars from the persioed meteor shower - but had no luck with that either! It has been a tough day..
 
 
In answer to your last suggestion:
[EMAIL="bob@sts-ubuntu2:~$"]bob@sts-ubuntu2:~$[/EMAIL][B][I] sudo net view //STS-UBUNTU2/share1
[/I][/B][sudo] password for bob: 
Invalid command: net view
Usage:
net rpc             Run functions using RPC transport
net rap             Run functions using RAP transport
net ads             Run functions using ADS transport
net file            Functions on remote opened files
net share           Functions on shares
net session         Manage sessions
net server          List servers in workgroup
net domain          List domains/workgroups on network
net printq          Modify printer queue
net user            Manage users
net group           Manage groups
net groupmap        Manage group mappings
net sam             Functions on the SAM database
net validate        Validate username and password
net groupmember     Modify group memberships
net admin           Execute remote command on a remote OS/2 server
net service         List/modify running services
net password        Change user password on target server
net changetrustpw   Change the trust password
net changesecretpw  Change the secret password
net time            Show/set time
net lookup          Look up host names/IP addresses
net join            Join a domain/AD
net dom             Join/unjoin (remote) machines to/from a domain/AD
net cache           Operate on the cache tdb file
net getlocalsid     Get the SID for the local domain
net setlocalsid     Set the SID for the local domain
net setdomainsid    Set domain SID on member servers
net getdomainsid    Get domain SID on member servers
net maxrid          Display the maximul RID currently used
net idmap           IDmap functions
net status          Display server status
net usershare       Manage user-modifiable shares
net usersidlist     Display list of all users with SID
net conf            Manage Samba registry based configuration
net registry        Manage the Samba registry
net eventlog        Process Win32 *.evt eventlog files
net help            Print usage information
[EMAIL="bob@sts-ubuntu2:~$"]bob@sts-ubuntu2:~$[/EMAIL] 

**I changed my smb.conf to look like this**:
 
 
#======================= Global Settings 
[global]
## Browsing/Identification ###
# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = STARLIGHT
# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)
# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

#### Networking ####
interfaces = lo, eth0
bind interfaces only = yes
hosts allow = 192.168.1.
#### Debugging/Accounting ####
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d

####### Authentication #######
# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
#   security = user
# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true
# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam
   obey pam restrictions = yes
# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
   unix password sync = yes
# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<[EMAIL="kahan@informatik.tu-muenchen.de"]kahan@informatik.tu-muenchen.de[/EMAIL]> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
   pam password change = yes
# This option controls how unsuccessful authentication attempts are mapped 
# to anonymous connections
   map to guest = bad user
########## Domains ###########

########## Printing ##########

############ Misc ############

# Setup usershare options to enable non-root users to share folders
# with the net usershare command.
# Maximum number of usershare. 0 (default) means that usershare is disabled.
   usershare max shares = 100
# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
   usershare allow guests = yes
#======================= Share Definitions 
[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700
# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
#
# My Shares
#
[share1]
path = /media/sdb1
read only = No
guest ok = Yes
[share2]
path = /media/sdb2
read only = No
guest ok = Yes

************************** My Logs ***********
 
[EMAIL="bob@sts-ubuntu2:/var/log/samba$"]bob@sts-ubuntu2:/var/log/samba$[/EMAIL] [B]more log.192.168.1.54
[/B][2010/08/13 01:13:47,  0] param/loadparm.c:8569(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/media failed. Permis
sion denied
[2010/08/13 01:13:47,  0] param/loadparm.c:8569(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/media failed. No suc
h file or directory
[2010/08/13 01:13:47,  0] smbd/service.c:1202(make_connection)
  192.168.1.54 (192.168.1.54) couldn't find service media
[2010/08/13 01:13:59,  0] lib/util_sock.c:539(read_fd_with_timeout)
[2010/08/13 01:13:59,  0] lib/util_sock.c:1491(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  read_fd_with_timeout: client 0.0.0.0 read error = Connection reset by peer.
[EMAIL="bob@sts-ubuntu2:/var/log/samba$"]bob@sts-ubuntu2:/var/log/samba$[/EMAIL] 
 
[EMAIL="bob@sts-ubuntu2:~$"]bob@sts-ubuntu2:~$[/EMAIL] [B]more /var/log/samba/log.smbd
[/B][2010/08/13 01:13:38,  0] smbd/server.c:1069(main)
  smbd version 3.4.7 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2010/08/13 01:13:38,  0] smbd/server.c:1115(main)
  standard input is not a socket, assuming -D option
[EMAIL="bob@sts-ubuntu2:~$"]bob@sts-ubuntu2:~$[/EMAIL]

---

### Post by Morbius1 on 2010-08-13
> In answer to your last suggestion:
bob@sts-ubuntu2:~$[B][I] sudo net view //STS-UBUNTU2/share1
[/I][/B][sudo] password for bob: 
Invalid command: net viewThat's because you ran it from Linux. I want you to run it from Windows:
> From the [COLOR=Blue]"Command Prompt" of Windows[/COLOR] run the following command and post the output:
```
net view \\Ubuntu_server_name\share1
```

> process_usershare_file: stat of /var/lib/samba/usershares/media failed. Permis
sion denied
[2010/08/13 01:13:47,  0] param/loadparm.c:8569(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/media failed. No suc
h file or directory
Please post the output of the following commands from the Linux box:
```
net usershare info
```
```
sudo net usershare info
```

---

### Post by n8nt on 2010-08-13
Here is the output of the Linux box commands: (there wasn't any...)
 
[EMAIL="bob@sts-ubuntu2:~$"]bob@sts-ubuntu2:~$[/EMAIL] sudo net usershare info
[EMAIL="bob@sts-ubuntu2:~$"]bob@sts-ubuntu2:~$[/EMAIL] net usershare info
[EMAIL="bob@sts-ubuntu2:~$"]bob@sts-ubuntu2:~$[/EMAIL] 

 
Here is the output from the windows box: (I also did a ping on the name)
 
Microsoft Windows [Version 6.1.7600]
Copyright (c) 2009 Microsoft Corporation.  All rights reserved.
C:\Users\Bob Tournoux>net view [\\STS-UBUNTU2\share1]("file://\\STS-UBUNTU2\share1")
System error 53 has occurred.
The network path was not found.

C:\Users\Bob Tournoux>\\192.168.1.52\share1
The specified server cannot perform the requested operation.
C:\Users\Bob Tournoux>ping STS-UBUNTU2
Pinging STS-UBUNTU2 [192.168.1.52] with 32 bytes of data:
Reply from 192.168.1.52: bytes=32 time<1ms TTL=64
Reply from 192.168.1.52: bytes=32 time<1ms TTL=64
Reply from 192.168.1.52: bytes=32 time<1ms TTL=64
Reply from 192.168.1.52: bytes=32 time<1ms TTL=64
Ping statistics for 192.168.1.52:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 0ms, Average = 0ms
C:\Users\Bob Tournoux>
 
Here is one more net command that I ran that may give some info:
 
[EMAIL="bob@sts-ubuntu2:~$"]bob@sts-ubuntu2:~$[/EMAIL] **sudo net service**
Enter root's password:
Could not connect to server 127.0.0.1
Connection failed: NT_STATUS_ACCESS_DENIED
[EMAIL="bob@sts-ubuntu2:~$"]bob@sts-ubuntu2:~$[/EMAIL]

---

### Post by n8nt on 2010-08-13
WHOA! 
I got it - i think...
I tried this command:
C:\Users\Bob Tournoux>net view [\\STS-UBUNTU2]("file://\\STS-UBUNTU2")
Shared resources at [\\STS-UBUNTU2]("file://\\STS-UBUNTU2")
sts-ubuntu2
Share name  Type  Used as  Comment
-------------------------------------------------------------------------------
share1      Disk
share2      Disk
The command completed successfully.

C:\Users\Bob Tournoux>
 
Then I tried mapping to [\\STS-UBUNTU2\share1]("file://\\STS-UBUNTU2\share1") and it worked.
 
I did make a minor change to the smb.conf file although I don't think it probably made any difference, but here is my final smb.conf file:
 
 
#======================= Global Settings =======================
[global]
## Browsing/Identification ###
# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = STARLIGHT
netbios name = STS_UBUNTU2
# server string is the equivalent of the NT Description field
;  server string = %h server (Samba, Ubuntu)
server string = %h
# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

#### Networking ####
interfaces = lo, eth0
bind interfaces only = yes
hosts allow = 192.168.1.
#### Debugging/Accounting ####
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d

####### Authentication #######
# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
#   security = user
;security = user
# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true
# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam
   obey pam restrictions = yes
# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
   unix password sync = yes
# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<[EMAIL="kahan@informatik.tu-muenchen.de"]kahan@informatik.tu-muenchen.de[/EMAIL]> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
;   pam password change = yes
# This option controls how unsuccessful authentication attempts are mapped 
# to anonymous connections
   map to guest = bad user
########## Domains ###########

########## Printing ##########

############ Misc ############

# Setup usershare options to enable non-root users to share folders
# with the net usershare command.
# Maximum number of usershare. 0 (default) means that usershare is disabled.
   usershare max shares = 100
# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
   usershare allow guests = yes
#======================= Share Definitions 
[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700
# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
#
# My Shares
#
[share1]
path = /media/sdb1
read only = No
guest ok = Yes
browsable = yes
writeable = yes
[share2]
path = /media/sdb2
read only = No
guest ok = Yes

-------  end of the smb.conf ------
 
 
Now I can do what I wanted to do:
go into the windows explorer and map a network drive. Now I can do that. 
 
Thanks for all of your help.
Bob

---

### Post by n8nt on 2010-08-13
Sad news...
I re-booted my Ubuntu and now I cannot access the files from windows. 
 
I tried changing the share names in the smb.conf but that did not work.
 
I cannot ping STS-UBUNTU2 but I can ping the ip address of 192.168.1.52
 
I guess I have to start over. What can a guy expect - it is Friday the 13th!

---

### Post by n8nt on 2010-08-13
OK. If I try to map a network drive using the IP address, for example, I put the following into the path textbox:
 
[\\192.168.1.52\share3]("file://\\192.168.1.52\share3")
 
then it works, that is, it makes a connection to the mounted filesystem on Ubuntu. 
 
I think there may be a problem of some kind when I re-boot the Ubuntu when the mapped drive is connected. I will try this test again - this time I'll close all connections first. Actually, I will unmount the ntfs file systems before shutting down the ubuntu. I did not do that before and when I tried to map a drive from the windows machine, I received an error saying that could not be done - but i don't remember the error now..
 
This is weird. Now when I start the ubunu back up, once again I cannot map to the shared drives.  I get an error that says 192.168.1.52 exists but  Windows can't find "share3".
 
If I go to my Ubuntu and run these 3 commands then it seems to allow me to connect to the NTFS drives from windows:
 
sudo service winbind restart
sudo service nmbd restart
sudo service smbd restart
 
Is all of this normal? I'm hoping that at least as long as I don't shut it down I'll not have problems.
 
I don't know why I can no longer reference the UBUNTU2 server by its name.

---

