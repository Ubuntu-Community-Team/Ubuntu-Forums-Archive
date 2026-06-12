---
title: "Apache2 - virtual host 8080 port"
date: 2012-03-15
forum: General Help
---

### Post by spindler on 2012-03-15
I am having a problem pointing to a website on my development server which listens on port 8080.

When I type the IP address such as   192.166.123.111:8080  into a web browser I can see my default HTML webpage for my DEVELOPMENT WEBSERVER. 

When I type a domain address  such as  newsite.mysite.com I am directed to my PRODUCTION WEBSERVER  which is located at  the same IP address only it listens on port 80. 

This is my first website on my new development server and I am sure I have forgot something in setting up the virtual host file.   Here is the file:

<VirtualHost *:8080>
        ServerAdmin [EMAIL="me@mysite.com"]me@mysite.com[/EMAIL]
        ServerName newsite.mysite.com
        ServerAlias newsite.mysite.com


        DocumentRoot /home/websites/newsite
        <Directory />
                Options FollowSymLinks
                AllowOverride All
        </Directory>
        <Directory /home/websites/newsite>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride All
                Order allow,deny
                allow from all
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny


I created this file in the director  /etc/apache2/sites-available

I then ran the following commands.

 [B][FONT=Calibri]1.       [/FONT]Sudo a2ensite newsite
[FONT=Calibri]2.       [/FONT][/B]   [B]Sudo service apache2 reload
[FONT=Calibri]3.       [/FONT][/B]   **Sudo service apache2 restart**


I then rebooted the server for good measure but I am not able to get to my website.


Any help?


Spindler

---

### Post by wallaroo on 2012-03-17
I think you'll find this behavior is correct.

I presume you have set DNS (hosts file) to point 'mysite.com' to 192.166.123.111
By default all access to 'mysite.com' will be through port 80 unless specified otherwise.

By setting virtualhost details on port 8080, you are telling Apache what to do if someone comes in through port 8080, which in your case is to direct them to your development site.

Anyone coming in via port 80 will always be directed to your production site because that's the only site mapped to port 80.

Named Virtualhosts are really only effective when there are multiple sites on the same port, so all you need to do is set up your 'VirtualHost' on port 80, that way anyone coming in on 'mysite.com' will go to the default Production site while anyone coming in on 'newsite.mysite.com' will go to the Development site.

(But you can still have a port 8080 listener for your development site if you want to).

BTW: You're missing </Directory> and </VirtualHost> tags, did you also add a symbolic link in the 'sites-enabled' directory?

And another tip: After you make changes to Apache and restart it, make sure you empty your browser's cache before accessing your sites, otherwise you can get unpredictable results because the cache is generally used to access your site. The cache updates work on changes to the site documents and not to site structural changes.

---

### Post by spindler on 2012-03-18
Thank you very much.  This is helpful. I am not really sure what you mean by the following:

[SIZE=2][I]Named Virtualhosts are really only effective when there are multiple  sites on the same port, so all you need to do is set up your  'VirtualHost' on port 80, that way anyone coming in on 'mysite.com' will  go to the default Production site while anyone coming in on  'newsite.mysite.com' will go to the Development site.

[/I][SIZE=1]Do I set up a virtual host on the development server to listen to port 80?  My router does not allow two machines to listen on the same port.  So I am not sure how the command will be routed to the right server.  Can you explain a little more?

Is there a way I can get my production server to handle the virtual host request for the development server?  Is there a way I can point to the development server from my production server?[/SIZE][/SIZE]

---

### Post by wallaroo on 2012-03-18
Just to clarify, are you talking about two web sites on the same server with one instance of Apache, or are you talking about two physical servers (different PCs) each with an instance of Apache, one hosting the Prod site and the other hosting the Dev site?

You mention only a single internal IP address, so it's a bit unclear.

---

### Post by spindler on 2012-03-18
I have two physical computers on the network.  One has an Ip address of 192.168.1.100 (Production Server) and the other is 192.168.1.102 (DEV Server).  Each server is running apache2.

The router has port 80 open for 192.168.1.100(Production server) and port 8080 for 192.168.1.102 (dev server).  My production server has 4 or 5 websites and the development server will have a couple of websites that will need a year to develop before they can go live. It will be developed by many people and it would be easier to access via a domain name.   

