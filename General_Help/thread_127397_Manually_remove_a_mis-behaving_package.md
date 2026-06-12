---
title: "Manually remove a mis-behaving package?"
date: 2006-02-08
forum: General Help
---

### Post by rmarkin on 2006-02-08
After a failed attempt to upgrade from php4.4 to php5 I am trying to revert back to php4.X.

One of the dependencies requires that phpmyadmin be removed.  Synaptic gives the following error in the "Error" "The following problems were found on your system" window:  "**E: phpmyadmin: subprocess pre-removal script returned error exit status 127**"

The "Terminal" view shows more of an explanation of the error: 

[B]Preconfiguring packages ...
(Reading database ... 99686 files and directories currently installed.)
Removing phpmyadmin ...
/var/lib/dpkg/info/phpmyadmin.prerm: line 12: db_get: command not found
dpkg: error processing phpmyadmin (--purge):
 subprocess pre-removal script returned error exit status 127[/B]

This throws a major kink in getting php working again because I can't install anything until phpmyadmin is gone!

"dpkg --configure -a" (as seen in another similar post returns nothing as shown below.  "dpkg -P phpmyadmin" then returns the same error.

[B]robert@ubuntu:~$ sudo dpkg --configure -a
Password:
robert@ubuntu:~$ sudo dpkg -P phpmyadmin
(Reading database ... 99686 files and directories currently installed.)
Removing phpmyadmin ...
/var/lib/dpkg/info/phpmyadmin.prerm: line 12: db_get: command not found
dpkg: error processing phpmyadmin (--purge):
 subprocess pre-removal script returned error exit status 127
Errors were encountered while processing:
 phpmyadmin
robert@ubuntu:~$[/B]

I tried what this post suggested -> [http://www.ubuntuforums.org/showthread.php?p=705969#post705969](http://www.ubuntuforums.org/showthread.php?p=705969#post705969)
and received the following (I am assuming he meant to write "apt-get remove phpmyadmin" instead of phpmyinstall):

[B]robert@ubuntu:~$ sudo apt-get remove phpmyadmin
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  phpmyadmin
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 11.1MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 99686 files and directories currently installed.)
Removing phpmyadmin ...
/var/lib/dpkg/info/phpmyadmin.prerm: line 11: /usr/share/debconf/confmodule: Permission denied
dpkg: error processing phpmyadmin (--remove):
 subprocess pre-removal script returned error exit status 1
Errors were encountered while processing:
 phpmyadmin
E: Sub-process /usr/bin/dpkg returned an error code (1)
robert@ubuntu:~$[/B]

Notice the "**permission denied**"

Any ideas?
How can I remove this program?
Can I remove it manually?  I hope I don't have to attempt that.

Thanks in advance for any ideas.

Robert

---

### Post by lamego on 2006-02-08
Did you check the permissions on /usr/share/debconf/confmodule ? 
You mau need to chown/chmod to give them access to root for the removal...

---

### Post by rmarkin on 2006-02-08
[QUOTE=lamego]Did you check the permissions on /usr/share/debconf/confmodule ? 
You mau need to chown/chmod to give them access to root for the removal...[/QUOTE]

The permissions of /usr/share/debconf/confmodule are root:root 644

Should I try maybe 744?

Thanks fo rthe reply

---

### Post by lamego on 2006-02-08
Yes you should...

---

### Post by rmarkin on 2006-02-08
Here are the results:

[B]robert@ubuntu:/usr/share/debconf$ sudo chmod 744 confmodule
Password:
robert@ubuntu:/usr/share/debconf$ ls -la
total 36
drwxr-xr-x    2 root root 4096 2005-10-07 22:50 .
drwxr-xr-x  254 root root 8192 2006-02-07 23:21 ..
-rwxr--r--    1 root root 2236 2005-09-16 07:42 confmodule
-rw-r--r--    1 root root 2831 2005-09-16 07:42 confmodule.sh
-rw-r--r--    1 root root  414 2005-09-16 07:42 debconf.conf
-rwxr-xr-x    1 root root 1999 2005-09-16 07:42 fix_db.pl
-rwxr-xr-x    1 root root 2138 2005-09-16 07:42 frontend
-rwxr-xr-x    1 root root 2390 2005-09-16 07:42 transition_db.pl
robert@ubuntu:/usr/share/debconf$ sudo apt-get remove phpmyadmin
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  phpmyadmin
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 11.1MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 99686 files and directories currently installed.)
Removing phpmyadmin ...
/var/lib/dpkg/info/phpmyadmin.prerm: line 13: db_get: command not found
dpkg: error processing phpmyadmin (--remove):
 subprocess pre-removal script returned error exit status 127
