---
title: "Cannot save or open anything"
date: 2009-08-21
forum: General Help
---

### Post by HolyMythos on 2009-08-21
I just installed Ubuntu today and everything seemed to go fine. I dual partitioned between Vista and Ubuntu. I got the 9.0.4 version of Ubuntu, can't remember what it was called.

Well, everything was going fine until I got a popup about automatic updates. The updates had a filesize of 414M, and my harddrive had more than enough space to hold it, so I went to start the download. It then gave me an error saying that there wasn't enough diskspace in "/". I don't know what that means, so I figured it meant my harddrive. I went to check my harddrive and noticed it was named "235.4 GB Media". It asked to mount it when I tried opening it, which worked when I put in my password.

I can't open up some programs either. For example, OpenOffice won't load. I try to update Firefox and it tells me that I don't have enough space. It said that it would copy over some of my files from Windows but it didn't. What's the problem?

---

### Post by Soapy.Illusions on 2009-08-21
Can you go into your terminal window (it is one of your applications)
 
type in 
 
```

sudo fdisk -l

```
 
I am doing this by memory and not 100% sure that is the command... but anyways if I was right can you just copy paste the output here

---

### Post by cariboo on 2009-08-21
From what you are describing, you don't have enough space on your / partition. Could you open an Applications-->Accessories-->Terminal and type:

```
df -h
```

This will print out on screen a listing of your partitions, with how much space has been used eg:

```
df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hdb1             7.2G  2.2G  4.7G  32% /
tmpfs                 220M     0  220M   0% /lib/init/rw
udev                   10M  152K  9.9M   2% /dev
tmpfs                 220M  4.0K  220M   1% /dev/shm
/dev/hdb3             1.8G  1.7G   91M  95% /home
```

as you can see from the above listing /home is just about full. Paste the output of the above command, as I suspect your / partition may be to small.

---

### Post by HolyMythos on 2009-08-21
Give me a minute. I freaked and went back to Vista because I thought I broke everything. That normally happens whenever I try to do something different with my computer. Lemme go back to Unbuntu. I think you're right:

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             2.3G  2.3G     0 100% /
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G   92K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G  168K  1.5G   1% /dev
tmpfs                 1.5G  508K  1.5G   1% /dev/shm
lrm                   1.5G  2.7M  1.5G   1% /lib/modules/2.6.28-11-generic/volatile
overflow              1.0M   16K 1008K   2% /tmp
```

---

### Post by HolyMythos on 2009-08-21
How do I put more space on it?

---

### Post by Soapy.Illusions on 2009-08-21
You can use what is called gParted

Boot off of your live cd 

In a terminal window type

```

sudo gparted

```

From there you can mess around and make any changes to your partitions, and nothing will happen until you press Apply

BE WARNED... backup everything! gParted can be very dangerous if you do not know how to use it

---

### Post by zkriesse on 2009-08-21
OR! you could re-load the Ubuntu Live CD and set up the partition again. Give yourself at least a 1/4 or the hardrive for Ubuntu. If you become a hardcore Ubuntu user like some of us then you'll want more space for Ubuntu...

---

