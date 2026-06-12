---
title: "Setting Up FTP With Permissions"
date: 2010-12-29
forum: General Help
---

### Post by NessDan on 2010-12-29
So I recently got an old computer to use as a server and I have a whole list of things I want to do on it, but I'm having difficulties.

When I installed the server, I installed AMP, FTP, Samba, CUPS, and some other items.

I made a user account called 'nessdan' which (currently!) is in these groups:
www-data adm dialout cdrom plugdev lpadmin sambashare admin

The www-data group was added because I wanted to FTP my site files into '/var/www/' . Okay, that ended up working out for me. This is where things got sticky.

I installed PHPMyAdmin and the files went to '/usr/share/phpmyadmin/' . I wanted to install a new theme so I downloaded it onto my Laptop, then logged in via FTP but couldn't transfer files into there! It turns out the folder was owned by 'root' and was in the group 'root'. The only thing I could come up with was to change that folders permissions so the owner was 'nessdan' and the group 'admin'. I was going to do that to the entire /usr/share/ folder but I didn't know whether or not I should be changing the permissions in the first place.

But the the trend continues! I have my print server setup and working but I wanted the server to hold the Windows drivers, so I went to '/var/lib/samba/' to do some work but noticed that a lot of the files' permissions were locked down to read only and the owner and group were 'root' . I ended up doing a 'chmod 775' and changing the owner and group to 'nessdan' and 'admin', respectively. Well I transfered over the files but now the service nmbd isn't working.

The good news is, I expected to mess something up along the way and had already planned on reinstalling Ubuntu Server 10.10. I've only had the server for 4 days now and I knew from the beginning I'd be wiping it clean. I want to know how to set this thing up proper and the biggest problem is getting access into folders so I can FTP into them.

My question is this: When I do wipe my PC clean and start anew, how should I go about the changes that I did before (PHPMyAdmin, Samba Driver Folder)?

---

### Post by NessDan on 2011-01-04
It's been 6 days, so bump!

---

### Post by NessDan on 2011-01-11
Another 6 days and no answer, is this a difficult question? I just want to be able to update programs by downloading them on my PC and FTPing them into the proper folders.

---

