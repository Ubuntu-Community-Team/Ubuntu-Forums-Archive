---
title: "Thunderbird deletes new emails"
date: 2011-08-09
forum: General Help
---

### Post by irw on 2011-08-09
Over the last few months, I have noticed a number of emails going missing, nad over the last few days it has happened as I watch:

When I hit "Get mail", I can see the emails coming into my inbox, but then a random number just disappear, and cannot be found using the thunderbird search tools.

After seeing [this page]("http://www.makeuseof.com/tag/how-to-recover-deleted-emails-in-thunderbird/"), I looked at my inbox file today immediately after this had happened, and the emails were all there, but marked deleted.
In thunderbird, they are not in the trash folder, they do not seem to exist at all.
After compacting, they disappear forever.

I have no filters running.
I yesterday spent a long time creating a new profile, and with no add-ons and no filters, I have seen this again today - 8 out of ten emails newly downloaded disappeared as I watched.


Help!

Any ideas why / how to stop this?

If this continues, I will have to change email client, but I have got used to Thunderbird and would rather not.

---

### Post by Kira_Belka on 2011-08-09
click   in thunderbird "edit"-"preferences"-"security"-"junk" tab Reset Training Data... it probably has to help

---

### Post by Habitual on 2011-08-09
Logged in to mail anywhere else, at work maybe?

---

### Post by irw on 2011-08-10
This happened with a new setup of Thunderbird, so no junk training data.

I have not accessed the email from anywhere else - as I said, I see the emails arrive in my inbox, then they disappear as I am watching.
Then when looking at the inbox file, the emails are marked as deleted, even though I have not touched them, and they do no show up in the deleted folder.

---

### Post by dragonfly41 on 2011-08-10
Could it be your POP Mail Server deleting them ?

In Thunderbird > Edit > Account Settings > Server Settings

In POP Mail Server settings ..

have you ticked the boxes

"leave messages on server"
and 
"until I delete them"

---

### Post by SoFl W on 2011-08-10
Check your Retention Policy.  

I think it is in two places, right click on the folder, select settings and the Retention Policy tab.
Also check disk space under account settings.

(and if your retention policy is set properly, check and make sure your system time/date is correct)

---

### Post by irw on 2011-08-10
OK, I think I have solved the problem.

I have been using the "unified Folders" to look at the incoming mail for several accounts.

*One* of the Inbox mbox files was corrupt - and for some reason that seemed to cause problems for incoming email from other accounts as well. Instead of being a text file, it was binary according to gedit / looking at the contents with cat.
The main inbox file was corrupt, but when I set up a new gnail account, 8 of 10 of my incoming gmail emails "disappeared".
That mbox file was not corrupt, because I could edit it with a text editor and remark the missing emails as not deleted.

I exported all my email using the [ImportExportTools]("https://nic-nac-project.org/~kaosmos/index-en.html") extension.
After this, I deleted the contents of the Mail folder for that profile.
I then imported my email back, and after some tidying up, I am now working with no corrupted mbox files (I manually checked each one - dozens with all the folders I have to organise my email.


Now to look at my wife's email, because after asking me what I was doing, she said she had the same problem!

---

