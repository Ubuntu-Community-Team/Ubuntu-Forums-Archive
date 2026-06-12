---
title: "Move from Thunderbird to Claws frustrated by folder issue."
date: 2010-08-26
forum: General Help
---

### Post by casbahdk on 2010-08-26
I have exported my locally stored folders from Thunderbird 3, however Claws Mail appears not to support locally stored folders. How do I import my Thunderbird based mbox files into Claws Mail?

The following seems to be a similar thread, with the same problem as I have, but no solution:

[http://crunchbanglinux.org/forums/topic/3070/new-mail-folder-in-claws-mail/]("http://crunchbanglinux.org/forums/topic/3070/new-mail-folder-in-claws-mail/")

I have been through the documentation and googled, but no luck so far. Anyone have an idea how to solve this?

I am using Claws Mail version 3.7.4.

---

### Post by casbahdk on 2010-08-26
I believe I have found the answer, so I am posting this for others that run into the same issue. This could eventually be used as part of a HowTo, for other users unfamiliar with how Claws Mail functions.

The answer is - File > Add mailbox > MH

The default folders that are a part of the new folder's hierarchy (which often confuses newbies like myself), are used with the MH handling system (there are a number of e-mail clients using MH, including Evolution and MUTT), and function as a local que. All that you have to do is right-click the new mailbox labeled "MH" and chose to create a new folder. When the dialog pops-up, make sure to check the item "inherit properties from parent folder" and input the name for the new folder. Highlight the new folder, and then go to File > Import mbox file.

---

