---
title: "Cannot save image edits to NAS"
date: 2010-01-07
forum: General Help
---

### Post by MacDuff on 2010-01-07
Still cannot save Image edits to a NAS.  This problem has plagued me since Ubuntu 8.10 and it is still broken in 9.10.  Image files edited in The Gimp, Digikam and Showfoto cannot be saved to a DNS-323 Network Attached Storage.

I have posted a number of times to the forums and many suggestions have been made, none of which solved the problem.  At one time I could save images edited by the Gimp but not digiKam, but with the current updates to 9.10 I cannot save images from either of those applications.  

Appeals to digiKam received the response that the problem was fixed with the release of Version 1.0.0 but that Ubuntu has not made it available through the repositores.  My installed version is 1.0.0 but does not work and now I find that I cannot save images edited with The Gimp.

Can anyone shed any light on the state of this problem or am I the only person who is using a D-Link NAS with Ubuntu for photo storage?

---

### Post by gordintoronto on 2010-01-07
Can Nautilus copy files to the NAS?

---

### Post by Paul Stone on 2010-01-07
Maybe this will help (and then again, maybe not).


==================


[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/286828](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/286828)

==================


[INDENT]Skokie  wrote on 2008-12-02:  	  #62

Thank you to all who have taken the time to investigate! The DNS323 suffers from this server side DFS bug but it is possible to work around it!!!

Connect to the DNS using the web GUI and goto tools->system.

In this page you can save the configuration to your workstation.
After saving edit the file and add the following line under ;[ global ]
msdfs root = no

Save the file and now back in the GUI for the DNS323, upload the config you edited. The device will reset but the settings will be passed on to the samba server and all will be well in wellsville.

Thanks again![/INDENT]


==================


[INDENT]Steve French  wrote on 2009-08-05:  	  #96

Simplifying:
1) older smbfs/smbmount had a "bug": they didn't support DFS (which Windows clients do, and Linux cifs client does) which is a critical feature of the protocol in multiple server environments
2) Windows does not support Unix Extensions

Samba server introduced a bug (long since fixed) which affects clients which support BOTH

Asking the kernel cifs client to always disable DFS support (ie without a mount option) to work around a bug in one server version would make things even worse because that would hurt accessing all of the servers that have working DFS support.[/INDENT]

==================


I also see mentions on the interwebs of using nounix and/or nodfs options in your fstab file in order to workaround this bug, which apparently exists in the (old-ish) SAMBA server on your NAS.  So, if the workaround above doesn't work, I would try that.

Good luck!

---

### Post by Paul Stone on 2010-01-07
Also, this looks interesting, from the same thread.  It would be ideal if you could update the firmware in your NAS and fix it that way.

[INDENT]mipper  wrote on 2008-12-11:  	  #64

@Skokie
Thanks very much for this tip. That's sorted me out nicely.

I've contacted D-Link regarding a firmware fix for this issue and received the following reply:

"A firmware is being develop, we don't have an ETA or upgrades that it will have, i invite you to go to forums.dlink.com, you can post and get updated information by product managers on new releases."

So a genuine fix is on the way, just no idea when. Looking at the frequency with which firmware upgrades have been release in the past I'd hope it's not too long before it arrives.

Many thanks to all who responded.
[/INDENT]

---

### Post by Paul Stone on 2010-01-07
Another possibility...

