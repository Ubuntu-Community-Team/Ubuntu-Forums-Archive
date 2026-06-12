---
title: "Seperate home partition at installation"
date: 2010-11-01
forum: General Help
---

### Post by winchendonsprings on 2010-11-01
I'm having some small lagging problems with my upgrade to 10.10. I haven't done a clean install since 9.04 so I'm thinking of doing one... and I have a few questions.

Would making a separate partition at installation be worth it? 

If so how much run should I set for / ? 10gb? more? less?

Also should I create a swap partition? I never use hibernate. Actually whats a good reason anyone would use hibernate on a desktop? on a laptop I could see a few instances but anyway it's shutdown or suspend for me. 

my reference -  [http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by blueridgedog on 2010-11-01
How much system memory do you have?  How big of a hard drive do you have?

---

### Post by winchendonsprings on 2010-11-01
12gb memory. 1200gb hdd space

i like the option that i can re install my system in a year or so without heavy backups by keeping my /home folder in tact.

---

### Post by Slim Odds on 2010-11-01
1.2 TB and you only want to give / 10 GB? Man are you cheap.

I'd make it at least 20GB.

---

### Post by winchendonsprings on 2010-11-01
whats the benefit of giving the system so much room? will it use it all? I 'm not cheap I'm just saying that tutorial recommends 10gb. I dont go nuts installing stuff so I don't know if 10gb is too much/too little for /

---

### Post by Boondoklife on 2010-11-01
Ya know I just posted on a question like this the other day: [HERE]("http://ubuntuforums.org/showthread.php?t=1609133")

It has alot of info about why you should really only make a separate partition for your home dir if you need to limit the space users can use.

The ability to keep the settings in your home dir is not realistic if you are upgrading from one version to another or god forbid from say 8.04 to 10.04. The reasoning behind this is settings that are from an older version may not work in a newer one.

So in short why are you wanting to do it?

---

### Post by winchendonsprings on 2010-11-01
hmmm

so your saying a normal install is the best? (format the whole drive into a single partition)

The only thing that stinks about doing a full reinstall other than backing up music,photos,videos, doc,etc., is adjusting all the preferences for say - firefox profiles, email client info, and compiz settings just to name a few of the heavy ones. 

Any ideas for help on this that maybe I haven't thought of?

What do some people do for the settings of all there applications when they do a reinstall? it seems like some people do this rather than upgrade, yeah? seems like a hassle every six months.

---

### Post by Boondoklife on 2010-11-01
> **winchendonsprings said:**
> hmmm

so your saying a normal install is the best? (format the whole drive into a single partition)

The only thing that stinks about doing a full reinstall other than backing up music,photos,videos, doc,etc., is adjusting all the preferences for say - firefox profiles, email client info, and compiz settings just to name a few of the heavy ones. 

Any ideas for help on this that maybe I haven't thought of?

What do some people do for the settings of all there applications when they do a reinstall? it seems like some people do this rather than upgrade, yeah? seems like a hassle every six months.

Not really as there is no guarantee the newer apps will work with older configs, and if you run into this it can cause issues. Upgrades are normally safe, but you dont need a separate partition for your data to survive. The only real way this could serve the settings backup situation would be on a reinstall. But when someone is reinstalling they are generally trying to fix something. Now if somethings is wrong why would you want to keep those settings?

See no real reason, outside of a HD quota, to have home on a different partition. In short just select the default partition layout unless you have a REAL reason to do so.

---

### Post by winchendonsprings on 2010-11-01
where are my compiz settings? in .compiz under /home? or in .config/compiz? or somewhere else? that would be my biggest thing to reconfigure that has nothing wrong with it now.

---

### Post by oldfred on 2010-11-02
I converted from upgrades to new installs. I also have a laptop and install to it. So I recognized that I wanted to make it as easy as possible.
I did the install as much from the command line as I could and copied the history to a bash file, cleaned it up and now run it to reinstall every time. It creates mounts, edits fstab, installs apps (list from dpkg) and changes some settings.

I copy most of my /home over as I am upgrading each version and the software will update that just as an upgrade would. I also export a list of installed applications to reinstall all the additional programs I have installed. If I manually modify any system wide configurations in /etc I back those up, but do not copy to a new install as those settings may not be compatible.

Since I have room I keep 3 root partitions of 20-25GB and each install goes into the next one. That way I have old (so I can always boot or find old settings), current working, and beta to test next version. I keep all my data in separate /data partition, with some data still in a NTFS partition to share with my XP install that I only use occasionally any more.

Partitioning basics with some info on /data older but still relevant
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition]("http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition")

 dpkg --get-selections > ubuntu-files
