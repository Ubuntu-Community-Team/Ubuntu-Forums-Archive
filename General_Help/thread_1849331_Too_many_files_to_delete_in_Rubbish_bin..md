---
title: "Too many files to delete in Rubbish bin."
date: 2011-09-24
forum: General Help
---

### Post by dchurch24 on 2011-09-24
Hi,

I've written some software that I've long forgotten that seems to be filling up a folder called "TVAutomation". If I try to do "ls" it simply hangs, if I right click the folder and delete it it goes to the Rubbish Bin. If I empty the Rubbish Bin, the timer dialog shows up on screen for about 30 seconds, then disappears, leaving the Rubbish Bin full still.

I cannot seem to get rid of this folder no matter what, and am constantly being told that "This PC has less than xxMB remaining".

How can I delete this folder and/or empty the Rubbish Bin?

---

### Post by 2F4U on 2011-09-24
What about rm -rf folder_name in a terminal? This deletes the folder and all files in it without putting it in the trash.

---

### Post by thefasterblueone on 2011-09-24
rm -rf /path/to/the/folder #will delete folder
be very carefull!
rm -rf / path/to/the/folder #will delete every file on your system! See the space between / and path? The shell sees that command as
rm -rf /
because of that space.

---

### Post by dchurch24 on 2011-09-24
Hi, thanks for that. I had tried that too, but it simply hangs. I've left it doing it for around 10 hours in case it really was deleting but ultimately the folder was still there, intact with it's files.

---

### Post by hakermania on 2011-09-24
> **dchurch24 said:**
> Hi, thanks for that. I had tried that too, but it simply hangs. I've left it doing it for around 10 hours in case it really was deleting but ultimately the folder was still there, intact with it's files.
how many files are there? Just curious!

---

### Post by dchurch24 on 2011-09-24
I'm not sure, it won't let me do a 'ls' on that directory without hanging.

If I do, "Properties" on the folder, it simply does nothing.

My guess is in the hundreds of thousands.

---

### Post by HermanAB on 2011-09-24
Howdy,

It may be blocked by a file or directory that is not owned by you.  So try doing it as root:

sudo rm -rf /path/to/folder

---

### Post by dino99 on 2011-09-24
then try to split the deletion using either a->z* or by .extension

so nautilus or gnome-commander cant open that folder ? Can you cd to that folder ?

---

### Post by hwttdz on 2011-09-24
I oftentimes work with a large number of files so hopefully I can give you some helpful tips.  

1) find is more reliable than ls when it comes to deleting a large number of files

2) xargs can be used to divy up a command that would otherwise fail due to exceeding the maximum number of arguments allowed by the shell

so I'd probably start with something along the lines of

```
cd foldername
find . -xdev -ignore_readdir_race -type f -user `whoami`|xargs -n 50 -t /bin/rm -rf
```

