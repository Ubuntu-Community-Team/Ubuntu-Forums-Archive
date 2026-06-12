---
title: "How do I combine Thunderbird 2.0 and 3.1 Inbox files?"
date: 2011-07-21
forum: General Help
---

### Post by cfechols on 2011-07-21
I installed Thunderbird 3.1.ll on Ubuntu 11.04 (64-bit) on my new computer, and need to combine my old Inbox file from my Ubuntu 9.04 Thunderbird 2.0.x on the old machine with the messages I've received in my new Inbox while trying to solve this problem.

I've copied the old Inbox file into my new profile (name changed to Inbox.old), and I've
copied the new Inbox file to Inbox.new.

After shutting down Thunderbird, I used a bash shell to execute the commands:

   cp Inbox.old Inbox
   cat Inbox.new >> Inbox

(all files are in the same "Mail/mail.xxx.com" directory).

Executing "ls -l" reveals that the Inbox file size is equal to the size of the two files combined, as I'd expect.

But when I restart Thunderbird, it doesn't recognize the old messages, listing only the new ones.  When I go to Edit -> Folder Properties, then select "Repair Folder",  Thunderbird discards the Inbox.old data, leaving only the appended Inbox.new which is the same as Inbox (I do this offline with Internet disconnected so no new messages can be received).

It also ignores the other folders and sub-folder directories and files that I also copied into their proper locations in the Mail directory tree.

What's going on here, and how do I get it to recognize these files I want to import?  I have not been able to find any information online about how to do this.

Is there anyone out there who can explain how to get these to work?  If I attempt to use Import, it apparently expects stuff from some other operating system or email client.

Any enlightenment is greatly appreciated!

---

