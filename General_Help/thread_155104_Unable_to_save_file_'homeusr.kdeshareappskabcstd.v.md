---
title: "Unable to save file '/home/usr/.kde/share/apps/kabc/std.vcf'."
date: 2006-04-04
forum: General Help
---

### Post by joey111 on 2006-04-04
if I want to store an email in kontact it suddenly says:*Unable to save file '/home/usr/.kde/share/apps/kabc/std.vcf'.*
and*Cannot write to addressbook*.
First the email in the contacts list appears, but after reopening Kontact it is gone.Why?

---

### Post by GeneralZod on 2006-04-04
[QUOTE=joey111]if I want to store an email in kontact it suddenly says:*Unable to save file '/home/usr/.kde/share/apps/kabc/std.vcf'.*
and*Cannot write to addressbook*.
First the email in the contacts list appears, but after reopening Kontact it is gone.Why?[/QUOTE]

Probably a permissions problem, though I have no idea how something like this could occur.  Have you used Kontact as root, recently?

Anyway, please paste the output of 

```

ls -l ~/.kde/share/apps/kabc

```

---

### Post by joey111 on 2006-04-04
sure, sorry;
here it is:[I]ls -l ~/.kde/share/apps/kabc
total 296
drwx------  2 johannes johannes  4096 2006-04-04 22:14 lock
drwxr-xr-x  2 johannes johannes  4096 2006-03-16 12:30 logos
drwxr-xr-x  2 johannes johannes  4096 2006-03-16 12:30 photos
drwxr-xr-x  2 johannes johannes  4096 2006-03-16 12:30 sounds
-rw-r--r--  1 root     root     36301 2006-04-03 16:25 std.vcf
-rw-r--r--  1 johannes johannes 36301 2006-04-03 22:19 std.vcf_1
-rw-r--r--  1 johannes johannes 36301 2006-04-04 22:14 std.vcf_2
-rwx------  1 johannes johannes 28407 2006-03-29 23:33 std.vcf_3
-rwx------  1 johannes johannes 33576 2006-03-30 22:17 std.vcf_4
-rwx------  1 johannes johannes 33588 2006-03-31 22:14 std.vcf_5
-rwx------  1 johannes johannes 33580 2006-04-01 17:59 std.vcf_6
-rwx------  1 johannes johannes 33580 2006-04-02 23:30 std.vcf_7
[/I]
ok,solved, i just had to get back the file from root with chown to johannes.Thank u GeneralZod;
why are there different vcffiles?

---

### Post by GeneralZod on 2006-04-04
[QUOTE=joey111]
-rw-r--r--  1 root     root     36301 2006-04-03 16:25 std.vcf
[/QUOTE]

```

sudo chown johannes:johannes ~/.kde/share/apps/kabc/std.vcf

```

:)

---

### Post by poekie on 2006-08-24
I have the same problem, for the organizer, addressbook, journal, everything but the mail part. chown did not work.. 
This just happened after my tmp-dir was full and I couldn't receive any mail (though this is stored somewhere else). Now I can't add things in the non-mail parts of kontact.. the addressbook-folder can be changed in config and then it works but the one from the organizer can't...

---

### Post by poekie on 2006-09-04
I had to delete the files in the /home/<user>/.kde/share/apps/kabc/lock folder and that did the trick. Works fine now.

---

### Post by tjk on 2007-03-19
> **poekie said:**
> I had to delete the files in the /home/<user>/.kde/share/apps/kabc/lock folder and that did the trick. Works fine now.

Just had to add to this thread, as this was the only solution that I could find in the forums to my problem, which was: that I couldn't right click on an email address and save to addressbook.  (and I therefore think this thread should be updated)  Until I deleted the files in the folder stated in quote, an error message would pop up saying that it couldn't save.  

The files don't seem to replace themselves once deleted, but I haven't  discovered any problems as a result of them not existing -- if anyone thinks that this could pose a problem down the road please let me know.

NOTE: I would recommend that if you choose to do this procedure, that you backup the folder in case you need to restore it for some reason...

---

