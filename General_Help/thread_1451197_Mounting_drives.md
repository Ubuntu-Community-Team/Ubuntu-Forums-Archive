---
title: "Mounting drives"
date: 2010-04-10
forum: General Help
---

### Post by archeryrob on 2010-04-10
I am rebuilding some Pent 4 computers I picked up for some HTPC starter machines. The wife is never sold on this stuff, until see gets addicted to it.

I went out on the network and found my video and audio stored on a windows drive. I mounted the drive and have it displayed as a icon on the desktop for the shared folders (drives) on the windows machine

The file browser shows "music on rob" and "video on rob" as the drives, so they are mounted. The problem is I can not see them from in VLC or Amarok. They are only showing the local disk stuff. Once they are mounted I should be able to see them on every program, correct?

---

### Post by cogier on 2010-04-10
I presume these disk(s) are on a Windows machine. Can you see you see the Music/Video files if you double click on the Desktop icon? If you can't then it is in Windows that you will need "Share" the folders so that Ubuntu can see them.

---

### Post by archeryrob on 2010-04-10
I can see them from file manager and they are mapped, or mounted, and they are on a windows machine. I can right click on a movie and select "Open with VLC Player" and watch the movie.

I can only open previously opened video on the network from VLC and not click through the network like I can with file manager. It does not show the mounted drives. how can I change this?

---

### Post by Morbius1 on 2010-04-10
Nautilus creates an actual mount point but because of a cruel joke by the developers it's in a hidden directory:

**/home/your_user_name/.gvfs**

Note the "." in front of "gvfs". See if your application can see the hidden directory.

---

### Post by archeryrob on 2010-04-10
OK, I can see them with the command in VLC. Can i get them to permanently mount to VLC and Amarok? I tried draging ot the left and it will not stay.

Now showing twice on file managers and still not on VLC.

thanks, Morbius

---

### Post by archeryrob on 2010-04-10
Best I can get so far is that i created an Icon on the desktop for videos with path "smb://windows_machine/video/" and then it shows me all the videos. I can then right click and select "open with VLC"

But I still can not get it in VLC or Amarok. I want to be able to use these cheaper computers to stream videos to the TV's and set one for using Amarok like Itunes and stream play lists over the network to an amp in the garage to play music on the patio. So far, network connection without file manager is eluding me.

---

### Post by Morbius1 on 2010-04-10
You could try a symbolic link from the hidden directory to a "real" directory. Something like this:

Open **Terminal**
Type **mkdir /home/your_user_name/NetShares**
Type **ln -s /home/your_user_name/.gvfs /home/your_user_name/NetShares**

---

### Post by archeryrob on 2010-04-10
That did not seem to work. I did, how ever, right click on .gvfs and click "add to bookmarks" and it added that to the left menu. You try and do the same with the shared folders and they go in but disappear right away again.

it did make the NetShares folder but nothing was in it.

{EDIT}
OK, I must have typed some thing wrong. Your way did move .gvfs into netshares, but I got the save just adding a bookmark. So I guess there is no way to actually map a network drive and make it look like it's a drive on your computer.

---

### Post by archeryrob on 2010-04-10
Looks like Samba shares on Amarok is the way to do that. NetShare folder looks blank when viewing it from Amarok. I'll start a nother thread or search for this one.

---

### Post by archeryrob on 2010-04-11
I found this for anyone wanting to mount Network drives.

[http://happylinuxthoughts.blogspot.com/2008/05/permanently-mount-samba-or-windows.htm]("http://happylinuxthoughts.blogspot.com/2008/05/permanently-mount-samba-or-windows.html")


"Also, I've found many programs that aren't able to see samba shares,  even though the OS can."

---

