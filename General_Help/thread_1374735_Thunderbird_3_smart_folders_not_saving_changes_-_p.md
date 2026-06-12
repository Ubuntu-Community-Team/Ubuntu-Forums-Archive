---
title: "Thunderbird 3 smart folders not saving changes - possible workaround"
date: 2010-01-07
forum: General Help
---

### Post by nbaks on 2010-01-07
I recently upgraded to Thunderbird 3 using the ubuntuzilla script. One of the great new feature is the so called 'Smart folders' which lets you view all of your mail from different accounts in one list. Since I have set up automatic rules to sort mails from different people and mailing lists in different sub-folders I wanted to include these in the list too. However very time I tried to get Thunderbird to include sub-folders from my different accounts, the settings would reset itself - but now I think I might have found a fix:

[LIST=1]
[*]In your Thunderbird folder find the folder called 'smart mailboxes'
[*]Right-click the file 'Inbox.msf' and select 'Properties' (I think it's called this i'm on a Danish system)
[*]Go to the 'Rights' section (again this is what I think it's called)
[*]Set your own rights to 'read' only, exit
[*]Open Thunderbird
[*]Right-click the Smart folders Inbox and select 'Properties'
[*] Choose the folders you want to include, remember to check 'Match all messages'
[/LIST]

Now the changes should stick after a restart.

Let me know if it works.

---

### Post by Anicky on 2010-02-25
Downgrading my own rights on smart mailboxes/INBOX.msf (however absurd it may look) did work for me on a MacBook, and I hope it will work on other systems, too. Thank you very much for the tip.

---

### Post by bellalistair on 2010-05-03
That's bizarre! but works for me on lucid, I've not got the smart folders working quite right yet as it is including an inbox in templates. But at least I can stop it showing unread messages as being in the templates smart folder now.
Thanks.

---

