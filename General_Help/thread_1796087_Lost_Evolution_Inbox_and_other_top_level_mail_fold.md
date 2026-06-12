---
title: "Lost Evolution Inbox and other top level mail folders during upgrade to 11.04"
date: 2011-07-03
forum: General Help
---

### Post by SusieSA on 2011-07-03
Hi.  I've just upgraded to 11.04 and I created a evolution-backup.tar.gz file as I've done in other upgrades.  When I restored the backup and started Evolution, I've lost all the emails in top-level folders (Inbox, Sent, Drafts etc).  My own custom folders within these top level folders contain the emails that I backed up. There are quite a few important emails that I've yet to respond to in my Inbox and this is very concerning.

Also, I've lost all my Contacts!

Any ideas - this has worked flawlessly before.

---

### Post by SusieSA on 2011-07-03
Another snippet of information.

.evolution/mail/local$ vi Inbox

When I look in the Inbox file (which is 1.6G), I can find the text of an email which I know to be in my Inbox and not in a sub-directory.  But it just seems that Evolution isn't displaying this message.

Thanks!

---

### Post by SusieSA on 2011-07-04
I sorted this out!  Yippee! And I have to say that it was a very simple problem.  

11.04 (or is it Evolution?) no longer uses the .evolution folder to store folders and mail.  It uses the .local/share/evolution folder.  So when I used the tar command to restore my backup that I'd taken from 10.04, I could move the .gconf and .gnome2_private files as before.  But all the files in the restored .evolution folder needed to be moved to the .local/share/evolution folder.  Now it all works fine. 

I hope that this helps somebody else.  The documentation for upgrading to 11.04 could have been clearer because I'm sure that this is a common problem.

---

### Post by dcstar on 2011-07-04
> **SusieSA said:**
> I sorted this out!  Yippee! And I have to say that it was a very simple problem.  

11.04 (or is it Evolution?) no longer uses the .evolution folder to store folders and mail.  It uses the .local/share/evolution folder.  So when I used the tar command to restore my backup that I'd taken from 10.04, I could move the .gconf and .gnome2_private files as before.  But all the files in the restored .evolution folder needed to be moved to the .local/share/evolution folder.  Now it all works fine. 

I hope that this helps somebody else.  The documentation for upgrading to 11.04 could have been clearer because I'm sure that this is a common problem.

**Who** told you to use a tar backup for the upgrade?

---

### Post by SusieSA on 2011-07-04
Now that is a good question, David!  I've been using Ubuntu for 5 years now and have done similar upgrades about times before and every time I've done an upgrade, I've used the tar backup.  Now, when I revisit the Installation Guide, Section 3 (Before Installing Ubuntu) has a sub-section called 'Back Up Your Existing Data!'.  So I backed up everything including my email.  Seemed logical to use the old way that I've always done it before. 

Also, I did the complete installation of 11.04 and erased 10.04 so I was extra cautious to back up everything.

What *should* I have done?

And now I'm in a pickle with my Contacts because they too are in the wrong folder and I'm struggling to get Evolution to read the Contacts.  Any ideas would be greatly appreciated.

Thanks David.

---

