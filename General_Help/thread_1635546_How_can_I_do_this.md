---
title: "How can I do this"
date: 2010-12-01
forum: General Help
---

### Post by braggman on 2010-12-01
I am using Ubuntu directly from a CD. I am trying to recover files from an unbootable Windows Vista computer that was infected by a virus. I can't seem to see any of the user files or documents to transfer them to my USB hard drive. However I can see all the existing files on the USB drive with no issues. Are the files hidden because I'm doing something wrong, are they encrypted by Windows, or are the contents of the local user files just hidden from Ubuntu?

---

### Post by CharlesA on 2010-12-01
Did you select the correct drive from the Places menu?

---

### Post by braggman on 2010-12-02
I can access the hard drive. I can see some of the programs in "Program files" and "program files x86" but not the ones with the data I need. All of the folders inside "Users" are empty. The main User profile doesn't display at all. And "Documents and Settings" is empty.

---

### Post by CharlesA on 2010-12-02
Then I'd say the user data was wiped out somehow. Are you able to boot off a Vista cd and run a repair on the install?

---

### Post by braggman on 2010-12-02
I'll have to try that when I can get access to the restore CD. I don't have it with me. I was hoping to sidestep that with Ubuntu. There is all financial and payroll info for my brother's business on the laptop so I'm nervous about trying a restore. I don't think the data is gone because I can see all other data, just not anything that would require a user login to get to. Either they are encrypted or not visible from Ubuntu because all of the nuts and bolts Windows files are intact and visible. Thanks for the suggestions. I'm afrail that I'll just have to try repairing when I get the disk back.

---

### Post by CharlesA on 2010-12-02
For the most part, if the files aren't encrypted, you can see them with a livecd. Trying a repair is probably the best thing you can do.

---

### Post by braggman on 2010-12-02
Thank you Charles. I found the problem. When viewing the hard drive from Ubuntu some of the Windows "friendly names" are not preserved. The documents for the main user profile were not stored with the original user name that Windows displays. Instead they are all located under "Default User." I assume that's the case if there is only one log-in profile. It may have been different had we created multiple profiles on this computer. I was able to find the profile I needed ,and began copying files. LiveCD seems to be a very useful tool for even dedicated Windows users to keep even if they only use it for file recovery from an infected computer that won't boot.

---

### Post by CharlesA on 2010-12-02
Ah. Gotcha. I totally forgot about that. Windows can be a pain with naming sometimes.

Glad you were able to pull the files off. :)

---

