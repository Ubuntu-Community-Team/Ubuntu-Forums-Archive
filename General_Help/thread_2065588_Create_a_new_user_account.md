---
title: "Create a new user account"
date: 2012-10-02
forum: General Help
---

### Post by Zeppeliner on 2012-10-02
Hi 

   I am using ubuntu 12.04. I have to install an astronomical software called IRAF on my laptop. The installation process requires the creation of a user account called iraf. I attach the instructions below.

Use System>Administration>Users and Groups to create an account with username "iraf", real name "IRAF Maintenance", home directory "/iraf/iraf/local", shell "/bin/tcsh", and a secure password. Be sure to grant admin privilege to this account. For sudo commands here on, use this password. An easy way to avoid confusion is to assign the same password to this account as to your other sysadmin account.

   I am trying to create the account from the system> > Users and Groups. How can i set the home directory under /iraf/iraf/local? The command there creates home/iraf. Also how will is set shell as /bin/tcsh?


    Thanx a lot for your help.

---

### Post by Statia on 2012-10-02
Create a symlink from /home/iraf to /iraf/iraf/local or edit /etc/passwd.
Install tcsh with sudo apt-get install tcsh , then you should be able to set it as shell in the GUI, otherwise edit /etc/passwd to set the shell there.

---

### Post by jerrrys on 2012-10-02
Hi Zeppeliner, welcome to the forums :)

First I do not use this program and wouldn't know what to do with it if I managed to get it installed.  There may be a problem running it on 12o4, doesn't look like its been upgraded lately.  If you can't get it installed on 12o4 you could back up to 10o4.  The big difference between the two is gnome2 (10o4) and gnome3 (12o4).  Just throwing this out there.

Good luck

[http://www.aavso.org/photometry-course](http://www.aavso.org/photometry-course)

---

### Post by Zeppeliner on 2012-10-04
Thanx a lot Jerrys

    This IRAF installation was so simple!!!

---

### Post by jerrrys on 2012-10-04
Congratulations  :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by jbullis on 2013-04-10
Hey guys, I am new to the forums, new to linux and new to the world if IRAF...so im hoping this will be and easy (albeit dumb) question. I am in the process of trying to install and i am running into issues. I have been able to create the new user, but the instructions I have are telling me to use the setenv command on the folder where these files are? (setenv iraf /iraf/iraf) Ubuntu then tells me I have no setenv command. I have installed the tcsh software package, but still get the same response. Any suggestions?

---

