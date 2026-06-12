---
title: "Nautilus Desktop home folder view wont go away!"
date: 2009-08-07
forum: General Help
---

### Post by conorsulli on 2009-08-07
[IMG]http://lh3.ggpht.com/_pTXoX0TFemk/SnyU_ZRhxDI/AAAAAAAABKo/_ve0MCFeEk4/s800/Screenshotdesktop.png[/IMG]
Screenshot included if you don't feel like reading all the below..

Hey guys,
I just recently rescued my system from a very nasty user privileges hiccup where I was trying to move my home folder to a separate /home partition and eventually even root could modify the files.. I managed to fix the issue but now I have folder View activated on the desktop of my new home folder, Its cluttered and driving me mad!

I did have Ubuntu-tweak installed but didn't enable it through that or Gconf-editor..

The screenshot shows "Desktop_is_home_dir" unselected but yet all my icons are on there... I am able to disable the computer/Trash/Network icons through gconf however not the Home folder "Desktop_is_home_dir" activation.

At first I thought it was because I had mounted my new partition to show on the desktop (which is on ubuntu by default) was the reason however disabling this had no such luck.... They still showed just not my pen-drives etc.

The only thing that switches them off is if I disable nautilus drawing the background completely, and then I cannot right-click to change the background , add desktop shortcuts etc vanish also, so my  whole desktop becomes useless to me.

I also ran "sudo apt-get remove" on ubuntu-tweak and nautilus, Further I ran "sudo apt-get purge" to remove configuration files and "sudo apt-get clean". I deleted my user/.nautilus file and before reinstalling nautilus and checked that gconf-editor was editing the "user/.gconf/apps/nautilus/preferences/..." xml file correctly..(which it had)...

I'm completely bewildered by it to be honest and google prooved not to be my friend on this occasion, I could only find how to enable it :(. I'm all out of Ideas:confused:  and would love the help anyone could suggest. .

Cheers..........](*,)

---

### Post by burmanabhay88 on 2009-08-07
goto terminal.
And give me the result of this command
```
$HOME
```

Don't forget to write the extra dollar sign!!!
Okay...

The dollar here is not part of the terminal
On screen your command will look something like
> conorasulli@conorsulli-laptop:~$ $HOME

---

### Post by conorsulli on 2009-08-07
Well the output was 
"bash: /home/conor: is a directory"......:-(.

Thank you for your quick response by the way.

---

### Post by burmanabhay88 on 2009-08-07
can you give a screen shot of your problem????

---

### Post by conorsulli on 2009-08-07
Update: Screenshot, for got to attach it last time.

---

### Post by mcduck on 2009-08-07
Edit ~/.config/user-dirs.dirs and set "XDG_DESKTOP_DIR" to "$HOME/Desktop".

---

### Post by conorsulli on 2009-08-07
> **mcduck said:**
> Edit ~/.config/user-dirs.dirs and set "XDG_DESKTOP_DIR" to "$HOME/Desktop".

THANKS!!:popcorn:

This solved the issue, remember I had it set to home in the ubuntu tweak gui version, did a reboot and all was back to normal.

---

