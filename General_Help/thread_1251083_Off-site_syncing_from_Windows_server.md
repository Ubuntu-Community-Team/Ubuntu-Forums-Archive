---
title: "Off-site syncing from Windows server?"
date: 2009-08-27
forum: General Help
---

### Post by rmeske on 2009-08-27
I am not sure if this is the correct location to post this question, if not, please let me know where it would be most appropriate.

I am looking for the best method of syncing files across the internet from a Windows server.  All changes and updates are made on the Windows server during the day and over-night they are sent to an off-site computer running Ubuntu 8 Desktop.  Why Ubuntu Desktop?, because I originally installed it for testing our cross-browser/cross-platform applications and was to lazy to uninstall and install Ubuntu Server.

Currently the overnight syncing is done with ftp.  Why ftp?, because it was easy to get through the firewalls and NAT routers. I am running Webdrive on the Windows server to make the ftp connection and then to sync all change files.  On the Ubuntu computer I am using proftp for the ftp server.  For the most part this works fairly effectively.  The shortfall is that there seems to be a limit on file size.  Any file over 200MB  will not completely copy over the connection.  I am fairly certain it is Webdrive that has the limit.

On any particullar day, there can be just a few hundred files to several thousand files.  The average size of files is around 250KB with many in the 1MB to 2MB range.  There are occasionaly some files that can be several hundred MB.

My goal is to have the Ubuntu computer as a readonly-failover server for most of the files.  The fail-over would be a manual process. The files needing access that are being backed up are; a Subversion repository, a document management system (Knowledge Tree), a development web site and finally .

My question is, does anyone have any idea of a better approach to this.  The main hurdle is that the Windows server is where all the changes occur, so it does not look like rsync would be the best option.

Thanks in advance for your suggestions/ideas!

---

### Post by i.r.id10t on 2009-08-27
Copy over ssh using passwordless keys, or use rsync.  And yes, there is rsync for win32

---

### Post by moored99 on 2009-08-27
Sounds like a job for rsync that will run on both platforms.

[http://www.samba.org/rsync/](http://www.samba.org/rsync/)

[http://www.itefix.no/i2/node/10650](http://www.itefix.no/i2/node/10650)

Edit beat me to it.

---

### Post by moored99 on 2009-08-27
Wrong Post. Sorry.

---

### Post by rmeske on 2009-08-27
Thank you for the replies.

Has anyone used rdiff-backup?  It seems to be similar to rsync but allows the ability of keeping backups of previous changes to files so that you can revert back to an earlier copy.

Would there be any advantage long term of changing from Ubuntu Desktop to Server?  Does the server version have the same GUI interface?

---

### Post by i.r.id10t on 2009-08-27
Server does not install a gui by default.  Otherwise it is all the same.

---

