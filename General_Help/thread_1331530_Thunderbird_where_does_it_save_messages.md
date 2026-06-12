---
title: "Thunderbird where does it save messages?"
date: 2009-11-19
forum: General Help
---

### Post by daldude on 2009-11-19
Where does Thunderbird save all the messages from the Inbox and Sent folders?
It would be nice to be able to backup  all your messages in the case of having to reinstall Ubuntu or do a fresh upgrade from one version to another.

---

### Post by Irihapeti on 2009-11-19
Thunderbird profiles (including messages) are in ~/.thunderbird. (~ is your home directory) You'll need to have "show hidden files" on in order to find it.

---

### Post by ricardo.gloe on 2009-11-19
Thunderbird saves your profile (along with all your messages, etc.) in /home/xxxuserxxx/.mozilla-thunderbird. 

Backing this folder up and then copying it back after a clean install does exactly what you're saying.

---

### Post by daldude on 2009-11-19
> **ricardo.gloe said:**
> Thunderbird saves your profile (along with all your messages, etc.) in /home/xxxuserxxx/.mozilla-thunderbird. 

Backing this folder up and then copying it back after a clean install does exactly what you're saying.


Ok I think I found it. The Folder was called Mozilla-thunderbird which seems to be the right one because it had more sub folders in it one of which looked like my e-mail addresses. 
You would not happen to know where the Windows XP version of Thunderbird saves my messages and can I copy from XP Thunderbird to Ubuntu Thunderbird so I can have all the messages I backup in XP avalible in Ubuntu too? I have a ptogram that runs in Windows that backsup all my E-mail Messages in one easy step without having to know where the messages arre saved.
I don't understand why Thunderbird still does not have  Backup and Restore Messages Option.

Thanks

---

### Post by Irihapeti on 2009-11-19
You can install ImportExportTools extension to backup and restore messages. It's available from [https://nic-nac-project.org/~kaosmos/index-en.html](https://nic-nac-project.org/~kaosmos/index-en.html)

---

### Post by VanillaMozilla on 2009-11-19
> **daldude said:**
> You would not happen to know where the Windows XP version of Thunderbird saves my messages... 
[http://kb.mozillazine.org/Profile_folder_-_Thunderbird](http://kb.mozillazine.org/Profile_folder_-_Thunderbird)
Note that you can have Windows and Linux versions share a profile if you want.

---

