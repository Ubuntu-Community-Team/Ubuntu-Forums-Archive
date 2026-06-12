---
title: "Apache will not start"
date: 2009-08-19
forum: General Help
---

### Post by keb329 on 2009-08-19
Hello everyone..  Hope someone can help me out here.  I've been running Ubuntu 8.04 with an Apache webserver on it for our math department using webwork.  It's been running great since last November but now Apache will not start.  I get the following message when I attempt to start it:

Syntax error on line 45 of /etc/apache2/conf.d/webwork.conf:
Can't locate Net/IP.pm in @INC (@INC contains: /opt/webwork/pg/lib
/opt/webwork/webwork2/lib 
/etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl . /etc/apache2) at /opt/webwork/webwork2/lib/WeBWorK/Authz.pm line 66.\nBEGIN failed--compilation aborted at /opt/webwork/webwork2/lib/WeBWorK/Authz.pm line 66.\nCompilation failed in require at /opt/webwork/webwork2/lib/WeBWorK.pm line 48.\nBEGIN failed--compilation aborted at /opt/webwork/webwork2/lib/WeBWorK.pm line 48.\nCompilation failed in require at /opt/webwork/webwork2/lib/Apache/WeBWorK.pm line 35.\nBEGIN failed--compilation aborted at /opt/webwork/webwork2/lib/Apache/WeBWorK.pm line 35.\n\t(in cleanup) Can't locate Net/IP.pm in @INC (@INC contains: /opt/webwork/pg/lib /opt/webwork/webwork2/lib /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl . /etc/apache2) at /opt/webwork/webwork2/lib/WeBWorK/Authz.pm line 66.\nBEGIN failed--compilation aborted at /opt/webwork/webwork2/lib/WeBWorK/Authz.pm line 66.\nCompilation failed in require at /opt/webwork/webwork2/lib/WeBWorK.pm line 48.\nBEGIN failed--compilation aborted at /opt/webwork/webwork2/lib/WeBWorK.pm line 48.\nCompilation failed in require at /opt/webwork/webwork2/lib/Apache/WeBWorK.pm line 35.\nBEGIN failed--compilation aborted at /opt/webwork/webwork2/lib/Apache/WeBWorK.pm line 35.\nCompilation failed in require at /etc/apache2/conf.d/webwork.conf line 62.\n

I have no clue what this is telling me.  All the files look ok to me.  I'm pretty new to linux and need help to get this server running again.

Thanks
KB

---

### Post by yeeeev on 2009-08-19
I don't know WebWork, but it seems that something in your configuration files is pointing to ip.pm which is no longer there.
I ran: aptitude search net-ip
and got the following:
p   libnet-ip-perl                  - Perl extension for manipulating IPv4/IPv6 
p   libnet-ipv6addr-perl            - Check validity of IPv6 addresses          
p   php-net-ipv4                    - IPv4 network calculations and validation  

Try installing them (start with whichever one that makes sense) and it might solve the issue.

Good luck!

---

### Post by keb329 on 2009-08-19
What I discovered is the usr/local folder was empty with a mod date on the folder of 04 Aug 2009.  I have no idea why these folders/files were deleted.  Fortunately there was a usr/local.old folder from November so I copied everything from local.old to local.  The server started then and appears to be running ok.  However, when I start the web server I get the following:

warn] The Alias directive in mod_perl at line 2 will probably never match because it overlaps an earlier Alias.

httpd not running, trying to start

I'd like to know what this is telling me and how to fix it.

Thanks,
KB

---

### Post by yeeeev on 2009-08-20
What it is telling (as far as I understand) is that one of the aliases in your mod_perl configuration files is a duplicate of a previously used alias. Check the mentioned line in the mod_perl conf file and see if it makes sense.

---

