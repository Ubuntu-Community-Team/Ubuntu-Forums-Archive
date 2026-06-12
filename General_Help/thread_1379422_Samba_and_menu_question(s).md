---
title: "Samba and menu question(s)"
date: 2010-01-12
forum: General Help
---

### Post by haemphyst on 2010-01-12
First question:  (and I will probably be directed to search for the answer, but I already have, and have not discovered an answer...)  What's the deal with Samba?  Is it broken?  I can't get my laptop to connect to a Server 2003 box, no matter what I do.  I've tried by server name (it doesn't ping it...  It does, but it tries to ping an IP outside of my network, with no response.)  I have tried connecting to the server using the server's IP address, and I can't get that to work, either.  A ping to the IP does return, as expected.

Second question:  How can I get the now static, if failed, "mappings" to the 2003 server (called fileserver) in my Places menu to go away?  (see picture...)

[http://i134.photobucket.com/albums/q91/haemphyst/menu.jpg](http://i134.photobucket.com/albums/q91/haemphyst/menu.jpg)

The top one of those says "**open 'smb://si;haemphyst@fileserver/applications/'**"
When I click this one, it will ask me for "Password required for share applications on fileserver", and I click the radio button "Remember Forever".  Approximately 15 to 20 seconds later, I receive an error notification:

**Could not open location 'smb://si;haemphyst@fileserver/applications/'**
and "**Failed to mount Windows share**"

The bottom one says "**open 'smb://si;haemphyst@192.168.1.2/applications/'**"
When I click this one, it too asks me for my password for "Password required for share applications on 192.168.1.2", which I provide, click the Remember forever button again, and INSTANTLY, I receive the same window again, but the password field is blank.

I can't seem to find ANYTHING to tell me what's wrong here!  PLEASE help!  :)

---

### Post by Puck7 on 2010-01-12
2nd problem: Open up Nautilus, and on the left part you'll see the Favorites folders, just right click and Remove.

Also make sure you have a samba password setup. If you didn't do one, you will probably not log in.
Use this to create a samba user and password
```
sudo smbpasswd -a <username>
```

---

### Post by haemphyst on 2010-01-12
OK.  Entered provided code, as I hadn't done that before.  Copy and past of results follows:

haemphyst@dell-ubuntu:~$ sudo smbpasswd -a haemphyst
[sudo] password for haemphyst: 
New SMB password:
Retype new SMB password:
Unable to create directory /var/run/samba for file mutex.tdb. Error was No such file or directory
tdbsam_open: Converting version 0.0 database to version 4.0.
tdbsam_convert_backup: updated /var/lib/samba/passdb.tdb file.
account_policy_get: tdb_fetch_uint32 failed for field 1 (min password length), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 2 (password history), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 3 (user must logon to change password), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 4 (maximum password age), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 5 (minimum password age), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 6 (lockout duration), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 7 (reset count minutes), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 8 (bad lockout attempt), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 9 (disconnect time), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 10 (refuse machine password change), returning 0
Added user haemphyst.
haemphyst@dell-ubuntu:~$ 

And same result when attempting connection.  Next?

And the "Favorites" edit worked.  Thanks for that!

---

### Post by doas777 on 2010-01-12
[LEFT]it seems like part of the problem is that you are mixing gui (usershares) samba config with traditional samba config. I don't know how to back you out of that position, but I have figured out after some opain, that you should never mix the two. if you use /etc/samba/smb.conf, do not use the right click menu to create shares, and vice versa.
[/LEFT]

---

### Post by haemphyst on 2010-01-12
That was the first time I had ever done anything "backend".  I had COMPLETELY used the GUI for configuring previously.  I had no idea as to how to do anything otherwise, so maybe this latest effort by me wasn't effective on the GUI side...  I don't know.

---

### Post by haemphyst on 2010-01-14
Bump...

Anyone?

---

### Post by haemphyst on 2010-01-20
bump...  again...

Really?  Please help...

---

### Post by airtonix on 2010-01-20
this uri doesn't look correct : 
```

smb://si;haemphyst@fileserver/applications/

```

Should it not simply be : 
```

smb://fileserver/applications/

```

leave out what you were trying to attempt with the semi-colon and @ sign.

---

### Post by haemphyst on 2010-02-06
Airtonix...  I tried to copy and paste that line you thought it should be into my CLI, and nothing...

I installed smdb...  (I don't know why...)  Nothing.

I click "Connect to Server..." in my "Places" menu, select Windows Share from the menu there, type "fileserver" into the "_S_erver" box, tab to the "_S_hare" box, type "applications", and hit enter...  wait for sometimes as long as 30 seconds or so, and finally get the fail to connect window.  This is getting REALLY frustrating.

Any other suggestions?  Please?

---

