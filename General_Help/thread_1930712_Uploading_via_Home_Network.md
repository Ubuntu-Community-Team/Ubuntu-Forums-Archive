---
title: "Uploading via Home Network"
date: 2012-02-24
forum: General Help
---

### Post by Vic Wintergreen on 2012-02-24
I want to be able to upload to SoundCloud tracks that are on another computer on my home network. However when I am given the upload locations there does not appear to be a link to the network. How can I add this feature, if indeed it is addable (word?). Thanks in advance. Vic

---

### Post by greenpeace on 2012-02-24
Hi Vic, word! [1]

Is the remote machine unix-based?  You might get some mileage mounting the drive over ssh [2]... but that seems to be a lot of work. 

I tried with sFTP but no luck... you might just have to resort to copying the file to your local machine first.


[1] [http://www.thefreedictionary.com/Addable](http://www.thefreedictionary.com/Addable)
[2] [http://www.ubuntugeek.com/mount-a-remote-folder-using-ssh-on-ubuntu.html](http://www.ubuntugeek.com/mount-a-remote-folder-using-ssh-on-ubuntu.html)

---

### Post by wubrgamer on 2012-02-24
j

---

### Post by Vic Wintergreen on 2012-02-24
The home network is the standard MicroShaft one I created with the set up on my XP disc. I can find all active computers on my network via the network tab in Ubuntu (some run XP, some Vista and some W7) so dragging the file over isn't a problem. I edit music on a XP PC and store the wavs on an internal SATA drive which is shared over the home network. The idea is to upload the wavs (some of which are over 300mB) whilst I am still editing in my DAW. I was checking to see if I can add the network to an upload destination folder, much as it is in the MS Home network. If it can't be done, so be it. I use a common monitor for the two PC's and the PC's are in the same room, so I can just throw them on a stick and waz them that way if the network option isn't a goer. Thanks though. Vic

---

### Post by greenpeace on 2012-02-24
I can't see any simple way to achieve it.. Sticking them on a usb and moving it that way will be the easiest thing!

---

### Post by LewisTM on 2012-02-24
So what you wanna do is "Save" a file from a sound editing software in Ubuntu (which one?) to an MS network?
Depending on the capabilities of your software you may take two shortcuts.

You can navigate to your network share/folder in Nautilus and create a bookmark. With some luck the bookmark will be available in the file selection dialog of your sound app.

Lots of apps don't support that directly. What you can do instead is open up Nautilus and go to your ~/.gvfs directory (it's hidden so enter it manually or reveal hidden files). Bookmark that and call it something like 'File Shares'. 
If not done already, connect to your share on the MS network with Nautilus. Then in the save file dialog, choose the 'File Shares' bookmark and then the directory called '{share} on {server}'.

Hope this helps!

---

### Post by Lee_Bo on 2012-02-24
Another way, although lengthy, may be to "connect to server" and connect to the remote folder/drive.  Then save your files on your laptop and drag/drop to the remote directory.

---

### Post by Vic Wintergreen on 2012-02-24
Sorry Lewis - I wasn't clear. I am using PreSonus on an XP PC and saving the wavs on the SATA drive in that PC. The drive is shared over the home network. If I browse my network in Ubuntu, I find the drive and folders and files. What I don't find as an upload option is my network when asked to select files for uploading. I think under Windows, the network appears as a location when asked to select files for uploading. I may be wrong, I will check later. Thanks for all the help, will look into some of the work arounds. Vic

---

