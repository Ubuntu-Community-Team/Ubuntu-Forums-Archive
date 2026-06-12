---
title: "lamp issue?"
date: 2011-04-13
forum: General Help
---

### Post by speckmc on 2011-04-13
having an issue here with an ubuntu web server

it seems as it is a permissions issue i can go in through nautilus and set the permissions so that anyone can view...

however as soon as my "web designer" makes changes and uploads them via the ftp client... i get

403 forbidden 
you dont have permission to access ______________ on this server

i can then go back in and change permissions and everything works again...

im considering killing the server, formatting and starting over..

i made the mistake of loading a gui on this thing (im a windows admin) and i dont need it now, as im a lot more comfortable with the command line portion, infact i find myself opening the terminal window on the gui and doing everything that way....

soo my question is, is there any easy fix to this, or do i just need to kill it and start a new
?

or do i pack up my linux bag and crawl back to windows (dont want to do that)

:confused:

---

### Post by fragos on 2011-04-13
The problem is likely how your developer had permissions set before the FTP. Others: may not be set to read only.

---

### Post by speckmc on 2011-04-13
> **fragos said:**
> The problem is likely how your developer had permissions set before the FTP. Others: may not be set to read only.

but if i set others to read only then we cant upload via ftp, nor can i access the site, im thinking i need to just give up and kill the server and reformat reinstall and leave off the gui


or are you saying how he has his set when hes creating the content before he uploads, hes using a windows based box and dream weaver

---

### Post by fragos on 2011-04-13
The Windows based box and file systems are the problem as they don't have the permissions scheme used by Linux and therefore the Apache server. After FTP from Windows the permissions need to be reset on the server. Read only is the proper setting for the user Other: of web pages as your webmaster and you can log into the FTP as Owner: and have Read Write. Your developer should have known this.

---

### Post by speckmc on 2011-04-13
> **fragos said:**
> The Windows based box and file systems are the problem as they don't have the permissions scheme used by Linux and therefore the Apache server. After FTP from Windows the permissions need to be reset on the server. Read only is the proper setting for the user Other: of web pages as your webmaster and you can log into the FTP as Owner: and have Read Write. Your developer should have known this.


my web guy doesnt even know what linux or apache is, hes good at making pretty pictures, but hasnt a clue what hes doing on anything else

ill have to see what i co do with the permissions, this will be a bit of a pain in the **** having to log onto the linux box and update permissions every time he makes a change, he seems to edit things almost daily...

is there any work around for this so that we dont have to do this every time he makes a change to the site and uploads it?

---

### Post by fragos on 2011-04-13
If your web guy doesn't understand the basics of the Internet you need a new one that does. You shouldn't have to make up for his failures. If he can't upload a page that renders on the Internet he hasn't done his job.

---

### Post by SeijiSensei on 2011-04-13
First of all, it's bad practice to make edits to a production site.  Clone the site to another directory and let the developer play with that.  When everyone has signed off on the changes, move them into production.  (You do have method for reviewing his changes before they are committed to public display, yes?)

I actually maintain three versions of the sites I work on.  One is production; it's never touched until everyone is happy with any new changes being made.  The second is a demo site that my clients can review before the changes are migrated into production.  The third is the development site that I can play with knowing that if I break something it won't affect either of the other sites.  When we're ready to release a new version of the site, I move the production site into an archive, copy the demo site to production and, if the development site is ready for review, make that the new demo site.

You can play with things like group membership and permissions on the developer's account to insure whatever is uploaded has the right ownerships.  I'd strongly suggest that's not the way to go, however.  Have the developer work in the cloned site and move things into production when everyone agrees they're ready to go.

---

### Post by speckmc on 2011-04-14
> **SeijiSensei said:**
> First of all, it's bad practice to make edits to a production site.  Clone the site to another directory and let the developer play with that.  When everyone has signed off on the changes, move them into production.  (You do have method for reviewing his changes before they are committed to public display, yes?)

I actually maintain three versions of the sites I work on.  One is production; it's never touched until everyone is happy with any new changes being made.  The second is a demo site that my clients can review before the changes are migrated into production.  The third is the development site that I can play with knowing that if I break something it won't affect either of the other sites.  When we're ready to release a new version of the site, I move the production site into an archive, copy the demo site to production and, if the development site is ready for review, make that the new demo site.

You can play with things like group membership and permissions on the developer's account to insure whatever is uploaded has the right ownerships.  I'd strongly suggest that's not the way to go, however.  Have the developer work in the cloned site and move things into production when everyone agrees they're ready to go.

