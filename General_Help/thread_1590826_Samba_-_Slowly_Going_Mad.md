---
title: "Samba - Slowly Going Mad"
date: 2010-10-08
forum: General Help
---

### Post by Quarkrad on 2010-10-08
Two 10.04 machines on home network - just want to share files on one of the machines.  Not sure how many times I have installed and deleted Samba on both machines (via Synaptic) but it not proving easy.  Most threads/googles are about Ubuntu to Windows or over remotes networks  - so far I've failed over home (same room) connection.  When I get it 'almost working' I keep getting a window popping up asking me for a password but I never create a password.  I do not need a password between 2 of my own machines sitting in the same room.  How do you file share (easily?) between two Ubuntu machines without having to use a password?

---

### Post by luvshines on 2010-10-08
Maybe this is what you need:
[http://ubuntu.swerdna.org/ubulanprimer.html#firewall](http://ubuntu.swerdna.org/ubulanprimer.html#firewall)

Believe me, it's pretty easy. Just follow the steps. See the Usershares settings

---

### Post by Morbius1 on 2010-10-08
Why not post the output of the following commands on one of your machines so we can see what you've done:
```
net usershare info
```
```
testparm -s
```
If you created a guest share and you are relentlessly asked for a password it may not be a Samba issue but a Linux file permissions issue.

---

### Post by Quarkrad on 2010-10-08
I think I am MAD now!  I have installed Samba via Synaptic and restarted the PC because although Synaptic is green against Samba the is no Samba folder in /etc/   So, on rebooting I still have no /etc/samba folder although Synaptic is telling me it is installed (green) - also, Applications/Ubuntu Software Centre - if I type Samba I see a nice green tick against Samba  SMB/CIFS file, Print, and login server for Unix.

---

### Post by luvshines on 2010-10-08
Well you can check if it's installed using:
```
dpkg -l | grep -i samba
```

If it is, check what all it provides
```
dpkg -L <package listed by above cmd>
```

Also, if service is running:
```
ps aux | grep smb
```

---

### Post by Quarkrad on 2010-10-08
I probably should stop messing as I am a newbie but as there is no /etc/samba folder (and obviously no samba config file) I thought I would **sudo apt-get install samba** in terminal. Everything appears to have gone OK but I still have no config file because there is no /etc/samba folder.  I'm a bit lost.

---

### Post by luvshines on 2010-10-08
The commands which I mentioned will not change/ruin anything.
They will just list things and are very safe.
Rest assured they won't add to your madness ;)

---

### Post by Quarkrad on 2010-10-08
Thanks for your help.  Here is the output from terminal

**dpkg -l | grep -i samba**

rc  gadmin-samba                          0.2.8-1                                               GTK+ configuration tool for samba
ii  libwbclient0                          2:3.4.7~dfsg-1ubuntu3.2                               Samba winbind client library
ii  python-samba                          4.0.0~alpha8+git20090912-1                            Python bindings for Samba
ii  python-smbc                           1.0.6-0ubuntu3                                        Python bindings for Samba clients (libsmbcli
ii  samba                                 2:3.4.7~dfsg-1ubuntu3.2                               SMB/CIFS file, print, and login server for U
ii  samba-common                          2:3.4.7~dfsg-1ubuntu3.2                               common files used by both the Samba server a
ii  samba-common-bin                      2:3.4.7~dfsg-1ubuntu3.2                               common files used by both the Samba server a
ii  samba-ldb-tools                       4.0.0~alpha8+git20090912-1                            LDAP-like embedded database - tools
ii  samba4-common-bin                     4.0.0~alpha8+git20090912-1                            Samba 4 common files used by both the server
ii  smbfs                                 2:3.4.7~dfsg-1ubuntu3.2                               Samba file system utilities
rc  system-config-samba                   1.2.63-0ubuntu4                                       GUI for managing samba shares and users
rc  winbind                               2:3.4.7~dfsg-1ubuntu3.2                               Samba nameservice integration server

**dpkg -L <package listed by above cmd>**
Sorry - I didn't understand what to do

**ps -aux | grep smb**

Warning: bad ps syntax, perhaps a bogus '-'? See [http://procps.sf.net/faq.html](http://procps.sf.net/faq.html)
liz       1723  0.0  0.0   3328   804 pts/0    S+   17:29   0:00 grep --color=auto smb

(note - liz is user name)

---

### Post by luvshines on 2010-10-08
Oh!! A correction, **ps aux | grep smb** (Corrected this in original post as well)

Neways, see what:
```
dpkg -L samba-common
```

---

### Post by Quarkrad on 2010-10-08
Output from terminal:-

liz@lizubuntu:~$ dpkg -L samba
/.
/usr
/usr/bin
/usr/bin/eventlogadm
/usr/bin/smbstatus.samba3
/usr/bin/smbcontrol
/usr/bin/profiles
/usr/bin/tdbbackup
/usr/bin/pdbedit
/usr/sbin
/usr/sbin/smbd
/usr/sbin/nmbd
/usr/sbin/mksmbpasswd
/usr/share
/usr/share/apport
/usr/share/apport/package-hooks
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/smbstatus.samba3.1.gz
/usr/share/man/man1/smbcontrol.1.gz
/usr/share/man/man1/profiles.1.gz
/usr/share/man/man8
/usr/share/man/man8/smbd.8.gz
/usr/share/man/man8/mksmbpasswd.8.gz
/usr/share/man/man8/tdbbackup.8.gz
/usr/share/man/man8/eventlogadm.8.gz
/usr/share/man/man8/nmbd.8.gz
/usr/share/man/man8/pdbedit.8.gz
/usr/share/doc
/usr/share/doc/samba
/usr/share/doc/samba/diagnosis.html
/usr/share/doc/samba/README.Debian
/usr/share/doc/samba/copyright
/usr/share/doc/samba/NEWS.Debian.gz
/usr/share/doc/samba/README.build.gz
/usr/share/doc/samba/changelog.Debian.gz
/usr/share/lintian
/usr/share/lintian/overrides
/usr/share/lintian/overrides/samba
/usr/lib
/usr/lib/samba
/usr/lib/samba/vfs
/usr/lib/samba/vfs/recycle.so
/usr/lib/samba/vfs/audit.so
/usr/lib/samba/vfs/extd_audit.so
/usr/lib/samba/vfs/full_audit.so
/usr/lib/samba/vfs/netatalk.so
/usr/lib/samba/vfs/fake_perms.so
/usr/lib/samba/vfs/default_quota.so
/usr/lib/samba/vfs/readonly.so
/usr/lib/samba/vfs/cap.so
/usr/lib/samba/vfs/expand_msdfs.so
/usr/lib/samba/vfs/shadow_copy.so
/usr/lib/samba/vfs/shadow_copy2.so
/usr/lib/samba/vfs/xattr_tdb.so
/usr/lib/samba/vfs/streams_xattr.so
/usr/lib/samba/vfs/streams_depot.so
/usr/lib/samba/vfs/readahead.so
/usr/lib/samba/vfs/fileid.so
/usr/lib/samba/vfs/preopen.so
/usr/lib/samba/vfs/syncops.so
/usr/lib/samba/vfs/acl_xattr.so
/usr/lib/samba/vfs/acl_tdb.so
/usr/lib/samba/vfs/smb_traffic_analyzer.so
/usr/lib/samba/vfs/dirsort.so
/var
/var/lib
/var/lib/samba
/var/lib/samba/printers
/var/lib/samba/printers/COLOR
/var/lib/samba/printers/IA64
/var/lib/samba/printers/W32ALPHA
/var/lib/samba/printers/W32MIPS
/var/lib/samba/printers/W32PPC
/var/lib/samba/printers/W32X86
/var/lib/samba/printers/WIN40
/var/lib/samba/printers/x64
/var/spool
/var/spool/samba
/etc
/etc/ufw
/etc/ufw/applications.d
/etc/ufw/applications.d/samba
/etc/logrotate.d
/etc/logrotate.d/samba
/etc/init
/etc/init/smbd.conf
/etc/init/nmbd.conf
/etc/init.d
/etc/cron.daily
/etc/cron.daily/samba
/etc/init.d/smbd
/etc/init.d/nmbd

---

### Post by luvshines on 2010-10-08
Can you check this for samba-common ?

---

### Post by Quarkrad on 2010-10-08
Is this what you mean/require:-

liz@lizubuntu:~$ dpkg -L samba-common
/.
/etc
/etc/samba
/etc/samba/gdbcommands
/etc/dhcp3
/etc/dhcp3/dhclient-enter-hooks.d
/etc/dhcp3/dhclient-enter-hooks.d/samba
/etc/pam.d
/etc/pam.d/samba
/var
/var/cache
/var/cache/samba
/var/lib
/var/log
/var/log/samba
/usr
/usr/share
/usr/share/samba
/usr/share/samba/lowcase.dat
/usr/share/samba/panic-action
/usr/share/samba/smb.conf
/usr/share/samba/smb.conf.dapper
/usr/share/samba/smb.conf.etch
/usr/share/samba/smb.conf.gutsy
/usr/share/samba/upcase.dat
/usr/share/samba/valid.dat
/usr/share/doc
/usr/share/doc/samba-common
/usr/share/doc/samba-common/Roadmap
/usr/share/doc/samba-common/changelog.Debian.gz
/usr/share/doc/samba-common/copyright
/usr/share/doc/samba-common/NEWS.Debian.gz
/usr/share/doc/samba-common/README.gz
/usr/share/doc/samba-common/WHATSNEW.txt.gz
/usr/share/doc/samba-common/README.build.gz

---

### Post by luvshines on 2010-10-08
Yeah. Since this says that /etc/samba directory is being created, it should be there :) [unless you accidentally deleted it]
Also, a sample smb.conf file in /usr/share/samba/smb.conf which you can copy in /etc/samba/ and begin configuration.

If you follow the link which I referred, usershares are very easy to configure and you would actually avoid all smb.conf complications

Since samba package provide /etc/init.d/smbd , the service start/stop file should also be there.

---

### Post by Quarkrad on 2010-10-08
I created a samba folder in /etc/ and copied the config file from /usr/...  into it.  Via gknautilus I go to the file I want to share and I get a right-click Sharing Options.  I choose to share this folder and allow others to create/delete files  but when I click Create Share I get an error - 

Samba's testparm returned error 1: Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
ERROR: cache directory /var/cache/samba does not exist

This samba is not straight forward - why do I have so many things missing when samba was installed via Synaptic?  (note- I would class myself as a newbie although I have been using Ubuntu since 8.x  I thought Synaptic loaded all the relevant packages/files/install scripts etc).

---

### Post by Morbius1 on 2010-10-08
Excuse the interruption but I think we may have a problem:
> ii  samba-common-bin                      2:3.4.7~dfsg-1ubuntu3.2                                common files used by both the Samba server a
ii  samba4-common-bin                     4.0.0~alpha8+git20090912-1                             Samba 4 common files used by both the serverIt appears you have a partial combination of Samba3 and Samba4 installed.

You need to get rid of the Samba4 stuff. I don't know if that will be enough but try that first.

---

### Post by Quarkrad on 2010-10-08
Unfortunately I have to go out now - being told off for spending too much time on PC.  Thank you both for your help.  There was a samba4 entry in Synaptic and I deleted it.  When I try to share a folder now (with others able to create/delete) I get the error:

'net usershare' returned error 255: net usershare add: cannot convert name "Everyone" to a SID. The connection was refused. Maybe smbd is not running.

---

### Post by Morbius1 on 2010-10-08
When you get back run the following command again to see if you are error free and so we can see if you have the default smb.conf set up:
```
testparm -s
```If it's error free then check the following for the "cannot convert name "Everyone" to a SID" error:
[COLOR=Blue]EDIT: First thing is to check what the error message suggested - see if smbd is running:[/COLOR]
```
 sudo service smbd status
```If it's not running then start it:
```
 sudo service smbd start
```If that doesn't fix it then check the permissions of the following file:
```
ls -dl /var/lib/samba/usershares 
```It should come back with this:
> drwxrwx--T 2 root sambashare 4096 If it does then there is a very dirty workaround for this problem:
Edit smb.conf as root and add the following line to the [global] section:
```
security = share
```This was a very old bug that was fixed long ago so I'm not sure how it got into 10.04.

---

### Post by luvshines on 2010-10-08
> ```
ls -dl /var/lib/samba/usershares 
```It should come back with this:
If it does then there is a very dirty workaround for this problem:
Edit smb.conf as root and add the following line to the [global] section:
```
security = share
```This was a very old bug that was fixed long ago so I'm not sure how it got into 10.04.

@ Morbius1
Glad that you interrupted :D and made Quarkrad remove Samba4 stuff, I totally forgot that when dpkg -l output was posted.

For this particular defect, I saw some other threads mentioning it and they were not able to resolve.
Since I was not able to recreate it, so don't have any knowledge of it.
Could you please give me some pointers on the same, I would like to learn. Maybe some links to actual problem and solutions, PLZ... **Hope I am not asking too much**
How come SID error coming into picture ?

---

### Post by Morbius1 on 2010-10-08
luvshines,

I'm glad you posted. I forgot the obvious. You will also get that error if smbd is not running which is exactly what the error message implied:
> The connection was refused. Maybe smbd is not running.     I'll update my last post to include a start smbd command.

I will try to find the bug reports on this. It goes back to 2008 or so. I keep notes because I'm getting old an feeble minded but I tend to keep the solution not where I got it. :wink:

---

### Post by Quarkrad on 2010-10-09
wow - virtually there.  You were right - I needed to add the security = share to the global section - I suddenly got the two little arrows appear on the Shared Folder.  My only issue now is that on my remote PC (other side if the room) when I go Places/Network and navigate to the Shared Folder when I double clip I get a window pop up asking me for my password.

As these are both my PCs in the same room I would rather not have to keep putting in a password.  Is there as way **not** to have this window come up - why does it ask me for my password when I have never entered a password during set up? The odd thing to me is - what is this password, I have no idea, it certainly is not the users' IDs, I've tried them both.

---

### Post by Morbius1 on 2010-10-09
The password prompt will occur under 2 conditions relavent to a Linux to Linux environment:

(1) You haven't made your shares guest accessible. You really need to provide us with the output of the following commands so we can help you better:
```
net usershare info
``````
testparm -s
```(2) The linux permissions of the folder you are trying to share does not have the right settings for "others" to access the folder. Nautilus-shares will modify permissions automatically unless you are trying to share an NTFS or FAT32 partition.

If you give us the info requested in (1) above we can be more specific in our help.

---

### Post by Quarkrad on 2010-10-09
Very sorry - the shared folder sits on a NTFS partition.  The output of net usershare info was:

net usershare info
[home_files]
path=/media/Home_Files
comment=
usershare_acl=Everyone:F,
guest_ok=n


I guess now I've told you the shared Folder sits on a NTFS partition things are a little different - apologies.  Is it possible for me to access my other PC without having to go through the password step?  I am intrigued what the actual password samba is asking me for actually is though.

---

### Post by Morbius1 on 2010-10-09
Accessing a remote share is a two step process. Samba determines who ***may*** access a share but Linux itself determines who ***can*** access the target folder through file/folder permissions. The two need to be in sync. Nautilus-shares will automatically modify linux permissions on linux filesystems so they are in sync but linux can't modify permissions on a Windows filesystem outside of a mount or in fstab.

Sorry, got a little long-winded there. One way to fix this is to add a line to your smb.conf file:

Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Add the following line to the [COLOR=Blue][global][/COLOR] section of smb.conf:
```
force user = liz
```Save the file, exit gedit, and back in the terminal restart smbd:
```
sudo service smbd restart
```

---

### Post by Quarkrad on 2010-10-09
Sorry - I have not given the complete picture,  I am learning a lot so it is much appreciated.  The shared folder is on my wife's machine - this is the one we have been doing all the work on - as per previous posts her user name is **liz**.  I sit at my machine and want to access files that are on her machine - my user name is **dad**.  Will this change your last post? I assume the liz pc has to allow a use called dad the access (read/write) to the shared folder.

note.  some time ago I changed the ownership of the NTFS partition from root to liz so my wife could access the drive without any issues.

---

### Post by Morbius1 on 2010-10-09
Well, as it turns out I made a mistake in reading your output:
> net usershare info
[home_files]
path=/media/Home_Files
comment=
usershare_acl=Everyone:F,
[COLOR=Blue]guest_ok=n[/COLOR]It's asking for a password because you told it to ask for a password. Go back into nautilus and and select "Guest Access" so that will remove the need for a password.

If /media/Home_Files points to an NTFS partition then you still need to make sure that the permissions are set correctly  for "Others" to access the folder. Since you did this:
> note.  some time ago I changed the ownership of the NTFS partition from  root to liz so my wife could access the drive without any issues.     
You may have already changed permissions - I don't know.

To answer you original question, the "force user" is applied to the smb.conf file on the machine that has the folder you are sharing. If /media/Home_FIles exists on liz's machine then it's force user = liz.

---

### Post by HermanAB on 2010-10-09
How do you share files easy between two machines? 

You can use netcat:
On the server:
$ echo Hello | nc -l -p 5000

On the client:
$ echo Aloha | nc server.ip.add.ress 5000

Whatever you type on the keyboard of one terminal will be echoed on the other terminal.

You can also use netcat to copy a file over the network

---

### Post by Quarkrad on 2010-10-09
90% there - thank so much.   I allowed Guest Access via nautilus and it worked perfectly.  I could access the followed and files on my others PC (liz) from my PC.   However, when I rebooted liz it did not work* - there are no files in 'windows shares on liz'.  Is this because I have configured the liz PC to boot without a password?  (As there only two of us in the house it is just quicker to boot without the password).  Does samba/shared folder need the user to have logged on?  

* I notice that when the PC boots nautilus does not show the two arrows on the shared folder. However, if I gksudo nautilus and navigate to he shared folder it does have two arrows on it.

---

### Post by luvshines on 2010-10-09
@Quarkrad

I had similar problem when I shared it through gksudo.
Try this, instead of opening and sharing the folder via gksudo ie as root share them as liz user itself, ie open nautilus without gksudo

It may complain while sharing that user doesn't have permission on /var/lib/samba
This error is due to /var/lib/samba/usershares being owned by root user and sambashare group

I resolved it by adding my user to 'sambashare' group:
```
sudo usermod -a -G sambashare liz
```

This way it should sustain rebooting

---

### Post by Morbius1 on 2010-10-09
>   However, when I rebooted liz it did not work* - there are no files in 'windows shares on liz'I'm unfamiliar with Nautilus displaying anything like "Windows shares 0n ..." If you mean that from your machine there are no shares visible on Liz's  machine then it's likely that nmbd is not running on liz's machine.

```
sudo service nmbd status
```If it's not running then start it:
```
sudo service nmbd start
```

---

### Post by Quarkrad on 2010-10-10
Luvshines - Morbius1.   Success, thank you very much for all your help and patience guiding me through - much appreciated.

---

### Post by luvshines on 2010-10-10
Feels gud to know that you finally achieved what you wanted.

As to your last query, after you were 90% there ;), can you please share how you resolved it so that others can benefit if they reach here.

**PS: Don't forget to mark this SOLVED**

---

### Post by Quarkrad on 2010-10-10
Actually I did not need anything after my 90% position.  Even though I had rebooted and I was at 90% - for some reason when I tried it this morning it all worked.  I have rebooted both machines a number of times now and it is sable.  Once again - thanks.

---

