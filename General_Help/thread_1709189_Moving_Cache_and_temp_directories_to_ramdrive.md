---
title: "Moving Cache and temp directories to ramdrive"
date: 2011-03-17
forum: General Help
---

### Post by deviant085 on 2011-03-17
Hey all, I just got myself a OCZ vertex 2 SSD and have been moving cache directories to a ram drive to try to help extend the life of my SSD and improve system performance. I have created a ram drive for my /tmp directory in fstab like so


  ```
 tmpfs /tmp tmpfs nodev,nosuid,noexec,mode=1777 0 0
```


  And have since moved my Firefox temporary files to the /tmp directory and it have gotten me thinking, what else can I move here. I am going to upgrade my computer to have 8gb’s of ram which is way more than I’ll ever need. I would like to move the transmission cache dir there but I don’t know how to. Anyone have any tips on that? I was thinking of maybe a script that will run when I login to create a symbolic link? As I can’t find any setting to do it. 



  Can anyone think of any other directories I could move to there? 



  Cheers.


PS: also if anyone can think of a reason why this would be a bad idea please let me know :)

---

### Post by deviant085 on 2011-03-19
Bump, anyone??

---

### Post by theller on 2011-04-10
I just got a kingston 30g ssd and wanted to do the same thing you were doing. I am very new to terminal commands. Could anyone give me some details for the code used to move your tmp file? 

So far all I could do was move the music, video, docs... so two accounts share a single file on an external WD hard drive. So you are actually using the ram for tmp files. Would 4g be enough or should I use my spin drive.

---

### Post by deviant085 on 2011-04-11
What i was doing is creating a ramdrive and mounting it on /tmp I have 4gb of ram in my computer and it works fine. i always have plenty to spare. 

to create the ram drive is fairly easy. 

Open up gedit to modify /etc/fstab
```
sudo gedit /etc/fstab
```then add this line to the end of it. 
```
tmpfs /tmp tmpfs nodev,nosuid,noexec,mode=1777 0 0
```be careful, if you screw something up you may cause your system not to boot. to be on the safe side, maybe create a backup of your fstab 
```
sudo cp /etc/fstab /etc/fstab.backup
```and if you do screw up your system you can just boot from the live cd and restore the original file :)

google moving firefox & chrome cache directories to a ram disk. there are heaps of articles on it... it will help extend the life of your ssd and also speed up your browser :)

---

### Post by theller on 2011-04-17
Thanks, I think I did it? How do I know it's working? 

Does that code make all /tmp files go to the RAM, or just firefox?

I have an external 500g drive. Besides music, video, documents and photos what else can I move off the SSD? Should I move the entire /home? The SSD is only 30g so I am trying to keep it slim.

---

### Post by Locke_99GS on 2011-04-19
```
df
```
That'll let you know if it worked.

That change will place anything that would go to /tmp to RAM. A lot of things use /tmp - it's the *nix standard location for all things temporary.

---

### Post by PipeBoss on 2011-04-20
Noob questions - why use a RAM drive for /tmp stuff?  How does that extend the life of a SSD, and how does that compare to a standard HDD?  Can I do the RAM drive setup now with my current HDD and will I see any benefit to it?  I've only got 2GB RAM.  I currently have a 1TB HDD unpartitioned which I'm looking to partition into an OS partition and Media partition.  I'm not quite sure why I didn't partition it when I initially set up Ubuntu on it...  Down the road I was thinking about picking up a SSD for the OS.  U10.04 (if it matters)

---

### Post by solitaire on 2011-04-20
Basically using ram to store /tmp/ directory is (in my view) good housekeeping.
It's faster than SSD or HD access and it's wiped every time you shutdown/reboot.

Also i've pointed all my Cache & thumbnail files to /tmp/ to keep things tidy.

---

### Post by PipeBoss on 2011-04-20
Thanks, solitaire!

---

### Post by theller on 2011-04-21
Here is one of the many articles I have seen that say SSD's will last longer the less you write to them: [http://forums.nvidia.]("http://forums.nvidia.com/index.php?showtopic=138887")

Another reason I want to move tmp to ram is the write speed of the SSD is more than 3 times slower than read. Check out the Details tab (and the price) [newegg]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820139162") .

---

### Post by theller on 2011-04-21
So I ran df and got:

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             27616124   3996836  22216460  16% /
none                   2054820       392   2054428   1% /dev
none                   2059032       196   2058836   1% /dev/shm
tmpfs                  2059032        12   2059020   1% /tmp
none                   2059032        84   2058948   1% /var/run
none                   2059032         0   2059032   0% /var/lock
none                   2059032         0   2059032   0% /lib/init/rw
/dev/sdc1              3864064   1457408   2406656  38% /media/6338-3261
/dev/sdb1            471793992  37802124 410026124   9% /media/3ae8526e-34ef-4015-ab78-a59a9a32aa27

The last 2 lines are external drives. So does /tmp mean it's not working?

---

### Post by dino99 on 2011-04-21
Linux and of course Ubuntu use the ram to load as much it need before using at last swap partition. So gambling with oldish winblows garbage is useless

only my 2 cents

---

### Post by Locke_99GS on 2011-04-21
That means that you have a tmpfs file system mounted at /tmp. It is working.

---

### Post by theller on 2011-04-21
Thankyou!

---