[http://ubuntuforums.org/showpost.php?p=6238553&postcount=5](http://ubuntuforums.org/showpost.php?p=6238553&postcount=5)


> **cebesius said:**
> I ran into some problems connecting to my DNS-323 after upgrading (fresh install) to Ubuntu 8.10.  It's much easier to troubleshoot this type of issue using the command line.  Adapt this to suit your environment:
```
smbclient --debuglevel=1 //yourdns323/yourshare
```
If you know the IP address of your DNS-323, use it instead of its hostname, unless you know for certain that DNS will resolve its hostname to the correct IP address.
In my environment, that means I tried:
```
smbclient --debuglevel=1 //sanbox/volume_1
Enter cebesius's password: 
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.0.24]
Server not using user level security and no password supplied.
Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
tree connect failed: SUCCESS - 0
```
Ubuntu 8.10 is trying to use a (more secure) form of authentication that the DNS-323 doesn't support.  There is definitely more than one way to solve this.

One way is to hack your DNS-323 to have an updated Samba server which supports more secure types of authentication.  This would probably void your warranty, and since I'm not going to try, I won't be covering it.

Another way is to contact D-Link and complain about the Samba on the DNS-323 until they release a firmware with a better version of Samba.

Another way is to make Ubuntu authenticate with your DNS-323 using the weak lanmanager style authentication that the DNS-323 expects.  To make this work, I had to edit my samba configuration.  Open it up for editing by doing:
```
gksu gedit /etc/samba/smb.conf
```
Find the [global] section, and insert this line:
```
client lanman auth = yes
```

Now try to connect.  That solved it for me.  Hopefully it will for you too.

---

### Post by MacDuff on 2010-01-08
> **gordintoronto said:**
> Can Nautilus copy files to the NAS?

Yes, Nautilus can copy with no problem.  Open Office can save files with no problem.  Any text editor can edit and save files, but it will sometimes, (often) throw up a message telling me that it needs to re-load the file.  I tell it "Yes" and everything is OK.

Way back with Version 8.10, nothing could save to the NAS, but now it is only image files.  Things have improved but I am a photographer and editing images is a very important part of my day, so this is very frustrating.

---

### Post by MacDuff on 2010-01-08
> **Paul Stone said:**
> Maybe this will help (and then again, maybe not).

Skokie  wrote on 2008-12-02:  	  #62

Thank you to all who have taken the time to investigate! The DNS323 suffers from this server side DFS bug but it is possible to work around it!!!

Connect to the DNS using the web GUI and goto tools->system.

In this page you can save the configuration to your workstation.
After saving edit the file and add the following line under ;[ global 
msdfs root = no

Save the file and now back in the GUI for the DNS323, upload the config you edited. The device will reset but the settings will be passed on to the samba server and all will be well in wellsville. 

Call me stupid but I do not know what this refers to.
I can find "tools>system in the DNS web interface but what "workstation configuration file" must be edited and saved?  

As I mentioned in my reply to the first response.  I can connect to the NAS and I can add view, create and delete files on it.  I can edit text and OpenOffice files on it, but I cannot edit and save image files that are located on it.  

The work around I have been using is to open image files that are located on the NAS, save them locally and then copy them from the local directory to the NAS and it will over-write them with no problem.  But that is a lot of extra work. 

For some reason, SOME editors ONLY (Raw Therapee works just fine) cannot seem to be able to save an edit directly to the NAS. digiKam never could after Ubuntu Ver 8.04. At one point, using 9.10, The Gimp could for a short time but now, once again, cannot.   The only changes have been the routine Ubuntu updates.   Acting on advice from the digiKam mailing list, I downloaded a digiKam tarball and installed it but that did not solve the problem and may have been what broke the Gimp, who knows?

Quel frustration!

---

### Post by Paul Stone on 2010-01-08
Have you already tried this workaround (keeping the database file on your local hard disk)?

[http://lists.kde.org/?l=kde-bugs-dist&m=117536777106366&w=2](http://lists.kde.org/?l=kde-bugs-dist&m=117536777106366&w=2)

---

### Post by MacDuff on 2010-01-08
Yes Paul, I have been using a symlink since I first began to use Ubuntu and discovered digikam about three years ago.  I still use the symlink even though it is claimed not to be needed with digkam 1.0.0 because it seems to do the opening directory scan faster using the symlink.

As I say, digikam has no problem displaying the files and will let me edit them but will not let me save them to the source.

I keep praying that each new bug fix will solve the problem but it has been over a year now and the problem still exists.  Every few months I make a plaintive plea to see if anyone has found and fixed the problem. 

If it has not been addressed by the next release of Ubuntu (10.04) I am afraid I will have abandon Ubuntu and to return to my big investment in Photoshop on Windows. 

It will break my heart, particularly as I have convinced others to drop Windows and move to Linux.  But I have eaten crow before, I guess I can do it again.

---

### Post by jandro_s on 2010-01-10
I had the same problem of not being able to save my files from within Gimp, however adding the nodfs to the fstab where I configured the mount did the trick.

I change my fstab from:

//x.x.x.1/Servidor /home/myuser/mountdir cifs uid=myuser,workgroup=myworkgroup,credentials=/root/.smbcredentialscasa,dir_mode=0777,file_mode=0777,rw,iocharset=utf8 0 0

to:

//x.x.x.1/Servidor /home/myuser/mountdir cifs uid=myuser,workgroup=myworkgroup,credentials=/root/.smbcredentialscasa,dir_mode=0777,file_mode=0777,nodfs,rw,iocharset=utf8 0 0

Thank you everyone for the help.

Regards

---

### Post by MacDuff on 2010-01-10
> **jandro_s said:**
> I had the same problem of not being able to save my files from within Gimp, however adding the nodfs to the fstab where I configured the mount did the trick.

I change my fstab from:

//x.x.x.1/Servidor /home/myuser/mountdir cifs uid=myuser,workgroup=myworkgroup,credentials=/root/.smbcredentialscasa,dir_mode=0777,file_mode=0777,rw,iocharset=utf8 0 0

to:

//x.x.x.1/Servidor /home/myuser/mountdir cifs uid=myuser,workgroup=myworkgroup,credentials=/root/.smbcredentialscasa,dir_mode=0777,file_mode=0777,nodfs,rw,iocharset=utf8 0 0

Thank you everyone for the help.

Regards

Thanks good people.  The addition of "nodfs" to the fstab entries that mount the NAS, solved the problem.
I was sure that I tried that some time ago but it did not work so special thanks to jandro_s for including the line from his fstab entry.  I did a character by character comparison with mine and it all works now.  
Much appreciated!

---

### Post by jandro_s on 2010-01-11
Happy to hear that it helped you too.

Regards

---

### Post by Paul Stone on 2010-01-11
Awesome!!

8)

---

### Post by jqsmooth on 2010-02-07
Another thank-you. This solved my GIMP save problem to dlink 323 nas mounted via fstab.

---

