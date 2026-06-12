---
title: "mount drive - How Can I mount a drive in the same way ubuntu does?"
date: 2011-07-20
forum: General Help
---

### Post by Keypel on 2011-07-20
When I go to places->500gb file system

an icon gets placed on my Desktop and the partition gets mounted at

/media/68bb54ae-5d14-9584-8b51-954128462154

But.....  When I use the command

sudo mount /dev/sdb2 /media

No icon is displayed on the Desktop and it gets mounted at /media

I'v also tried

sudo mount /dev/sdb2 /media/68bb54ae-5d14-9584-8b51-954128462154

but I get the error mount does not exist

**how do I mount it the same way ubuntu does using the command line?**

---

### Post by Primefalcon on 2011-07-20
you need to create the folder that your trying to mount to first

use sudo mkdir /dev/whatever for that

---

### Post by Primefalcon on 2011-07-20
btw you dont have to mount to the /dev folder, you can mount to a folder on your desktop if you wish

---

### Post by seawolf167 on 2011-07-20
> **Keypel said:**
> 
But.....  When I use the command

sudo mount /dev/sdb2 /media

No icon is displayed on the Desktop and it gets mounted at /media


You shouldn't mount at /media, you should mount within it

```
sudo mkdir /media/mymountpoint
sudo mount /dev/sdb2 /media/mymountpoint
```

> **Keypel said:**
> 
sudo mount /dev/sdb2 /media/68bb54ae-5d14-9584-8b51-954128462154

but I get the error mount does not exist

This is because the mount point within the /media folder doesn't exist, you have to create it first (but seriously, why do you want that string as your mount name???)

```
sudo mkdir /media/68bb54ae-5d14-9584-8b51-954128462154
sudo mount /dev/sdb2 /media/68bb54ae-5d14-9584-8b51-954128462154
```

If you want it to mount automatically at boot though, you'll need to add an /etc/fstab entry

---

### Post by Keypel on 2011-07-20
> **Primefalcon said:**
> you need to create the folder that your trying to mount to first

use sudo mkdir /dev/whatever for that

wait... so when gnome gui mounts it, it is creating the folder 68bb54ae-5d14-9584-8b51-954128462154 ???

I trying to mount it the same way gnome gui mounts it. You know, where you have that icon on the Desktop and how it mounts it in

/media/68bb54ae-5d14-9584-8b51-954128462154

and has has the little eject icons in nautalus.

What command does gnome gui issue to do all that stuff?

---

### Post by seawolf167 on 2011-07-20
> **Keypel said:**
> What command does gnome gui issue to do all that stuff?

No idea - probably something similar, but with "extra features" like creating the desktop icon. If you choose to have it automounted at boot you *should *have a desktop icon (I know at least in 10.04 and 10.10 it gave me icons on my desktop at boot). Else a simple symlink or launcher will do the trick if the desktop icon isn't automatically created.

---

### Post by AlphaLexman on 2011-07-20
The problem... if you create the directory '/media/68bb54ae-5d14-9584-8b51-954128462154' 

The next time your system tries to auto-mount, it will **NOT** be mounted at '/media/68bb54ae-5d14-9584-8b51-954128462154' 

But instead at '/media/68bb54ae-5d14-9584-8b51-954128462154[COLOR="Red"]**_**[/COLOR]' EDIT: Note the _underscore_ at the end.

And any links would be broken!

---

### Post by Keypel on 2011-07-20
> **seawolf167 said:**
> No idea - probably something similar, but with "extra features" like creating the desktop icon. If you choose to have it automounted at boot you *should *have a desktop icon (I know at least in 10.04 and 10.10 it gave me icons on my desktop at boot). Else a simple symlink or launcher will do the trick if the desktop icon isn't automatically created.

Everything is fine with the gui way. No issues there. I am just wondering what is the command that gnome issues to make all that happen.

> **AlphaLexman said:**
> The problem... if you create the directory '/media/68bb54ae-5d14-9584-8b51-954128462154' 

The next time your system tries to auto-mount, it will **NOT** be mounted at '/media/68bb54ae-5d14-9584-8b51-954128462154' 

But instead at '/media/68bb54ae-5d14-9584-8b51-954128462154[COLOR="Red"]**_**[/COLOR]' EDIT: Note the _underscore_ at the end.

And any links would be broken!

I didn't create the folder, didn't seem right.

Is there a way to monitor all the commands that gnome issues?

---

