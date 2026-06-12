---
title: "iso file extraction issue"
date: 2010-08-15
forum: General Help
---

### Post by irishpunk76 on 2010-08-15
I downloaded an ISO of some nes roms and used the archive manager to extract the files. It extracted them but it added a ;1 to the end of the extension. I don't want to go through 3500+ rom files and delete the added ;1 to the nes extension. How can I prevent this in the future?:popcorn:

---

### Post by Herman on 2010-08-15
:D Hello irishpunk76, 
I don't know anything about .nes rom files or extracting files from an .iso with archive manager, but since you have been waiting so patiently for several hours now and nobody else has helped you yet I'll give it a try and see if I can be of any help.
```
#!/bin/bash
# a script for renaming .nes;1 files to .nes
for f in *.nes*; do mv "$f" "${f%.nes;1}.nes"; done
``` If the above script is dropped into a directory full of files with the '.nes:1' file name extension it should rename every file with the '.nes' extension, getting rid of the ';1' characters for you.


For extracting files from an .iso, I normally mount the .iso first with a command like, 
```
sudo mkdir /media/mycdproject
``````
sudo mount -o loop -t iso9660 mycdrom.iso /media/mycdproject
```
Where: the .iso file to be mounted is located in my /home/herman directory
    Where:  the name of the file is 'mycdrom.iso'
    Where: the mount point you made for it is named '/media/mycdproject'
    If not, please alter the command to suit your particular computer's setup.
**Note:** We can read and copy from a mounted .iso file but we can't write to one.  At least I haven't been able to find out how.
To alter an .iso file we mount it so we can copy the contents to a regular directory. 
Then we do whatever work we need to do, and then make a new .iso file out of the directory with a genisoimage command. 

I'm not sure about why it's necessary to use archive manager for what you're trying to do, I'm only guessing, so if I'm telling you something that's not applicable to your situation, then I'm sorry if I'm wasting your time. :D

---

### Post by irishpunk76 on 2010-08-17
Thanks a ton for that script. I know nothing about scripting aside from batch files in windows. I didn't even know how to get that to run under linux so I just copied into gedit and did a google search and found my answer. Ran it and it worked like a champ. I really appreciate your response. Again THANKS!

---

### Post by Herman on 2010-08-17
:D That was the first time you've ever run a bash script?
Well done for being clever enough to find out what to do and give it a try.
You have sampled just a small morsel of the magical powers of GNU/Linux.
May the force be with you.

Regards, Herman :)

---

