---
title: "Giving Myself Permission To Save My Own Files"
date: 2009-08-30
forum: General Help
---

### Post by DocHolliday2006 on 2009-08-30
Hey. So my computers's mobo died and I'm not replacing it. I need to get several small files off my hard drive.

What I did was find an old working computer and hook up my hard drive to it. 

When I do that it won't boot. Gives me some command prompt which my newbie eyes can not understand. 

So I made a bootable Ubuntu install disk,opened ubuntu that way, and now want to move my files to my USB stick. 

The problem is it says I don't even have permission to view the folder the files are in, which means I can't move them.

How can I, with as explicit directions for a newbie, gain permission or otherwise move the files to my USB stick.

Thanks.

---

### Post by gldearman on 2009-08-30
From the LiveCD, you should have permission to do about everything.

But, try this

Open the terminal.

Type:

```
sudo nautilus --browser
```

That will open a File Browser window, to which you should be accustomed.  But it will do it with root access, so you should have superuser powers.

I was pretty sure a File Browser window from the LiveCD already had root powers, but this is worth a try.

Remember that superuser powers can be dangerous.  But this computer is already shot, so how much damage can you possibly do?

If this fails, you will have to change ownership on the old drive.  We'll get to that if we have to.

---

### Post by SoftwareExplorer on 2009-08-30
What if, while you are booted in the liveCD, you Go Alt+F2 and put ```
gksudo nautilus
``` and hit run. Then it should let you save files. We will have to make them belong to your user on wherever you are restoring to, but I can help you with that :)

---

### Post by tgeer43 on 2009-08-30
This would probably be the easiest way for a newbie as it doesn't involve using the command line. It assumes that you have internet connectivity when booting from the Ubuntu CD.


[LIST]
[*]Go to System->Administration->Synaptic Package Manager. In the search box enter: nautilus-gksu
[*]In the search results right-click the nautilus-gksu package and select 'Mark for installation' then click on the apply button (green checkmark).
[*]Now use the graphical file manager to browse to the CD's /media directory. Find the folder that corresponds to the hard drive in question. Right click on it and select 'Open as administrator'. Now do the same for the folder that corresponds to your USB drive.
[/LIST]
You've now opened up two new nautilus file manager windows with which you should be able to drag and drop files from the HD to the USB without any permission issues as you are currently operating as root.

Hope this helps,

tgeer

[edit] Oops, two people already beat me to it while I was typing with even easier methods.

---

### Post by DocHolliday2006 on 2009-08-30
That did it! Thanks. 

-Andrew

> **gldearman said:**
> From the LiveCD, you should have permission to do about everything.

But, try this

Open the terminal.

Type:

```
sudo nautilus --browser
```

That will open a File Browser window, to which you should be accustomed.  But it will do it with root access, so you should have superuser powers.

I was pretty sure a File Browser window from the LiveCD already had root powers, but this is worth a try.

Remember that superuser powers can be dangerous.  But this computer is already shot, so how much damage can you possibly do?

If this fails, you will have to change ownership on the old drive.  We'll get to that if we have to.

---

