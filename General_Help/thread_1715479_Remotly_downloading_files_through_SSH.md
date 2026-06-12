---
title: "Remotly downloading files through SSH"
date: 2011-03-27
forum: General Help
---

### Post by Rikeshar on 2011-03-27
Hello everyone. I need help figuring out how to set up a script to log on to a server through SSH, copy file from the server to the local machine, and then run a script on the downloaded file.

More specifically, I've got a minecraft sever that is run on ubuntu. I know that I can do

# ssh username@ipaddress

to log on to the server through the termial. After this it asks me for a password. Once I type in the password I have access to the directories on the server. How can I set up a script to log on to the server and enter password? Once I do this, how do I automate it to copy a file from that server to ~/Desktop ? If I can do this, I have a script that will run from there.

Any help would be appreciated!

*EDIT* 
I've learned that I can do 
scp -r remoteuser@remotebox:/remote/directory /local/directory to copy files from a server to my local machine, but it still asks me for the server password. how do I make it so that the password is automatically entered?

---

### Post by papibe on 2011-03-27
You can skip the use of passwords, and enable Public Key Authentication. Check this [tutorial]("http://principialabs.com/beginning-ssh-on-ubuntu/").

Once that is working, you can use several programs to copy files, like scp (in tutorial), sftp, or even rsync over ssh.

Good Luck!

---

### Post by Rikeshar on 2011-03-30
Works like a charm. Thanks for the help.

---

