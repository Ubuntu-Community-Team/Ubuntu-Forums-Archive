---
title: "How to add autoupdate to my script"
date: 2011-03-10
forum: General Help
---

### Post by satya164 on 2011-03-10
My dear bros, I've made a little script which helps to install codecs, flash, wine etc. in Fedora. They are not easy for fedora users as just doing a apt-get install in Ubuntu. Project page is here - [fedorautils.sf.net/]("http://fedorautils.sourceforge.net/")

But I want to add a autoupdate feature to it. The script should be able to check the sourceforge site and notify if an update is available. i think this is a must have feature fr the script as many things are fixed and features added eventually. So if someone has something wrong in his version of the script he can try the new one to see if the problem has been fixed.

Also i want to add a logging feature. can I print all the terminal output to a file? It would help me a lot to see what went wrong.

Though it is not Ubuntu related, your scripting knowledge could help me and I would be grateful for that. That is the reason I posted here.

---

### Post by deeZee on 2011-03-10
I can't help you with the autoupdate, but if you want to redirect the output to a file use > or >>.  

For example, ```
ls > directoryList.txt
``` would redirect the output of the ls command to a file named directoryList.txt, which would be created in your current directory.

If you want to add the output to the same file each time you run a command then type in```
ls >> directoryList.txt
``` which would simply add the new output to your existing directoyList.txt file (or create the file in your current directory if it didn't already exist.)

---

### Post by satya164 on 2011-03-11
> **deeZee said:**
> I can't help you with the autoupdate, but if you want to redirect the output to a file use > or >>.  

For example, ```
ls > directoryList.txt
``` would redirect the output of the ls command to a file named directoryList.txt, which would be created in your current directory.

If you want to add the output to the same file each time you run a command then type in```
ls >> directoryList.txt
``` which would simply add the new output to your existing directoyList.txt file (or create the file in your current directory if it didn't already exist.)
Thanks. will try:)

---

