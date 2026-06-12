---
title: "very slow loading after login"
date: 2011-01-25
forum: General Help
---

### Post by Ve5ahchoo8ah on 2011-01-25
hi
I have a problem after I login to ubuntu it takes maybe 15-30 seconds until desktop is ready!
it wasn't like this before! I used to login and immediately using system but now I should wait and usually this result in broken loading of "MacSlow's Cairo-Clock"
I have disabled and re-enabled all of "startup application" but no difference!

---

### Post by blueturtl on 2011-01-25
To find out if the boot process has been corrupted for your user, create another user and log in using that user. If the new user logs in faster, there is something wrong in your user profile. If the new user has the same lag, then something must be amiss system wide. Please note that when you create a new user, the first log in takes a little longer than usually because all the user files are generated during the first log in. So really, try creating another user, logging in as that user, twice, and see how the second log in goes for the new user.

---

### Post by blueturtl on 2011-01-25
This has actually happened to me once. Try see if [this]("http://ubuntuforums.org/showthread.php?t=48094&highlight=login") fixes it.

---

### Post by Ve5ahchoo8ah on 2011-01-25
thanks for your reply

I created a new user and after few restarts I can say it's a little better but it takes about 15 seconds too!

I also renamed .gnome2 directory but no help at all

---

### Post by blueturtl on 2011-01-25
Any recent changes to software or hardware on that computer?

Is your hard disk nearly full? Fragmentation starts to become a problem after the disk capacity used is over 80%.

---

### Post by Ve5ahchoo8ah on 2011-01-25
no there's not any new hardware!
and my disk:
> $ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda8             81459088  14273952  63047196  19% /
none                   2056328       248   2056080   1% /dev
none                   2061924       580   2061344   1% /dev/shm
none                   2061924       112   2061812   1% /var/run
none                   2061924         0   2061924   0% /var/lock
/dev/sda1             77312780  48427256  28885524  63% /media/WinXP
/dev/sda5            102430408  89234912  13195496  88% /media/Win7
/dev/sda6             66573324  41923948  24649376  63% /media/Storage
/dev/sda7            155011152 113759080  41252072  74% /media/Games
/home/samic/.Private  81459088  14273952  63047196  19% /home/samic/Private


---

### Post by blueturtl on 2011-01-25
Have you used any third party repositories to replace system components with unsupported or unstable versions?

What are the last applications you installed before this started happening?

---

### Post by Ve5ahchoo8ah on 2011-01-25
I don't remember when it starts but as a matter of fact about a week ago I installed a series of updates and then my system was fast again! actually on fire!! but I don't know when maybe after installing other updates it came back!!

---

### Post by blueturtl on 2011-01-25
Your sources.list looks fine... I'm a bit dumbfounded right now. Will post again tomorrow.

---

### Post by Ve5ahchoo8ah on 2011-01-25
thanks anyway
especially for your time

---

### Post by blueturtl on 2011-01-31
I've been away. You still have this problem?

If you do, now would be a good time to post more detailed system spesifications...

---

### Post by |{urse on 2011-01-31
reboot and do a dmesg | more
then paste it up here in an attachment
maybe that will shed some light.

---

### Post by Ve5ahchoo8ah on 2011-01-31
hi
I did dmesg twice:

---

### Post by |{urse on 2011-01-31
> nvidia: module license 'NVIDIA' taints kernel.
[    8.672597] Disabling lock debugging due to kernel taint

^ this is a normal message for the official "closed source" NVIDIA driver. Your kernel is fine.
> 
HEST: Table is not found

^ this is a known bug.. I would love if someone could tell me what exactly it affects.

Everything looks normal bootwise.

Is the floppy drive disabled in your bios? That will help a bit.

Also you could disable apparmor, be sure to read up on this before you do it so you know what the security risks are. Personally, I disable it because it takes too long at boot and interferes with mysql.

```
sudo /etc/init.d/apparmor stop
sudo update-rc.d -f apparmor remove
aptitude remove apparmor apparmor-utils
```

I think you'll see a definite improvement in bootup speed after disabling apparmor, but again it comes at a cost security-wise.

---

### Post by Ve5ahchoo8ah on 2011-02-01
thanks [|{urse]("http://ubuntuforums.org/member.php?u=223883")
I did as you said but it didn't help

I took a video from my screen please watch it:
[COLOR=Blue]_[http://www.youtube.com/watch?v=Xutot3nbq5U](http://www.youtube.com/watch?v=Xutot3nbq5U)_[/COLOR]

I mean the delay after I enter my password until desktop is completely ready
also about floppy drive: [COLOR=Blue]_[http://i56.tinypic.com/2n9j59u.jpg](http://i56.tinypic.com/2n9j59u.jpg)_[/COLOR]
thank you

---

### Post by |{urse on 2011-02-03
Sorry about that, I was looking for boot issues. Forum blindness!

Just a shot in the dark but if you disable double-buffering in conky does it speed things up at all? Post your .conkyrc. also try disabling conky and reboot just to help narrow things down. 

also is your loopback interface set up correctly? I've seen that slow things quite a bit initially after logon.

gksudo gedit /etc/network/interfaces

make sure 
auto lo
iface lo inet loopback
are in there.

I'll post back if I can think of anything else.. I'm not going to mention desktop effects yet because your system looks beefy enough. We can consider alternate drivers if that ends up being the problem later.

---

### Post by Ve5ahchoo8ah on 2011-02-04
first of all I should really thank you "|{urse" because of your time and consider that you put in my problem
I send my .conkyrc and interfaces in a file
I previously disabled everything (including conky) in my "startup application" but it didn't help
I was thinking the other day that maybe I should wait until 11.04 and then install a fresh ubuntu that time! I'm just not pretty sure that I have backed up every setting that I have made now! ;)

anyway
thanks a lot

---

