---
title: "sudo chown -R yourname directory"
date: 2012-05-12
forum: General Help
---

### Post by carmenin87 on 2012-05-12
I have a shared folder on my Ubuntu server into which I copy movies and other folders across the network.

These movies and folders that are being copied are moved from Windows 7 computers and other Ubuntu computers.  Often, I find once the files/folders get onto the Ubuntu server, they have a padlock on them and I have to run the below command to gain access to them

sudo chown -R yourname directory

I'm doing this so often now that I was wondering, is there a way to create a batch file with this command so that I can just double click on it and it would automatically run the command on the folder and all subfolders.

My username is user
The directory where I am saving all the files/folders is simply called share.

Thank you

---

### Post by sudodus on 2012-05-12
I suggest that you add the following alias into ~/.bashrc

```
alias clown="sudo chown -R $USER share"
```

So edit your .bashrc file and (for clarity) add the line near the other alias lines. Use double-quotes because you want the shell variable $USER to expand into your user name.

Maybe you should use the full path to the folder, for example
/home/$USER/share

---

