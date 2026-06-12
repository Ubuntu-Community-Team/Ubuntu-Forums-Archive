---
title: "sudo rm -R me"
date: 2011-06-15
forum: General Help
---

### Post by ckfoxtrot on 2011-06-15
I am ashamed to say I made a pretty n00by mistake day before yesterday.  As a disclaimer, this is a long post, so as to document what happened and what I tried for others (with, I am sure, mistakes on my part along the way) and to give you all a better idea of how to answer my questions at the end.

So, what did I do that was so terrible?

While trying to properly set up snort on my system running Ubuntu 11 Server I accidentally entered:

```
sudo rm -R usr/share
```Fortunately, I caught it quick and hit ctrl-c.  Unfortunately, it did remove some files, which ones I am not certain.  Right afterwards I tried a few different methods to restore any deleted files without any luck (testdisk & scalpel)

Shortly after I started to experience a few problems.  To start, the menu bar in nautilus disappeared, as well as my ability to right click, but only running gksu nautilus, then non-su as well.

After ```
sudo aptitude reinstall nautilus
``` and some playing around I these functionalities returned.

I also ran across a forum thread here from a user who accidentally did rm -R /usr/share/applications.  Reading the responses to him, I did both of the following (the first one modified from the second, but run first, I am not sure if it was a good idea or not):

```
dpkg-query -S /usr/share/
dpkg-query -S /usr/share/ | sed -e "s/:.*$//" -e "s/,//g" | xargs sudo aptitude reinstall
```then the original recommendation:

```
dpkg-query -S /usr/share/applications/
dpkg-query -S /usr/share/applications | sed -e "s/:.*$//" -e "s/,//g" | xargs sudo aptitude reinstall]
```

Next, I ran into some problem where I needed to reinstall gvfs (I do not remember the exact problem), so once again, ```
sudo aptitude reinstall gvfs
```Then, sometime after this, I lost right click ability on my desktop and in the top and bottom gnome panels.  I could not figure out what to do, ```
sudo aptitude reinstall ubuntu-desktop
``` not helping at all, so eventually, and very reluctantly, I decided to restart.

When encountering this desktop problem, one potential solution I found while searching was to restart the desktop with ctrl-alt-backspace.  As this keyboard shortcut is disabled by default, I enabled it before restarting, and used this as my way to restart, which performed its function but didn't help me any...

At this point, my problems increased in both number and difficulty.  To begin, my monitor gave me an "Out of Range" message (viewsonic VA720, on a different note, I really wish there was better linux driver support for this).

So being, next I booted from my Ubuntu cd, first trying the install CD repair options, which were of no use.  Next, I booted into Ubuntu with recovery mode with low graphics (or something to that effect).  It would just hang at one point of the boot screen, saying it had loaded some sort of gnome interface or package and would wait and remove it if not working or something to that effect.

Thinking it was simply stalled, I restarted once or twice.  Finally, by happenstance, I hit escape at this point and was greeted with a purple Ubuntu 11 loading screen, asking me for my disk encryption password at the bottom!

After a bit of google searching, I found that ctrl-alt-numpad+ or  numpad- changes the resolution.  This helped somewhat, though each  different setting still left me with a garbled/multiplied display or, at best, one  that was 2/3 off the screen (only showing anything if I moved the mouse  down very far in each case).  In the last case, seeing 1/3 of the window clearly, I was shown a graphics trouble shooting window.  Switching back to the garbled resolution, where I could see the window boxes to click for cancel or ok, I clicked out, having the first option selected (something about launching in trouble shooting or low graphics mode), which brought up another window.  Switching back 1/3 view I could read something about waiting for the screen to restart, but there were boxes at the bottom again, so I clicked to continue.  This did not help at all.

Due to this, I restarted with the command line.  I tried to reinstall ubuntu-desktop again, as well as ```
sudo dpkg-reconfigure xserver-xorg
```.

After ```
startx
```I am able to see my screen and my desktop!  Unfortunately, both the top and bottom Ubuntu gnome panels are missing, alt-f2 doesn't work, and I still cannot right click on the desktop.

