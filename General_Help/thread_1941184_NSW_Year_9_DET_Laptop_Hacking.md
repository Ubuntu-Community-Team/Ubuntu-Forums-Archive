---
title: "NSW Year 9 DET Laptop Hacking"
date: 2012-03-15
forum: General Help
---

### Post by Darestium on 2012-03-15
Hey,

I am Year 9 Student in a NSW school in Australia. Every person in NSW in my year group recieves a free "laptop" (it's really a netbook) and it is not really ours until we reach the end of year 12, sure we get to take it home, but the DET still owns it.

Now, the [DER]("http://en.wikipedia.org/wiki/Digital_Education_Revolution") supply the laptops, and have put all sorts of restrictions in place to prevent the students from running executable files (other then the ones installed on the system). In previous years there have been directorys in "C:\Windows" which have been writable, thus, allowing the students to copy portable executables to that location and run them from there, however, they have appeared to fix this hole and many others. I've been studying their method of blocking and it seems that it has a program whitelist (in "HLM\SOFTWARE\Polices\Microsoft\Windows\SrpV2\Exe") that checks the application that is attempting to run against it, it appears that the executables folder, file name, copyright info, and description are checked against the values in this list. Before I knew this, I wrote a program in Java (on the computer, I managed to get eclipse running without using the exe as the launcher, see [here]("http://programmers.stackexchange.com/questions/134738/java-ide-written-in-pure-java")) that searchs in the specificed directory recursively, and then the user can choose to view the writable directorys. 

I tryed this in the "C:\Windows" path, no directorys where writable, and there where many in the number of thousands that wern't. I also tryed it in "C:\Program Files\" it found a few writable directorys namely "C:\Program Files\ThinkPad\Utilities\" which contained multiple executables. I found that I could delete and run these at will! So I backed them up, then placed Firefox portable in that directory and renamed it's executable to the one which previously resided there, and I got the all too familiar error "This program is blocked by group policy. For more information, contact your system administrator.". I then tryed disabling group policy through the registry, as I am a standard account, many of the keys are not writable "HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows\System" seemed to be one of them...

I have also thought of writting a program that allows me to change a programs copyright information, or program details but from what I have read it seems impossible. Also, just to let you know, many options suggested by friends and people, are not viable, people suggested booting off a thumbdrive, creating a new partition or using [this]("http://pogostick.net/%7Epnh/ntpasswd/") to add an admistrator account. However the boot order seems to put the HDD as first priority, and a password has been set on the BIOS, so I cannot edit it. Also, I cannot remove the harddrive as there is a sticker on the bottom of it which shows if you have voided the ceil, they check it every year.

Does anyone have any ideas how I could run executable files? 

Note: I don't know if this is the correct place to post this but, due to it being about Windows, but if anyone could provide an recomendation for where else to post it, please let me know.

---

### Post by Grenage on 2012-03-15
You won't get any help for that sort of thing around here; it's rather frowned upon to help people circumvent academic or business security.

---

### Post by sffvba[e0rt on 2012-03-15
> **Grenage said:**
> You won't get any help for that sort of thing around here; it's rather frowned upon to help people circumvent academic or business security.

This

*Thread **closed**.*


404

---

