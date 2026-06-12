---
title: "Changing &quot;places&quot; drop down menu"
date: 2010-11-20
forum: General Help
---

### Post by kanishkdudeja on 2010-11-20
how can we add new items in the places menu displayed on the top and change locations pointed to by the items already present there ?

---

### Post by inso_741 on 2010-11-20
"Menubar>Bookmarks>Edit Bookmarks" ???

---

### Post by WorMzy on 2010-11-20
You can also edit the ~/.gtk-bookmarks file.

---

### Post by kanishkdudeja on 2010-11-20
@inso_741..

there is no bookmarks manager anywhere..

@wormzy..

dat file doesnt contain all the items

---

### Post by northern lights on 2010-11-20
> **kanishkdudeja said:**
> @inso_741..

there is no bookmarks manager anywhere..


Open an instance of nautilus (your file manager) and utilize it's "bookmarks" menu.

---

### Post by kanishkdudeja on 2010-11-20
ive added bookmarks there..but dey still do not appear in Places on my desktop

---

### Post by inso_741 on 2010-11-21
be clear about what you want!!!

---

### Post by kanishkdudeja on 2010-11-26
yeah dats what i want..i want customize the places menu displayed on the desktop

---

### Post by WorMzy on 2010-11-26
Never seen a places menu on the desktop.. could you take a screenshot of it?

You can create launchers on your desktop by right-clicking it and choosing "Create Launcher", that launcher can then be used to open an application or a location. Is that what you want?

---

### Post by kanishkdudeja on 2010-11-26
ive attached the..i want to customize the items that are under the places menu..

---

### Post by WienerWuerstel on 2010-11-26
Just Drag and Drop the Folder into the Personal Space of Nautilus like that

---

### Post by WorMzy on 2010-11-26
That's not the desktop, that's the panel. Only one part of that menu can be edited, and that's part (1) in this screenshot:
[IMG]http://img227.imageshack.us/img227/4395/menuls.png[/IMG]
You can edit part (1) by using the methods already outlined in the first few replies of this thread: Editing ~/.gtk-bookmarks, or using nautilus' bookmarks manager.

Both parts of (2) cannot be modified, as far as I know. Removable media will automatically update as and when devices are detected/disconnected. You can stop partitions appearing in this list by mounting them outside of /media, e.g. in /mnt. You can use /etc/fstab for this purpose.

---

### Post by inso_741 on 2010-11-27
> **WorMzy said:**
> There are 10 kinds of people in this world: Those who understand ternary, those who don't, and those who confuse it with binary.
I agree!!!LOL!!!

---

### Post by jal on 2010-12-01
> **WorMzy said:**
> That's not the desktop, that's the panel. Only one part of that menu can be edited, and that's part (1) in this screenshot:
[IMG]http://img227.imageshack.us/img227/4395/menuls.png[/IMG]
You can edit part (1) by using the methods already outlined in the first few replies of this thread: Editing ~/.gtk-bookmarks, or using nautilus' bookmarks manager.

Both parts of (2) cannot be modified, as far as I know. Removable media will automatically update as and when devices are detected/disconnected. You can stop partitions appearing in this list by mounting them outside of /media, e.g. in /mnt. You can use /etc/fstab for this purpose.


(All,) Thank you for this information, very helpful.

However, I am showing a couple of partitions in the places panel which are not mounted and not in fstab. Selecting causes them to mount on /media, but unmounting them doesn't remove them from the panel. 10.04 lucid

They're not in the .gtk-bookmarks file. They have been mounted in the past. 

any ideas? That info has to be stored somewhere... or is it just that the partitions exist?

---

### Post by WorMzy on 2010-12-01
It's just letting you know that they exist, and gives you an easy way to mount them if necessary.

Like I said: if you don't want them to appear in the list, you can create an entry for them in fstab which mounts them to a folder other than media. For example, if I don't want sda3 to appear in the list, I can create an entry in fstab as such:
```
/dev/sda3 /mnt/storage ext4 defaults,noauto 0 0
```

The fstab file is quite easy to understand, though I recommend that you A) don't modify any of the other lines in it, and B) ask for assistance creating an entry, so that we can help to make sure that you get it right.

For B), we'll need to know some info about your partitions, so open a terminal and enter
```
sudo fdisk -l && sudo blkid -c /dev/null
``` and then post the output here (inside [CODE[COLOR="Black"]][[/COLOR]/CODE] tags). We will also need to know which partitions you don't want to be in the list.

---

### Post by jal on 2010-12-01
> **WorMzy said:**
> It's just letting you know that they exist, and gives you an easy way to mount them if necessary.



I see. Thank you. I'll leave the fstab alone for now, I don't want them mounted. 

Having them show on the panel does no harm, I was just wondering.

---

### Post by sofasurfer on 2010-12-02
This makes no sense at all. The guy asked how to edit the places menu. One other guy went so far as to say thaat there is no places menu!!! WTF!!! On the panel at the bottom of the screen are "applications", "places" and "system". 

If you go to system>preferences>main-menu, you can edit the "applications" and the "system" menus. But you can not edit the "places" menu. That is what was asked about in the 1sr post.

It was also stated that you can open nautilus to edit "places". I think that may be the answer but it is not exactly clear. That dropdown menu in Nuatilus doesn't make sense to me. But I was able to delete an unwanted item in "places"

So, why does the "places" menu not appear in system>preferences>main-menu?

---

