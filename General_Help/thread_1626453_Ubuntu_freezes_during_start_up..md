---
title: "Ubuntu freezes during start up."
date: 2010-11-20
forum: General Help
---

### Post by xieon on 2010-11-20
[QUOTE=So everyone knows the details. My computer was fine, then, poof, like this.]
My computer turns on
It then goes to the purple Ubuntu screen with the moving dots
It then flashes black with some text, super quick, impossible to read
Then there is just a black screen with a flashing _ sign, no matter how long I leave it there for.[/QUOTE]

I am using a dual boot Ubutnu 10.10 / Windows 7 lap top.


Everything was going fine, the lats program I was working with is skype (so perhaps thats the problem). I had to hard shut down my laptop because it froze, and now I've been unable to get back in.

I have to be on windows 7 do do anything, which sucks.

I start up the computer
Get the grub boot-loader
Select Ubuntu (normal, not recovery)
Then it does the purple ubuntu scrolling screen
After that it's just
_

^^^That's just flashing on a black screen, I'll try to post an alright picture incase it helps

---

### Post by xieon on 2010-11-20
Still not even a suggestion? I'm stuck w/o ubuntu or my files, and it's a really big pain.

What could be causing it and how to get rid of it

---

### Post by sikander3786 on 2010-11-20
Select Recovery from Grub menu and drop to root shell. Try these commands to fix broken pacakges (if any).

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

Please post the error reported there.

---

### Post by xieon on 2010-11-20
> **sikander3786 said:**
> Select Recovery from Grub menu and drop to root shell. Try these commands to fix broken pacakges (if any).

```
sudo apt-get install -f
``````
sudo dpkg --configure -a
```Please post the error reported there.


thanks for helping me out, i think it is a package since the last thing i did was install skype.


does the reovery usually take a while, because it seems mine is hanging on recovery too. It runs a ton of lines, then stops, I'll write down the line and re-post unless you think I should wait because its still doing its thing

---

### Post by Hippytaff on 2010-11-20
if you don't mind me jumping in here sikander recovery doesn't usually take that long, then you should get a menu to choose how you want to boot...if it loops (like m lubuntu install I'm trying to fix did earlier) you might want to boot from liveCD and get the output to sikanders suggested commands that way :-)

---

### Post by sikander3786 on 2010-11-20
> **Hippytaff said:**
> if you don't mind me jumping in here sikander recovery doesn't usually take that long, then you should get a menu to choose how you want to boot...if it loops (like m lubuntu install I'm trying to fix did earlier) you might want to boot from liveCD and get the output to sikanders suggested commands that way :-)
You are welcome :-)

<off-topic>So you've got a creamy mug of coffee now. Nice :-)</off-topic>

If you are talking about chroot, I am not that much experienced with that. And as you mentioned you had an experience fixing that earlier, you can carry on with **xieon**.

Good Luck!

**[COLOR="Red"]Edit:[/COLOR]** Recovery shouldn't take that much time to load as **Hippytaff** mentioned. If you are unable to boot the recovery mode either, the only possibility left is chrooting your install from a Live CD/USB and try to fix any broken packages or just do a clean install after backing up all your data.

---

### Post by Hippytaff on 2010-11-20
<off-topic>I didn't realise...I prefered my loads of uncreamy mugs, but one reason I hid my beans and am not too much of a fan of those icons is everyone assignes too much credance to what you say if you have lots of beans and a pretty coffee effort</off-topic>

Also I don't have much experience of Chroot, I used this [https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)
:-)

---

### Post by xieon on 2010-11-20
> **Hippytaff said:**
> if you don't mind me jumping in here sikander **recovery doesn't usually take that long**, then you should get a menu to choose how you want to boot...if it loops (like m lubuntu install I'm trying to fix did earlier) **you might want to boot from liveCD and get the output to sikanders suggested commands that way** :-)

I have a live CD, and I can boot into that, but I don't know what you want me to get the output from. Sikanders? Could you clarify what exactly I'm susposed to do once I boot into the computer through the live CD

> **sikander3786 said:**
> You are welcome :-)

