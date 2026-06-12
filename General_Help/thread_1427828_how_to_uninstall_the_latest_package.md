---
title: "how to uninstall the latest package?"
date: 2010-03-12
forum: General Help
---

### Post by siukimfong on 2010-03-12
I use the command ```
dpkg -l
``` to see all the packages installed in my Ubuntu. The question is that I want to uninstall the latest package but there's no date in the package list made by the command "dpkg -l". so how can I do that?

---

### Post by DawieS on 2010-03-12
Open a file browser. Navigate to  the "**/var/cache/apt/archives**" folder. You will now see a list of applications (.deb) files.

Click on the "**View - Visible Columns**" tab. Select "**Date Accessed**". A new column will appear showing the dates which these files were last accessed.

Click on the "**Date Accessed**" tab to sort the list from last to first accessed.

Now look through the list and decide which are the applications that you want to uninstall.:razz:

---

### Post by pastalavista on 2010-03-12
Or you can go-- System > Administration > Synaptic Package Manager | File > History 

as long as you installed it from a .deb package.. which is all dpkg handles.. (not binaries or executable shell scripts) Synaptic keeps track of it.

---

### Post by siukimfong on 2010-03-13
> **DawieS said:**
> Open a file browser. Navigate to  the "**/var/cache/apt/archives**" folder. You will now see a list of applications (.deb) files.

Click on the "**View - Visible Columns**" tab. Select "**Date Accessed**". A new column will appear showing the dates which these files were last accessed.

Click on the "**Date Accessed**" tab to sort the list from last to first accessed.

Now look through the list and decide which are the applications that you want to uninstall.:razz:

thanx. but it'll be better if commands could do that in case of no X-Window. An idea has come out that it can enter into the directory "**/var/cache/apt/archives**" , use "ls -l" to show the file information, find the latest package downloaded and then use another command to uninstall it. 

Am I right?

---

### Post by DawieS on 2010-03-14
> **siukimfong said:**
> thanx. but it'll be better if commands could do that in case of no X-Window. An idea has come out that it can enter into the directory "**/var/cache/apt/archives**" , use "ls -l" to show the file information, find the latest package downloaded and then use another command to uninstall it. 

Am I right?
You are right. The command "**ls -ltc**" will produce the same list, sorted in order of last to first accessed.

It is always easier (and faster) to click on the various options in an X environment. However, you can achieve the same by typing commands in a terminal. You must then be prepared to do a lot of typing (and reading the manual) of the various commands, and their options. You can expand your knowledge of the available commands by looking at the "**SEE ALSO**" section near the bottom of a manual page, to find related commands. You can scroll through the manual with the "**up**" and "**down**" keys, and quit the manual by pressing "**q**".

To learn more about the "**ls**" command, type "**man ls**" in a terminal. To learn more about installing/removing packages via a terminal, type "**man aptitude**" in a terminal.

If you are going to make extensive use of the terminal, it is useful to learn the shortcuts of doing things in the terminal. For example, by pressing the "**up**" arrow repeatedly, you can insert your previous commands in the command line, which you can then edit, and execute by pressing "**Enter**". Another example is to use "**^**" (shift 6) to substitute certain character strings: If your previous command was "**ls -lg**", and you type "**^g^t**" and "**Enter**", your new command will be "**ls -lt**".:grin:

---

