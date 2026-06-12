---
title: "evolution trash doesn't empty"
date: 2012-04-22
forum: General Help
---

### Post by mune on 2012-04-22
I saw that  a similar issue has already be discussed in the past, but the solutions are not applicabile: I think the dir sturucture is changed yo to my 11.10.

It is said to delete files in .evolution/mail/local/ but I have .config/evolution/... and in .config/evolution/mail/ there isn't a /local/ folder.

I haven't noticed that in the past month up to yesterday, because evolution does not complain. I checked just because I was stating a back-up.

Please give me a hint.

Thanks

---

### Post by mune on 2012-04-22
I did some other investigation. I launched evolution from the command line to see what its errors were.

When I say to empty the trash folder it asks for the POP password of my main mail account; systematically, isn't it bizzare: what does it matter?

```
(evolution:5495): camel-WARNING **: CamelVeeStore::get_trash_folder_sync() reported failure without setting its GError

(evolution:5495): camel-WARNING **: CamelPOP3Folder::refresh_info_sync() reported failure without setting its GError

(evolution:5495): camel-WARNING **: CamelPOP3Store::get_folder_sync() reported failure without setting its GError

(evolution:5495): camel-WARNING **: CamelPOP3Store::get_inbox_folder_sync() reported failure without setting its GError

```

---

### Post by mune on 2012-04-23
Following the suggestion in an another thread but for another ubuntu version I did
```
find ./.config/evolution/ -name "*Trash*" -print -exec rm {} \
```
and
```
rm .local/share/evolution/mail/local/..#evolution.Trash.cmeta
```

But still the trash bin is full of all the 2011 deleted mails in january  and of all the subsequents of the 2012 (2610 mails!). (And it not wants to empty.)

---

### Post by audiomick on 2012-04-23
There is a check box in the Evolution prefernces on the "general" tab that you can select to tell it to empty the trash every time you close Evolution, or once a week, once a month etc. Select that and see if that solves your issue.

---

### Post by mune on 2012-04-23
Thanks for the reply.

> **audiomick said:**
> There is a check box in the Evolution prefernces on the "general" tab that you can select to tell it to empty the trash every ...

I will use it but now I want to get rid of the two thousands mails that are in trashcan.

---

### Post by audiomick on 2012-04-24
I reckon that if you set a tick on the box there, if the mails are all in the Evolution trash rather than the system trash, the should be removed next time you shut down, or at whatever point in time it is set to empty.

---

### Post by Zill on 2012-04-24
mune:  Please post the output of the following two commands:
```
evolution --version
```
```
locate folders.db
```

---

### Post by mune on 2012-04-24
Thank for the reply.

> **Zill said:**
> mune:  Please post the output of the following two commands:
```
evolution --version
```
My evolution (ubuntu 11.10) complains
```
evolution --version
Opzione --version sconosciuta
```
(unrecognized option), but in the GUI in the about window evolution states it is ver. 3.2.2 .

