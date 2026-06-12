---
title: "installing Courier (all components) login fail"
date: 2012-09-05
forum: General Help
---

### Post by palloy on 2012-09-05
I am running Ubuntu 12.04 with Cherokee 1.2.101 . 
I have installed Courier-ESMTP, -POP3S, -IMAPS and -webadmin from the  Ubuntu Software Centre (v0.66.1), and I'm now trying to get webadmin working so  that I can configure the Courier settings. 

The instructions at the courier website say that I should use the  installation instructions that come with the packaged pre-built  binaries, but they are the same, despite the file system layout being  somewhat different. 

/usr/lib/courier/libexec/courier/webmail/webadmin is actually at 
/usr/lib/courier/courier/webmail/webadmin . 
/usr/lib/courier/etc/webadmin/password is actually at 
/etc/courier/webadmin/password . 

I can get the Administrative Login screen up, and the installation  process already asked me to preset the password, and  /etc/courier/webadmin/password contains my password, but the login page  seems to reject my password and returns "302" and reloads the login page. 

I'm beginning to think that the Ubuntu installation process hasn't  worked properly. I can't find any "how-to install Courier on Ubuntu".  Does anyone have experience of Courier on Ubuntu?

---

### Post by TheFu on 2012-09-05
This seems like a webadmin issue, not a courier one.  Courier was pretty simple, at least the way we installed it. It sorta just worked.

Did you install webadmin using Software Center too?  Perhaps webadmin needs to see the courier installation when it is installed?

---

### Post by nothingspecial on 2012-09-05
Prefix changed from lubuntu to ubuntu

---

### Post by palloy on 2012-09-05
Just to be clear, webadmin is Courier-webadmin, and yes, it came from the USC. 

The instructions say to copy webadmin from /usr/lib/courier/libexec/courier/webmail/webadmin to /*<docroot>*/cgi-bin/ .  That did not exist, but I located it in /usr/lib/courier/courier/webmail/webadmin .

Next the instructions say to "Execute 'make install-webadmin-password'. This     prompts for a password, which is saved in the file     /usr/lib/courier/etc/webadmin/password".  Again that did not exist, but I located it at /etc/courier/webadmin/password and it already had the password in it from the install process, so this step isn't necessary if installed from USC.

I am running the browser from localhost, so SSL shouldn't be necessary. I set up Cherokee with a new virtual server "courier" and browsed to [http://courier/cgi-bin/webadmin](http://courier/cgi-bin/webadmin) and the login page came up OK. But neither my password nor "admin", "password" or null works. It just refreshes the page. No errors in error.log .

The webadmin file is an ELF binary which is mostly unreadable in gedit, but the string "/usr/share/courier/webadmin/webadmin.pl" is in there, and that file exists. I don't speak Perl, but I can make out that this does create the login page, amongst other things. "BADPASS" seems to be one error message.  Error messages go to [ open (STDERR, ">&STDOUT");  ] but I don't know where that is.

---

### Post by TheFu on 2012-09-06
I've never used webadmin, so these comments might not be helpful at all.

Are you certain that SSL isn't required for logins?  Just because something is local, doesn't mean the system doesn't configure to use it. You should definitely try it instead or de-configure that.  The system may display the login screen on port 80 (in addition to port 443), but only return results on port 443. That could explain what you are experiencing.

stderr and stdout are special files on all UNIX-like OSes.  There is nothing different about them here either.  That line redirects stderr into stdout ... which mean whatever server is running webmin should capture that output and do something with it.  Usually, that means put it into a log file.  I'd start looking under /var/log/ ... if cherokee a web server, then I'd look inside that log file?

Could it be that one part of the system is looking for files in a different place from the other.  If the instructions are just text files or from some web page, you'relooking for them on the system is probably smart.  However, if those locations are coming from part of an installation program/script - I'd definitely honor that somehow.  If more than 1 file isn't in the place that the other program thinks it should be, I'd find a way to fix that in some settings for one of them OR look into forcing an install where it is expected.

If you are tired of fighting with the packaged versions, you could grab the source for one or both tools and install using their normal method.  Long term, this isn't the best idea since package management doesn't exist and someone will manually need to install the updates as they come.  Given a choice, I'd install webmin that way but completely lock down which parts of the internet can reach it at all.  I'd block every IP except my static "desk" IP.  Webmin has had security issues, so doing that is a best practice anyway.

Sorry I'm not any real help.

---

### Post by palloy on 2012-09-06
> Are you certain that SSL isn't required for logins? 
The Courier documentation says "either SSL, or access from a local IP       address" so to get it up and running on my test machine I used localhost. The packaged Ubuntu documentation hasn't been modified, although some of the paths are different, so who knows.

 > I'd start looking under /var/log/ 
Yes, but I can't find anything relevant there.  I think I want the STDOUT of a process that was invoked by CGI in Cherokee. Does that have a standard place? 

> Could it be that one part of the system is looking for files in a different place from the other.
Yes, in which case I'll never be able to sort it out.

Thanks for the ideas, even if unhelpful. I has made me think it through again.

---

### Post by TheFu on 2012-09-06
> **palloy said:**
> Yes, but I can't find anything relevant there.  I think I want the STDOUT of a process that was invoked by CGI in Cherokee. Does that have a standard place? 

A web server will require stdout be  used for all CGI programs - that is where the generated HTML comes from  the CGI program back to the web server to be shipped to the web browser.  If the web server expects that  traffic to be displayed on a different port - not where you're browser  is waiting - then it doesn't care what your browser is doing and will try  that other port instead.   

stdout and stderr are special files on all POSIX systems, including Windows. It works exactly the same way on all of them.  redirection, pipes, etc. same-same.

Both webmin and cherokee use non-standard ports according to their project pages.  10000 for webmin and 9090 for cherokee. It is possible that the ubuntu installers decided to change those ports and that the integration effort made them different again. Web servers normally have 5-10 different configuration files to split up different aspects of the configuration into bite-sized amounts. Those files are stored in sub-directories so that file permissions can be shared with unprivileged users in a safer way.  For any specific virtual server, there are usually 2-3 related config files.  Sorry if I'm explaining more than you need.

 Are you running a firewall either on the system or at the router blocking the configured ports?  Basically, you need to find all the ports listed in each config for each server and  ensure those are all working.  I would use telnet for that testing.

Web servers often split logs between "access" and "errors" logs. These are usually different for each virtual web site too.  The locations are specified somewhere under /etc/apache/vhosts in apache.  Nginx works the same way /etc/nginx and so does pound (/etc/pound/).   I have no idea where Cherokee does it, but it would be a good guess that log file locations are configured under /etc/cherokee/????.conf in some way.  Inside the config file, it will point to 1 or more log files under /var/log ....  

This is pretty normal stuff.  99% of all servers work this way on UNIX - conf in /etc and logs in /var/log.  Only the Java servers get confused about where log and config files should be located.  They can't help it, since they actually believe that code will run on any platform without any tuning or knowledge of the platform.

If you are trying to set this up for home use, fantastic. You are learning in a way that you'll never forget. The general solution will be etched in your mind for any other service you want to run.

We've been talking concepts, but not specifics.  You need to post some config files for webmin and cherokee to get any real help.

Have you considered just using Courier without webmin?

---

