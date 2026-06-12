---
title: "Rsync, cron job without placing in root directory"
date: 2011-09-05
forum: General Help
---

### Post by spec36 on 2011-09-05
I am setting up a computer for two people who need to transfer a folder from one main user to another user. 

So for example user #1 will be the primary editor of files in this directory and then I want to run a cron job about every 10 minutes to update any changes to another users directory.

To do this I was going to write a .sh script with rsync and a cron job to auto run the task. Problem is I need to automate without having to enter a password. I know this can be done by placing the .sh script in the root directory, but I don't want to activate the root user, just so the users will not need to remember the extra password.

Any help on how to auto run this from the primary user #1 account would be much appreciated.

Thanks,

---

### Post by Hugh971 on 2011-09-05
How are you setting up the cron job? I run an rsync script on my server with cron and I set it up by running 

```
sudo crontab -e
```

---

### Post by papibe on 2011-09-05
Which password are you referring to?

If I have to guess, you are using rsync over ssh, so you have to enter the password to create the connection. Is that right?

For that situation you may create public authentication keys. If you choose an empty pass phrase you could fully automate your rsync scripts. You wouldn't need to run the script as root. Check [this]("http://principialabs.com/beginning-ssh-on-ubuntu/") guide to do that.

There is an disadvantage of that, user#1 could connect passwordless to user#2's machine. You have to evaluate if that is acceptable or not.

Now, there's a way around this. Export the user#2's destination using NFS. Mount that directory in user#1's machine. You can mount it in a place that don't bother user#1, like /media/.Proyect/ or something of your preference.

This way you can use rsync running locally mirroring /home/user1/source to /media/.Proyect

If that helps?
Regards.

---