Next, I came across ctrl-alt-f1-f7 on while searching the internet for solutions, allowing me to get back to the terminal easily.  I tried multiple different methods to restore my panels:

```
metacity --replace
gnome-panel
```and perhaps more.  These commands did not work, as they were not sending the commands to the desktop GUI and would simply tell me that they could not start the desktop.  At this time I did not think to open one of the folders on my desktop and go to applications and start terminal that way, which later dawned on me.

I also tried deleting my gconf files too.  This brought me to the point where my volume icons were on the desktop again, which was helpful.

Last, I did:

```
sudo aptitude reinstall gnome-panel gnome-applets libgnome-desktop* libgnomepanel*
```if I remember the packages correctly (the first two I am certain of).

Success!  Top and bottom panels restored, as well as the ability to right click on the desktop!  Unfortunately, then, to see what it might do and if it might help, I run metacity --replace and the panels disappear again, as well as the title and menu bars on all my application or folder windows!  Fortunately, restarting restored them.

Now, I am still experiencing a few issues, though I am very happy to have my desktop back in mostly working order.

To start, I had to reset all of my desktop settings: background, top panel icons, mouse speed, theme, etc.  Not really a big deal.  However, for some weird reason, now my trash can icon looks different/weird and the mouse icon I select in customize theme is acting funny.

If I select a non-default icon, it only changes the mouse icon when it is hovering over a non-ubuntu application.  For example, it will still show the default icon when hovering over the desktop, nautilus, terminal (if I remember right), etc.  However, if I hover over firefox, it shows the icon I set it too, and a very small instance of it at that.

So, on to my questions/

1)  Any ideas on how to fix the mouse pointer icon?

2) I reinstalled all the applications that are supposed to be installed in /usr/share/applications, using dpkg-query as a guide, but what else should I be concerned with checking to make sure it is still there and in working order, in both /usr/share/ itself and /usr/share/applications?

3) Should I just reinstall Ubuntu?  This would be a pain, though less so thanks to the fact that it is installed on one hard drive out of three and most of my important files are either on or backed up to the latter two.

Just to check, if I do reinstall Ubuntu, this will not affect these other two hard drives and their partitions, correct?

Also, if I do reinstall, is there an easy way to backup my configs for different packages I have installed, just so I don't miss anything by accident?  Right now, all I am really concerned with is netatalk/afpd/avahi, ssh server, denyhosts...

If you have read this far and have any ideas or suggestions I gladly welcome them.  I feel like such a noob.

I know there are ways to setup ```
rm
``` to not delete files straight away, rather move them to another directory, but is there a way to put a time limit on how long these files are kept there, or maybe better to just have rm move them to the trash can?

Thanks for reading, hopefully this might help others too, or act as a lesson/cautionary tale of how not to do things :O

ck

---

### Post by mmsmc on 2011-06-15
wow, what an adventure

---

### Post by ckfoxtrot on 2011-06-15
> **mmsmc said:**
> wow, what an adventure

It definitely has been, but at least I haven't lost anything important (other than time...) and am learning a fair amount from my mistakes (which is why I do not believe in regret or crying over spilled milk)  ;).

---

### Post by nothingspecial on 2011-06-15
While I applaud your tenacity and resourcefulness, 
 one thing this whole adventure should have taught you is to **_backup_** your important personal data.

See, if you make an unrecoverable error, linux is very easy to fix. You just reinstall it. If you have every important file backed up then this can be accomplished in about 20 minutes.

Now I happen to like trying to fix broken systems, I enjoy it, but this feature of linux should not be ignored.

Well done =D>

---

### Post by Derek Karpinski on 2011-06-15
consider editting your .bashrc file and adding this line:
 
```
 alias rm = 'rm -i'
```
 
This will ask you whether or not you want to 'really delete this file' whenever you enter 'rm'

---

### Post by FormatSeize on 2011-06-15
Good job on knowing what to do. Rescuing things can be an adventure, and this was one heck of a tale. This is also great information just to have available in general.

---

