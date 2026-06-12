---
title: "It's like I have someone else's computer."
date: 2011-02-11
forum: General Help
---

### Post by ewaynec on 2011-02-11
I was recording a DVD when I wanted to look at a folder to see if there was a file there. I went to "places", as I always do, and a window poped up asking for a password. This has never happened before. I entered the password and went to the folder. I always view folders as "list", then they displayed as "icons". I finished the recording and re-started. It still appears the same, and when I open programs I notice little differences in the way things look and feel. 
  The reason I was recording DVD's was to get some of the movies off my hard drive. It was down to 81Gbs free, It now says there is 365 Gbs free. I have searched everything and I see nothing missing. 
  I am baffled, any ideas.
     Wayne

---

### Post by aeiah on 2011-02-11
sounds like you've accidentally hacked into someone elses computer. do you often find yourself in strange places without any memory of how you got there? :(


ahem. anyway...

this does seem very strange. how is your computer set up? do you have several different partitions? perhaps you have 81GB free on home, but 365GB free on another partition? or perhaps this network location you selected has more free space and that's what you saw...

---

### Post by JOHNNYG713 on 2011-02-11
Hmmm, Are you the only user ? Do you have any Guest users ? Have you opened System> Administration> Users and groups, And poked around in there ? Sounds to me like you might be logged in as another user or Root ! Or some how your permissions got screwed up !

---

### Post by ewaynec on 2011-02-11
I am the only user. I have a 500 Gbt hard drive with 1 partition. No other OS or HDD. I have been using Ubuntu for a couple of years, I am still a novice. I am currently on 10.04, and have been since 10-04.
  This may be related, I was looking at putting some things on my USB drive, (a 4 Gbt Patriot) when I noticed that it had 3.7 Gbt. where it had always had 4.0. I tried to format it and it always came back with 3.7 Gbt, it had always shown it to be 4.0 Gbt. there was a folder on it (lost and found)with nothing in it. I tried to delete it, (move to trash, then empty the trash) it said I did not have permission. I tried this several times without success and gave up. I then tried to record the DVD, and that is where I noticed the problem, as mentioned above.
  No I do not smoke whacky tabacky, nor did I have a drink until after this.

---

### Post by lisati on 2011-02-11
Movies and DVDs can use up a lot of disk space very easily. With DVDs, we're talking gigabytes here. A standard single layer DVD can easily use up 4.7Gb. Commercial movies (ahem, legal backups only I hope!) and double-layer DVDs can easily use up 8.5Gb.

---

### Post by corncob on 2011-02-11
> **ewaynec said:**
>  there was a folder on it (lost and found)with nothing in it. I tried to delete it, (move to trash, then empty the trash) it said I did not have permission. I tried this several times without success and gave up. 

When this happens to me I launch the file browser with
```
gksudo "dbus-launch nautilus --no-desktop --browser %U"
```
I had copied the code from somewhere in these forums and made a launcher out of it to use in these cases.  When the browser is open you might want to click on preferences in the Edit menu.  Then, in the Behavior tab, check "Include a delete command that bypasses trash".  That way, when you right-click the directory, you can delete it directly without going through root's trash.

---

### Post by ewaynec on 2011-02-14
OK forget all the other stuff, I can live with it, but will someone tell me why I have to put in my password to browse my files, and how can I change where I don't have to.
   Wayne

---

### Post by ewaynec on 2011-02-14
I just did some checking and found; When I go to Places, Home folder, it ask for a password. When I go to Places, Computer, and step through to the home folder, it accesses it without a password. I can open any folder on the computer this way, but I cannot go to Places, home folder without a password. I have read every help file I can find, looked on every forum I can find, and I don't see a solution. 
  I'm stumped, I hope you are not.
     Wayne

---

### Post by tredegar on 2011-02-15
Somehow the "Home" nautilus bookmark has become associated as not "Open this directory with nautilus" (which would be correct) but as "Open this directory as administrator" (which is not what you want). So you are asked for the password.

This second option is normally on the R-click menu, and is not the default. Somehow it has become the default.

You could navigate to computer ... home and try R-ckicking your username, choose Open with ... Other application .. File Browser, and check "Remember this association".

If that doesn't work you could try opening nautilus, editing the bookmarks, and taking a look at the Home one. Does it look strange? If you can't edit it to make it look like the other bookmarks, then maybe just delete it and then recreate it by navigating to computer - home - username and then Bookmarks .... Add bookmark.

There's another way to do all this by editing something about mimetypes, but I don't have the link.

---

### Post by ewaynec on 2011-02-17
Alright, I said I would be happy if I could access my personal folder without a password. I am happy. Thanks to "tredegar", you got me going in the right direction. 
  My personal folder ("wayne") was owned by me, but the "home" folder was owned by root. I changed the ownership of "home" to "wayne" and it works without a password.
  Thanks to all.
     Wayne

---

### Post by tredegar on 2011-02-17
Pleased you got it fixed up.

---

### Post by ewaynec on 2011-02-23
Actually I didn't get it fixed. I tried it and it worked, so I posted that it was fixed, then the next time I tried it , it asked for the password. Now sometimes it does and sometimes it doesn't. I am more baffeled now

---

### Post by tredegar on 2011-02-23
OK.

Give the following command in a terminal
```
nautilus /home
```
When nautilus opens, R-click your username
Click Open with ... Other application
Choose File browser from the list.
Check the "Remember this" 
Click Open.
[I did ask you to do this before, but you did not say if you tried it, or what happened.]

If that doesn't work, please post the output of the following commands

```
cat ~/.gtk-bookmarks
ls -al /home
```

---

