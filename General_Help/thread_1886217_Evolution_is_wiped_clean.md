---
title: "Evolution is wiped clean"
date: 2011-11-24
forum: General Help
---

### Post by jereece on 2011-11-24
I just fired up my email (Evolution) and almost everything is gone.  I do not have an InBox, Sent Mail, or any of the folders. The only folders I have for Mail is Search Folders > Unmatched.  My contacts are there in the contact section and the calendar is there but everything in Mail is gone.  No folders, no nothing.

Under Preferences > Mail Accounts, my email accounts are there.

Any suggestions?

Thanks,
Jim

---

### Post by Dejavou42 on 2011-11-24
what happened before it was wiped? Update? Install new software? 

Also, what type of mail account are you using? POP or IMAP?

---

### Post by jereece on 2011-11-24
Just booted up this morning.  No updates or anything new installed in weeks.  The email accounts are POP.

---

### Post by BC59 on 2011-11-24
In Evolution the email data are stored in ~/.evolution

You can check inside to see the size of the files corresponding to the folders Inbox, Trash etc. If the size is big, means the contain files, you can copy ~/.evolution and use it in another Ubuntu computer, or in a Virtual machine Ubuntu.

Another solution would be to export everything and then import to see if there is a change.

---

### Post by Dejavou42 on 2011-11-24
Ouch. Are your accounts showing up in ~/.local/share/evolution?

---

### Post by Dejavou42 on 2011-11-24
BC59: Evolution recently changed the storage location to ~/.local/share/evolution. If the files are there, it could be that the folder location is not set correctly in evolution.

---

### Post by jereece on 2011-11-24
The only thing in ~/.evolution is a folder called "Tasks".  Under that there is another folder called "Tasks" and then a folder called "Views" but all of them are empty.

Under ~/.local/share/evolution it appears the files are there.  I have a folder called "Mail".  Under that are folders for IMAP, Local, POP and vfolder.  Under Local I see files for InBox, Sent, Trash, etc. that are all of various sizes and most of them have a modified date of yesterday. 

So it appears that the files are there but for some reason Evolution is not showing them.

---

### Post by Dejavou42 on 2011-11-24
not necessarily, those folders will always be there. If they aren't, evolution recreates them. You'll need to open ./local/share/evolution/mail/pop. You should see some other folders in there. These folders will be named like: [email]Username@example.com@pop3.example.com[/email]. IF a folder like that exists then hopefully your mail is still there. If a folder like that is not there, then your account has been deleted and the folders with it.

---

### Post by jereece on 2011-11-24
Yes in  ./local/share/evolution/mail/pop I see folders for both of my email accounts.  Under each of these folders I see 1 folder called "cache" and 2 files "folders.db" and "uid-cache".  Under "cache" there are some 40 or 50 folders with letters and numbers but each of them is empty.

---

### Post by BC59 on 2011-11-24
You could install Thunderbird and migrate your messages 

Install Thunderbird and open a working account in order to be created the files Inbox, Sent etc.

```
gksudo nautilus
```

go to ~/.local/share/evolution and **copy** the Inbox, Sent, etc files and paste them to ~/home/.thunderbird/whatever.default/mail/local folders and replace the existing files

Now right click on each file and change owner, from root.

Open now Thunderbird to see if your messages are there.

---

### Post by Dejavou42 on 2011-11-24
hmmm.... that's not good. The folders with letters and numbers are the containers that hold the e-mails. If all of them are empty then your e-mails are gone....

---

### Post by jereece on 2011-11-25
I think my hard drive is failing.  I have had some other weird things happen.

---

