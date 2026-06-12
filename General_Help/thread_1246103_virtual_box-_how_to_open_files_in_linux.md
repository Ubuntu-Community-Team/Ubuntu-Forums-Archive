---
title: "virtual box- how to open files in linux?"
date: 2009-08-21
forum: General Help
---

### Post by abhilashm86 on 2009-08-21
i installed sun virtualbox, now i want to access hard disk and files on my computer, but windows shows only C drive....
i have set some shared folders in virtualbox->settings, but i can't open that in windows? 
please tell easiest method of opening files in virtualbox.........

---

### Post by howefield on 2009-08-21
> **abhilashm86 said:**
> please tell easiest method of opening files in virtualbox.........

You could try using Bridged Adapter in the Virtualbox network settings for your virtual machine. That will allow the virtual machine to access your local network including the host machine.

---

### Post by abhilashm86 on 2009-08-21
so now in settings network1 should be bridged adapter? i'm trying this....
ok one more simple problem, if i start working on virtual machine windows, how to come back to ubuntu without shutdown the virtual machine winodws?

---

### Post by mjwalfredo on 2009-08-21
> **abhilashm86 said:**
> i installed sun virtualbox, now i want to access hard disk and files on my computer, but windows shows only C drive....
i have set some shared folders in virtualbox->settings, but i can't open that in windows? 
please tell easiest method of opening files in virtualbox.........

When you share a directory from the host machine, you can access it in your Windows guest by the UNC pathname.  The machine name will be "vboxsvr".  Say you gave your share the name of myshare, the UNC you would use for your drive mapping would be "\\vboxsvr\myshare".

You shouldn't need to change your networking setup to get this to work.  It works perfectly fine for me in NAT mode.

Also, I am assuming you are in full screen mode and that is why you can't switch back to Ubuntu.  If you press the host key (usually Right Ctrl) + F, that should put your virtual machine in windowed mode.  Press Right Ctrl + F again and you will go back to fullscreen.

---

### Post by howefield on 2009-08-21
> **abhilashm86 said:**
> ...how to come back to ubuntu without shutdown the virtual machine winodws?

Are you working in full screen mode with your virtual machine ? (you cannot see your Ubuntu desktop).

Use the keyboard shortcut to another workspace ? Or come out of full screen mode - it is only a key press away ctrl + f

Run dual monitors....

---

### Post by abhilashm86 on 2009-08-21
> **mjwalfredo said:**
> When you share a directory from the host machine, you can access it in your Windows guest by the UNC pathname.  The machine name will be "vboxsvr".  Say you gave your share the name of myshare, the UNC you would use for your drive mapping would be "\\vboxsvr\myshare".

You shouldn't need to change your networking setup to get this to work.  It works perfectly fine for me in NAT mode.

Also, I am assuming you are in full screen mode and that is why you can't switch back to Ubuntu.  If you press the host key (usually Right Ctrl) + F, that should put your virtual machine in windowed mode.  Press Right Ctrl + F again and you will go back to fullscreen.

now i'm able to switch between two OS:), now 
i have shared whole /home/abhilash in shrare settings, winodws says \\vboxsvr\abhilash, error was ```

network path not found
```
how to set it

---

### Post by abhilashm86 on 2009-08-21
> **howefield said:**
> Are you working in full screen mode with your virtual machine ? (you cannot see your Ubuntu desktop).

Use the keyboard shortcut to another workspace ? Or come out of full screen mode - it is only a key press away ctrl + f

Run dual monitors....

yup now its working!! yes thanks, i'll create a shortcut and moke it work on another workspace:)

---

### Post by abhilashm86 on 2009-08-21
can i try samba for sharing files in virtualbox?? will that work as i'm having host ubuntu and windows guest OS........

---

### Post by mjwalfredo on 2009-08-21
You can use Samba but VirtualBox's built-in sharing is pretty simple.  When you created the shared folder, did you specify a "Folder Name" that is different than the actually directory name?  If so, you need to use that "Folder Name" listed in the shared folder configuration panel rather than the actual directory name.

---

### Post by okmat on 2009-08-21
Hello there, you can connect all your virtualBox shared folders as Network Drives, that way you'll have a Letter assigned for each shared folder you wish to have in "My Computer".

On your windows virtual machine open My Computer, in the Tools menu look for "Map Network Drive...", click Browse for a folder and you should see a line that reads "VirtualBox Shared folders" expand it and you will see all VirtualBox Shared folders (due to some strange reason, sometimes you have to expand it twice in order to be able to click the OK button below).

Select the folder you want, click ok. After that, assign a drive letter, make shure "Reconnect at login" is checked and click finish. 
Now you should be able to access your VBox shared folders straight from "my computer"

Hope that helps

Cheers!

---

### Post by abhilashm86 on 2009-08-21
> **okmat said:**
> Hello there, you can connect all your virtualBox shared folders as Network Drives, that way you'll have a Letter assigned for each shared folder you wish to have in "My Computer".

On your windows virtual machine open My Computer, in the Tools menu look for "Map Network Drive...", click Browse for a folder and you should see a line that reads "VirtualBox Shared folders" expand it and you will see all VirtualBox Shared folders (due to some strange reason, sometimes you have to expand it twice in order to be able to click the OK button below).

Select the folder you want, click ok. After that, assign a drive letter, make shure "Reconnect at login" is checked and click finish. 
Now you should be able to access your VBox shared folders straight from "my computer"

Hope that helps

Cheers!
yes i had'nt named while sharing files in settings, now i'll try it, thanks:)

---

