---
title: "Gitweb and apache server in ubuntu 10.04"
date: 2010-07-27
forum: General Help
---

### Post by VictorRodriguez on 2010-07-27
[FONT=Liberation Serif, serif][SIZE=3]Hi this is a simple problem  that I had with Ubuntu 10.04  , git 1.7.1.1, git web and apache http server 2.2.16. las week.[/SIZE][/FONT]
 

 [FONT=Liberation Serif, serif][SIZE=3]The main problema was that I couldn't implement a local server for and internal project in a LAN network and then public the Git repositories in a gitweb template and that any one inside the LAN could clone them by http . [/SIZE][/FONT] 
 

 [FONT=Liberation Serif, serif][SIZE=3]Well there are many pages of how to do this and they were very helpful you will find them in the end of this comment but I hope this detailed guide could help someone else if you follow this steps [/SIZE][/FONT] 
 

 [FONT=Liberation Serif, serif][SIZE=3]fist you should have installed in your computer the latest version of git  ( [http://git-scm.com/](http://git-scm.com/) ) or tipe [/SIZE][/FONT] 
 

 [FONT=Liberation Serif, serif][SIZE=3]	$sudo apt-get install git-core [/SIZE][/FONT] 
   
 [FONT=Liberation Serif, serif][SIZE=3]Install the apache server 2 [/SIZE][/FONT] 
 

 [FONT=Liberation Serif, serif][SIZE=3]	$sudo apt-get install apache2-utils apache2-common[/SIZE][/FONT]
 

 [FONT=Liberation Serif, serif][SIZE=3]Then after doing this you should be able to type in your browser  [http://localhost/](http://localhost/) and it should appear[/SIZE][/FONT]
 

  [FONT=Liberation Serif, serif][SIZE=3]It works![/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=3]This is the default web page for this server.[/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=3]The web server software is running but no content has been added, yet.[/SIZE][/FONT]
 

 [FONT=Liberation Serif, serif][SIZE=3]Well done you have a local server on your LAN wasn't so hard really ? So try it  type your IP in the web browser [/SIZE][/FONT] 
 

 [FONT=Liberation Serif, serif][SIZE=3]	$ifconfig [/SIZE][/FONT] 
 

 [FONT=Liberation Serif, serif][SIZE=3]will show your IP [/SIZE][/FONT] 
 

 [FONT=Liberation Serif, serif][SIZE=3]NOW THE HARDEST PART FOR ME sorry if it isn't for some one else. But I am new in linux and was hard. [/SIZE][/FONT] 
 

 [FONT=Liberation Serif, serif][SIZE=3]**VIRTUAL HOST 	**[/SIZE][/FONT]
 

 [FONT=Liberation Serif, serif][SIZE=3]imagine that this is not a computer instead a server, as you want well it should have the capability to handle different  web pages or hosts[/SIZE][/FONT]
 

 [FONT=Liberation Serif, serif][SIZE=3]Virtual Hosting allow web servers to host more than one website on a single  machine. This is how sharing hosting works. It will allow you to access to your local repository using addresses such as [http://dev.mysite.com](http://dev.mysite.com) instead of [http://localhost/~myuser/myproject/](http://localhost/~myuser/myproject/) :) .[/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=3]
First of all, you need an apache server ready to run on your machine (like we said before), if it is not yet install, open a terminal and type[/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=3]Once the server is installed, it is time to get into [/SIZE][/FONT]**[FONT=Liberation Serif, serif][SIZE=3]apache 2 configuration[/SIZE][/FONT]**[FONT=Liberation Serif, serif][SIZE=3].
Let's open apache's main configuration file, name [/SIZE][/FONT]**[FONT=Liberation Serif, serif][SIZE=3]/etc/apache2/apache2.conf[/SIZE][/FONT]**[FONT=Liberation Serif, serif][SIZE=3]. A search for the word [/SIZE][/FONT][FONT=Liberation Serif, serif][SIZE=3]virtual[/SIZE][/FONT][FONT=Liberation Serif, serif][SIZE=3] bring us to the following line:[/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=3]	[/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=3]	Include /etc/apache2/sites-enabled/[^.#]*[/SIZE][/FONT]
 

 [FONT=Liberation Serif, serif][SIZE=3]This mean that when starting apache, it will look for files in [/SIZE][/FONT]**[FONT=Liberation Serif, serif][SIZE=3]/etc/apache2/sites-enabled/[/SIZE][/FONT]**[FONT=Liberation Serif, serif][SIZE=3].
Lets go there and see what is in.[/SIZE][/FONT]
 [INDENT][FONT=Liberation Serif, serif][SIZE=3]$cd /etc/apache2/sites-enabled/[/SIZE][/FONT][/INDENT] [INDENT][FONT=Liberation Serif, serif][SIZE=3]$ls -l[/SIZE][/FONT][/INDENT] [INDENT][FONT=Liberation Serif, serif][SIZE=3]total 1[/SIZE][/FONT][/INDENT] [INDENT][FONT=Liberation Serif, serif][SIZE=3]lrwxrwxrwx 1 root root 36 2005-12-27 01:42 000-default -> /etc/apache2/sites-available/default[/SIZE][/FONT][/INDENT] [FONT=Liberation Serif, serif][SIZE=3]Well, this only links to the file in directory /etc/apache2/sites-available/ . You might wonder what is the point in doing such. Well, this simply allows you, mainly when you are using your box as a web server, to:[/SIZE][/FONT]
 
[LIST=1]
[*][FONT=Liberation Serif, serif][SIZE=3]Have 	a simple [/SIZE][/FONT][FONT=Liberation Serif, serif][SIZE=3]main 	configuration[/SIZE][/FONT][FONT=Liberation Serif, serif][SIZE=3] 	file[/SIZE][/FONT]
[*][FONT=Liberation Serif, serif][SIZE=3]Do 	be able to edit or create a new host by creating/editing a file from 	/etc/apache2/sites-available/[/SIZE][/FONT]
[*][FONT=Liberation Serif, serif][SIZE=3]In case 	your web server doesn't restart because of misconfiguration, you can 	simply remove the link from the file in /etc/apache2/sites-enabled/ 	pointing to the malformed file in /etc/apache2/sites-available/[/SIZE][/FONT]
[/LIST]
 [FONT=Liberation Serif, serif][SIZE=3]Now let say you want to be able to map the domain name [/SIZE][/FONT]**[[FONT=Liberation Serif, serif][SIZE=3]dev.example.com[/SIZE][/FONT]]("http://dev.example.com/")**[FONT=Liberation Serif, serif][SIZE=3] to you local machine, using the code file in [/SIZE][/FONT]**[FONT=Liberation Serif, serif][SIZE=3]/home/myuser/public_html/[example.com/]("http://example.com/")[/SIZE][/FONT]**[FONT=Liberation Serif, serif][SIZE=3].
While in [/SIZE][/FONT]**[FONT=Liberation Serif, serif][SIZE=3]/etc/apache2/sites-available[/SIZE][/FONT]**[FONT=Liberation Serif, serif][SIZE=3], create a new file (let say [/SIZE][/FONT][FONT=Liberation Serif, serif][SIZE=3]example.com.conf[/SIZE][/FONT][FONT=Liberation Serif, serif][SIZE=3])[/SIZE][/FONT]
 [INDENT][FONT=Liberation Serif, serif][SIZE=3]$sudo vi example.com.conf[/SIZE][/FONT][/INDENT] [FONT=Liberation Serif, serif][SIZE=3]Now add the following lines:[/SIZE][/FONT]
 [INDENT][FONT=Liberation Serif, serif][SIZE=3]<VirtualHost [dev.example.com]("http://dev.example.com/")>
ServerAdmin webmaster@localhost
#We want to be able to access the web site using [www.dev.example.com]("http://www.dev.example.com/") or [dev.example.com]("http://dev.example.com/")
ServerAlias [www.dev.example.com]("http://www.dev.example.com/")
DocumentRoot /home/myuser/public_html/[example.com]("http://example.com/")  
#if using awstats
ScriptAlias /awstats/ /usr/lib/cgi-bin/
#we want specific log file for this server
CustomLog /var/log/apache2/example.com-access.log combined
</VirtualHost>[/SIZE][/FONT][/INDENT] [FONT=Liberation Serif, serif][SIZE=3]Now, we specified a new host to apache but it is not yet linked to the repertory where apache actually look for virtual hosts. Let go to:[/SIZE][/FONT]
 [INDENT][FONT=Liberation Serif, serif][SIZE=3]$cd /etc/apache2/sites-enabled/[/SIZE][/FONT][/INDENT] [FONT=Liberation Serif, serif][SIZE=3]and create a link to the file we just created:[/SIZE][/FONT]
 [INDENT][FONT=Liberation Serif, serif][SIZE=3]$sudo ln -s /etc/apache2/sites-available/example.com.conf example.com.conf[/SIZE][/FONT][/INDENT] [FONT=Liberation Serif, serif][SIZE=3]Now apache is almost ready to restart, but before doing so, we must inform our linux system that [/SIZE][/FONT][[FONT=Liberation Serif, serif][SIZE=3]dev.example.com[/SIZE][/FONT]]("http://dev.example.com/")[FONT=Liberation Serif, serif][SIZE=3] and [/SIZE][/FONT][[FONT=Liberation Serif, serif][SIZE=3]www.dev.example.com[/SIZE][/FONT]]("http://www.dev.example.com/")[FONT=Liberation Serif, serif][SIZE=3] are not to be looked for on the net, but on the local machine instead.
To do so, simply edit [/SIZE][/FONT]**[FONT=Liberation Serif, serif][SIZE=3]/etc/hosts[/SIZE][/FONT]**[FONT=Liberation Serif, serif][SIZE=3] and add the new host names at the end of the line beginning by 127.0.0.1, which is localhost.[/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=3]
In the end, your file should look like:[/SIZE][/FONT]
 [INDENT][FONT=Liberation Serif, serif][SIZE=3]127.0.0.1 localhost.localdomain localhost [dev.example.com]("http://dev.example.com/") [www.dev.example.com]("http://www.dev.example.com/")[/SIZE][/FONT][/INDENT] [FONT=Liberation Serif, serif][SIZE=3]And now we are done, simply reload apache:[/SIZE][/FONT]
 [INDENT][FONT=Liberation Serif, serif][SIZE=3]sudo /etc/init.d/apache2 reload[/SIZE][/FONT][/INDENT] [FONT=Liberation Serif, serif][SIZE=3]Open your web browser and enter the following address [/SIZE][/FONT]*[[FONT=Liberation Serif, serif][SIZE=3]dev.example.com[/SIZE][/FONT]]("http://dev.example.com/")*[FONT=Liberation Serif, serif][SIZE=3]. And will bring your web page. [/SIZE][/FONT] 
 


 [FONT=Liberation Serif, serif][SIZE=3]**CLONING YOUR PROJECT BY YOUR VIRTUAL HOST**[/SIZE][/FONT]
 


 [FONT=Liberation Serif, serif][SIZE=3]If it works well there are just one single thing to do in order to work with static IP addresses  [/SIZE][/FONT] 
 [FONT=Liberation Serif, serif][SIZE=3]if your IP is FOR EXAMPLE 197.12.2.0 [/SIZE][/FONT] 
 [FONT=Liberation Serif, serif][SIZE=3]<VirtualHost 197.12.2.0:80>
	ServerAdmin webmaster@localhost
	#We want to be able to access the web site using [www.dev.example.com]("http://www.dev.example.com/") or [dev.example.com]("http://dev.example.com/")
	ServerAlias [www.dev.example.com]("http://www.dev.example.com/")
	DocumentRoot /home/myuser/public_html/[example.com]("http://example.com/")  
	#if using awstats
	ScriptAlias /awstats/ /usr/lib/cgi-bin/
	#we want specific log file for this server
	CustomLog /var/log/apache2/example.com-access.log combined
</VirtualHost>[/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=3]and thats all, try to put your IP address in other computer ant it will work with out touching the /etc/hosts file. [/SIZE][/FONT] 
 


 [FONT=Liberation Serif, serif][SIZE=3]Now lets check if this work in git repositories, that is what we want. [/SIZE][/FONT] 
 


 [FONT=Liberation Serif, serif][SIZE=3]Imagine that you have a Git project like project1, we need to clone it with –bare option in order to put it like public, this topic is well described in the progit book ([http://progit.org/book/](http://progit.org/book/)) on the public server chapter ([http://progit.org/book/ch4-5.html](http://progit.org/book/ch4-5.html)) when you have your git  repositories like project1.git in the example directory /home/yourname/yourrepos/  and you can clone it successfully with the instruction [/SIZE][/FONT] 
 


 [FONT=Liberation Serif, serif][SIZE=3]	git clone /home/yourname/yourrepos/project1.git [/SIZE][/FONT] 
 


 [FONT=Liberation Serif, serif][SIZE=3]in any place of your computer, it means that you just need to  do this[/SIZE][/FONT]
 


 [FONT=Liberation Serif, serif][SIZE=3]	$ cd project1.git[/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=3]	$ mv hooks/post-update.sample hooks/post-update[/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=3]	$ chmod a+x hooks/post-update[/SIZE][/FONT]
  


 [FONT=Liberation Serif, serif][SIZE=3]Next, you need to add a VirtualHost entry to your Apache configuration with the document root as the root directory of your Git projects. ( This was the part that I was stook for a week ) [/SIZE][/FONT] 
 [FONT=Liberation Serif, serif][SIZE=3]We already have a virtual host working ( that was why I decided to first implement the Visrtual Host in apache ) [/SIZE][/FONT] 
 [FONT=Liberation Serif, serif][SIZE=3]<VirtualHost 197.12.2.0:80> [/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=3]	ServerAdmin webmaster@localhost [/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=3]	ServerName git.example.com [/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=3]	ServerAlias [www.git.example.com](www.git.example.com) [/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=3]	DocumentRoot  /home/yourname/yourrepos[/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=3]	ScriptAlias /awstats/ /usr/lib/cgi-bin/ [/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=3]	CustomLog /var/log/apache2/example.com-access.log combined [/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=3]</VirtualHost> [/SIZE][/FONT]
 


 [FONT=Liberation Serif, serif][SIZE=3]You’ll also need to set the Unix user group of the drectories to [/SIZE][/FONT][FONT=Liberation Serif, serif][SIZE=3]www-data[/SIZE][/FONT][FONT=Liberation Serif, serif][SIZE=3] so your web server can read-access the repositories, because the Apache instance running the CGI script will (by default) be running as that user:[/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=3]	$ chgrp -R www-data  /home/yourname/yourrepos/[/SIZE][/FONT] [FONT=Liberation Serif, serif][SIZE=3]Now reload your apache and try to check your IP address in your web browser it will show your files, not in the way we want. [/SIZE][/FONT] 
 [FONT=Liberation Serif, serif][SIZE=3]Try to clone your project [/SIZE][/FONT] 
 [FONT=Liberation Serif, serif][SIZE=3][FONT=Liberation Serif, serif]	$git clone [http://197.12.2.0/project1.git](http://197.12.2.0/project1.git)[/FONT][/SIZE][/FONT] 


 [FONT=Liberation Serif, serif][SIZE=3]If it works, perfect you can keep on this tutorial.[/SIZE][/FONT]
   
 [FONT=Liberation Serif, serif][SIZE=3]**GITWEB **[/SIZE][/FONT] 
 


 [FONT=Liberation Serif, serif][SIZE=3]Install git web [/SIZE][/FONT] 
 [FONT=Liberation Serif, serif][SIZE=3]	$sudo apt-get install gitweb[/SIZE][/FONT]
 


 [FONT=Liberation Serif, serif][SIZE=3]clone the git project [/SIZE][/FONT] 
 


 [FONT=Liberation Serif, serif][SIZE=3]	[/SIZE][/FONT][FONT=Liberation Serif, serif][SIZE=3]$ git clone git://git.kernel.org/pub/scm/git/git.git[/SIZE][/FONT]
 


 [FONT=Liberation Serif, serif][SIZE=3]generate the custom CGI script[/SIZE][/FONT]
 


 [FONT=Liberation Serif, serif][SIZE=3]$[/SIZE][/FONT][FONT=Liberation Serif, serif][SIZE=3]cd git/[/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=3]$ make GITWEB_PROJECTROOT=" /home/yourname/yourrepos/" prefix=/usr gitweb/gitweb.cgi[/SIZE][/FONT] [FONT=Liberation Serif, serif][SIZE=3]$ sudo cp -Rf gitweb /var/www/[/SIZE][/FONT] [FONT=Liberation Serif, serif][SIZE=3]now check the /etc/gitweb.conf file , it shoul be something like this [/SIZE][/FONT] 
 


 [FONT=Liberation Serif, serif][SIZE=3]# path to git projects (<project>.git)    #### CHANGE TO YOUR PROJECTROOT###[/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=3][SIZE=3]$projectroot = "[/SIZE][FONT=Liberation Serif, serif][SIZE=3]/home/yourname/yourrepos/[/SIZE][/FONT][SIZE=3]"; [/SIZE][/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=3] # directory to use for temp files [/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=3]$git_temp = "/tmp"; [/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=3] # target of the home link on top of all pages [/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=3]#$home_link = $my_uri || "/"; [/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=3] # html text to include at home page [/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=3]$home_text = "indextext.html"; [/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=3]########CHANGE TO YOUR LAST VIRTUAL HOST ####[/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=3] @git_base_url_list = ('http://git.example.com'); [/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=3] # file with project list; by default, simply scan the projectroot dir. [/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=3]$projects_list = $projectroot; [/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=3] # stylesheet to use [/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=3]$stylesheet = "/gitweb/gitweb.css"; [/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=3] # logo to use [/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=3]$logo = "/gitweb/git-logo.png"; [/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=3] # the 'favicon' [/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=3]$favicon = "/gitweb/git-favicon.png";[/SIZE][/FONT]
 


 [FONT=Liberation Serif, serif][SIZE=3]Now we should make another Virtual Host like we did above  in the VIRTUAL HOST section[/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=3]but it should be like this [/SIZE][/FONT] 
 


 [FONT=Liberation Serif, serif][SIZE=3]<VirtualHost 197.12.2.0:80> [/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=3]ServerName dev.example.com [/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=3]ServerAlias [www.dev.example.com](www.dev.example.com) [/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=3]DocumentRoot /var/www/gitweb [/SIZE][/FONT]
     [FONT=Liberation Serif, serif][SIZE=3]<Directory /var/www/gitweb> [/SIZE][/FONT]
         [FONT=Liberation Serif, serif][SIZE=3]Options ExecCGI +FollowSymLinks +SymLinksIfOwnerMatch [/SIZE][/FONT]
         [FONT=Liberation Serif, serif][SIZE=3]AllowOverride All [/SIZE][/FONT]
         [FONT=Liberation Serif, serif][SIZE=3]order allow,deny [/SIZE][/FONT]
         [FONT=Liberation Serif, serif][SIZE=3]Allow from all [/SIZE][/FONT]
         [FONT=Liberation Serif, serif][SIZE=3]AddHandler cgi-script cgi [/SIZE][/FONT]
         [FONT=Liberation Serif, serif][SIZE=3]DirectoryIndex gitweb.cgi [/SIZE][/FONT]
     [FONT=Liberation Serif, serif][SIZE=3]</Directory> [/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=3]#if using awstats [/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=3]ScriptAlias /awstats/ /usr/lib/cgi-bin/ [/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=3]#we want specific log file for this server [/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=3]CustomLog /var/log/apache2/example.com-access.log combined [/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=3]</VirtualHost> [/SIZE][/FONT]
 


 [FONT=Liberation Serif, serif][SIZE=3]If you reload your apache it will tell you to use the name virtual host option, here is the best of apache the capabilityto handle more that one virtual host just. Here we've setup two different directory trees, one for each site. If you wanted to have identical content it might make sense to only create one, and then use symbolic links instead.[/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=3]The next thing to do is to enable virtual hosts in your Apache configuration. The simplest way to do this is to create a file called [/SIZE][/FONT][FONT=Liberation Serif, serif][SIZE=3]/etc/apache2/conf.d/virtual.conf[/SIZE][/FONT][FONT=Liberation Serif, serif][SIZE=3] and include the following content in it:[/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=3]#[/SIZE][/FONT] [FONT=Liberation Serif, serif][SIZE=3]#  We're running multiple virtual hosts.[/SIZE][/FONT] [FONT=Liberation Serif, serif][SIZE=3]#[/SIZE][/FONT] [FONT=Liberation Serif, serif][SIZE=3]NameVirtualHost *[/SIZE][/FONT] [FONT=Liberation Serif, serif][SIZE=3](When Apache starts up it reads the contents of all files included in [FONT=Liberation Serif, serif]/etc/apache2/conf.d[/FONT], and files you create here won't get trashed on package upgrades.)[/SIZE][/FONT]
 


 [FONT=Liberation Serif, serif][SIZE=3]To enable the sites that we have created simply run as root :[/SIZE][/FONT]
   [FONT=Liberation Serif, serif][SIZE=3]# a2ensite git.example.com [/SIZE][/FONT] 
 [FONT=Liberation Serif, serif][SIZE=3]and the same for all the sites enabled[/SIZE][/FONT]
 


 [FONT=Liberation Serif, serif][SIZE=3]At finally thats all, it  wasn't soo difficult but take some time to fix this problem  now when you load your web page it should look like [http://git.kernel.org/](http://git.kernel.org/) and you should be able to clone like your web page said. [/SIZE][/FONT] 
 [FONT=Liberation Serif, serif][SIZE=3]#################IMPORTANT #################[/SIZE][/FONT]
 


 [FONT=Liberation Serif, serif][SIZE=3]IF YOU HAVE A PROXY IN YOUR NETWORK YOU SHOULD DESEABLE COMPLETELY IF NOT SOME ERRORS LIKE 504 OR 500 WILL APEAR IN YOUR TERMINAL WHEN YOU TRIE TO CLONE THE PROJECTS [/SIZE][/FONT] 
 [FONT=Liberation Serif, serif][SIZE=3]TRY WITH unset http_proxy[/SIZE][/FONT]
  [FONT=Liberation Serif, serif][SIZE=3]it could work it depends how you had configure your proxy [/SIZE][/FONT] 
 [FONT=Liberation Serif, serif][SIZE=3]if some one else find another way to do this please feel free to contribute whit this long post [/SIZE][/FONT] 
 [FONT=Liberation Serif, serif][SIZE=3]Hope it could help someone trying to do implement gitweb in ubuntu 10.04 and apache 2 [/SIZE][/FONT] 
 [FONT=Liberation Serif, serif][SIZE=3]Thanks for all [/SIZE][/FONT] 
 [FONT=Liberation Serif, serif][SIZE=3]Sincerely yours [/SIZE][/FONT] 
 [FONT=Liberation Serif, serif][SIZE=3]Victor Rodriguez [/SIZE][/FONT] 
 


 [FONT=Liberation Serif, serif][SIZE=3]Bibliography [/SIZE][/FONT] 
 [FONT=Liberation Serif, serif][SIZE=3][http://progit.org/book/](http://progit.org/book/)[/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=3][http://www.debuntu.org/2006/02/22/7-virtual-hosting-using-apache-2](http://www.debuntu.org/2006/02/22/7-virtual-hosting-using-apache-2)[/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=3][http://www.debian-administration.org/articles/412](http://www.debian-administration.org/articles/412)[/SIZE][/FONT]

---

### Post by airtonix on 2010-12-31
sigh. 

1. this is copy paste from this fail guide.
2. you fail at using code blocks
3. what is awstats got to do with running a git http interface ? 

there a so many errors in this guide. why did you bother?

---

