---
title: "Rsyslog dynamic file name"
date: 2011-02-11
forum: General Help
---

### Post by Khodeir on 2011-02-11
Hello all, 

I've been trying to set up rsyslog on my PC to listen for logs from my router. I haven't really had much experience with rsyslog so it took me a while and i had to fiddle quite a bit with the conf files. Anyway, I got it working now and i realized that it wouldn't take very long for one log file to get huge at the rate of logs being stored. I looked into dynamic file names and although the documentation was quite good, it seems i misunderstood something.

The way I've got it working at the moment is I have added one conf file to /etc/rsyslog.d that contains the following lines:

```
$template DynFile,"/var/log/router-log/%$YEAR%-%$MONTH%-%$DAY%.log"
:source, isequal, "localhost" /var/log/messages.log
:source, isequal, "localhost" ~
auth,authpriv.*                 ~
*.*;auth,authpriv.none          ~
cron.*                          ~
daemon.*                        ~
kern.*                          ~
lpr.*                           ~
mail.*                          ~
user.*                          ~
:source, !isequal, "localhost" ?DynFile
:source, !isequal, "localhost" ~

```

I imagine this looks very amateurish to all of you experts but the reason it has so many rules is because, for some reason, when i omit them, i get a whole load of non-router-related info. Anyway, it worked with a static name but when i added the DynFile template it simply doesn't respond. I must be doing something wrong. Any ideas?

Thank you for looking :D, 
Khodeir

---

### Post by Khodeir on 2011-02-12
Hello all,

Just an update:

I finally managed to get an error message! It might seem weird that i'm psyched about that, but at least i know it tries to run the statement now. So the error, which was in syslog, seems to imply that rsyslog doesn't have write-privileges in /var/log. I'm going to try to move the directory to write in my home folder or something. Still, it's interesting.. I thought it ran with root privileges. 

Thanks for reading, 
Khodeir

---

### Post by Khodeir on 2011-02-12
Hello again, 

One more update:

I tried changing the location of the router log and i think I might understand why it's not writing to the file. I'm not sure how valid this is so feel free to tell me i'm wrong. 

Syslog successfully creates the file with the desired characteristics that i've defined in the template. However, for some reason, it creates the file as "syslog" (as a different user) and then tries to edit it as "khodeir" (me). Because it was created under syslog, the user "khodeir" does not have write-privileges and so i get the error "Could not open dynamic file".

I've tried creating the folder with different permissions but, sadly, to no avail. Any ideas?

Thanks again, 
Khodeir

---

### Post by Khodeir on 2011-02-12
Hello all,

I finally managed to get it working! It seems the fix was quite easy. For anyone who gets the following error (under these circumstances):

```
Could not open dynamic file '/*/*/*.log' - discarding message
```

The fix is to edit the line: "$PrivDropToGroup syslog" in /etc/rsyslog.conf to "$PrivDropToGroup adm". This simply changes the privileges to all users within the group adm.

Thank you for reading, 
Khodeir

---

