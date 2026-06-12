---
title: "Empty Trash command for /.Trash folder?"
date: 2010-08-28
forum: General Help
---

### Post by ProcyonSJJ on 2010-08-28
Hi everyone.  Apologies all around if this has been asked/answered but I searched for a solution before posting to no avail.

Simply put, I mount /home on a logical partition.  Files and directories that I trash from here go nicely into the recycle bin, and I can right click on it and choose "Empty Trash" with no problem.  Files off of the root directory in directories that I "own" (i.e. /mydir/*) do not play as nicely.  I went ahead and followed instructions from another post, namely:

```

sudo mkdir /.Trash
sudo chmod 1777 /.Trash

```

And after trashing some files from /mydir, there is indeed a subdirectory with my uid (1000) and files that I trash from /mydir are going in there.  However, the recycle bin on my desktop remains empty, and the only method I have for deleting said files is by deleting them from the /.Trash/1000 folders through the command line.

So my question is: Is there anyway that I can trash files from /mydir, see them appear on the desktop recycle bin, and empty the trash without the need to rm them directly through the command line?  Not sure if it will help, but here is my fstab:

```

# / was on /dev/sda1 during installation
UUID=4129f389-92be-459e-8bbc-928c1440f718 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=6a30914d-04a3-4b03-85bd-2bf16a68a41a /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=f388cf04-bbd6-4bf9-9d69-0778b0f158fd none            swap    sw              0       0

```

Thanks very much for any help.

---

### Post by Ocxic on 2010-08-28
The trash that appears in your menu bar is only for "~/.Trash-UID" (UID is your user ID)

thus /.Trash will not do anything to that applet. 

I think if you bind /.Trash to ~/.Trash-UID it will do what you want.

"sudo mount --bind /.Trash ~/.Trash-UID"   (if you type "~/.Trash" then it hit the TAB key it will auto-complete for you.

---

### Post by kerry_s on 2010-08-28
1. you should not have folders/files out side your /home/you. why would you do that?

2. user trash is in ~/.local/share/Trash

simply put there is no reason to have user folders/files outside of a users /home/*, if it's sharing you need there's system-> preferences-> personal file sharing. 
why are you trying to compromise the security of the linux file tree?

---

### Post by ProcyonSJJ on 2010-08-28
@kerry_s: Fair question, I wanted to have a development environment outside of my home directory that not just myself, but other users on my system could have read/write access to, without necessarily giving everyone read/write access to the contents of my home directory.  Having a general repository outside of /home seemed like a simple solution.  If there is a better means of accomplishing this, by all means, I would love to know.  Along these lines, is there a recommended solution for having a community folder of media files (e.g. photos, music, movies, etc.)?  Would one create a home directory for these that is accessible to everyone?  And if so, would these files properly go to the correct trash cans?  Thanks.

---

### Post by kerry_s on 2010-08-28
i understand, sorry a little tired.

i'm a whole lota rusty on sharing.

i think what you would first do is create a group, say "developers", make sure the users you want access are in that group(use system-> administration-> users & groups to make)

then you create say /home/develop owned by the developers group with read/write. that should allow easy access, but still be safe. i'm not sure about how the trash worked, but i think it was via user, for example user 1 empties the trash, it would use there trash, then if user 2 used the trash it would use his trash. does that make since? lol

sorry, things change so fast in linux you can never really keep up.

---

### Post by kerry_s on 2010-08-28
looks like the setting is already in nautilus.
open /home as root(gksudo nautilus /home)
right click & create a folder
right click the folder-> sharing options

follow the directions from there.

when you use "move to trash" it go's to your trash.

---

### Post by ProcyonSJJ on 2010-08-28
Interesting, I only ever thought of the Sharing Options as a network feature (a la Windoze).  Thanks for the suggestion kerry_s, I'll give it a try.

---

### Post by kerry_s on 2010-08-28
> **ProcyonSJJ said:**
> Interesting, I only ever thought of the Sharing Options as a network feature (a la Windoze).  Thanks for the suggestion kerry_s, I'll give it a try.

i was thinking that to, that might be what the second option is for, but i didn't test that.

---

