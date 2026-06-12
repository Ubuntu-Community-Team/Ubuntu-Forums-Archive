---
title: "URGENT help needed everything wiped?"
date: 2010-05-21
forum: General Help
---

### Post by tigs6969 on 2010-05-21
ok so i was downloading as i usually do on rapidshare than the net stops working. i restart the computer as i usually do and than i saw that everything was completely missing. all my documents, all my files in downloads... everything. even my bookmarks on firefox are gone. the panel at the bottom of the screen which shows everything that is open is missing too
how do i fix this and get everything back?

---

### Post by tigs6969 on 2010-05-21
anyone? im using the latest ubuntu

---

### Post by tigs6969 on 2010-05-21
do i need to put more info or is everyone stumped?

---

### Post by bapoumba on 2010-05-21
Please do not bump your thread that often..
What were you downloading? Rapidshare is not the safest place I can think of.
I gather you can normally boot, your regular user is functional and only files from /home are missing, am I correct?

Are you using gnome ?

---

### Post by Rubi1200 on 2010-05-21
I am just clutching at straws here, but did you try this?

> **Restart GNOME without rebooting the computer**

                                                                                             
[LIST=1]
[*]                       Save and close all open applications.
[*]                       Use the **Ctrl**+**Alt**+**Backspace** 							 shortcut keys to restart GNOME. 					
[*]                       If **Ctrl**+**Alt**+**Backspace**               is disabled, type 						
[/LIST]



This is the link where I took it from:

[https://help.ubuntu.com/6.06/ubuntu/desktopguide/C/desktop-tips.html](https://help.ubuntu.com/6.06/ubuntu/desktopguide/C/desktop-tips.html)

---

### Post by 3rdalbum on 2010-05-21
> **Rubi1200 said:**
> I am just clutching at straws here, but did you try this?



This is the link where I took it from:

[https://help.ubuntu.com/6.06/ubuntu/desktopguide/C/desktop-tips.html](https://help.ubuntu.com/6.06/ubuntu/desktopguide/C/desktop-tips.html)

Don't give out information for old versions of Ubuntu. In Ubuntus 9.10 and later, you use Alt-SysRq-K to restart the X server.

Unfortunately I can't really answer the question, I don't know what's going on.

---

### Post by tigs6969 on 2010-05-21
> **bapoumba said:**
> Please do not bump your thread that often..
What were you downloading? Rapidshare is not the safest place I can think of.
I gather you can normally boot, your regular user is functional and only files from /home are missing, am I correct?

Are you using gnome ?
i dont think the downloading has anything to do with it as ive been using rapidshare for 4 years now no problems
yeah only files from /home are missing
and yes im using gnome

---

### Post by Rubi1200 on 2010-05-21
> **3rdalbum said:**
> Don't give out information for old versions of Ubuntu. In Ubuntus 9.10 and later, you use Alt-SysRq-K to restart the X server.

Sorry about that :oops:

I wasn't paying attention to the fact that it was for 6.06

---

### Post by bapoumba on 2010-05-21
> **tigs6969 said:**
> i dont think the downloading has anything to do with it as ive been using rapidshare for 4 years now no problems
yeah only files from /home are missing
and yes im using gnome

Then open a terminal and look at the output of:
```
ls -l
```
Do you see your files there ?

If so, it is a display problem.
Please start with
```
killall gnome-panel
```

If not, then you'll need some forensics: [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by tigs6969 on 2010-05-21
> **bapoumba said:**
> Then open a terminal and look at the output of:
```
ls -l
```Do you see your files there ?

If so, it is a display problem.
Please start with
```
killall gnome-panel
```If not, then you'll need some forensics: [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
not really the smartest 
when i did ls -l it just showed folders. how do i search in the folders?

---

### Post by bapoumba on 2010-05-21
> **tigs6969 said:**
> not really the smartest 
when i did ls -l it just showed folders. how do i search in the folders?
Not the smartest ? I am quite sorry. This is a way to see if your files are still there and you have a display problem or if your files are really gone.

By default, the terminal opens in your /home folder. If you have your folders present, chances are your files are not gone.

```
cd <insert_folder_name>
ls -l

```
will have you browse specific folders.

```
cd ~
```
takes you back /home.

---

### Post by tigs6969 on 2010-05-21
Thanks for that
I checked and nothing shows up in there

---

### Post by cbecker78 on 2010-05-21
1) Some questions:  When you boot up, do you still have a /home folder? Does your gnome panel show up?  If you had any customization to your theme (or used a theme other than default), is that customization still being used?Do you still have all of your programs?  Answering those will probably help folks trying to troubleshoot for you.

2) One thing that occurs to me is it is possible you somehow created a different user account, but I don't know.  Try booting a live cd and mounting your ubuntu partition.  see if there is more than one user account, see if you can view any files in /home.

*Until you fix this, it is probably important not to save any files anywhere.  If linux is like window (i don't know if it is)  it is possible that for some reason the headers of your files have been damaged or removed... this is what happens in windows when you delete something.  Although the file apears gone, all the data is still there, the OS just can't see it.  There are some tools in windows that will allow you to recover everything in such a cas eof accidental deletion or corrupt file headers.  I assume there is the same in linux, though someone else will have to chime in to say if that is the case.

---

### Post by Chesamo on 2010-05-21
> **cbecker78 said:**
> *Until you fix this, it is probably important not to save any files anywhere.  If linux is like window (i don't know if it is)  it is possible that for some reason the headers of your files have been damaged or removed... this is what happens in windows when you delete something.  Although the file apears gone, all the data is still there, the OS just can't see it.  There are some tools in windows that will allow you to recover everything in such a cas eof accidental deletion or corrupt file headers.  I assume there is the same in linux, though someone else will have to chime in to say if that is the case.
Correction: The file space is de-allocated from the file system. The headers are not deleted.

---

### Post by cbecker78 on 2010-05-21
@Chesamo: Ah.. I stand corrected.  Is there still a way to recover files that are in this unallocated space? 

@OP: Rereading the OP, I see that the gnome panel is gone too on the bottom.  What about on the top?  Did you ever try "killall gnome-panel"?

---

