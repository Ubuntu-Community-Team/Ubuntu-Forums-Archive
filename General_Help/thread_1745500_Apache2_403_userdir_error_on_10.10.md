---
title: "Apache2 403 userdir error on 10.10"
date: 2011-05-01
forum: General Help
---

### Post by deadtom on 2011-05-01
I upgraded to 10.10 and now none of my userdirs are accessible.

The error log shows this error:

*(13)Permission denied: access to /~<user> denied*

I've tried chmoding to 711, 755 and 777, setting the group and/or owner to www-data and nothing works.

Nothing has changed in my file permissions, ownership or apache2.conf from before the upgrade so I don't understand what's going on here.

I've been messing with this for two days, found lots of people complaining of this issue but the only ones that were solved were done by setting folder permissions or ownership.

My userdir.conf:
```

<IfModule mod_userdir.c>
        UserDir public_html
        UserDir disabled root

        <Directory /home/*/public_html>
#                AllowOverride FileInfo AuthConfig Limit Indexes
                AllowOverride None
                Options MultiViews Indexes SymLinksIfOwnerMatch IncludesNoExec
                <Limit GET POST OPTIONS>
                        Order allow,deny
                        Allow from all
                </Limit>
                <LimitExcept GET POST OPTIONS>
                        Order deny,allow
                        Deny from all
                </LimitExcept>
        </Directory>
</IfModule>

```Any help is greatly appreciated.

---

### Post by Doug S on 2011-05-01
I have also seen many postings about permissions and such, and don't fully understand why so many have so much trouble. My public_html is working fine, and I don't have any special ownership. I tried to go the other way and create the error you are seeing. Since your userdir.conf is slightly different than the default (AllowOveride None), I tried it. It worked as expected and also enabled unrestricted access to my .htaccess protected folder, as expected with the AllowOveride directive. I disabled the userdir mod with "sudo a2dismod userdir" just to see the error resulting message, which was different, so I re-enabled the mod with "sudo a2enmod userdir". I changed the permissions of my public_html directory from 755 to 700, and then got the error message you listed. In an attempt to try to actually help, all I can think of is to list my permissions and such below:```
drwxr-xr-x 18 doug doug     4096 2011-04-12 15:15 public_html
```and then the index.html file within:```
-rw-r--r-- 1 doug doug 5722 2011-04-12 15:19 index.html
```

---

### Post by Doug S on 2011-05-01
Actually, where my permissions might differ from many others is for my home directory itself, where I have it set to 755 (and before everyone writes back saying that is bad, please know that I am the only one with access to this server). I changed it to 700 and also got the access error message.
I will think about this some more, because in the future I would like to be able to restrict access to my home directory but allow apache access to my public_html stuff.

---

### Post by deadtom on 2011-05-01
Thanks for your response Doug, I do appreciate it.

I hadn't considered disabling and re-enabling the mod using a2dimod and a2enmod so I did that just to try it out. It claimed to have disabled and re-enabled it and I restarted apache, no good.

Also matched my permissions to yours and still not working.

This is quite perplexing.

---

### Post by Doug S on 2011-05-02
Yes, it is perplexing.
The only other things I can think to mention are: My apache2.conf file is original; My default file has only the "AllowOverride All" mod to allow use of .htaccess; I am running 10.10 server editiion, not "kubuntu".

---

### Post by deadtom on 2011-05-02
If I remove the allowoverride, it gives errors about not being able to read the .htaccess file. I don't want access to those anyway. Just for testing purposes I did enable that and make an htaccess file but it didn't help.

The only difference with kubuntu is the kde interface. Like I said though, something got changed in the upgrade from 9.10 to 10.10, I just don't know what.

---

### Post by dragonfly41 on 2011-05-02
Same 403 error solved here ..

[http://ubuntuforums.org/showthread.php?t=763919](http://ubuntuforums.org/showthread.php?t=763919)

---

### Post by deadtom on 2011-05-02
> **dragonfly41 said:**
> Same 403 error solved here ..

[http://ubuntuforums.org/showthread.php?t=763919](http://ubuntuforums.org/showthread.php?t=763919)

Thanks Dragonfly41 but that was not the same issue. I did have the site folder set to all the right permissions and at one point I had it wide open, world writeable and it still could not be accessed.

I did figure out what the issue was though. Every folder in the path to the site folder has to be set to o+x. I discovered this by running a *namei -m* on the index.html file in my public_html folder and saw that my home folder was the only on in the path not set to o+x. I made that change and was then able to bring up my site.

I checked the permissions on all of the other user's home folders and they were all the same, had to change them all. Those folders were set to o-x in 9.10 and things worked fine so this must be a security change in 10.10. Some notice about that would have been nice.

Again, just to be clear, every folder in the path to the site has to be set to o+x.

---

### Post by dragonfly41 on 2011-05-02
I suggest now mark the thread as SOLVED

---