> ```
locate folders.db
```
I have a lot of mail folders:
```
/home/fmune/.local/share/evolution/mail/1183020266.7575.20@lello/folders.db
/home/fmune/.local/share/evolution/mail/1183021690.7575.22@lello/folders.db
/home/fmune/.local/share/evolution/mail/1183023164.7575.24@lello/folders.db
/home/fmune/.local/share/evolution/mail/1183023447.7575.25@lello/folders.db
/home/fmune/.local/share/evolution/mail/1184160185.6882.0@lello/folders.db
/home/fmune/.local/share/evolution/mail/1184160371.6882.1@lello/folders.db
/home/fmune/.local/share/evolution/mail/1197233448.24968.0@lello/folders.db
/home/fmune/.local/share/evolution/mail/1251801972.24909.1@lello/folders.db
/home/fmune/.local/share/evolution/mail/1294104592.4419.2@lello/folders.db
/home/fmune/.local/share/evolution/mail/emae-check-authtype-0x7f0465a0ec80/folders.db
/home/fmune/.local/share/evolution/mail/emae-check-authtype-0x7f7489bc8cd0/folders.db
/home/fmune/.local/share/evolution/mail/emae-check-authtype-0x7fbb4419ccb0/folders.db
/home/fmune/.local/share/evolution/mail/emae-check-authtype-0x7fbb4419d050/folders.db
/home/fmune/.local/share/evolution/mail/local/folders.db
/home/fmune/.local/share/evolution/mail/local_mbox/folders.db
/home/fmune/.local/share/evolution/mail/pop/<OMITTED_email_address>/folders.db
/home/fmune/.local/share/evolution/mail/pop/<OMITTED_email_address>/folders.db
/home/fmune/.local/share/evolution/mail/pop/<OMITTED_email_address>pop.postecert.it/folders.db
/home/fmune/.local/share/evolution/mail/pop/<OMITTED_email_address>@mail.postecert.it:995/folders.db
/home/fmune/.local/share/evolution/mail/pop/<OMITTED_email_address>@mail.postecert.it/folders.db
/home/fmune/.local/share/evolution/mail/pop/<OMITTED_email_address>@pec.postecert.it:995/folders.db
/home/fmune/.local/share/evolution/mail/pop/<OMITTED_email_address>@pop.postecert.it:995/folders.db
/home/fmune/.local/share/evolution/mail/pop/<OMITTED_email_address>@relay.poste,it/folders.db
/home/fmune/.local/share/evolution/mail/pop/<OMITTED_email_address>@relay.poste.it/folders.db
/home/fmune/.local/share/evolution/mail/pop/<OMITTED_email_address>@relay.postecert.it/folders.db
/home/fmune/.local/share/evolution/mail/pop/<OMITTED_email_address>@relay.postecert.it:995/folders.db
/home/fmune/.local/share/evolution/mail/pop/<OMITTED_email_address>@mail.postecert.it:995/folders.db
/home/fmune/.local/share/evolution/mail/pop/<OMITTED_email_address>folders.db
/home/fmune/.local/share/evolution/mail/pop/<OMITTED_email_address>relay.postecert.it:995/folders.db
/home/fmune/.local/share/evolution/mail/pop/<OMITTED_email_address>èpstecert.ir@relay.postecert.it/folders.db
/home/fmune/.local/share/evolution/mail/pop/<OMITTED_email_address>/folders.db
/home/fmune/.local/share/evolution/mail/pop/<OMITTED_email_address>:25/folders.db
/home/fmune/.local/share/evolution/mail/pop/<OMITTED_email_address>/folders.db
/home/fmune/.local/share/evolution/mail/pop/<OMITTED_email_address>@deskve.dnsalias.org/folders.db
/home/fmune/.local/share/evolution/mail/pop/<OMITTED_email_address>@popmail@email.it/folders.db
/home/fmune/.local/share/evolution/mail/spool/var/spool/mail/mune/folders.db
/home/fmune/.local/share/evolution/mail/vfolder/folders.db
/home/mune.old/.evolution/mail/local/folders.db
/home/mune.old/.evolution/mail/pop/<OMITTED_email_address>/folders.db
/home/mune.old/.evolution/mail/pop/<OMITTED_email_address>/folders.db
/home/mune.old/.evolution/mail/pop/<OMITTED_email_address>pop.postecert.it/folders.db
/home/mune.old/.evolution/mail/pop/<OMITTED_email_address>@mail.postecert.it:995/folders.db
/home/mune.old/.evolution/mail/pop/<OMITTED_email_address>@mail.postecert.it/folders.db
/home/mune.old/.evolution/mail/pop/<OMITTED_email_address>@mail.postecert.it:995/folders.db
/home/mune.old/.evolution/mail/pop/<OMITTED_email_address>@pec.postecert.it:995/folders.db
/home/mune.old/.evolution/mail/pop/<OMITTED_email_address>@pop.postecert.it:995/folders.db
/home/mune.old/.evolution/mail/pop/<OMITTED_email_address>@relay.poste,it/folders.db
/home/mune.old/.evolution/mail/pop/<OMITTED_email_address>@relay.poste.it/folders.db
/home/mune.old/.evolution/mail/pop/<OMITTED_email_address>@relay.postecert.it/folders.db
/home/mune.old/.evolution/mail/pop/<OMITTED_email_address>@relay.postecert.it:995/folders.db
/home/mune.old/.evolution/mail/pop/<OMITTED_email_address>folders.db
/home/mune.old/.evolution/mail/pop/<OMITTED_email_address>relay.postecert.it:995/folders.db
/home/mune.old/.evolution/mail/pop/<OMITTED_email_address>@relay.postecert.it/folders.db
/home/mune.old/.evolution/mail/pop/fmune@pop.tiscali.it/folders.db
/home/mune.old/.evolution/mail/pop/<OMITTED_email_address>/folders.db
/home/mune.old/.evolution/mail/pop/<OMITTED_email_address>:25/folders.db
/home/mune.old/.evolution/mail/pop/<OMITTED_email_address>/folders.db
/home/mune.old/.evolution/mail/pop/<OMITTED_email_address>@deskve.dnsalias.org/folders.db
/home/mune.old/.evolution/mail/pop/<OMITTED_email_address>/folders.db
/home/mune.old/.evolution/mail/pop/<OMITTED_email_address>@pop.gmail.com/folders.db
/home/mune.old/.evolution/mail/pop/<OMITTED_email_address>/folders.db
/home/mune.old/.evolution/mail/pop/<OMITTED_email_address>@popmail.email.it/folders.db
/home/mune.old/.evolution/mail/pop/<OMITTED_email_address>@popmail@email.it/folders.db
/home/mune.old/.evolution/mail/spool/var/spool/mail/mune/folders.db
/home/mune.old/.evolution/mail/vfolder/folders.db
/home/mune.old/Scrivania/bruno/evolution/mail/local/folders.db
[...]
```