### Post by AlphaLexman on 2011-07-20
Go to 'System -> Preferences -> Removable Drives and Media'

---

### Post by Keypel on 2011-07-20
> **AlphaLexman said:**
> Go to 'System -> Preferences -> Removable Drives and Media'

I don't have that path on my system (10.10 Maverick Meerkat) but if I did what info would I discover? Would it list the command I am looking for?

---

### Post by AlphaLexman on 2011-07-20
> **Keypel said:**
> Would it list the command I am looking for?No.

I believe you are getting off track from your original post. I don't mind answering your questions, just keep on topic instead of jumping from one thought to another.

You stated earlier that "Everything was fine the GUI way."

If you are still having problems, please continue. If not, start a new thread and mark this one as solved.

Regards.

---

### Post by Keypel on 2011-07-20
> **AlphaLexman said:**
> No.

I believe you are getting off track from your original post. I don't mind answering your questions, just keep on topic instead of jumping from one thought to another.

You stated earlier that "Everything was fine the GUI way."

If you are still having problems, please continue. If not, start a new thread and mark this one as solved.

Regards.

Yes, everything _**is**_ fine the gui way. I have no questions about the gui. I never did.

No I have not gotten off track at all. you took that quote out of context. the compete quote was:

> Everything is fine with the gui way. No issues there. I am just wondering what is the command that gnome issues to make all that happen.

You see, I'm _not_ looking to do anything via the gui. I'm trying to do what gnome does only I want to do it via command line. I don't see where I have gotten off track at all. Please specify the post where I go off track.

My goal has been clear from the start off this tread. 

The title of this thread is:

mount drive - How Can I mount a drive in the same way ubuntu does?

Sorry to sound testy, especially when I am the one asking for help but I have definitely not gotten off track.

Please re-read my very first post.

I honestly don't know how I can be any clearer, The first post says exactly what I'm trying to do.

---

### Post by AlphaLexman on 2011-07-20
You're not being testy, my last post was a little strict.

However, does this not answer your question??

> **seawolf167 said:**
> ```
sudo mkdir /media/mymountpoint
sudo mount /dev/sdb2 /media/mymountpoint
```

You agreed that the '/media/xxxxx-xxxx-xxxxxxxxx' was abad place to mount from the command line. Have you tried seawolf167's suggestion?? And what is not working with it??

---

### Post by Keypel on 2011-07-20
yeah, I totally agreed that the '/media/xxxxx-xxxx-xxxxxxxxx' was a bad place to mount. 

However When I read:

[QUOTE=Seawolf167]

sudo mkdir /media/mymountpoint
sudo mount /dev/sdb2 /media/mymountpoint[/QUOTE]

I thought mymountpoint was an example word like foo or bar. I didn't realize I literally type mymountpoint as part of the command.

So now that I realize that and have tried it out, yes this thread is in fact solved.

**EDIT**

I guess mymountpoint was an example after all. 

I guess the only difference is: 

When gnome mounts it, it creates a folder named 68bb54ae-5d14-9584-8b51-954128462154 in the /media folder 
When gnome unmounts it, that same folder is deleted automatically.

To do something very similar:

to mount:
```
sudo mkdir /media/500GB; sudo mount /dev/sdb2 /media/500GB
```

to unmount:
```
sudo umount /media/500GB/; sudo rmdir /media/500GB/
```

As far as my no "unmount Desktop icon" problem, that was caused by mounting directly in the /media dir. Apparently that is a no no. Having a sub folder such as /media/500GB solves that problem.

I apologize if I didn't explain my original problem well enough. I also apologize that I didn't understand Seawolf's original solution sooner.

As always, I very much appreciate all the great help I receive here. Ubuntu community is the best!!

Thank You SeaWolf Thank You AlphaLexman.

Marked as Solved.

--

---

### Post by seawolf167 on 2011-07-21
Glad you got it sorted out - I should add that you can create an alias in your ~/.bashrc file and enter the commands (mount, unmount, etc.) so a quick two or three letter keystroke will do what you need it to do.

The usage for your case (modify or change as needed) is:

Edit bashrc

```
gedit ~/.bashrc
```

add your alias' at the bottom of the file, an example is

```
alias md="mkdir /media/mymountpoint"
alias mm="mount /dev/sdb2 /media/mymountpoint"
```

save, exit, and reload your config (or close the terminals and re-open or logoff/login, etc.)

```
exec bash
```

Now to make your directory, just type

```
sudo md
```

and to mount your device, type

```
sudo mm
```

---