from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

---

### Post by dcstar on 2010-11-02
> **winchendonsprings said:**
> 12gb memory. 1200gb hdd space

i like the option that i can re install my system in a year or so without heavy backups by keeping my /home folder in tact.

A separate /home means you can reinstall/upgrade without worrying about losing data there, you'd be a mug not to do it.

It will do no harm having some Swap, the disk space used is trivial.

---

### Post by winchendonsprings on 2010-11-02
>  It will do no harm having some Swap, the disk space used is trivial. 	

I know it will do no harm, but will it do any good? is it used for anything besides hibernate?

Also now I'm thinking that making a separate /home partition would be good if I only wanted music, pics, docs, etc and not file settings. I want some file settings but not all I guess.  I think It will feel good to start fresh. 

Also I don't know what size I would need to make a system partition. 10gb, 25gb? would there be lots of wasted space?

---

### Post by oldfred on 2010-11-02
One on the more knowledgeable users here (Herman) tested with & without swap. He did find having some swap was helpful even when you have lots of memory and swap is never used. He speculated that the kernel would check for swap and if not found spent some time resolving that. I did not save link to where he comment on it.

Herman on advantages/disadvantages of separate system partitions
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

I have several system partitions of 20-25GB. I have installed lots of programs and have used about 6GB. My /home is about 1GB. And all my data including most hidden data folders normally in /home, like firefox profiles & thunderbird profiles have been moved (and linked back in to home) to /shared (NTFS) or /data. But I understand if you want to create a DVD you may need 4GB in /tmp as a temporary file, so some extra room is not totally wasted. You can get by with less if cramped for space but why, if you have a large drive?

---

### Post by blueridgedog on 2010-11-02
> **winchendonsprings said:**
> 12gb memory. 1200gb hdd space

i like the option that i can re install my system in a year or so without heavy backups by keeping my /home folder in tact.

I have 8 gb of memory and use no swap on average, but have a 4 gb swap partition.  I recommend similar in your case.

As to /home, I have a partition that stores my files, but I do not mount it as home, but in stead mount it as /home/USER/Documents, then create symbolic links to Music, Pictures and etc. under /home/USER.  This allows me to have my file remain constant from install to install and to not need to deal with a separate /home.  I can generally do a clean install and relink to my files in a very short period of time.

In your case then, I would recommend you determine the amount of space needed for your files (say 1T) then create a 4gb swap partition, a 199gb / partition and a 1T files partition that you will mount inside your home directory.

Just my suggested method mind you...

---

### Post by philinux on 2010-11-02
> **winchendonsprings said:**
> I know it will do no harm, but will it do any good? is it used for anything besides hibernate?

Also now I'm thinking that making a separate /home partition would be good if I only wanted music, pics, docs, etc and not file settings. I want some file settings but not all I guess.  I think It will feel good to start fresh. 

Also I don't know what size I would need to make a system partition. 10gb, 25gb? would there be lots of wasted space?

I went for a 12 gig root and its still only 55% used.

I had 2 gig swap (got 2 gig ram) and the rest home.

For swap read this. With 12 gig ram it would not get used unless you hibenate or suspend etc.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by Slim Odds on 2010-11-02
I think that the concept of "wasting" 10GB on a 1,200 GB drive is just paranoid.

Just remember that if you only make 2 partitions (/ and /home) that **everything** that doesn't go in /home goes in / 

