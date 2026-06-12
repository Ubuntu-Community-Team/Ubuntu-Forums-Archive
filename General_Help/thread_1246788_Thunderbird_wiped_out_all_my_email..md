---
title: "Thunderbird wiped out all my email."
date: 2009-08-22
forum: General Help
---

### Post by r11_kaede on 2009-08-22
Hi guys,

As the subject name goes, Thunderbird wiped out all my email accounts after I did the usual upgrading to 2.0.0.23. It does not recognize the mail in my profile folders, even after I deleted the *.msf files, deleted/restored the profile folder.

I'm out of ideas. Any one? :)

Thanks.

---

### Post by HiImTye on 2009-08-22
were you using POP3 with the 'delete from server' option enabled? if not your mail should still be on your server

---

### Post by r11_kaede on 2009-08-22
unfortunately, I actually did delete my messages from the servers. 

So essentially this means that my emails are all gone?

---

### Post by r11_kaede on 2009-08-22
Well, I'm done with Thunderbird. No way can I use a program that wipes out all my mail after one simple upgrading. I'll switch to Claws from now on.

Thanks anyway, for your help. Appreciate it.

---

### Post by howefield on 2009-08-22
> **r11_kaede said:**
> Well, I'm done with Thunderbird. No way can I use a program that wipes out all my mail after one simple upgrading. I'll switch to Claws from now on.

Thanks anyway, for your help. Appreciate it.

Thunderbird can only do what you tell it to do. Your mail loss was completely preventable.

---

### Post by jotiho on 2009-09-01
I've just had a similar problem, but I'm hoping to be able to recover the emails from the .mozilla-thunderbird/xxxxxxxx.default directory once I can figure out how to point Thunderbird at it. Any suggestions welcome.
 
>>Thunderbird can only do what you tell it to do. Your mail loss was completely >>preventable.
 
When I first set up T-bird I did not get the option to change the default "delete files from server" option. This does strike as a bug rather than a feature!

---

### Post by sedawk on 2009-09-01
No mails are lost until you do not start to delete stuff
from .mozilla-thunderbird/...
Somewhere inside there are standard mbox-files any unix mail-reader
can use.
You can even open them with a text-editor to check what is inside.

In worst case you can rename .mozilla-thunderbird to .mail_backup
then start with a new setup in thunderbird and with new
(empty) folders and then copy over the mail files (mbox-files)
from the .mail_backup/... to your new .mozilla-thunderbird directory
(one-by-one).

I once had a similar problem but I cannot remember how I solved
it - some import/export plugin or if I copied my old mail-tree
to a subtree of the new thunderbird installation.

I think detailed instructions about how to move old mails
to a new user/thunderbird installation are available on the internet.

---

### Post by adam.ec on 2009-10-17
> **howefield said:**
> Thunderbird can only do what you tell it to do. Your mail loss was completely preventable.

As an application programmer I would be inclined to agree with you but I actually don't.

I haven't updated, changed or done anything to my Thunderbird application other than press the 'Get Mail' button for about three weeks. Yesterday, my mail filters completely disappeared and my mail started coming straight into 'Inbox' rather than the folders it was assigned to.

As of this morning Thunderbird claimed it was downloading message 4 of 11. Strange how only one turned up in my inbox. I never asked Thunderbird to do this. Anyway, my Thunderbird is set to leave email on the server, so I went to my webmail and guess what? It isn't leaving mail on the server.

There are plenty of posts on the Windows versions of Thunderbird losing the message filters. I can't find any for Linux so I haven't got a clue what happened. I have reinstalled Thunderbird and tried to import the mail folders again but the mail that should have been there just never made it. At no point did I ask Thunderbird to do this. Can you explain to me how I can prevent losing my email and my filters?

Sorry if I seem a bit off-hand but I began learning to program in 1982. My father used to tell me "The computer only does what you tell it to do". I've tried to believe this statement for 25 years. Now I am much more experienced and have surely decided that a computer does not always just do what you tell it to. It annoys me more that less experienced users are told the same thing when they get problems like this. If users should have to leave their mail on the server, why does the program offer the facility to wipe them off?

---

### Post by stinger30au on 2009-10-17
> **r11_kaede said:**
> Hi guys,

As the subject name goes, Thunderbird wiped out all my email accounts after I did the usual upgrading to 2.0.0.23. It does not recognize the mail in my profile folders, even after I deleted the *.msf files, deleted/restored the profile folder.

I'm out of ideas. Any one? :)

Thanks.

did you backup all data *BEFORE* you did the upgrade

---

