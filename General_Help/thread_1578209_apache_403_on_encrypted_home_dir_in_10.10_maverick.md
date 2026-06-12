---
title: "apache 403 on encrypted home dir in 10.10 maverick meerkat"
date: 2010-09-20
forum: General Help
---

### Post by tacitdynamite on 2010-09-20
I just installed 10.10 maverick meerkat with an encrypted home dir. I'm having the same problem as ChrisEffel in  this thread: [http://ubuntuforums.org/showthread.php?t=1509379](http://ubuntuforums.org/showthread.php?t=1509379) and jmblock2 in this thread: [http://ohioloco.ubuntuforums.org/showthread.php?t=1327157](http://ohioloco.ubuntuforums.org/showthread.php?t=1327157). their solutions don't work for me. 

Basically, I downloaded a fresh install of apache and went through the steps of installing a virtual host as per [https://help.ubuntu.com/community/ApacheMySQLPHP#Virtual%20Hosts](https://help.ubuntu.com/community/ApacheMySQLPHP#Virtual%20Hosts), the ubuntu ApacheMySQLPHP guide. I followed the steps carefully. When I browse to [http://localhost/](http://localhost/) at the end of the steps I get 403 Forbidden, and ```
tail -n 1 /var/log/apache2/error.log
``` reads ```
[error] [client 127.0.0.1] (13)Permission denied: access to /favicon.ico denied
```, which reflects what's really going on here - no amount of chmodding is giving apache access to files in the home dir.

I thought maybe this was an encrypted home drive issue, as per this bug report in 10.04: [https://bugs.launchpad.net/ubuntu/+source/apache2/+bug/585212](https://bugs.launchpad.net/ubuntu/+source/apache2/+bug/585212).  but his solution, which is also ChrisEffel's solution in the thread mentioned above, ```
chmod o+x $HOME
```, does nothing for me. i've also ```
chmod 0755 public_html
```, and ~/public_html/index.html is also chmod 0755'd.

This is driving me crazy because I had it set up just fine (without home disk encryption) under 9.10 just a week ago ... any of you apache gurus have any tips?

jmblock2 said in [http://ohioloco.ubuntuforums.org/showthread.php?t=1327157](http://ohioloco.ubuntuforums.org/showthread.php?t=1327157) that "parent directory of www also needed to be set to www-data" which, since I've followed [https://help.ubuntu.com/community/ApacheMySQLPHP#Virtual%20Hosts](https://help.ubuntu.com/community/ApacheMySQLPHP#Virtual%20Hosts) (the ubuntu ApacheMySQLPHP guide) would be the parent directory of ~/public_html, namely, my home dir. do I really want to set my home dir, /home/`whoami`/, to www-data? how would I do that, anyway, with chgrp? seems sketchy.

---

### Post by robsoles on 2010-09-20
I reviewed the other threads you have linked and a notable difference  between your problem and theirs is that you are trying from an encrypted  home directory and that will take some beating - I didn't spot where  either of the other people mentioned they are working from an encrypted  home directory.

Apache2, to the best of my understanding of both httpd & 'encrypted  home dir', would have to run as you (or the user that owns the encrypted  home directory) and have your password available to it so as to decrypt  & mount your home folder and read from it when a page is requested.

To the best of my understanding your encrypted home folder can **either** only be read by you **or** can only be read by yourself and root provided you are logged in to have decrypted your home folder.

It would be better to use the default location [COLOR=Blue][COLOR=Black]/var/www/[/COLOR]'your-site'[/COLOR] with no encryption set on it.

---

### Post by tacitdynamite on 2010-09-20
Thanks for looking over the links and for your suggestions - you were totally right. I found the solution in [this thread by cozman69]("http://ubuntuforums.org/showthread.php?p=9644980"). 

Basically, this is what I did:

```

sudo mkdir /home/public_html
cd /home/public_html
sudo mkdir $USERNAME
sudo chown $USERNAME:$USERNAME $USERNAME
# copies the CONTENTS of ~/public_html to the dir we just created, following symlinks and preserving permissions
rsync -av public_html/ /home/public_html/$USERNAME/
cd ~
rm -rf public_html
# creates a symlink so that your experience will be the same
ln -s ../public_html/$USERNAME/ ./public_html

```

Then to set up apache userdir permissions: 
```

sudo vim /etc/apache2/conf.d/userdir

```
Copy and paste, save and close:
```

UserDir /home/public_html
UserDir disabled root

<Directory /home/*/public_html>
AllowOverride FileInfo AuthConfig Limit
Options Indexes SymLinksIfOwnerMatch IncludesNoExec
</Directory>

```
Then enable the userdir mod:
```

cd /etc/apache2/mods-enabled/
sudo ln -s ../mods-available/userdir.* .
sudo /etc/init.d/apache2 reload

```

Next, I created a Virtual Host for local dev that linked to the folder we created above: 
```

cd /etc/apache2/sites-available/
sudo cp default ldev
# replace /var/www with /home/public_html/$USERNAME
sudo sed -i 's|var/www|home/public_html/'$USERNAME'|g' ldev
# enable the new virtual host
cd ../sites-enabled/
sudo ln -s ../sites-available/ldev ldev
sudo a2ensite ldev
sudo /etc/init.d/apache2 restart
# make your hosts file register the ldev TLD
# first backup the hosts file
sudo cp /etc/hosts ~/.hosts.bak
# append ldev to the localhost (::1) line for webkit browsers
sudo sed -i '/::1/s|$| ldev|' /etc/hosts
# append ldev to the 127.0.0.1 line for firefox
sudo sed -i '/127.0.0.1/s|$| ldev|' /etc/hosts
# now you should be able to see index.html at ldev
# first copy a sample document 
sudo cp /var/www/index.html ~/public_html
# then open it in a browser
gnome-open http://ldev/

```

---

### Post by robsoles on 2010-09-20
Please consider using 'thread tools' in red above to mark this thread as solved.

---

### Post by james_fried on 2010-09-28
@tacitdynamite - cheers for posting this. I've just spent three hours pulling my hair out over why an imported site wouldn't work on my laptop with hosted files in my home dir. Like you no amount of chmod / chown / www-data / 777 combos would work... your post showed me the problem :: ENCRYPTION!!! (I'd completely forgotten I turned it on for this laptop install!)

just wish that apache could have given a more helpful message than the default:

```
(13)Permission denied: access to / denied
```

I might check out the work-arounds, or just go back to /var/www :D

---

### Post by tacitdynamite on 2010-09-28
Maverick Meerkat was the first time I had used the home disk encryption; before, I used the alternate install disk w/ full disk encryption, which gave me a transparent experience and let me really forget about it. When I upgrade next time, I'll definitely go back to that because now, when I have any kind of webdev problem, I think, "is this because my home disk is encrypted?" Glad this helped someone else!

---

