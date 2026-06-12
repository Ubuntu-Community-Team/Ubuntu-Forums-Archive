---
title: "Program install problem"
date: 2009-08-19
forum: General Help
---

### Post by cmcanulty on 2009-08-19
I am so frustrated. I have tried to install numerous chess and go programs with synaptic or add/remove programs. They all install but with various errors.They won't work so I uninstalled all of them. Then I try to delete the files and it says I can't even though I am the only user. So I try to post in beginners forum and it says I don't have authorization to. I feel like giving up and back to windows.

---

### Post by credobyte on 2009-08-19
You are the only user, but - to get root privileges, you need to use sudo or gksudo ( for graphical stuff ).
Can you tell us more about these *mysterious errors* ?

---

### Post by approaching on 2009-08-19
Even if you never made another user on the system, there will always be other user accounts. in particular, there is the concept of root, which is the super user, the one who can do everything. you are not that user, don't log in as that user. that user is basically reserved for administrative commands and a few other things. if you want to delete those files that it says you don't have permissions for, do something along these lines (but please know what you are doing before you go and just delete files, because i can guess that you just want to remove an application, not delete them)

sudo rm -rf /the/directory/you/want/to/delete/ (never enter this "sudo rm -rf /" it will nuke your system)

to remove an application, try something like this:

sudo apt-get remove package-name

what are you trying to install? there is a chess game in the games directory already. are you doing the install via command line or the synaptic package manager?

---

### Post by cmcanulty on 2009-08-19
I uninstalled all of them but the files are still there and I want to delete, I thought Ubuntu should delete them when I uninstall ?

---

### Post by approaching on 2009-08-19
i believe that there is an option to "completely remove" rather than just uninstall. did you get what you wanted to install installed?

---

### Post by cmcanulty on 2009-08-19
OK I got the files deleted with the gksudo command that is so much easier than su! Thanks. I will try to install them again and write down the error messages but each time it is different and apparently there is no way to copy and paste them ? I am working constantly until Sun now so will update on this next week, thanks again

---

### Post by cmcanulty on 2009-08-20
Yes by using gksudo which I didn't really understand but it let me delete the leftover files, thanks

---

### Post by Copernicus1234 on 2009-08-20
Im not sure why gksudo lets you remove the files, but if using sudo, you have too options when removing files:

sudo apt-get remove <package> = uninstall the program but leave config files
sudo apt-get purge <package> = uninstall and remove config files

---

### Post by pedro_orange on 2009-08-20
> **Copernicus1234 said:**
> Im not sure why gksudo lets you remove the files, but if using sudo, you have too options when removing files:

sudo apt-get remove <package> = uninstall the program but leave config files
sudo apt-get purge <package> = uninstall and remove config files

I'm presuming he did:

```
gksudo nautilus
```

So he opened a nautilus session as su. So he could delete stuff. Gksudo is what you should use to open a graphical application as su. There are issues with profiles when opening things as sudo, so you should use gksudo.

---

### Post by cmcanulty on 2009-08-20
Yes I did do gksudo nautilus. Not sure why the files weren't deleted when I uninstalled the programs. PS I'm a she.

---

