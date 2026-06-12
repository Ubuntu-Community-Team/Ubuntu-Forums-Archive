---
title: "Evolution - how to delete a specific crashy email"
date: 2011-03-02
forum: General Help
---

### Post by happyisland on 2011-03-02
Hey Ubuntu geniuses,

I've got a problem with my evolution here at work, which is running on a vanilla Ubuntu 10.10 install. Yesterday we received an email from a supplier with some tiff attachments. When this email is clicked on it freezes Evolution. The further problem is that I can't even browse into the inbox folder where it is since that email is the last thing that was highlighted. 

My question: what is the best method for removing a single email from the Inbox? I thought about into the .evolution/mail folder, but I wasn't sure which files to modify to solve the problem.

Any advice would be much appreciated!

-HI

---

### Post by philinux on 2011-03-02
> **happyisland said:**
> Hey Ubuntu geniuses,

I've got a problem with my evolution here at work, which is running on a vanilla Ubuntu 10.10 install. Yesterday we received an email from a supplier with some tiff attachments. When this email is clicked on it freezes Evolution. The further problem is that I can't even browse into the inbox folder where it is since that email is the last thing that was highlighted. 

My question: what is the best method for removing a single email from the Inbox? I thought about into the .evolution/mail folder, but I wasn't sure which files to modify to solve the problem.

Any advice would be much appreciated!

-HI

You could try this. Close evolution. Browse to the .evolution/mail/local folder and delete the file folders.db.

Restart evolution and it will create a new folders.db file. This can sometimes be at fault.

---

### Post by happyisland on 2011-03-02
Hey Philinux,

Thanks for the idea, but I tried it and that same dang email is still freezing up Evolution. Any other ideas?

Best from Aruba,

HI

---

### Post by fonsi2099 on 2011-05-28
Copied from other thread ti works fine with 11.04.

The folder structure has changed slightly on 11.04 or probably on Evolution 2.32. Anyway, the folders in question are now ~/.local/share/evolution/mail/local/ and so on. 
go there an delete the mail/ file you need to delete, I think if you try these steps but with that folder name, you'll get the same result as me.

:popcorn:

---

### Post by felixa on 2012-01-19
hello,

there is an "on board" solution for this problem. Also, if the message containing
the "crashy" tiff comes from an IMAP folder, the shell solution wouldn't help, as 
you would not be ably to delete the message on your local computer. Instead,
try this:

first, start evolution in non-preview mode:[INDENT]  evolution --disable-preview
[/INDENT]second, disable rendering of HTML mails:[INDENT]Edit > Preferences > Mail Preferences > HTML Mail > Simple Text Mode
("Display as Text-Only")
[/INDENT]now, you can safely delete the offending messages.

hth,
felixa

---

