---
title: "Unable to set up vsftpd with SSL &quot;ECONNREFUSED&quot;"
date: 2011-01-30
forum: General Help
---

### Post by Dark_Jester on 2011-01-30
I am running Ubuntu 10.10 in a Virtualbox machine, and I have been trying to set up an FTP server using vsftpd, but to no avail.

I have been following [epimeteo's]("http://ubuntuforums.org/member.php?u=54113") howto at [http://ubuntuforums.org/showthread.php?t=518293](http://ubuntuforums.org/showthread.php?t=518293), but I keep running into this same problem. Every time I try to enable SSL on the server, the entire thing breaks and I can't even restart the server any more! 

Before I try to add SSL capabilities, my settings in **/etc/vsftpd.conf** look like this:
```
# FTP config file /etc/vsftpd.conf
listen=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
dirmessage_enable=YES
use_localtime=YES
xferlog_enable=YES
connect_from_port_20=YES
idle_session_timeout=600
data_connection_timeout=120
ftpd_banner=Welcome to the Netherworld FTP service.
chroot_local_user=YES
chroot_list_enable=YES
chroot_list_file=/etc/vsftpd.chroot_list
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/private/ssl-cert-snakeoil.key
userlist_deny=NO
userlist_enable=YES
userlist_file=/etc/vsftpd.allowed_users
```This works. I can use standard FTP to log in with my account user/pass. 

I then append the following to the file, in an attempt to enable SSL:
```
#
# SSL settings
ssl_enable=YES
allow_anon_ssl=NO
force_local_data_ssl=YES
force_local_logins_ssl=YES
ssl_tlsv1=YES
ssl_sslv2=YES
ssl_sslv3=YES
# Filezilla uses port 21 if you don't set any port
# in Servertype "FTPES - FTP over explicit TLS/SSL"
# Port 990 is the default used for FTPS protocol.
# Uncomment it if you want/have to use port 990.
#listen_port=990
```I then reset the server so it will use the new settings, here is the terminal output:
```
$ sudo restart vsftpd
vsftpd start/running, process 3192

```At this point, it stops working. When I try to use Filezilla to connect to 127.0.0.1 in FTPES mode, I get the following:
```
Status:    Connecting to 127.0.0.1:21...
Status:    Connection attempt failed with "ECONNREFUSED - Connection refused by server".
Error:    Could not connect to server
```At first I thought perhaps I needed to tell Filezilla to use port 990 instead of 21. But this did not change the result. So I tried to uncomment the last line "**listen_port=990**" in the vsftp.conf. This is when I noticed a problem. I cannot reset the server:
```
$ sudo restart vsftpd
restart: Unknown instance: 
```Restarting the machine does not help, so all I can think to do is completely remove and reinstall vsftpd using **sudo apt-get remove --purge vsftpd** and **sudo apt-get install vsftpd. **But while this will reset everything to the basics and let me gain access to the server it does not solve the problem. I still cannot enable SSL without the server breaking.

Thank you for sticking with me through that long winded problem description, I hope somebody can help me solve this problem, I've been trying for 3 days to get this server going!

-Edit: I managed to find out that the server was trrowing a silent error that I could read by manually running vsfptd. This pointed me to a problem in the configuration with the RSA certificate, and a quick fix and reboot later it was working :)

---

### Post by journeyfarm on 2012-12-12
Thank you for the tip.  I had the same issue and it turned out that I did not install the RSA certificate yet.

I used the instructions on this website to generate a certificate:

[http://wiki.vpslink.com/Configuring_vsftpd_for_secure_connections_%28TLS/SSL/SFTP%29#Generate_a_Certificate](http://wiki.vpslink.com/Configuring_vsftpd_for_secure_connections_%28TLS/SSL/SFTP%29#Generate_a_Certificate)

It also required adding a link to the certificate in the vsftpd config file.

---

### Post by Trevor_Rose on 2013-09-12
I was having a similar problem just now, but I found there was nothing wrong with my set up in Ubuntu, it was the settings in the FTP client (Filezilla) that were wrong ... so double check that (mine was fine once I changed it from a computer name to specific IP address, and also made sure it was in passive mode, and not assuming a port number) ;-)

---

