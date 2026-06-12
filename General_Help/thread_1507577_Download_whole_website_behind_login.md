---
title: "Download whole website behind login"
date: 2010-06-11
forum: General Help
---

### Post by nonewforth on 2010-06-11
I'd like to download a whole website for offline reading, I know wget does this, but how would it work with a site that needs login to view content? Of course I've got the password to login, I just don't know how to let wget know that.

Thanks in advance.

---

### Post by dcstar on 2010-06-12
> **nonewforth said:**
> I'd like to download a whole website for offline reading, I know wget does this, but how would it work with a site that needs login to view content? Of course I've got the password to login, I just don't know how to let wget know that.

Thanks in advance.

Try reading the man page, it is spelt out there:

```
man wget
```

---

### Post by nonewforth on 2010-06-12
> **dcstar said:**
> Try reading the man page, it is spelt out there:

```
man wget
```

Of course I've seen the man page, but I'm new to this and a little overwhelmed by the number of possible arguments. If anyone knows if what I'm asking for is possible, let me know. Thanks.

---

### Post by mr clark25 on 2010-06-12
looked through the man page and found this:
```

 --user=user
       --password=password
           Specify the username user and password password for both FTP and
           HTTP file retrieval.  These parameters can be overridden using the
           --ftp-user and --ftp-password options for FTP connections and the
           --http-user and --http-password options for HTTP connections.

```

you would use it like this:
```

wget --user=[username] --password=[password] http://website.com/path/to/file

```

replace [username] with your username, [password] with your password, and website.com/path/to/file with the complete url to the website you wish to download.


if you want me to, i can make a script that will ask you where you want to place the downloaded file, what your username is and what your password is, and then get the website.

just try not to violate any copyrights.

---

### Post by nonewforth on 2010-06-16
> **mr clark25 said:**
> looked through the man page and found this:
```

 --user=user
       --password=password
           Specify the username user and password password for both FTP and
           HTTP file retrieval.  These parameters can be overridden using the
           --ftp-user and --ftp-password options for FTP connections and the
           --http-user and --http-password options for HTTP connections.

```

you would use it like this:
```

wget --user=[username] --password=[password] http://website.com/path/to/file

```

replace [username] with your username, [password] with your password, and website.com/path/to/file with the complete url to the website you wish to download.


if you want me to, i can make a script that will ask you where you want to place the downloaded file, what your username is and what your password is, and then get the website.

just try not to violate any copyrights.

Thanks mr clark25, that would be excellent if you make that script. Sorry for the late reply. There's no problem with copyright, I'm already a paying member of the site, i'd like to view articles when I don't have internet access. 

Thanks again.

---

