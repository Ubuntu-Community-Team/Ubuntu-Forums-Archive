---
title: "Any recommendations for: Ubuntu Server + NAS + GUI?"
date: 2011-06-02
forum: General Help
---

### Post by CyborgNinja111 on 2011-06-02
I've awakened from the dark-side of the force and converted to Ubuntu (thank you). 

What configuration would you guys recommend for setting up and running a general NAS using the latest version of Ubuntu Server? I have an older Xeon Poweredge server and would like to provision it as a very general, very basic file/storage server. 

My goal is just to get 'green' as fast as possible and continue on with my work and focus on productivity for my job and family. Presently, I do not have a nice block of time that I'd normally would just love to dedicate into learning CLI in depth and with full confidence before deploying the server. So its not laziness so much as it is a necessity for me. 

The server will be (Private/SOHO) LAN only with no connection whatsoever to the cloud (either directly or indirectly). I will be taking advantage of the disk array on the server and using both RAID 0 and 1. Also, I would love to use the system in a 'headless' config and remote access into it via a windows and ubuntu workstation. Any suggestions along these lines is appreciated!

I'd like the Ubuntu Server config to be as 'lightweight' and as simple to execute as possible. Again, just a simple dedicated storage system and not necessarily a mail, dns, firewall etc. server appliance. 

And although I know its not typically recommended (for security purposes) I'd like to possibly use a GUI as I am a very visual person. I am new to Ubuntu (a Windows convert) and learning CLI on other versions of Ubuntu. In the meantime I'd just like to get the server up and running kicking files back and forth to my windows and ubuntu workstation as fast as possible. All without having to crash course into the serious depths of CLI at this time.  

 Given my preference for a GUI, I know many of you would recommend just installing a desktop version of Ubuntu for this purpose. However, before I go down that path I thought I'd just see what you guys had to say about the advantages of using an alternative configuration using Ubuntu Server Edition.

Your thoughts?

---

### Post by jamesisin on 2011-06-02
Your situation sounds similar enough to mine.  I have an old server running 9.10 Desktop (which new needs rebuilding since 9 is no longer getting updates).  I chose the Desktop version because some operations are simply simpler using a GUI and there is no other setup required this way.  I recommend using 10.04 since it's an LTS release (5 years of updates as opposed to 2 years).

Now that the server is configured I rarely sign into it at the console.  I can use rsync through ssh to move files onto that machine.  I can log into that machine from any machine on my network (virtual or otherwise) using ssh and make most changes easily enough (moving files or running a backup script for instance).

From Ubuntu (or any unix-like operating system) your terminal is all you need to access the server.  From Windows I use Cygwin which allows me to run BASH in a Windows command line.

My server is connected to my regular network so it is connected to the Internet in this way, but I also have it connected to its own router so that I can have a dedicated wireless network for serving FLAC files to my hi-fi system (any machine connected to that wi-fi connection currently has no Internet access though I intend to setup that server as a proxy server to give my hi-fi machine Inernet access through the server).

The server has four 1.5 TB drives (two mirrored for backups).  I chose to not use a RAID setup.  You can read about my backups here:

[http://jamesisin.com/a_high-tech_blech/index.php/2010/08/backup-script-a-love-story/](http://jamesisin.com/a_high-tech_blech/index.php/2010/08/backup-script-a-love-story/)

I will eventually write an article on moving files using rsync.  Let me know if I should bump that up on my priority list.

Hope that helps.

---

### Post by SteveHillier on 2011-06-16
Hi Cyborgninja,
I am joining your thread because I am currently trying to configure Ubuntu as a file / NAS type server.
Just for starters I understand why you might want to use a GUI, it just makes life easier when you are used to it but having said that many of the things you might want to do to set your server up will be dealing with config files directly.  Ok, you can use a graphical editor rather than VI (which I still find a bit cranky).
Once you know where these reside and what changes you need to make the server install becomes less daunting.
I set up a test bed late this afternoon and have yet to do the final config, but for file server purposes most of what you will want to do will be in the samba config file /etc/samba/smb.conf.  There is plenty of help on this forum on Samba if you need it.
In the server install you can select which features you want installed.  I have installed mine at present as a LAMP server with Samba.  I will probably want ftp at some time.
I think what I shall do is post to this thread as I proceed.
Hope this starts to be of help to you.

[EDIT] Try looking at this thread - you may find it useful.  [http://ubuntuforums.org/showthread.php?t=1700919]("http://ubuntuforums.org/showthread.php?t=1700919")

---

### Post by SteveHillier on 2011-06-17
A follow up to my last post.
When we set up the machine yesterday we set it up with two hard disks.  
On disk we partitioned with / and /swap partitions.  The second disk we set up with a single paritions /data.  We could easily have done this on a mirrored disk as you can mirror during the partition phase.
Today we edited our smb.conf and added in the shares area the following

[data]
path = /data
guest ok = yes
browseable = yes

Then we ran ```
sudo smbd restart
``` to restart the samba server

On the windows machine we went to map a network drive.  In the path name we entered \\ubuntubox\data and mapped it to drive z:.

Drive now accessible.

Depending how you want to use the NAS drives you might need to change the samba path directives to point to other areas / partitions on the disk.  you might want to use user directives if you want to restrict shares to particular users.

Hope this helps you a bit.
Steve

---

### Post by Roasted on 2011-06-17
I just set up samba with a simple gui tool. It can be found via apt get @ sudo apt-get install system-config-samba or through searching "samba" in the software center.

It allows you to add samba users, shares, basic permissions, etc. Once done, you're in good shape. I used it in conjunction with a 2x500gb software MDADM raid setup using a mirror. It runs great and I have zero issues with it. While I do have quite a bit of samba experience, it was still pretty painless to set up. No complaints there.

---

