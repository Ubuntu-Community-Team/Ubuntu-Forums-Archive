---
title: "format drive from inside install disk?"
date: 2011-05-02
forum: General Help
---

### Post by webcabbie on 2011-05-02
So I have a dell dimension 4550

Its got 2 hd

one was blank and the other had winxp on it. I installed ubuntu to the blank hd and I thought i formatted the winxp hd but apparently i didnt. 

Now when my install boots it doesnt work. It keeps flickering etc and the folders only show for a milisecond.. its crazy

I just put the install disk in and ubuntu looks normal there. I wanna try to format xp off of the other disk. Any ideas?

---

### Post by TeoBigusGeekus on 2011-05-02
You can install gparted
```
sudo apt-get install gparted
```
run it
```
gksu gparted
```
and format xp.
But I don't think this will help with the problems in your ubuntu installation.

---

### Post by webcabbie on 2011-05-02
Im in it but the format option is not available? Is there a way to do this in the live cd? Thats where I am now

---

### Post by webcabbie on 2011-05-02
ok I got the format option open what should I format it to?

---

### Post by TeoBigusGeekus on 2011-05-02
You have to unmount the drive first: right click > unmount.

---

### Post by TeoBigusGeekus on 2011-05-02
Ah sorry, I didn't see your previous post.

The format file system depends on what you want to do with it. If you want to install windows again on it, then you should go with ntfs. If you want to use it for linux, then ext4 should be ok.

---

### Post by webcabbie on 2011-05-02
ill either use it as a storage device or reinstall ubuntu is there an option that covers both?

---

### Post by TeoBigusGeekus on 2011-05-02
Of course, ext4.

...and if you reinstall ubuntu, go with lucid or maverick - natty is just too buggy.

---

### Post by webcabbie on 2011-05-02
ur saying the latest version natty is just too buggy? will the live cd install earlier version?

---

### Post by webcabbie on 2011-05-02
Im not sure what I did but now it says unallocated with a grey icon for the whole thing

---

### Post by TeoBigusGeekus on 2011-05-02
No, you will have to create another live cd/usb.
See [here]("http://www.ubuntu.com/download/ubuntu/alternative-download#bt") for 10.04 and [here]("http://releases.ubuntu.com/maverick/") for 10.10.

---

### Post by TeoBigusGeekus on 2011-05-02
> **webcabbie said:**
> Im not sure what I did but now it says unallocated with a grey icon for the whole thing

You've deleted the partition. Now right click it and format it.

---

### Post by webcabbie on 2011-05-02
When I right click the only available options are new and information. I want to delete and reformat both drives and reinstall.. christ this is usually so easy

---

### Post by TeoBigusGeekus on 2011-05-02
Yes, select new (partition). After that you're going to be able to format the drive.

---

### Post by webcabbie on 2011-05-02
and if i do both in ext4 ill be able to use either for the install of the ox or as a backup drive for storage right?

---

### Post by TeoBigusGeekus on 2011-05-02
Yep.

---

### Post by webcabbie on 2011-05-02
**** i went back into install and selected the smaller drive to install the os on.. will it automatically create the swap? MAN...

---

### Post by TeoBigusGeekus on 2011-05-02
> **webcabbie said:**
> **** i went back into install and selected the smaller drive to install the os on.. will it automatically create the swap? MAN...
If you chose to "Install ubuntu on a whole wide drive" (or whatever it's called), I think it will.

---

### Post by webcabbie on 2011-05-02
ohhhfahh hearing some intense spinng..whirring.. im hoping the drive took the format o.k. Everyone cross your fingers and hold your breath

---

### Post by webcabbie on 2011-05-02
finished install still having the same problem.. anyway to fix it without reinstalling?

its like flickering? like the screen respolution is way too high? I cant even get to the terminal. 

Ill go find an earlier version while you guys think about it.

---

### Post by webcabbie on 2011-05-03
reinstalled 10.10 as suggested flicker went away seems to be running ok but a bit on the slow side.

This is only a p4 with 700mb of ram but I didnt expect it to be this slow. I have a processor monitor up and running on the tool bar and it spikes to 100% every time a page loads in the browser. I wonder how much some more ram would help it out?

---

