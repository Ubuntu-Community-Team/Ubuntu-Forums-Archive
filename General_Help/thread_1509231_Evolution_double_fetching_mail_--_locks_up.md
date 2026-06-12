---
title: "Evolution double fetching mail -- locks up"
date: 2010-06-14
forum: General Help
---

### Post by AFD8766 on 2010-06-14
Within the last few days, Evolution barely opens, and every message has a duplicate message.  The duplicate shows as unread, whether I read the original message or not.  All duplicates occur only for messages received prior to Wednesday late PM (about four days ago).  

My in-box was already large, and the program now takes forever to open.  In its attempt to get all the messages, it shows: 
Fetching mail (...)
Generating message list (...)
Storing folder (...)

I've watched the system monitor, and I'm open to suggestions if looking for something specific could help.  When I first attempt to open the program, it grabs a substantial portion of the CPU as status "running" or "uninterruptible."  If I let it grind away for a while (15 or more minutes), the program opens, and has the double entries and continues to labor to get the new e-mail.  In the most recent try, the program opens, and eventually is able to get mail.  
 
This recent problem MIGHT be related to traveling, when I switched to working off-line for a while, and was usually hibernating the machine in between uses, rather than shutting down.  Also, I resorted to checking mail via a web mail program at one point.  

Could I have hit the wrong option about synchronizing folders?  Default is "do not synchronize."  When off-line, I only want to read and answer messages from the inbox, and have them sent from the outbox when I again have access.  What is the proper way to do this?  I don't have any messages in folders except a few draft e-mails.   

I'm running Evolution 2.26 on Jaunty.  

What did I do wrong, and how do I fix it!??

PS:  Is there a more specific forum for Evolution?

---

### Post by dcstar on 2010-06-14
> **AFD8766 said:**
> Within the last few days, Evolution barely opens, and every message has a duplicate message.  The duplicate shows as unread, whether I read the original message or not.  All duplicates occur only for messages received prior to Wednesday late PM (about four days ago).  

My in-box was already large, and the program now takes forever to open.  In its attempt to get all the messages, it shows: 
Fetching mail (...)
Generating message list (...)
Storing folder (...)
..........

[LIST=1]
[*]Are you running 32-bit?
[*]Are your Evolution data files over the 2GB limit?
[/LIST]

---

### Post by AFD8766 on 2010-06-14
Thanks for the questions


