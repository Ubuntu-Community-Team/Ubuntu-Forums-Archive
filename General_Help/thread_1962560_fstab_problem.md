---
title: "fstab problem"
date: 2012-04-21
forum: General Help
---

### Post by alena2 on 2012-04-21
Hello, I am sorry I am posting on ubuntu forum when I am a Linux Mint user but when I was searching for help, this forum (especially [_this thread_](http://ubuntuforums.org/showthread.php?t=1384916)) seems to me like the right way to go.

I already posted on [_here_]("http://forums.linuxmint.com/viewtopic.php?f=46&t=100172&start=0") on Linux Mint forum and described my problem there but I am still in the same problems which I was in yesterday. There are pieces of advice by others and they might describe problem better and give you more useful information than copy and paste my text I posted there.

I have been using Mint for four months, in booting/mounting/etc I am a total noob.

Thanks for any help, I am desperate :(

---

### Post by Paqman on 2012-04-21
That fstab shows your root partition as read-only. Change that line from:
```
UUID=3cbb67e7-2aee-4a20-9544-2de13b9447ac  /            ext4  ro                       0  1 
```
to:
```
UUID=3cbb67e7-2aee-4a20-9544-2de13b9447ac  /            ext4  errors=remount          0  1 
```

---

### Post by alena2 on 2012-04-21
But how? I cant edit anything in nano, not in recovery mode, even not as an admin user, it keeps saying "read only file system" (or something very similar, I use my language version).

---

### Post by Paqman on 2012-04-21
Boot up into your LiveCD or USB, mount that partition and edit the file that way.

---

### Post by alena2 on 2012-04-21
I tried according to _[this]("http://ubuntuforums.org/showpost.php?p=8688514&postcount=8")_, and:

```
root@ubuntu:~# mkdir rootmount
root@ubuntu:~# mount -t ext4 /dev/sda9 ~/rootmount
root@ubuntu:~# sudo cp ~/rootmount/etc/fstab ~/rootmount/etc/fstab.broken
*so far no problem*

root@ubuntu:~# sudo cp ~ /rootmount/etc/fstab.bak ~/rootmount/etc/fstab
after this its saying this: 
**cp: target `/home/ubuntu/rootmount/etc/fstab' is not a directory**
```

---

### Post by Paqman on 2012-04-21
You don't want to restore your backup, because your backup has the same error. Now that you've got the partition mounted, just open up the file (which will be at ~/rootmount/etc/fstab from the look of it) and make the edit to the file I detailed above.

---

### Post by alena2 on 2012-04-21
Thanks. Its for the first time it doesnt say its "read only". But after I finish (ctrl + X) and confirm changes (Y) it asks me "File Name to Write", when I type fstab (and enter) and then check the file again, there are no changes. It remains the same :confused: 
I am sorry I am wasting your time with this and appreciate your help and time you are giving me.

And another question: shouldnt be edited also this line
```
/dev/sda6                                  /media/sda6  ntfs  nls=iso8859-1,ro,noauto,umask=000  0  0  
```?
I mean that **ro, noauto**.

---

### Post by dino99 on 2012-04-21
> **alena2 said:**
> Thanks. Its for the first time it doesnt say its "read only". But after I finish (ctrl + X) and confirm changes (Y) it asks me "File Name to Write", when I type fstab (and enter) and then check the file again, there are no changes. It remains the same :confused: 
I am sorry I am wasting your time with this and appreciate your help and time you are giving me.

And another question: shouldnt be edited also this line
```
/dev/sda6                                  /media/sda6  ntfs  nls=iso8859-1,ro,noauto,umask=000  0  0  
```?
I mean that **ro, noauto**.

you need to use sudo to edit fstab (sudo nano /etc/fstab)

---

### Post by Paqman on 2012-04-21
That file will be owned by root, did you open it using sudo?

As for the other entry, that's up to you. It's not a system partition, as you can tell from the way it's mounted at /media/sda6. It's and NTFS (ie: Windows) partition, so unless you want to be able to write to it, there's no harm in it being read only.

---

### Post by alena2 on 2012-04-21
You guys are great :)

Yes, I did (but for the first time not, I am a noob, really). But I was choosing the file manually (ctrl + r, ctrl + t), and thats probably the changes didnt remain, when I use 
sudo nano ~/rootmount/etc/fstab
the changes are there now! 

@dino99
just sudo nano /etc/fstab brougt me to this fstab:
```
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda10 swap swap defaults 0 0
/dev/sda8 swap swap defaults 0 0
```I can ignore this fstab, can I?


So I changed "ro" to "errors=remount" in the fstab file in rootmount/etc, can I reboot now? Or there must some unmounting done before it?


Seems I am getting somewhere with you, thanks a lot, THANKS!!! :-)

---

### Post by Paqman on 2012-04-21
> **alena2 said:**
> I can ignore this fstab, can I?


Yes, that's the one for the LiveCD. You wouldn't be able to chage it anyway.

> 
So I changed "ro" to "errors=remount" in the fstab file in rootmount/etc, can I reboot now? Or there must some unmounting done before it?


Go ahead and reboot. Out of interest: how did your fstab end up like this in the first place? If it's because of Storage Device Manager then I'd stop using it right away. Sounds like it's done more harm than good. It's a pretty old tool, I'm not sure it's being maintained any more.

---

### Post by alena2 on 2012-04-21
> **Paqman said:**
> Yes, that's the one for the LiveCD. You wouldn't be able to chage it anyway.



Go ahead and reboot. Out of interest: how did your fstab end up like this in the first place? If it's because of Storage Device Manager then I'd stop using it right away. Sounds like it's done more harm than good.

Yes, I changed there something by mistake. I dont want to use more partitions in the future anyway. Now I am in process of trying Mint, applications etc, then I will make a reinstall and with only one Linux partition - I've got more than one now because I wanted to try to make more on my own and find if I was able to do it with no help :D ).

I am gonna reboot now and post again (I hope :)) from my regular system.

---

### Post by alena2 on 2012-04-21
Again from ubuntu.

After choosing Mint in grub menu after 10-15 secs of booting it says following (or something very similar, dont remember exactly every word, I wrote down just something):
An error occured while mounting /.
Press S to skip mounting, M for manual recovery.

S leads to nowhere, just black screen.

After pressing M its saying this:
Root filesystem check failed. A maintenance shell will now started, Control plus D will terminate this shell and reboot the system. 
Give root password for maintenance.

After giving password I am in the command line.


**Edit: **I googled little and after that I added "-ro" (errors=remount-ro) - to edit fstab is question of two mins now so its not a big task to change it back /I spent hours on this! :D/ and now I am after so many hours in Mint again :-)

1. can you explain to me why this small change makes the system boot with no problem?
I guess it means something like "if there is an error remove read-only". What was there by default before changes had been made by me in Manager? 
2. clock is now +4.00 hrs than time actually is, do not understan why. System time is ok though.
3. I cant mount one of the partition:
> Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sda6 on /media/sda6I am gonna make some changes in manager but ONLY on this partition to make it mountable, if I wont figure it out by myself I will ask again, I dont wanna screw something again :)

[B]4. Thanks guys for helping, especially Paqman, you cant imagine how happy I am now :-)

[/B]I am marking the thread as Solved.

---

