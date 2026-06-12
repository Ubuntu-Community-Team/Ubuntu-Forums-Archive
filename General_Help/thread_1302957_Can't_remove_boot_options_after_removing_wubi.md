---
title: "Can't remove boot options after removing wubi?"
date: 2009-10-27
forum: General Help
---

### Post by Oyjord on 2009-10-27
Hi all,

I installed wubi/ubuntu, uninstalled it under Add/Remove programs, did NOT reboot (my mistake), then installed Windows 7.

Now, when I reboot my PC, I get an option to load Windows 7 or Ubuntu.  Ack.  I uninstalled Ubuntu, I should be booting directly into Windows.  In my new Windows 7 Add/Remove Programs list, there's no wubi/ubuntu to uninstall.

Please advise on how I can simply boot normally into Windows.

Thanks in advance!
Oyjord.

---

### Post by martrn on 2009-10-27
Ask at the windowze forums [http://thewinforums.com/]("http://thewinforums.com/") or simular about howto remove entries from the boot system of the operating system you have.  Not everyone here has windowze.

---

### Post by Oyjord on 2009-10-27
> **martrn said:**
> Ask at the windowze forums [http://thewinforums.com/]("http://thewinforums.com/") or simular about howto remove entries from the boot system of the operating system you have.  Not everyone here has windowze.

Um, thanks?  You don't suppose over there they'll simply says "Go to the wubi forums?"  I figure I only encountered this problem bc of wubi, so perhaps others who'd used it might be able to help.

Also, linux/open source folks tend to be more helpful, as a community.  Maybe I'm wrong (at least in your case)....

---

### Post by Oyjord on 2009-10-27
BTW, for those who might have this similar problem, booting into Repair and typing at the command prompt "Bootrec.exe /FixMbr" does NOT work.

Ugh.

---

### Post by martrn on 2009-10-27
> **Oyjord said:**
> BTW, for those who might have this similar problem, booting into Repair and typing at the command prompt "Bootrec.exe /FixMbr" does NOT work.Ugh.

Here is what I can find out (though don't have windows working).  Source : [http://vlaurie.com/computers2/Articles/bootini.htm]("http://vlaurie.com/computers2/Articles/bootini.htm"). boot.ini is one of the very first files that come into play when a Windowzes system is started up. It is a plain text file that is kept in the system root, so it is usually C:\boot.ini. Because it is an essential system file, the attributes are set to hidden, system, read-only just protect it. That means that it will not appear in the file lists in windowze file manager unless the default windows settings are changed to show hidden files.

The file 'boot.ini' contains the location of the windowze operating system on the computer. If there is a multi-boot system, the locations of of any other operating systems are also contained there.

You need to find this windowze file and edit it.

Thats the best I can do.

Sometimetimes people who use wubi we never see again.  Have you not thought that they might be at the windowze forums. [[http://thewinforums.com/]("http://thewinforums.com/") ] See post no 2 in this thread.

---

