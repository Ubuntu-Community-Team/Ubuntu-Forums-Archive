---
title: "Possible? /temp/www/fake/ contents (directory) avaliable through /temp/www/"
date: 2010-12-20
forum: General Help
---

### Post by 0949er on 2010-12-20
I have a web server whos DocumentRoot is:

/tmp/www

Now, /temp/www/fake/ is a directory that contains a series of other files/folders.

What I want to do is access the files in /temp/www/fake as if they were in the root directory (/temp/www/)

For example:
[http://127.0.0.1/test.php](http://127.0.0.1/test.php)

could either be located in "/temp/www/test.php"
**-or-**
located in "/temp/www/fake/test.php"


so "http://127.0.0.1/test.php" would essentially call both directories. Is this possible? Whould I do this through apache or through the actual file system somehow? (Like some sort of symbolic link?) I would love to hear your input.

---

### Post by 0949er on 2010-12-20
any ideas?

---

### Post by efflandt on 2010-12-20
I don't think you can have your cake and eat it too.  A particular virtual host has a particular path for its document root.  And while you could symlink from the main path to other content, you would need a symlink in /tmp/www/ pointing to the specific file in /tmp/www/fake/ and have apache configured to follow symlinks.

Otherwise if you had a default index.html (or any other file with a specific name) in both directories, how would it know which one to serve?

---

### Post by 0949er on 2010-12-21
this is called ambiguity I think lol. I just dont want to look at all those fake folders. Is there a way to hide the folder? Other then adding the prefix "."?

---

### Post by CharlesA on 2010-12-21
> **0949er said:**
> this is called ambiguity I think lol. I just dont want to look at all those fake folders. Is there a way to hide the folder? Other then adding the prefix "."?

Why even bother?

You use folders to have some organization instead of throwing everything into one folder.

---

### Post by 0949er on 2010-12-22
there are select "locations" that bots willl attempt to make a connection to, i.e. "server.com/mysql/setup.php" looking for ways to backdoor a server. I have about 20 "fake" folders inside my root www directory and would like to "organize it" by placing all the folders that go "nowhere" inside one folder so I dont have to fish through them when looking for directors such as "include" or "img" that actually contain substance. you get what I am saying? I want to put all those directories in server.com/fake so they are orginized in one spot, while they are not visually in my way in the root directory. *exhale*

---

### Post by CharlesA on 2010-12-22
Are you talking about search spiders, or people trying to get into your web server?

---

### Post by 0949er on 2010-12-22
> **CharlesA said:**
> Are you talking about search spiders, or people trying to get into your web server?

not exactly sure which one it is, for example, a ip address will attempt to connect to:

/php/myadmin/setup.php
/php/MyAdmin/setup.php
/phpmyadmin/setup.php
/scripts/setup.php

which I have "created" so that they will think they have a connection, where-as its really a php script file that just logs their IP address and notifies me.

Is this not a good way to go about this? In Apache, is there a way to forward specific request to a specific location? Or perhaps a way that if a user try to navigate to a non-existent file/folder, it automatically redirects them to a specific location?

---

### Post by CharlesA on 2010-12-22
I don't think that's a search spider, judging from what they are looking for, but I'm not 100% sure.

You can password protect sensitive directories by using .htaccess.

---