That means everything. So for example /tmp is really in /

So if you ever want to do something like copy a data DVD, you might just need that extra 10GB in / because that is where /tmp is and /tmp is where the copy will be placed temporarily before is it written to the new disk.

The extra 10GB is less than 1% of the drive.

---

### Post by winchendonsprings on 2010-11-03
the 1200gb is split between my two main drives. so it's not a single drive and as of right now there isn't more than 10% free space on either one. Also the only reason I have so much RAM is for running multiple virtual machines at once. When the vm's aren't running I don't need nearly that much memory.

So this is what I'm thinking I'll do after reading all the great replies with great ideas, some more complex than others. I think I'll not create a seperate partition for /home at all. I'm just going to back up my music,pics,video,docs,etc. now, and the next time I need to do a fresh install. Truthfully, I'm not the type of guy to do a reinstall every 6 months even if I make it easier for myself. Every 2 years is more like it. Regular upgrades have been fine so far.

What I will do is back up my firefox, thunderbird and compiz settings to replace on the new install. All the other applications I use will be rather easy to reset the settings. Also it will give me a good fresh felling. 

I will throw a 1gb swap partition on there at new install. what blueridgedog said made sense to me andd 1 gb is nothing. 

Between today and this weekend I will read this entire post again and may decide to change my mind and create a partition for /home.

---

### Post by Boondoklife on 2010-11-03
You could look into using LVM, this would let you combine the two drives into one. This way you would not have to have a separate partition for your home dir and use both.

---

### Post by winchendonsprings on 2010-11-04
This has gotten a little bit off topic. The fact that there are two  drives aren't playing a part in me deciding if I should create a /home  partition. Sorry about that.

one drive - fully formated ext4 except 1gb swap. This will contain / and /home
second drive - fully  formated ext4  storage


boondoklife you like the sound of that? no seperate partition for /home

---

### Post by Boondoklife on 2010-11-04
> **winchendonsprings said:**
> This has gotten a little bit off topic. The fact that there are two  drives aren't playing a part in me deciding if I should create a /home  partition. Sorry about that.

one drive - fully formated ext4 except 1gb swap. This will contain / and /home
second drive - fully  formated ext4  storage


boondoklife you like the sound of that? no seperate partition for /home

LOL, I'm just givin ya ideas on what you can do other than that; if you really have your heart set on it go for it! Linux is YOUR os, run it how you like that is why I use it. =]

The LVM suggestion was just an idea in case you did want one large volume, it will make sure that you can get access to the entire space and put what ever you want on it. kinda like a stripe raid only safer.

---

### Post by Slim Odds on 2010-11-04
Having a 1GB swap partition with 12GB of RAM make no sense at all.

Your virtual address space is the combination of your physical RAM and your swap partition disk space.

So you are increasing your virtual space from 12GB to 13GB, which is effectively nothing (about 8%). Do you think that if you exceed your 12GB usage, that you'll only do it by a few percent?

If you're going to have swap space, make it at least 4GB, but with 12GB you probably don't really need it at all. Have you ever actually hit the swap?

I have an 8GB machine that never swaps even when I run tons of apps and virtual machines.

The only reason I created a swap space was so that I could hibernate if I wanted to.

---

### Post by winchendonsprings on 2010-11-04
Well I have never checked to see if I've ever used the swap. If, while running virtual machines and things got laggy I think I would have checked, but I never did. So what you're saying is that since I never hibernate and have a lot of ram I'll never need it. 

Is there any case where ubuntu will look for swap, not find any of it and freak out at all? like what oldfred said a few comments back?

---

### Post by Boondoklife on 2010-11-04
> **winchendonsprings said:**
> Well I have never checked to see if I've ever used the swap. If, while running virtual machines and things got laggy I think I would have checked, but I never did. So what you're saying is that since I never hibernate and have a lot of ram I'll never need it. 

Is there any case where ubuntu will look for swap, not find any of it and freak out at all? like what oldfred said a few comments back?

