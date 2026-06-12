---
title: "My folder disappeared"
date: 2009-09-27
forum: General Help
---

### Post by Skillachi on 2009-09-27
So I already made this post in the [x86-64bit section]("http://ubuntuforums.org/showthread.php?t=1271834") of the forum but I decided to repost because I know alot of you guys dont check every forum.
Im using ubuntu 9.04 64bit with ext4 on a hp dv6700t laptop.

The problem i'm having is simply that a folder within the "documents" folder has simply disappeared from existence. I know I didnt delete it... of course I wouldnt delete such an important folder. But its not there anymore... So any ideas as to where it might have gone? and How to get it back?

Also are there any data recovery tools which can possibly find back the folder if it somehow got deleted? I've seen it done with windows, hoping it can be done here too.

---

### Post by credobyte on 2009-09-27
By the first, there's no such a thing as "My Documents" in Ubuntu - I think you are talking about users home directory ? If so, try to remember one of the files you had there and run the following command:

```
find / -name <filename>

```[COLOR=Gray]** Replace <filename> ( eg., tutorial.pdf [without extension] ).

[/COLOR]P.S. - Information about data recovery process can be found [HERE]("https://help.ubuntu.com/community/DataRecovery").

---

### Post by Skillachi on 2009-09-27
Well true there is no My Documents folder in ubuntu... Its a habit from too many years of windows usage. I'm talking about the Documents folder. thx for correction

Did the search, found nothing

---

### Post by Shujah on 2009-09-27
Three possible scenarios

1. You deleted the dir, in that case check the trash, and check the root trash @ /root/.local/share/trash.

2. Folder is hidden (somehow), press ctrl+h to toggle hidden file view.

3. Folder permissions maybe the reason IF you are not the owner, but that would issue a warning about rights.

---

### Post by NetFreeDiver on 2009-10-27
Hi All,

My folder disappeared, too. And I am (or a system that can not distinguish the difference between a file and a folder) the reason.
I had a _folder_ called "str.out". I was editing many "str.out" _files_ and copying and pasting them. At one point when I was pasting an "str.out" _file_ inside the folder that contains "str.out" _folder_ it asked me if I wish to replace "str.out", I tought that one is the previous "str.out" _file_ so I said YES. Indeed it was the folder itself. So I ended up deleting my own folder.

Would you please instruct me in finding out my files inside my "str.out" folder?

Thanks in advance,

Riza

---