Errors were encountered while processing:
 phpmyadmin
E: Sub-process /usr/bin/dpkg returned an error code (1)
robert@ubuntu:/usr/share/debconf$  [/B]

What is the missing db_get command?

---

### Post by rmarkin on 2006-02-08
A locate attempt for db_get shows that there are no files named db_get on my machine at all.

Google searching db_get does not make it clear to me exactly where that command is supposed to reside.

Any ideas?

---

### Post by rmarkin on 2006-02-08
Does anybody know what the best / safest way would be to manually remove a mis-behaving package?

---

### Post by rmarkin on 2006-02-08
It looks like I have to manually remove phpmyadmin from by Breezy installation.  Can anybody assist me so that I don't remove anything necessary and so that Synaptic will understand that the package is gone?

Please reference this post -> [http://www.ubuntuforums.org/showthread.php?t=127345](http://www.ubuntuforums.org/showthread.php?t=127345)

Thank you,
Robert

---

### Post by MasJ on 2006-02-08
Well, I had the same problem a little while back. I can't remember exactly how I fixed it but if you search this forum for a solution, you'll find it. I'm sure I found it over here somewhere.
After using that trick, I managed to uninstall Phpmyadmin. It was just a simple chmod command, but to what file, I cannot remember. Sorry if this is of not much help..

---

### Post by MasJ on 2006-02-08
Well, I looked around a bit for you, the Phpmyadmin fix I used was not actually a chmod, it was what is described in this thread:
[http://www.ubuntuforums.org/showthread.php?t=79934](http://www.ubuntuforums.org/showthread.php?t=79934)

I'll quote the fix here for you.
[Quote=Surfoo]
Edit /var/lib/dpkg/info/phpmyadmin.prerm and before the comment "# Package maintainer's commands follow:", add this line :

. /usr/share/debconf/confmodule

without forget the point.
Save, and after apt-get remove phpmyadmin
[/quote]

Hope this helps..

---

### Post by pappo on 2006-02-08
I believe using "apt-get remove phpmyadmin" should do it.
Synaptic will know it is gone after you do a "apt-get update"

---

### Post by rmarkin on 2006-02-09
I wish that would do it.  If I try it I get the errors listed on the other thread.  Do you know how I could manually remove the package?

---

### Post by n5jyk on 2006-02-09
somthing to try...

open synaptic. search for phpmyadmin. click phpmyadmin once then click the "properties" button once. click the "installed files" tab. That should give you the location of everything installed.... HOWEVER. Since it also requires some php4 and apache1.3.x libs, I suggest fixing the broken packages or mark phpmyadmin for "complete removal" from within synaptic. I don't see a "complete remove" for apt-get.

If your apache and php is hosed.... you might want to remove them completely, apache and php, including libs, and start over.

If that doesn't work... maybe someone will come along very soon with the right answer.

-b

---

### Post by rmarkin on 2006-02-09
[QUOTE=n5jyk]somthing to try...

open synaptic. search for phpmyadmin. click phpmyadmin once then click the "properties" button once. click the "installed files" tab. That should give you the location of everything installed.... HOWEVER. Since it also requires some php4 and apache1.3.x libs, I suggest fixing the broken packages or mark phpmyadmin for "complete removal" from within synaptic. I don't see a "complete remove" for apt-get.

If your apache and php is hosed.... you might want to remove them completely, apache and php, including libs, and start over.

If that doesn't work... maybe someone will come along very soon with the right answer.

-b[/QUOTE]

Thanks for the reply.  I just did "apt-get -f install" with no packages and it seemed to clear up Synaptic so at least I can add packages again.  phpmyadmin is still installed and probably will not uninstall but I can live with that.  I had already tried removing everything like you mentioned but I couldn't because of the broken phpmyadmin package.  Now that I have Synaptic working again I re-installed apache2 and what was left of the needed php4 stuff.  Of course there are still some php5 things installed that I can't get rid of because of phpmyadmin.  And of course php is not parsing anything anymore, but that will be another post.  Thanks for the help!

---

### Post by rmarkin on 2006-02-09
MasJ,

Are you saying to include the period in front of /usr/share/...... or not include it?

---

### Post by MasJ on 2006-02-09
Include it. Don't leave the period out.
Just put this in, without the quotes:
". /usr/share/debconf/confmodule"

---

### Post by rmarkin on 2006-02-10
YEAH!  I did not notice that there was a space after the "." in the added line!  I typed it in correctly and voila it worked.  Thank you all very much for your help!

Robert

---

### Post by perceptor on 2006-02-15
Remove the file: /var/lib/dpkg/info/phpmyadmin.prerm

> sudo mv /var/lib/dpkg/info/phpmyadmin.prerm /var/lib/dpkg/info/phpmyadmin.prerm_bkp
sudo rm /var/lib/dpkg/info/phpmyadmin.prerm

---

### Post by jml75 on 2006-02-23
Thanx a million!

I was stuck with the same problem.

Did what you pointed out, fixed my problem!

Thanx!

---

### Post by hardbop200 on 2006-03-04
[QUOTE=MasJ]Well, I looked around a bit for you, the Phpmyadmin fix I used was not actually a chmod, it was what is described in this thread:
[http://www.ubuntuforums.org/showthread.php?t=79934](http://www.ubuntuforums.org/showthread.php?t=79934)

I'll quote the fix here for you.


Hope this helps..[/QUOTE]

Just want to let the writers in this thread know that this fix helped me as well.  I was unable to remove phpmyadmin until I read this tip.  It works great!  Thank you!

\\:D/

---

### Post by bohsocks on 2008-02-19
Hi... I'm having the same problem.... I tried to install the Dell Photo Printer 720 using a HOWTO on this website... and it didn't work... I"m trying to uninstall the package, and it won't let me:

rob@rob-laptop:~$ sudo apt-get remove z600cups
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libsm-dev libice-dev x11proto-xext-dev libatk1.0-dev x11proto-kb-dev
  libglib2.0-dev libotr2 x11proto-xinerama-dev libpango1.0-dev
  x11proto-render-dev libxi-dev libxrender-dev libcairo2-dev libxdmcp-dev
  libpng12-dev libfontconfig1-dev xtrans-dev x11proto-core-dev libxcursor-dev
  x11proto-randr-dev libgtk2.0-dev libxext-dev zlib1g-dev x11proto-input-dev
  libfreetype6-dev x11proto-fixes-dev libxau-dev libxrandr-dev libexpat1-dev
  libxft-dev libx11-dev libxfixes-dev libxinerama-dev
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  z600cups
0 upgraded, 0 newly installed, 1 to remove and 7 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 303kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 114781 files and directories currently installed.)
Removing z600cups ...
/var/lib/dpkg/info/z600cups.postrm: 2: /etc/init.d/cups: not found
dpkg: error processing z600cups (--remove):
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 z600cups
E: Sub-process /usr/bin/dpkg returned an error code (1)

This not working stops me from installing/uninstalling ANYTHING.... HELP!

---

