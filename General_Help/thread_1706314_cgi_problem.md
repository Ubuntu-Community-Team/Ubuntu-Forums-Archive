---
title: "cgi problem"
date: 2011-03-13
forum: General Help
---

### Post by vivek.pandey on 2011-03-13
hey everyone
i am learning cgi on my own.just started and facing a problem, have googled for solution but couldnt find one. i wrote following code
```

#!/usr/bin/perl

print "Content-type:text/html\r\n\r\n";
print '<html>';
print '<head>';
print '<title>Hello Word - First CGI Program</title>';
print '</head>';
print '<body>';
print '<h2>Hello Word! This is my first CGI program</h2>';
print '</body>';
print '</html>';

1;

```
i have an apache server on localhost.
i saved this file as /var/www/hello.cgi
i also changed the permissions using
chmod 775 /var/www/hello.cgi
i could see this file on my server but when i click i just get the entire code and not the output of the code ie hello world

can anyone please suggest me how to rectify t

thanx in advance

---

### Post by r-senior on 2011-03-13
Have you looked at the "But it's still not working" section in here:

[http://httpd.apache.org/docs/2.2/howto/cgi.html]("http://httpd.apache.org/docs/2.2/howto/cgi.html")

"The source code of your CGI program or a "POST Method Not Allowed" message
    That means that you have not properly configured Apache to process your CGI program. Reread the section on configuring Apache and try to find what you missed."

---

### Post by vivek.pandey on 2011-03-13
> **r-senior said:**
> Have you looked at the "But it's still not working" section in here:

[http://httpd.apache.org/docs/2.2/howto/cgi.html]("http://httpd.apache.org/docs/2.2/howto/cgi.html")

"The source code of your CGI program or a "POST Method Not Allowed" message
    That means that you have not properly configured Apache to process your CGI program. Reread the section on configuring Apache and try to find what you missed."

thanx for your reply
actually i havent done the configuration it seems and started directly with codes..how stupid :-(
i dont remember where i imstalled apache2 so on terminal i typed wheris apache2
i got some 5 locations 
here are some problems
1) none of them are actually visible. i mean when i go to these locations i dont see any such folder but i can see them through my terminal

2) so i decided to work with terminal.used ls to see the files.out of those 5 locations i got, 1 had a file called httpd.conf as mentioned in that tutorial /etc/apache2httpd.conf
but the problem is it is empty.
i dont remeber touching that file ever but its empty . no cat no vi no nano no gedit works.. all return empty files


now please anyone tell whats this new panic
please help

---

### Post by r-senior on 2011-03-13
On Ubuntu the Apache config is slightly different from standard and makes it easier to set up multiple virtual servers. There's information here (more reading ;)):

[https://help.ubuntu.com/10.10/serverguide/C/httpd.html]("https://help.ubuntu.com/10.10/serverguide/C/httpd.html")

If this is just a testing/learning server, you can decide whether you want to make your CGI setup global or for the default virtual host. If you want to make everything global, the equivalent of httpd.conf is /etc/apache2/apache2.conf.

Don't be alarmed if you find Apache confusing to configure. You'll learn a lot. Once you get CGI up and running, if you want to continue with Perl you might also want to look into the mod_perl module, which is more efficient because it doesn't load up the interpreter on each request.

[http://en.wikipedia.org/wiki/Mod_perl]("http://en.wikipedia.org/wiki/Mod_perl")

Working from the terminal is probably the easiest option and good practice if you end up doing this is a server environment. In your case you can launch gedit with root privileges:

$ gksudo gedit <filename>

(In a server environment, you'd need to use a non-GUI editor, like vi :D or nano).

---

### Post by vivek.pandey on 2011-03-13
thanx for your time and links
in my /etc/apache2/apache2.conf there is nothing called ScriptAlias in it.so i just added one more ine in the configuration file ScriptAlias /cgi-bin/ /var/www/apache2/cgi-bin
but still nothing happens

and yes as far as gksudo gedit <filename> is concerned i prefer sudo gedit<filename>  :-)
thanx again

---

### Post by r-senior on 2011-03-14
> **neo_aryan said:**
> and yes as far as gksudo gedit <filename> is concerned i prefer sudo gedit<filename>  :-)

Most of the time sudo works, but gksudo (think graphical sudo) is best for GUI applications like gedit. Use sudo for command line programs like service, chmod, vi, etc.

$ gksudo gedit /etc/profile
$ sudo vi /etc/profile

More reading ;) ... [http://psychocats.net/ubuntu/graphicalsudo]("http://psychocats.net/ubuntu/graphicalsudo")

---

### Post by vivek.pandey on 2011-03-14
thanx again for your link.i keep learning new things here in this forum
but what about my original problem?
thanx

---

### Post by r-senior on 2011-03-14
You probably need to re-read the "configuring Apache" document and see what you missed. 

Some ideas:

* Did you try restarting Apache ($ sudo service apache2 restart)?
* Have you looked in the Apache log files (/var/log/apache2/*.log)?
* Is your script executable?
* Did you set the permissions properly on the Directory directive for the ScriptAlias?
* Do you have Perl installed?
* Have you searched for blog posts and tutorials written by someone who has done the same:

[how-to-install-apache2-webserver-with-phpcgi-and-perl-support-in-ubuntu-server.html]("http://www.ubuntugeek.com/how-to-install-apache2-webserver-with-phpcgi-and-perl-support-in-ubuntu-server.html")

---

### Post by vivek.pandey on 2011-03-14
thanx again for your reply
* i restarted my apache when i first uploaded the file and evrerytime afer that whenever i made some changes
* i have been using perl from last 2 months so no question of perl not being installed.. its actually installed by default
*here the problem is i checked /etc/apache2/apache2.conf i cant find scriptAlias directive so how can i uncomment it
* i went through many tutorials all say about that scriptAlias which i cant found in my config file
* i have taken the script from a tutorial.. it works when i click their link to see the output.so script isnt the problem
* problem is the scriptAlias so log file also is mot of any help
thanx again

---

### Post by r-senior on 2011-03-14
You need to add ScriptAlias somewhere. Try adding this to /etc/apache2/sites-available/default. In the middle somewhere - it doesn't matter as long as it's within the <VirtualHost> ... </VirtualHost> block. It may already be in there, commented out, or it may not. It should also work in /etc/apache2/apache2.conf, but that would be global, as discussed above:

```

ScriptAlias /cgi-bin/ "/usr/lib/cgi-bin/"

        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

```

This is what my /etc/apache2/sites-available/default contains (among other things). I just created your Perl script in my /usr/lib/cgi-bin directory and it works OK for me. Apart from the fact it should probably be "Hello World" of course. ;)

---

### Post by vivek.pandey on 2011-03-15
thanx you are trying to solve my problem so patiently and helpfully
wish my profs in college would be having these qualities 
anyways
ok i made a mess of the configuration files so reinstalled apache2.
now the when i type localhost i get 

This is the default web page for this server.

The web server software is running but no content has been added, yet.

i dont have any idea what i need to add as i have some files in /var/www..but unlike last time its not listing those files on default page

secondly i checked the ScriptAlias directive in the file /etc/apache2/sites-available/default  within the virtualhost block (as you said) and its there uncommented..it was there even last time . i was just trying to locate in /etc/apache2/apache2.conf..so was unable to find.this tim went for the correct location

thirdly i added a file hello.pl (which is the same cgi file) in /usr/lib/cgi-bin and saved it. now when i type localhost/cgi-bin/hello.pl 
i get this

```

Internal Server Error

The server encountered an internal error or misconfiguration and was unable to complete your request.

Please contact the server administrator, meet.vivek.pandey@gmail.com and inform them of the time the error occurred, and anything you might have done that may have caused the error.

More information about this error may be available in the server error log.

```

i dont have any idea now as what to do now
so please help me out
thanx a lot

---

### Post by vivek.pandey on 2011-03-15
anybody please ?

---

### Post by r-senior on 2011-03-15
OK ... let me try on this laptop that doesn't have Apache installed. (I've not shown the *output* for all commands here, only where it's important).

$ sudo apt-get install apache2

Then, enter this URL in a browser: [http://localhost](http://localhost). See first screenshot for output that confirms Apache is running. 

Now to add a document ...

$ cd /etc/apache2/sites-available/
$ grep DocumentRoot default
/var/www

$ sudo vi /var/www/test.html

```

<html>
	<head>
		<title>Test</title>
	</head>
	<body>
		<p>This is a test page.</p>
	</body>
</html>

```

Save and enter this URL in a browser: [http://localhost/test.html](http://localhost/test.html). See second screenshot for output that confirms this page is being served. 

Now to add a Perl script:

$ grep ScriptAlias default
ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/

$ sudo vi /usr/lib/cgi-bin/test.pl

```

#!/usr/bin/perl

print "Content-type:text/html\r\n\r\n";
print '<html>';
print '<head>';
print '<title>Test Perl</title>';
print '</head>';
print '<body>';
print '<p>Test Perl.</p>';
print '</body>';
print '</html>';

1;

```

Save it and make sure it's executable (remember that Apache is not running as root, so this needs to be world executable - perhaps not the best approach but it's just a test).

$ chmod +x /usr/lib/cgi-bin/test.pl

Enter this URL in a browser: [http://localhost/cgi-bin/test.pl](http://localhost/cgi-bin/test.pl). See third screenshot for output that confirms this Perl script is being served via CGI.

---

### Post by vivek.pandey on 2011-03-15
> **r-senior said:**
> OK ... let me try on this laptop that doesn't have Apache installed. (I've not shown the *output* for all commands here, only where it's important).


$ chmod +x /usr/lib/cgi-bin/test.pl



thanx a lot this line was the only thing missing...this did the trick
thanx a lot you dont know how grateful i am towards you..really learnt a lot from you...thanx again ;-)

---