There /home/fmune and /home/mune -now, /home/mune.old- because when in january I reinstalled the system from scratch there was already a folder named "mune" in the home partition, so, being afraid that the installation was going to overwrite the home dir -or use it-, I named the new one as "fmune".

As you can see I made a lot of mail addresses too.

---

### Post by Zill on 2012-04-24
mune:  Thanks for the info.  Please now post the output from the following command:
```
ls -l ~/.local/share/evolution/mail/local/
```

---

### Post by mune on 2012-04-24
Here it is:
```
fmune@lello:~$ ls -l ~/.local/share/evolution/mail/local/
totale 15484
drwx------ 2 fmune fmune   466944 2012-04-24 17:14 cur
-rw-r--r-- 1 fmune fmune 15370240 2012-04-24 17:14 folders.db
drwx------ 2 fmune fmune     4096 2011-12-16 19:33 new
drwx------ 2 fmune fmune     4096 2012-04-24 16:42 tmp

```

---

### Post by Zill on 2012-04-24
mune:  I suggest you try the following:

1)  **Close Evolution** (very important!)
2)  Open a terminal (Ctrl-Alt-t), then paste in the following code and hit enter.
```
mv ~/.local/share/evolution/mail/local/folders.db ~/.local/share/evolution/mail/local/folders.db_old
```
3)  Restart Evolution
4)  Wait a short while for Evolution to reindex files.
5)  Try to Expunge the Trash

What this exercise does is to rename the Evolution data file "folders.db" to "folders.db_old".  As Evolution will not find this file when it starts up, it will automatically generate a new "folders.db" file.  If the original "folders.db" was corrupted then this should create a "clean" file.

If there are any problems with this then you can always go back to the original configuration, with the original "folders.db" file, simply by reversing the code in point 2) above.

---

### Post by mune on 2012-04-24
I Did it.

as evolution opens, it regenerates the index, when disk stopped doing some activities I tryed to expunge the trash but there was any result: all the deleted mails remained in their place.:(

---

### Post by Zill on 2012-04-25
mune:  The method I described *should* work if you use POP3 mail.  If you use IMAP, rather than POP3, then you may need a different solution.

AIUI, IMAP mail is held on the server, rather than your email client (Evolution).  This means that unwanted mail must be deleted from the server.

Unfortunately, I only use POP3 email here and so have no experience of IMAP.  Hopefully, someone more knowledgeable will be able to advise further.

All I can suggest now is that you clarify if you are using POP3 or IMAP.

---

### Post by mune on 2012-04-25
All my email accounts use POP3.

I had a local mail account in /var/spool/mail/mune" but I haven't it now.

---

### Post by mune on 2012-04-25
Incredible!

I was used to do manually file->empty_trash, and just I have tryed to check in the preferences "expunge on exit"; it worked!:D

Thanks

---

### Post by Zill on 2012-04-26
> **mune said:**
> Incredible!

I was used to do manually file->empty_trash, and just I have tryed to check in the preferences "expunge on exit"; it worked!:D

Thanks
Great news. :-)

Glad you got it working.

---

### Post by audiomick on 2012-04-29
> **mune said:**
> Incredible!

I was used to do manually file->empty_trash, and just I have tryed to check in the preferences "expunge on exit"; it worked!:D

Thanks


ummm....


> **audiomick said:**
> There is a check box in the Evolution prefernces on the "general" tab that you can select to tell it to empty the trash every time you close Evolution, or once a week, once a month etc. Select that and see if that solves your issue.


> **mune said:**
> Thanks for the reply.

I will use it but now I want to get rid of the two thousands mails that are in trashcan.

> **audiomick said:**
> I reckon that if you set a tick on the box there, if the mails are all in the Evolution trash rather than the system trash, the should be removed next time you shut down, or at whatever point in time it is set to empty.

:-\"

---

### Post by mune on 2012-04-29
[QUOTE=audiomick]ummm....


:-\"[/QUOTE]

Incredible because it worked.

Just luck :)

---

