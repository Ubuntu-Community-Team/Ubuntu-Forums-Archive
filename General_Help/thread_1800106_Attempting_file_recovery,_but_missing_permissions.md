---
title: "Attempting file recovery, but missing permissions"
date: 2011-07-08
forum: General Help
---

### Post by DuxWonder on 2011-07-08
Hello all.

I have a friend who uses Ubuntu as his OS. He was attempting to update from 10.10 to 11.04 by way of the update manager. 

However, I got a message from him this morning that a certain error code appears when he tries to boot up:

"The disc drive for / is not ready or not present".

My first instinct is to make an Ubuntu USB drive and recover the folder and files he wold like to save and format the drive from there. However, I ran into a roadblock there as well; When I try to copy and paste, I receive a message saying I don't have permission to copy the files.

I have two questions in this matter:
1:In worst case scenario, I would like to just save his files from the hard drive and start again. How do I change the permissions from my USB to be able to copy and paste the files?

2: Is the system (as-it-currently-is) savable?

I appreciate the assistance!

-DuxWonder :guitar:

---

### Post by lmarmisa on 2011-07-08
I will try to help you but maybe we will need more information about the problem:

1) The problem could be due to the read permissions of the files and folders that you are trying to copy. Try to copy them with root privileges (use **sudo**).

2) Boot into a Ubuntu Live CD / USB, open Firefox, visit the page [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) and follow the instructions for running the Boot Info Script. Finally, post here the results.

Best regards,

Luis

---

### Post by coffeecat on 2011-07-08
> **DuxWonder said:**
> My first instinct is to make an Ubuntu USB drive and recover the folder and files he wold like to save and format the drive from there. However, I ran into a roadblock there as well; When I try to copy and paste, I receive a message saying I don't have permission to copy the files.

I have two questions in this matter:
1:In worst case scenario, I would like to just save his files from the hard drive and start again. How do I change the permissions from my USB to be able to copy and paste the files?

I presume the USB is prepared from an Ubuntu ISO running live with the "ubuntu" account. If so, this is common problem caused by the UID of the live ubuntu account being 999 and the UID of your friend's account being 1000 (if his is the first created account). Simply open a root nautilus with:

```
gksudo nautilus
```

...and use that to copy the files. When the root nautilus window opens it will do so in the /root folder of the live filesystem. You need to navigate to where the hard drive partition is mounted (probably in a folder in /media) and thence to his home folder.

As to whether the system is salvagable, I agree with lmarmisa to run the boot info script. Don't forget to post the contents of the RESULTS.txt file between [noparse]```
 and 
```[/noparse] tags for clarity. You can use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the message toolbar for this.

---

