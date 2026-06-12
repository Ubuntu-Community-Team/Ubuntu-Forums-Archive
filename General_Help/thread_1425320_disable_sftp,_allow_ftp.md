---
title: "disable sftp, allow ftp"
date: 2010-03-08
forum: General Help
---

### Post by daytripper1021 on 2010-03-08
Hi, I want to allow ftp in the Ubuntu server that I have. SFTP was preinstalled but the client connecting to it doesn't have an SFTP client on their end.
 
What I've done is comment on this line on the sshd_config file in /etc/ssh:
 
# Subsystem sftp /usr/lib/openssh/sftp-server

I tried to test it by ftp attempt from my laptop to the ubuntu server but I still couldn't connect.
 
Is there anything else i should've done?

---

### Post by dcstar on 2010-03-08
> **daytripper1021 said:**
> Hi, I want to allow ftp in the Ubuntu server that I have. SFTP was preinstalled but the client connecting to it doesn't have an SFTP client on their end.
 
What I've done is comment on this line on the sshd_config file in /etc/ssh:
 
# Subsystem sftp /usr/lib/openssh/sftp-server

I tried to test it by ftp attempt from my laptop to the ubuntu server but I still couldn't connect.
 
Is there anything else i should've done?

Install a ftp server package.

---

### Post by daytripper1021 on 2010-03-09
> **dcstar said:**
> Install a ftp server package.
 
Hi David. I was able to download vsftpd when I ran "sudo /etc/init.d/vsftpd start" and the response was "OK."
 
However, when I did ps -ef|grep ftp no ftp process was running. further, my ftp tests failed.
 
hope u could help. thanks.

---

### Post by gmargo on 2010-03-09
How did you install it?  I just tried installing it on Karmic, and it installed fine and started automatically.  I just did this:
```

$ sudo aptitude -V -R install  vsftpd
[ normal install text, starts vsftpd server ]
$ ps -efw|grep ftp
root     20952     1  0 07:36 ?        00:00:00 /usr/sbin/vsftpd
gmargo   20961  2013  0 07:36 pts/1    00:00:00 grep ftp

```

---

### Post by daytripper1021 on 2010-03-09
> **gmargo said:**
> How did you install it? I just tried installing it on Karmic, and it installed fine and started automatically. I just did this:
```

$ sudo aptitude -V -R install  vsftpd
[ normal install text, starts vsftpd server ]
$ ps -efw|grep ftp
root     20952     1  0 07:36 ?        00:00:00 /usr/sbin/vsftpd
gmargo   20961  2013  0 07:36 pts/1    00:00:00 grep ftp

```
 
I installed via "sudo apt-get install vsftpd" command. 
 
I tried the sudo aptitude command you mentioned but still, no success:
 
```

[EMAIL="root@RPBox"]root@RPBox[/EMAIL]:~# sudo aptitude -V -R install vsftpd
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 70 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
[EMAIL="root@RPBox"]root@RPBox[/EMAIL]:~# ps -ef|grep ftp
root      6292  6271  0 09:43 pts/0    00:00:00 grep ftp

```
 
pls help. thanks.

---

### Post by gmargo on 2010-03-09
Try to purge it (aptitude purge vsftpd) then install it again.  What's the output of the install step?

---

### Post by daytripper1021 on 2010-03-09
> **gmargo said:**
> Try to purge it (aptitude purge vsftpd) then install it again. What's the output of the install step?
 
I did as you advised. Here's the output of the purge:
 
```

[EMAIL="root@RPBox"]root@RPBox[/EMAIL]:~# aptitude purge vsftpd
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
The following packages will be REMOVED:
  update-inetd{u} vsftpd{p}
0 packages upgraded, 0 newly installed, 2 to remove and 70 not upgraded.
Need to get 0B of archives. After unpacking 602kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 43750 files and directories currently installed.)
Removing vsftpd ...
 * Stopping FTP server: vsftpd                                                  No /usr/sbin/vsftpd found running; none killed.
                                                                         [ OK ]
Purging configuration files for vsftpd ...
Processing triggers for man-db ...
(Reading database ... 43697 files and directories currently installed.)
Removing update-inetd ...
Processing triggers for man-db ...
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
[EMAIL="root@RPBox"]root@RPBox[/EMAIL]:~# ps -ef|grep ftp
root      6482  6271  0 10:26 pts/0    00:00:00 grep ftp

```
 
And here's the reinstall result:
 