1.) I think this indicates I am running a 64-bit kernal?
PASTING = = >
alex@alex-laptop:~$ uname -a
Linux alex-laptop 2.6.28-19-generic #61-Ubuntu SMP Wed May 26 23:32:46 UTC 2010 x86_64 GNU/Linux
< = =  END PASTE
Gleaned from
[http://www.linuxquestions.org/questions/linux-kernel-70/how-to-check-whether-kernel-is-32-bit-or-64-bit-in-linux-701576/]("http://www.linuxquestions.org/questions/linux-kernel-70/how-to-check-whether-kernel-is-32-bit-or-64-bit-in-linux-701576/") (see last post!)

2.) After much searching, I found the data files
/home/alex/.evolution/mail/local/
Inbox 2.3 GB
Sent 488 MB
(Thanks: [http://www.go-evolution.org/FAQ#Where_does_Evolution_store_my_data.3F]("http://www.go-evolution.org/FAQ#Where_does_Evolution_store_my_data.3F"))

So I'm not sure how the above information is useful, being a relative newbie.  This seems more to the point:
[http://www.go-evolution.org/FAQ#Why_does_Evolution_download_duplicate_emails.3F_How_can_I_get_rid_of_them.3F_Why_does_Evolution_reload_old_mails_from_server_when_.22Leave_a_message_on_the_pop_server.22_is_activated.3F]("http://www.go-evolution.org/FAQ#Why_does_Evolution_download_duplicate_emails.3F_How_can_I_get_rid_of_them.3F_Why_does_Evolution_reload_old_mails_from_server_when_.22Leave_a_message_on_the_pop_server.22_is_activated.3F")

I woke up this morning feeling more convinced that the problem was caused by me checking messages via webmail, while "leave messages on server is activated," which is mentioned in the FAQ above (in the Q).  The answer gives a link to a script, but I barely know how to put something into Terminal.  Another option is a plug-in.  (Both links below)

Learn how to run scripts? Download the plug-in, and learn how to use a tar.gz?  Would either implementation work?  Or manually nuke the dupes and avoid webmail in the future?  Or are there other choices?

Script posting
[http://lists.ximian.com/archives/public/evolution/2005-January/041442.html]("http://lists.ximian.com/archives/public/evolution/2005-January/041442.html")
Plug-in
[http://people.gnome.org/~carlosg/stuff/evolution/]("http://people.gnome.org/~carlosg/stuff/evolution/")

I didn't see anything in Synaptic Package Manager, which would be my preferred avenue.

---

### Post by ThesaurusRex on 2010-06-14
A mail client which gets duplicate mails and always marks the new ones as unread usually hints that you may be using POP instead of IMAP.

---

### Post by philinux on 2010-06-14
Evolution does not delete mails it merely hides them. You must do Folder>Expunge. You can change the default settings.

---

### Post by AFD8766 on 2010-06-14
Thanks for both responses.

@ ThesaurusRex
Receiving e-mail server type = POP
Sending e-mail server type = SMTP
Why might this matter?  Back to the original quest: what went wrong, and how do I fix it??

@ philinux
Confusing terminology, but I think I get what you're saying, especially after reading 2.1.9 in the User Guide.
Anyhow, for the time being I am not able to empty the trash.  "Error while expunging folder."  Ditto on expunging inbox or sent items. I will close all programs and re-start evolution and try again.  Other suggestions??

---

### Post by AFD8766 on 2010-06-14
Update:  Re-started computer, opened Evolution (15 or so minutes), attempted to empty trash, or expunge.  No luck.

Turned off automatic send/receive ("check for messages every __ minutes").

Initially "storing folder" went through, slowly, several folders.  Now "storing folder" and "generating message list" are both stuck on zero, unable to be canceled.  Likewise the cancel button is unresponsive. System monitor shows Evolution no longer using CPU (~1% and flat); 54 MiB memory but status is "sleeping."  

Can anyone suggest a workaround to shrink my inbox and thereby allow Evolution to function?  It is time for desperate measures!?

On a related note, so I avoid this inbox bloat in the future, how does one save older messages in a way that shrinks the inbox and sent items?  I don't see this in the User Guide.

---

### Post by mars-2010 on 2010-06-15
I found the following post in launchpad.  It is worth a try.

[nocturrne]("https://launchpad.net/%7Enocturrne")             wrote             on 2008-06-30:                                                             [ #18]("https://bugs.launchpad.net/evolution/+bug/197290/comments/18")                                                        I have the same problem every 6 months or so.  This lame bug has been around since at least 2005.  Please fix it.
 Ubuntu Gutsy 7.10
Evolution 2.12.1
 The best workaround I have found is to use archivemail to archive the old mail in the file, reducing the file size.
 install archivemail:
 sudo apt-get install archivemail
 archive all mail older than 90 days:
 archivemail -d90 ~/.evolution/mail/local/yourmailfile
 After doing this, the file size is reduced way below 2GB, so it will open the next time you start evolution. If you like you can decompress the archive file and import it into another folder in evolution - takes a while though...
 Regards

---

### Post by AFD8766 on 2010-06-17
Somewhat different solution, from here:
[http://ubuntuforums.org/archive/index.php/t-1085838.html]("http://ubuntuforums.org/archive/index.php/t-1085838.html")
specifically I used the least invasive solution, dcstar's 16 January post:
> Shutdown Evolution client
Rename /home/dc/.evolution/mail/local/folders.db file
Restart Evolution again and now syncs should be successful.

It seems there is a database listing the various mail box files that can get corrupted, and just deleting the individual cmeta and index files does not fix this up.

This method leaves your Calendar/Contact info intact.  

Still, I have to delete the duplicate e-mails that were somehow generated.  And ultimately, I don't know how this happened.  I strongly suspect that either accessing webmail and/or hibernating without shutting down and/or a too-large mailbox all contributed.  

Now I would like to archive, but that didn't work... subject of another post soon if necessary.  

I'll look for comments for a day or two, then call this solved.

---