### Post by fgsupport on 2011-06-15
> **ckfoxtrot said:**
> share/applications?

3) Should I just reinstall Ubuntu?  This would be a pain, though less so thanks to the fact that it is installed on one hard drive out of three and most of my important files are either on or backed up to the latter two.


Also, if I do reinstall, is there an easy way to backup my configs for different packages I have installed, just so I don't miss anything by accident?  Right now, all I am really concerned with is netatalk/afpd/avahi, ssh server, denyhosts...

If you have read this far and have any ideas or suggestions I gladly welcome them.  I feel like such a noob.



Yep re-install it, you are never going to know when you have finished finding things that are missing and it seems you machine is working enough to do this (at tleast form recovery mode). 

The following will be helpful:
back up your /etc partition into a tar file ```
tar -cvzf etc.tar.gz /etc
``` it won't take up much space at all and its useful to be able to compare files afterwards.

If you have space its easiest just to back up the whole of /home, there is a lot of stiff stored in user's .files etc that is useful to restore

then do the following ```
sudo dpkg --get-selections >dpkg.out
```, this backs up a  list of  all the packages you have installed.

Copy all this across to another disk and reinstall. 

copy across the dpkg.out file and do
```
sudo dpkg --set-selections < dpkg.out
sudo apt-get dselect-update
```Make sure you have the multiverse enabled in software sources first if you are suing it. This should restore all your packages.

Now recreate the users and restore /home if you backed it up.  If you did check that user ids and names match up if you do ```
ls -l /home 
``` and it shows something like 
```
drwxr-xr-x 89 1001 1001 4.0K 2011-06-15 12:51 paulm
```rather than
```
drwxr-xr-x 89 paulm paulm 4.0K 2011-06-15 12:51 paulm
```you will need to fix this. You can do  this with (for example)

```
sudo usermod  --uid 1001 --gid 1001paulm
```or 
```
chown -R paulm.paulm /home/paulm
```I prefer to do the former but make sure you are not logged in as the user you are trying to change. 

Finally extract  etc.tar.gz to a folder somewhere (not to /etc) 
```
/path/to/etc
```e.g. /home/tmp/
the following should spit out a list of files that differ
```
 for file in $(find /etc/ -print); do sudo diff -q  /home/tmp/$file $file| grep -v "Common subdirectories"; done
```you can then compare and edit them.

At the end of this you should have an identical system.

---

### Post by ckfoxtrot on 2011-06-15
Wow thanks for the detailed response fgsupport!  My /home backup is still finishing up but once that is done I am going to reinstall.  I'll report back after I sort everything out.

ck

---

### Post by ckfoxtrot on 2011-06-17
Well, re-installation was a success, my system is probably in a better state than before even.

Having home$ and /etc/ backed up helped out tremendously, especially for re-installing and configuring some packages, like netatalk.  When first setting that up to share files and have one partition to act as a time machine storage drive for my MBP it took me quite a while to get it configured right, mainly due to some small errors or changes from the guide I was following.  With those files on hand it was a breeze.

Now too I have set up a crontab for daily backups to a partition on one of my other HDDs, backing up /etc/, /var/log/, /home/, and a small share folder I keep on my main drive.

I do have a question about this, however.  I set it up to tar each of these locations at 6am daily.  Will it simply overwrite each file every day or is it going to add a new one or simply not make a backup if there is a file in the way?  From what I can gather it seems like the former, but I am not positive.

I am also toying with a way to rm files to the trash instead of deleting them outright.

Right now I have .bash_aliases set to include:

```
alias rm="mv --target-directory ~/.local/share/Trash/files"
```

Need to test it still and I am not positive if that is the best method (assuming it works).

Thanks again for the help.

ck

---

### Post by ssreddy555 on 2011-06-17
Isn't it easier to back up & restore with Dejadup?

---

### Post by ckfoxtrot on 2011-06-17
> **ssreddy555 said:**
> Isn't it easier to back up & restore with Dejadup?

I just checked that out and it seems like a decent backup option.  I may have to play with it in the future if my cron tars don't seem good enough.

Thanks for the tip!

---

