---
title: "Permision denied when using cp command"
date: 2011-04-23
forum: General Help
---

### Post by Victor43 on 2011-04-23
Hello all.

I've done a fresh install of Ubuntu 9.04 and tried to create a folder using the File Brower went to my user account and proceeded to create a directory. Then when trying to cp a file to this new directory I get permission denied. I checked the directory permissions and discovered that its owner was root not the user that I was signed in as.

So I had no choice but to enable the root account so I could copy the file I wanted. Why could I not have copied the file using the user that I was signed/logged int as without resorting to changing users to root.

I hope that its not a bug of some kind or maybe I did something weird during the install. Any thoughts or ideas would be appreciated because I would like to disbale the root account again.

Thanks in advance.

Victor

---

### Post by kiyop on 2011-04-23
Did you open nautilus or some file manager with "sudo" or "gksu", like the following?
```
sudo nautilus
gksu nautilus
```When nautilus is executed with sudo or gksu, the root privilege is used.

cf) you had better use "gksu" instead of "sudo" in executing graphical applications like nautilus.

...Oh! Typing speed of Demus is faster than I. Please read DeMus's to change owner and permission. Thanks DeMus.

One thing to notice:
Not "[COLOR=red]S[/COLOR]udo" but "sudo"

Refer to
```
man chown
man chmod
```

---

### Post by DeMus on 2011-04-23
> **Victor43 said:**
> Hello all.

I've done a fresh install of Ubuntu 9.04 and tried to create a folder using the File Brower went to my user account and proceeded to create a directory. Then when trying to cp a file to this new directory I get permission denied. I checked the directory permissions and discovered that its owner was root not the user that I was signed in as.

So I had no choice but to enable the root account so I could copy the file I wanted. Why could I not have copied the file using the user that I was signed/logged int as without resorting to changing users to root.

I hope that its not a bug of some kind or maybe I did something weird during the install. Any thoughts or ideas would be appreciated because I would like to disbale the root account again.

Thanks in advance.

Victor

Open a terminal. Type
```
Sudo chown -R username:username foldername
```
Instead of "username" you type your real username. The 1st one is your accountname, the 2nd is the group to which you belong.
This way you will become the owner. Instead of "foldername" you type ofcourse the name of the folder it concerns.
When you do an ```
ls -l
``` after this and you see the permissions are not good then use:
```
chmod -R 755 foldername
```
This way you, as user, will get Read, Write and eXecute permissions, while others can Read and eXecute.
Hope this helped you.

---

### Post by yetiman64 on 2011-04-23
> **Victor43 said:**
> Hello all.

I've done a fresh install of **Ubuntu 9.04** and tried to create a folder using the File Brower went to my user account and proceeded to create a directory. Then when trying to cp a file to this new directory I get permission denied. I checked the directory permissions and discovered that its owner was root not the user that I was signed in as.

So I had no choice but to enable the root account so I could copy the file I wanted. Why could I not have copied the file using the user that I was signed/logged int as without resorting to changing users to root.

I hope that its not a bug of some kind or maybe I did something weird during the install. Any thoughts or ideas would be appreciated because I would like to disbale the root account again.

Thanks in advance.

Victor

Jaunty is "End Of Life", you won't get any security updates etc. for it.

Enabling the root account in Ubuntu is your choice but goes against the Canonical security model and is potentially dangerous (especially when using an out of date OS), please reconsider switching it off. Getting help here may be difficult for you if you don't switch it off (Forum rules). **Edit**: instructions for disabling root account are in the Rootsudo link below (just saw you mentioned you want it off).

Please read the Community documentation for Rootsudo. Link #4 in my sig.

To do what you want use the command "sudo" before the copy command to raise copy's privileges to that of root. Your user password set up when you did the install is what is used with sudo.

DO NOT use sudo with graphical apps, use gksudo or gksu. Graphical sudo section from the link mentioned above will explain why. Also DO NOT change ownership or permissions of system folders to that of a user, it is a good way to reduce security in your system or break it.

Please read [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Victor43 on 2011-04-23
Many thanks for all the replies. I'll take another try at it given all the suggestions. 

Victor

---

### Post by Victor43 on 2011-04-23
> **kiyop said:**
> Did you open nautilus or some file manager with "sudo" or "gksu", like the following?
```
sudo nautilus
gksu nautilus
```When nautilus is executed with sudo or gksu, the root privilege is used.

cf) you had better use "gksu" instead of "sudo" in executing graphical applications like nautilus.

...Oh! Typing speed of Demus is faster than I. Please read DeMus's to change owner and permission. Thanks DeMus.

One thing to notice:
Not "[COLOR=red]S[/COLOR]udo" but "sudo"

Refer to
```
man chown
man chmod
```

The only thing that I tried to do was using Terminal and then proceeding to the directory I wanted to copy the file from. From there I executed the command cp filename /mnt and then got the permission denied error. 

Thanks again

---

### Post by yetiman64 on 2011-04-23
> **Victor43 said:**
> The only thing that I tried to do was using Terminal and then proceeding to the directory I wanted to copy the file from. From there I executed the command cp filename /mnt and then got the permission denied error. 

Thanks again
Navigate to the directory with the file you want to copy (I'm keeping to the method you describe above) and issue the command,

```
sudo cp <filename> /mnt
``` this is because /mnt is owned by root (you will need to input your user password, note though it won't show as you input it in the terminal). In fact everything outside of your home directory is owned by root and normally you would be expected to write only to your home directory.

Another problem in this case is it is not normal to copy a file to that directory as it is used as a mounting point for other situations (chroots are one example that comes to mind).

If you wish to delete a file from that directory you will need to use sudo with the rm command to do so.

If you use nautilus as root to do copying/deleting to such a directory, please ensure you use gksudo or gksu as using sudo alone may render your install (in particular the desktop) unbootable. The file .ICEauthority can end up with the wrong permissions or in the root's ownership, not a nice situation. The command to use to get a root browser,

```
gksu nautilus.
``` also _if_ you use this command and your terminal doesn't return to a prompt on closing nautilus use the keyboard combination CTRL + C to get it back.

Good luck from yetiman64.

---

### Post by kiyop on 2011-04-23
To understand what is the cause of the problem, see the above [#7]("http://ubuntuforums.org/showthread.php?p=10711849").

Judging from your post #1:
> **Victor43 at #1 said:**
> 
I've done a fresh install of Ubuntu 9.04 and tried to create a folder using the File Brower went to my user account and proceeded to create a directory. Then when trying to cp a file to this new directory I get permission denied.

I could not guess that you tried to copy file into /mnt, because you wrote "create a folder"("create a directory") and "cp to this new directory". I guessed that you (with your user account) created a directory in a directory your user account have whole privilege.

Thanks, [yetiman64]("http://ubuntuforums.org/member.php?u=1043255")

---

