---
title: "Complete newb cannot find the iso file to burn"
date: 2009-07-06
forum: General Help
---

### Post by SCBrazil on 2009-07-06
Hi, 
My Kubuntu file just finished downloading. I'm a complete newb to this so I'm sorry if this is a ridiculous queston. I did check to see if someone else already posted and I could not find anything in the FAQs
.
My problem is basically this; where is the iso file that I have to burn?
After the download finished I got a 695mb .rar file on my desktop entitled  

kubuntu-9.04-desktop-i386

After unraring I got a folder with the same name and a bunch of other folders and files inside. What exactly do I burn therefore?

Thanks. It took me a day to download and I can't wait to see what this looks like.

---

### Post by Bradj47 on 2009-07-06
Inside the .rar file was there an .iso file? If so you need to use an ISO burner to burn it to disk. Google search for 'ISO burner for <your OS>'.

---

### Post by Jebtrix on 2009-07-06
Where you getting Kubuntu from that its in .rar format?

---

### Post by Jebtrix on 2009-07-06
There might be a slight chance that the .rar file is an misnamed .iso file. WinRAR would extract the misnamed file and not even tell you.. just tried it myself.

---

### Post by SCBrazil on 2009-07-06
[http://www.kubuntu.org/getkubuntu/download](http://www.kubuntu.org/getkubuntu/download)

---

### Post by Jebtrix on 2009-07-06
Rename the .rar file to .iso, and your burning program will complain if its not a real iso.

---

### Post by SCBrazil on 2009-07-06
I am working from inside Windows XP.
When I open the unrarred folder, inside I get these files;

wubi
md5sum
README
autorun
ubuntu

and these folders

pressed 
pool
pics
isolinux
install
dists
casper
.disks

inside the folders are more files, none of them a .iso file.

---

### Post by Jebtrix on 2009-07-06
Renamed the big .RAR file you downloaded to .ISO extension instead.

---

### Post by Jebtrix on 2009-07-06
Put it this way, if you extract the so called .rar file, in the Winrar progress window, if it says filesystem.squashfs anywhere that means the .rar file IS the iso.

---

### Post by Jebtrix on 2009-07-06
Can you see the file extensions of your files? If you can't WinRAR associated itself with .iso files.  So without seeing the actual file extension, your mistaken it for a RAR because .iso files have WinRAR icons.. get it?? Open My Computer > Tools > Folder Options > View Tab > **UnCheck** Hide extensions for known file types, then check....

---

### Post by SCBrazil on 2009-07-06
So far so good Jebtrix. It seems to have worked, thanks a lot. 
If I manage to install I'll post success from inside kubuntu.
For any future posters who get the same problem; there is no need to put a .iso after the filename (I did this and it burnt as .iso.iso) Just try burning the '.rar' folder as is cos it isn't actually a rar, just looks like one with that icon of all those books on top of each other. 
Thanks a lot Jebtrix

---

