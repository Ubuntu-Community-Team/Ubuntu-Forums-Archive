---
title: "Mounting a network drive in ubuntu 11.04"
date: 2011-12-04
forum: General Help
---

### Post by jdc.84 on 2011-12-04
Hi,

I've just recently given another go to Ubuntu. I've got 11.04 all running smoothly, most of the drivers work and the programs insalled appropriately..

However I have a _**seagate freeagent golflex home**_ on my windows home network.

I can access the drive via a web browser on ip address '192.168.1.6' in ubuntu.

Does anyone know a way i can mount this ip as a drive on ubuntu?

The IP address also requires a username and password.


[I]I found the [following guide]("http://www.automaticable.com/2008-01-18/how-to-mount-a-network-drive-in-ubuntu/") but it returns:
Warning: mapping 'guest' to 'guest,sec=none'
Retrying with upper case share name
mount error(6): No such device or address
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
[/I]

---

### Post by Morbius1 on 2011-12-04
Open a terminal ant type:
```
nautilus smb://192.168.1.6
```When Nautilus opens up to that location bookmark it: Bookmarks > Add bookmark. It will then show up on the left side panel of Nautilus just like a "mapped drive" does in Windows.

---

### Post by jdc.84 on 2011-12-04
Brilliant, just the job thank you very much :)

---

### Post by jdc.84 on 2011-12-04
Will this work without using the guide I posted in the OP?

Secondly, is it possible to rename the drive as it appears in the left column in Nautilus? 
At the moment it is labeled 'goflex home public on 192.168.1.6'. I went to edit the bookmark and re titled the bookmark 'Network Drive', however in the left hand column in nautilus it is still refering to the drive as 'gofle....'.

---

### Post by Morbius1 on 2011-12-04
> Will this work without using the guide I posted in the OP?
Yes. 
> Secondly, is it possible to rename the drive as it appears in the left column in Nautilus? 

Yes, right click the bookmark and select Rename.

---

### Post by jdc.84 on 2011-12-04
Hmm... When i right click on the icon in the left hand column in nautilus i do not get an option to edit or rename it.

I can only rename the files within the drive, bu not the drive it self.

---

### Post by Morbius1 on 2011-12-04
Give me a minute while I bring up 11.04 and see if I can reproduce this problem.

---

### Post by Morbius1 on 2011-12-04
That's interesting. You are correct it cannot be renamed. Must be some Unity thing.

As a workaround, once the share appears in Nautilus drag and drop the name from the location bar to the right side of nautilus below the line where Documents, Pictures, etc.. are listed not above it as it appears now. You should be able to right click > rename at that location.

[COLOR=Blue]**EDIT**[/COLOR]: I meant left side of nautilus. Sorry

---

### Post by jdc.84 on 2011-12-04
Thanks for all the help so far by the way...

In the left hand column in nautilus i cannot drag any of the drives around.

I currently have 'home' 'file system' 'goflex home public on 192.168.1.6' in the left hand column, i cannot drag any of them around nor can i edit any of them either.

On a side note, i plugged a usb stick (it found it instantly) in and i cannot rename this drive either.

---

### Post by Morbius1 on 2011-12-04
You're not dragging any of the items on the left panel of Nautilus. You are dragging the icon in the location bar at the top of nautilus to a location under the line at the left panel of Nautilus.

---

### Post by jdc.84 on 2011-12-04
Hmm, well i tried dragging from what i thought was the location bar but to no avail.

I searched for an alternative, and found 'File Manager' which seems to to have copied or is using all the book marks i made in nautilus. Further more the renaming of the bookmarks i did in nautilus has now appeared in the tree on the left hand side of 'File Manager'

I now have 'Network Drive' instead of 'GoFlex....'. 

Thanks for all your help, very much appreciated. I think i will give it a rest now for this evening though.

---

### Post by MuRozvi on 2011-12-11
The solution given here is some what misleading. What the solution does is just book mark the drive, it does not mount the drive.

---

### Post by Morbius1 on 2011-12-11
> **MuRozvi said:**
> The solution given here is some what misleading. What the solution does is just book mark the drive, it does not mount the drive.
Technically correct but it depends on how the user uses the remote share. 

If he uses Nautilus to connect to the remote share then selecting the bookmark will connect, mount, and display it's contents. To the user it's seamless.

---

### Post by jdc.84 on 2011-12-11
I'm starting to get the jist of ubuntu.

Whether it maps the drive or bookmarks its location doesn't really matter to me as long as i can see it.

I can change the name of the bookmark no problem, however i can't seem to get nautilus, in the left hand panel, to change the bookmark name.

