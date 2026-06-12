---
title: "Impossible to boot in Ubuntu"
date: 2010-06-08
forum: General Help
---

### Post by SnqKe on 2010-06-08
Hello !

Since yesterday, my computer, a fujitsu siemens esprimo mobile v5535, can't boot.
I have upgraded my Ubuntu 9.10 to 10.04, and i had trouble with my resolution which was blocked to 800*600. I wanted 1024*768.

So, i tried to install SiS drivers, but now, my computer screen display a jerky image.
I can't boot Ubuntu in graphic mode because i can't log in, and i don't know why, but i can't boot in Recovery Mode too, because it display a jerky image too.

I found that i could type CTRL + ALT + F1 to boot in terminal, but it doesn't work.

How could i do ?

(Sorry for my english, i'm french and i'm not very good in english ^^)

Thanks !

---

### Post by spotted zebra on 2010-06-08
Do you have important files on the hard drive that you are putting ubuntu on? if not i would recommend formatting it and trying again.

if you do have files on their it's a different story. get back to me about the files and ill think about how to work this one out.

---

### Post by SnqKe on 2010-06-08
Yes, i have some important email which are hosted in my thunderbird

---

### Post by oldfred on 2010-06-08
I would first use a liveCD and back up the important data. The thunderbird data is in a hidden file so from the liveCD it will have a dot at the front.
It was in ~/.mozilla-thunderbird with ver2 but I think the new tbird moved it I have not yet converted my thunderbird. The profile is 8 char.default.

It is now:
~/.thunderbird/profiles/xxxxxxxx.default/

Can you edit the boot stanza so you can get to a command line?. Try replacing quiet splash with single.

---

### Post by SnqKe on 2010-06-08
I tried with a LiveCD of Ubuntu 7.10, but when i'm going on "Computer", i just have "47.5 GB Volume", "System", "Filesystem" which redirect me in Ubuntu LiveCD's files, and WINRE which were my Windows Files. Why ?

---

### Post by mixmaster on 2010-06-08
7.10 is very old.  Maybe it can't read the partition table.  Try a more recent live CD.

---

### Post by kennedyvelez on 2010-06-08
> **SnqKe said:**
> I tried with a LiveCD of Ubuntu 7.10, but when i'm going on "Computer", i just have "47.5 GB Volume", "System", "Filesystem" which redirect me in Ubuntu LiveCD's files, and WINRE which were my Windows Files. Why ?


You should use Lucid -the emails in your thunderbird are still in your email account... so you could format without problem...

---

### Post by SnqKe on 2010-06-08
I'm downloading Ubuntu 10.4 Lucid Lynx DVD, i will give you result.

@kennedyvelez: Not with Hotmail or Yahoo :s

---

### Post by SnqKe on 2010-06-09
Hello,

Today, i tried Ubuntu 9.10 Live CD because, i don't know why, Ubuntu 10.04 Live CD don't work with my computer ...

I have access to the real Ubuntu part, but when i tried to go to ~/.thunderbird/, i had a warning which alert me that the directory is forbidden.
How could i do ? Thanks !

---

### Post by alfamud on 2010-06-09
u have no permision to got there, sudo nautilus i gess, btw if live cd does not work i would try an easier way, if ur sis has ubuntu on her machine, just put ur hard drive with hers, her computer would boot normaly but it will recognize ur HD "as XXX GB File System", just surf in the directories with as root, find all ur ur music documents and all and put em in web storage or pendrive or in ur sis harddrive :3

Sis can be usefull sometimes :3

PD: i think the directory would be ./mozilla/thunderbird  i dont use that program

---

