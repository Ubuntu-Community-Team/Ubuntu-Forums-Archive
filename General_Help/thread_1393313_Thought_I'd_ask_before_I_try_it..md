---
title: "Thought I'd ask before I try it."
date: 2010-01-29
forum: General Help
---

### Post by Silvertones on 2010-01-29
My install is Wubi with Win XP. I use Thunderbird for email. I mostly use UBUNTU now for all Internet. What I normally do is copy the contents of the TB profile in Ubuntu to the TB profile in Windows. Just copy and paste into the appropriate folder in the "host" folder. Now TB is the same in Windows as in UBUNTU. My question is this:
In Ubuntu why wouldn't it work to change the default folder for TB to the TB profile folder for Windows that lives in the "host" folder. That would keep things synced at all times.
The reason I want to do this is I had a vid proplem with Ubuntu and of course couldn't get to the most recent emails. I back up once a week.
Is anyone doing this?

---

### Post by sgage on 2010-01-29
That's what I've been doing for years :-)

Actually, I config my Linux TB to point to the mail store folder on the Windows side, and symlink the Windows abook.mab to my Linux TB profile.

I do the same sort of thing with Firefox - I symlink my bookmarks database and such to the Linux profile. Everything synchronized, no problem!

[edited to add: make sure to run your symlinks in the right direction!]

---

### Post by Silvertones on 2010-01-29
Ah that's right. When I copy and paste the whole profile then everything gets synced however if I do it they way I described only the MAIL will get synced.
What is symlink?

---

### Post by Vaphell on 2010-01-29
symlink = symbolic link, it is a virtual object pointing at some other real object (file, directory) located somewhere else.
Let's say you have in your home symlink to /some/other/dir/far/far/away named mydir
cd ~/mydir (~ = home dir) will go to the target dir (/some/other/dir/far/far/away) without the need to enter the whole physical path.
When you create symlink to the windows thunderbird files in ubuntu configs, ubuntu tb teleports to the win tb and operates there.



read about ln command (ln --help in terminal)
don't forget -s parameter to create symlink, otherwise you'll create hardlink which is a real bond between shortcut and the target dir - delete would remove both, while symlink can be safely deleted without any harm for its target dir.

---

### Post by Robster2 on 2010-01-29
Short answer is - if you can access the files from Ubuntu go for it.

I don't use wubi, but I think you will find what you need here.

[http://ubuntuforums.org/archive/index.php/t-462379.html](http://ubuntuforums.org/archive/index.php/t-462379.html)

You will something about creating a FAT32 partition this old information. The NTFS Configuration Tool  (In the software manager- bottom of the application menu)  allows you to write directly to the Windows partition.

---

### Post by Silvertones on 2010-01-29
Because I use Wubi it's easier to just drag and drop the Ubuntu profile into the Windows profile.

---

