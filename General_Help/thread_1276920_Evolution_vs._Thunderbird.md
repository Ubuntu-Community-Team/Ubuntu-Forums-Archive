---
title: "Evolution vs. Thunderbird"
date: 2009-09-27
forum: General Help
---

### Post by Howard Kaikow on 2009-09-27
Back when I used ubuntu 7.04, I installed Thunderbird and had it share mailboxes, etc, with Thunderbird installed in Windows 2000 on my multiboot PC. I used a small FAT32 partition to share things.

I now have ubuntu 9.04 and am trying to decide on which mail prog to use.

I'd like to try installing Evolution in Windows, if that proves to be satisfactory, I'll try to share Evolution files with ubuntu Evolution.

My questions, at this time, are there documents that explain:

1. how to share files with Evolution on both Windows and Ubuntu;
2. Can Evolution import Thunderbird mailboxes;
3. Can Evolution import Thunderbird address book;
4. Can Evolution import THunderbird message filters.

I'm reluctant to print out the 194 page Evolution manual until I get answers to the above.

P.S. Is there a forum devoted to discussing Evoultion?

---

### Post by FunkyRes on 2009-09-27
I run my own imap server that grabs my pop accounts via fetchmail.

Then I use thunderbird from Linux and squirrelmail from elsewhere.

If you don't want to set up your own imap server, some third party e-mail providers provide imap. IMHO imap is the way to go. It's not too popular with ISP's though.

---

### Post by Howard Kaikow on 2009-09-28
I installed Evolution.

1. First issue was that the install completed without asking the usual questions as to whether I wanted a desktop/quick launch icon or how to include in Start menu. Rather unusual for a program of this type.

2. So I used the Start menu to run the program. Message immediately popped up that a particuar API call could not be found. Thats AWFUL design! The installation program should be checking for the necessary libraries.

3. Turns out the missing API function requires at least Windows XP, and I am running Windows 2000 (Vista on another 'puter, but I'm not gonna switch to Evolution unless it works in windows 2000,

4. Note that there was needless use of the API function. Equivalent APIs are available in Windows 2000. The developers may have intentionally excluded Win 2000, for other reasons, but I know not why.

[Building Evolution on Windows](http://www.go-evolution.org/Building_Evolution_on_Windows) says nothing about excluding Windows 2000.

---

