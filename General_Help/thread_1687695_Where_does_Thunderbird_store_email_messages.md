---
title: "Where does Thunderbird store email messages?"
date: 2011-02-14
forum: General Help
---

### Post by daldude on 2011-02-14
What directory does Thunderbird store all the email messages in? If one can not boot Linux but has access to the partition it's installed via a Live CD where can they go to copy the email messages file or files to another partition to save them before reinstalling Ubuntu?

---

### Post by vanadium on 2011-02-14
Your email is under a hidden folder .thunderbird in your home directory. You really only care about the mail under "Local Folders", which you reach through a file path such as:
```

/home/yourlogin/.thunderbird/rnfqs5md.default/Mail/Local Folders

```
This folder contains all mail you downloaded locally from a pop account, or which you archived locally. Mail from imap accounts is actually stored on the server, and eventually cached locally.

Your mail is there in files in the mbox format. These are files named according to the folder names you see in Thunderbird. Their name does not have a file name extension.

For each mbox file, there is an .msf file. This is an index file, and you do not really care for these either. If absent, they are recreated by thunderbird.

So the only data of unique value are the mbox files containing your actual messages.

In practice, you can just copy the "Local Folders" directory for your backup.

---

### Post by Habitual on 2011-02-14
Just to be safe, copy the entire /home/yourlogin/.thunderbird directory.
You'll save everything.

```
cp -pr /home/yourlogin/.thunderbird /home/yourlogin/thunderbird.backup
```

---

