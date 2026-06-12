---
title: "OO not running as other users"
date: 2010-03-16
forum: General Help
---

### Post by jfreak53 on 2010-03-16
Ok here is what I got.  I am converting in a PHP file from the web on my server, apache server, converting from ODT to PDF using this command:

```
exec('oowriter -headless -invisible "macro:///Microtronix.Conversion.ConvertWordToPDF('.$dirLoc.$fileName2.'.odt)"', $result2);
```

Now I know that the exec command is right.  Also if I run this command from console as the user it doesn't work unless I put sudo in front of it, in which case it works.

So I tried editing sudo with visudo and added this line for the apache user:

```
admin1 ALL=NOPASSWD: /usr/bin/oowriter
www-data ALL=NOPASSWD: /usr/bin/oowriter
```

I know huge security risk, but I wanted to try and see if it would work.  That is admin1 my user and www-data the apache user.  But no, it didn't work.

So I even tried cp oowriter exec to the directory with the php file and give owner to apache and run perms.  Nothing, still no go.

Any ideas?  I know the command works only if I use sudo with it.

---

### Post by dcstar on 2010-03-17
> **jfreak53 said:**
> Ok here is what I got.  I am converting in a PHP file from the web on my server, apache server, converting from ODT to PDF using this command:

```
exec('oowriter -headless -invisible "macro:///Microtronix.Conversion.ConvertWordToPDF('.$dirLoc.$fileName2.'.odt)"', $result2);
```

Now I know that the exec command is right.  Also if I run this command from console as the user it doesn't work unless I put sudo in front of it, in which case it works.

So I tried editing sudo with visudo and added this line for the apache user:

```
admin1 ALL=NOPASSWD: /usr/bin/oowriter
www-data ALL=NOPASSWD: /usr/bin/oowriter
```

I know huge security risk, but I wanted to try and see if it would work.  That is admin1 my user and www-data the apache user.  But no, it didn't work.

So I even tried cp oowriter exec to the directory with the php file and give owner to apache and run perms.  Nothing, still no go.

Any ideas?  I know the command works only if I use sudo with it.

You have to check if the apache process (or whatever runs) has appropriate permissions to access the macro and read/write **all** the files involved in the job.

---