### Post by piedro on 2010-12-06
In addition: It's really annoying that you cannot really edit the places menue within nautilus: 

Yes you can add or remove places or change their order. But you can not organize by subfolders, filtering or tags (labels). I really think this is a serious issue and not to be ridiculed. I personally can't work effeciently with nautilus because you can't have more than about 20 - 30 places (aka bookmarks aka favorites ...) before the menue get's cluttered and you have to scroll through to find things again ... 

So to ask this question seriously again: 
Is there any tool or possibility to truly edit the places menue?  
Or is there any panel applet to use thats more sopphisticated than the builtin one? 
Or is there a nautilus extension that does the job? 

thx for reading, 
piedro

---

### Post by em3raldxiii on 2011-02-12
> **WorMzy said:**
> That's not the desktop, that's the panel. Only one part of that menu can be edited, and that's part (1) in this screenshot:
[IMG]http://img227.imageshack.us/img227/4395/menuls.png[/IMG]
You can edit part (1) by using the methods already outlined in the first few replies of this thread: Editing ~/.gtk-bookmarks, or using nautilus' bookmarks manager.

Both parts of (2) cannot be modified, as far as I know. Removable media will automatically update as and when devices are detected/disconnected. You can stop partitions appearing in this list by mounting them outside of /media, e.g. in /mnt. You can use /etc/fstab for this purpose.

I would like to add my name to the list of people who are finding it difficult to edit the Places menu.  It's important to note that I have been using Ubuntu since Breezy because it shows that even though I am obviously very familiar with Ubuntu, I am still baffled by "simple" things sometimes (I dabbled with Hoary but didn't commit 'til Breezy).

Anyhoo ... I would like to thank Wormzy for posting that very clear graphic which will help me illustrate my point.  Under the lower part of **Section 2** of the above image (namely, below [/i]Computer[/i], I have an entry (Pictures) for a location that apparently cannot be mounted.  Specifically, when I click on it, it pops up "unable to mount Pictures".  What I would like to do is remove that entry completely.

Now, I have cracked open my fstab file, but everything in there seems fine.  All of the mounts noted inside that file work perfectly fine when navigated to.  For example, I have 3 network shares (... smb shares I think), Pictures, Videos, and Music each corresponding to an entry in my home directory (such as ~/Music).  I also have 3 Windows partitions (for my residual evil Vista installation that I keep around for playing WoW occasionally) which also correspond to home directories such as ~/windows_01.

This leads me to think that waayyy back when I first set up my fstab, I may have experimented and done something incorrectly, subsequently remedied my error, and perhaps left behind some kind of residual problem.  It's not in my fstab, it's not in my bookmarks.  In the left pane of my nautilus browser, it is the only mount point that does NOT have an "eject" style button.  I cannot do anything sensible when I right-click on it (mount, open, etc).  What I think this little pane needs is an option to "Remove from this list" when right clicking on an item.  Of course, there would have to be a configurator specifically to address re-adding these items somewhere intuitive such as right-clicking on the blank space and have "add item to this list".

I also subscribe to the idea of discussing issues here on the forums prior to submitting bug reports because it's all too easy for even seasoned users like myself to encounter problems that aren't bugs at all.  It's a function of ever-more-complicated software, I am afraid.

I'd also be interested to know if there are quick-and-easy ways of changing the icons for items in this same part of the Places menu ... but that's probably better suited to a different thread.

---

### Post by anand warik on 2011-02-12
WienerWuerstel,in your attachment one can see command prompt right in the nautilus window. How does that happen?

And also how do one delete a post from here. There is an edit button which tells you can edit/delete but there i couldn't find a button for delete

---

### Post by drs305 on 2011-02-13
> **anand warik said:**
> And also how do one delete a post from here. There is an edit button which tells you can edit/delete but there i couldn't find a button for delete

Once posted, they become (more or less) permanent. Moderators/staff can delete posts but normal users, even the person making the post, cannot.

If you really need a post deleted you can "Report it" via the link in the lower left corner of the thread, stating what you want and why.

---

### Post by WorMzy on 2011-02-13
> **em3raldxiii said:**
> I have an entry (Pictures) for a location that apparently cannot be mounted.  Specifically, when I click on it, it pops up "unable to mount Pictures".  What I would like to do is remove that entry completely.

Is this the message you receive?:
[IMG]http://img440.imageshack.us/img440/710/20110213124514365x194sc.png[/IMG]

That seems to be caused by the "users" option in fstab for NTFS partitions mounted in /media. In my case, this is the entry in question:
```
UUID=7A5C94995C94522D                     /**_media/_**Terastore        ntfs-3g auto,uid=1000,gid=100,umask=002,**_users_** 0 0

```

Removing the "users" option, or changing the mount location to /mnt/Terastore removes the duplicate/buggy entry. Hopefully you can use this information to fix your list.


@anand, it looks like WienerWuerstel is using [Nautilus Elementary]("http://www.webupd8.org/2010/01/nautilus-elementary-simplified-nautilus.html"), which comes with an embedded terminal. There is a plugin available for standard nautilus [here]("http://software.flogisoft.com/nautilus-terminal/en/#download").

---

### Post by lisati on 2011-03-05
> **anand warik said:**
> And also how do one delete a post from here. There is an edit button which tells you can edit/delete but there i couldn't find a button for delete

You can use the "report abuse" button [IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG] and one of the forum staff will have a look.

---