```

[EMAIL="root@RPBox"]root@RPBox[/EMAIL]:~# sudo aptitude -V -R install vsftpd
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
The following NEW packages will be installed:
  update-inetd{a} [4.31]  vsftpd [2.2.0-1ubuntu1]
0 packages upgraded, 2 newly installed, 0 to remove and 70 not upgraded.
Need to get 0B/162kB of archives. After unpacking 602kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Preconfiguring packages ...
Selecting previously deselected package update-inetd.
(Reading database ... 43688 files and directories currently installed.)
Unpacking update-inetd (from .../update-inetd_4.31_all.deb) ...
Selecting previously deselected package vsftpd.
Unpacking vsftpd (from .../vsftpd_2.2.0-1ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up update-inetd (4.31) ...
Setting up vsftpd (2.2.0-1ubuntu1) ...
update-rc.d: warning: vsftpd stop runlevel arguments (0 1 6) do not match LSB Default-Stop values (1)
 * Starting FTP server: vsftpd                                           [ OK ]
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
[EMAIL="root@RPBox"]root@RPBox[/EMAIL]:~# ps -ef|grep ftp
root      6603  6271  0 10:27 pts/0    00:00:00 grep ftp

```
 
Still no success. :(

---

### Post by gmargo on 2010-03-10
Everything looks good; sure seems like the daemon is starting.
Maybe someone else is listening on the ftp port, so vsftpd can't get it?  Use netstat -an to see if anyone is listening on port 21.
Is there anything in /var/log/vsftpd.log?

---

### Post by daytripper1021 on 2010-03-10
> **gmargo said:**
> Everything looks good; sure seems like the daemon is starting.
Maybe someone else is listening on the ftp port, so vsftpd can't get it? Use netstat -an to see if anyone is listening on port 21.
Is there anything in /var/log/vsftpd.log?
 
Hi. the vsftpd.log is empty (0 bytes). Below is the result of netstat -an:
 
```

[EMAIL="root@RPBox"]root@RPBox[/EMAIL]:~# netstat -an|grep 21
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN
tcp6       0      0 :::21                   :::*                    LISTEN

```
 
Does this mean I need to disable these processes? Doesn't vsftpd need this? If not, how do I remove them?
 
Thanks again.

---

### Post by asmoore82 on 2010-03-10
> **daytripper1021 said:**
> Hi, I want to allow ftp in the Ubuntu server that I have. SFTP was preinstalled but the client connecting to it doesn't have an SFTP client on their end.
 
What I've done is comment on this line on the sshd_config file in /etc/ssh:
 
# Subsystem sftp /usr/lib/openssh/sftp-server

I tried to test it by ftp attempt from my laptop to the ubuntu server but I still couldn't connect.
 
Is there anything else i should've done?

The best advice is get sFTP on the client end.
If the client is linux, a basic sftp client is built in to Gnome:
"Places -> Connect to Server..." and choose "SSH" as "Service type"
If you want something a little beefier, use filezilla.

If the client is windoze, use filezilla or winscp.

Any passwords you send over regular ftp _***[COLOR="Red"][SIZE="3"]will[/SIZE][/COLOR]***_ be snooped by *someone*.

If your Ubuntu Server's SSH service is exposed to the wide 'net,
just do this to prove to yourself that the bad guys are out there:
```
cat /var/log/auth.log| grep -i fail | grep root
```

---

### Post by daytripper1021 on 2010-03-11
> **asmoore82 said:**
> The best advice is get sFTP on the client end.
If the client is linux, a basic sftp client is built in to Gnome:
"Places -> Connect to Server..." and choose "SSH" as "Service type"
If you want something a little beefier, use filezilla.
 
If the client is windoze, use filezilla or winscp.
 
Any passwords you send over regular ftp _***[COLOR=red][SIZE=3]will[/SIZE][/COLOR]***_ be snooped by *someone*.
 
If your Ubuntu Server's SSH service is exposed to the wide 'net,
just do this to prove to yourself that the bad guys are out there:
```
cat /var/log/auth.log| grep -i fail | grep root
```
 
thanks asmoore I'm aware of the risk. we have dozens and dozens of servers here in the office intranet using ftp. access to internet by such servers is limited and protected by our IT security (I hope). hope u understand my need to have ftp instead.
 
thanks again.

---

### Post by gmargo on 2010-03-11
> **daytripper1021 said:**
> ```

root@RPBox:~# netstat -an|grep 21
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN
tcp6       0      0 :::21                   :::*                    LISTEN

```
Clearly you have another ftp daemon installed.  It doesn't show up in the **ps **output because **inetd** is doing the listening for it, and invokes the daemon on demand.  Look in **/etc/inetd.conf** (assuming the **openbsd-inetd** package is used) and you should see a line starting with ftp like this:
```

ftp             stream  tcp     nowait  root    /usr/sbin/tcpd  /usr/sbin/in.ftpd

```In this example (from my own main system), /usr/sbin/in.ftpd belongs to the **ftpd** package.  If you remove the conflicting ftp daemon package ("aptitude purge ftpd" in this case), then **vsftpd** should start successfully.  Or use the ftp daemon you already have installed (but **vsftpd** is a better choice is this is on an internet-facing port.)

If you have the **xinetd** package installed instead of **openbsd-inetd**, then the configuration is a bit different, probably in **/etc/xinetd.conf** and perhaps **/etc/xinetd.d/***.

---

### Post by daytripper1021 on 2010-03-12
hi gmargo. I found the inetd.conf file and it was empty. but still I removed the ftpd via " sudo apt-get remove ftpd" command plus " apt-get autoremove" as suggested by the system to clean the dependencies as well.
 
however, the problem still remains. :(
 
I tested FTP from my laptop to the server (command line) and all I got was below:
 
```

ftp 192.168.2.55
Connected to 192.168.2.55.
SSH-2.0-OpenSSH_5.1p1 Debian-6ubuntu2

```
 
no prompt for login appeared. further, when I checked the netstat -an command here's what I got:
 
```

[EMAIL="root@RPBox:/etc"]root@RPBox:/etc[/EMAIL]# netstat -an|grep 21
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN
tcp        0      0 192.168.2.55:21         172.16.72.157:55322     ESTABLISHED
tcp6       0      0 :::21          

```
 
The link is established but no login. I can't seem to disable the listening port of inet even when I've already uninstalled it.
 
Please help.
 
Thanks.

---

### Post by gmargo on 2010-03-12
> ftp 192.168.2.55
Connected to 192.168.2.55.
SSH-2.0-OpenSSH_5.1p1 Debian-6ubuntu2Looks like you've got Secure Shell configured to listen on port 21.  Check **/etc/ssh/sshd_config**.

---

### Post by daytripper1021 on 2010-03-15
> **gmargo said:**
> Looks like you've got Secure Shell configured to listen on port 21. Check **/etc/ssh/sshd_config**.
 
Hi the following lines were already commented in my sshd_config when I opened it:
 
```

# What ports, IPs and protocols we listen for
#Port 22
#Port 21
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
.
.
# Subsystem sftp /usr/lib/openssh/sftp-server
```
 
Pls help. thanks.

---

### Post by gmargo on 2010-03-15
Although your sshd_config does not indicate it, clearly ssh is still listening on port 21.  You do realize, don't you, that you can't just edit the config files and expect changes to take place; you must restart the daemons affected by them.  In fact, why don't you do a nice reboot just to make sure everyone is in sync?

---

### Post by daytripper1021 on 2010-03-15
> **gmargo said:**
> Although your sshd_config does not indicate it, clearly ssh is still listening on port 21. You do realize, don't you, that you can't just edit the config files and expect changes to take place; you must restart the daemons affected by them. In fact, why don't you do a nice reboot just to make sure everyone is in sync?
 
of course! reboot! Haaaay....it's working now! thank you thank you!!!! :)
 
```
ftp 192.168.2.55
Connected to 192.168.2.55.
220 (vsFTPd 2.2.0)
User (192.168.2.55:(none)): c0re
530 This FTP server is anonymous only.
Login failed.
ftp> bye
221 Goodbye. 
```
 
All I need to do left is to config vsftpd itself to allow non-anonymous logins. Thanks!!!

---

### Post by Lytspeed on 2010-05-11
Hello all,

I have read through this thread closely and tried the things mentioned, but I am still having trouble connecting to VSFTPD after upgrading to Server x64 10.4.  Before the upgrade, everything was working fine.  I have only one user account ("administrator") on the machine and need local user login with no anonymous logins allowed.

Here is the relevant content from my vsftpd.conf (everything else is commented out):

```
listen=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
ftpd_banner=Welcome to the machine_name Server FTP service.
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
local_root=/var/www/
```

Here is the result of the login attempt (done from local command line, but the result is the same from a remote machine.)  Note that the server responds with the correct banner, so I know no other FTP service is intercepting the command:

```
ftp localhost
Connected to localhost.
220 Welcome to the machine_name Server FTP service.
Name: administrator
331 Please specify the password.
Password:
530 Login incorrect.
Login failed.
ftp> bye
221 Goodbye.
```

Here is the result of the netstat command mentioned earlier in the thread, and I suspect this might be the source of my problem, but I don't know what it means or where to go from here:

```
sudo netstat -an|grep 21
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN     
unix  2      [ ACC ]     STREAM     LISTENING     40578    /tmp/orbit-administrator/linc-1960-0-12179382f0314
unix  3      [ ]         STREAM     CONNECTED     185121   
unix  3      [ ]         STREAM     CONNECTED     44421    
unix  3      [ ]         STREAM     CONNECTED     41621    /tmp/orbit-administrator/linc-19be-0-20008befa871
unix  3      [ ]         STREAM     CONNECTED     41121    
unix  3      [ ]         STREAM     CONNECTED     40721    
unix  3      [ ]         STREAM     CONNECTED     40581    /tmp/orbit-administrator/linc-1960-0-12179382f0314
unix  3      [ ]         STREAM     CONNECTED     40021    
unix  3      [ ]         STREAM     CONNECTED     7213     @/var/run/hald/dbus-FQdJKK4Uh8
unix  3      [ ]         STREAM     CONNECTED     7211     
unix  2      [ ]         DGRAM                    5821     
unix  2      [ ]         DGRAM                    4821     
```

Any advice is appreciated.

---

### Post by daytripper1021 on 2010-05-12
> **Lytspeed said:**
> Hello all,
 
I have read through this thread closely and tried the things mentioned, but I am still having trouble connecting to VSFTPD after upgrading to Server x64 10.4. Before the upgrade, everything was working fine. I have only one user account ("administrator") on the machine and need local user login with no anonymous logins allowed.
 
Here is the relevant content from my vsftpd.conf (everything else is commented out):
 
```
listen=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
ftpd_banner=Welcome to the machine_name Server FTP service.
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
local_root=/var/www/
```
 
Here is the result of the login attempt (done from local command line, but the result is the same from a remote machine.) Note that the server responds with the correct banner, so I know no other FTP service is intercepting the command:
 
```
ftp localhost
Connected to localhost.
220 Welcome to the machine_name Server FTP service.
Name: administrator
331 Please specify the password.
Password:
530 Login incorrect.
Login failed.
ftp> bye
221 Goodbye.
```
 
Here is the result of the netstat command mentioned earlier in the thread, and I suspect this might be the source of my problem, but I don't know what it means or where to go from here:
 
```
sudo netstat -an|grep 21
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN     
unix  2      [ ACC ]     STREAM     LISTENING     40578    /tmp/orbit-administrator/linc-1960-0-12179382f0314
unix  3      [ ]         STREAM     CONNECTED     185121   
unix  3      [ ]         STREAM     CONNECTED     44421    
unix  3      [ ]         STREAM     CONNECTED     41621    /tmp/orbit-administrator/linc-19be-0-20008befa871
unix  3      [ ]         STREAM     CONNECTED     41121    
unix  3      [ ]         STREAM     CONNECTED     40721    
unix  3      [ ]         STREAM     CONNECTED     40581    /tmp/orbit-administrator/linc-1960-0-12179382f0314
unix  3      [ ]         STREAM     CONNECTED     40021    
unix  3      [ ]         STREAM     CONNECTED     7213     @/var/run/hald/dbus-FQdJKK4Uh8
unix  3      [ ]         STREAM     CONNECTED     7211     
unix  2      [ ]         DGRAM                    5821     
unix  2      [ ]         DGRAM                    4821     
```
 
Any advice is appreciated.
 
I'll try to pay forward ok? :)
 
your netstat seems to be ok. can u try logging-in with a different userid?

---

### Post by gmargo on 2010-05-12
Is your "administrator" a normal user, or root?

---

### Post by Lytspeed on 2010-05-12
> **daytripper1021 said:**
> I'll try to pay forward ok? :)
 
your netstat seems to be ok. can u try logging-in with a different userid?

I created a new user ("ftptest") and tried logging in.  The result is the same:

```
ftp localhost
Connected to localhost.
220 Welcome to the CFH Web Server FTP service.
Name (localhost:administrator): ftptest
331 Please specify the password.
Password:
530 Login incorrect.
Login failed.
ftp> bye
221 Goodbye.
```

**gmargo**:  Both the "adminstrator" user and the "ftptest" user are members of the Administrator group, but are not specifically root.  I changed the "ftptest" user to a Desktop User and got the same result.

Thanks for your replies, folks.  As I mentioned before, I'm a bit flummoxed, because this was working fine before I upgraded to 10.4.

---

