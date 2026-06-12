---
title: "Cant find Trash bin"
date: 2011-07-08
forum: General Help
---

### Post by kleinempfaenger on 2011-07-08
Hi,
I'm not able to delete files, because Xubuntu doesn't find the trash bin. An error message pops up, telling me that the bin couldnt be found or created. Some days ago I deleted some .trash and other hidden files from a USB-stick, maybe this is the reason.
How could I recover the bin?
Thanks, kl

---

### Post by JC Cheloven on 2011-07-08
Your trash should be at
/home/xyz/.local/share/Trash/

There are 2 folders there. The files you moved to the trash are in
/home/xyz/.local/share/Trash/files
And this one contains info about items moved to the trash
/home/xyz/.local/share/Trash/info

Where xyz is your username.
Perhaps if you recreate these directories everything could get normal again.

---

### Post by mikejonesey on 2011-07-08
to show it on your desktop;

```
gconf-editor
```
and you can select desktop icons in apps>nautilus>desktop

---

### Post by kleinempfaenger on 2011-07-09
Thank you very much for your help, but still I'm searching for the  mssing link. I found the folder, ~/.local/share/Trash (empty), but  xubuntu doesn't find it. When I open the bin from the desktop icon, the  direction is: "trash:///". Where is that? Is there a way to indicate in  the preferences where the trash should be moved? Would it be posible to  reinstall the trash package?
Thank you.

---

### Post by scooper77515 on 2011-07-09
> to show it on your desktop;

Code:
gconf-editor

and you can select desktop icons in apps>nautilus>desktop

I lost my trash can a couple days ago. Got an error on startup saying it could not be loaded, and I could delete it or not, I said delete. 

This worked for me, got my trash can back on desktop.

Thanks!

---

### Post by kleinempfaenger on 2011-07-10
Another tip from anybody? Still my trash folder doesn't work.
Could anybody tell me how to reinstall trash in xubuntu or link the trash can to the folder mentioned above? I can't even delete files definitely.
Please....
Greetings, kl

---

### Post by kleinempfaenger on 2011-07-10
Shift + Delete deletes files definitely, I found that out now. But waste bin still doesn't work.

---

### Post by Toz on 2011-07-10
Is the Thunar daemon running?```
ps -ef | grep Thunar | grep -v grep
```

If not, try starting it up and see if that fixes the problem:
```
Thunar --daemon
```

---

### Post by WorMzy on 2011-07-10
Do you have gvfs installed?

---

### Post by kleinempfaenger on 2011-07-11
Thanks again,

gvfs is installed.

Toz:
ps -ef | grep Thunar | grep -v grep
familia   1449  1359  0 12:49 ?        00:00:00 Thunar --sm-client-id 2d23ef068-8a77-4687-820f-67604d3e6d68 --daemon

I think it is running, isn't it?

Thunar --daemon
Nothing happened.

I think I will change back to Nautilus. I have too much problems with Thunar. Another problem is to disable previews, which is extremely difficult and doesnt really work. Some huge image files consume all my memory, generating previews I don't need.

-----

I changed default file-browser to Nautilus.
Waste bin also doesn't work, but it askes me to delete the files definitely, what is ok.

Folders on desktop (only those) still open with Thunar.

---

### Post by JC Cheloven on 2011-07-11
It could be the permissions for the Trash folder. You can check
```
ls -al ~/.local/share
ls -al ~/.local/share/Trash

``` (one at at time) to see if the permissions are read-write-excute for the owner (and that you're the owner of course).

Different subject: if you landed in Xubuntu looking for a lighter desktop, and for a reason or another it doesn't work for you, you may want to try  [Lubuntu]("http://www.lubuntu.net"). It's an even lighter desktop, perhaps too basical for some, but I quite like it.

---

### Post by kleinempfaenger on 2011-07-13
Thanks again. Yes, I was searching for a lighter alternative, because Unity consumes a lot of computer and human memory. Finally I got convinced that it's not that important which session, as Gnome is still running, but I like the typical Xubuntu bar at the bottom. Smart design.

After Playing around with different appeariences and changing between Gnome and Xubuntu sessions Trash folder works again. I don't know why. So this item is solved for me.

I was not able to get completely rid of Thunar. The folders on my desktop would open in Thunar, although I set Nautilus as default browser. Uninstall is not possible, as it completely uninstalls xfce-desktop too. I will start a new Thread about that point.

Greetings, kl

---

### Post by JC Cheloven on 2011-07-14
> **kleinempfaenger said:**
> ... Uninstall is not possible, as it completely uninstalls xfce-desktop too...
Just note: I think there's not such package as "xfce-desktop" in the ubuntu repository. Perhaps you mean ```
xubuntu-desktop
``` or ```
xfce4
```
Both are "meta packages" (is how they're named). Merely a list of dependencies used for convenience at the time of installing, but unistalling a meta package will NOT affect any of the real packages actually installed. In fact, it's usual to see in the instructions something like "you can safely remove this package if you don't want some of the programs".

So go ahead ;)

---

