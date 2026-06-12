---
title: "&quot;Permission denied&quot;-error when accessing a subversion repository via HTTP"
date: 2009-11-25
forum: General Help
---

### Post by Jockel on 2009-11-25
Okay, I have my first real Linux installation (Ubuntu 9.10, 64 bit) running, so please have some patience with me.
I'm trying to make a Subversion repository available via HTTP, but I'm having a problem with the permissions. I tried to follow several tutorials(*) and I think I mixed them all and messed this way everything up now and I'm quite lost :-(

(*) Tutorials that I had a look at:
[http://chestofbooks.com/computers/revision-control/subversion-svn/Setting-Up-HTTP-Authentication-Serverconfig-Httpd-Authn-Basi.html](http://chestofbooks.com/computers/revision-control/subversion-svn/Setting-Up-HTTP-Authentication-Serverconfig-Httpd-Authn-Basi.html)
[https://help.ubuntu.com/community/Subversion](https://help.ubuntu.com/community/Subversion)
[http://develobert.blogspot.com/2008/02/svn-cant-open-file-format-permission.html](http://develobert.blogspot.com/2008/02/svn-cant-open-file-format-permission.html)


What I have so far:
I can access my repository via file:///usr/local/svn/repos/project.
Apache server 2.2.12 is up and running. But if I try to access the repository via [http://localhost/svn/](http://localhost/svn/) and entering my credentials (the same I use as if I would access the repository via file:///), I get the following error-message:

```
<D:error>
<C:error/>
&#8722;
<m:human-readable errcode="13">

Can't open directory '/usr/local/svn/repos': Permission denied
</m:human-readable>
</D:error>
```The mentioned directory belongs to the group "svn". As a user I tried "www-data" and also my own user "jr".

My /etc/apache2/httpd.conf looks like this:

```
<Location /svn>
DAV svn
SVNParentPath "/usr/local/svn/repos"
SVNListParentPath On
AuthType Basic
AuthName "Subversion repository"
AuthUserFile "/etc/subversion/passwd"
Require valid-user
</Location>
```Svnserve was started manually after executing ```
umask 002
``` (like described here: [http://svnbook.red-bean.com/nightly/en/svn.serverconfig.multimethod.html](http://svnbook.red-bean.com/nightly/en/svn.serverconfig.multimethod.html)).

Could someone guide me through this, which permissions have to be changed, what else I have forgot, etc. to make this work?

PS: I'm not sure, that this is the right category, but I couldn't find any obvious other one where this question belongs to. Sorry about that.

[SOLUTION]
Never mind. I found the solution, after I stumpled over another (german) forum entry ([http://forum.subversionbuch.de/viewtopic.php?t=224](http://forum.subversionbuch.de/viewtopic.php?t=224)). My "root"-directory (/usr/local/svn) didn't had the right permission. I granted only permissions to /usr/local/svn/repos which was not sufficient.

---

