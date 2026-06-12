---
title: "another thread about broadcom chipsets"
date: 2006-05-09
forum: General Help
---

### Post by Xploit on 2006-05-09
I have searched these boards for 2 days trying to get wifi to work.....but nothing seems to cut it.

I have tried ndiswrapper from apt-get and the drivers straight from my windows partition and that was no luck.

I then tried the same ndiswrapper and .inf and .sys file from dell, that was no luck.

I then downloaded ndiswrapper 1.16 from source forge and that was no luck

last I tried ndiswrapper (same one from apt-get) , but this time I used bcmwl5a.inf instead of bcmwl5.inf (which is suppose to be the right one). and yet again it doesn't work.

every time I try ndiswrapper -l

I always get bcmwl5 driver present, but I have never in all those attemps gotten the "hardware present" part

Also, during my first few attempts "sudo modprobe ndiswrapper" would not output anything back.  Now it outputs "FATAL: Error inserting ndiswrapper (/lib/modules/2.6.12-10-686/misc/ndiswrapper.ko): Invalid argument"

I am wondering if this is because I went from 386 to the 686 kernel, but atleast "hardware present" should show when I type ndiswrapper -l.  

686-smp kernel would not work on my Dell Intel Duo laptop.  It would freeze at boot.

Anyone have any opinions?

---

### Post by Xploit on 2006-05-10
so no one has any sugguestions.......Maybe even a guess???  :(

---

### Post by hermesrules on 2006-05-10
[QUOTE=Xploit]so no one has any sugguestions.......Maybe even a guess???  :([/QUOTE]

Exploit, if you are running Dapper (or any kernel above 2.6.15) then you most likely have the native bcm43xx driver loaded on boot. It CANNOT coexist with ndiswrapper, and even though you might be seeing everything ok, your wireless won't work.

Unload the bcm43xx like this:

```
sudo rmmod bcm43xx
```

then do
```
iwconfig
```

to see what the output is. bcm43xx maps (at least on my machine) the wireless device on eth1, while ndiswrapper does it on wlan0.

You should also blacklist bcm43xx so that it doesn't get loaded on boot. You may have to reconfigure ndiswrapper to use the right inf file (not the sys!). I can't recall which was the file to do that, I think /etc/modprobe/blacklist, but to be certain do a search on the forums on "bcm43xx blacklist", and read some of the threads that will come up.

Hope this helps. This is how I fixed my wireless. Unfortunately, the native driver is not stable enough yet, and would drop the connection randomly. Therefore I chose to use ndiswrapper, and it's been working wonderfully.

Good luck!

---

### Post by Xploit on 2006-05-15
Well I did rmmod bcm43xx  and all it says was that module does not exist.  So obviously blacklisting it would not do anything.  So still no wifi :(

---

### Post by hermesrules on 2006-05-15
[QUOTE=Xploit]Well I did rmmod bcm43xx  and all it says was that module does not exist.  So obviously blacklisting it would not do anything.  So still no wifi :([/QUOTE]

Hm... When you do iwconfig, what's the output? Assuming you once had wireless running Ubuntu, do you remember what your wireless device was called? In my case it is wlan0, but if I use the bcm43xx driver, it becomes eth1. Note in the iwconfig output if there is anything different.

Another issue might be incompatibility between the version of ndiswrapper you are using and your kernel. This might be the thing for sure, if you compiled it from source, but later updated the kernel. The best thing to do is to find on the forums how to remove COMPLETELY ndiswrapper from your system. I think it is a matter of deleting several directories, but don't really remember which ones.

If you remember installing ndiswrapper via apt-get, then do

```
sudo apt-get remove --purge ndiswrapper
```

Then simply install ndiswrapper again via apt-get, and follow the instructions on setting it up using the inf file for your wireless. I think that in my case the file ending in a at the end did the trick, the other one would not work.

Also, if you type lspci, what is the output? Can you see your wireless card listed? If I remember correctly, even without any drivers working, you should still be able to see it when listing pci cards...

Well, that's all I can think of now. Good luck, and I hope it works!

---

### Post by Xploit on 2006-05-19
> Assuming you once had wireless running Ubuntu

Only time I had wireless was on Windows.

I am at work so I can't tell you what it says for sure.  

But Iwconfig says something like:

lo        no wireless extensions found
eth0    no wireless extensions found

lspci detected a wifi card that is how I matched the ID to the proper ndiswrapper driver on the ndiswrapper wiki.  

I followed the uninstall directions on that site and I deleted all the files relating to ndiswrapper.  I am gonna try again downloading the latest version and re-compiling it.

Thanks a lot for your help though.

---

### Post by hermesrules on 2006-05-19
You are certainly welcome. My hunch is you wouldn't need to compile ndiswrapper from source. Just use the latest version available in the repositories, and it should be fine. Recompilation may require a lot of manual work. Well, I have done it both ways, but compiling is the one I enjoyed less. I don't think I ever had to compile ndiswrapper on ubuntu though.

Take care, and hopefully you will have your connection soon, so that life comes back to normal! (at least that's how I feel)

---

