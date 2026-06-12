---
title: "Seperate hdd dual boot"
date: 2010-08-27
forum: General Help
---

### Post by Corey4666 on 2010-08-27
Hey everyone, I have not used ubuntu in a while because I've been using dial up and had no luck with my hardware modem.

Anyways I got satellite internet now. I been wanting to install ubuntu. I have 2 seperate hdd's a 250gig and 80gig. 1 sata and 1 ide. I want to install ubuntu on my 80 gig sata. 

I know how to install to my 2nd hdd, I've done it in the past. I did however boot my system after installing and it would automatically pick to log into ubuntu and not windows. I was curious on what I should do to get the dual boot working on start up? 

It might be important to note that I will be using Ubuntu 7.10 for right now. I can not download ubuntu since I have a 250mb limit per day. I might be able to get the new ver in the future but as of now my internet always disconnects at my unlimited download time of 3:00-7:00am .....

---

### Post by quixote on 2010-08-28
Remember, it's exactly for people with slow (or no) connections that the [ship a free LiveCD]("http://www.ubuntu.com/desktop/get-ubuntu") program exists.  Admittedly, they warn that it can take forever for it to arrive... :(

About your main question: does grub not even give you a choice of Windows, or is it just that the default is ubuntu?  I'm assuming that with 7.10, you're using the old grub, not grub2.  (There are complete instructions [here]("http://members.iinet.net.au/~herman546/p15.html#menu.lst").)

--If there's no Windows option at all:

If your Windows is, say on the first partition of of the first HD loaded by the BIOS, that would make it /dev/sda1.  So, in /boot/grub/menu.lst you need the following lines:```

title        MS Windows and-any-other-descriptive identifiers-you-want
root        (hd0,0)    *[if windows is on the 2nd HD, 1st partition, /dev/sdb1, this would be root (hd1,0)]*
savedefault     *[I don't remember using this.  Not sure it's necessary.]*
makeactive
chainloader    +1

```


--If you have the option, it's just not the default:

The default is usually the first one in menu.lst, right after 
### END DEBIAN AUTOMAGIC KERNELS LIST towards the end of the file.  The numbers start from 0, so if Windows is the fifth possible choice (eg two Ubuntu versions, each with a recovery option), then "default  4" would make the fifth (Windows) entry the default.  The default option is near the beginning of menu.lst:```
## default num
default        0
```

---

