---
title: "Error upon start up."
date: 2009-09-26
forum: General Help
---

### Post by Son of MaxVK on 2009-09-26
I recently tried to install steam onto ubuntu, it worked but I had to install a few new fonts to get it to work correctly. I have done that now and it is working fine but now I get an error upon start up:

If I could get a screen shot I would but I can't at the point this error shows.
> 
User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be allowed by user and have 644 permissions. User's $HOME directory must be owned by user and not written by other users.

I have totally no idea how to fix this or where to start looking for help other than here. Any help appreciated!

---

### Post by LoloftheRings on 2009-09-26
Looks like something went wrong and you altered your home permissions.
press Control-Alt-F1 and logon with your normal user account. Now execute this command to restore file permissions on your user home.

```
chmod -R 744 /home/yourusername
#check if you don't get any errors, if not, execute the following command to logout of the shell
exit
```

Now, switch back to the graphical environment by pressing Control-Alt-F7

for more information, see this turorial:
[http://ubuntuforums.org/showthread.php?p=6161267](http://ubuntuforums.org/showthread.php?p=6161267)

---

