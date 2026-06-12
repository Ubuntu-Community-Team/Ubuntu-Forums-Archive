---
title: "A VPN and how to secure a webpage question"
date: 2012-10-08
forum: General Help
---

### Post by cackles on 2012-10-08
After upgrading from 8.04 all the way through to 12.04 last night I thought Id play with a couple things.

First is VPN. Ive taken a notion to set this up. Does anyone know/can suggest the best way for VPN so windows machines can connect? Ive read a ton of ways to do it and some are a bit dated, but the more recent seem to be focused more on ubuntu to ubuntu connections.

Second, Ive been trying to secure webpages and I can only do it if they are in a link. Basically if I .htaccess a folder and it has index.html it will load index.html. If I hit refresh when on the page it prompts for the pass then. I have secured plenty of pages, but they are all in subdirs from the directory .htaccess is located. I read there is a better way by using ubuntu, but the writer never elaborated.

Any help appreciated, thanks.

---

### Post by Lars Noodén on 2012-10-08
By secure a web page don't you mean running HTTPS?

Anyway, in regards to .htaccess.  Don't use it  unless you don't have administrative access to your web server.  If you do have administrative access to you web server, the changes go into the web server's configuration file under the section for the appropriate virtual host and directory.

---

### Post by Sidner on 2012-10-08
In regard to VPN, the easiest way is to configure a PPTP VPN, since it's comes built-in with Ubuntu and Windows.

About the secure website, I have all traffic coming to port 80 (http) forwarded to port 443 (https) and, of course, a virtual host for each one. Just search google, you're bound to find some guide to this.

---

### Post by Lars Noodén on 2012-10-08
> **Sidner said:**
> In regard to VPN, the easiest way is to configure a PPTP VPN, since it's comes built-in with Ubuntu and Windows.

About the secure website, I have all traffic coming to port 80 (http) forwarded to port 443 (https) and, of course, a virtual host for each one. Just search google, you're bound to find some guide to this.

PPTP might be the easiest but it defeats any security advantage a VPN might otherwise have given:

