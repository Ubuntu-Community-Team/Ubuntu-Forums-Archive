---
title: "Desperate to delete strange email"
date: 2010-02-19
forum: General Help
---

### Post by sallymc on 2010-02-19
Hi

Somebody has sent me an email that crashes Evolution. When I click on the email, that's it - I have to end the Evolution process and go back in again. Definitely can't double click it, or right-click to delete or simply delete. It just freezes. I can't see any of the text of the email, but I can see that there is a .tiff attachment.

I've poked around in the .evolution/ folders and can't find the right thing to delete to get rid of this specific email. Any ideas?

Using 9.10

Thanks!
                                                                                                   [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]                            [[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=8846187")                                                                       [IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG]             [[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=8846187")

---

### Post by howefield on 2010-02-20
Should be in your .evolution folder. 

Open Places > Home Folder, and go into the .evolution folder.

My mail is stored in home/user/.evolution/mail/imap/user@gmail.com@imap.gmail.com/folders/INBOX

Delete the offending mail.

If you are using pop to access your mail, I'd guess the path to yours would be similar, only substituting imap with pop.

---

