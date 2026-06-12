---
title: "Change Permission on subdirectories"
date: 2012-02-22
forum: General Help
---

### Post by spidy_x5 on 2012-02-22
Hey Guys,

I installed a turnkey Joomla server in Virtualbox and am hosting a website from one of my machines.

I'm trying to make a package available from this site. I set up FTP and copied the .pkg file over, but it is being recognized as a directory and sub-directories.

I'm able to access the top directory because I ran the command below:

find /var/www/joomla/LogMeInInstaller.pkg -type f -exec chmod g+rx {} \;

however I can't see any of the sub-directories, I was wondering if someone could inform me how I can apply these same settings to all the sub directories so that I do not have to do it manually one by one.

---

### Post by roelforg on 2012-02-22
use the -r arg of chmod

---

### Post by spidy_x5 on 2012-02-22
Hey thanks Roel,

I think that is exactly what I'm looking for, however I'm not sure if you meant to add this in place of gx+r or if it goes somewhere else. When I add the -r in front or behind of gx+r it says "cannot access gx+r no such file".

If you could elaborate that would be fantastic.

Thanks,

---

### Post by roelforg on 2012-02-22
> **spidy_x5 said:**
> Hey thanks Roel,

I think that is exactly what I'm looking for, however I'm not sure if you meant to add this in place of gx+r or if it goes somewhere else. When I add the -r in front or behind of gx+r it says "cannot access gx+r no such file".

If you could elaborate that would be fantastic.

Thanks,

I just see a typo: the arg is -R (case-sensitive ya know)
Your chmod was:
```

chmod g+rx

```
should be (for subdirs):
```

chmod -R g+rx

```

---

### Post by TheFu on 2012-02-22
This is all you need
$ chmod +r /var/www/joomla/LogMeInInstaller.pkg

There's no need for a 'find' to change permissions on a single file or recursively when just 'r' (read) is involved.

Recursively, it would be
$ chmod -R  +r /var/www/joomla/LogMeInInstaller.pkg
but since the "LogMeInInstaller.pkg" is probably a single file, this probably will not have the desired effect. Rather, 
$ chmod -R  +r /var/www/joomla/
is probably what you think you want .... I'd be a little worried in doing this, but I don't know Joolma.  I'd think that Joomla has a public download directory "somewhere" where you probably want to place this file instead.

This is one of those questions where asking specifically about Joomla and making a file public will get better answers, I think.

---

### Post by spidy_x5 on 2012-02-22
That did it. A lot easier way of doing it than what I found on google.

Thanks man.

---

