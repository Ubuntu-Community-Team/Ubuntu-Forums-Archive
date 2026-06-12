---
title: "Apache/PHP troubles after transferring development env to new workstation"
date: 2009-10-29
forum: General Help
---

### Post by ColdFFF on 2009-10-29
First off, a little bit of a backstory:


I work at developing the frontend and backend systems for a utilities supplier. The live systems are hosted offsite on a server, and all development is done and tested locally.

On my old machine, I had apache2, php5 and postgresql installed, and the two systems were run from /home/alex/code/(back/front)end

Today I was asked to switch all my work over to a new machine, so I copied over my home folder, and got to work installing.

Now, onto the issues.

It has been a long while since I last installed apache, php and *sql, so I've probably messed up with a configuration file somewhere.

1) localhost:8080 should point to /home/alex/code/backend
I have set up a virtualhost in /etc/apache2/sites-enabled/000-default as so:
```
<VirtualHost *:8080>
        DocumentRoot /home/alex/code/backend/
        <Directory "/home/alex/code/backend/">
                Options SymLinksIfOwnerMatch
                AllowOverride All
                Order deny,allow
                Allow from all
        </Directory>
        ErrorLog /var/log/apache2/error.log

    Loglevel debug
        CustomLog /var/log/apache2/access.log combined
    
</VirtualHost>
```
and added:
```
NameVirtualHost *:8080
Listen 8080
```
to /etc/apache2/ports.conf

When I try to browse to localhost:8080 I get a 403 error message - "You don't have permission to access / on this server." The error log shows
```
[error] [client 127.0.0.1] Directory index forbidden by Options directive: /home/alex/code/backend/
```

Any ideas on what I have done wrong, and how to fix this?

2) localhost:8081 should point to /home/alex/code/frontend
This one doesnt appear to be an apache error (I think). Using the same setup as above (except swapping backend to frontend, 8080 to 8081).
When I try to access the site I get "Your PHP installation does not support PostgreSQL. You need to recompile PHP using the --with-pgsql configure option." I have installed php5, php5-pgsql and postgresql (and their dependancies) via synaptic, do I need to do anything else?

---

### Post by Giblet5 on 2009-10-29
Who owns /home/alex/code/backend?

It has to be accessible by user apache...

---

### Post by ColdFFF on 2009-10-29
Output of ls -l:

> ...
lrwxrwxrwx  1 alex staff   49 2009-10-12 09:51 backend
...

How can I check if the apache user is a member of the group staff?

---

### Post by Giblet5 on 2009-10-29
> **ColdFFF said:**
> Output of ls -l:

How can I check if the apache user is a member of the group staff?

From a terminal window, ```
less /etc/group
```

Apache has the oddball user name of www-data and there will be a group called that as well.

I would add user www-data to group staff.


Easy test of permissions: ```
sudo -u www-data ls -l /home/alex/code/backend
```

---

### Post by ColdFFF on 2009-10-29
Ok, I think Ive correctly added www-data to staff:
```
sudo usermod -g staff www-data
```

less /etc/group shows:
```
staff:x:50:www-data
```

I also restarted apache just for good measure, but still no luck :(

Edit:
sudo -u www-data ls -l /home/alex/code/backend returns:
```
lrwxrwxrwx 1 alex staff 49 2009-10-12 09:51 /home/alex/code/backend
```

---

### Post by Giblet5 on 2009-10-29
> **ColdFFF said:**
> ```
lrwxrwxrwx 1 alex staff 49 2009-10-12 09:51 /home/alex/code/backend
```

/home/alex/code/backend is a link to ... something, and you displayed the mode of the link. (and it doesn't behave like a directory link would behave)

What is the ownership/mode of the real object that /home/alex/code/backend is linked to? Is that object a directory? Can www-data 'cd' to it? Can www-data read files in that directory? If not, there will be trouble.

---

### Post by ColdFFF on 2009-10-29
Sorry, I must have missed half the line with that paste :/

Yes, backend is a symlink to the name of the current branch I am working in.

Changed the branch folder so it is now accessible, all is working now :) Thanks

---

### Post by Giblet5 on 2009-10-29
> **ColdFFF said:**
> Sorry, I must have missed half the line with that paste :/

Yes, backend is a symlink to the name of the current branch I am working in.

Changed the branch folder so it is now accessible, all is working now :) Thanks

Great!

Branch folder? You're linking to a CVS or subversion branch?

Remember that every time you update, the mode/ownership of that real folder will likely revert.

Happy coding!

---

