---
title: "aircrack problem"
date: 2009-11-04
forum: General Help
---

### Post by rastro123 on 2009-11-04
Hi, I was using aircrack, and everything was working ok, then I did a reinstall of 9.04, as the wireless doesn't seem to work in 9.10. I installed to / which is where I think it was before, but now the aircrack suite is not putting files into my home folder - the fragment files etc, when I go to aireplay. It tells me that the files do not exist. However today I went to use unetbootin and I saw when I was looking for a file, that all of the files related to the aircrack process are in my /root folder, and not in the home folder. So I assume this is why when I try to run packetforge, it says the file does not exist. What can I do about this? I just tried to reinstall ubuntu telling it to install in /home but it wouldn't let me, saying I need to specify a root system. I tried to access the root folder to move the files to my home folder, but it won't let me access it. I'm most grateful if anyone can help me with this, I don't get it, - it was all working fine before the reinstall. Thanks.

---

### Post by phillw on 2009-11-04
> **rastro123 said:**
> Hi, I was using aircrack, and everything was working ok, then I did a reinstall of 9.04, as the wireless doesn't seem to work in 9.10. I installed to / which is where I think it was before, but now the aircrack suite is not putting files into my home folder - the fragment files etc, when I go to aireplay. It tells me that the files do not exist. However today I went to use unetbootin and I saw when I was looking for a file, that all of the files related to the aircrack process are in my /root folder, and not in the home folder. So I assume this is why when I try to run packetforge, it says the file does not exist. What can I do about this? I just tried to reinstall ubuntu telling it to install in /home but it wouldn't let me, saying I need to specify a root system. I tried to access the root folder to move the files to my home folder, but it won't let me access it. I'm most grateful if anyone can help me with this, I don't get it, - it was all working fine before the reinstall. Thanks.


hi, there is an active thread for all things aircrack over here ... [http://ubuntuforums.org/showthread.php?t=528276](http://ubuntuforums.org/showthread.php?t=528276)

They should get you up and running,

Regards,

Phill.

---

### Post by rastro123 on 2009-11-04
thanks mate, I'll have a look now

---

### Post by badger_fruit on 2009-11-04
Strange problem but perhaps something like this would be best asked :- [http://www.remote-exploit.org/community.html](http://www.remote-exploit.org/community.html)

EDIT >>>>>>>
Or that other link someone posted above!

---

### Post by rastro123 on 2009-11-04
ok, I'm on it! I just found out how to access the root folder - gksudo, I didn't know this before. I'm thinking, run aicrack again and when I need to run packet forge, first I go to the root folder and copy the files to my home folder and see if that is ok. Thanks guys for advise.

---

### Post by rastro123 on 2009-11-04
no, that idea didnt work, I just tried to copy from root folder to home folder and it wont let me. I need to be able to tell aireplay to put the files in my home folder and not the root. Frustrating. I'll go to remote exploit and see whats said.

---

### Post by rastro123 on 2009-11-04
Ok, quick further update - I got all the files in my home folder now using the command sudo nautilus - Im not exactly sure why it wouldnt work a moment ago.

---

### Post by phillw on 2009-11-04
> **rastro123 said:**
> no, that idea didnt work, I just tried to copy from root folder to home folder and it wont let me. I need to be able to tell aireplay to put the files in my home folder and not the root. Frustrating. I'll go to remote exploit and see whats said.

```
sudo cp -p /*filename* /home
```

Will copy the files named in *filename* over to your home directory & preserve permissions. You can use wildcards, e.g. air*

the -p means that they won't switch over to being owned by root, which can cause problems.

Phill.

---

### Post by phillw on 2009-11-04
> **rastro123 said:**
> Ok, quick further update - I got all the files in my home folder now using the command sudo nautilus - Im not exactly sure why it wouldnt work a moment ago.


sorry for the delay ... my system created a crash-dump while I was writing the sudo cp instruction ... just finished filing it.

Phill.

---

### Post by phillw on 2009-11-04
> **rastro123 said:**
> Ok, quick further update - I got all the files in my home folder now using the command sudo nautilus - Im not exactly sure why it wouldnt work a moment ago.

An important btw ....   airero can cause quite large files, when you have copied them over from root, you would be advised to **rm** them, as it appears you're having to use sudo commands, please check your **sudo rm** before you issue it - you don't get any "Are you sure Y/N" stuff !!!!

Phill.

---

### Post by rastro123 on 2009-11-04
thanks mate. I copied the files over, but after I posted I realized that the little padlocks were on my files, and so when I tried to run packetforge, it came up with error. I'll go through the process again and try what you say. Thanks again.

---

