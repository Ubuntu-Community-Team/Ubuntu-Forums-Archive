---
title: "What sort of UAC system does ubuntu use?"
date: 2010-03-19
forum: General Help
---

### Post by Simbachips on 2010-03-19
Been doing a little bit of research into vista's new UAC system that integrates more of a MAC style but still remaining somewhat a DAC system. The new hybrid is called MIC and works hand in hand with UIPI which works with integrated levels of the user and other objects to make vista more secure. My question to you is; what information can you give me about Ubuntu's UAC structure, that is similar to the information a gave you about vistas'? e.g. if it's a DAC or MAC, if DAC What makes it a DAC system? Same with MAC. 

I already know that Apparmor is the application equivalent to Vistas inbuilt UIPI.

---

### Post by Mighty_Joe on 2010-03-19
Linux (and Unix in general) has always had a system of users and permissions, so we really don't have a cool acronym for it.  
Ubuntu is unique among Linuxes in that one logs in as a "regular" user and then uses "sudo" with their own password to execute system commands (see [this article]("https://help.ubuntu.com/community/RootSudo")).  The other Linux flavors I've used have completely separate "regular" users and a root account.

---

### Post by sisco311 on 2010-03-19
This should answer your questions: [http://content.hccfl.edu/pollock/AUnix1/FilePermissions.htm](http://content.hccfl.edu/pollock/AUnix1/FilePermissions.htm)


The traditional Unix/Linux system of users, groups, and read-write-execute permissions is an example of DAC, but several MAC systems are available. i.e.: SELinux or AppArmor.

---

### Post by Simbachips on 2010-03-20
Thanks for the help, I came across what Mighty-Joe said about using a Sudo command to initiate a root user account. I read that this is not as secure as it may sound or that Linux in general is actually quite poor without any hardening techniques. If any one would like the article I would be happy to supply. sisco 311; that's some good reading, thanks.

---

