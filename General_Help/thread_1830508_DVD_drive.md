---
title: "DVD drive"
date: 2011-08-21
forum: General Help
---

### Post by DWSchwaab on 2011-08-21
I have a Gateway laptop with Natty Narwhale installed. I would like to simply watch DVD's sometimes, or write stuff to  a disc to take it off my harddrive. The problem is I can't get the drive to work!

I've looked everywhere my very limited computer skills know of and I can't find a driver to run the DVD drive that was already installed in the laptop. Can someone , please, tell me how I can find and load a driver so that I can use my DVD reader/writer?

I would really appreciate the help.

Dave

---

### Post by lmarmisa on 2011-08-21
Please, post the output of this command:

```

sudo lshw -C disk

```

---

### Post by seventyeights on 2011-08-21
Please run Applications/Accessories/Terminal and enter the command:
```
sudo lshw -C disk
```

If you see your dvd listed, then go ahead and install medibuntu and libdvdcss, instructions here:
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

You can use Brasero to make data dvds.

If you still can't get it to work, then please post the results from the above command.

---

### Post by DWSchwaab on 2011-08-23
I've learned that computers don't like me, so I take everything very slow and carefully. 

I put in the command and found my DVD drive, went to Medibuntu, installed what they said to install and did what they said to do. Nothing works! It still won't play a DVD because of the copyright. I also tried Brasero and burned a test disk. The result was unrecognizable by my computer and unreadable by another computer.

I just don't understand why things seem so complicated to me. Asking a DVD drive to play a DVD seems like a simple thing, so why can't I do it? I can use a flash drive to transfer information to another computer, but I can't save it by burning it to a disc. If the disc drive can't be made to do what it was made for, then a large part of my computer needs are unavailable to me!

By the way, the answer to that command was a long list of information, which I already used when I went to Medibuntu. I still need help to get this thing working; if you still need to know that stuff, I'll write it all down in my next post. It seems to me, the big problem is the need to get around the copyright! How do I do that?

Thanks for any help you can give me.

Dave

---

### Post by DWSchwaab on 2011-08-23
bump

---

### Post by seventyeights on 2011-08-24
It always works for me. My best guess is maybe you installed the wrong number of bits. 

First,  verify if your installed system is 32 or 64 bits with the command:
```
uname -m
```

i686 means 32 bit, amd64 means 64 bit

Second, check your install of dvdcss
```
dpkg -s libdvdcss2
```
and look in the list for "Architecture" 

If you got it wrong then you'll have to repeat the commands you did on that medibuntu page, but change "install" to "remove", and then install the right ones.

---

### Post by DWSchwaab on 2011-08-25
Okay, so we corrected the libdvdcss installation and now I can play DVD's.

Thank you seventyeights for your help!

Still not having any luck with using Brasero. though. When it reaches the end of the burn, it says it needs to eject the disc to finish and tells me to do it manually. As soon as I hit the button to open the disc drawer, it says the file is corrupt! The resulting disc is not readable on my computer, and not playable on another.

What am I doing wrong?

---

