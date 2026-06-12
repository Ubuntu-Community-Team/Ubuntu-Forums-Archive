---
title: "crazy problem with gnome terminal"
date: 2010-02-12
forum: General Help
---

### Post by Andres Gonzalez on 2010-02-12
I am using Ubuntu release 8.10

Recently a new problem with gnome terminal has come up.  When I open a file to edit using vim, after about 10 key strokes (the number varies) the key binding get all screwed up. For example, pressing the key 'j' instead of advancing the cursor down a line, just prints a 'j' on the screen--however, I am not in edit mode. I press the ESC key and I get '^[' printed on the screen.  What is very strange, is that sometimes this does NOT happen and sometimes it will work OK for a few minutes then go crazy on me. xterm does not seem to have this problem.

Any help would be greatly appreciate.

Thanks,

-Andres

---

### Post by Andres Gonzalez on 2010-02-12
bump

Please, this problem is getting very frustration.

-Andres

---

### Post by garvinrick4 on 2010-02-12
Sounds like a vim problem not Linux. Have you uninstalled.
Then cleaned cache and reinstalled to make sure you have a 
good install of vim.

sudo apt-get purge (package name)    

sudo apt-get clean

sudo apt-get install (package name)

---

### Post by VMC on 2010-02-12
> **Andres Gonzalez said:**
> I am using Ubuntu release 8.10

Recently a new problem with gnome terminal has come up.  When I open a file to edit using vim, after about 10 key strokes (the number varies) the key binding get all screwed up. For example, pressing the key 'j' instead of advancing the cursor down a line, just prints a 'j' on the screen--however, I am not in edit mode. I press the ESC key and I get '^[' printed on the screen.  What is very strange, is that sometimes this does NOT happen and sometimes it will work OK for a few minutes then go crazy on me. xterm does not seem to have this problem.

Any help would be greatly appreciate.-Andres

I've never had this problem. Perhaps look into your ".bashrc" settings for a clue. Have you edited that file in any way?

Since xterm works, then it must be something in bash that messes things up. Is it the same file your editing or just any file?

Ok, I see, its vim and not vi. So you installed vim? What version?

---

### Post by Andres Gonzalez on 2010-02-12
Thanks for the responses guys.

I tried the re-install of vim and I can not get the symptoms to re-appear. That does not mean it is fix because the problem is rather intermittent, so time will tell. hopefully that will do it.

Actually the suggestion to look at bash seems good because it is doing some strange things also. For example, sometimes using the TAB key will not complete the file name--it just hangs and the cursor will not move at all. only a ctl-C will free it.  Again, this happens occasional so it is hard to debug. 

Again, thanks for all of the suggestions.

-Andres

---

