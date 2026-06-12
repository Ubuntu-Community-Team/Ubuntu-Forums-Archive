---
title: "awstats"
date: 2010-03-20
forum: General Help
---

### Post by tommytomato on 2010-03-20
hi all

any one know of a link to a install tutorial for installing awstats on Ubuntu 9.10

I haven't been able to find one yet, they all seem to be older systems

TT ( karl )

---

### Post by Wingthor on 2010-03-25
Hi, 

Doesn't know about any tuts.. But I just downloaded the tar, and then runned the install script within the tools directory. Works fine, but have problems with the GeoIP plugin. However just use one tutorial you find best and install. This is is more an Apache/Perl issue this feature. But DO TAKE BACKUP OF YOU APACHE CONF file before starting the install procedure.

Regards

---

### Post by gordintoronto on 2010-03-25
> **tommytomato said:**
> hi all

any one know of a link to a install tutorial for installing awstats on Ubuntu 9.10

I haven't been able to find one yet, they all seem to be older systems

TT ( karl )

Run Administration/Synaptic and search for awstats. Select it for installation, click on "apply."

Then read this thread for a tutorial:
[http://ubuntuforums.org/showthread.php?t=8410](http://ubuntuforums.org/showthread.php?t=8410)

---

### Post by ScottyExpress on 2010-08-25
I am having a problem configuring AWStats. Here is copy of what I get when I run the configuration script:


----- AWStats awstats_configure 1.0 (build 1.8) (c) Laurent Destailleur -----
This tool will help you to configure AWStats to analyze statistics for
one web server. You can try to use it to let it do all that is possible
in AWStats setup, however following the step by step manual setup
documentation (docs/index.html) is often a better idea. Above all if:
- You are not an administrator user,
- You want to analyze downloaded log files without web server,
- You want to analyze mail or ftp log files instead of web log files,
- You need to analyze load balanced servers log files,
- You want to 'understand' all possible ways to use AWStats...
Read the AWStats documentation (docs/index.html).

-----> Running OS detected: Linux, BSD or Unix
Warning: AWStats standard directory on Linux OS is '/usr/local/awstats'.
If you want to use standard directory, you should first move all content
of AWStats distribution from current directory:
/home/scott
to standard directory:
/usr/local/awstats
And then, run configure.pl from this location.
Do you want to continue setup from this NON standard directory [yN] ? y

-----> Check for web server install

Enter full config file path of your Web server.
Example: /etc/httpd/httpd.conf
Example: /usr/local/apache2/conf/httpd.conf
Example: c:\Program files\apache group\apache\conf\httpd.conf
Config file path ('none' to skip web server setup):
> /etc/apache2/httpd.conf

-----> Check and complete web server config file '/etc/apache2/httpd.conf'
  All AWStats directives are already present.

-----> Need to create a new config file ?
Do you want me to build a new AWStats config/profile
file (required if first install) [y/N] ? y

-----> Define config file name to create
What is the name of your web site or profile analysis ?
Example: [www.mysite.com](www.mysite.com)
Example: demo
Your web site, virtual server or profile name:
> [www.scottyexpress.com](www.scottyexpress.com)

-----> Define config file path
In which directory do you plan to store your config file(s) ?
Default: /etc/awstats
Directory path to store config file(s) (Enter for default):
> /home/scott/awstats

-----> Create config file '/home/scott/awstats/awstats.[www.scottyexpress.com.conf](www.scottyexpress.com.conf)'
Error: Failed to open '/home/scott/wwwroot/cgi-bin/awstats.model.conf' for read.
scott@scott-desktop:~$ 


Anyone have any ideas?

Thanks!

[http://www.scottyexpress.com/ubuntu.htm](http://www.scottyexpress.com/ubuntu.htm)

---