The  reason why I have two physical computers is because while I am developing a new website code can be created that could sometimes crash the MYSQL or apache2...which then sometimes requires me to reload linux or a backup of a previous image.

I do not want my production websites affected.

---

### Post by wallaroo on 2012-03-18
OK thanks - that's a lot clearer now.

Your external DNS (your public web address) for arguments sake we'll say 'mysite.com' will always default to port 80 and your router will route all accesses to your production server (but you know that).

And yes if someone comes in on port 8080 your router will direct it to your development server, and you have an 8080 listener running on the server so all is OK.

So to catch and redirect the dev site address 'newsite.mysite.com' on port 80 you need to have some internal DNS that will re-direct it.

By default your Production Server will act as the internal DNS so if you make an entry in your '/etc/hosts' file on the production server, then port 80 calls to dev should redirect.

So adding '192.168.1.102 newsite.mysite.com' to file '/etc/hosts' on the Prod server should redirect all requests to that site to your development server. (It's a good idea to add entries for your Prod & Dev servers to the dev server 'hosts' file as well).

If your Production server has to go down for maintenance and you want the dev server to continue, then you can either tell you developers to only come in on port 8080 or temporarily modify the router to direct port 80 to the dev server and let its 'hosts' file manage re-directions.

---

### Post by spindler on 2012-03-19
Thanks for the help. This is making sense but I am still having a problem with the implementation.

I updated the hosts file on the production server.  This is what my hosts file looks like now.

[SIZE=2][I]127.0.0.1       localhost
127.0.1.1       ubuntu-server2.server.net       ubuntu-server2
192.168.1.102 newsite.mysite.com

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters[/I][/SIZE]

I did not update the hosts file on the dev server.  It is not clear to me as to why I need to. I would think that the virtual host file located on the dev server would then redirect the request to the folder.  Can you  explain why I need to update the hosts file on the dev server?

After updating this hosts file on the production server and reloading the web browser (clearing cashe) the website on the dev server is still not visible.  It still points to the production server default html page.

Is there a service I need to reload/restart to activate the changes?

---

### Post by wallaroo on 2012-03-19
oops! this will only work locally, not 'internet -> server -> server'.

I've revisited the various redirection methods available and I think the best method for your requirements is to use the '.htaccess' file on the production server to physically re-direct your users from 'newsite.mysite.com' to 'newsite.mysite.com:8080', which I'm sure is what you were looking for from the start.

This is best because it gets users off the production server rather than being continually channeled through the prod server.

So to set it up...

1. Enable mod_rewrite.
2. In the production site config file, locate the <Directory> entries for the site root directory.
    - 'FollowSymLinks' needs to be included in the 'Options' list.
    - 'AllowOverride Fileinfo' is needed.
3. In the actual root directory of the prod site create or edit the file '.htaccess'
    - add the following lines with the appropriate URLs...

        RewriteEngine on
        RewriteCond %{HTTP_HOST} ^newsite\.mysite\.com$ [NC]
        RewriteRule ^(.*)$ http://newsite.mysite.com:8080/$1 [R=301,L]


.. re-start Apache, clear your browser cache and that should do it.

---

### Post by wallaroo on 2012-03-19
Hi Spindler,

Did the revised solution work for you?

---

### Post by spindler on 2012-03-19
I see where you are going with this.  I am having a weird problem creating the file.

I am not located at my server.  I am remotely logging in and I cannot copy a file I created locally to my server.  I want to add the .htaccess file to the var/www directory since this is where I have the default html webpage for the production server. 

How do I create the file remotely?  Using putty through port 22, I attempted to do the following:

sudo gedit .htaccess
gksu gedit  .htaccess
sudo cat > .htaccess

I also tried uploading a zip file.

I keep getting a permission denied error even when the file has 777 permission.

Any idea how i can remotely do this?

---

### Post by wallaroo on 2012-03-20
Well that is odd. I would have thought you'd have the necessary authority.
Just in case Putty is imposing some restriction, try just ssh from a terminal.
Or try an FTP client to upload the file.

---