The xdev tells find not to branch to other filesystems,
the ignore_readdir_race tells it not to worry if a file has disappeared since find found it (it's kind of weird, shouldn't actually matter here)
type f - tells it to find all files (i.e. no directories, this command is just going to clean up a lot of files to make it easier to deal with other commands later, specifically I'm worried about the effects of running rm -rf on a directory which has contents on a different filesystem)
and user `whoami` where "`whoami`" can be replaced by your username tells it to only try to delete your files, i.e. no root stuff.  I assume most of it is yours with possibly a handful of root files, but it's a good idea to never run a "find|rm" command as root, that's a good way to blast your system in a hurry.

And onto the xargs command:
the -n 50 tells it to try to operate on 50 files at a time
the -t tells it to echo to the terminal the commands that are being run
and for rm I suppose you don't need the "-r" as we're only deleting files (no directories), and the "-f" says don't worry if it's a write protected file, I'm sure I want it gone.

Run that command and you should be down to a manageable number of empty directories and files owned by another user and we can talk about cleaning out the toplevel directory.  If all's going well you should see a large number of rm commands scrolling down your terminal as the files disappear in a puff of smoke (figuratively of course, if your computer starts smoking, worry).

---

### Post by dniMretsaM on 2011-09-24
PLEASE BE CAREFUL WITH THE[FONT=Courier New] rm -rf[/FONT] COMMAND!!!

If the folders are in the trash, run this to delete them:
```
rm -rf ~/.local/share/Trash/files/*
```This will completely remove everything in the trash. If that doesn't work, try this (use this only if you get permission errors when you try to use the previous command):
```
sudo rm -rf ~/.local/share/Trash/files/*
```

---

### Post by dchurch24 on 2011-09-24
Thanks guys.

The family is watching TV on it now (it's a MythFrontend) so I'll have to wait until the morning whilst they're still asleep to try these out.

I'll keep you posted.

Many thanks.

---

### Post by dchurch24 on 2011-09-25
Hi guys, I tried running the 'rm -rf ~/.local/share/Trash/files/*' and 'sudo rm -rf ~/.local/share/Trash/files/*' commands, but again it just hangs when when executing.

So I used the 'find' method, but alas, the same is true - it simply sits there at the terminal doing nothing.

I really need to find which program is filling the drive up - it's a small drive admittedly (as it's primarily used as a Myth frontend, I chose the smaller HDD size as there's very little that needs to go on the actual local machine), but something is creating files at a stupid rate. Whichever program is it, I've obviously (for once) put some error trapping in as there are now 0 bytes remaining on the disk and it's not throwing an error. Damn!

I'm starting to think I'm going to need to scrap it and reinstall the OS, which seems a bit of a mission just to delete a folder ;-)

---

### Post by dchurch24 on 2011-09-25
> **dino99 said:**
> then try to split the deletion using either a->z* or by .extension

so nautilus or gnome-commander cant open that folder ? Can you cd to that folder ?

I can cd to it, I just can't do anything when I'm there.

Now, for some reason I can't even open the Rubbish bin in Nautilus either - I get some sort of DBUS error.

The folder size is being reported as 448856064.

---

### Post by WasMeHere on 2011-09-25
Maybe something is wrong with the file system. Boot from a live CD or live USB and run 'fsck' to check and or repair the file system. If you have an ext3 or ext4 system, run ```
e2fsck -f
``` to force checking even if the file system seems clean.

After that you can mount the file system and cd to the 'crowded' directory. And finally, try to delete its content using the 'find method' suggested by *hwttdz*.

---

### Post by dchurch24 on 2011-09-25
Thanks - I was just about to do the disk check, my conclusion is that it's damaged somehow as well.

Thanks for the tip, I'll do exactly that.

---

### Post by patryk77 on 2011-09-25
I recommend running:
```
rm -rf ~/.local/share/Trash/files/; mkdir ~/.local/share/Trash/files/
```

rather than
```
rm -rf ~/.local/share/Trash/files/*
```

The first will try and delete the directory and recreate it, while the second will generate a list of files and tell rm to delete every one (and programs often have problems dealing with a ridiculously long argument list).

If it takes a really long time, just go for a beer / bike ride / nap / party / night's sleep / second honeymoon until it finishes.

---

### Post by dchurch24 on 2011-09-25
> **patryk77 said:**
> I recommend running:
```
rm -rf ~/.local/share/Trash/files/; mkdir ~/.local/share/Trash/files/
```

rather than
```
rm -rf ~/.local/share/Trash/files/*
```

The first will try and delete the directory and recreate it, while the second will generate a list of files and tell rm to delete every one (and programs often have problems dealing with a ridiculously long argument list).

If it takes a really long time, just go for a beer / bike ride / nap / party / night's sleep / second honeymoon until it finishes.

Cheers. I'll try that first. I'm having to create a boot USB key to try the method before your post, so whilst I'm doing that I'll try your way.

Thanks to all of you BTW. It's this that makes the community what it is.

---

### Post by hakermania on 2011-09-25
But seriously, something is wrong, I created a bash script that created thousands of folders and thousands of files containing things (not empty ones), and rm deleted all of them rather quickly....
Even if you have many many many more files than me, an hour would be more than enough to delete these files, unless the number tends to infinity :P

---

### Post by patryk77 on 2011-09-25
> **hakermania said:**
> But seriously, something is wrong, I created a bash script that created thousands of folders and thousands of files containing things (not empty ones), and rm deleted all of them rather quickly....
Even if you have many many many more files than me, an hour would be more than enough to delete these files, unless the number tends to infinity :P

Clearing /tmp/motion takes a long time for me when there is more than 10K files in it...

I agree that less than an hour, but it can easily take 20 minutes.

---

### Post by dchurch24 on 2011-09-25
Yes, I think something is defintely wrong.

You got me thinking with that - I seem to remember that it's something to do with Motion. However, I had 0 bytes left on the drive - I've set off the 

```

sudo rm -rf ~/.local/share/Trash/files/; mkdir ~/.local/share/Trash/files/


```

...and then went out for a couple of hours. I now have 3.7gb of space, so it appears, albeit slowly, to be doing something. It's still running.

---

### Post by patryk77 on 2011-09-25
Yeah, df was my trick to make sure rm was working hehe.

Are you running Motion as well?

---

### Post by dchurch24 on 2011-09-25
I was, but now I've uninstalled it in an effort to figure out what it is that's chewing up the disc space.

It's a bit disconcerting - I went to Mexico for two weeks, I come back and my drive is full, presumably with Motion capture files!

---

### Post by dchurch24 on 2011-09-25
It's now showing 17gb free - so IT'S WORKING! ;-) - it's still running the rm command, but I guess there must have been MILLIONS of tiny files in there, so I might book up a three month holiday and see if it's finished when I get back ;-)

Thanks guys.  I'll mark this thread as solved.

In case anyone searches for a similar problem and turns this up; it was this:

```

sudo rm -rf ~/.local/share/Trash/files/; mkdir ~/.local/share/Trash/files/

``` 

that solved it.

Very handy tip about the 'find' though - thanks to all.

---

### Post by patryk77 on 2011-09-25
> **dchurch24 said:**
> I was, but now I've uninstalled it in an effort to figure out what it is that's chewing up the disc space.

It's a bit disconcerting - I went to Mexico for two weeks, I come back and my drive is full, presumably with Motion capture files!

Yeah, Motion does tend to take up a ridiculous amount of space.

I have been meaning to write a cron script to move the *.swf daily and remove the thousands of JPGs some day.

Glad you got it sorted out.

---

### Post by dchurch24 on 2011-09-25
Would you believe it's still running? It's been about 12 hours now. I now have 36gb spare, which is an improvement on the 0 bytes it was reporting earlier! 

Thanks a lot for your help, much appreciated.

---

