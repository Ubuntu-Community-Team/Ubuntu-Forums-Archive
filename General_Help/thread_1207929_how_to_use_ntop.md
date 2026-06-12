---
title: "how to use ntop??"
date: 2009-07-08
forum: General Help
---

### Post by harivittal.hk on 2009-07-08
hi..when i installed and used 'ntop' command to see my b/w usage..this is what the output i got on terminal..wot to do wit this...harivittal@harivittal-desktop:~$ ntop
Thu Jul  9 02:02:57 2009  NOTE: Interface merge enabled by default
Thu Jul  9 02:02:57 2009  Initializing gdbm databases
Thu Jul  9 02:02:57 2009  **ERROR** ....open of /var/lib/ntop/prefsCache.db failed: File open error
Thu Jul  9 02:02:57 2009  Possible solution: please use '-P <directory>'
Thu Jul  9 02:02:57 2009  **FATAL_ERROR** GDBM open failed, ntop shutting down...
Thu Jul  9 02:02:57 2009  CLEANUP[t3068106416]: ntop caught signal 2
Thu Jul  9 02:02:57 2009  THREADMGMT[t3068106416]: ntop RUNSTATE: SHUTDOWN(7)
Thu Jul  9 02:02:57 2009  CLEANUP[t3068106416] catching thread is unknown
Thu Jul  9 02:02:57 2009  CLEANUP: Running threads
Thu Jul  9 02:02:57 2009  CLEANUP: Locking purge mutex (may block for a little while)
Thu Jul  9 02:02:57 2009  CLEANUP: Locked purge mutex, continuing shutdown
Thu Jul  9 02:02:57 2009  CLEANUP: Continues
Thu Jul  9 02:02:57 2009  PLUGIN_TERM: Unloading plugins (if any)
Thu Jul  9 02:02:57 2009  CLEANUP: Clean up complete
Thu Jul  9 02:02:57 2009  THREADMGMT[t3068106416]: ntop RUNSTATE: TERM(8)
Thu Jul  9 02:02:57 2009  ===================================
Thu Jul  9 02:02:57 2009          ntop is shutdown...        
Thu Jul  9 02:02:57 2009  ===================================

---

### Post by ju2wheels on 2009-07-08
```
 sudo ntop 
```

Run it as root using sudo...

worked for me. I got your error without sudo.

Edit: Note, you may have to press ENTER twice after the above command so that it asks you for your admin/root user password before you are able to connect to the server on [http://localhost:3000](http://localhost:3000)

---

### Post by jonobr on 2009-07-08
Confirming ju2wheels comment,
a while ago I was playing with this and found that the permissions on installation were wrong.

You couyld run with sudo as mentioned, however, if you

ls /var/lib/ntop

you will see the write permission on some of these files are missing.

ON the test system I had I just granted full permession and ran as a regular user.
That confirmed it was a permissions issue

---

### Post by ju2wheels on 2009-07-08
What makes you think the permissions were incorrect? This application is starting a web server on the host machine so this is most likely why it requires admin/root access to start the server.... it could be a security risk if normal users shouldnt be able to start it otherwise.

---

### Post by jonobr on 2009-07-08
I dont disagree.

As mentioned, I was doing this on a test system to try and get this to run, so changing the permissions for me was not an issue.
Of course , deploying and granting access should not require changing permissions willy nilly, as an admin, it should only be accessed as root, 

Sorry for the confusion

---