I have never seen anything that said you DON'T need it, but you could always start with a 1GB swap partition and shrink it from there till you get to the point where you have no swap. Worst case scenario boot from the live cd and put back the swap.

---

### Post by winchendonsprings on 2010-11-04
Let's say I create no swap partition. How will I know if I ever need it? Say I have multiple virtual machines running as well as multiple high ram use applications. How will I know? Just by checking if the RAM is maxed out?

here's what I just read. linked to in a post a few comments back.

> 
**For a personal laptop or desktop computer**, in my opinion it's much better to install in one large partition for everything. Some people like a separate /home.
Be aware that you will still need to keep a separate backup of your  files even if you do have a separate /home partition. I prefer not to  have any separate partitions at all, not even for swap, I use a swap  file instead.
Advantages of installing in one big partition with directories for /bin /  boot  /dev  /etc  /home  /lib  /lost+found  /media / mnt  /opt  /proc  /root  /sbin  /selinux  /srv  /sys  /tmp  /usr  and /var,

[LIST]
[*]each directory is always as large as it needs to be - no need to resize with a partition editor if one directory grows too big
[*]no need for careful planning of partition sizes in advance before installing, everything will be okay
[*]editor when a directory grows or shrinks, it takes care of itself automatically
[*]only one file system to take care of, you only need to run e2fsck once a month or so
[*]less complicated, less to go wrong, easier to fix if something does happen
[*]besides, you will have a backup made, and you just need to make one backup
[*]The operating system boots faster and runs faster, at least according to results from tests I made recently
[*]faster, simpler installation process
[/LIST]
**For a computer you plan to share with other users, such as a**** server,** especially if you suspect that some of the other users may not be completely trustworthy.
Advantages of installing with separate partitions for each directory like /root /home /tmp /var and all the rest,

[LIST]
[*]if you can only get say 4GB hard disks or something like that  you still install an operating system in a computer and use three or  four small hard disks with one or two partitions on each one. That would  have been useful in the old days when most people could not buy very  big hard disks, but now we can buy 1 or 2 TB size hard disks
[*]useful for servers, especially in the old days when they used Unix  in big old mainframe computers with a lot of users in a University  campus or somewhere like that. May be useful even in these modern times  for servers where they are anticipating the possibility of malicious  users who might attack one directory and fill it up with large files to  try to bring the system down
[*]Different file systems can be used in different partitions and  mounted with different file system options, eg journaling or no  journaling, encrypted or no-encrypted, etc.
[*]supposed to be easier to recover from a catastrophe of some kind by  restoring one just one or two affected partitions, (presumably from a dd  backup I suppose). In order to make it recoverable you will probably  need to go to the work of making and keeping frequent backups of every  partition in case something happens to one of them to avoid the need to  re-install the entire system. That would have been important in the old  days when hard disks\ technology was not so far advanced and hard disks  were flaky compared with the hard disks we have now. Actually it only  takes half an hour or so to perform a complete re-install nowadays since  we have CD installers instead of tapes or punch cards. (We don't have  to type the operating system in by hand or anything like that).
[*]You can learn how to maintain a complex system in case you decide to  become a professional sys-admin some day in charge of complex equipment  - practice borking your own system and getting it fixed again in the  least possible time
[/LIST]


---

### Post by oldfred on 2010-11-04
I found Herman's discussion on swap. He actually uses a swap file. He tried setting swappiness to 0 but it slowed things down. He uses 10. He is also using SSD as his main drive.

[http://ubuntuforums.org/showthread.php?t=1501069](http://ubuntuforums.org/showthread.php?t=1501069)

---

### Post by Slim Odds on 2010-11-04
As mentioned before, the virtual memory space is the combination of real RAM and swap on disk.

Even if you have swap space, you can still run out of virtual space. With 12GB of RAM you'd have to try really hard to fill it up.

I have 8GB of RAM and I never use swap space except for hibernation (which I almost never use BTW), even when I intentionally load tons of program that I'm not really using.

Just go without swap for a while and watch your memory usage. But with 12GB you won't have anything to worry about.

---