[http://www.h-online.com/security/features/A-death-blow-for-PPTP-1716768.html](http://www.h-online.com/security/features/A-death-blow-for-PPTP-1716768.html)

That's nothing new, just something final and irrevocable.

Ideally your services should be secure enough to handle a direct connection to the net.  If they are not, there they probably shouldn't be connected to the LAN either.  

If you still want a VPN, the better place to look would be IPsec or OpenVPN.  But the way to secure a web connection is to use HTTPS.

---

### Post by cackles on 2012-10-08
The pages are on my Ubuntu server, so I have full access. When I say secure, I meant password protect. Sorry, I spent about 18hrs solid trying to get .htaccess to work and looking at VPN so I was a bit fried. I have .htaccess 'working', but I cant seem to get the directory it is in protected, just the sub directories from where it is located. Means that at the top level if there is index and htaccess, index still loads and htaccess wont kick in unless the page is refreshed.

Any chance you can throw me a few keywords or a link to get me started using the virtual hosts solution, please? I keep coming across htaccess, php scripts and asp solutions.

I'll indulge in https in the near future, maybe tonight if I hit another wall with VPN and htaccess :)

PPTP is one of the things I noticed there was a few big warnings about giving a false sense of security. OpenVPN seems easy enough to setup server side, but I dont know how to connect to it using a windows machine. Seems like it would be simple enough to config a Linux client but I want to be able to simply fire up a windows machine from anywhere and use its native VPN support. But if I need to use another prog on top, I think I can deal with that.

---

### Post by Lars Noodén on 2012-10-08
You don't need .htaccess if you have administrative access to your web server.  .htaccess is a work-around to give some extra permissions to users without actually having to give any permissions at all to the server's configuration files.

It should go something like this:
```

<Directory /some/directory>
    AuthType Basic
    AuthName "Enter password"
    AuthBasicProvider file
    AuthUserFile /path/to/passwordfile
    Require valid-user
</Directory>

```

Look up [AuthUserFile](http://httpd.apache.org/docs/2.2/mod/mod_authn_file.html#authuserfile) and the others in the documentation for more details.  

Remember to reload the server's configuration after making changes.  Also, the password file should *not* be anywhere within DocumentRoot.  It should be outside.

[htpassword](http://manpages.ubuntu.com/manpages/precise/en/man1/htpasswd.1.html) is what you'll used to generate the passwords for basic authentication.  If you look you can tie it to various databases, but that's for later if ever.

---

### Post by cackles on 2012-10-08
That looks almost exactly like what Ive been doing with .htaccess. So the only difference is this goes into the default file in sites-enabled?

I have a dir under /home that Ive been putting the password files into to keep them seperate and out of the way and apache restart seems to be only two taps of a cursor key away nowadays. Also I think that when you make any file with a . at the start apache automatically hides it, not sure though, been months since I really looked at it.

Edit: apache.conf, got it, I think.
Edit; Edit: Nope, same result. So it must be something else Ive done. Ill backup my apache folder then purge apache and install again.

7hrs after the last edit and ... same result.

/home/cackles/mysite with index.html and .htaccess will allow index.html to load and wont prompt for a pass until the page is refreshed.

/home/cackles/mysite/subdir will prompt for a pass before it goes any further.

---

### Post by greenpeace on 2012-10-09
Could you post what you're putting into your configuration file?  For example, if you're configuring like: 

```
<Directory **/home/cackles/mysite/subdir**>
    ....
</Directory>
```

then I understand that access shouldn't be restricted to **/home/cackles/mysite/index.html**


Also, consider using **reload** rather than **restart**, to avoid downtime on your server when you're refreshing your configurations.  This should be appropriate: 

```
sudo service apache2 reload
```

---

### Post by Lars Noodén on 2012-10-09
> **cackles said:**
> That looks almost exactly like what Ive been doing with .htaccess. So the only difference is this goes into the default file in sites-enabled?

Yes.  .htaccess is only an extension of the configuration file.  It is for cases where you want to allow end users to do some configuration but without giving the whole vhost away.  Say [allowing tens of thousands of students and faculty to limit access to their own web pages](http://www.umich.edu/~umweb/how-to/htaccess.html).  Using the main configuration file simplifies things by keeping it all in the same place and reduces likelihood of mistakes, security  or other kinds.

In default Apache for Ubuntu, there is a default virtual host in  [font=Courier New]/etc/apache2/sites-available/default[/font]  Use that.

If you are putting web pages in your own home directory, you might be interested in the [user_dir](http://httpd.apache.org/docs/2.2/howto/public_html.html) module if you aren't already using it.

---

### Post by cackles on 2012-10-09
Tried using the default file but when I do it either goes to the default setup and ignores the vhost, gives error or keeps displaying last cached page, probably shouldnt but does. Im using a much shorter version.

Currently using

<VirtualHost *:80>
        ServerName mysite.com
        DocumentRoot /home/cackles/mysite/
</VirtualHost>

If I even attempt to use the default as a template it goes to internal server error 9/10 times. Both my vhosts look like that.

I have mysite1, mysite2 and default, basically.

I have

<Directory /home/cackles/mysite/test>
   AuthType Basic
    AuthName "Enter password"
    AuthBasicProvider file
    AuthUserFile /home/cackles/scrappass
    Require valid-user
</Directory>

For the password protection. I entered this into apache2.conf though. I also added /test so that I dont have any errors for now. So should that actually be in the vhost config file for that website? I saw examples with it in apache2.conf and httpd.




I might have the VPS part cracked, will see later if it works out. Havent started it yet but down to about three tuts with good potential.

---

### Post by greenpeace on 2012-10-09
OK, try putting a **<location>** directive in the **<VirtualHosts>** section for this domain.  I would put this in the main configuration file where I have defined all my VirtualHosts.  In my case that is: **/etc/apache2/apache2.conf**

Something like:

```
<VirtualHost *:80>
    ServerName your-url.com
    DocumentRoot /var/www/test
    CustomLog /var/log/apache2/access.log common
    <location />            
        Deny from all
        AuthType Basic 
        AuthName "Enter Password"
        AuthUserFile /home/cackles/scrappass
        require valid-user
    </location>
</VirtualHost>
```


let us know how you get on!

---

### Post by cackles on 2012-10-11
Still loads the page and this time when I refresh I get the forbidden page instead of the password box.

I dont put my vhosts into the apache.conf, I make individual files and a2ensite them.

My document root is in the home dir, not the www. Could this be the problem? I changed the example from /var/www/test to its dir in the code.

---

### Post by clay7 on 2012-10-11
Are you restarting Apache after making changes to the configuration files? That needs to be done so that the changes you make go into effect.

You probably know this but I just wanted to post this for the sake of those who don't know.

```
sudo restart apache2
```

---

### Post by greenpeace on 2012-10-11
@cackles, I'm not sure then... if I get a chance I'll try to replicate your setup on a spare box and test it.

ps. better practice is to *reload* apache, rather than restart, to avoid downtime:

```
sudo service apache2 reload
```

---

