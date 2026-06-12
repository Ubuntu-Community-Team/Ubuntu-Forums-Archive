---
title: "Apache2 - SSI not working"
date: 2010-07-25
forum: General Help
---

### Post by AF1HS on 2010-07-25
Following a catastrophic crash, Ubuntu 9.10 Server was reinstalled with the full LAMP configuration. However, the website pages that worked fine before the crash are only partially working now. Many of the .html files have "php includes" for headers, footers and sidebars and none of these are working anymore. 
 
I have looked through dozens of forums and examined SSI but they all seem to indicate the use of .shtml files. I just need plain vanilla html files to open embedded plain vanilla php files. I have the httpd.conf set up with the "Options +Include" and the "AddType text/html .html" lines and still no change after a restart.
 
What am I overlooking here?
 
TIA

---

### Post by robsoles on 2010-07-26
Make a file in the root of your website called phpinfo.php and give it the following content:
```
phpinfo();
```
(Pretty sure I am remembering my PHP days aright here but just Google 'phpinfo' command if I am wrong)

Then open the page in your browser thus: [http://example.com/phpinfo.php](http://example.com/phpinfo.php)

Please post back if you get a page full of information about your PHP setup or if it gives you an error response - I can pursue it from there with you.

---

### Post by AF1HS on 2010-07-26
I get what looks like  a normal phpinfo page.

---

### Post by robsoles on 2010-07-26
If it's public, please PM me the website's address - if not then please show me the source code a browser cops off the server for a resultant page from one of the .html files which includes some PHP script, I suppose you could just confirm for me that the server is just sending the code that should do the include?

Been a while since I was immersed in this stuff but it should come back quick enough to me with a little more exposure - also, each time one of us posts this thread goes to the top of a list and others might join in who are currently immersed instead of trying to remember stuff! ;)

---

### Post by AF1HS on 2010-07-26
The site is at [http://www.af1hs.com](http://www.af1hs.com)
 
If you do a "View Source" you can see where the php includes are being called but never acted upon.
 
Thanks for taking the time to help!!
 
Art

---

### Post by robsoles on 2010-07-26
In httpd.conf file make sure at least the second line, if not perhaps both of the following lines, are present in either the 'global' section or at least the specific website's section:
```
AddType text/html .html
AddOutputFilter INCLUDES .html
```please post back whether they were already there and if not whether or not this made it work.

---

### Post by AF1HS on 2010-07-26
My httpd.conf file contained the following:
 
DirectoryIndex     index.html   index.htm   index.php
AddType application/x-httpd-php  .php
Options  +Includes
 
I've modified it to what you suggested, restarted Apache2 and got a failure:
 
*We failed to correctly shutdown apache, so we're killiing all running apache processes.*
*This is almost certainly suboptimal, so please make sure your system is working as you'd expect now!*
*  . . . waiting Syntax error on line 2 of /etc/apache2/httpd.conf:*
*Invalid command 'AddOutputFilter', perhaps misspelled or defined by a module not included in the server configuration.*
 
Apache is NOT working now

---

### Post by robsoles on 2010-07-26
I hope you just removed the lines I gave you in my previous post and tried restarting it again.

Use the syntax that is shown in the file on the 'AddType application/x-httpd-php  .php' line to make the following instead:

AddType application/x-httpd-php  .html


EDIT: Don't put it at the start of the file please! Put this new line I am suggesting straight after the line I have modeled it from. Those other lines shouldn't have gone at the start of the file but after the 'modules'.so section of the file!

I should have told you to make a backup of your httpd.conf file before applying an edit so you would only need to copy the backup back over the original again and restart it to recover if something about the edit trashed it - sorry.

---

### Post by AF1HS on 2010-07-26
I have no 'modules' section.  I saved the original httpd.conf when I first started editing it and it had just the one line:
 
   DirectoryIndex    index.html
 
I'm assuming the 'modules' section is sitting in apache2.conf which in turn pulls in the httpd.conf changes.
 
If you've recently gone to the website, it's thoroughly messed up now pulling up a dialog box about the application/x file - trying to clean up that mess now.

---

### Post by wojox on 2010-07-26
Did you Port Forward port 443 on your router?

---

### Post by robsoles on 2010-07-26
> **wojox said:**
> Did you Port Forward port 443 on your router?

Question is about Server Side Includes and not SSL Encryption.



@AF1HS: I get your "It works!" page each time I check since finding your post this morning.

I sure hope you can get your site's home directory re-configured into apache's configuration real soon!!

Did you backup the entire set of .conf files for it before you (I assume) re-installed it?

---

### Post by AF1HS on 2010-07-26
robsoles:
 
true - I never needed port 443 when this worked earlier - only 80 is opened.
 
I had to step away from the server for a while and I'm glad to see that I'm beyond that earlier application-x error.
 
I don't use the default /var/www/ directory so I'll have to change the pointer and see if I can get the web pages back in view.
 
I hope this works :)

---

### Post by wojox on 2010-07-26
Doht my bad. I thought SSL. Sorry AF1HS.;)

---

### Post by AF1HS on 2010-07-26
Looks like that fixed it!!  Thank you so much for all the time you spent helping out.
 
Gotta run and check to make sure the "whole" thing is back  :p
 
 
Thanks again!!

---

### Post by robsoles on 2010-07-26
Welcome, site looks much more functional now!

Please consider marking your thread as solved using the 'thread tools' in red above.

---

