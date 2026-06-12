---
title: "Postfix email sending program not working"
date: 2011-10-17
forum: General Help
---

### Post by aplusguy on 2011-10-17
p { margin-bottom: 0.08in; }   

    My Linux operating system is Ubuntu 10.10.  I have a website with an online store developed in PHP ready to go into Production with the exception of being able to automatically send an email with the details of the order to the customer.  The default and recommended send mail program for Ubuntu 10.10 is Postfix.  According to the Postfix online manual, when Postfix is installed, it should work without changing any of the configuration files.  But it hasn't worked even once for me, not even after uninstalling it, and re-installing it.  I used the command 'sudo apt-get install postfix' in the Terminal window to install it initially, and that is a standard and correct syntax for Ubuntu 10.10.  There was a display on the screen saying that Postfix was successfully installed.  Also I successfully installed Apache2 successfully, and is working quite well for my test website.  I have uninstalled postfix and re-installed it via the Synaptic Package Manager (SPM).  I get the same result.  The output in the /var/log/apache2/error.log file is 'sh: usr/sbin/postfix: not found'.  To see what output I would get when I uninstalled Postfix, the output was the same.  So, I am thinking that Postfix isn't working at all, even when it is properly and successfully installed.   
    The only other possible cause of this problem that I can think of is if some of the configuration values in etc/postfix/main.cf may need to be changed.  I have searched the Internet extensively for help with this problem.  Also I have spent about $50 on two books that have only a few pages each on Postfix, and they have not been any help.  I simply can't seem to find enough information to help me resolve this problem.   
    Another possible factor of this problem is that I am not trying to set up a full-fledged server environment, such as example.com; my host provider will furnish the server.  I am using 'localhost' as a test environment, and I have some confusion about how I need to use that in the Postfix configuration file.  When initially installing Postfix, it asked for the domain name and hostname.  Upon subsequent re-installations of Postfix, those values were not requested again, so I assume they remained the same.  I think the domain name defaulted to '127.0.0.1', and I left it that way.  The hostname originally defaulted to 'user-System-Product-Name', but I changed it to 'PC1HostName' for brevity, and to have a more meaningful name.  If you know how to make Postfix work, I would immensely appreciate your help.  I have copied and pasted the /etc/postfix/main.cf below since that is a very important file for Postfix.
 

 # See /usr/share/postfix/main.cf.dist for a commented, more complete version 
  
  
 # Debian specific:  Specifying a file name will cause the first 
 # line of that file to be used as the name.  The Debian default 
 # is /etc/mailname. 
 #myorigin = /etc/mailname 
  
 smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu) 
 biff = no 
  
 # appending .domain is the MUA's job. 
 append_dot_mydomain = no 
  
 # Uncomment the next line to generate "delayed mail" warnings 
 #delay_warning_time = 4h 
  
 readme_directory = /usr/share/doc/postfix 
  
 # TLS parameters 
 smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem 
 smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key 
 smtpd_use_tls = yes 
 smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache 
 smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache 
  
 # See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for 
 # information on enabling SSL in the smtp client. 
  
 myhostname = PC1HostName 
 alias_maps = hash:/etc/aliases 
 alias_database = hash:/etc/aliases 
 mydestination = localhost, PC1HostName, localhost.localdomain, localhost 
 relayhost =  
 mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 
 mailbox_size_limit = 0 
 recipient_delimiter = + 
 inet_interfaces = loopback-only 
 default_transport = error 
 relay_transport = error 
 html_directory = /usr/share/doc/postfix/html 
 home_mailbox =  
 smtpd_sasl_auth_enable = no 
 smtpd_sasl_type = cyrus 
 smtpd_sasl_path = smtpd 
 smtpd_sasl_authenticated_header = no 
 smtpd_sasl_security_options = noanonymous 
 smtpd_sasl_local_domain =  
 broken_sasl_auth_clients = no 
 smtpd_recipient_restrictions = permit_mynetworks, reject_unauth_destination 
 smtpd_sender_restrictions =  
 mailbox_command =  
 smtp_use_tls = no 
 smtpd_tls_received_header = no 
 smtpd_tls_mandatory_protocols = SSLv3, TLSv1 
 smtpd_tls_mandatory_ciphers = medium 
 smtpd_tls_auth_only = no 
 tls_random_source = dev:/dev/urandom

---

### Post by hwttdz on 2011-10-17
The first place I'd look is where it says. What do you get if you run? 

which postfix
ls -l /usr/sbin/postfix

Also, preempting the next problem you'll have.  I set up postfix with a gmail smtp relay as most servers reject mail if you don't have a static ip with reverse dns setup.

---

### Post by dcstar on 2011-10-17
```
sudo dpkg-reconfigure postfix
```
Select "Internet" site and whatever else makes sense.

Set the internal network IP range to the real IP range as well.

---