<off-topic>So you've got a creamy mug of coffee now. Nice :-)</off-topic>

If you are talking about chroot, I am not that much experienced with that. And as you mentioned you had an experience fixing that earlier, you can carry on with **xieon**.

Good Luck!

**[COLOR=Red]Edit:[/COLOR]** Recovery shouldn't take that much time to load as **Hippytaff** mentioned. If you are unable to boot the recovery mode either, the only possibility left is chrooting your install from a Live CD/USB and try to fix any broken packages or just do a clean install after backing up all your data.

Sorry again, but I'm confused.

I can boot into ubuntu using the live cd, but how would I fix the packages. Wouldn't my PC think I'm running off the CD. I could mount the drives, but how would I go about removing the packages from the actual drive ubuntu is on?


Thanks for the help guys, once I get some more responses, I'm going to give it a go and see how it works. Windows 7 is working alright for me, but I can't access the files in my ubuntu folder, ugh, so I'd like to fix this.

Thanks!


Edit, I have uploaded a better picture of what it looks like. 
its just a since _ flashing on a black background, nothing else. Its the same flashing thing that's in a dos prompt _

Obviously in the image the dos stuff isn't there, but other than that it looks like that

---

### Post by sikander3786 on 2010-11-20
> I can boot into ubuntu using the live cd, but how would I fix the packages. Wouldn't my PC think I'm running off the CD.

You need to chroot your / partition following the link Hippytaff provided in above post.

[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)

---

### Post by xieon on 2010-11-20
> **sikander3786 said:**
> You need to chroot your / partition following the link Hippytaff provided in above post.

[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)

Ok, I'll try to follow that and see if I can do it/causing the problem.

I was wondering, could I boot from the live CD and do a repair install, that way I don't delete all my files, but it fixes any problems.

Otherwise I could always make a list of the things I downloaded and then copy my files to an HDD and reinstall thtat one, but first way sounds easier

---

### Post by Hippytaff on 2010-11-20
you can boot from livecd and back everything up, then reinstall :-)

save chroot-ing

---

### Post by sikander3786 on 2010-11-20
> I was wondering, could I boot from the live CD and do a repair install, that way I don't delete all my files, but it fixes any problems.

No. Unfortunately there is no option like that yet in Ubuntu.

> Otherwise I could always make a list of the things I downloaded and then copy my files to an HDD and reinstall thtat one, but first way sounds easier

You can mount your Ubuntu partition and you'll find all the downloaded packages under /var/cache/apt/archives. Copy them over to a safe location. You can also copy all your settings/config for different apps by pressing Ctrl + H in the home directory of your previous install and copy them over. (I have not done that but it should work).

Also copy all your personal files and re-install. Put the packages back in their place and config in there place and you'll be good to go.

You can wait for some other opinions on this.

---

### Post by xieon on 2010-11-20
> **sikander3786 said:**
> No. Unfortunately there is no option like that yet in Ubuntu.



You can mount your Ubuntu partition and you'll find all the downloaded packages under /var/cache/apt/archives. Copy them over to a safe location. You can also copy all your settings/config for different apps by pressing Ctrl + H in the home directory of your previous install and copy them over. (I have not done that but it should work).

Also copy all your personal files and re-install. Put the packages back in their place and config in there place and you'll be good to go.

You can wait for some other opinions on this.


That sounds good, I have a half TB external hard drive that's perfect for the job. So I back those up, re-install ubuntu, then I just paste them right back over and I'm golden, or would I still have to find all the packages in the software center and install them, then paste my backup data over it.

So far, your idea is looking like the best one.


Also, the recovery mode failed, it got hung up and stuck on this for a while.
```
[    4.26242878] Adding 1254396K swap on /dev/sda6. Priority:-1 extents1 across: 1254396K
```

---

### Post by linux18 on 2010-11-20
chrooting is *easy* when you know 2 things: where your partition is mounted and how to copy/paste.

1 start a live cd 