I agree he hasn't or isn't doing his job, but I didn't hire the guy, my boss did, unfortunately....

As far as the site goes, I'd like to have a few versions to play with, however, two things have a tendancy to happen:
1. My boss has one of those "moments of enlightenment" and calls "mr web guy" and says "change this that and this... NOW..." no questions of what will it cause will the site go down.. Nothing
2. The government calls up and say....and I kid you not here.. "we need you to change this we don't like how it's worded" or "you have a mis-spelling on your site on page x 10 lines down on the 2nd paragraph... Fix it" and a slew of other demands.. If we don't comply within 24 hrs ... boom fine

So while different versions would be nice nobody in this place will ever move rapidly enough for the gorvernments happiness nor would they comply with approving things as they are all far too lazy for that!

And like I said I'm a windows admin but I don't want another windows server in my farm to maintain lol so I'd like to stick with Linux, but I need to find a way for mr bone head to stop messing up the permissions, and Linux is still new to me so lol... I know a gummed up the whole works and beauty of a Linux server by installing the stupid GUI on the bleedin thing as well. hencethe consideration of just killing it and starting o er

---

### Post by SeijiSensei on 2011-04-14
So from what you've posted, the problem is that developer connects with FTP under his username so the uploaded files aren't visible to the www-data user?

Here's one approach you can try.  First make the FTP user's primary group be "www-data", the same as the owner of /var/www.

```
sudo usermod -g www-data username
```

Next, make sure that /var/www is owned by www-data with group www-data, and that the directory is group-writable like this:

```
cd /var
sudo chown www-data.www-data www
sudo chmod g+w www

```

Now he should be able to upload files to /var/www that will be owned by the developer's username with group www-data.  Of course, if the website is in some non-standard location instead of /var/www, you'd apply these commands to that directory instead.

Try this yourself first in some other directory like your $HOME.  I might have missed something along the way.  

Another option is to use [Samba]("https://help.ubuntu.com/community/Samba") and let the developer connect to the share with Windows.  Define a share for the website in /etc/samba/[smb.conf]("http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html") like this:

```

[website]
    path = /var/www
    valid users = developer
    force user = www-data
    force group = www-data

```

The "force user" and "force group" directives make Samba write to the operating system as the specified user and group rather than with the "developer" username.

Create an smb user with the same username and password as the developer has now (replace "developer" with his user name in the share definition above).  

```
sudo smbpasswd -a developer
```

For added security, remove all the other share definitions from smb.conf except this one.  If the developer's IP address is static, or if it's dynamic from a known range, you can further enhance security by adding "hosts allow = [IP address or subnet]" like "hosts allow = 10.10.10.10" or "hosts allow = 10.10.10.0/24".  You probably want to add your local network address or subnet to the list as well.

You'll need to open ports 137-139 on the server's firewall.  Another way to enforce security is to limit access to these ports to only the IP address(es) he connects from.  If you use iptables, you'd want to add a rule like:

```
iptables -A INPUT -p tcp -s 10.10.10.0/24 --dport 137:139 -j ACCEPT
```

This approach lets the developer "map a network drive" in Windows, say W:, that points to \\server\website.

---

### Post by speckmc on 2011-04-14
thank you! most helpful reply so far!! i really do appreciate it, ill attempt this tonight when i get onsite :P  i think i need to open up telnet access to the damn thing lol that way i can do stuff remotely, i take vacations but, usually they end up being a working vacation:( so remote access is something i usually have to setup

---

### Post by SeijiSensei on 2011-04-14
> **speckmc said:**
> thank you! most helpful reply so far!! i really do appreciate it, ill attempt this tonight when i get onsite :P  i think i need to open up telnet access to the damn thing lol that way i can do stuff remotely, i take vacations but, usually they end up being a working vacation:( so remote access is something i usually have to setup

Use SSH, not telnet.  If the machine is visible on the Internet, just install openssh-server and make sure port 22 isn't closed by your firewall rules.

If the server is behind a firewall, and you have a Linux machine at your end, you might want to look into using [OpenVPN]("http://openvpn.net") to set up a full-time tunnel between them.  If you set up the firewalled machine as a client using the "remote" directive in OpenVPN, it will connect through the firewall back to you.  I recommend using a [static-key configuration]("http://openvpn.net/index.php/open-source/documentation/miscellaneous/78-static-key-mini-howto.html") as it's the simplest one to set up.

You're welcome, by the way!

---

