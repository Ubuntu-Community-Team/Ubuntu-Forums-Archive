---
title: "I have a problem opening directories"
date: 2009-12-13
forum: General Help
---

### Post by L a r r y on 2009-12-13
I installed Kiwi  version of Ubuntu 9.04, then brought in a backup of everything in my home/user folder, from 8.04.

It affected a few things adversely, including trying to open my Home Folder on the Places menu.  It wants to open in my text editor, which cannot open a directory.

I can open a file browser and hit the name of my home directory, and have it open correctly.  I only loaded a backup of everything in my /home/user directory, so I can open the Computer from the Places menu.

I have a launcher on my top panel that leads to my website folder in /home/user.  It too opens in gedit instead of in Nautilus.

I could do a fresh install again of 9.04, then bring in my backup again, minus a few selected files so that I don't overwrite whatever it was that is now messed up.  What files should I exclude from my tar file backup?

Another thing that got messed up was 9.04's shutdown drop-down menu.  8.04's shutdown button is now just a log-out and change user button.  I added the grey shutdown button that lets me restart, shut down or hibernate, but I don't have the drop-down menu that I originally saw.

My NVIDIA GeForce video card really set up nicely under 9.04, but that's gotten messed up as well, though I have reached a setting that works.

Any advice would be kindly appreciated.

Some good things that happened with my backup restoration:  I installed Thunderbird email client and it immediately saw my email settings.  I installed gftp and it immediately saw my web site settings.  I installed Wine and it instantly restored my Windows programs that I use in Linux.

I tried to import my bookmarks from an html file, but I was unable to organize that mess, but when I restored my Firefox profile, my bookmarks were as I left them in the crashed computer that was running 8.04.

---

### Post by NoaHall on 2009-12-13
Try this - ```
 sudo mv ~/.gconf ~/.gconf.old && sudo mv ~/.gconf.d ~/.gconf.d.old
```
And then reboot or use alt + k + prt scr to restart x.

---

### Post by L a r r y on 2009-12-13
> **NoaHall said:**
> Try this - ```
 sudo mv ~/.gconf ~/.gconf.old && sudo mv ~/.gconf.d ~/.gconf.d.old
```
And then reboot or use alt + k + prt scr to restart x.

That was a partial solution.  I ran your command, and .gconf was moved successfully to .gconf.old. .gconf.d does not exist. After I restarted, my shortcuts on the launch bar were gone and the drop-down menu under the red icon was back to original 9.04 style and position.

The Home folder, Desktop and Bookmarks on the Places menu are still bringing up gedit.

In checking, I found .gconf and .gconf.old, but I also found .gconfd, while .gconf.d does not exist.  So I edited the last half of the command to replace .gconf.d with .gconfd and re-ran that portion, and restarted.

I didn't see where running that made any difference.  I still have the places menu mess, and my video setup is still messed up.  

Just checking in the hidden files again, I now have an old version and a regular version of both .gconf and .gconfd.

**I will wipe it again and start over.**

Where before I overwrote my Home folder at /home/user with my 8.04 backup tar file, I will reinstall the OS on the system partition and home partition, then extract my tar file into my /home/user directory.  That will put the files into the /home/user/home/user directory, and from there I can copy files and folders into their proper places.  This way I won't overwrite say my Desktop folder and run the risk of messing up the Places menu.

That is one grey area that I have seen many people puzzled over:  Where is the Places menu stored, and how can it be edited?  I can right-click on the menus and see a chance to edit the menus, but that only covers the Applications and System menus, Not the Places Menu.  I thought if I could get into it I could maybe find why it is being opened by gedit instead of Nautilus.

I've got to get back the very orderly way that 9.04 handled my video card.  This card is the best card I have ever had, and it came in a very solidly-built computer that I got at a swap meet.  The motherboard on my old one gave up on me, after requiring several jiggles of the video card in its slot to get it to boot.

---

### Post by L a r r y on 2009-12-14
One update:  My video issue came about when I selected system > Preferences > Appearance > Visual Effects and selected anything other than None.

It had nothing to do with my bringing in backups from my previous 8.04 installation.

I reinstalled the operating system and set it up the way I wanted it, and thought now if I just extract those backups, I will put in my Firefox, Thunderbird and gftp profiles, then I will back the new system up.

Unfortunately, what I did was to end up overwriting the home directory again, and while I cut it short, I am already buggared-up on the Places menu again, with it wanting to launch directories in the text editor again.

So I will have to reinstall yet again and update, but this time, before I do anything with backups from the old install, I will back this 9.04 up!

It would sure save a lot of time if I could just go in and edit the Places menu behavior!

---

### Post by L a r r y on 2009-12-15
Just to wind this up, I opened a thread called, "[Edit the Places Menu?]("http://ubuntuforums.org/showthread.php?t=1354542")" which posed the specific question I would like to see an answer to.  However, I solved the issue by reinstalling and taking care not to back up and overwrite my home directory with previous version files.

I want to thank all who have read and have participated in the discussion.

---

### Post by Agent ME on 2009-12-15
> **NoaHall said:**
> Try this - ```
 sudo mv ~/.gconf ~/.gconf.old && sudo mv ~/.gconf.d ~/.gconf.d.old
```
And then reboot or use alt + k + prt scr to restart x.
None of the "sudo" parts to the command are needed. You're only messing with files owned by your own user, why would you need root privileges?


I see you solved this by just reinstalling -- I would've suggested doing the same as you did with the .gconf* folders to most of the other . folders, especially .nautilus and .local.

---

### Post by L a r r y on 2009-12-17
> **Agent ME said:**
> None of the "sudo" parts to the command are needed. You're only messing with files owned by your own user, why would you need root privileges?


I see you solved this by just reinstalling -- I would've suggested doing the same as you did with the .gconf* folders to most of the other . folders, especially .nautilus and .local.

Thanks, Agent ME!  The additional folders you mentioned would be worth a shot if there is another time.

I just reinstalled after trying 9.10, where I was improperly using the cp command to copy folders over, getting "cp: Omitting 'folder'."

When I did drag some files over using gui drag-and-drop, trying to import my Firefox, mail and ftp settings, I was getting some permissions denied, so I thought sudo was needed.  I have some settings backed-up on another partition from my 8.04 use.

I found a command line tutorial on [www.tuxfiles.org](www.tuxfiles.org), that explained my issue with cp.

I recently replaced my computer, and this one is a 1GHz Athlon similar to the other one, but much superior video card, and I have had no trouble getting 9.04 or 9.10 to run.

---

