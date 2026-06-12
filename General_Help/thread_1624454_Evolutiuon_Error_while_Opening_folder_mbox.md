---
title: "Evolutiuon Error while Opening folder mbox"
date: 2010-11-17
forum: General Help
---

### Post by rinrada on 2010-11-17
Yesterday I used Unison to sync my desktop and laptop. Now I am getting the following error when I open my Evolution Inbox (and a few of my other mailbox folders).

"Error while Opening folder mbox:/home/myname/.evolution/mail/local#Archive/foldername"

"column folder_name is not unique"

I have tried moving the .evolution/local/mail folder opening Evolution, closing and then moving back - no joy. It is also definitely not a folder size problem, my mailbox is less than 1GB.

Opening Evolution from the terminal I get;
** (evolution:7529): DEBUG: mailto URL command: evolution %s
** (evolution:7529): DEBUG: mailto URL program: evolution

(evolution:7529): camel-local-provider-WARNING **: Could not save summary for local providers
****repeated many times, then ****
evolution-mail-Message: Error occurred while existing dialogue active:
column folder_name is not unique

I tried using the advice in this thread (the only one I can find with a similar error):
[http://ubuntuforums.org/showthread.php?t=1491376&highlight=evolution+column+folder_name+is+not+unique](http://ubuntuforums.org/showthread.php?t=1491376&highlight=evolution+column+folder_name+is+not+unique)

and used the following command

cd ~/.evolution/mail ; for i in `find . -name folders.db`; do echo "Rebuilding Table $i"; sqlite3 $i "pragma integrity_check;"; done

However, I still get the problem. I'll paste the print out below as it is rather long.
Any help would be appreciated.:(

---

### Post by rinrada on 2010-11-17
We'll I'll be damned - I was almost in tears yesterday and fought it for another hour plus this morning. And now I found the simplest solution.

Quit Evolution

In the folder .evolution/mail/local I found the file folders.db and changed the name (to foldersbak.db).

Open Evolution

It reloads the mail and generates and new folders.db file

---

### Post by dcstar on 2010-11-17
> **rinrada said:**
> Yesterday I used Unison to sync my desktop and laptop.
.........

Are you running the same Ubuntu version on both machines?

---