Anyway, i had some other trouble with Ubuntu screens: [http://ubuntuforums.org/showthread.php?t=1893036](http://ubuntuforums.org/showthread.php?t=1893036)

And am now having to reinstall ubuntu. My knowledge of the operating system is very low and this will be the least time consuming method i think

---

### Post by jdc.84 on 2011-12-15
Ok, so my computer is back to normal and ready.

So, using the method of bookmarking an IP address isn't really fool prove...

One example, 3 days ago we had to reset our modem. Not just turn on and off, but press the reset button. Thus all settings were lost... As a result the modem remapped the network drive to a different port.. consequently the bookmark on ubuntu then became broken as it was hard coded in to search for a specific address.

On the windows computers using the network drive, they (each computer) each have a program (supplied by seagate) which searches for the drive. I can only assume then that this program doesn't look for an ip address but instead looks for a mac address...

"bookmark" - the term I find a little confusing as is often/typically associated with internet browsers. When i began to explain this to my Dad it took a while... And i can bet that he will have forgotten the next time he loads up ubuntu as bookmarks have been cemented in his head over 15 years as links to website, not network drives in the equivalent of windows explorer on ubuntu

Either way, is it possible therefore to mount a network drive by mac address? Or is there an equivalent to "Network Places" as found in windows, so i can mount the drive by name as found in "Network Places"?

---

### Post by Morbius1 on 2011-12-15
> Or is there an equivalent to "Network Places" as found in windows, so i  can mount the drive by name as found in "Network Places"?
Open Nautilus and select "Network"

If you can't find it there then post the output of the following command please:
```
smbtree
```BTW, Some routers give you the option of forcing it to supply the exact same ip address to the same client using something called "DHCP Reservation".

---

### Post by jdc.84 on 2011-12-15
> Open Nautilus and select "Network"

Thanks. 
I had Nautilus in 'Tree' mode on the left hand side. As a result it wasn't showing "Browse Network". I put it to "Places" and it became visible.

I now have the bookmark as:
smb://goflex_home/ which is working a treat. :)
______________________________________________________________________

However there is now another problem with the network drive.


I have Ubuntu on 2 computers now (a desktop and a laptop). Both have the nautilus bookmarking the network drive via name. 

I can write edit and delete items on the drive in Nautilus, however when i open Libre (which i am assuming is the Ubuntu version of openOffice writer), i cannot save a document i create to the network drive.

When I open Libre, create a document, try to then save the file to the network drive i get an error (on both computers) reading:
"Error saving the document Untitled1:
General Error.
General input/output error."

It says the same message what ever i try to save the file as... Any ideas

(this also happens in Calc.
I just tested in the basic Text Editor and this can write to the drive)

---

### Post by Morbius1 on 2011-12-16
The thing with LibreOffice is a known "problem". Not sure if you would call it a bug since it's doing what it's designed to do but you might want to look at post #4: [http://ubuntuforums.org/showthread.php?t=1645957](http://ubuntuforums.org/showthread.php?t=1645957)

[COLOR=Blue]NOTE[/COLOR]: I haven't done this myself since I use these external drives as backup vehicles not as interactive storage resources. So if I were you I would make a backup copy of the file before you edit it. You also don't have to use nano to edit the file since that requires a learning curve to use, so I would edit it with gedit as root:
```
 gksu gedit /usr/bin/soffice
```

---

### Post by jdc.84 on 2011-12-16
OK, thank you! I will have a read of that post and see if i can try and fix the problem :)

(so far all the problems i've hit have been fixable, hopefully this time round i'll be able to stick with Ubuntu and not have to return to windows :D )

---

### Post by jdc.84 on 2011-12-22
Hi, 

Well, after a great deal of time investment i have decided to revert back once again to windows.

The last time I tried Ubuntu was version 9. The improvements from then are quite noticable (one big issue in 9 was the os could not come out of sleep) but unfortunately there are still too many nuances which get in the way of day to day tasks.

Things I personally found hard:
1 - When i start the computer or log in as a different user i can't get nautilus to automatically load up the "bookmarks". In my case we have a network drive accessed by 6 computers thus all info must be stored on there. It would be very nice to just have the "bookmarks" load up automatically. Or better still be able to mount properly a network drive. Although i do not even know if windows does this when you click "map network drive".

2 - For some reason i cannot rename the network drive in the tree view in nautilus which is confusing to a few. I can rename the bookmark, but i cannot get the link to the network drive to show the name change in tree view

3 - I love the Natty GUI however it is insanely annoying to have the launcher disappear all the time. And i searched but could not find an easy way to get the thing to stay out.

4 - As a windows user and web developer, i am very used to key board shortcuts... i would have loved to have seen a chart displaying all the standard windows shortcuts with the Ubuntu equivalents. Some were the same but some were not. As crossing over from windows is quite a change, a chart even including the options available on windows but not on ubuntu would have been very good to read.

5 - The computer i was testing the new ubuntu on was a reasonably high spec yet the GUI of natty was often slow.


Basically, i am very busy every day with work and simply do not have the time to spend half an hour to an hour trying to find out how to do something or fix something ata every step of the way.

With libre for example, i found a work around by using a completely different program AbiWord... but then there were tonight an array of problems with images being pasted into a document. When ever i played with the wrapping the image became huge and distorted.

I appreciate the input people are giving to world of open source programs, and if i could i would contribute. However right now i simply do not have the time.

---

### Post by Morbius1 on 2011-12-23
That decision is yours of course and I will not argue with that decision but ....
> 1 - When i start the computer or log in as a different user i can't get  nautilus to automatically load up the "bookmarks". In my case we have a  network drive accessed by 6 computers thus all info must be stored on  there. It would be very nice to just have the "bookmarks" load up  automatically. Or better still be able to mount properly a network  drive. Although i do not even know if windows does this when you click  "map network drive".
Gigolo will do what you want: [http://ubuntuforums.org/showpost.php?p=9941016&postcount=3](http://ubuntuforums.org/showpost.php?p=9941016&postcount=3)
> 2 - For some reason i cannot rename the network drive in the tree view  in nautilus which is confusing to a few. I can rename the bookmark, but i  cannot get the link to the network drive to show the name change in  tree viewI can't explain the inability to rename the "drive" but I never use Tree View. If you use Gigolo all of these remote shares will mount automatically and you can find them all at /home/user-name/.gvfs. Make a bookmark to that location.

Items (3), (5), and possibly (4) is the reason the gods invented Xubuntu. Xubuntu or more precisely the XFCE Desktop Environment ( DE ) was created for a desktop ( and I'll include laptop to that description ) computer and reflects the philosophy that a DE is a platform to get something else done not an application that requires a new paradigm to be learned.

---

### Post by jdc.84 on 2011-12-23
Ah man... :P... Well now that sounds tempting to enter back into linux... Xubuntu and Gigolo (sounds a little x rated), i'll give them a go.

Cheers

---

