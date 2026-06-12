---
title: "Ubuntu 11.10 refusing to boot after update"
date: 2011-12-05
forum: General Help
---

### Post by interacter on 2011-12-05
Hi all

Yesterday I updated Ubuntu using the system update tool.

After this, everything stopped.

It was hanging on "Checking Battery Status" (it's a desktop!) so I had a look around and it appeared to be a graphics driver issue.

So I tried everything I could find (using my phone!) - reinstalling lightdm, reinstalling the gnome power manager.

Nothing.

After a few attempts, it then started to hang after a load of system checks.  It would produce a list about 25 items long, the only fail on there being the automatic error config (I think that's what it was).

So this morning I got it to boot from a live USB and tried the suggestions in this thread: [http://ubuntuforums.org/showthread.php?t=1863679](http://ubuntuforums.org/showthread.php?t=1863679) - this fixed issues before.

Plenty of updates downloaded, but now it stops at the splash screen.  Under "Ubuntu" all of the little dots are purple (as opposed to white and scrolling).

I get no other error messages.

Ctrl+Alt+Del and Ctrl+Alt+F1 gets me a terminal but I can't type anything into it.

Can you give me any advice?  I really need to get at one email (just one!!!) that's downloaded onto the system...

Thanks, in advance.

Neil

---

### Post by BC59 on 2011-12-05
As I understood the Upgrade went wrong and this is not news. I don't know why they continue to offer this possibility.

But if you boot from a USB you have access to everything in your computer (speaking about email). So you can backup and reinstall.
I would suggest you to format the /Home folder because you will have trouble again. 

So, boot from a USB and depends on what type of email you use. If it was Thunderbird, you copy the folder /.thunderbird in Home and that's it. When you reinstall the system, you paste the folder to Home and your account is working directly.
With Evolution is something like this. Copy the /.evolution, /.gconf/apps/evolution/ and ~/.gnome2_private/Evolution folders. Then restore them to start again your account.
To backup Firefox do the same and copy the /.firefox folder.

---

### Post by interacter on 2011-12-05
Thanks for your advice - I was hoping it wouldn't come to that!!!

I also need to pull files off the PC before I wipe it.  However, I can't seem to find them.  

I'm searching for the folder name in the explorer window, but it isn't coming up with any...  There are 2 lots - one would have been in the Documents section on my old profile and the other folder on the desktop.

Any ideas?

Also, when I search for Thunderbird, I'm getting about 10 different folders.  Really not sure which is which.

Is there a good way to tell?

Thanks!

---

### Post by BC59 on 2011-12-05
To find your own /Home partition you have to look to Nautilus left panel and to the Devices. Is one of the devices you see there. Open the file system and ask to find Home and then your user name and home again. Then push CTRL+H to see the hidden files.
If you can do the backup of everything then we could search for a solution.

---

### Post by interacter on 2011-12-05
Brilliant!  I have now copied everything from my old profile - HOWEVER I can't get into some of the folders as it says that I don't have the right permission?

Same for the .thunderbird folder - how can I get around this to ensure that everything I need is there?

---

### Post by interacter on 2011-12-05
The folder properties say user 1000 for each of these folders that I can't get access to.

Is there any way of changing this?

---

### Post by BC59 on 2011-12-05
Yes. Run from a terminal:

```
gksudo nautilus
```

and then you can copy everything. BUT after that the files copied they will belong to root, so you have to change permissions again with gksudo nautilus, right click properties, change permissions. But this is when you restore them to the new system.

---

### Post by interacter on 2011-12-06
You're a marvel - I've managed to  get in far enough to copy everything out...

Here's hoping I can sort the permissions on the way back in as easily!

---

### Post by BC59 on 2011-12-06
The best way to have a dependable computer is to fresh install the system. And the most recommended way to make your partitions is to have a partition for the system ~/ about 6GB a swap equal to your RAM and a separate ~/Home partition for your personal Data. This way when you have problems like that, you format only ~/ and the ~/Home directory with your data stays intact.

---

### Post by kio_http on 2011-12-06
Failed upgrades can often be solved like this


When it hangs press ALT + CTRL + F1

Login

type

```
sudo apt-get install -f
```

---

### Post by didinium on 2011-12-06
He said he already tried that.

---

