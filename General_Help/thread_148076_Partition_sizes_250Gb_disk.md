---
title: "Partition sizes 250Gb disk"
date: 2006-03-21
forum: General Help
---

### Post by jethro10 on 2006-03-21
Hi everyone, I'm going to set up my first proper linux box and want advice on partition sizes.
I have set-up linux before so am a little familiar but this is my first serious non dual boot system, dedicate to me learning it proplerly.
On my windows I have a Drive C: of 20Gb with 140Gb as Drive d: which is all storage and "My Documents", so if I screw up I can re-install without losing my data.

I see the same is with linux with the /home/ directory becoming drive D: in my comparison here.
The Pc will be 250Gb in size and want advice on partition sizes. I dont want to make the /home/ too big and run out of places to install software etc.
any ideas ?
Thanks in advance

Jeff

---

### Post by AndrewCaul on 2006-03-21
Is this a seperate drive you want to partition or is it the one with Windows on it?

---

### Post by jethro10 on 2006-03-21
Hi,
Its a brand spanking new PC, supplied OS free and going to be used for Ubuntu only.

PS : Sorry, I realise i've probably posted into the wrong forum also.

Jeff

---

### Post by jethro10 on 2006-03-22
Hello !!
Is anyone there !!

So if all else fails, I give 200 of 250mb to home directories and let the system split the rest out ? I just dont know how much space installing packages take on linux so dont have a 'feel' for what to give it.
My new PC arrives tomorrow :-)

thanks
Jeff

---

### Post by MJSOnline on 2006-03-22
250GB eh...  Ok  why dont you  let the install package auto partion it for you? I have mine at 4GB system, 512MBSwap and rest as data. M

---

### Post by jethro10 on 2006-03-22
Actually, I never though of letting it do it itself !

Sounds like a plan.
The good news is my PC is a day early so will be able to try it tonigh.

Thanks
Jeff

---

### Post by AndyCooll on 2006-03-22
If you're going to do the same as your XP machine when you reach the partitioning stage then I would suggest you choose the manual partitioning option. Since you have 250gb, you have loads of space to play with. 

It really is your choice how you set up your partitions, but you might choose to create partitions along the following lines:

  /       10gb. This is root, which is where the operating system will install. You can get away with 2, 3 or 4gb. 10gb gives room to breathe and expand.
swap    2gb. Depending on how much RAM you have, roughly twice the size of that.
/home  10gb. That will be plenty! Again, you can choose significantly less if you wish. Remember that programs you use will also add any settings files to this directory. They are usually hidden (press CTRL+h to view). For example Firefox stores your bookmarks here, Evolution your e-mails etc etc. By putting this on a separate partition means that if you do a reinstall you won't lose all those settings for the other programs you took ages to to sort out.
/files.   The rest, or break it down to a few partitions if you prefer. Call it/them what you want. You'll want to manually give this partition(s) a name and mount point.

Creating separate "home" and "files" partitions is the bit which ensures your information is kept if you ever do a re-install.

If you let Ubuntu sort them out itself it won't create separate partitions that you can keep if  a re-install is required. It will create a swap partition and then everything else will be lumped in the root partition. 

:cool:

---

### Post by jethro10 on 2006-03-22
Thanks Mr Cooll.

this /files/ bit is the one I was sorta getting at.
I suppose I'll be installing and re-installing for a while till I get use to it.


Jeff

---

### Post by robinl on 2006-03-23
Well just for your information I have 1.5Gb of ram and a 1GB swap but ubuntu NEVER uses it. It keep on saying 0byte used. Now I'm thinking about deleting the swap since it's not using it anyways... ;)

---

### Post by cotcot on 2006-03-23
As you have loads of space and you want to learn you could only use half of your HDD and leave the other half to install the next Ubuntu version (prerelease or final as a version for testing before you do something on the other install ) and to backup. If you do not like the size it is always possible to resize (GParted liveCD).

---

### Post by mannheim on 2006-03-23
At the very least, create one partition that you do not intend to use right now. Make it 10 GB or whatever, and use it when you want to do a clean install of the next version of the operating system (dapper or beyond). This is something I didn't do first time around, and when I wanted a clean install I had to resize partitions and make space.

---

### Post by jethro10 on 2006-03-23
Keeing space back for another version is a good idea.

I gather installing 2 versions is like a windows dual boot and you get this grub thing to choose which one to run?

Ta

Jeff

---