2 open your ubuntu partition in nautilus (so that it's mounted in /media) 

3 open a terminal

4:

```
 
UROOT=/media/YOUR_UBUNTU_PARTITION/

sudo mount --bind /dev $UROOT
sudo chroot $UROOT
mount -t proc none /proc
mount -t sysfs none /sys
mount -t devpts none /dev/pts 
```


5 aptitude -f install, dpkg-reconfigure -a, rm -r /home/*/.config

use that rm one as a last resort

---

### Post by xieon on 2010-11-20
> **linux18 said:**
> chrooting is *easy* when you know 2 things: where your partition is mounted and how to copy/paste.

1 start a live cd 

2 open your ubuntu partition in nautilus (so that it's mounted in /media) 

3 open a terminal

4:

```
 
UROOT=/media/YOUR_UBUNTU_PARTITION/

sudo mount --bind /dev $UROOT
sudo chroot $UROOT
mount -t proc none /proc
mount -t sysfs none /sys
mount -t devpts none /dev/pts 
```
5 aptitude -f install, dpkg-reconfigure -a, rm -r /home/*/.config

use that rm one as a last resort

Sorry, but I'm a bit confused.

You want me to open a terminal in the live CD, after I mounted my ubuntu partition.

Then type the code, but when I get to the last line what do I type
5 aptitude -f install

---

### Post by sikander3786 on 2010-11-21
> **xieon said:**
> Sorry, but I'm a bit confused.

You want me to open a terminal in the live CD, after I mounted my ubuntu partition.

Then type the code, but when I get to the last line what do I type
5 aptitude -f install
Aptitude is not installed by default on 10.10, use apt-get.

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

---

### Post by xieon on 2010-11-21
Sorry for being such a newie to linux guys, but thankfully linux and ubuntu has a great community. 

> **sikander3786 said:**
> No. Unfortunately there is no option like that yet in Ubuntu.



You can mount your Ubuntu partition and you'll find all the downloaded packages under /var/cache/apt/archives. Copy them over to a safe location. You can also copy all your settings/config for different apps by pressing Ctrl + H in the home directory of your previous install and copy them over. (I have not done that but it should work).

Also copy all your personal files and re-install. Put the packages back in their place and config in there place and you'll be good to go.

You can wait for some other opinions on this.

> **sikander3786 said:**
> Aptitude is not installed by default on 10.10, use apt-get.

```
sudo apt-get install -f
``````
sudo dpkg --configure -a
```


Basically I'm just lost with this chrooting stuff, and what not.

Could you just tell me all the directores I need to copy
I'll copy my own private stuff
Then I'll re-install 10.10
Then I will go into a live CD, and paste all the copied stuff back???


^^If the above idea will work, then fine, if not can someone please explain this chroot thing for me. I'm sorry that Im a little slow and I don't understand what to do.

I booted from a live CD, I've gotten that far.

---

### Post by xieon on 2010-11-21
[QUOTE=So everyone knows the details. My computer was fine, then, poof, like this.]
My computer turns on
It then goes to the purple Ubuntu screen with the moving dots
It then flashes black with some text, super quick, impossible to read
Then there is just a black screen with a flashing _ sign, no matter how long I leave it there for.[/QUOTE]


Unless someone can help me out because I'm really lost I'm just going to do a hard copy/paste re-install.

Is there a program that I can use that would make this easier? Such as

[http://www.debianadmin.com/backup-and-restore-your-ubuntu-system-using-sbackup.html](http://www.debianadmin.com/backup-and-restore-your-ubuntu-system-using-sbackup.html)

It sucks Im going to lose all my settings, but I can't seem to get this to work, and I need to use it.

**Edit:**
I said I did, but I have yet to try Linux18's workaround. I'm going to try it, but I only know what to do with the code he posted, there's more he posted outside the code box I'm not sure what to do with....
```
5 aptitude -f install, dpkg-reconfigure -a, rm -r /home/*/.config

use that rm one as a last resort
```I have tried this:
[http://ubuntuforums.org/showthread.php?p=9907252](http://ubuntuforums.org/showthread.php?p=9907252)
and it failed

---

