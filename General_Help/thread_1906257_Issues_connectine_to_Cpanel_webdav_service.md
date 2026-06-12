---
title: "Issues connectine to Cpanel webdav service"
date: 2012-01-08
forum: General Help
---

### Post by lostnode on 2012-01-08
Hello there, not sure if I am posting this in the right place or not.

I am trying to connect to my cpanel server via webdav.  It works fine on windows platform using netdrive, and I am trying to set up my linux laptop to do the same.

I have done the "file -> connect to server" approach using the correct server and port (2077 for http, 2078 for https) and it saying "Connecting..." but it never actually connects and I am wondering is I am missing a package or something.  I cannot seem to get it work at all.  Any ideas?

I am using Ubuntu 11.10.

---

### Post by lostnode on 2012-01-09
Is there another way to connect to a webdav server?  This is quite urgent and I would like to use my linux laptop as apposed to my windows laptop, as windows has a tendency to crash half way through anything causing more downtime than progress. 

Has anyone ever tried to connect to a Cpanel web drive via linux and succeeded?  Has anyone had the same issue where it sits there and says "Connecting...."  Any help would be appreciated.

Also a quick note, this seems to be an issue connecting to CPanel only, I connected to my CloudMe drive with absolutely no issue.

---

### Post by lostnode on 2012-01-09
Ok, found a solution, which requires a bit of work of course.

1. Install davfs2 ->  sudo apt-get install davfs2
2. Create where you'd like to mount it ->  sudo mkdir /mnt/webdrive******
3. Mount it -> sudo mount -t davfs [http://cpanelserver.com:2077](http://cpanelserver.com:2077) /mnt/webdrive
4. Enter username and password.

Voila you are connected to the cpanel server, so it seems to be an issue with Ubuntu and its ability to connect to cpanel via the "file -> connect to server..." method, which after a bit of research, has been an issue for years that has never been fixed. (articles dating back to 2007).  You'd think they'd have fixed it by now.  But atleast I have my work around.
*[I]*****[/I]

---

