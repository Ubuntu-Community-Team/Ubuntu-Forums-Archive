---
title: "Making Ubuntu Fast using RAM (updated and simplified)"
date: 2010-10-12
forum: General Help
---

### Post by terminator14 on 2010-10-12
**[SIZE="4"]About the Project[/SIZE]**

Back in the summer of 2010, I wrote a HOWTO that can be found [here]("http://ubuntuforums.org/showthread.php?t=1499338"). Later that year, I wrote a script that did the same thing, but was a lot easier to use. With over 55,000 views, and 33 pages of replies (at time of writing), it's apparent that people have been using it. While I've tried to maintain the script by doing quick tests on new versions of Ubuntu, the code has become old, and hard to manage, so I figured a rewrite was in order. Recently, I had some time, so I spent the past month working about 5 hours a day to rewrite this thing, basically from scratch.

Now, the script has cleaner code, should be easier to maintain, and gives the user as many options as possible, while having good default settings that should work for anyone.

**[SIZE="4"]What does it do?[/SIZE]**

So you've probably read this far, but have never heard of my previous HOWTO so you're clueless as to what the script actually does. The basic concept is simple. Many people today have plenty of RAM. Enough so in fact, to load an entire Operating System into it, and run the OS entirely from RAM. Why would you want to do this? Because RAM is fast. Really really fast. To quote myself from my old HOWTO,

> **terminator14 said:**
> Looking at the DDR2 page of wiki, it is clear the advantage RAM has over regular hard drives. Something as cheap as DDR2-533, something you could easily obtain an extra 1 GB of for about $30, has roughly a speed of 4266 MB/s. Compared to a regular 100MB/s hard drive, that's 42 times faster. If you have a slightly more expensive system that supports faster RAM (I have 6GB of DDR2-1066 RAM), the speed of the RAM can be up to 8533 MB/s. Imagine every file your operating system requests to read or write being served up at that speed!

"But doesn't RAM forget everything as soon as you reboot or shut down your computer?" you may ask. This is indeed the case, and normally that would be a deterrent as no one wants an Operating System that they can't save anything to. In Linux however, the separation of the OS from your home folder (where 90% of your data is stored) and the ability to mount partitions in place of folders at boot (with the help of fstab) solves this problem. 

Simply put, your desktop, music, photos, videos and downloads are all stored in your /home folder. Even applications such as firefox, transmission, evolution, and many others (most applications actually) store their settings in your /home folder. What the script does is make sure that the /home folder is NOT located on your RAM, but on a partition located on your hard drive, allowing you to save all the files, folders, application settings, and multimedia you want while still getting the benefits of your OS running directly out of RAM. It does this in the background of course, so you never see the difference, and unless you go looking for it, you'd never be able to tell that your /home is not located where the rest of your system is. 

**[SIZE="4"]Who it's for[/SIZE]**

If you've been upgrading your computer by buying faster and faster processors and never seem to get the speed you're hoping for, it may be because the processor isn't what's holding your computer back. Anyone who has ever owned or has experienced the speed of a computer running from an SSD can tell you that running your OS from a faster medium makes a huge difference in speed, and in most cases even a bigger difference than buying a faster processor. Unfortunately, SSDs are still rather expensive. Luckily, linux is capable of using RAM as the medium from which the OS runs, and since you already have RAM, and in many cases you already have enough RAM, you can run your computer faster than an SSD for free.

Technically, this method isn't really directly supported by the Ubuntu development team, so if you run into problems, you may have to do some digging online or post a comment and wait for a reply to find out how to solve it. This is something you have to be ready for. I suggest not trying this first in a production environment (if you have a work computer that NEEDS to work 100% of the time, it may not be the best idea to test this on it or you may end up with a problem that prevents you from meeting a deadline). Having said that however, I've been running my OS out of my RAM for months now, and once I got the hang of it, it's as stable as can be.

**[SIZE="4"]What it will run on[/SIZE]**

The old script was designed and tested on Ubuntu 10.04, and later updated for newer versions.

The new script was designed and tested on Ubuntu 14.10, and will be undated for newer versions of Ubuntu when they are released.

The git repo will tell you what versions of Ubuntu the script is available for - just look at the file names. 

**[SIZE="4"]Manual[/SIZE]**

Most of the main script is self explanatory as it asks the user questions and says what it will and will not do. The only undocumented feature of the main script is the following command:

```
sudo ./RAM_booster.sh --uninstall
```

which, if run at any point, will undo everything the script has done. If the script is interrupted for any reason, it will actually ask you if you want to run the same uninstall method in order to revert the changes it made. This is why, if you run into problems or want to get rid of the RAM Session (which is what I refer to the OS that is created), the line above is your best friend. Although this is the best way to force an uninstall, if your install went fine and you want to uninstall, you can simply run the script again. It will detect that it has run before and offer to uninstall itself for you.

A few lines up, I referred to RAM_booster.sh as the "main" script because it actually creates 3 other scripts and places them into the RAM Session environment. The additional scripts are:

[SIZE="3"]rupdate[/SIZE]: Since the RAM Session is copied upon boot from a read only squashfs image, any software you download or updates you perform inside the RAM Session are undone as soon as you reboot. The only way to perform an update is to chroot into the folder to which the OS was copied to create the RAM Session (/var/squashfs), and update from inside that. After this, the squashfs image has to be recreated using /var/squashfs. As this can be a lengthy process, rupdate takes care of all that. All you need to do is run it, wait until it finishes, and reboot to take advantage of the newly installed updates. 

[SIZE="3"]redit[/SIZE]: rupdate takes care of any updates you may need to do to the RAM Session from the repos, but what if you need to change some settings in /etc/ or download and install a .deb file, or even compile a program from source? redit allows you to chroot into /var/squashfs and edit the RAM Session directly. Any changes you make with redit will be permanent, assuming you let it recreate the squashfs image. Note: people who have used RAM Booster before will know this as the rchroot script.

[SIZE="3"]rupgrade[/SIZE]: while rupdate takes care of updates to the system, rupgrade takes care of any updates that I make to RAM Booster, or any accompanying scripts. You can run this script yourselves, but cron already does this for you once per day. If there are updates available, you'll get a popup letting you know to run rupgrade

**[SIZE="4"]Video[/SIZE]**

Yes, there's finally a video showing how to use RAM Booster!

[https://www.youtube.com/watch?v=pmqxDfdtDKg&feature=youtu.be]("https://www.youtube.com/watch?v=pmqxDfdtDKg&feature=youtu.be")

**[SIZE="4"]Updates in the new version[/SIZE]**

The new version now has:

[INDENT]Cleaner code
Support for many different Ubuntu partition configurations (except btrfs)
Support for upstart (by enabling proper upstart chroots)
Much better handling of chroot unmounting
[INDENT]It detects and stops any programs running in the chroot, and any filesystems mounted in the chroot before unmounting it[/INDENT]
Support for an encrypted filesystem
Support for encrypted home directories
Support for efi
Support for lvm
[/INDENT]

**[SIZE="4"]Development[/SIZE]**

[SIZE="3"]Original Script[/SIZE]:

Although the idea of creating a script to do this seemed pretty simple before I started (I already had the commands the script should run - see Original HOWTO), it ended up being quite complex. The hardest part was probably getting grub2 to work the way I wanted. The script needed to find /home, /boot, identify them for grub using a UUID, and write a grub.d script. This took a bit of work.

For testing, I used Ubuntu 10.04 x64 Desktop (and later Ubuntu 10.10 x64 Desktop), and ran them in VMware. All I can say is thank god for VMWare and snapshots. I literally tested the script a hundred times during development, something I would have never been able to do without VMWare. At one point I had about 20 different snapshots at different points of testing with different hard drive configurations (different locations for partitions that were to hold /boot and /home) and my VM was about 120GB (no joke).

I also used apt-cacher-ng running in another debian VM to make sure that while working on the rupdate script, I wasn't downloading the same updates over and over and over again from the internet. Not only would that have taken a painfully long time, but would have gotten me in trouble with my ISP (I have a monthly limit for downloads that I already exceed with torrents), and would have put unnecessary strain on official update servers.

This took about a week to write, and I'm very curious how I did. If anyone looking at my bash code can improve the code's efficiency or make it work better, or even has a general comment about how bad I am at bash and why, let me know.

[SIZE="3"]Updated Script[/SIZE]:

Again, since I already had most of the code, and most of it was working, I figured I would be done in a week or two. One month of coding later, I was finally done. Why is coding never as quick as it seems it should be? Or is that just me?

It was mostly more of the same - lots of vmware testing and commiting to git.

**[SIZE="4"]Bugs[/SIZE]**

If you run into any bugs, big or small, post a reply to this thread and I'll do my best to fix them. Even if it's been months since the last reply, I don't check this thread every day, but do get an email as soon as someone posts, so I'll respond as soon as I can.

If your bug is serious and warrants reproducing, I may ask you to post the /var/log/ram_booster.log logfile from your Original OS so that I can duplicate your install.
The file shouldn't have any private info in it - just your partition table, lvm layout (if you're using that), /etc/fstab, the output of some commands that ran during install, and things like that. Look through the file before you post it to make sure you're ok sharing what's in it.

**[SIZE="4"]Final Words[/SIZE]**

Although I tested the script hundreds of times in VMware when I originally wrote it, and hundreds of times when I rewrote it, the updates for the new versions of Ubuntu get significantly less testing (mostly because most of the time, hardly anything changes). On the off chance that this introduces a bug that gets past me, let me know and I'll do my best to fix it.

**[SIZE="4"]Updates/Changes[/SIZE]**

For a breakdown of the changes made to the scripts over time, see the git log.

**[size="4"]Download[/size]**

In order to get the latest version of the script, first install git:

```
sudo apt-get install git
```

Once that's done, run:

```
git clone git://github.com/terminator14/RAM_booster.git
```

This will create a RAM_booster folder in your current working directory with the script in it. Keep in mind that there are different versions of the script in the folder that is created - each file is labelled for the version of Ubuntu it will work for. You only need to run the one that corresponds to your version of Ubuntu.

**[size="4"]Leadership[/size]**

I started this project in 2010, when I was still using Ubuntu, and was still going to school, having no job to pay for an SSD. Since then, I've moved on to other distributions, and have bought multiple SSD drives. This has resulted in a steady decrease in my dedication to this project.

I no longer have the will, and often lack the time to keep this project as up-to-date as it should be. While I've been trying to keep this project going by updating it to work on new releases of Ubuntu, and even rewrote it, there is so much more that could be done with it. For example:

[LIST]
[*]Support for other distros (at the very least - Linux Mint)
[*]More rigorous bug testing
[*]Use of LXC instead of chroot
[*]Added features
[/LIST]
If anyone who knows how to write bash scripts (or any other language if you plan on a rewrite), is familiar with git, and is comfortable with virtualization (comes in very handy for testing) is interested in taking over the project, please contact me.

Until I find someone who wants to take the project over, I will continue to answer questions, try to do bug fixes, and try to keep updating it to work with new releases of Ubuntu.

---

### Post by Sylslay on 2010-11-10
Well, thx for script.

It works form me on Ubuntu 10.10.

Got only 1GB ram.

Ubuntu 10.10 was installed on USB key. 
Fresh install without update, then connected to internet and su root, 
run the script and :

script was perfect, working: (after I unmounted other partiton than sdb!!!, if not it laod file from fat32 and ubuntu 10.04 to squash )

sqash made by it is around 670MB

ubuntu was installed from liveCD on 8gb USB steak.

partiton  sdb1: fat32 512 MB
partiton  sdb2: ext4  6000MB mount at /
partiton  sdb3: ext4  1024MB mount at /realusb 
partiton  sdb4: swap  512MB

/dev/sdb3 was used to copy home folder by that script.

thx its working , but IMHO I need at list 2GB RAM for bettr results, becosue swap is slower down that beast :-)
give it try at december, when get 2x1GB ram from my parents PC.

thx 
PS: My first gnome loaded to ram :-) and it's faster then load normal way from USB

---

### Post by terminator14 on 2010-11-11
> **Sylslay said:**
> Well, thx for script.

It works form me on Ubuntu 10.10.

Got only 1GB ram.

Ubuntu 10.10 was installed on USB key. 
Fresh install without update, then connected to internet and su root, 
run the script and :

script was perfect, working: (after I unmounted other partiton than sdb!!!, if not it laod file from fat32 and ubuntu 10.04 to squash )

sqash made by it is around 670MB

ubuntu was installed from liveCD on 8gb USB steak.

partiton  sdb1: fat32 512 MB
partiton  sdb2: ext4  6000MB mount at /
partiton  sdb3: ext4  1024MB mount at /realusb 
partiton  sdb4: swap  512MB

/dev/sdb3 was used to copy home folder by that script.

thx its working , but IMHO I need at list 2GB RAM for bettr results, becosue swap is slower down that beast :-)
give it try at december, when get 2x1GB ram from my parents PC.

thx 
PS: My first gnome loaded to ram :-) and it's faster then load normal way from USB

Awesome! Good to know it works. Thanks.

---

### Post by hexion111 on 2010-11-14
Just was I was looking for. I will give it a try in a few days.

Thanks for posting this.

---

### Post by terminator14 on 2010-11-24
> **hexion111 said:**
> Just was I was looking for. I will give it a try in a few days.

Thanks for posting this.

You get a chance to try it? How did it go?

---

### Post by yesrno on 2010-12-07
Hmmm so I tried your script out, but at some point it was asking me to choose between 3 options - where to store the home folder. So I entered a 2, which would be for choosing a disk manually, but when I entered 2 the scripts started doing all kinds of things and at one point I saw it copying my home folder to somewhere (?) and then I saw it was trying to copy all my VM disks and I canceled the script :oops:. I ran the un-installer and it says it's un-installed but when I run the script again, it says the only option is to un-uninstall :o!

---

### Post by asmoore82 on 2010-12-07
Linux does this already.

The output of the `free` command tells you how much RAM is currently used by filesystem caching in the "cached" column.

Overbearing caching schemes are a trade-off: trading faster *first run* of any given App for increased, or *slower*, boot times. Subsequent runs of said App will be exactly the same in either case.

See the cache at work on stock Ubuntu 10.04:
```
**ubuntu$** dd if=ubuntu-10.04.1-desktop-i386.iso of=/dev/null
1404032+0 records in
1404032+0 records out
718864384 bytes (719 MB) copied, [COLOR="Purple"]10.9608 s, 65.6 MB/s[/COLOR]
**ubuntu$** dd if=ubuntu-10.04.1-desktop-i386.iso of=/dev/null
1404032+0 records in
1404032+0 records out
718864384 bytes (719 MB) copied, [COLOR="Purple"]0.879604 s, 817 MB/s[/COLOR]
**ubuntu$** dd if=ubuntu-10.04.1-desktop-i386.iso of=/dev/null
1404032+0 records in
1404032+0 records out
718864384 bytes (719 MB) copied, [COLOR="Purple"]0.881407 s, 816 MB/s[/COLOR]
**ubuntu$** dd if=ubuntu-10.04.1-desktop-i386.iso of=/dev/null
1404032+0 records in
1404032+0 records out
718864384 bytes (719 MB) copied, [COLOR="Purple"]0.861888 s, 834 MB/s[/COLOR]
**ubuntu$**
```^repeated access to the same data is nearly instant

The vanilla Linux setup gives you the best of both worlds:
Extremely efficient on-demand caching *plus* at the kernel's discretion
it can still free this memory for use by your apps as needed.

---

### Post by terminator14 on 2010-12-07
> **asmoore82 said:**
> Linux does this already.

The output of the `free` command tells you how much RAM is currently used by filesystem caching in the "cached" column.

Overbearing caching schemes are a trade-off: trading faster *first run* of any given App for increased, or *slower*, boot times. Subsequent runs of said App will be exactly the same in either case.

See the cache at work on stock Ubuntu 10.04:
```
**ubuntu$** dd if=ubuntu-10.04.1-desktop-i386.iso of=/dev/null
1404032+0 records in
1404032+0 records out
718864384 bytes (719 MB) copied, [COLOR="Purple"]10.9608 s, 65.6 MB/s[/COLOR]
**ubuntu$** dd if=ubuntu-10.04.1-desktop-i386.iso of=/dev/null
1404032+0 records in
1404032+0 records out
718864384 bytes (719 MB) copied, [COLOR="Purple"]0.879604 s, 817 MB/s[/COLOR]
**ubuntu$** dd if=ubuntu-10.04.1-desktop-i386.iso of=/dev/null
1404032+0 records in
1404032+0 records out
718864384 bytes (719 MB) copied, [COLOR="Purple"]0.881407 s, 816 MB/s[/COLOR]
**ubuntu$** dd if=ubuntu-10.04.1-desktop-i386.iso of=/dev/null
1404032+0 records in
1404032+0 records out
718864384 bytes (719 MB) copied, [COLOR="Purple"]0.861888 s, 834 MB/s[/COLOR]
**ubuntu$**
```^repeated access to the same data is nearly instant

The vanilla Linux setup gives you the best of both worlds:
Extremely efficient on-demand caching *plus* at the kernel's discretion it can still free this memory for use by your apps as needed.

I'm sure you're absolutely right and this is indeed correct (nice example too btw - I didn't know the OS would store an entire file like that). What the script does (like you said) is speed up the first time use of programs. So basically, if you just boot your Ubuntu, and open firefox (for example), regular Ubuntu will need to copy data from the HDD to RAM before it runs firefox which will take a few seconds (in my experience, anywhere from nearly instant up to 10 seconds - especially if it's a 5400 RPM drive like some laptops have). If the same scenario happens within the RAM Session after running the script, the data needed for firefox to load is already in RAM. That is the main difference. All subsequent launches of firefox in both cases will be from RAM and should be instant (in theory anyway). Perhaps I should have been more clear in my description of what the script does to speed up the OS when compared to a regular install. 

Despite the fact that a regular OS will eventually be as fast as RAM if you use it long enough without a reboot, the fact remains that inside the RAM Session, the system just feels more responsive as applications load instantly every single time. Perhaps this is a temporary benefit as a regular Ubuntu installation would eventually store all the apps you have used in RAM anyway, but to me this felt like a huge difference and was worth it at the time. 

You're also right about this system being a trade-off: faster first time run of apps vs slower boot time (as the system needs to copy everything to RAM at boot). I would just add that along with slower boot time, you also get some complexity added. By that I mean - you need to understand how this system works (at least a little) in order to know how to update your RAM Session properly. You also need to understand how to add files to the RAM Session that can survive a reboot, or edit config files in /etc. I think users need to realize this trade-off and make their own decision as to whether or not this trade-off is worth it to them. The best way to make the decision however if a reader of this thread is on the fence is to try the script and see for themselves if the benefits outweigh the trouble.

I used to think they did until I installed my OS onto my SSD. Now my OS is plenty fast, which means I don't use the script anymore as its benefits no longer outweigh its trouble for me. I will however try to fix any bugs that people report the script has.

---

### Post by Slim Odds on 2010-12-07
You could accomplish the same result by simply creating a list of applications that you want to be "first time fast" and just read them from disk in rc.local during startup.

That would put them in the file cache where they would be loaded "instantly" at the expense of reading them from the hard drive at boot.

---

### Post by terminator14 on 2010-12-07
> **Slim Odds said:**
> You could accomplish the same result by simply creating a list of applications that you want to be "first time fast" and just read them from disk in rc.local during startup.

That would put them in the file cache where they would be loaded "instantly" at the expense of reading them from the hard drive at boot.

Good point. I think this is the basic idea behind preload, but I never could get preload to function properly. I wonder if something as simple as that (reading files in rc.local at boot) would end up with the exact same results in terms of speed of opening apps and speed of the OS itself as this script provides. If so, that would make the issue this script addresses be solved by something 100x simpler, which is always a good thing.

The only potential problem I see with simply reading a file in rc.local (not running it but simply reading it) is that any libraries the file needs when it runs will not be read into RAM. This won't cause any problems - it simply means when the app is launched by the user, the main file will already be in RAM but the libraries it needs will still need to be copied from the HDD to RAM before they can be used. I'm not a programmer, and having limited knowledge of exactly how libraries are linked to apps, I may be wrong about this, but I'm pretty sure this is the case.

---

### Post by terminator14 on 2010-12-07
> **yesrno said:**
> Hmmm so I tried your script out, but at some point it was asking me to choose between 3 options - where to store the home folder. So I entered a 2, which would be for choosing a disk manually, but when I entered 2 the scripts started doing all kinds of things and at one point I saw it copying my home folder to somewhere (?) and then I saw it was trying to copy all my VM disks and I canceled the script :oops:. I ran the un-installer and it says it's un-installed but when I run the script again, it says the only option is to un-uninstall :o!

Thanks for your feedback. I'll take a look. A few things could help me out though, if you don't mind:

1. What OS did you run this script on? 10.04? 10.10?
2. What is the layout of your filesystems on the OS you ran it on? Is your /home on the same partition as your '/'?
3. How far did the script get in asking you questions before it started to copy your /home after you chose to enter the device manually? Normally, after you choose 2, it will ask which device you want to use for /home. It will then verify that the device is valid, make sure it's empty (or ask you to empty it if it finds files on it), it will format it, and it will copy your current /home to that device. So copying the files you have in your old /home to the new device is done by design in order for you to have access to your old /home in the RAM Session. There would be a problem with the script if it somehow jumped the gun and as soon as you hit option 2, it started to copy your /home to a device you haven't chosen yet. Are you saying this is what happened? If so, where did the files get copied to?


As for the uninstall not working, that is incredibly strange. The way the script determines if it ran before is a file called /Original_OS. When the script runs normally, it makes sure the file doesn't exist before it continues. If it doesn't, the script keeps running and this file is created. When the script is launched again, it checks for the file again, but this time when it finds it, it tells you that the script ran before, and asks if you want to uninstall. The uninstall function removes the /Original_OS file (along with anything else the script may have done). The uninstall function is one of the simplest functions within the entire script, and looking at it now, I don't see where I could have messed it up. Does the /Original_OS file exist on your original OS? If it does, run "RAM_booster.sh --uninstall" and check again. Is it not being removed? The line within the uninstall function that removes that file is "sudo rm -f /Original_OS", which means it's removing it as root. That means it should pretty much never fail. Are you sure you didn't just run the script as "RAM_booster.sh --uninstall" again?

---

### Post by Slim Odds on 2010-12-07
> **terminator14 said:**
> Good point. I think this is the basic idea behind preload, but I never could get preload to function properly. I wonder if something as simple as that (reading files in rc.local at boot) would end up with the exact same results in terms of speed of opening apps and speed of the OS itself as this script provides. If so, that would make the issue this script addresses be solved by something 100x simpler, which is always a good thing.

The only potential problem I see with simply reading a file in rc.local (not running it but simply reading it) is that any libraries the file needs when it runs will not be read into RAM. This won't cause any problems - it simply means when the app is launched by the user, the main file will already be in RAM but the libraries it needs will still need to be copied from the HDD to RAM before they can be used. I'm not a programmer, and having limited knowledge of exactly how libraries are linked to apps, I may be wrong about this, but I'm pretty sure this is the case.

I didn't go into that much detail, but yes, I was also thinking that you would want to read the libs as well. The 'ldd' program will tell you what libs an application references.

Like you said, it would be far simpler and also not impact the existing system in any way.

---

### Post by terminator14 on 2010-12-07
> **Slim Odds said:**
> I didn't go into that much detail, but yes, I was also thinking that you would want to read the libs as well. The 'ldd' program will tell you what libs an application references.

Like you said, it would be far simpler and also not impact the existing system in any way.

Definitely sounds like an idea that might work. I wonder if anyone has tried such a solution before. I whipped up a simple script to demo the theory. Here's the code: 

```
#!/bin/bash
while read LINE; do
	if [[ -r "$LINE" ]]
	then
		#Read file
		dd if=$LINE of=/dev/null

		#Read its library dependencies
		LIBS=$(ldd /bin/grep | grep -o '/.*[ ]')

		#Check if each file exists and read it
		IFS=$'\n'
		for LIBRARY in $(echo "$LIBS")
		do
			if [[ -e "$LIBRARY" ]]
			then
				dd if=$LIBRARY of=/dev/null
			fi
		done
	else
		#File not readable. Find out why
		if [[ ! -e "$LINE" ]]
		then
			echo "$LINE does not exist!"
		else
			echo "You do not have permission to read $LINE"
		fi
	fi
done < /filename/to/read/from
```

replace "/filename/to/read/from" with path to a file that contains programs you want to be preloaded into RAM. Each program needs to be on its own line and have its full path. Ex:

```
/usr/bin/firefox
/usr/bin/evolution
/usr/bin/vmware
```

If anyone wants to give it a go and post some results, that would be great. My SSD would make it hard to tell if it was working or not since either way is fast. 

Anyone who wants to test this: to test this, you'd basically need to see how long an app takes to launch after a reboot normally, then reboot again so the app is not in RAM anymore, run the script above and run the same app again. Here are the steps in point form so they are a little more clear:

1. Reboot
2. Start app (like firefox) and note how long it took to open
3. Close the app and reboot
4. Run above script
5. Start same app and note how long it took to open this time
6. Did the script make a difference?

This should show if it improved the load speed any. To make it permanent, just call the script above from rc.local, making it run at boot.

If you can, use larger apps, or ones that normally take the longest to load to make the difference more apparent.

Note: This is just a quick thing I wrote so I never bothered to save and run this. For all I know, there's a bracket missing somewhere (though I would have probably picked up on that). If it won't run, let me know. Also, if there's a better way to read a file so it's stored into RAM (not that there's anything wrong with the dd way AFAIK) let me know too.

If this works and gives good results, it will be funny how a script that I whipped up in 10 min in gedit, and that I never even bothered to save as I was working on it can accomplish the same thing as a script that took me a week to write, and had at least 5 different versions (save files at different stages of completion).

---

### Post by jim_deadlock on 2010-12-08
My installation went smoothly on 10.10 (32-bit) with a separate /home partition. I ended up with a 1.2G image so I need to delete some stuff to fit into my paltry 1G RAM but I'm unclear about this:

> "If saving space on that partition is your goal, you can also remove the old /home files which are still in the same place they used to be, they just get hidden by the new /home partition."Does this mean that if I delete some files in my original /home directory that will shrink my ramboost image so I can run it? Or do I need to delete stuff in /var/squashfs ?

---

### Post by nolag on 2010-12-08
Will it make a write back after issuing a shutdown?  Otherwise all updates will go away with a simple reboot, and that would suck.

---

### Post by terminator14 on 2010-12-08
> **jim_deadlock said:**
> My installation went smoothly on 10.10 (32-bit) with a separate /home partition. I ended up with a 1.2G image so I need to delete some stuff to fit into my paltry 1G RAM but I'm unclear about this:

Does this mean that if I delete some files in my original /home directory that will shrink my ramboost image so I can run it? Or do I need to delete stuff in /var/squashfs ?

"With a separate /home partition"? Did you already have that /home partition before you ran the script or did you give the script a device to copy your /home partition to?

That note means this:

If you gave the script a device to be your new /home partition, what it does is copy your existing files from /home to the new device. In then mounts the device as your /home in BOTH your original OS and the RAM Session. What happens on the original OS is that the original files at /home do NOT get deleted. When the device gets mounted at /home, it gets mounted OVERTOP of your old /home. That means there are still files there, you just don't see them unless you unmount your new device from /home. 

The only use of seeing the old files is a) cleanup - to make sure old junk isn't just lying around or b) to delete the files and shrink the partition your original OS was installed on.

NEITHER reasons affect the RAM Session in any way. Finding and deleting your old /home files will NOT make the squashfs image smaller because these files are NOT copied over to the RAM Session.

What you are looking for is deleting files from /var/squashfs that you don't need, and then rerunning the squashfs recreation commands (see inside of script for commands needed - search for 'mksquashfs'). The easier way to accomplish this (the way that doesn't require you to recreate the squashfs image manually) is to just remove (uninstall) packages from your Original OS that you don't need and that take up tons of space. After you do that, rerun the script (you may need to tell the script to uninstall first to remove the image you already created) so that it can make a new, smaller image.

The thing is though, with 1GB RAM, not only will you need to remove enough packages from your OS to fit the image into RAM, but you will need extra RAM for the OS to use (every program you run makes variables and stores stuff in RAM). That means you either need to remove somewhere close to 500MB of stuff so that the 1.2GB image would now be about 700MB, giving you 300MB of RAM, or the more practical alternative, is buy a little more RAM.

In your case, the following won't help you but if anyone still wants to find their old /home files, you will need to not be using the /home before you unmount it. Since your desktop uses /home, you need need to shut down your entire GUI and drop down to the terminal. To do this, make sure no applications are running, open terminal and type:

```
sudo service gdm stop
```

which will take you out to the console. After that, you may need to hit Alt + <- (left arrow) or Alt + -> (right arrow) to get a console you can log into. Login, make sure you cd out of /home by running:

```
cd /
```

unmount the device from your /home with:

```
sudo umount /home
```

and restart the GUI with

```
sudo service gdm start
```

Your desktop, and the rest of your /home folder is now the old version of them. You can delete these files since you have a backup of them on the device that gets mounted at boot to your /home. To remount the device as your /home again, just reboot and fstab will do this for you.

As an alternative for people who know their way around fstab, you can also comment out the line in fstab that mounts /home, reboot, deal with your old files, restore fstab, and reboot again. Make sure to fix fstab when you're done or your RAM Session's /home and your Original OS's /home will not be synced.

---

### Post by terminator14 on 2010-12-08
> **nolag said:**
> Will it make a write back after issuing a shutdown?  Otherwise all updates will go away with a simple reboot, and that would suck.

It will NOT make a write during a shutdown. And you are absolutely right in that all regular updates will be undone after a reboot. This is why I wrote the rupdate script, which does not update the RAM Session you are running but instead runs updates on the /var/squashfs from which the squashfs image is created. It then automatically recreates that image, and replaces your old image with it. That means the squashfs image will get the updates, and after you reboot, your updates will stick. rupdate is easy to use and basically does everything for you to update your squashfs image.

Do NOT using the regular Ubuntu updater unless you want temporary updates that last until the next reboot. Use rupdate (which gets copied to your path so you can run it from anywhere using the terminal) instead. Try "rupdate --help" to see all the different options it comes with.

---

### Post by jim_deadlock on 2010-12-08
The first time I attempted an install with my original /home but that created a hopelessly large 13G image, so I uninstalled and then used Gparted to create a new partition and used it for the "separate /home" option during the install - I also did some cleaning with ubuntu-tweak before I started. Unfortunately my old computer is maxed out at 1G RAM but I think I may be able to clear out 500M worth of packages, it'll be a good spring cleaning exercise for me anyway.

---

### Post by terminator14 on 2010-12-08
> **jim_deadlock said:**
> The first time I attempted an install with my original /home but that created a hopelessly large 13G image, so I uninstalled and then used Gparted to create a new partition and used it for the "separate /home" option during the install - I also did some cleaning with ubuntu-tweak before I started. Unfortunately my old computer is maxed out at 1G RAM but I think I may be able to clear out 500M worth of packages, it'll be a good spring cleaning exercise for me anyway.

Sounds like a plan. If you actually accomplish this, I'd be interested to know what packages you removed to clear up 500M.

---

### Post by Slim Odds on 2010-12-09
Sorry to say, but the original "solution" is overcomplicated to simply give the appearance of a faster system. The system is not really any faster since reading the applications and libraries must be read from disk at some point. And it is prone to too many potential problems.

I don't think that we are going to outsmart the linux file caching.

I actually liked the "preloading" the file cache idea. That one is much more natural, simple and does not have any side-effects.

---

### Post by terminator14 on 2010-12-09
> **Slim Odds said:**
> Sorry to say, but the original "solution" is overcomplicated to simply give the appearance of a faster system. The system is not really any faster since reading the applications and libraries must be read from disk at some point. And it is prone to too many potential problems.

I don't think that we are going to outsmart the linux file caching.

I actually liked the "preloading" the file cache idea. That one is much more natural, simple and does not have any side-effects.

You are right - one of the biggest problems with the script is its complexity and its potential for problems. I tried to overcome most of the problems I came across (like when I first boot a RAM Session, the internet wouldn't work) but there may be others I am not aware of that users of the script may run into (some problems more serious than others). Also, since I'm not an actual linux developer, I am not entirely sure how this script effects the OS under the hood. That means all I can do is fix problems that arise and have limited ability to predict which problems may show themselves in the future.

I still think that the solution might be useful to people with extremely slow hard drives however, since the OS would load everything in one go during boot, and work very quickly afterwards, instead of being slow throughout (until enough data got cached to speed up the OS that is). And despite the potential for problems, I haven't run into too many since the initial batch of problems I ran into (which the script already addresses).

I like the preloading idea too, specifically for its simplicity, and hopefully someone can help us try it out.

---

### Post by Slim Odds on 2010-12-10
Don't get me wrong. I appreciate your effort. But as you've learned, there are several ways to approach a problem and in this case I think that just preloading is much simpler and less error prone. Especially since it takes advantage of the existing file caching (which we all know works very well).

---

### Post by v5ar on 2010-12-10
> **Slim Odds said:**
> Don't get me wrong. I appreciate your effort. But as you've learned, there are several ways to approach a problem and in this case I think that just preloading is much simpler and less error prone. Especially since it takes advantage of the existing file caching (which we all know works very well).
yes, but those ways solve different problems

preloading idea works well for whats intended, you preload your application to memory and they are opened faster, but when that application reads/writes data to hard drive it doesnt have any effect on speed of that reading and writing, your hard drive has,
application loading is faster, because your application is already loaded but actually the biggest speed difference you gain or loose is your hard drive speed, because every millisecond some application is writing something to it, hence terminator14 mention having SSD makes your system really fast (and it should)

thats where implementation terminator14 posted comes in, ( and its concept that puppy uses)
everything is in memory, your application, your system, your partition (script gives you choice)
whatever your do, its done in memory, and no preloading can done that, unless you preload everything, and thats how we come to this solution, and still loading squash should be faster since its smaller than preloading everything as it is from your media

boot will be slower, since you have to load everything in memory, and no matter what solution you choose, youll always have to load everything if you want to load everthing, so time spent reading from hard drive is always the same, and the conclusion is that the only simple implementation of that can be made with terminator14s script

ive been thinking about this ide for some time, and since im programmer, thought i could approach this by making utility rather than script but terminator14s idea and implementation is really great and since i have no time maybe i could rather point what would suit better for some of us :)

in live mode puppy loads everthing to memory and then when you end your work, you can save everything by making squash from that sytem and then that is loaded next time, and again, when you end your work, its saved again, etc so you actully have normal system which runs very fast, no need for separation of /home or anything else obviosly

so your load everything to ram (which takes time) and you save everything to media (which takes time) but your system works really fast when your running it, obviously this is for those who want THAT!

so what i would like is just that, load your system, ok, then u make squash from running system (script does that? will try it after work), and then you run it from memory, and, again, when you want to shutdown, you run that script to make squash from currently running filesytem, which is in memory, but you save squash to your media, and at the next boot, that new squash is loaded to ram and so on

ill try it today, and if im right chroot and sudo rupdate do just that?

anyway, that solution should end up being very simple and error prone(you make squash, mount and load it to memory, use it and then recreate squash from that fileystem once again and use it next)
i think ill try to do that if i find time, just need to see more about squashfs and unionfs 

or just to ask, what would happen if i run that script in already running system from memory, where would that squash end up, it seems to me that your script is almost able to do what i want and before i can try for myself why not asking

PS
i use word media rather than hard drive since im doing all this on usb, and its painfully slow having your system on usb (unless its really fast usb, which it isnt)

---

### Post by terminator14 on 2010-12-10
> **v5ar said:**
> so what i would like is just that, load your system, ok, then u make squash from running system (script does that? will try it after work), and then you run it from memory, and, again, when you want to shutdown, you run that script to make squash from currently running filesytem, which is in memory, but you save squash to your media, and at the next boot, that new squash is loaded to ram and so on

ill try it today, and if im right chroot and sudo rupdate do just that?

That's kind of how it works, except the script is NOT run on every shutdown from within the RAM Session. This is because creating a new squashfs image takes a while, and unless you actually changed something (either downloaded updates, or change some settings in /etc), there's no need to recreate the squashfs image every time.

When you do need to update, rupdate does that. It updates the /var/squashfs on your main OS (/var/squashfs is the folder that stores a copy of your main OS) and then rupdate recreates the filesystem.squashfs image so that next time you reboot, and pick the RAM Session from the grub menu, you'll boot into an updated OS.

chroot lets you change settings in /var/squashfs (like /etc/hosts or something), and after running "sudo rupdate -f", a new filesystem.squashfs file will be created with those settings saved.

> **v5ar said:**
> what would happen if i run that script in already running system from memory

The script has a safeguard to make sure it doesn't run from within the RAM session. If you remove a few lines in the script (remove the safeguard) and ran it from the RAM Session anyway, I imagine it would treat the RAM Session as a regular system and try to copy it to /var/squashfs. If it was successful, it would create a /live/filesystem.squashfs and change your grub to point to it. The problem with that is:

1. Since your /var and /live (which would be created) would be in your RAM, you would run out of RAM very quickly.

2. Even if you had like 12GB of RAM and it completed, as soon as you reboot, the /var/squashfs and /live inside the RAM Session would disappear, which would make grub have an entry pointing to a non-existent squashfs file - that is assuming it would not get any errors trying to create a grub entry for a file located in RAM in the first place.

If you were to modify the script however so that if it is run from the RAM Session, it would use rsync to sync up the RAM Session with /var/squashfs, leave grub alone, and recreate the filesystem.squashfs file, placing it where the old file was, I suppose it could work the way you want.

---

### Post by Stason on 2010-12-22
> **Slim Odds said:**
> You could accomplish the same result by simply creating a list of applications that you want to be "first time fast" and just read them from disk in rc.local during startup.


Could you please elaborate on how to list needed programs in rc.local?

---

### Post by Slim Odds on 2010-12-22
> **Stason said:**
> Could you please elaborate on how to list needed programs in rc.local?

I'm not really sure. You can make your own list of applications that you use most. Then you can use ldd to determine what libraries it uses. That would be a start.

terminator had a script earlier in this thread that seems to be a good start.

---

### Post by davek06 on 2010-12-27
Hi, I have maybe a dumb question, but, if my root partition has 7 GB of data and I have separated /home, does it mean, that I need to have at least 7 GB of RAM ?? And that every time I would like to boot to RAM it would copy 7 GB of data? thx for answer

D.

---

### Post by terminator14 on 2010-12-28
> **davek06 said:**
> Hi, I have maybe a dumb question, but, if my root partition has 7 GB of data and I have separated /home, does it mean, that I need to have at least 7 GB of RAM ?? And that every time I would like to boot to RAM it would copy 7 GB of data? thx for answer

D.

Wow 7GB on the root partition? Really? That sounds unusually large to me. Are you sure you aren't including /home in that? Try:

```
df -h /
```

if you are unsure. But if you are sure, then ya, I suppose in that case, you would need 7GB of RAM + another few hundred MB for the OS to work with (at least). 

If you know where most of that 7GB is located (like if it's in /root or something), you could try modifying the script to mount that particular folder somewhere else at boot, or modify the RAM Session's /etc/fstab to do so after the script has finished running (modify /var/squashfs/etc/fstab to point to a device for that folder, then reconstruct the squashfs image), exactly like the script does with /home, but as it stands now, the script isn't written to handle something like that.

If you were to run the script, you could see just how large your /live/filesystem.squashfs image had become. I haven't used the script since I've written it (have been running my OS from an SSD instead), so I don't remember if squashfs images do any kind of compression, and what the compression ratio might be. The best way to check is just to run it. If it's too large, and you can't use it, run the uninstall script and it will be deleted.

---

### Post by TheeMahn2003 on 2011-01-03
> **terminator14 said:**
> Wow 7GB on the root partition? Really? That sounds unusually large to me. Are you sure you aren't including /home in that? Try:

```
df -h /
```

if you are unsure. But if you are sure, then ya, I suppose in that case, you would need 7GB of RAM + another few hundred MB for the OS to work with (at least). 

If you know where most of that 7GB is located (like if it's in /root or something), you could try modifying the script to mount that particular folder somewhere else at boot, or modify the RAM Session's /etc/fstab to do so after the script has finished running (modify /var/squashfs/etc/fstab to point to a device for that folder, then reconstruct the squashfs image), exactly like the script does with /home, but as it stands now, the script isn't written to handle something like that.

If you were to run the script, you could see just how large your /live/filesystem.squashfs image had become. I haven't used the script since I've written it (have been running my OS from an SSD instead), so I don't remember if squashfs images do any kind of compression, and what the compression ratio might be. The best way to check is just to run it. If it's too large, and you can't use it, run the uninstall script and it will be deleted.

The squash file system is substantially reduced in size by compression using Ultimate Edition 2.6.1 as an example.  The filesystem.squashfs is 2.4 GB (2,620,391,424 bytes) the true filesystem size is: 7,699,632,128 bytes.  I do not know if you have seen my [screenshots]("http://ubuntuforums.org/showpost.php?p=10311996&postcount=86") comparing a fairly fast ssd and "toram".  I imagine the minimum amount of ram to do as I am doing to be 4GB, maybe 3GB (loading 2.4 GB squash to ram and leaving enough ram to use it effectively to load applications into memory)

I have been giving this real thought in my case having 8GB of ram.  To have it fully boot up create another ram-drive say a 1/2 GB and copying my home folder to it then un-mounting the old hard disk based home folder pointing it to the newly apointed ram-disk, on shutdown reversing the process.

I notice alot of load time being from say firefox and cache being pulled from hard disk.  It was really noticeable when I set my home folder to a USB stick.

I went back changed the fstab to what was the original boot drive, re-built squash and sudo cp -a /home/* /  I now I have 2 separate home folders depending which kernel I select a regular boot uses my regular home folder and boot to ram using /theemahn/  I noticed a considerable speed gain over the 33MB/s of the USB stick, but 100MB/s v/s 2.1GB/s would be the bomb.  It would slow down the boot-up and shutdown process, but I typically only boot every few days.

If I have time to look into / write a script to automate this.  I will be more then happy to share it with you fellas.

If you would like to see what I refer to in compression this is a few of the command I use to build Ultimate Edition:

#calculate disksize or ubiquity will be inaccurate
printf $(sudo du -sx --block-size=1 edit | cut -f1) > extract-cd/casper/filesystem.size

In your scripts case would be:
printf $(sudo du -sx --block-size=1 /var/squashfs/ | cut -f1) > /tmp/squashfs.size
cat /tmp/squashfs.size #this will display the size of the contents of what will be the virtual disk this we honesty do not care about.
rm /tmp/squashfs.size #cleanup

To obtain what will be the size of the ramdisk required would be a formula size of "results" + say 512mb (maybe a little less)
printf $(sudo du -sx --block-size=1 /live/filesystem.squashfs  | cut -f1) > /tmp/ram.size
cat /tmp/ram.size
rm /tmp/ram.size

It would be quite simple instead of cat to assign as variables and calculate.

I just thought I would try and help out.  I am sorry to say this, but I am rarely on this board.  If you have any questions or need assistance it is probably more likely that you will get a response on our forum see my sig.

I have started testing speed, I have introduced a 500mb ramdisk, I eventually want to populate with my home to test all scenarios.  I am afraid this may involve me re-writing sections of casper the friendly ghost.

theemahn@SledgeHammer:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
aufs                  4.0G   20M  3.9G   1% /
none                  4.0G  320K  4.0G   1% /dev
/dev/shm              2.5G  2.5G   56K 100% /live/image
tmpfs                 4.0G   20M  3.9G   1% /live/cow
tmpfs                 4.0G     0  4.0G   0% /live
none                  4.0G   20M  3.9G   1% /var/lib/ureadahead/debugfs
none                  4.0G  268K  4.0G   1% /dev/shm
tmpfs                 4.0G   12K  4.0G   1% /tmp
none                  4.0G  320K  4.0G   1% /var/run
none                  4.0G     0  4.0G   0% /var/lock
none                  4.0G     0  4.0G   0% /lib/init/rw
/dev/sda2              75G   68G  7.0G  91% /media/Winderz
/dev/sdb1             100G   23G   72G  24% /home
/dev/sdb2             831G  816G   15G  99% /media/TeraByte
/ramdisk              500M     0  500M   0% /ramdisk
/dev/sdc1             466G  443G   24G  95% /media/Tuneage
/dev/sdd1             3.8G  8.0K  3.8G   1% /media/008F-0EEB
/dev/sde1             466G  316G  151G  68% /media/Storage
theemahn@SledgeHammer:~$ nano /etc/fstab


I opened firefox and 20 tabs (huge difference in load as apposed to 1 or blank) with various webpages & began.

Cold start not using ramdrive:
#clear the cache
theemahn@SledgeHammer:~$ sync; echo 3 | sudo tee /proc/sys/vm/drop_caches
theemahn@SledgeHammer:~$/usr/bin/time firefox -P default
5.47user 0.44system 0:09.22elapsed 64%CPU (0avgtext+0avgdata 745648maxresident)k
24inputs+25904outputs (0major+113499minor)pagefaults 0swaps

Cached not using ramdrive:
5.27user 1.33system 0:10.70elapsed 61%CPU (0avgtext+0avgdata 705824maxresident)k
95886inputs+27472outputs (399major+110080minor)pagefaults 0swaps

Very little gain, barely over 1 sec.

If I have time will come back and post results when the entire O/S including home is stored in ram.  After watching the thumb drive light flash for things as simple as key-presses I believe the home folder to be a key element & noticeable difference.  Bootchart even after loading the ISO to ram had some large spikes as it was accessing the home folder on USB, further leading me to believe this theory.

---

### Post by terminator14 on 2011-01-04
> **TheeMahn2003 said:**
> The squash file system is substantially reduced in size by compression using Ultimate Edition 2.6.1 as an example.  The filesystem.squashfs is 2.4 GB (2,620,391,424 bytes) the true filesystem size is: 7,699,632,128 bytes.  I do not know if you have seen my [screenshots]("http://ubuntuforums.org/showpost.php?p=10311996&postcount=86") comparing a fairly fast ssd and "toram".  I imagine the minimum amount of ram to do as I am doing to be 4GB, maybe 3GB (loading 2.4 GB squash to ram and leaving enough ram to use it effectively to load applications into memory)

So squashfs does do compression, and a considerable amount apparently. Interesting - thanks for the info. And yes, I have seen your screenshots - and they're almost unbelievable, thanks for those as well.

> **TheeMahn2003 said:**
> I have been giving this real thought in my case having 8GB of ram.  To have it fully boot up create another ram-drive say a 1/2 GB and copying my home folder to it then un-mounting the old hard disk based home folder pointing it to the newly apointed ram-disk, on shutdown reversing the process.

I notice alot of load time being from say firefox and cache being pulled from hard disk.  It was really noticeable when I set my home folder to a USB stick.

I went back changed the fstab to what was the original boot drive, re-built squash and sudo cp -a /home/* /  I now I have 2 separate home folders depending which kernel I select a regular boot uses my regular home folder and boot to ram using /theemahn/  I noticed a considerable speed gain over the 33MB/s of the USB stick, but 100MB/s v/s 2.1GB/s would be the bomb.  It would slow down the boot-up and shutdown process, but I typically only boot every few days.

If I have time to look into / write a script to automate this.  I will be more then happy to share it with you fellas.

A slightly more dangerous approach to keeping your /home past a reboot, as a power outage would revert you back to the last version of your /home, but it should speed up the OS even more, and by the sound of it, considerably so. Interesting - especially since the use of a UPS and the stability of Linux makes this approach not all that much more "dangerous". If you make a modification like that (I'm assuming you'll start with my script rather than from scratch?) I'll be glad to either upload the file on this thread and give you credit, or link to your thread if you chose to make one. Even if you choose to start from scratch (which I don't see a reason for unless you want to do a lot more than just this feature), the projects sound similar enough that I'll link to your thread or wherever you upload it (if you permit me to do so).

> **TheeMahn2003 said:**
> If you would like to see what I refer to in compression this is a few of the command I use to build Ultimate Edition:

#calculate disksize or ubiquity will be inaccurate
printf $(sudo du -sx --block-size=1 edit | cut -f1) > extract-cd/casper/filesystem.size

In your scripts case would be:
printf $(sudo du -sx --block-size=1 /var/squashfs/ | cut -f1) > /tmp/squashfs.size
cat /tmp/squashfs.size #this will display the size of the contents of what will be the virtual disk this we honesty do not care about.
rm /tmp/squashfs.size #cleanup

To obtain what will be the size of the ramdisk required would be a formula size of "results" + say 512mb (maybe a little less)
printf $(sudo du -sx --block-size=1 /live/filesystem.squashfs  | cut -f1) > /tmp/ram.size
cat /tmp/ram.size
rm /tmp/ram.size

It would be quite simple instead of cat to assign as variables and calculate.

I just thought I would try and help out.

It would be nice if people could run a few, or one line in bash to determine if they have enough RAM for the ram session before ever running the script.

The problem with:

```
sudo du -sx --block-size=1 /live/filesystem.squashfs  | cut -f1
```

is that the file /live/filesystem.squashfs is created during the very last stage of the script, so it can't be accessed until the script is done running.

```
sudo du -sx --block-size=1 /var/squashfs/ | cut -f1
```

on the other hand can be used before the script runs with a slight modification (since /var/squashfs isn't created until about half way through the script):

```
sudo du -hcs --one-file-system / --exclude=/dev/* --exclude=/tmp/* --exclude=/sys/* --exclude=/proc/* --exclude=/home/*
```

which should, in theory, show how much space you need for your RAM session, though I'm not 100% sure about its accuracy. You would also need to add the extra 512MB or w/e for the system to use for regular operations.

> **TheeMahn2003 said:**
> I am sorry to say this, but I am rarely on this board.  If you have any questions or need assistance it is probably more likely that you will get a response on our forum see my sig.

I have started testing speed, I have introduced a 500mb ramdisk, I eventually want to populate with my home to test all scenarios.  I am afraid this may involve me re-writing sections of casper the friendly ghost.

theemahn@SledgeHammer:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
aufs                  4.0G   20M  3.9G   1% /
none                  4.0G  320K  4.0G   1% /dev
/dev/shm              2.5G  2.5G   56K 100% /live/image
tmpfs                 4.0G   20M  3.9G   1% /live/cow
tmpfs                 4.0G     0  4.0G   0% /live
none                  4.0G   20M  3.9G   1% /var/lib/ureadahead/debugfs
none                  4.0G  268K  4.0G   1% /dev/shm
tmpfs                 4.0G   12K  4.0G   1% /tmp
none                  4.0G  320K  4.0G   1% /var/run
none                  4.0G     0  4.0G   0% /var/lock
none                  4.0G     0  4.0G   0% /lib/init/rw
/dev/sda2              75G   68G  7.0G  91% /media/Winderz
/dev/sdb1             100G   23G   72G  24% /home
/dev/sdb2             831G  816G   15G  99% /media/TeraByte
/ramdisk              500M     0  500M   0% /ramdisk
/dev/sdc1             466G  443G   24G  95% /media/Tuneage
/dev/sdd1             3.8G  8.0K  3.8G   1% /media/008F-0EEB
/dev/sde1             466G  316G  151G  68% /media/Storage
theemahn@SledgeHammer:~$ nano /etc/fstab


I opened firefox and 20 tabs (huge difference in load as apposed to 1 or blank) with various webpages & began.

Cold start not using ramdrive:
#clear the cache
theemahn@SledgeHammer:~$ sync; echo 3 | sudo tee /proc/sys/vm/drop_caches
theemahn@SledgeHammer:~$/usr/bin/time firefox -P default
5.47user 0.44system 0:09.22elapsed 64%CPU (0avgtext+0avgdata 745648maxresident)k
24inputs+25904outputs (0major+113499minor)pagefaults 0swaps

Cached not using ramdrive:
5.27user 1.33system 0:10.70elapsed 61%CPU (0avgtext+0avgdata 705824maxresident)k
95886inputs+27472outputs (399major+110080minor)pagefaults 0swaps

Very little gain, barely over 1 sec.

If I have time will come back and post results when the entire O/S including home is stored in ram.  After watching the thumb drive light flash for things as simple as key-presses I believe the home folder to be a key element & noticeable difference.  Bootchart even after loading the ISO to ram had some large spikes as it was accessing the home folder on USB, further leading me to believe this theory.

I would have thought caching would have had a bigger impact. I would also be curious to know how long the same test would take in a ram session on the same machine.

---

### Post by Slim Odds on 2011-01-04
The entire reason the word "squash" is in "squashfs" is because it is a compressed file system.

It's a bit of a "cute" word for compressed.

---

### Post by terminator14 on 2011-01-04
> **Slim Odds said:**
> The entire reason the word "squash" is in "squashfs" is because it is a compressed file system.

It's a bit of a "cute" word for compressed.

I thought it might have been because the entire file system was squashed into a single file, but that makes sense. Thanks

---

### Post by gimfred on 2011-01-09
On reading this thread (I haven't done it dispite having adequate ram specs) I wondered if it would be possible to sync/mirror the ram drive (rdd) to a copy of your squashfs via rsync. 

In my mind:

squashfs > rdd ... rsync (rdd > hdd) | [cron job] +5m

on synaptic/apt-get/whatever/, data is written to rdd then
rsync approprate dirs for changes. Would this cause problems?

---

### Post by terminator14 on 2011-01-10
> **gimfred said:**
> On reading this thread (I haven't done it dispite having adequate ram specs) I wondered if it would be possible to sync/mirror the ram drive (rdd) to a copy of your squashfs via rsync. 

In my mind:

squashfs > rdd ... rsync (rdd > hdd) | [cron job] +5m

on synaptic/apt-get/whatever/, data is written to rdd then
rsync approprate dirs for changes. Would this cause problems?

If I understand you correctly, you're wondering if it's possible to run a cron job, say every 5 min, to rsync the RAM session you're in to the squashfs image.

In theory, it should be. There are a few problems that need to be overcome in order to make this happen however:

Since the filesystem.squashfs file is a readonly file and cannot be modified, the cronjob would have to rsync the RAM Session to the /var/squashfs folder from which the filesystem.squashfs image is created. This means the squashfs image would need to be recreated from /var/squashfs before the image could be usable (before the updates rsync has produced can be available). This poses a different problem:

Recreating the squashfs image using mksquashfs every 5 minutes would use up a significant amount of processing power. This would unnecessarily slow down the RAM Session because the CPU would always be busy. I say "unnecessarily" because most of that processing power would go towards creating images that would NOT be used - only the last image created before you reboot would be used. This means running mksquashfs every time you rsync would be impractical. 

What that means is that the user will have to either run a command or a script just before he reboots that will run mksquashfs for him, in order to recreate the squashfs image and make the updates copied over by rsync available next time he reboots. That also means that it would take the user several minutes to reboot his computer. He could of course opt out of running mksquashfs during the reboot, and the /var/squashfs folder would remain updated, but that would mean the filesystem.squashfs file would not be. This would result in the user booting into an older, un-updated version of the RAM session. From there, the user can run the mksquashfs command and reboot again to boot from the new image, but the problem then becomes: if crontab updates an already updated /var/squashfs automatically it will override any updates that /var/squashfs may have had.

In order to solve this problem, the script can force a mksquashfs command to run upon reboot or shutdown. The unfortunate side-effect of this would be that the user will be unable to use his computer while the script is running as I imagine the script would run at a stage in the shutdown process that would make the desktop, and other applications (such as firefox) unavailable to him. This would cause the user to have no choice but to stare at the screen as mksquashfs does its thing, or go for a walk.

The entire problem could be avoided if you could write directly to the read-only filesystem.squashfs image, and from what I've read, this could be possible if you combine the image with a union mount filesystem such as UnionFS or aufs, but I know far too little about either to know if this is something that could be done.

---

### Post by joesnose on 2011-01-15
> **yesrno said:**
> Hmmm so I tried your script out, but at some point it was asking me to choose between 3 options - where to store the home folder. So I entered a 2, which would be for choosing a disk manually, but when I entered 2 the scripts started doing all kinds of things and at one point I saw it copying my home folder to somewhere (?) and then I saw it was trying to copy all my VM disks and I canceled the script :oops:. I ran the un-installer and it says it's un-installed but when I run the script again, it says the only option is to un-uninstall :o!


I have this very same problem.

I already have a home partition.

When i try to uninstall it says it has uninstalled but upon restarting the script it just tells me i need to uninstall. the only way to fix this is to manualy delete Original_OS.

here is what my terminal spits out if it helps.

```
1) Launch gparted (it will be installed if necessary)
2) Enter device name to use for /home
3) Exit script
-ne 
Your choice: 
2










-e You have chosen to enter the device name to use for /home

-e Please enter the device name of the partition you wish to use for
/home. This should be something like /dev/hda2 or similar. Please be certain
about your choice as any data on the partition you choose will be deleted
permanently!

Your choice: read: 1235: Illegal option -e
















RAM_booster.sh: 1235: [[: not found
RAM_booster.sh: 1235: [[: not found
-e Running file check on your device...

RAM_booster.sh: 1235: [[: not found
RAM_booster.sh: 1235: [[: not found
RAM_booster.sh: 1235: [[: not found
Everything checks out.
-e Formatting 

```

---

### Post by joesnose on 2011-01-15
> **yesrno said:**
> Hmmm so I tried your script out, but at some point it was asking me to choose between 3 options - where to store the home folder. So I entered a 2, which would be for choosing a disk manually, but when I entered 2 the scripts started doing all kinds of things and at one point I saw it copying my home folder to somewhere (?) and then I saw it was trying to copy all my VM disks and I canceled the script :oops:. I ran the un-installer and it says it's un-installed but when I run the script again, it says the only option is to un-uninstall :o!


I have this very same problem.

I already have a home partition.

When i try to uninstall it says it has uninstalled but upon restarting the script it just tells me i need to uninstall. the only way to fix this is to manualy delete Original_OS.

here is what my terminal spits out if it helps.

```
1) Launch gparted (it will be installed if necessary)
2) Enter device name to use for /home
3) Exit script
-ne 
Your choice: 
2










-e You have chosen to enter the device name to use for /home

-e Please enter the device name of the partition you wish to use for
/home. This should be something like /dev/hda2 or similar. Please be certain
about your choice as any data on the partition you choose will be deleted
permanently!

Your choice: read: 1235: Illegal option -e
















RAM_booster.sh: 1235: [[: not found
RAM_booster.sh: 1235: [[: not found
-e Running file check on your device...

RAM_booster.sh: 1235: [[: not found
RAM_booster.sh: 1235: [[: not found
RAM_booster.sh: 1235: [[: not found
Everything checks out.
-e Formatting 

```

---

### Post by joesnose on 2011-01-15
sorry double post

---

### Post by joesnose on 2011-01-15
> **yesrno said:**
> Hmmm so I tried your script out, but at some point it was asking me to choose between 3 options - where to store the home folder. So I entered a 2, which would be for choosing a disk manually, but when I entered 2 the scripts started doing all kinds of things and at one point I saw it copying my home folder to somewhere (?) and then I saw it was trying to copy all my VM disks and I canceled the script :oops:. I ran the un-installer and it says it's un-installed but when I run the script again, it says the only option is to un-uninstall :o!


I have this very same problem.

I already have a home partition.

When i try to uninstall it says it has uninstalled but upon restarting the script it just tells me i need to uninstall. the only way to fix this is to manualy delete Original_OS.

here is what my terminal spits out if it helps.

```
1) Launch gparted (it will be installed if necessary)
2) Enter device name to use for /home
3) Exit script
-ne 
Your choice: 
2










-e You have chosen to enter the device name to use for /home

-e Please enter the device name of the partition you wish to use for
/home. This should be something like /dev/hda2 or similar. Please be certain
about your choice as any data on the partition you choose will be deleted
permanently!

Your choice: read: 1235: Illegal option -e
















RAM_booster.sh: 1235: [[: not found
RAM_booster.sh: 1235: [[: not found
-e Running file check on your device...

RAM_booster.sh: 1235: [[: not found
RAM_booster.sh: 1235: [[: not found
RAM_booster.sh: 1235: [[: not found
Everything checks out.
-e Formatting 

```

---

### Post by terminator14 on 2011-01-15
> **joesnose said:**
> I have this very same problem.

I already have a home partition.

When i try to uninstall it says it has uninstalled but upon restarting the script it just tells me i need to uninstall. the only way to fix this is to manualy delete Original_OS.

here is what my terminal spits out if it helps.

```
1) Launch gparted (it will be installed if necessary)
2) Enter device name to use for /home
3) Exit script
-ne 
Your choice: 
2










-e You have chosen to enter the device name to use for /home

-e Please enter the device name of the partition you wish to use for
/home. This should be something like /dev/hda2 or similar. Please be certain
about your choice as any data on the partition you choose will be deleted
permanently!

Your choice: read: 1235: Illegal option -e
















RAM_booster.sh: 1235: [[: not found
RAM_booster.sh: 1235: [[: not found
-e Running file check on your device...

RAM_booster.sh: 1235: [[: not found
RAM_booster.sh: 1235: [[: not found
RAM_booster.sh: 1235: [[: not found
Everything checks out.
-e Formatting 

```

The only reason '[[' would not be found (as in the line "RAM_booster.sh: 1235: [[: not found") that I can think of (and the simplest explanation) is that you're forcing the script to run in /bin/sh rather than /bin/bash because /bin/sh has no idea what '[[' is. This script will NOT work in /bin/sh. Try again by making it executable with:

```
sudo chmod a+x ./RAM_booster.sh
```

and running it with:

```
./RAM_booster.sh
```

---

### Post by joesnose on 2011-01-15
Thanks Terminator, that solved all my problems, both uninstalling and installing.

thanks for the great script.

---

### Post by terminator14 on 2011-01-15
> **joesnose said:**
> Thanks Terminator, that solved all my problems, both uninstalling and installing.

thanks for the great script.

Glad I was able to help :)

---

### Post by Bazzi313 on 2011-01-16
how do u run the script

---

### Post by James78 on 2011-01-16
Your script is VERY interesting. I can't wait to try this out. Thanks for all the work you did!

Note: You spelled separate as seporate everywhere, not a problem, but thought you might like to know. :)

> **Bazzi313 said:**
> how do u run the script
```
chmod +x RAM_booster.sh
sudo ./RAM_booster.sh
```

---

### Post by terminator14 on 2011-01-16
> **James78 said:**
> Your script is VERY interesting. I can't wait to try this out. Thanks for all the work you did!

Thanks. Glad people appreciate the work I put in. :)

> **James78 said:**
> Note: You spelled separate as seporate everywhere, not a problem, but thought you might like to know. :)

Haha I guess I should find a spellcheck that works with gedit - or work on my spelling. I corrected it. Thanks.

I also added a check to make sure people aren't forcing it to run in sh, which should help some people figure out why they are having errors running it. It's just too bad the counter for number of downloads of the script got reset - that was an interesting statistic.

---

### Post by Bazzi313 on 2011-01-17
```
chmod +x RAM_booster.sh
sudo ./RAM_booster.sh
```[/QUOTE]

its says no command, and is this after downloading scipt ?

---

### Post by terminator14 on 2011-01-17
> **Bazzi313 said:**
> ```
chmod +x RAM_booster.sh
sudo ./RAM_booster.sh
```

its says no command, and is this after downloading scipt ?

Download the script, move it to your Desktop from your Downloads folder, and open the terminal. Cd to your Desktop:

```
cd ~/Desktop
```

untar the script:

```
tar -xzf RAM_booster.sh.tar.gz
```

give yourself execute permissions on it:

```
sudo chmod a+x RAM_booster.sh
```

and run it as root:

```
sudo ./RAM_booster.sh
```

---

### Post by mande01 on 2011-01-18
Hello,
this looks really cool, I came here looking for a debian version of FreeNAS.
Basically i want to use debian (or ubuntu) as a server. But i want it to load the OS into Ram like FreeNAS does with its embedded version.

Do you think this script would be good for that?
Any suggestions or hints before I begin?

I plan on running the system off an SD card or USB key and load the system on RAM.
Then have all the storage on SATA drives, specifically the frequent files/apps on a small fast SATA (not SSD) and the rest of the storage on 1.5TB drives.

Any pointers or information would be great.

Thanks,
And hopefully I'll be reporting back soon.
Der

---

### Post by mande01 on 2011-01-18
Hello,
this looks really cool, I came here looking for a debian version of FreeNAS.
Basically i want to use debian (or ubuntu) as a server. But i want it to load the OS into Ram like FreeNAS does with its embedded version.

Do you think this script would be good for that?
Any suggestions or hints before I begin?

I plan on running the system off an SD card or USB key and load the system on RAM.
Then have all the storage on SATA drives, specifically the frequent files/apps on a small fast SATA (not SSD) and the rest of the storage on 1.5TB drives.

Any pointers or information would be great.

Thanks,
And hopefully I'll be reporting back soon.
Der

---

### Post by terminator14 on 2011-01-18
Judging from all the double posts recently, I guess it's not just me having problems with ubuntuforums not loading pages in the last couple days. Anyone know what's going on with that?

> **mande01 said:**
> Hello,
this looks really cool, I came here looking for a debian version of FreeNAS.
Basically i want to use debian (or ubuntu) as a server. But i want it to  load the OS into Ram like FreeNAS does with its embedded version.

Do you think this script would be good for that?
Any suggestions or hints before I begin?

I plan on running the system off an SD card or USB key and load the system on RAM.
Then have all the storage on SATA drives, specifically the frequent  files/apps on a small fast SATA (not SSD) and the rest of the storage on  1.5TB drives.

Any pointers or information would be great.

Thanks,
And hopefully I'll be reporting back soon.
Der

If you decide to go the debian route, you will more than likely need to modify this script to do for debian what it does now for Ubuntu. I'm not sure quite how much modification is required, and for all I know it might work as is, but it's unlikely. You could also try to find a debian based project that does the same thing, but I'm not aware of any.

As for doing this with ubuntu - I thought about doing the same thing when I was writing the script but I had enough servers so I ended up not doing so. The things you should keep in mind are:

1. If you reconfigure your server in the RAM session, it will NOT be permanent. You need to use the rchroot script to configure your /var/squashfs instead. This of course applies to all cases, not just server builds, but you need to make sure you understand this before you proceed or you might end up killing several hours or even days configuring a server that will get its settings wiped just after a reboot. Read the **Manual** and **Tricks** sections of [http://ubuntuforums.org/showpost.php?p=9960597&postcount=1](http://ubuntuforums.org/showpost.php?p=9960597&postcount=1) carefully and make sure you understand them.

2. This script is untested with the Ubuntu Server Edition. You will either need to start out with regular Ubuntu and add server programs to it, or test and modify the script to work with the Ubuntu Server Edition if that is what you prefer.

3. /var/log/ is stored in RAM. This means unless you copy your logs to some sort of storage regularly, a reboot or power outage would result in you losing all your logs. In case someone hacks your server, all they would have to do is issue the reboot command to wipe any tracks they may have left behind in the logs. If the server crashes for some reason, you may also have a tough time figuring out why it happened if you don't have logs to look back at.

4. /var/www/ is stored in RAM. If your server is going to be running apache, or any other web server, you may want to link /var/www/ with another directory on a device that can store the files more permanently than RAM can. Either that, or you could simply make sure you copy the files over when you boot from storage to /var/www/, or edit the /var/squashfs/var/www/ to contain the files (using rchroot). In theory, having /var/www/ in RAM should speed up the web server's ability to serve up pages, but apache probably stores those pages in cache either way, so it won't make much of a difference.

5. There may be other unexpected problems that I am not aware of. Make sure you run plenty of tests on your server once you think you're done configuring. Reboot, and make sure all the settings are still there. You don't want to have a server that runs for 6 months keeping a RAID5 working, only to find out that after a reboot, it no longer recognizes the drives that were part of the RAID and your data (6 months worth) is gone.

PS. And maybe I should have led with this:

Servers like Debian or Ubuntu Server Edition are pre-configured to store active daemons (programs) in cache (RAM), while keeping config files that need to be remembered on the HDD. Using this script for a server would probably be more trouble than it would be worth. The only upside would likely be bragging rights that you have a "super fast server" although in reality it would probably be only slightly faster than a normal server, if at all.

---

### Post by James78 on 2011-01-20
To the thread OP. I see there's a Tutorials and tips forum... Do you think that might be a better place for this topic? :)

---

### Post by terminator14 on 2011-01-20
> **James78 said:**
> To the thread OP. I see there's a Tutorials and tips forum... Do you think that might be a better place for this topic? :)

Yes, I do. Or I did. That's why I posted the [original thread there]("http://ubuntuforums.org/showthread.php?t=1499338"), and that's why I posted this thread there. Anything that gets posted in the tutorials & tips needs to be reviewed by a moderator first. When a mod reviewed this thread, he decided this would be a better place for it since the majority of it is one script, so the mod moved it.

---

### Post by James78 on 2011-01-20
> **terminator14 said:**
> Yes, I do. Or I did. That's why I posted the [original thread there]("http://ubuntuforums.org/showthread.php?t=1499338"), and that's why I posted this thread there. Anything that gets posted in the tutorials & tips needs to be reviewed by a moderator first. When a mod reviewed this thread, he decided this would be a better place for it since the majority of it is one script, so the mod moved it.
Ahhhh, I seee. :D I could've used this script, were it not for how big my squashfs image was. 3GB, I have 2.99GB (4GB in my system), 64 bit.. Somethings eating 1GB :(. But the parts I did use, it worked really well and I had no problems. It was really easy to get back to the default configuration I had before.

---

### Post by terminator14 on 2011-01-20
> **James78 said:**
> Ahhhh, I seee. :D I could've used this script, were it not for how big my squashfs image was. 3GB, I have 2.99GB (4GB in my system), 64 bit.. Somethings eating 1GB :(. But the parts I did use, it worked really well and I had no problems. It was really easy to get back to the default configuration I had before.

Cool, glad most of it worked for you - too bad it was everything but the useful part :).

---

### Post by AlecTeal on 2011-01-21
this is brilliant i think - its doing its thing now

when it updates does it re-do the entire thing again or just the changes?

is it also posible to exclude directories, i use an encrypted fs for my home; its just copied that, and the home directory.

and then it tried to copy /mount

good tool guys, nearly ready to be used :)

---

### Post by terminator14 on 2011-01-21
> **AlecTeal said:**
> when it updates does it re-do the entire thing again or just the changes?

It does the whole process over again - it runs mksquashfs on /var/squashfs/ to create the image. As far as I know there's no simple way to write to the image once it's made so just copying the changes with rsync (or similar) is not an easy task.

> **AlecTeal said:**
> is it also posible to exclude directories, i use an encrypted fs for my home; its just copied that, and the home directory.

Excluding directories is not really built into the script as an option, but if you open the script for editing and search for the word "exclude", you will find this:

```
#Check if /home needs to be included in the file system transfer
if [[ "$NewHome" == "true" ]]
then
	#Exclude /home. It will be copied later.
	sudo rsync -av --delete / ${DEST} --exclude=/proc/* --exclude=/tmp/* --exclude=/dev/* --exclude=/sys/* --exclude=/home/* --exclude=/etc/mtab --exclude=/live --exclude=/RAM_Session --exclude=/Original_OS --exclude=${DEST} 2>&1 | tee /tmp/fs_sync
else
	#Don't exclude /home. Delete anything in Trash for every user being copied.
	sudo rsync -av --delete / ${DEST} --exclude=/proc/* --exclude=/tmp/* --exclude=/dev/* --exclude=/sys/* --exclude=/etc/mtab --exclude=/live --exclude=.gvfs --exclude=.local/share/Trash/files/* --exclude=/RAM_Session --exclude=/Original_OS --exclude=${DEST} 2>&1 | tee /tmp/fs_sync
fi
```

If you add another "--exclude=/..." to those (if you're not sure which one to add it to, add to both - it shouldn't cause any problems), whatever you need excluded will be.

If what you want excluded is INSIDE the /home however and the /home is going to be copied to a new partition, what you're looking for is this line to add an --exclude statement to:

```
sudo mkdir -p /mnt/home && sudo mount $DEVICE /mnt/home && sudo rsync --progress -rav --exclude=.gvfs --exclude=.local/share/Trash/files/* /home/* /mnt/home/
```

> **AlecTeal said:**
> and then it tried to copy /mount

/mount is not part of a regular filesystem. Ubuntu already has a /mnt and /media for mounting. The script can't really guess at what's important and what's not if you have modified your filesystem structure - it assumes you stick to what Ubuntu provides you, which should be the case 99% of the time (hopefully).

Looking at the rsync commands I used however, I'm starting to think you may have actually meant /mnt. I should have probably added /mnt and /media to be excluded from those. I'm going to take a second look at those lines to make sure adding /media and /mnt won't break anything, and if it doesn't, I'll update the script I uploaded. For now, if the script starts copying other mounted filesystems you don't want it to copy, stop the script with Ctrl+C, force it to uninstall (it should offer to do this as soon as you try to stop it), unmount the extra filesystems, and run the script again.

Edit: I updated the script to exclude /media and /mnt while it copies / to /var/squashfs. If this causes problems or breaks the script completely, let me know, but in theory it shouldn't do anything bad.

---

### Post by u_kapaley256 on 2011-01-28
Hey,

   Thanks for the script.Seems like it would be awesome.But doesn't seem to work.The system boots up fine and all, but while copying the file system to ram i see an error "expr : syntax error" at 0% but it continues and completes anyway.The filesystem (or image,whatever you call it) was reported by the script to be about 2 gb but my system runs with ram utilization at 1.2gb . I have a system with amd turion m500 2.1 ghz and 8gb ram(the main reason for this) running kubuntu 10.10

Do you know what might have gone wrong and how to correct it ?

Thanks.

---

### Post by terminator14 on 2011-01-29
> **u_kapaley256 said:**
> Hey,

   Thanks for the script.Seems like it would be awesome.But doesn't seem to work.The system boots up fine and all, but while copying the file system to ram i see an error "expr : syntax error" at 0% but it continues and completes anyway.The filesystem (or image,whatever you call it) was reported by the script to be about 2 gb but my system runs with ram utilization at 1.2gb . I have a system with amd turion m500 2.1 ghz and 8gb ram(the main reason for this) running kubuntu 10.10

Do you know what might have gone wrong and how to correct it ?

Thanks.

"expr : syntax error" appears on mine as well. Not sure what it means but it is not a problem. If you are not sure if it worked or not, run:

```
ls /
```

and look for a file either called "Original_OS" or "RAM_Session". If you see the "Original_OS" file when you were actually booting into the RAM Session, it did not work. If you see the "RAM_Session" file, then you are inside the RAM Session and you're good.

What are you using to determine your RAM utilization? Is it the System Monitor? Last I checked, it didn't accurately reflect how full RAM is in this situation. Use 'free -m' instead.

PS. I like how you compensate for not having spaces after your periods and commas almost everywhere by having one place (1.2gb . I) with a space before AND after your period... :P

Edit: Looked into expr. The error appears to be the result of an improperly formed expr command, as any bad expr command will give the same error. As for stopping it - first I'd need to find where it occurs. The rsync statement itself appears in /usr/share/initramfs-tools/scripts/live, but the expr command in question doesn't seem to come from there. The file has 3 expr statements, all of which I tried adding 2>/dev/null to. This failed. If the expr statement doesn't come from there, it could come from anywhere, which is hard to trace. I did a little grepping of /etc and /usr to find the most likely places it came from, and after a few tries to add 2>/dev/null to a few files, I gave up. The problem seems to mostly be aesthetic as the RAM Session still boots and works fine. Unless someone is curious enough to trace this error to its source, we can simply ignore it.

---

### Post by blizzards7 on 2011-02-01
Hey there terminator this looks awesome, thanks for the post. I hate to be a nuisance (mainly because I'm pretty much a beginner at this stuff), but I was hoping you could help me out with setting this up. My plan is to mix this with the backup iso made by remastersys to get have a custom Ubuntu based off 10.10 that runs entirely in the RAM. In addition I was planning on being able to boot this OS off my flash drive (being in the RAM would enable me to put the custom OS on multiple computers at the same time). Since I'm not all too good at the linux thing, I was hoping you could give me some basic instructions. Since my iso is customized with remastersys, there is no reason to save any data whatsoever (including documents because I can use Dropbox for that). So I have no reason to put the /home folder on a separate partition. Also there isn't really too much reason to enable any of the update things you mentioned so once it's made that's it. My main concern is quite simply how should I run this to set it up for putting it all on my flashdrive. Just some info: my iso is about 930M and the filesystem.squashfs file is about 900M so I know I'll need around 1.5G of RAM for it to run at a reasonable speed. Also, I've been using VirtualBox for most of my testing (I managed to find a way to set it up to boot of my flashdrive). I know this is quite similar to VMware which I noticed you mentioned you used, so if possible, explaining how to set it up all through VMware/VirtualBox would be awesome!

Thanks so much in advanced, I can imagine it must annoying having to deal with linux noobs like me ;)

- blizzards7

---

### Post by terminator14 on 2011-02-03
> **blizzards7 said:**
> Hey there terminator this looks awesome, thanks for the post. I hate to be a nuisance (mainly because I'm pretty much a beginner at this stuff), but I was hoping you could help me out with setting this up. My plan is to mix this with the backup iso made by remastersys to get have a custom Ubuntu based off 10.10 that runs entirely in the RAM. In addition I was planning on being able to boot this OS off my flash drive (being in the RAM would enable me to put the custom OS on multiple computers at the same time). Since I'm not all too good at the linux thing, I was hoping you could give me some basic instructions. Since my iso is customized with remastersys, there is no reason to save any data whatsoever (including documents because I can use Dropbox for that). So I have no reason to put the /home folder on a separate partition. Also there isn't really too much reason to enable any of the update things you mentioned so once it's made that's it. My main concern is quite simply how should I run this to set it up for putting it all on my flashdrive. Just some info: my iso is about 930M and the filesystem.squashfs file is about 900M so I know I'll need around 1.5G of RAM for it to run at a reasonable speed. Also, I've been using VirtualBox for most of my testing (I managed to find a way to set it up to boot of my flashdrive). I know this is quite similar to VMware which I noticed you mentioned you used, so if possible, explaining how to set it up all through VMware/VirtualBox would be awesome!

Thanks so much in advanced, I can imagine it must annoying having to deal with linux noobs like me ;)

- blizzards7

I haven't really used remastersys to know what it does or how it does it, and I'd give it a try if I could (since you're not the first person to ask how my script interacts with it), but I'm on the clock to get my CCNA, so time is something I don't have a lot of.

If I understand correctly, remastersys makes an iso of your filesystem that you can burn to a cd/dvd. If you don't need to have a way to get updates, and you don't need a /home mounted, then start with unpacking the iso.

What's inside of it? Where is your filesystem? Is it in a squashfs image? Or is it in one of the folders? If it's a squashfs image, great - copy that to your usb. If not, find / of your filesystem (the folder where /etc/ /var/ /home/ and other folders reside), and make a squashfs image out of it using:

```
sudo mksquashfs /path/to/root/folder/ /media/USB/filesystem.squashfs -noappend -always-use-fragments
```

Once you're done that, install grub onto the USB and configure it to copy the squashfs to RAM. You may find my original article, or the inside of my RAM_booster script useful to figure out how to do that.

You might also want to try this: there are plenty of guides online on how to customize a livecd - just google for them. Once you find a guide, follow it and edit the livecd to your liking. When finished with the guide and you have an iso of a bootable livecd again, try this: [http://ubuntuforums.org/showpost.php?p=10012643&postcount=1]("http://ubuntuforums.org/showpost.php?p=10012643&postcount=1") to make the livecd copy itself to RAM on boot.

---

### Post by EgoGratis on 2011-02-27
Just what i am looking for! This part i think i do understand:

1.) Install Ubuntu 10.10 to the USB key.
2.) Update, install drivers and everything you need and remove everything you don't need.
3.) Run RAM_booster.sh.
4.) Reboot and choose new option inside Grub2 menu.

This part i think i do not understand:

1.) How should i partition (size)  the USB (8GB) key. 
2.) / and /boot and /home should be made? Best file system would be?
3.) I want changes to be remembered. So /home should be made at the install time?
4.) Updating should be done by booting in to the original OS and running sudo ./RAM_booster.sh and then sudo rupdate -f is that procedure correct?!

---

### Post by terminator14 on 2011-04-06
> **EgoGratis said:**
> Just what i am looking for! This part i think i do understand:

1.) Install Ubuntu 10.10 to the USB key.
2.) Update, install drivers and everything you need and remove everything you don't need.
3.) Run RAM_booster.sh.
4.) Reboot and choose new option inside Grub2 menu.

This part i think i do not understand:

1.) How should i partition (size)  the USB (8GB) key. 
2.) / and /boot and /home should be made? Best file system would be?
3.) I want changes to be remembered. So /home should be made at the install time?
4.) Updating should be done by booting in to the original OS and running sudo ./RAM_booster.sh and then sudo rupdate -f is that procedure correct?!

Sorry I haven't checked this thread in a while - it's been a busy couple of months.

Anyway,

First 4 steps are right. Then:

1.) Make one big partition to mount /, and a smaller one to mount /home if you want to save it to the drive.
2.) / needs to be created yes. /boot can be on a separate partition but doesn't have to be. /home can also be on the same partition as /, but only if you don't want changes saved. If you do, make a separate partition for /home. As for the FS, I prefer ext4.
3.) You can either make /home at install time, or use gparted later. The script will help you make a new /home if you don't already have one.
4.) No. Updating is done from the RAM session. You don't have to boot back into the original OS to update. Also, the RAM_booster.sh script is only responsible for installing and removing the RAM session, it doesn't do the update. It creates another script - rupdate, to do the updating. All you have to do is run "sudo rupdate" from the RAM session and it should update everything. The longest part of the update process is not the update, but the recreation of the RAM session image. This is why it only gets recreated if it needs to be - if an update actually took place. If no update took place, it doesn't get recreated. The "sudo rupdate -f" command (the -f parameter specifically) tells the script to force the recreation of the RAM session image even if no update took place. This is only needed if you ran rchroot and made changes, or if you have another reason for wanting the RAM session image updated besides the update. If that's confusing, basically just use the "sudo rupdate" command to update.

PS. It's probably too late for this reply since you probably either figured it out, or gave up by now, but I'm writing it anyway just in case anyone else is unclear on these same points.

---

### Post by ytaews on 2011-05-27
I'm having an issue with connecting to the internet after running rchroot. I am running from a RAM session, but when I rchroot to edit it, I have no internet access from inside the terminal.

This is a pretty big issue because I can't apt-get, rupdate or make any changes requiring the internet. Same issue when I rchroot to the Original OS.

That's pretty much the extent of my debugging ability, not sure how much more detail I can provide sorry.

Other than that, the script is great, thanks. Been enjoying the speed for a while and while it could be something unrelated, my power consumption seems to have dropped by about 15% (probably due to fewer reads and writes from the HDD), which is always handy on a laptop.

---

### Post by Rebelli0us on 2011-05-27
Very nice, I'd love to get rid of the unused "swap" partition and have Linux use RAM more aggressively. But I'm not interested in typing arcane commands, it should be a simple option in System Administration.

---

### Post by terminator14 on 2011-05-27
> **Rebelli0us said:**
> Very nice, I'd love to get rid of the unused "swap" partition and have Linux use RAM more aggressively. But I'm not interested in typing arcane commands, it should be a simple option in System Administration.

One of the most awesome things about linux is that even if developers don't implement a feature into the OS that you would like to have, you have the tools necessary to implement that feature quickly and easily. The "arcane commands" used to do this are the best part of linux. At least imo.

As for swap, if you are talking disabling swap on a regular OS install to speed it up, all you would need to do (I would imagine) is disable swap. To do this temporarily, run:

```
sudo swapoff -a
```

This will first copy anything you have in swap to RAM, and then disable all swap devices. If you want swap not to be mounted on boot, you'll have to edit /etc/fstab. By edit, I mean it's as simple as commenting out the line that has the word "swap" in it.

The only step past that would be to have applications preloaded into RAM when you boot so that they load quickly when you run them as they won't have to copy from your HDD to ram (they will have already done that). For that, you would simply need something like the preload app:

```
sudo apt-get install preload
```

---

### Post by ytaews on 2011-05-28
> **ytaews said:**
> I'm having an issue with connecting to the internet after running rchroot. I am running from a RAM session, but when I rchroot to edit it, I have no internet access from inside the terminal.

This is a pretty big issue because I can't apt-get, rupdate or make any changes requiring the internet. Same issue when I rchroot to the Original OS.

Managed to fix this. I could still connect fine by IP address, so I edited /etc/hosts to add entries for the servers I needed.

Wondering if anyone knows what the cause of the problem may have been.

Thanks again for the script, terminator.

---

### Post by terminator14 on 2011-05-28
> **ytaews said:**
> Managed to fix this. I could still connect fine by IP address, so I edited /etc/hosts to add entries for the servers I needed.

Wondering if anyone knows what the cause of the problem may have been.

Thanks again for the script, terminator.

Sorry - I saw Rebelli0us' post (since it was the latest one yesterday), but I didn't notice your original post.

The script should copy everything necessary to have internet within the chroot. Mostly, this involves /etc/resolv.conf, which sounds like your problem.

/etc/hosts is kind of like a shortcut for dns resolving which is normally done by the server listed in /etc/resolv.conf. Make sure your /etc/resolv.conf exists in the chroot, and points to a dns server that is actually up and running. I think that the problem may be that in your case, the /etc/resolv.conf isn't being copied from your OS into the chroot environment for some reason.

That is of course assuming that you have no internet at all in the chroot environment, and you can't even ping google for example. If you have internet and only some servers that contained the updates couldn't be resolved, it may just be a problem with their dns and has nothing to do with your pc. In that case, /etc/hosts would be the best way to go.

---

### Post by dancer_69 on 2011-05-28
Did you plan to update the script for Ubuntu 11.04?
I want to give a try, but I haven't a 10.10 or previous version

---

### Post by terminator14 on 2011-05-28
> **dancer_69 said:**
> Did you plan to update the script for Ubuntu 11.04?
I want to give a try, but I haven't a 10.10 or previous version

I'm afraid that there are no plans to update the script to 11.04. This is for several reasons:

1. My new job has me working 11-14 hours per day (plus overtime), 7 days a week, and what little free time I have I mostly spend on studying for my CCNA, which was part of the deal for getting my job in the first place (I had so many months to get certified).

2. Right after I wrote the original script, I got an SSD which I now run both my Linux and my Windows from. The SSD's advantage is that it is more stable then the RAM script, since the OS was never designed by the developers to run from RAM, which sometimes causes problems that need to be debugged. Unfortunately, my time is a bit limited right now and debugging an OS isn't something I have time for these days - for now, I just need the OS to work. Not that the script gave me a lot of huge problems when I was using it, but there were a few that had to be overcome, which took some time.

Having an SSD and not needing the script also means I have no personal stake in the script's continued life, so unfortunately I am kind of less motivated to continue to support it. My only motivation right now is giving back to the ubuntu community, which has helped me a lot in the past.

3. I have a terrible memory, and by now have no idea how the script works or what it does. To modify it, I would need to spend some time re-reading all the code, and the comments to try to remember how I made it work.

4. I would also need some time to setup a testing environment in VMware again, which from what I remember was somewhat complex, involving over 100 GB of snapshots.

So that's mainly the reasons there are no plans to work on the script anytime soon. I might try to port it to 11.04 if I have some time in the future, but it's probably not going to happen for at least a couple of months.

---

### Post by ytaews on 2011-05-29
> **terminator14 said:**
> The script should copy everything necessary to have internet within the chroot. Mostly, this involves /etc/resolv.conf, which sounds like your problem.

/etc/hosts is kind of like a shortcut for dns resolving which is normally done by the server listed in /etc/resolv.conf. Make sure your /etc/resolv.conf exists in the chroot, and points to a dns server that is actually up and running. I think that the problem may be that in your case, the /etc/resolv.conf isn't being copied from your OS into the chroot environment for some reason.

Thanks, this was the problem. I had a look at your rchroot script and I think the issue may have been in the rchroot script, line 180 -

sudo cp /etc/resolv.conf $Orig_OS/$SquashFS/etc/resolve.conf - should be 'resolv.conf'

I've changed this and it seems to have fixed it.

---

### Post by terminator14 on 2011-05-29
> **ytaews said:**
> Thanks, this was the problem. I had a look at your rchroot script and I think the issue may have been in the rchroot script, line 180 -

sudo cp /etc/resolv.conf $Orig_OS/$SquashFS/etc/resolve.conf - should be 'resolv.conf'

I've changed this and it seems to have fixed it.

That is definitely a problem. Good find!

There were actually about 3 other places I made that same mistake, which I just corrected and reuploaded. Thanks!

---

### Post by XBMC old School on 2011-07-02
For simplicity, would anyone be interested in doing a youtube tut?

---

### Post by RJ12 on 2011-07-02
> **XBMC old School said:**
> For simplicity, would anyone be interested in doing a youtube tut?

This would be nice :)

---

### Post by terminator14 on 2011-07-03
> **XBMC old School said:**
> For simplicity, would anyone be interested in doing a youtube tut?

Sounds interesting. If anyone is up for it, then great! I would do it myself but I'm a bit short on time these days, and if I do get some time to work on this project again, I think I'd rather focus on updating it to work with the new Ubuntu first. If no one has made a youtube tutorial by then, maybe I will.

---

### Post by ytaews on 2011-08-01
Hi again,

Thanks for all the work you've put into the script, it's served me well over the past few months, but I've decided to go the whole way and buy an SSD, mainly for the reliability and faster boot times compared to this script.

I'm just wondering if there's a way to turn the squashfs image back to a / partition - I could reinstall ubuntu from scratch but it took me a long while to get everything set up properly (which I didn't do to the Original_OS) so this would be a lot quicker. If there's a guide for doing this that you could point me to, that'd be great, thanks.

---

### Post by terminator14 on 2011-08-02
> **ytaews said:**
> Hi again,

Thanks for all the work you've put into the script, it's served me well over the past few months, but I've decided to go the whole way and buy an SSD, mainly for the reliability and faster boot times compared to this script.

I'm just wondering if there's a way to turn the squashfs image back to a / partition - I could reinstall ubuntu from scratch but it took me a long while to get everything set up properly (which I didn't do to the Original_OS) so this would be a lot quicker. If there's a guide for doing this that you could point me to, that'd be great, thanks.

Glad to hear that you appreciate the effort I put in :)

Since this script only works on older versions of Ubuntu, I assume that's what you've been using with it up to this point. SSDs however benefit greatly from TRIM, which is a relatively new feature for linux, which means that you should probably install the newest Ubuntu in order for your SSD to work to its full potential. If I was you, I would format either way.

If you want to keep your files and settings, you would probably just need to copy your /home somewhere safe (Guide: [http://www.go2linux.org/how-to-move-home-directory-to-another-partition]("http://www.go2linux.org/how-to-move-home-directory-to-another-partition")), format and install the new ubuntu, and then copy the backup back to /home, or tell /etc/fstab to mount the /home partition. If your /home is on a separate partition already, it may just be as simple as reinstalling ubuntu and telling the new ubuntu which partition to mount as home, and all your files and settings should be copied over. You will just need to reinstall any software your had installed before.

If you want to copy the entire RAM Session to a real partition, you probably just need to copy your / to a new partition, (sudo cp -ax / /media/backup), and then install grub onto the new partition to make it bootable.

I hope that helps.

---

### Post by ytaews on 2011-08-02
Ah right, thanks. I had planned to leave /home on the old drive, and just have / on the new one. I'm running Maverick at the moment (I thought only Lucid was missing TRIM support?). Natty doesn't play nice with my hardware for one reason or another (more trouble than it was worth). So I guess I'll just wait until October before installing the SSD and see whether Oneiric works at all. Either way I'll just start fresh then.

Thanks again.

---

### Post by awdiwdwf on 2011-09-27
Is there any way to do this with an uncompressed filesystem? I know it's insignificant, but I like having my processor cycles available elsewhere. Also, I'm just generally curious, as all the examples I've seen thus far have been compressed. Is this because of general convenience, or because of limits of the system? Thanks for all your help.

---

### Post by terminator14 on 2011-09-27
> **awdiwdwf said:**
> Is there any way to do this with an uncompressed filesystem? I know it's insignificant, but I like having my processor cycles available elsewhere. Also, I'm just generally curious, as all the examples I've seen thus far have been compressed. Is this because of general convenience, or because of limits of the system? Thanks for all your help.

In my case, I did this for 2 reasons:

1) When I got the idea for this project, I had no clue where to start until I came across this post by capink:

[http://ubuntuforums.org/showthread.php?t=707230](http://ubuntuforums.org/showthread.php?t=707230)

and because a compressed image is what it dealt with, that's what I went with.

2) Fitting an entire OS inside of RAM, with room to spare for things RAM usually does requires quite a bit of RAM. A compressed filesystem results in something that is accessible to more people since it will be smaller, and require less RAM - far more people have 2GB or 4GB of RAM than 6 or 8GB.

I'm sure there must be a way to achieve the same result with an uncompressed filesystem, but what it is - I have no clue.

---

### Post by [deXter] on 2011-11-15
Has anyone tried this script on 11.04 or 11.10 yet? If so, does it work fine or are there any major issues?

---

### Post by terminator14 on 2011-11-17
> **'[deXter] said:**
> Has anyone tried this script on 11.04 or 11.10 yet? If so, does it work fine or are there any major issues?

I too am curious. I would try it myself but I've been pretty busy with work. If someone has the time to try this, please let us know the result.

---

### Post by xris_xcess on 2011-12-31
I have tested on a minimal install of 11.10 running xfce4.

When I try to install live-initramfs, I get the following:

update-initramfs: Generating /boot/initrd.img-3.0.0-12-generic
cp: cannot stat '/lib/libacl*': No such file or directory
E: /usr/share/initramfs-tools/hooks/live failed with return 1

followed by an dpkg error.

So... is it that since I did a minimal install im missing libacl? I tried installing it manually and aptitude says it's installed... but, if I look directly, it isn't there (or at least where the script is looking).

Anybody run into this? or knows how to fix it?

---

### Post by xris_xcess on 2011-12-31
Ahh... I see that 11.10 doesn't have a live-initramfs package...

What would be the equivalent, if any, then?

---

### Post by [deXter] on 2011-12-31
> **xris_xcess said:**
> Ahh... I see that 11.10 doesn't have a live-initramfs package...

What would be the equivalent, if any, then?


Try installing live-boot-initramfs-tools

---

### Post by xris_xcess on 2012-01-02
OK.

Tried to install live-boot-initramfs-tools... it seems to be the new name/replacement for initramfs-tools, but I still get en error from the /usr/share/initramfs/hooks/live.

I looked in the file and there are references to /lib/files*, but when I looked in the /lib folder they are not here, they are in the /lib/i386-linux-gnu folder!!! So I changed the references to the new folder, but I still get errors, although I'm no sure what because it only gives me and exit code 1 and no other info.

I'll keep diggin.

I see that on the original instructions there also is info to change a reference from /usr/bin/udevinfo to /sbin/udevadm, so i'll try that al well.

---

### Post by Krillezz on 2012-05-12
Is there a method to make this work in 12.04? :) 
sounds like something i would like to try or have. Something awesome would be if this was made an option somewhere, ex. System settings -> system -> load ubuntu to ram? y/n

---

### Post by jadtech on 2012-05-12
this  apparently didnt work several years ago was causing people all kinds of issues what makes you think it will work now ??

---

### Post by terminator14 on 2012-05-12
> **jadtech said:**
> this  apparently didnt work several years ago was causing people all kinds of issues what makes you think it will work now ??

Who exactly were these people who had "all kinds of issues" with this? There are multiple posts here in the comments of people using this script successfully... And while it is true that some people had trouble initially (which was to be expected of a script this large and [relatively] complex), any bugs that were commented about were fixed, and the script reuploaded. If you personally had trouble with the script, you should have commented about it, as I did my best to answer each person's comments individually, including answering your highly rude comment today, almost 2 years after I wrote the script.

Oh and FYI, "." <-- this is a period. It goes at the end of a "[sentence]("http://en.wikipedia.org/wiki/Sentence_%28linguistics%29")". "?" <-- this is a question mark. It follows a question, but has no space between it and the last word of the sentense. Oh and there's only one that is required - two question marks don't make it a better question...

> **Krillezz said:**
> Is there a method to make this work in 12.04? :) 
sounds like something i would like to try or have. Something awesome would be if this was made an option somewhere, ex. System settings -> system -> load ubuntu to ram? y/n

I have kind of stopped supporting the script, but have been thinking about at least giving it a try on the new OS to see if it at least works, since no one else has commented about trying it recently.

As for the built in option - I'm afraid that's beyond my expertise, and I highly doubt Canonical would be interested in implementing something like this unless it was highly refined and dead simple, and even then, Canonical would still probably pass.

I'll post back if I have the time to give it a try on the new versions of Ubuntu.

---

### Post by terminator14 on 2012-05-12
> **xris_xcess said:**
> OK.

Tried to install live-boot-initramfs-tools... it seems to be the new name/replacement for initramfs-tools, but I still get en error from the /usr/share/initramfs/hooks/live.

I looked in the file and there are references to /lib/files*, but when I looked in the /lib folder they are not here, they are in the /lib/i386-linux-gnu folder!!! So I changed the references to the new folder, but I still get errors, although I'm no sure what because it only gives me and exit code 1 and no other info.

I'll keep diggin.

I see that on the original instructions there also is info to change a reference from /usr/bin/udevinfo to /sbin/udevadm, so i'll try that al well.

Just noticed that I never replied to your comments. I didn't notice it till now - for some reason I didn't get an email about your post, despite being subscribed to get emails instantly if anyone posts. Sorry.

As for your problem, I'm afraid I've never tried to run it with a minimal install. If I get around to trying it with the new version of Ubuntu, I might update the script, and maybe that'll help you run it in the minimal install as well, if you're still interested in doing that.

---

### Post by terminator14 on 2012-05-13
I recently had some time to kill, and with this script fresh in my mind from just having replied to a post, I decided to give it a quick try on Ubuntu 12.04. There were a few minor alterations that were required, but overall it practically ran exactly as originally intended. I uploaded the updated script, but left the old one in place just in case you still wanted to run it on Ubuntu 10.04/10.10 for some reason - well, that and I like the fact that my script has a statistic attached to it that says it's been downloaded almost 250 times, which gets reset if I upload a new version. :)

---

### Post by gumbomumbo on 2012-06-12
Hey, great idea with the script, I'm running into a a problem when trying to install it though (lucid)

[spoiler]
Would you like a cron job to be added to run the update script at midnight
every day in the RAM Session? In order to take advantage of these updates,
you would need to reboot after an update has been performed. [Y/n]

Your choice: n

You chose no.

Installing essential packages:
Running apt-get update...
Installing squashfs-tools...
Installing live-initramfs...
live-initramfs was not found in the repo. Attempting to download .deb
Installing dependencies for live-initramfs: busybox, user-setup...
Downloading and installing live-initramfs .deb...
live-initramfs failed to install. You'll have to download and install it
manually... Try: [https://launchpad.net/ubuntu/maverick/+package/live-initramfs](https://launchpad.net/ubuntu/maverick/+package/live-initramfs)
[/spoiler]

sudo apt-get install live-initramfs gives me:
[spoiler]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  loop-aes-utils curlftpfs genext2fs httpfs2 mtd-tools
The following NEW packages will be installed:
  live-initramfs
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/99.4kB of archives.
After this operation, 500kB of additional disk space will be used.
Unpacking live-initramfs (from .../live-initramfs_1.173.1-1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/live-initramfs_1.173.1-1_all.deb (--unpack):
 trying to overwrite '/usr/share/initramfs-tools/conf.d/compcache', which is also in package casper 0:1.236.3
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-19-generic
Processing triggers for ureadahead ...
Errors were encountered while processing:
 /var/cache/apt/archives/live-initramfs_1.173.1-1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/spoiler]

When trying to manually install it via the .dep from the internet page I get:
[spoiler]
(Reading database ... 90803 files and directories currently installed.)
Unpacking live-initramfs (from .../live-initramfs_1.173.1-1_all.deb) ...
dpkg: error processing /home/asdfa/live-initramfs_1.173.1-1_all.deb (--install)
:
trying to overwrite '/usr/share/initramfs-tools/conf.d/compcache', which is also in package casper 0:1.236.3
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-19-generic
Processing triggers for ureadahead ...
Errors were encountered while processing:
 /home/asdfa/live-initramfs_1.173.1-1_all.deb
[/spoiler]

Can you think of a way to fix this?

---

### Post by gumbomumbo on 2012-06-12
**Hey, great idea with the script, I'm running into a a problem when trying to install it though (lucid)**


Would you like a cron job to be added to run the update script at midnight
every day in the RAM Session? In order to take advantage of these updates,
you would need to reboot after an update has been performed. [Y/n]

Your choice: n

You chose no.

Installing essential packages:
Running apt-get update...
Installing squashfs-tools...
Installing live-initramfs...
live-initramfs was not found in the repo. Attempting to download .deb
Installing dependencies for live-initramfs: busybox, user-setup...
Downloading and installing live-initramfs .deb...
live-initramfs failed to install. You'll have to download and install it
manually... Try: [https://launchpad.net/ubuntu/maverick/+package/live-initramfs](https://launchpad.net/ubuntu/maverick/+package/live-initramfs)


**sudo apt-get install live-initramfs gives me:**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  loop-aes-utils curlftpfs genext2fs httpfs2 mtd-tools
The following NEW packages will be installed:
  live-initramfs
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/99.4kB of archives.
After this operation, 500kB of additional disk space will be used.
Unpacking live-initramfs (from .../live-initramfs_1.173.1-1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/live-initramfs_1.173.1-1_all.deb (--unpack):
 trying to overwrite '/usr/share/initramfs-tools/conf.d/compcache', which is also in package casper 0:1.236.3
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-19-generic
Processing triggers for ureadahead ...
Errors were encountered while processing:
 /var/cache/apt/archives/live-initramfs_1.173.1-1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


**When trying to manually install it via the .dep from the internet page I get:**
(Reading database ... 90803 files and directories currently installed.)
Unpacking live-initramfs (from .../live-initramfs_1.173.1-1_all.deb) ...
dpkg: error processing /home/asdfa/live-initramfs_1.173.1-1_all.deb (--install)
:
trying to overwrite '/usr/share/initramfs-tools/conf.d/compcache', which is also in package casper 0:1.236.3
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-19-generic
Processing triggers for ureadahead ...
Errors were encountered while processing:
 /home/asdfa/live-initramfs_1.173.1-1_all.deb

**Can you think of a way to fix this?**

---

### Post by terminator14 on 2012-06-12
> **gumbomumbo said:**
> 
Can you think of a way to fix this?

I'll install lucid in a VM later tonight and see if I can reproduce the error.

---

### Post by terminator14 on 2012-06-12
> **gumbomumbo said:**
> Can you think of a way to fix this?

Tried it using ubuntu-10.04.4-desktop-amd64.iso. My steps:

1. Installed the OS
2. Ran the script

I touched nothing else - not settings, not repos, not anything. As you can see, the repos had no problems installing the package. Are you using x86 or amd64?

Your errors also mention ureadahead. I'm not sure if this will help (especially since I can't reproduce the error) but try uninstalling it, and any other software you may have installed that deals with copying stuff to RAM at boot (other than what linux naturally does).

---

### Post by gumbomumbo on 2012-06-13
I have an x86. I'll try getting rid of ureadahead, thanks for the try ;)

---

### Post by zsasha2 on 2012-06-21
Hi everybody,

nice script, indeed, my thanks to the author!

I'm looking for some distro to build my home NAS.
The key point I am after is to be able to put [all] my hdd down to stand by mode while nobody use them (like during the night etc).
I have found however that "normal" ubuntu wakes up at least "/" hdd (to write logs? and do other stuff) regularly as well as another hdds. 
It is not what I wanted so I thought this script could do the trick - load whole system in memory so everything would work without accessing HDD.

(I do know there are some distro available that were initially modified to do that trick, but I also need couple of programs to be installed and I could not figure out how to do that for those distros).

Sorry for being long, just a question for author:

**can I do something to save RAM OS back to disk for the next boot?**
**in other words, can I save state of the RAM OS to survive rebooting?**

Like a script that being launched before shutting down would save/copy RAM back to Original OS?

It is how SLAX works by the way. When you tape "poweroff" it calls some script that saves everything that have been changed back to disk so next time when you boot your OS you have everything restored **AND **everything works from RAM as well.

Any advice would be much appreciated.
Thanks.

---

### Post by terminator14 on 2012-06-25
> **zsasha2 said:**
> Hi everybody,

nice script, indeed, my thanks to the author!

I'm looking for some distro to build my home NAS.
The key point I am after is to be able to put [all] my hdd down to stand by mode while nobody use them (like during the night etc).
I have found however that "normal" ubuntu wakes up at least "/" hdd (to write logs? and do other stuff) regularly as well as another hdds. 
It is not what I wanted so I thought this script could do the trick - load whole system in memory so everything would work without accessing HDD.

(I do know there are some distro available that were initially modified to do that trick, but I also need couple of programs to be installed and I could not figure out how to do that for those distros).

Sorry for being long, just a question for author:

**can I do something to save RAM OS back to disk for the next boot?**
**in other words, can I save state of the RAM OS to survive rebooting?**

Like a script that being launched before shutting down would save/copy RAM back to Original OS?

It is how SLAX works by the way. When you tape "poweroff" it calls some script that saves everything that have been changed back to disk so next time when you boot your OS you have everything restored **AND **everything works from RAM as well.

Any advice would be much appreciated.
Thanks.

Yes, this is what the script is designed to do - save any software you installed and any files you saved back to the HDD. This is not done when you reboot. It only does this when you tell it to. You can however easily alias the reboot or poweroff commands to save everything before actually rebooting or powering off.

On the one hand, this script, if used correctly, would actually be very useful in a NAS situation since all you would need is to configure it once to mount the HDDs, use NFS/SMB shares, and configure the users, and it would rarely need to be reconfigured again (as a home NAS anyway). On the other hand, the speed benefits of the OS copying itself to RAM on boot for a NAS become far less relevant than on a desktop.

As for your specific situation, I'm not sure how well this script would work for you. In theory, it should never write to the HDD during normal operations, but you may be better off using a distro specifically designed for running on a NAS, such as freeNAS, or, if you have the money, something like the QNAP lineup of products that comes with it's own custom version of linux as it's firmware. I'm pretty sure that both have an option to let the HDDs fall asleep if they are not being used, and freeNAS has the option to copy itself to ram as well (if I'm not mistaken).

---

### Post by zsasha2 on 2012-06-25
> **terminator14 said:**
> Yes, this is what the script is designed to do - save any software you installed and any files you saved back to the HDD. This is not done when you reboot. It only does this when you tell it to. You can however easily alias the reboot or poweroff commands to save everything before actually rebooting or powering off.
Oh, that's good.
Could you give me an example? What the name of the script and its cmd parameters? 
I mean the script that saves RAM back to HDD?
Where does it save its state? File or partition or something else? I think I would not want to save everything back to flash, because it could cause flash degradation so HDD would be an ideal in my case.

Do you have any manual somewhere?

> **terminator14 said:**
> On the one hand, this script, if used correctly, would actually be very useful in a NAS situation since all you would need is to configure it once to mount the HDDs, use NFS/SMB shares, and configure the users, and it would rarely need to be reconfigured again (as a home NAS anyway). On the other hand, the speed benefits of the OS copying itself to RAM on boot for a NAS become far less relevant than on a desktop.
The main benefit for me is not speed but to let HDD sleep while no one access them.
I think **unRAID **does pretty much what I want but it is quite expensive (price of a new big HDD!) and can't easily be customized.

> **terminator14 said:**
> As for your specific situation, I'm not sure how well this script would work for you. In theory, it should never write to the HDD during normal operations, but you may be better off using a distro specifically designed for running on a NAS, such as freeNAS, or, if you have the money, something like the QNAP lineup of products that comes with it's own custom version of linux as it's firmware. I'm pretty sure that both have an option to let the HDDs fall asleep if they are not being used, and freeNAS has the option to copy itself to ram as well (if I'm not mistaken).
The whole idea was to boot everything into RAM and that's it.
Also FreeNAS, being excellent NAS-OS, has some weak points in my opinion - it basically uses Raid5-like approach so it wakes up all disks just to read some small file.
Also the latest version requires 6 GIG of RAM - it is ridiculous! 

I want to use "**Greyhole**" to do disk pooling and "**SnapRAID**" to do parity calculation. But all data remains intact so if the system crashes  everything (apart from crashed disk of course) could be easily recovered by just plugging the disks into another system and remounting them so no hassle with Raid5 or anything like that.

---

### Post by tenmoi on 2012-06-26
Thank you a lot terminator14,

I've beeng searching for a how-to for quite sometime now. I'm over the moon I've come across this wonderful script. I'm running the script now and hope it'll work fine. 
Thank you.

---

### Post by tenmoi on 2012-06-26
Everything is fine except that the grub entry created by your script will not work.
These are the lines my machine displayed:
> 
error: no such device: ubuntu
error: no such device: ubuntu
error: no such disk
error: you need to load the kernel first

You hit 'enter' and turn back to the grub menu.

I had to add my own grub entry as follows

I opened:
/etc/grub.d/40_custom
and added:

> menuentry 'Ubuntu to Ram' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 33624d05-2f07-4f4d-b7f4-729f6691e7c9
	linux	/boot/vmlinuz-3.2.0-25-generic root=UUID=33624d05-2f07-4f4d-b7f4-729f6691e7c9 boot=live toram=filesystem.squashfs username=myusername noautologin quickreboot apparmor=0 security="" ro quiet 
	initrd	/boot/initrd.img-3.2.0-25-generic
}

Now I am typing on ubuntu to RAM.

So, please update your script for the grub entry for ubuntu 12.04

P.S I'm running ubuntu precise x64 on Dell R N5110, nvidia 525M.

Thank you.

---

### Post by terminator14 on 2012-06-26
> **zsasha2 said:**
> I think I would not want to save everything back to flash, because it could cause flash degradation so HDD would be an ideal in my case.

According to [http://www.allmemorycards.com/glossary/reliability.htm](http://www.allmemorycards.com/glossary/reliability.htm), 

> **http://www.allmemorycards.com/glossary/reliability.htm]A Multi-Level Cell memory card has in general at least 10 000 write and erase cycles.[/QUOTE]

which is the low end. SLC has 10 times that many.

[QUOTE=http://www.allmemorycards.com/glossary/reliability.htm]10 000 write and erase cycles can also be translated to that you can write and erase the entire content of the memory card once per day for 27 years.[/QUOTE]

Seeing as you will only be writing to the flash drive when you are shutting down, if you were to shut down the NAS 10 times per day, everyday, you might be in trouble in 3 years. For reference, I reboot either one of my 2 NAS's roughly once every 2-3 months. Even if, after 3 years, you begin to experience problems with your flash drive's reliability, I doubt you'll have a problem acquiring a new one that, by then, will be 10x the capacity, 10x the speed, and worth $20. I've been running freeNAS with 6x2TB drives off a USB drive for over a year without any problems.

[QUOTE=zsasha2 said:**
> Do you have any manual somewhere?

The manual is:

1. The first post on the first page of this thread. In order to download the script you literally have to scroll past this.
2. The script itself, as it explains every step of what it's doing
3. The heavily commented source code
4. My previous thread outlining the steps the script uses that the first post of this thread links to
5. The original capink's thread that the above thread links to

I have spent a considerable amount of time writing these (excluding capink's thread of course). If you aren't sure about how the script works - please start by reading them, or at the very least, #1, which answers your question.

> **zsasha2 said:**
> 
Also the latest version requires 6 GIG of RAM - it is ridiculous! 

I believe you are referring to this information here:

> **http://doc.freenas.org/index.php/Hardware_Recommendations]The best way to get the most out of your FreeNAS&#8482 said:**
> 

which clearly states that this is a filesystem requirement, and has nothing to do with the freeNAS OS itself. It also says that freeNAS offers an alternative filesystem if you don't have the RAM needed for ZFS.

[QUOTE=zsasha2;12054291] I want to use "**Greyhole**" to do disk pooling and "**SnapRAID**" to do parity calculation. But all data remains intact so if the system crashes  everything (apart from crashed disk of course) could be easily recovered by just plugging the disks into another system and remounting them so no hassle with Raid5 or anything like that.

Not sure if freeNAS supports this, but if this is any important feature, I doubt they would leave it out. Do a search and I'm sure you'll find freeNAS is either capable of this, or has an alternative that works just as well.

---

### Post by terminator14 on 2012-06-26
> **tenmoi said:**
> Everything is fine except that the grub entry created by your script will not work.
These are the lines my machine displayed:

You hit 'enter' and turn back to the grub menu.

I had to add my own grub entry as follows

I opened:
/etc/grub.d/40_custom
and added:


Now I am typing on ubuntu to RAM.

So, please update your script for the grub entry for ubuntu 12.04

P.S I'm running ubuntu precise x64 on Dell R N5110, nvidia 525M.

Thank you.

I'm glad it worked out in the end. Thanks for the information - I will download ubuntu precise x64 as soon as I get a chance and give it a try in a VM (unfortunately, I have no access to a Dell R N5110 or an nvidia 525M so a VM is the best I can do). I'll see if I can reproduce the problem. If I run into it as well, I'll be glad that you already have a working grub file for me to work with - thanks for that as well.

Has anyone else run into this?

---

### Post by tenmoi on 2012-06-29
Oh, I didn't read carefully

---

### Post by terminator14 on 2012-06-29
> **tenmoi said:**
> Could you please modify the script so that we can provide the 'update' parameter in order to update only the changed files in /var/squash. Right now the only way to update your squash file is by removing everything and copying everything back again, which is very inefficient and may unnecessarily harm your hard disk.

If you were talking about modifying the SquashFS image after an update rather than recreating it, then it is a great idea, and something I looked into back when I wrote the script, but unfortunately:

[QUOTE=http://en.wikipedia.org/wiki/SquashFS]SquashFS is a compressed read-only file system for Linux.[/QUOTE]

SquashFS images were never designed to be written to. There is a way to do it using UnionFS, which is what a lot of live CDs used to do (and maybe still do), but it seemed long and complicated, so I went with the simpler solution.

The script does not erase your OS during an update - only the image. The OS is always kept in /var/squashfs and is never erased (unless you choose to uninstall the script). The worst that can happen is that your computer crashes (for any reason) after the image has been erased but before the new image has finished being created. This will make the ram session unbootable (but still existent). To solve this, you would need to boot back into your original OS and give the mksquashfs command to recreate the image. Nothing would be lost. The only problem with this is the inconvenience of having to manually recreate the image.

Something I can do, that I just realized, is to decrease the time window this could occur by not deleting the squashfs image being used until the new one is created. This would decrease the window from the time it takes your computer to create the squashfs image (several minutes) to the time it takes to delete and rename a file (fractions of a second).

I will try to make this happen next time I get a chance.

---

### Post by terminator14 on 2012-06-30
> **terminator14 said:**
> Something I can do, that I just realized, is to decrease the time window this could occur by not deleting the squashfs image being used until the new one is created. This would decrease the window from the time it takes your computer to create the squashfs image (several minutes) to the time it takes to delete and rename a file (fractions of a second).

I made this change, tested it, and it works great, but according to the new ubuntu forums rules, I can't modify my original post anymore in order to update the script - I have to move the entire post to a wiki page. I'll look into how to do this sometime, but for now, here's the updated script.

The only change is that now, the filesystem.squashfs file is only deleted during an update once the new image is ready. With the old script, if a power failure happened exactly when the rupdate script was generating a new image, the ram session would become upbootable, forcing the user to boot back into the original OS and recreate the squashfs image by hand. No data would be lost, but this would be very inconvenient. Now, if a power failure occurs during the creation of the squashfs image, you will boot from the old squashfs image next time your computer starts. In order to build the new image again, you would simply run "sudo rupdate -f".

If you already have the ram session running and don't want to uninstall it just to install it with the new script, all you need to do to patch your ram session is to mount or boot into your original OS, edit the /var/squashfs/usr/sbin/rupdate file, and change the lines that read:

```
if [[ "$NICE" == "true" ]]
then
	sudo chroot $Orig_OS/ /bin/bash -c "nice -n 19 mksquashfs /$SquashFS /live/filesystem.squashfs -noappend -always-use-fragments"
else
	sudo chroot $Orig_OS/ /bin/bash -c "mksquashfs /$SquashFS /live/filesystem.squashfs -noappend -always-use-fragments"
fi
```

to now read 

```
if [[ "$NICE" == "true" ]]
then
	sudo chroot $Orig_OS/ /bin/bash -c "nice -n 19 mksquashfs /$SquashFS /live/filesystem.squashfs[COLOR="Sienna"].new[/COLOR] -noappend -always-use-fragments"
else
	sudo chroot $Orig_OS/ /bin/bash -c "mksquashfs /$SquashFS /live/filesystem.squashfs[COLOR="Sienna"].new[/COLOR] -noappend -always-use-fragments"
fi

[COLOR="Sienna"]#Enable the new squashfs image
sudo chroot $Orig_OS/ /bin/bash -c "rm /live/filesystem.squashfs 2>/dev/null"
sudo chroot $Orig_OS/ /bin/bash -c "mv /live/filesystem.squashfs.new /live/filesystem.squashfs"[/COLOR]
```

Note: look carefully at the code above - it is more than just copy-pasting the last 3 lines.

Once you do this, recreate the image with "sudo rupdate -f" and reboot.

---

### Post by tenmoi on 2012-07-01
Hi terminatior14,

Does this new script fix the boot error I reported earlier?

My RAM session is running fine so I haven't tried your latest script. I am just asking for my English-illiterate countrymen and save them the hard work of manually modifying the grub.cfg file.

Thank you.

---

### Post by terminator14 on 2012-07-01
> **tenmoi said:**
> Hi terminatior14,

Does this new script fix the boot error I reported earlier?

My RAM session is running fine so I haven't tried your latest script. I am just asking for my English-illiterate countrymen and save them the hard work of manually modifying the grub.cfg file.

Thank you.

Sorry - I was going to mention something about that in my last reply but I ran into the not-being-able-to-upload-the-new-script-without-converting-everything-to-a-wiki problem and forgot.

Basically, I installed x64 precise in a VM onto a single partition and ran the script, and had no grub problems with it. I've also seen no reports of any grub problems with the script in the comments. The problem you ran into was most likely caused by the specific configuration of either your partitions, or of grub itself. What was the arrangement of your partitions? Did you use a separate partition for /home? This information would be really helpful in recreating the problem, without which it's hard for me to address it.

By the way, you mentioned modifying the grub.cfg file - was that just you remembering the olden, pre GRUB 2 days, or did you actually replace your grub 2 with grub? The default is grub 2, which is what the script was designed to modify. If you have old grub instead, that would definitely have the potential for causing the problem you described. 

Since I haven't been able to reproduce it, the new update does not have a fix - it only has like 2 lines changed and 3 lines added that address a different potential problem.

---

### Post by tenmoi on 2012-07-01
Hi,

I installed the whole system on '/' on one partition and I didn't change many default values when I installed Ubuntu. THere's no swap partition. The mount point is '/'. The file system is ext4.
As I dualboot it with Windows7, grub is installed on an extended partition (sda5 in my case). The main system boot manager is EasyBCD.

```
$grub-install -v
grub-install (GRUB) 1.99-21ubuntu3.1
```

Thank you.

---

### Post by terminator14 on 2012-07-06
> **tenmoi said:**
> Hi,

I installed the whole system on '/' on one partition and I didn't change many default values when I installed Ubuntu. THere's no swap partition. The mount point is '/'. The file system is ext4.
As I dualboot it with Windows7, grub is installed on an extended partition (sda5 in my case). The main system boot manager is EasyBCD.

```
$grub-install -v
grub-install (GRUB) 1.99-21ubuntu3.1
```

Thank you.

Your grub version looks good, but I've never heard of EasyBCD. Why do you have it and grub? What's is it configured to do? 

I've installed Windows 7 onto the first partition and Ubuntu precise X64 onto an extended partition, with no swap space in a VM. I've also installed EasyBCD in Windows.

In order to attempt to replicate your setup, all I need now is to configure EasyBCD the same way yours is, and run the script on Ubuntu to see if I run into the same problem.

---

### Post by love &lt;3 on 2012-07-07
I've had failed attempts, and plenty of religious debates on IRC over this script. I just couldn't make it work. Thank you!!

---

### Post by terminator14 on 2012-07-07
> **love <3 said:**
> I've had failed attempts, and plenty of religious debates on IRC over this script. I just couldn't make it work. Thank you!!

What were the problems? What were you running it on?

---

### Post by hakovala on 2012-07-08
Hello to all.. 

I had similar problem with the grub not finding correct partitions to boot the ram session. 
The problem was that i had assigned labels to the partions and the script used those labels instead of uuids as supposed to.

To fix the problem I changed the lines that set ROOT_UUID and BOOT_UUID from:
```

sudo blkid -o value $ROOT_DEV | head -1
sudo blkid -o value $BOOT_DEV | head -1

```
to:
```

sudo blkid -o value -s UUID $ROOT_DEV
sudo blkid -o value -s UUID $BOOT_DEV

```

That should get uuid even if label is set or not.
I haven't tested without the labels, though.

Nice script by the way. I was in process of making something similar to use with my nas system before I found this script.
The main point for me with this script is that i can have non-persistent system to play with and to save my all ready worn out hdds of unnecessary read/writes.

---

### Post by love &lt;3 on 2012-07-08
I meant I'd tried to build my own version of this, and attempted its results by many means, prior to you having done so successfully.

Now, I ran it and it worked however, my SSD (Original OS) is more responsive due to squashfs compression causing a latency hit, throughput obviously is great, and my install is only 712mb it still starts in under 15sec. Can you so kindly make or tell me how to make it use something more efficient performance wise, for its filesystem?

---

### Post by tenmoi on 2012-07-09
> **terminator14 said:**
> Your grub version looks good, but I've never heard of EasyBCD. Why do you have it and grub? What's is it configured to do? 

I've installed Windows 7 onto the first partition and Ubuntu precise X64 onto an extended partition, with no swap space in a VM. I've also installed EasyBCD in Windows.

In order to attempt to replicate your setup, all I need now is to configure EasyBCD the same way yours is, and run the script on Ubuntu to see if I run into the same problem.

I use easyBCD because it's easy:p to configure. And I reinstall windows more often than I do Ubuntu.

---

### Post by terminator14 on 2012-07-09
> **hakovala said:**
> Hello to all.. 

I had similar problem with the grub not finding correct partitions to boot the ram session. 
The problem was that i had assigned labels to the partions and the script used those labels instead of uuids as supposed to.

To fix the problem I changed the lines that set ROOT_UUID and BOOT_UUID from:
```

sudo blkid -o value $ROOT_DEV | head -1
sudo blkid -o value $BOOT_DEV | head -1

```
to:
```

sudo blkid -o value -s UUID $ROOT_DEV
sudo blkid -o value -s UUID $BOOT_DEV

```

That should get uuid even if label is set or not.
I haven't tested without the labels, though.

Nice script by the way. I was in process of making something similar to use with my nas system before I found this script.
The main point for me with this script is that i can have non-persistent system to play with and to save my all ready worn out hdds of unnecessary read/writes.

That is very interesting. Maybe that is the same problem tenmoi ran into earlier. In any case, thanks for providing the helpful information - that should definately make it easy to test and fix (especially since you provided the fix :p) when I have some time to give it a try.

> **tenmoi said:**
> I use easyBCD because it's easy:p to configure. And I reinstall windows more often than I do Ubuntu.

Oh  - now it makes sense. I'll play around with it a bit more, but it is more likely that your problem is the same as what hakovala had noticed, since, from the sound of it, all it would take is for a partition to have a label. Do your partitions have labels?


> **love <3 said:**
> I meant I'd tried to build my own version of this, and attempted its results by many means, prior to you having done so successfully.

Now, I ran it and it worked however, my SSD (Original OS) is more responsive due to squashfs compression causing a latency hit, throughput obviously is great, and my install is only 712mb it still starts in under 15sec. Can you so kindly make or tell me how to make it use something more efficient performance wise, for its filesystem?

I'm afraid I can't help you there. When I got my SSD, I started using it instead of the script because the effort it took to look after my RAM based OS was not worth the minor (if any) speed advantage over running the OS from an SSD. While in theory, the speed difference between an SSD and RAM is great, in practice, the fact that decompression on the squashfs slows things down (depending on your CPU of course) and the fact that both methods are incredibly fast, making it hard to see a clear winner without benchmarks, makes the difference more or less negligible. 

Even in theory - I'm not sure what FS you could use over squashfs to make it more efficient.

---

### Post by tenmoi on 2012-07-10
> **terminator14 said:**
> 

Oh  - now it makes sense. I'll play around with it a bit more, but it is more likely that your problem is the same as what hakovala had noticed, since, from the sound of it, all it would take is for a partition to have a label. Do your partitions have labels?



I had never labelled the partition until I installed 12.04. Here's for your info, anyway.

> /dev/sda5: LABEL="ubuntu" UUID="33624d05-2f07-4f4d-b7f4-729f6691e7c9" TYPE="ext4" 

Thank you for your time.

---

### Post by terminator14 on 2012-07-10
> **tenmoi said:**
> I had never labelled the partition until I installed 12.04. Here's for your info, anyway.



Thank you for your time.

Definately sounds like that could be the problem - my script might be handling labeled partitions poorly when it comes time to creating the grub menu. If so, and if it does this consistently, that's a pretty big problem since I would imagine it's not that uncommon to label a partition, given how easy it is to do. I won't know for sure until it stops being so busy at work and I have a chance to try it out, which unfortunately might not be for a couple of days.

---

### Post by tenmoi on 2012-07-13
I edited the sh script according to post #111 and everything is fine now.

Thank you all.

---

### Post by terminator14 on 2012-07-13
> **tenmoi said:**
> I edited the sh script according to post #111 and everything is fine now.

Thank you all.

Thanks for letting me know - I'll update it as soon as I have some time. Unfortunately, it's still crazy busy at work, and I still need to figure out how to transfer the script to a wiki since I can't update the original post anymore. Hopefully I'll get around to it soon.

---

### Post by terminator14 on 2012-07-29
I just tested my script on an OS with a labeled partition, and it turns out that it did have a problem creating the grub menu. hakovala's advice was exactly right, and the fix ended up being quick, simple, and effective. Thanks hakovala!

---

### Post by Andrew James Collett on 2012-11-11
Hello there!

So reading through this has been incredibly interesting. Could you advise on whether or not it'd work with Ubuntu 12.10? I presume not, considering you have a different version for different Ubuntu Versions. What would need to be done to make the ubuntu 12.04 script work with 12.10? 

Really liking this idea. I can see a bright future for my PC. 
hah:-)

---

### Post by terminator14 on 2012-11-11
> **Andrew James Collett said:**
> Hello there!

So reading through this has been incredibly interesting. Could you advise on whether or not it'd work with Ubuntu 12.10? I presume not, considering you have a different version for different Ubuntu Versions. What would need to be done to make the ubuntu 12.04 script work with 12.10? 

Really liking this idea. I can see a bright future for my PC. 
hah:-)

It's hard to say without trying it, which I have not done yet, but if you're feeling adventurous, you can give it a shot. It should either work or tell you the problem. If you do try it, I highly recommend doing so in a virtual machine first so that you know if the script does anything unexpected. 

I might try it myself if I get some time in the next couple of days, and post an updated script. Even if it requires no changes, I will at the very least update the warning the 12.04 script is sure to display when you run it on 12.10.

---

### Post by Andrew James Collett on 2012-11-12
Okay so i tried it, but got this error 

```
var/mail/
var/metrics/
var/opt/
var/spool/
var/spool/mail -> ../mail
var/spool/anacron/
var/spool/anacron/cron.daily
var/spool/anacron/cron.monthly
var/spool/anacron/cron.weekly
var/spool/cron/
var/spool/cron/atjobs/
var/spool/cron/atjobs/.SEQ
var/spool/cron/atspool/
var/spool/cron/crontabs/
var/spool/cups/
var/spool/cups/tmp/
var/spool/libreoffice/
var/spool/libreoffice/uno_packages/
var/spool/libreoffice/uno_packages/cache/
var/spool/lintian/
var/spool/plymouth/
var/spool/rsyslog/
var/tmp/

sent 5561793113 bytes  received 2380988 bytes  8335841.35 bytes/sec
total size is 5551454554  speedup is 1.00
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1070) [sender=3.0.9]

Copying filesystem failed.

Exiting...
```

not too sure what that means, other than it failed. Also, would i be right to presume that's over 5 Gigs in size? I got rid of stuff in my home folder, but I have a lot installed, so its possible.


Im installing VM at the moment, VirtualBox, and will see how it works on a fresh install. is that what you meant?

---

### Post by terminator14 on 2012-11-12
> **Andrew James Collett said:**
> Okay so i tried it, but got this error 

```
var/mail/
var/metrics/
var/opt/
var/spool/
var/spool/mail -> ../mail
var/spool/anacron/
var/spool/anacron/cron.daily
var/spool/anacron/cron.monthly
var/spool/anacron/cron.weekly
var/spool/cron/
var/spool/cron/atjobs/
var/spool/cron/atjobs/.SEQ
var/spool/cron/atspool/
var/spool/cron/crontabs/
var/spool/cups/
var/spool/cups/tmp/
var/spool/libreoffice/
var/spool/libreoffice/uno_packages/
var/spool/libreoffice/uno_packages/cache/
var/spool/lintian/
var/spool/plymouth/
var/spool/rsyslog/
var/tmp/

sent 5561793113 bytes  received 2380988 bytes  8335841.35 bytes/sec
total size is 5551454554  speedup is 1.00
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1070) [sender=3.0.9]

Copying filesystem failed.

Exiting...
```

not too sure what that means, other than it failed.

It looks like rsync failed to copy some files from your OS to the location the RAM session will be stored. From the text you've provided, it's hard to say why. It looks like rsync finished copying everything it could however, so if the files that failed to copy are non-essential, the script might be overly cautious in not proceeding. I'll try running the script on a fresh install to see if the same thing happens on a fresh system. You can try modifying the script by replacing the lines that read:

```
#Check if /home needs to be included in the file system transfer
if [[ "$NewHome" == "true" ]] || [[ "$PreExistingHome" == "true" ]]
then
	#Exclude /home. It will be copied later.
	sudo rsync -av --delete / ${DEST} --exclude=/mnt/* --exclude=/media/* --exclude=/proc/* --exclude=/tmp/* --exclude=/dev/* --exclude=/sys/* --exclude=/home/* --exclude=/etc/mtab --exclude=/live --exclude=/RAM_Session --exclude=/Original_OS --exclude=${DEST} 2>&1 | tee /tmp/fs_sync
else
	#Don't exclude /home. Delete anything in Trash for every user being copied.
	sudo rsync -av --delete / ${DEST} --exclude=/mnt/* --exclude=/media/* --exclude=/proc/* --exclude=/tmp/* --exclude=/dev/* --exclude=/sys/* --exclude=/etc/mtab --exclude=/live --exclude=.gvfs --exclude=.local/share/Trash/files/* --exclude=/RAM_Session --exclude=/Original_OS --exclude=${DEST} 2>&1 | tee /tmp/fs_sync
fi
```

to now say:

```
#Check if /home needs to be included in the file system transfer
if [[ "$NewHome" == "true" ]] || [[ "$PreExistingHome" == "true" ]]
then
	#Exclude /home. It will be copied later.
	sudo rsync -av --delete / ${DEST} --exclude=/mnt/* --exclude=/media/* --exclude=/proc/* --exclude=/tmp/* --exclude=/dev/* --exclude=/sys/* --exclude=/home/* --exclude=/etc/mtab --exclude=/live --exclude=/RAM_Session --exclude=/Original_OS --exclude=${DEST} 2>/tmp/err.log | tee /tmp/fs_sync
else
	#Don't exclude /home. Delete anything in Trash for every user being copied.
	sudo rsync -av --delete / ${DEST} --exclude=/mnt/* --exclude=/media/* --exclude=/proc/* --exclude=/tmp/* --exclude=/dev/* --exclude=/sys/* --exclude=/etc/mtab --exclude=/live --exclude=.gvfs --exclude=.local/share/Trash/files/* --exclude=/RAM_Session --exclude=/Original_OS --exclude=${DEST} 2>/tmp/err.log | tee /tmp/fs_sync
fi
```

This should redirect all errors rsync comes across to /tmp/err.log. Once the modified script finishes running (when it exits with an error at the same point it did before), read /tmp/err.log, which should tell you which files rsync had trouble copying. I am guessing that the files that appear on that list will be some type of special files that rsync had trouble with.

> **Andrew James Collett said:**
> Also, would i be right to presume that's over 5 Gigs in size? I got rid of stuff in my home folder, but I have a lot installed, so its possible.

It's hard to say how big it will be before the script finishes running. Once the script is done, it will say how big the new image is.

Also, depending on which options you choose, the /home directory will not be stored on your RAM - it will have its own partition. In this case, it will not matter how big your /home is - it will not make the image any bigger.

> **Andrew James Collett said:**
> Im installing VM at the moment, VirtualBox, and will see how it works on a fresh install. is that what you meant?

Fresh install is good to try running the script on during experimentation, since it's a common starting point (my fresh install will be more or less the same as your fresh install), and that's what I'll try it on. My point about trying it in a virtual machine first was this:

When I write a script like this one, I try to make sure that it expects anything that can go wrong, and I make sure that if something does go wrong, it does not result in any kind of damage to your OS (deleted files, etc.). Despite this, the script was never tested on Ubuntu 12.10, so there is a chance, however small, that it might not like something that has changed in Ubuntu 12.10 since 12.04, and will do something unexpected. For this reason, I suggest that experimentation be done in a VM, where, if the script starts deleting your OS or creating millions of files in some directory in a infinate loop, or something else crazy, that your main OS with all your data on it will not crash. The worst that will happen is that the VM will crash, which you can easily restore. Also, snapshots are amazing in virtual machines, as they allow you to restore massive changes to an OS with a click of a button.

---

### Post by Andrew James Collett on 2012-11-13
So, did as you asked, (it only replaced one block of code though?, and here's the output of the err.log

```
rsync: readlink_stat("/run/user/andrew/gvfs") failed: Permission denied (13)
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1070) [sender=3.0.9]
```

and the final output after exit was the same as far as I can see.

Just downloading the Ubuntu 12.10 image, will try it in virtual machine once it's done.

I've only got 4 gig ram, that should be okay right?

Edit*

There seems to be nothing in that folder :-?

*Edit no2
Seems the permissions of the folder are weird, i as the user have only viewing perms on that file. but, since there is nothing in it, i'll try skip it? see what happens.

Also, i've noticed this folder doesn't exist in ubuntu 12.04, as far as i can see. so will see what happens if i ignor it.

*Edit 3!!!

Ran it like that, ignoring the file, and it finished successfully. however, when I booted into it, it got stuck. Said something about /live not being able to mount on /root/live. where can I find those output logs? Then I'll put em up.

---

### Post by terminator14 on 2012-11-13
> **Andrew James Collett said:**
> So, did as you asked, (it only replaced one block of code though?, and here's the output of the err.log

```
rsync: readlink_stat("/run/user/andrew/gvfs") failed: Permission denied (13)
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1070) [sender=3.0.9]
```

and the final output after exit was the same as far as I can see.

~/.gvfs is where your shares (Windows, FTP, etc.) get mounted to when you connect to a server from nautilus. ~/.gvfs has always had a problem being copied by rsync - I never did figure out why. My script's rsync commands ignored ~/.gvfs (--exclude=.gvfs) but the .gvfs directory has moved in Ubuntu 12.10 from ~/ to /run/user/<user>/gvfs. You can safely tell the script to ignore that directory, as you did. I will update the list of excluded directories in my script when I release a 12.10 version.

> **Andrew James Collett said:**
> Just downloading the Ubuntu 12.10 image, will try it in virtual machine once it's done.

I've only got 4 gig ram, that should be okay right?


For a basic, fresh install, that should be plenty of RAM. If you've installed a lot of programs, it's hard to say.

> **Andrew James Collett said:**
> Ran it like that, ignoring the file, and it finished successfully. however, when I booted into it, it got stuck. Said something about /live not being able to mount on /root/live. where can I find those output logs? Then I'll put em up.

I'm not sure which log would have the error you mentioned, but normally, you would be able to find it with:

```

cd /var/log
sudo grep -ri '/root/live' *
```

In your case however, it is likely that the logs get written to RAM just like everything else, so they may not be around when you reboot.

I will try to reproduce the problem by running the script on a fresh Ubuntu 12.10 install, but so far I'm having trouble running 12.10 and all its fancy graphics in my VM.

I'll post back when I try the script on 12.10.

---

### Post by Lyfang on 2012-11-13
Would be nice if Ubuntu supported to load the entire OS in RAM by default. Making an option for booting Ubuntu "RAM only". The possiblilty of choosing this on the GRUB menu and perhaps as default boot. Also set automatically to 'toram' if the system detects more than X amount of GB memory available. See also: [Unable to boot Ubuntu using TORAM=yes (copy livecd to RAM)]("https://bugs.launchpad.net/ubuntu/+source/casper/+bug/25496")

---

### Post by terminator14 on 2012-11-13
> **Lyfang said:**
> Would be nice if Ubuntu supported to load the entire OS in RAM by default. Making an option for booting Ubuntu "RAM only". The possiblilty of choosing this on the GRUB menu and perhaps as default boot. 

There are disadvantages to loading the OS to RAM like my script does. Anyone downloading and running my script must understand them and accept them before continuing. Setting this option by default may confuse a lot of people, as their config files will not be permanent and they won't understand why. It may also anger some people as they spend hours or days making changes to their OS that a reboot will undo. I think it would be a better idea if Ubuntu would do something like this:

[http://ubuntuforums.org/showpost.php?p=10212414&postcount=13]("http://ubuntuforums.org/showpost.php?p=10212414&postcount=13")

by default. Basically, it would preload all files and folders on the system into RAM at boot. This has the potential to have all the advantages of my script with none of the disadvantages. 

> **Lyfang said:**
> See also: [Unable to boot Ubuntu using TORAM=yes (copy livecd to RAM)]("https://bugs.launchpad.net/ubuntu/+source/casper/+bug/25496")

This is a completely different topic. I wrote a script a while back to make the TORAM feature work on live CDs, which can be found here:

[http://ubuntuforums.org/showthread.php?t=1603423](http://ubuntuforums.org/showthread.php?t=1603423)

It may or may not work with Ubuntu 12.10 though, as I wrote it in 2010. I did however update the script a few weeks ago to work on the latest Linux Mint, which can be found here:

[http://forums.linuxmint.com/viewtopic.php?f=42&t=115792]("http://forums.linuxmint.com/viewtopic.php?f=42&t=115792")

---

### Post by terminator14 on 2012-11-14
> **andrew james collett said:**
> *edit 3!!!

Ran it like that, ignoring the file, and it finished successfully. However, when i booted into it, it got stuck. Said something about /live not being able to mount on /root/live. Where can i find those output logs? Then i'll put em up.

After fixing the gvfs problem, I ran into the same problem with it not booting. I'm working on it. It looks like this problem might take a while to figure out though. Hopefully once it's solved, everything else goes smoothly, and I'll be able to upload the script right away.

---

### Post by Slim Odds on 2012-11-14
> **Lyfang said:**
> Would be nice if Ubuntu supported to load the entire OS in RAM by default. Making an option for booting Ubuntu "RAM only". The possiblilty of choosing this on the GRUB menu and perhaps as default boot. Also set automatically to 'toram' if the system detects more than X amount of GB memory available. See also: [Unable to boot Ubuntu using TORAM=yes (copy livecd to RAM)]("https://bugs.launchpad.net/ubuntu/+source/casper/+bug/25496")
There is no such thing as "the entire OS" in this context. This is part of the problem with this concept.

Ubuntu does load the "entire OS" into memory. Just not every possible application and library. As I've mentioned in the past (and Terminator has also mentioned), the best "solution" is to preload applications and their libraries based on YOUR needs (or desires).

This creates a simple and universal solution that is not dependent on any particular version of Ubuntu (for Linux for that matter).

Now, if you have 100 GB of RAM, then just copy the entire disk into RAM. It will take a while, but will be really fast after that.

---

### Post by tytanium0503 on 2012-11-14
> **terminator14 said:**
> After fixing the gvfs problem, I ran into the same problem with it not booting. I'm working on it. It looks like this problem might take a while to figure out though. Hopefully once it's solved, everything else goes smoothly, and I'll be able to upload the script right away.

Hey terminator. Once you figure this out could you explain what all is causing the mount issue? I'm trying to learn more about Ubuntu/linux and am intrigued with your script.

---

### Post by terminator14 on 2012-11-14
> **tytanium0503 said:**
> Hey terminator. Once you figure this out could you explain what all is causing the mount issue? I'm trying to learn more about Ubuntu/linux and am intrigued with your script.

I'll try, but if you are curious, you may want to check out this page:

[http://ubuntuforums.org/showthread.php?t=1499338]("http://ubuntuforums.org/showthread.php?t=1499338")

and this one:

[http://ubuntuforums.org/showthread.php?t=707230]("http://ubuntuforums.org/showthread.php?t=707230")

The first was my original tutorial for doing what the script does, but manually. It's a bit outdated, but the idea is the same, and without all the loops, if statements, questions to the user, and other code the script has, it might just be easier to read.

The second link was what my original tutorial was based on, without which, neither the tutorial nor the script would have been possible.

Also, if you just want to learn about what linux is made of in general (without focusing on squashfs), I recommend you check out the [lfs project]("http://www.linuxfromscratch.org/lfs/").

---

### Post by terminator14 on 2012-11-14
As far as I can figure, there has been a change in initramfs used in Ubuntu 12.10 where the directory /live had become /root/live, as outlined here:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=688782]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=688782")

The live-boot package version that comes in the repos of 12.10 does not account for this change. This caused the squashfs image not to boot. While the patches available on the page would probably fix the problem, a debian moderator replied to that post claiming that the new version of live-boot already addressed that problem. Having read that, I found the new version of live-boot online, which is newer than the one from the repos, and gave it a try. It worked perfectly.

After making the changes to the script, here's the 12.10 version. Let me know if there are any problems with it.

---

### Post by yhusha on 2012-12-05
ok so after trying this and it worked sort of ... it didn't seem to be much faster if at all though it took longer to boot with a 800+ mg squash and a gig of ram plus 2gig swap it should have performed better especially being that the ram never maxxed out aaccording to free...  and the swapp was almost always 3/4 free the uninstall command would not remove it so how to get rid of the configuration to try with a smaller squash tried the sudo remove thing mentioned in the forum but that didn't do anything and now it wont even boot to ram session after security updates  apparently squashfs has increased in size now?

---

### Post by yhusha on 2012-12-05
and by the way it is 12.04.1

---

### Post by terminator14 on 2012-12-05
> **yhusha said:**
> ok so after trying this and it worked sort of ... it didn't seem to be much faster if at all though it took longer to boot with a 800+ mg squash and a gig of ram plus 2gig swap it should have performed better especially being that the ram never maxxed out aaccording to free...  and the swapp was almost always 3/4 free the uninstall command would not remove it so how to get rid of the configuration to try with a smaller squash tried the sudo remove thing mentioned in the forum but that didn't do anything and now it wont even boot to ram session after security updates  apparently squashfs has increased in size now?

1. Please use punctuation. Your reply is hard to read as it was written as one long sentence.

2. The RAM session will speed up your computer if you have enough RAM to store the OS in it, as well as enough RAM left over for regular usage. You clearly do not. 1 GB is not enough for an 800+ MB image, plus regular usage. The fact that your RAM "never maxxed out" means nothing. RAM never maxes out at 100% usage. If it's usage is high enough, it will start using swap, which yours did. 3/4 free swap means your swap is 1/4 in use, which, out of 2gb, is 500MB. Swap is stored on a hard drive, and as such, slows down your system considerably. I've seen a few kb of swap usage noticeably slow down a system. 500MB is pretty much guaranteed to make your system slow. If you want to use this script, either decrease the size of the image considerably, or get more RAM.

3. The boot process takes longer by design, as it has to copy the 800+ MB image (in your case) into RAM. 

4. Why did the uninstall script not work? Did you run it from your original OS? What did it say? And after running the uninstall, you're not supposed to be able to boot into the ram session - that's kind of the point.

5. What security updates? Where (RAM session/Original OS)? What does that have to do with anything?

---

### Post by yhusha on 2012-12-05
well they were updates in the original os, and the ram session would not work before attempting to remove the ram session because after updates to the original the ram sessions would not boot anymore. so the idea is to get rid of that configuration.) it said not enough memory and no more processes could be killed so somehow updates to the original os increased the ram session squash
and the uninstall was done from the origanl not ram session as the ram session will not boot to try uninstall from it. 
yhusha@yhusha-AOD260:~$ sudo ./RAM_booster.sh --uninstall
[sudo] password for yhusha: 
sudo: ./RAM_booster.sh: command not found

---

### Post by terminator14 on 2012-12-06
> **yhusha said:**
> well they were updates in the original os, and the ram session would not work before attempting to remove the ram session because after updates to the original the ram sessions would not boot anymore. so the idea is to get rid of that configuration.) it said not enough memory and no more processes could be killed so somehow updates to the original os increased the ram session squash
and the uninstall was done from the origanl not ram session as the ram session will not boot to try uninstall from it. 
yhusha@yhusha-AOD260:~$ sudo ./RAM_booster.sh --uninstall
[sudo] password for yhusha: 
sudo: ./RAM_booster.sh: command not found

The 12.04 script is called "RAM_booster_Ubuntu_12.04.sh", not "RAM_booster.sh", and needs to be made executable with:

```
sudo chmod a+x RAM_booster_Ubuntu_12.04.sh
```

prior to being run.

---

### Post by apochry on 2012-12-06
Hi terminator,

and thanks for the great work you are sharing! I saw this thread  one and a half year ago and wanted do try it out, but didn't have enough RAM back than. Now I'm good to go (I have 8GB) and I would like give it a try.  :-)

There is only one thing I am concerned about...
I'm using my installation of 12.04-32bit quite a while already (since released) and I think, with all the stuff installed it might have gotten quite fat by now (big in size I mean). 
:confused: Should I be worried about the size of the image that is going to be created and loaded to RAM later? How can I check if it will fit in my 8Gigs of RAM?

Thanks!

-Christo

---

### Post by terminator14 on 2012-12-06
> **apochry said:**
> Hi terminator,

and thanks for the great work you are sharing! I saw this thread  one and a half year ago and wanted do try it out, but didn't have enough RAM back than. Now I'm good to go (I have 8GB) and I would like give it a try.  :-)

There is only one thing I am concerned about...
I'm using my installation of 12.04-32bit quite a while already (since released) and I think, with all the stuff installed it might have gotten quite fat by now (big in size I mean). 
:confused: Should I be worried about the size of the image that is going to be created and loaded to RAM later? How can I check if it will fit in my 8Gigs of RAM?

Thanks!

-Christo

The best way to check is to run it. The script will tell you at the end, when it's done creating the squashfs image, how big the image is. If you have more RAM than the image size, with enough RAM left over for regular OS operation, then you can give booting it a try. If not, you can always uninstall the RAM session without ever having booted into it.

There is only 1 thing that the script might change and not revert during an uninstall (if that's what your concern is): during the first stages of the script running, it asks you if you want a separate /home partition (if you don't already have one). If so, it asks you to prepare one on your hard drive, and tell the script which partition it is. Once you tell it, the script will copy your /home to the new partition, and mount it in the RAM session, as well as the original OS. If you choose to uninstall, this will not be undone automatically, and your OS's /home will remain mounted on the new partition you assigned it. If you choose to undo this manually, it's as easy as removing the /home line from your /etc/fstab and rebooting. Everything else done by the script will be undone by the uninstall argument to the script.

---

### Post by yhusha on 2012-12-06
ok so worked over the system shrunk the squash to around 600 mgs and redid the whole thing.  though the performance in ram session still feels like as it did when the squash was around 800 50ish. so will try with a 4 gig ram install. by way do not speak english... it is foreign strange language. for punctuations

---

### Post by terminator14 on 2012-12-06
> **yhusha said:**
> ok so worked over the system shrunk the squash to around 600 mgs and redid the whole thing.  though the performance in ram session still feels like as it did when the squash was around 800 50ish. so will try with a 4 gig ram install. by way do not speak english... it is foreign strange language. for punctuations

If it's still slow, it's either still using swap (see output of "free"), or other hardware in your computer is slowing it down (slow CPU?). 4 gigs of RAM should be a good start.

English is not my first language either. I'm not trying to make fun of you or anything - it really is hard to read your posts sometimes without commas or periods.

---

### Post by yhusha on 2012-12-08
yes still uses swap. should it not use any.

---

### Post by terminator14 on 2012-12-08
> **yhusha said:**
> yes still uses swap. should it not use any.

Ideally. Any swap usage slows down the system considerably.

---

### Post by cbennett926 on 2012-12-08
I've been trying to get his set up but whenever I pick a device to seperate the partitions, it cancels out and exits. I have a 500 GB harddrive and 8 gigs of RAM, I shrunk the partition to 100 gigs and now have 400 gigs of extended drive, all of which is unallocated space.

Tips?

Also this is on Ubuntu 12.10

---

### Post by terminator14 on 2012-12-08
> **cbennett926 said:**
> I've been trying to get his set up but whenever I pick a device to seperate the partitions, it cancels out and exits. I have a 500 GB harddrive and 8 gigs of RAM, I shrunk the partition to 100 gigs and now have 400 gigs of extended drive, all of which is unallocated space.

Tips?

Also this is on Ubuntu 12.10

Unallocated space isn't a partition. It sounds like you're trying to tell it something like /dev/sda when it's looking for something in the form of /dev/sda2 - the specific partition it should use for /home. Make sure the partition you are telling it to use is formatted as ext4, and empty.

---

### Post by cbennett926 on 2012-12-08
> **terminator14 said:**
> Unallocated space isn't a partition. It sounds like you're trying to tell it something like /dev/sda when it's looking for something in the form of /dev/sda2 - the specific partition it should use for /home. Make sure the partition you are telling it to use is formatted as ext4, and empty.


Just did this, there are now two partitions

/dev/sda1 - the primary partition that I am on right now

/dev/sda2 - The one I am trying to seperate to

```


This script will create a copy of your Ubuntu OS in /var/squashfs/ and
then use that copy to create a squashfs image of it located at /live. After
this seporation, your old OS and your new OS (the RAM Session) will be two
completely separate entities. Updates of one OS will not affect the update
of the other (unless done so using the update script - in which case two
separate updates take place one after the other), and the setup of packages
on one will not transfer to the other. Depending on what you chose however,
your /home may be shared between the two systems.

/home is the place where your desktop, documents, music, pictures, and program
settings are stored. Would you like /home to be stored on a separate partition
so that it can be writable? If you choose yes, you will need to provide a
device name of a partition as this script will not attempt to partition your
drives for you. If you choose no, /home will be copied to the RAM session
as is, and will become permanent. This means everytime you reboot, it will
revert to the way it is right now. Moving it to a separate partition will
also make /home shared between the two systems. If you are unsure, pick to
store /home on a separate partition.: [(S)eporate/(c)opy as is]: S






You chose to create a separate partition for /home

As this script is far too stupid to be able to find a partition to store
your /home for you, you will need to do this yourself and tell the script
the device name. The partition should be big enough to store your Desktop,
Music, Pictures, and whatever else your /home will contain. I recommend a
partition no smaller than 3GB. What would you like to do?:

1) Launch gparted (it will be installed if necessary)
2) Enter device name to use for /home
3) Exit script

Your choice [2]: /dev/sda2











/dev/sda2 is an invalid choice.

Exiting....


```

---

### Post by terminator14 on 2012-12-08
> **cbennett926 said:**
> Just did this, there are now two partitions

/dev/sda1 - the primary partition that I am on right now

/dev/sda2 - The one I am trying to seperate to

```


This script will create a copy of your Ubuntu OS in /var/squashfs/ and
then use that copy to create a squashfs image of it located at /live. After
this seporation, your old OS and your new OS (the RAM Session) will be two
completely separate entities. Updates of one OS will not affect the update
of the other (unless done so using the update script - in which case two
separate updates take place one after the other), and the setup of packages
on one will not transfer to the other. Depending on what you chose however,
your /home may be shared between the two systems.

/home is the place where your desktop, documents, music, pictures, and program
settings are stored. Would you like /home to be stored on a separate partition
so that it can be writable? If you choose yes, you will need to provide a
device name of a partition as this script will not attempt to partition your
drives for you. If you choose no, /home will be copied to the RAM session
as is, and will become permanent. This means everytime you reboot, it will
revert to the way it is right now. Moving it to a separate partition will
also make /home shared between the two systems. If you are unsure, pick to
store /home on a separate partition.: [(S)eporate/(c)opy as is]: S






You chose to create a separate partition for /home

As this script is far too stupid to be able to find a partition to store
your /home for you, you will need to do this yourself and tell the script
the device name. The partition should be big enough to store your Desktop,
Music, Pictures, and whatever else your /home will contain. I recommend a
partition no smaller than 3GB. What would you like to do?:

1) Launch gparted (it will be installed if necessary)
2) Enter device name to use for /home
3) Exit script

Your choice [2]: /dev/sda2











/dev/sda2 is an invalid choice.

Exiting....


```

At that point, your choices are 1, 2, or 3, where 2 (the choice in the square brackets) is the default option if you just press enter without typing anything. So in your case, either answer 2 (instead of /dev/sda2), or just hit enter, and the next screen will ask you for the partition. Sorry if it's confusing.

---

### Post by cbennett926 on 2012-12-08
> **terminator14 said:**
> At that point, your choices are 1, 2, or 3, where 2 (the choice in the square brackets) is the default option if you just press enter without typing anything. So in your case, either answer 2 (instead of /dev/sda2), or just hit enter, and the next screen will ask you for the partition. Sorry if it's confusing.

Ok, I'm getting it figured out now, however I got this error message

```


Installing essential packages:
Running apt-get update...
Installing squashfs-tools...
Installing live-boot-initramfs-tools...
Installing live-boot...
live-boot failed to download. You'll have to download and install it
manually... Try: http://packages.debian.org/sid/all/live-boot/download


```


I then ran

```


sudo apt-get install live-boot


```

After that it did install the right thing, and another dependent file/program. It still hangs and says it can't download after running the script again.

---

### Post by terminator14 on 2012-12-08
> **cbennett926 said:**
> Ok, I'm getting it figured out now, however I got this error message

```


Installing essential packages:
Running apt-get update...
Installing squashfs-tools...
Installing live-boot-initramfs-tools...
Installing live-boot...
live-boot failed to download. You'll have to download and install it
manually... Try: http://packages.debian.org/sid/all/live-boot/download


```


I then ran

```


sudo apt-get install live-boot


```

After that it did install the right thing, and another dependent file/program. It still hangs and says it can't download after running the script again.

The live-boot from the repos doesn't work properly. The one that works is live-boot_3.0~b7-1_all.deb, but all the links I used in the script for it went down, since the new stable version appears to now be live-boot_3.0~b8-1_all.deb. I was going to quickly update my script with the new URLs but I got side-tracked. Basically, go to:

[http://packages.ubuntu.com/hu/raring/all/live-boot/download](http://packages.ubuntu.com/hu/raring/all/live-boot/download)

and install that package. You may want to remove the one from the repos first (sudo apt-get remove live-boot)

If it still doesn't work (I haven't tested it with the b8 version), find live-boot_3.0~b7-1_all.deb somewhere. I'll update the script when I get a chance.

---

### Post by terminator14 on 2012-12-08
Actually, I decided to update the script after all. Unfortunately, to properly test it, I would need to create a VM and install Ubuntu 12.10 before running the script in it, which would take longer than I have, so please let me know if this doesn't work.

Update: I just tested it and it appears to work great on both x86 and x64 versions of Ubuntu 12.10.

---

### Post by yhusha on 2012-12-10
after making system even leaner. want to uninstall and redo do with new config . because now even with 4 media files playing and web browser and other apps it is not touching swap in original os so want to redo this. have an updated uninstall for 12.04  tried sudo ./RAM_booster_Ubuntu_12.04.sh . must this be done from ram session will try that

---

### Post by yhusha on 2012-12-10
.

---

### Post by ernest1 on 2012-12-10
Can anyone tell me if this works in Ubuntu 12.10?
I'm gonna try it asap :)

---

### Post by yhusha on 2012-12-10
ok so tried this from ram session  sudo ./RAM_booster_Ubuntu_12.04.sh --uninstall
and it showed sudo: ./RAM_booster_Ubuntu_12.04.sh: command not found

---

### Post by yhusha on 2012-12-10
yhusha@yhusha-AOD260:~$ sudo ./RAM_booster_Ubuntu_12.04.sh --uninstall
[sudo] password for yhusha: 
sudo: ./RAM_booster_Ubuntu_12.04.sh: command not found
yhusha@yhusha-AOD260:~$ sudo ./RAM_booster.sh --uninstall
sudo: ./RAM_booster.sh: command not found
that is i/o info from original os

---

### Post by yhusha on 2012-12-10
would realy like to try this with recent config 
-m
             total       used       free     shared    buffers     cached
Mem:           990        754        236          0         38        353
-/+ buffers/cache:        362        628
Swap:         1953          0       1953
thats current config original os so to uninstall and remake the ram session would probaly work greatly. with 3 media files playing and ff webbrowser and gnome term all up with 9 tabs.

---

### Post by apochry on 2012-12-10
> **ernest1 said:**
> Can anyone tell me if this works in Ubuntu 12.10?
I'm gonna try it asap :smile:

See post [#150]("http://ubuntuforums.org/showpost.php?p=12395151&postcount=150"). There is an updated script for 12.10 attached to it. This as what the author says about it:

> **terminator14 said:**
> Actually,  I decided to update the script after all. Unfortunately, to properly  test it, I would need to create a VM and install Ubuntu 12.10 before  running the script in it, which would take longer than I have, so please  let me know if this doesn't work.

---

### Post by yhusha on 2012-12-10
reruning the script process uninstalls the old ram session  .solved

---

### Post by terminator14 on 2012-12-10
> Actually, I decided to update the script after all. Unfortunately, to properly test it, I would need to create a VM and install Ubuntu 12.10 before running the script in it, which would take longer than I have, so please let me know if this doesn't work.

That post kind of makes it sound like the entire 12.10 version of the script needs testing. To be clear, the 12.10 script was tested months before that post, and uploaded a few pages earlier. The testing being referred to in this post is for a single part of the 12.10 script - the part that downloads and installs live-boot. Installing live-boot would normally be a simple task, but the fact that the one from the repos doesn't work makes this a bit more difficult. The original 12.10 script had wget commands to download the live-boot .deb from one of several different URL's, but all the links went down when a new stable version of live-boot became available. The code that finds and downloads the new version of live-boot is what has yet to be tested.

---

### Post by terminator14 on 2012-12-10
> **yhusha said:**
> reruning the script process uninstalls the old ram session  .solved

Yes, rerunning the script detects that it has previously run and offers to uninstall it.

---

### Post by yhusha on 2012-12-10
so the original os is real nice RBH in fact when idle it uses about 300megs of ram still uses about 100-400 megs of swap in ramsession however. need more ram apparently.

---

### Post by terminator14 on 2012-12-10
> **yhusha said:**
> so the original os is real nice RBH in fact when idle it uses about 300megs of ram still uses about 100-400 megs of swap in ramsession however. need more ram apparently.

Sounds like it.

---

### Post by HelmarD on 2012-12-14
I would like to add the following experience to this interesting thread:
I use Pear Linux 6 which is based on Ubuntu 12.04.
The script for ubuntu 12.04 is generally working well, but I found out that the system was not as fast as expected. Looking at the resources I found out that all CPUs were at 100% instead of being idle.
When booting the "normal" way (second optiong in grub) this was not the case.

Test machine: Thinkpad x121e, 256GB SSD, 16GB RAM, PearLinux installed/booted from 16GB USB Stick.

Best regards
Helmar

---

### Post by terminator14 on 2012-12-14
> **HelmarD said:**
> I would like to add the following experience to this interesting thread:
I use Pear Linux 6 which is based on Ubuntu 12.04.
The script for ubuntu 12.04 is generally working well, but I found out that the system was not as fast as expected. Looking at the resources I found out that all CPUs were at 100% instead of being idle.
When booting the "normal" way (second optiong in grub) this was not the case.

Test machine: Thinkpad x121e, 256GB SSD, 16GB RAM, PearLinux installed/booted from 16GB USB Stick.

Best regards
Helmar

Thanks for the input. I haven't tried Pear Linux myself, but I'm sure other people using it who may be interested in this script will find your input useful.

---

### Post by cyberphrog on 2012-12-14
Thanks, will give it a try.

---

### Post by solo16 on 2012-12-17
Hi terminator14,

First of all thanks for your sharing!!!

I have tried the script several times however It does not fully work for me.

I am using it with my little media server with 10.04 rt-kernel installed and it is running serial console mode.

I have successfully ran the script without error and rebooted into console mode it works but when I tried running it on serial console mode it does not work just black screen.

So could you please kindly teach me what to do in order to make it work with serial console?

Thank you in advance!!!

Cheers!!!

---

### Post by terminator14 on 2012-12-18
> **solo16 said:**
> Hi terminator14,

First of all thanks for your sharing!!!

I have tried the script several times however It does not fully work for me.

I am using it with my little media server with 10.04 rt-kernel installed and it is running serial console mode.

I have successfully ran the script without error and rebooted into console mode it works but when I tried running it on serial console mode it does not work just black screen.

So could you please kindly teach me what to do in order to make it work with serial console?

Thank you in advance!!!

Cheers!!!

No clue - I've never used serial console mode before. You could try the newer versions of Ubuntu if you are willing to update your media server's OS - maybe those will fix the problem. If not - I'm afraid I won't be much help with that particular problem.

---

### Post by terminator14 on 2013-02-22
> **terminator14 said:**
> ...according to the new ubuntu forums rules, I can't modify my original post anymore in order to update the script - I have to move the entire post to a wiki page. I'll look into how to do this sometime, but for now, here's the updated script.

I looked into this months ago but couldn't figure it out, so I put it off. Recently I've discovered git, and I figured I could use github to upload my script so I can always update it and people can help maintain it if they want.

To get the latest version of the scirpt, run:

```
sudo apt-get install git
git clone git://github.com/terminator14/RAM_booster.git
```

This should simplify things a bit - ever since the forum rule change, I've been uploading updates to the script to my replies instead of the original post, making them hard to find. With git, you'll always know what the latest version is.

---

### Post by rockcreektech on 2013-03-04
So I tried your script because it has some real potential for helping me with a home grown thin client project I'm working on. The two main features this has that make this so appealing are that it produces a machine that is completely power failure agnostic and that absolutely no changes become persistent unless I say so. However, I've run into a couple of snags that I'm hoping you can shed some light on. 

The most significant one is the fact the the /etc/network/interfaces file that ends up in the ram_session is totally different from the one in the original OS. If I rchroot into the sqashfs image, the file correctly matches the one from the original OS; so I can't figure out where the changes are coming from. The change that is most annoying is that "auto eth0" is missing; so I have to manually bring up the interface with "sudo ifup eth0" on every boot. Since both of the interface files that this should be sourced from are correct, I can't find a way to fix it.

The second oddity that I think is related to your script is not quite as deal breaking, but still annoying. Due to the fact that they are not specified explicitly in the grub entry that get's created for the ram_session, it totally ignores the "splash quiet" options in /etc/default/grub. Like I said, this is not exactly an earth shattering issue, but it probably would be nice if it checked the user's original boot parameters in grub configuration and included them into the ram_session grub entry.

Thanks for all your hard work on this. I know you've had to endure a lot of criticism from people who were too short-sited to see any potential benefits from it, but for those of us who aren't operating inside the box, it's nice to not have to do all this work all over again. It makes me scratch my head and wonder why anyone in the Linux community would feel the need to bash someone for exercising their Linus-given right to freely modify their OS any flippin' way they want to. I thought that was the point after all. 

:-k  :roll:

---

### Post by terminator14 on 2013-03-04
> **rockcreektech said:**
> The most significant one is the fact the the /etc/network/interfaces file that ends up in the ram_session is totally different from the one in the original OS. If I rchroot into the sqashfs image, the file correctly matches the one from the original OS; so I can't figure out where the changes are coming from. The change that is most annoying is that "auto eth0" is missing; so I have to manually bring up the interface with "sudo ifup eth0" on every boot. Since both of the interface files that this should be sourced from are correct, I can't find a way to fix it.

It's hard to say, but it's possible that your /var/squashfs and the /live/filesystem.squashfs image on your original OS are no longer in sync, which happens if your /var/squashfs was modified after the image was created. Basically, when you run "rchroot -R" you end up being chrooted into /var/squashfs on the original OS. You make changes that you want in your RAM session, and you tell it to recreate the filesystem.squashfs image when you are done. Grub does NOT use /var/squashfs/ to boot the RAM session - it uses the filesystem.squashfs image. That means that if you made changes to /var/squashfs (say through rchroot -R) but didn't have it recreate the filesystem.squashfs image (sudo rupdate --force), your /var/squashfs/etc/network/interfaces file will say one thing and your filesystem.squashfs's /etc/network/interfaces file will say another. Maybe that's what's happening there. If that's not it, then maybe some boot script is messing with your interfaces file, though I can't think of one that would.

> **rockcreektech said:**
> The second oddity that I think is related to your script is not quite as deal breaking, but still annoying. Due to the fact that they are not specified explicitly in the grub entry that get's created for the ram_session, it totally ignores the "splash quiet" options in /etc/default/grub. Like I said, this is not exactly an earth shattering issue, but it probably would be nice if it checked the user's original boot parameters in grub configuration and included them into the ram_session grub entry.

Something I overlooked when writing the original script. It has been fixed and uploaded to git. It still may not function the way you might expect however. While the splash screen will now activate if it is specified in /etc/default/grub, the rsync output that copies the squashfs image into RAM still shows up. Fixing it would likely require taking apart the initfs image, and a lot of tricky code that would require lots and lots of testing. If I spent a couple hours/days on it, I might have a fix, but honestly, it seems like a waste of time for something so minor, and aesthetic, especially since it provides interesting information (progress on how long it will take to copy the squashfs image to RAM).

If you want to try the fix without destroying your RAM session and recreating it with the new RAM_booster script, you should be able to do it if you just:

```
sudo rchroot -R
 change /etc/grub.d/06_RAMSESS
 exit
sudo rchroot -O
 change /etc/grub.d/06_RAMSESS
 update-grub2
 exit
sudo rupdate --force
```

In both cases, the new 06_RAMSESS should say:

```
#!/bin/sh -e

KER_NAME=$(ls /boot/ | grep vmlinuz | sort -n | tail -1 | sed 's/vmlinuz-//')
**[COLOR="#FF0000"]GRUB_CMDLINE_LINUX_DEFAULT=$([ -e /etc/default/grub ] && cat /etc/default/grub | grep GRUB_CMDLINE_LINUX_DEFAULT | grep -o '["].*["]' | tr -d '"')[/COLOR]**

if [ -z "$KER_NAME" ]
then
        KER_NAME=$(uname -r)
fi

cat << EOF

menuentry "Ubuntu, Linux $KER_NAME to RAM" {
  set uuid_grub_boot=6c599be7-bacc-4420-8c9b-aa9a9a70944c
  set uuid_os_root=6c599be7-bacc-4420-8c9b-aa9a9a70944c

  search --no-floppy --fs-uuid \$uuid_os_root --set=root
  search --no-floppy --fs-uuid \$uuid_grub_boot --set=grub_boot

  set grub_boot=(\$grub_boot)

  if [ \$uuid_grub_boot == \$uuid_os_root ] ; then                 
     set grub_boot=\$grub_boot/boot
  fi

  linux \$grub_boot/vmlinuz-$KER_NAME boot=live toram=filesystem.squashfs apparmor=0 security="" root=/dev/disk/by-uuid/\$uuid_os_root ro **[COLOR="#FF0000"]$GRUB_CMDLINE_LINUX_DEFAULT[/COLOR]**
  initrd \$grub_boot/initrd.img-$KER_NAME
}
EOF
```

> **rockcreektech said:**
> Thanks for all your hard work on this. I know you've had to endure a lot of criticism from people who were too short-sited to see any potential benefits from it, but for those of us who aren't operating inside the box, it's nice to not have to do all this work all over again. It makes me scratch my head and wonder why anyone in the Linux community would feel the need to bash someone for exercising their Linus-given right to freely modify their OS any flippin' way they want to. I thought that was the point after all. 

:-k  :roll:

While I appreciate your support and recognition of the work I put into this project, the criticism that some people have expressed has mostly been of a technical nature - whether or not such a drastic method is the best way of speeding up the computer as compared to other methods. I don't think anyone has even implied that I should not do what this script does just because it's messing with how Ubuntu does things.

Edit:

> **rockcreektech said:**
> So I tried your script because it has some real potential for helping me with a home grown thin client project I'm working on.

By the way, for this particular task you may be better of using my other script:
[URL="http://forums.linuxmint.com/viewtopic.php?uid=98503&f=213&t=115792&start=0"]
http://forums.linuxmint.com/viewtopic.php?uid=98503&f=213&t=115792&start=0[/URL]

which just adds a ToRAM feature to the LiveCD so that it copies the CD to RAM before it boots. The script also lets you easily customize the image, so you'll be able to install the thin-client software on the disk. The script was originally written for Ubuntu, but recently when I updated it, I only focused on making it work for Mint 13.

---

### Post by rockcreektech on 2013-03-05
> [COLOR=#000000]It's hard to say, but it's possible that your /var/squashfs and the /live/filesystem.squashfs image on your original OS are no longer in sync, which happens if your /var/squashfs was modified after the image was created. Basically, when you run "rchroot -R" you end up being chrooted into /var/squashfs on the original OS. You make changes that you want in your RAM session, and you tell it to recreate the filesystem.squashfs image when you are done. Grub does NOT use /var/squashfs/ to boot the RAM session - it uses the filesystem.squashfs image. That means that if you made changes to /var/squashfs (say through rchroot -R) but didn't have it recreate the filesystem.squashfs image (sudo rupdate --force), your /var/squashfs/etc/network/interfaces file will say one thing and your filesystem.squashfs's /etc/network/interfaces file will say another. Maybe that's what's happening there. If that's not it, then maybe some boot script is messing with your interfaces file, though I can't think of one that would.[/COLOR]

This happened when I originally created my squashfs image. I've not modified the original OS or /var/squashfs/ in any way. I did rchroot into both of them to see if either of them had a messed up interfaces file, but I never changed anything or recreated my image. This happened on my first boot after running rambooster for the first time.

> [COLOR=#000000] If I spent a couple hours/days on it, I might have a fix, but honestly, it seems like a waste of time for something so minor, and aesthetic, especially since it provides interesting information (progress on how long it will take to copy the squashfs image to RAM).[/COLOR]

Since this is being used for a thin client that will be deployed to my customers, there's really nothing interesting on the screen that I would want them to see :)

> [COLOR=#000000]While I appreciate your support and recognition of the work I put into this project, the criticism that some people have expressed has mostly been of a technical nature - whether or not such a drastic method is the best way of speeding up the computer as compared to other methods. I don't think anyone has even implied that I should not do what this script does just because it's messing with how Ubuntu does things.[/COLOR]

-and-

> [COLOR=#000000]By the way, for this particular task you may be better of using my other script:[/COLOR]
[URL="http://forums.linuxmint.com/viewtopic.php?uid=98503&f=213&t=115792&start=0"]
http://forums.linuxmint.com/viewtopic.php?uid=98503&f=213&t=115792&start=0[/URL]

[COLOR=#000000]which just adds a ToRAM feature to the LiveCD so that it copies the CD to RAM before it boots. The script also lets you easily customize the image, so you'll be able to install the thin-client software on the disk. The script was originally written for Ubuntu, but recently when I updated it, I only focused on making it work for Mint 13.[/COLOR]

I'm just saying that speed gains and whether or not there are better ways to achieve them is a very narrow view of the value of this approach you've taken. And while I love Mint (it's what I use on my own computers), it really isn't conducive to this project since there is no such thing as a minimal install of Mint.

Basically I want to achieve something very similar to a WYSE thin client with ThisOS , but without all the gaping security holes. So I'm starting with Ubuntu minimal, and putting on just the bare essential packages I need to achieve the desired result, including a ton of custom config that ultimately make it unrecognizable as a Linux installation. Then when I have it the way I want it, I want to make the whole thing boot up entirely into ram and get it's configuration from a central configuration server. The settings from the config server get grep'd and sed'd into all the appropriate places to make the computer do what it need to do, but disappear with every reboot; so nothing is ever permanent on the client. If the client were to be stolen, you'd lose a cheap, under powered piece of hardware and nothing more. If the end user decides to reboot by pulling the plug, the file system will be totally unaffected.

I've thought about starting out with a distro that was already designed to boot to a ramdisk, but most of them focus more on making their footprint as tiny as possible with extreme sacrifices to everything else (TinyCore) or trying to fit as much functionality as possible into a small ram-based full desktop environment (Puppy Linux). Neither of these were really what I was looking for.

I wanted to use the Ubuntu kernel because it has a great deal of hardware support built right in, making it so I should be able to put my whole project on a flash drive and turn just about any old computer instantly into my thin client. Space saving isn't really my biggest concern since storage space isn't that hard to come by even in flash drives these days. I just want a base platform that I can build into what I want with the least amount of headache possible, and Ubuntu minimal is great for that. I just have to find a way to accomplish my other goal of making it a ram boot, and RAM_booster seems like it might just be great for that.

If anyone has a better way of making my custom OS (not the LiveCD with all of it's software and fancy desktop environment :P ) boot entirely into ram then I'm open to suggestions. I also tried the method described in this thread:

[http://ubuntuforums.org/showthread.php?t=1967260&p=12521133#post12521133](http://ubuntuforums.org/showthread.php?t=1967260&p=12521133#post12521133)

but it was completely unsuccessful. I'm currently separating out /home and /var and making the root partition read only, but I really don't want changes to /home and /var persistent either...or susceptible to file system corruption from sudden reboots etc. So I'm really hoping to work out the kinks in RAM_booster.

Sorry for the long post :(

---

### Post by terminator14 on 2013-03-05
> **rockcreektech said:**
> This happened when I originally created my squashfs image. I've not modified the original OS or /var/squashfs/ in any way. I did rchroot into both of them to see if either of them had a messed up interfaces file, but I never changed anything or recreated my image. This happened on my first boot after running rambooster for the first time.

The only other thing I can think of is this:

> **terminator14 said:**
> **[SIZE="4"]Issues once you boot from RAM[/SIZE]**

The first time I did this, as soon as I booted from RAM I noticed that my Internet was not working. It turns out as stated [here]("https://bugs.launchpad.net/ubuntu/+source/fsprotect/+bug/477012") by jesbecker:

> apparmor does not work well with stacked and read only files systems. A work around for this bug is to either disable for remove apparmor.

Disable:
You can disable by adding apparmor=0 and security="" as kernel options in your grub boot configuration.

Remove:
You can also choose to remove apparmor by executing: sudo apt-get remove apparmor

This issue seems to affect any program that is protected/enforced by apparmor. 

As you may have noticed, this is the reason I added apparmor=0 and security="" to the end of the 50_RAMSESS. This fixes the internet. I also tried "sudo apt-get remove apparmor" as suggested by jesbecker before I made those additions to my 50_RAMSESS and that works too.

Maybe the apparmor=0 and security="" lines aren't helping in the new versions of Ubuntu like they used to. Try removing apparmor.

> **rockcreektech said:**
> Since this is being used for a thin client that will be deployed to my customers, there's really nothing interesting on the screen that I would want them to see :)


I see. If I get some free time between work, studying for LPIC, reading up on git, and messing with my Odroid-X, I'll see if I can find out how I can hide this.

> **rockcreektech said:**
> Basically I want to achieve something very similar to a WYSE thin client with ThisOS , but without all the gaping security holes. So I'm starting with Ubuntu minimal, and putting on just the bare essential packages I need to achieve the desired result, including a ton of custom config that ultimately make it unrecognizable as a Linux installation. Then when I have it the way I want it, I want to make the whole thing boot up entirely into ram and get it's configuration from a central configuration server. The settings from the config server get grep'd and sed'd into all the appropriate places to make the computer do what it need to do, but disappear with every reboot; so nothing is ever permanent on the client. If the client were to be stolen, you'd lose a cheap, under powered piece of hardware and nothing more. If the end user decides to reboot by pulling the plug, the file system will be totally unaffected.

I've thought about starting out with a distro that was already designed to boot to a ramdisk, but most of them focus more on making their footprint as tiny as possible with extreme sacrifices to everything else (TinyCore) or trying to fit as much functionality as possible into a small ram-based full desktop environment (Puppy Linux). Neither of these were really what I was looking for.

I wanted to use the Ubuntu kernel because it has a great deal of hardware support built right in, making it so I should be able to put my whole project on a flash drive and turn just about any old computer instantly into my thin client. Space saving isn't really my biggest concern since storage space isn't that hard to come by even in flash drives these days. I just want a base platform that I can build into what I want with the least amount of headache possible, and Ubuntu minimal is great for that. I just have to find a way to accomplish my other goal of making it a ram boot, and RAM_booster seems like it might just be great for that.

If anyone has a better way of making my custom OS (not the LiveCD with all of it's software and fancy desktop environment :P ) boot entirely into ram then I'm open to suggestions. I also tried the method described in this thread:

[http://ubuntuforums.org/showthread.php?t=1967260&p=12521133#post12521133](http://ubuntuforums.org/showthread.php?t=1967260&p=12521133#post12521133)

but it was completely unsuccessful. I'm currently separating out /home and /var and making the root partition read only, but I really don't want changes to /home and /var persistent either...or susceptible to file system corruption from sudden reboots etc. So I'm really hoping to work out the kinks in RAM_booster.

Sounds like an interesting project. If I had computers that needed to be used by the public (like a kiosk type deal with a coin mechanism), I would probably go about it in a very similar way. If you still don't have the hardware for your thin clients, I would suggest something like the raspberry pi ($35 computer), or the Odroid from Hardkernel (more expensive but has a quadcore CPU and more RAM than a raspberry).

> **rockcreektech said:**
> Sorry for the long post :(

My last post was just as long, and it looks like so is this one :)

---

### Post by rockcreektech on 2013-03-05
> [COLOR=#000000]I see. If I get some free time between work, studying for LPIC, reading up on git, and messing with my Odroid-X, I'll see if I can find out how I can hide this.[/COLOR]

Like I said. it's not the end of the world. The interfaces file glitch is the bigger issue. This issue was purely aesthetic. I'll try the apparmor deal and let you know.

> [COLOR=#000000]Sounds like an interesting project. If I had computers that needed to be used by the public (like a kiosk type deal with a coin mechanism), I would probably go about it in a very similar way. If you still don't have the hardware for your thin clients, I would suggest something like the raspberry pi ($35 computer), or the Odroid from Hardkernel (more expensive but has a quadcore CPU and more RAM than a raspberry).[/COLOR]

It's actually going to be very specific hardware because these will ultimately serve as cash registers.

---

### Post by terminator14 on 2013-03-15
> **rockcreektech said:**
> Since this is being used for a thin client that will be deployed to my customers, there's really nothing interesting on the screen that I would want them to see :)

If you are still looking for a way to hide the initial rsync message at boot, here's how:

Edit the script.

Just before the line that reads:

```
echo -e "Packages installed successfully\n"
```

which is about line 328, add the lines:

```
echo "Press Enter"
read key
```

to pause the script just after live-boot installs. Run the script, and when it pauses, open a new terminal and go to /lib/live/boot/. There, you will find the startup scripts that are responsible for rsync showing up on screen at boot, as well as the error messages that appear. To hide rsync, edit the file **9990-toram-todisk.sh**. Then:

[LIST]
[*]replace both occurrences of "rsync -a" with "rsync -aq" to tell rsync to be quiet.
[*]Comment out the line:
[/LIST]


```
echo " * Copying $MODULETORAMFILE to RAM" 1>/dev/console
```

Save the file, switch back to the terminal where the script is paused and continue running it (press enter). That should take care of all the messages intentionally placed there by live-boot. There are still 2 error messages that will remain:

```

expr: syntax error
sh: bad number
```

After a couple of hours of trying to find where they were coming from, I'm still not sure - all I know is it's one of the scripts.

---

### Post by terminator14 on 2013-03-18
```
expr: syntax error
sh: bad number
```

The new version of the script now hides these errors.

Also, for those interested, there is now a Mint 14 version of the script in the git repo.

---

### Post by schragge on 2013-03-18
> **terminator14 said:**
> ```
expr: syntax error
sh: bad number
```But why would you use *expr* at all? Since you're using *awk* anyway why won't you do arithmetics directly in *awk*?
```
ls -la ${MODULETORAMFILE} | awk '{print int($5/1024)+5000}'
```

---

### Post by terminator14 on 2013-03-18
> **schragge said:**
> But why would you use *expr* at all? Since you're using *awk* anyway why won't you do arithmetics directly in *awk*?
```
ls -la ${MODULETORAMFILE} | awk '{print int($5/1024)+5000}'
```

I did not write that code - that code is part of the live-boot package, which I am not a developer of. All I did was add "2>/dev/null" to the 2 lines that were displaying the errors. I'm sure you're right, but that's something the developers of live-boot would have to fix.

---

### Post by usuallywin on 2013-05-15
Sorry for the silly question:

Why do we need the rchroot?  Does rupdate deal with everything, including /etc or /sys?

And reading the "[Making Ubuntu Insanely Fast using RAM]("http://ubuntuforums.org/showthread.php?t=1499338")", why do we need to mount and unmount /sys /proc /dev for the update, isn't easier to create a [COLOR=#000000][FONT=Ubuntu Mono]squashfs [/FONT][/COLOR]directly based on the ram session and save it under [COLOR=#000000][FONT=Ubuntu Mono]/live/filesystem.squashfs[/FONT][/COLOR]?

Thanks

---

### Post by terminator14 on 2013-05-15
> **usuallywin said:**
> Sorry for the silly question:

Why do we need the rchroot?  Does rupdate deal with everything, including /etc or /sys?


rupdate does updates. If the updates make changes to files under /etc, or anywhere else on the filesystem, then rupdate makes sure that those changes do get included in the squashfs image.
rchroot is for custom changes. Say you wanted to make some changes to config files under /etc. rupdate would not wait for you to do so, and any changes made in the RAM Session's filesystem are ignored. rchroot on the other hand gives you a shell inside the RAM_Session, where anything you change will be saved. It makes /var/squashfs/ (located on the Orignal OS) your shell's root, and when you exit the shell, it automatically recreates the squashfs image. Basically without it, you would have to either boot into your original OS, or mount it, and modify files under /var/squashfs before recreating the squashfs image.

> **usuallywin said:**
> And reading the "[Making Ubuntu Insanely Fast using RAM]("http://ubuntuforums.org/showthread.php?t=1499338")", why do we need to mount and unmount /sys /proc /dev for the update, isn't easier to create a [COLOR=#000000][FONT=Ubuntu Mono]squashfs [/FONT][/COLOR]directly based on the ram session and save it under [COLOR=#000000][FONT=Ubuntu Mono]/live/filesystem.squashfs[/FONT][/COLOR]?

Thanks

Honestly, I wrote the script so long ago, I'm not even sure why I designed it that way. These days, I just fix small bugs in it when people find them, and answer questions. I think it's designed this way because:

During the first run of the script, there is no RAM Session, so /var/squashfs has to be created. Later, it's used to create the squashfs image. Once that's done, I never thought of taking it a step further and removing the /var/squashfs directory completely and just using the RAM Session as the source for the squashfs image.

Or maybe at some point I did consider it for a moment, but I was thinking that the downside of having the RAM Session be the source for the squashfs image is the increased risk of unrecoverable corruption. Eg. If you were in the middle of creating your squashfs image from your RAM Session, with the RAM Session being the source, and the power went out, you would have a useless, partially built squashfs image, and no RAM Session (since powering off the machine would have killed it). That scenario is easily fixed however by keeping the old squashfs in place during the update until the new one is created and ready to go (which my script does now, but this was not included with the original version), but maybe that hadn't occurred to me at the time.

---

### Post by usuallywin on 2013-05-15
Thank you for answering someone with "First cup of Ubuntu".  I registered just to ask that question

> **terminator14 said:**
> Say you wanted to make some changes to config files under /etc. rupdate would not wait for you to do so, and any changes made in the RAM Session's filesystem are ignored. 


When you say rupdate would not wait for you, what do you mean?  Is it used when you want to change only one thing in the source without saving everything in the ram session.  Or it is for another more important purpose.

> **terminator14 said:**
> [COLOR=#000000]Or maybe at some point I did consider it for a moment, but I was thinking that the downside of having the RAM Session be the source for the squashfs image is the increased risk of unrecoverable corruption.
[/COLOR]

I had that idea because I guess creating an image in ram session is faster.  A ram-hdd operation maybe a few times faster than a hdd-hdd one.  And with that speed, maybe it is possible to rupdate regularly in short intervals, and function like a normal OS.

---

### Post by terminator14 on 2013-05-15
> **usuallywin said:**
> Thank you for answering someone with "First cup of Ubuntu".  I registered just to ask that question

I hadn't noticed your "rank" - I never look. Everyone's questions are valid and worth answering.

> **usuallywin said:**
> When you say rupdate would not wait for you, what do you mean?  Is it used when you want to change only one thing in the source without saving everything in the ram session.  Or it is for another more important purpose.

rupdate runs "apt-get update && apt-get upgrade" - aka updates on the RAM Session. Running this in a terminal window inside the RAM session has no effect, since any updates done that way would be undone immediately after a reboot, so rupdate is the proper way to update the RAM session with new packages.

> **usuallywin said:**
> I had that idea because I guess creating an image in ram session is faster.  A ram-hdd operation maybe a few times faster than a hdd-hdd one.  And with that speed, maybe it is possible to rupdate regularly in short intervals, and function like a normal OS.

Could be something to that. If anyone ever re-creates my script, or if I wake up one day and decide that I have a few hours/days to kill on something I will probably never use (I don't use my own script since I got the SSDs), that might be something to look into. For now, I just fix its bugs.

---

### Post by usuallywin on 2013-05-15
> **terminator14 said:**
> 
rupdate runs "apt-get update && apt-get upgrade" - aka updates on the RAM Session. Running this in a terminal window inside the RAM session has no effect, since any updates done that way would be undone immediately after a reboot, so rupdate is the proper way to update the RAM session with new packages.


Sorry I think I have asked my question in a confusing way.  If rupdate handles all that, when should rchroot be used?  Is that when you want to change things in the source without saving the current ram session?  Or it is for something else.

---

### Post by terminator14 on 2013-05-15
The current RAM Session never gets saved. The /home partition from the current RAM session gets saved if it's mounted rather than being part of the squashfs image, but not the filesystem itself.

**rupdate:** updates the OS
**rchroot:** lets you modify the OS by letting you change the source of the squashfs image (/var/squashfs) and recreate the image

---

### Post by usuallywin on 2013-05-15
> **terminator14 said:**
> The current RAM Session never gets saved. The /home partition from the current RAM session gets saved if it's mounted rather than being part of the squashfs image, but not the filesystem itself.

**rupdate:** updates the OS
**rchroot:** lets you modify the OS by letting you change the source of the squashfs image (/var/squashfs) and recreate the image

Oh i get it.  So if i add a .txt file to / and click rupdate, i will not see it again if i reboot.  I have to use rchroot for that.  

So if i follow my last idea of making image based on the running ram session, I dont have to rchroot for making changes.  Is that accurate? 
 
Is that ok if i work on that based on your script?

---

### Post by terminator14 on 2013-05-15
> **usuallywin said:**
> Oh i get it.  So if i add a .txt file to / and click rupdate, i will not see it again if i reboot.  I have to use rchroot for that.

Yes.

> **usuallywin said:**
> So if i follow my last idea of making image based on the running ram session, I dont have to rchroot for making changes.  Is that accurate?

Yup
 
> **usuallywin said:**
> Is that ok if i work on that based on your script?

Sure, go ahead

---

### Post by sinekonata on 2013-05-24
Hi, first of all let me thank you for the effort you've put into making,  updating and sharing this script. As a big proponent of community based  economy/society it really means a whole lot to people like me :D

I  am trying to build a new system and was looking about either getting 8  or 16 GB or RAM and found this thread. I guess 8 GB is more than enough  to fit all of the OS as you said was the point of the project. Is 16GB  still worth it overall?
But furthermore is it still worth it if this  build includes a 250GB SSD for all my basic system and home files? The  42 coefficient you talked about would be greatly reduced right?
Also I  will be getting an FX-8350 CPU which is extremely fast, so would it be  worth to use this method overall or should I wait until it's outdated  and slow again?

---

### Post by terminator14 on 2013-05-24
> **sinekonata said:**
> Hi, first of all let me thank you for the effort you've put into making,  updating and sharing this script. As a big proponent of community based  economy/society it really means a whole lot to people like me :D

Always great to be appreciated :)

> **sinekonata said:**
> I  am trying to build a new system and was looking about either getting 8  or 16 GB or RAM and found this thread. I guess 8 GB is more than enough  to fit all of the OS as you said was the point of the project. Is 16GB  still worth it overall?

Many people, especially gamers, keep buying more and more RAM, as traditionally, RAM was the cheapest upgrade you could make to your PC, and the one that could potentially make a huge impact. At a certain point though, you have too much RAM. The only reasons I can think of to have more than 6GB of RAM is

1) Make sure you have enough RAM to future-proof your machine for another 10 years
2) Professional Photo/Video editing
3) Running multiple virtual machines on your PC
4) Some type of AutoCAD development
5) Being a scientist who work with huge databases that must reside in RAM
6) Some sort of huge database developer

Unless you fall within one of those categories, 16GB of RAM is a waste of money - at least in my opinion. The most hardcore of gamers won't need that much RAM for at least another 10 years. Even the new consoles that were recently announced (XBOX One and PS4) will only have 8GB of RAM, and even that will be shared between the CPU and GPU.

> **sinekonata said:**
> But furthermore is it still worth it if this  build includes a 250GB SSD for all my basic system and home files?

The reason I stopped using this script on my own computer was because the hassle of maintaining a RAM Session was not worth the speed difference between it, and simply running your OS from an SSD. If you already have an SSD, the only reason to use this script is to tell your friends that you do. You won't notice the difference between this and an SSD - not without benchmarks.

> **sinekonata said:**
> The  42 coefficient you talked about would be greatly reduced right?

An SSD like the Intel 520 Series, when connected to a SATA III controller, can read at about 550MB/s, and write at about 520MB/s - at least according to Intel. If you are comparing that speed to the same DDR2-533 RAM I did a comparison to earlier, than yes, the RAM will be about 8 times faster than the SSD. These days, you are more likely to have some DDR3 however, and depending on the RAM you have, DDR3 can be anywhere from 6GB/s to 17GB/s (according to this wiki: [http://en.wikipedia.org/wiki/DDR3_SDRAM](http://en.wikipedia.org/wiki/DDR3_SDRAM)), so if you really want to compare how much faster your RAM is than your SSD, you need to know how fast your SSD is, and what type of RAM you have and how fast it is.

> **sinekonata said:**
> Also I  will be getting an FX-8350 CPU which is extremely fast, so would it be  worth to use this method overall or should I wait until it's outdated  and slow again?

This script works better on computers that have regular drives, a fairly decent CPU, and a bit of RAM. Anyone who car afford an SSD (which these days is anyone who can afford a PC) would likely be better off with that.

---

### Post by sinekonata on 2013-05-24
>  The reason I stopped using this script on my own computer was because  the hassle of maintaining a RAM Session was not worth the speed  difference between it, and simply running your OS from an SSD. If you  already have an SSD, the only reason to use this script is to tell your  friends that you do. You won't notice the difference between this and an  SSD - not without benchmarks.

Because of the  paragraph you wrote next to that one, I had to find out that my average Samsung 840 SSD should  have 475-R and 250-W MB/s speeds whereas my Corsair Vengeance has a 20  GB/s bandwidth, so the "42 factor" is actually still on the money :D
So what you say here is that SSD is so fast that even 42 times faster makes no difference to my experience? If it doesn't make a difference, most of what follows is obsolete. Although if it does now or will in 5 years, as software grows heavier, should I need 16GB just for the sake using that difference to the max?

> 1) Make sure you have enough RAM to future-proof your machine for another 10 years
2) Professional Photo/Video editing
3) Running multiple virtual machines on your PC

1. I'm aiming for 5 years. And that is actually my main concern since with my current 4GB I already generally go over 85% +  25% SWAP making my session terribly slow. I can't imagine that programs/OSs won't double their needs in RAM over 5 years.
2. Amateur and very occasional Video editing only.
3. Never more than 2 VMs but, occasionally, yes. And let's say I don't want to dual-boot and feel my system can hanle a 2GB+ windows7 permanently active? 8GB won't be enough then, right?

One more thing is I believe Ubuuntu/Linux will always try to use the most RAM it can, right? And my "/" dir is 15.9GB exactly :D (excluding /home ofc). So the default Linux should normally automatically make use of 16 GB (as opposed to waste it and my money). And even if not maybe I install "preload" or some kind of script like yours (RAM drive is it?) or simpler to force it to.

At any rate the rest of your answer is very instructive stuff, thanks.

---

### Post by terminator14 on 2013-05-26
> **sinekonata said:**
> Because of the  paragraph you wrote next to that one, I had to find out that my average Samsung 840 SSD should  have 475-R and 250-W MB/s speeds whereas my Corsair Vengeance has a 20  GB/s bandwidth, so the "42 factor" is actually still on the money :D
So what you say here is that SSD is so fast that even 42 times faster makes no difference to my experience? If it doesn't make a difference, most of what follows is obsolete. Although if it does now or will in 5 years, as software grows heavier, should I need 16GB just for the sake using that difference to the max?



1. I'm aiming for 5 years. And that is actually my main concern since with my current 4GB I already generally go over 85% +  25% SWAP making my session terribly slow. I can't imagine that programs/OSs won't double their needs in RAM over 5 years.
2. Amateur and very occasional Video editing only.
3. Never more than 2 VMs but, occasionally, yes. And let's say I don't want to dual-boot and feel my system can hanle a 2GB+ windows7 permanently active? 8GB won't be enough then, right?

Sounds like you do legitimately require plenty of RAM, especially with you running a Windows 7 VM permanently. If I had tons of RAM, I would imagine that 4GB for the host and 4GB for the Windows 7 VM would be enough, but you say that 4GB for your host isn't enough, and if you needed a second VM to run, or wanted to make sure any future needs you have won't require more RAM, I guess 12-16 GB might make sense in your case.

> **sinekonata said:**
> One more thing is I believe Ubuuntu/Linux will always try to use the most RAM it can, right? And my "/" dir is 15.9GB exactly :D (excluding /home ofc). So the default Linux should normally automatically make use of 16 GB (as opposed to waste it and my money). And even if not maybe I install "preload" or some kind of script like yours (RAM drive is it?) or simpler to force it to.

At any rate the rest of your answer is very instructive stuff, thanks.

Yes, by default, Linux will try to make full use of your RAM, but it does this as you go. When you run a program, linux loads it, and its libraries to RAM, and keeps it there even after the program is terminated so that if you decide to run the program again shortly after, it doesn't have to load it from disk again. If you start running low on RAM, it will start replacing older cached information in RAM, but if you have 16GB, it should keep caching everything as you keep using it. Like you said, programs like preload make sure that linux doesn't wait for you to run a program before caching it in RAM. Ex: If you tell it to cache firefox, it will do so immediately on boot, so if you run it a minute later, it will already be in RAM. This is a much cleaner way to do things than my script.

---

### Post by ifoo1337 on 2013-06-02
Has somebody tried this on 13.04 yet?

EDIT: Works fine on Xubuntu 13.04 amd64.

---

### Post by terminator14 on 2013-06-03
> **ifoo1337 said:**
> Has somebody tried this on 13.04 yet?

EDIT: Works fine on Xubuntu 13.04 amd64.

Cool. Thanks for letting us know.

---

### Post by smanet on 2013-07-01
Works with Lubuntu 13.04 and latest updates.
In addition, my home is included in the process (not a separate partition) and encrypted.
I like to save what I need in another mounted partition :)
I'm running everything on a 32 GB flash drive.
thank you! this script is wonderful :)

---

### Post by terminator14 on 2013-07-01
> **smanet said:**
> Works with Lubuntu 13.04 and latest updates.
In addition, my home is included in the process (not a separate partition) and encrypted.
I like to save what I need in another mounted partition :)
I'm running everything on a 32 GB flash drive.

I hadn't tested the script with an encrypted /home before - nice to hear it works. Also cool that the 12.10 script still works on 13.04. Maybe I'll run it once or twice to make sure there's no minor changes I need, and add a 13.04 script, or just rename the 12.10 one. Thanks.

> **smanet said:**
> thank you! this script is wonderful :)

No problem :)

---

### Post by smanet on 2013-07-08
> **terminator14 said:**
> I hadn't tested the script with an encrypted /home before - nice to hear it works. Also cool that the 12.10 script still works on 13.04. Maybe I'll run it once or twice to make sure there's no minor changes I need, and add a 13.04 script, or just rename the 12.10 one. Thanks.



No problem :)

I'm quite new to Linux on RAM. I have 16 GB on my computer and I see that when my system came up, it took half ram has drive and the other half for programs.
I tried in a virtual machine and I got the same behaviour. As I don't need so much RAM for the filesystem, is there a possibility to allocate, for example, just 4 GB to the virtual filesystem?
Thank you again :)

---

### Post by terminator14 on 2013-07-08
> **smanet said:**
> I'm quite new to Linux on RAM. I have 16 GB on my computer and I see that when my system came up, it took half ram has drive and the other half for programs.
I tried in a virtual machine and I got the same behaviour. As I don't need so much RAM for the filesystem, is there a possibility to allocate, for example, just 4 GB to the virtual filesystem?
Thank you again :)

It's been a busy day, but I took a quick look and it appears that this is what's causing it:

[QUOTE=http://manpages.ubuntu.com/manpages/oneiric/live-boot.7..html]
       ramdisk-size
           This parameters allows to set a custom ramdisk size (it's  the  '-o
           size'  option of tmpfs mount). By default, there is no ramdisk size
           set, so the default of mount applies (currently  50%  of  available
           RAM). Note that this option has no currently no effect when booting
           with toram.
[/QUOTE]

Not sure if that last sentence applies in our case or not, but it sounds like what's happening. When I get some free time, I'll see if I can find where to set the parameter, and see if I can build it into the script.

---

### Post by smanet on 2013-07-09
> **terminator14 said:**
> It's been a busy day, but I took a quick look and it appears that this is what's causing it:



Not sure if that last sentence applies in our case or not, but it sounds like what's happening. When I get some free time, I'll see if I can find where to set the parameter, and see if I can build it into the script.

It's that for sure, as said I see this behaviour with any amount of RAM.
It's just annoying to "loose" 8 GB in filesystem :)
Anyway, take your time! I will also investigate if it's possible to setup a variable (maybe in GRUB?) to change that.
Thanks!

---

### Post by terminator14 on 2013-07-10
> **smanet said:**
> It's that for sure, as said I see this behaviour with any amount of RAM.
It's just annoying to "loose" 8 GB in filesystem :)
Anyway, take your time! I will also investigate if it's possible to setup a variable (maybe in GRUB?) to change that.
Thanks!

It took a bit of digging, but I think I got it. Assuming that you already ran the script, here's what you do from within the RAM session:

```
$ sudo rchroot -O	#Mounts the original OS. You could just reboot into the original OS and skip this step
$ vim /lib/live/boot/9990-overlay.sh

[INDENT]Change:

cow_mountopt="rw,noatime,mode=755"

to read:

cow_mountopt="rw,noatime,mode=755,size=16384M"[/INDENT]

$ update-initramfs -u
$ exit			#Now we exit the chroot
Reboot
```

I would imagine that values such as size=16G would work too, but I've only tried it in megabytes.
You may need to give it a bit less than 16 gigs, so try a few values and see how big you can get it without it dying on you.

If the RAM Session becomes unbootable, boot into your original OS and run the steps above again without the rchroot bit, as that's basically what you're doing.

Let me know if that works, and I'll see if I can add an option to the script to automate this.

---

### Post by smanet on 2013-07-19
Sorry, I was busy with the work and I didn't have time to look in here.
Basically, what's doing that command?
If I understood properly, shouldn't be the definition of the size of tmpfs?
If yes, I think that in there I should specify likely 2G in my case (that is the current size of my tempfs + some little space for normal operation).
Am I correct?
In this way, I will have the other entire RAM free for programs execution.
Also, I'm booting the system from a USB stick and if I just specify the size of the filesystem, it will run correctly in diverse systems.
Thank you again :)

---

### Post by terminator14 on 2013-07-19
The size of your root (/) mount point (where you are saving files to) is specified by the option I mentioned in the previous post. This seems to be an option for a mount command that the initrd ramdisk runs, and that is the easy way of modifying it without extracting and modifying the ram disk directly. Even if you set it to 16GB, if you only use a portion of that 16GB to save files, it will use the rest of that space for RAM. Yes, this does seem a bit unsafe in that if you write too much data to your RAM, you might run out of space for actual RAM to be used by programs, so a lower value than your max ram (16GB) would be advisable. Try it and see what values work.

---

### Post by smanet on 2013-07-19
I understood. I will try later on to change the size of it. I will try to give the minimum required to be operational, I think 3/4 GB are more than sufficient. And inter-portable too between current systems.
I think it will be a good idea to ask, during the process, how much RAM you will dedicate for your FS (maybe after guessing how much will be the SQUASHFS).
I will update soon! thanks again :)

---

### Post by wfchEbC on 2013-08-19
Is there a way to get this to work using a PXE server? This would allow me to have multiple clients using one image that boots into RAM.

---

### Post by terminator14 on 2013-08-21
> **wfchEbC said:**
> Is there a way to get this to work using a PXE server? This would allow me to have multiple clients using one image that boots into RAM.

Sorry for the late reply - I just noticed the email that said someone posted to this thread.

I actually have never had occasion to use PXE, so I have no idea how it works, or if what you are asking is possible. Maybe someone who knows a bit more about it can answer your question.

---

### Post by abhinav.kssk on 2013-09-05
> **terminator14 said:**
> Sorry for the late reply - I just noticed the email that said someone posted to this thread.

I actually have never had occasion to use PXE, so I have no idea how it works, or if what you are asking is possible. Maybe someone who knows a bit more about it can answer your question.

@terminator14

is there a ubuntu 13.04 version of the script? or can i use the 12.10 version script itself?

---

### Post by terminator14 on 2013-09-05
> **abhinav.kssk said:**
> @terminator14

is there a ubuntu 13.04 version of the script? or can i use the 12.10 version script itself?

There is no 13.04 version yet. I'll see if I can give 13.04 a try and update the script, but that might take a while. If you want to try the 12.10 version of the script on Ubuntu 13.04, I suggest you do so in a virtual machine first (to make sure it actually works) - otherwise, give me a few days and I might release a 13.04 version.

---

### Post by koen2 on 2013-09-06
> **terminator14 said:**
> There is no 13.04 version yet. I'll see if I can give 13.04 a try and update the script, but that might take a while. If you want to try the 12.10 version of the script on Ubuntu 13.04, I suggest you do so in a virtual machine first (to make sure it actually works) - otherwise, give me a few days and I might release a 13.04 version.

I'd like to second the request for a 13.04 version of the script, it would really be awesome!:)

---

### Post by terminator14 on 2013-09-07
13.04 version uploaded

---

### Post by AJ12Gamer on 2013-10-18
> **terminator14 said:**
> 13.04 version uploaded

13.10 is out. Can you do one for that one too please? Thank you.

---

### Post by terminator14 on 2013-10-18
> **AJ12Gamer said:**
> 13.10 is out. Can you do one for that one too please? Thank you.

I'll look into it.

---

### Post by terminator14 on 2013-10-20
> **AJ12Gamer said:**
> 13.10 is out. Can you do one for that one too please? Thank you.

13.10 version uploaded

---

### Post by AJ12Gamer on 2013-10-23
> **terminator14 said:**
> 13.10 version uploaded

Wow that was fast! Thank you so much! Can you make one that will work with Lubuntu 13.10? Thanks man your the best! ):P

---

### Post by terminator14 on 2013-10-23
> **AJ12Gamer said:**
> Wow that was fast! Thank you so much! Can you make one that will work with Lubuntu 13.10? Thanks man your the best! ):P

I've never used Lubuntu, but I figured I'd give it a try with my script.
I figured even if everything worked perfectly, at the very least, I would need to change a few aesthetic things like:

[LIST]
[*]Grub menu should say Lubuntu instead of Ubuntu
[*]Version check should account for the fact that /etc/issue might say Lubuntu instead of Ubuntu
[*]
[/LIST]

but nope. Not a single thing needed changing. It ran perfectly.
Now there might be something wrong and I'm just not seeing it (my testing wasn't very extensive), but as far as I can figure, it works exactly the same as regular Ubuntu.

---

### Post by AJ12Gamer on 2013-10-23
> **terminator14 said:**
> I've never used Lubuntu, but I figured I'd give it a try with my script.
I figured even if everything worked perfectly, at the very least, I would need to change a few aesthetic things like:

[LIST]
[*]Grub menu should say Lubuntu instead of Ubuntu
[*]Version check should account for the fact that /etc/issue might say Lubuntu instead of Ubuntu
[/LIST]

but nope. Not a single thing needed changing. It ran perfectly.
Now there might be something wrong and I'm just not seeing it (my testing wasn't very extensive), but as far as I can figure, it works exactly the same as regular Ubuntu.

When I ran the script with lubuntu everything went perfect until I installed pptview and rebooted.
initramfs came up. :/ what could be the cause?
Please help.

---

### Post by terminator14 on 2013-10-23
> **AJ12Gamer said:**
> When I ran the script with lubuntu everything went perfect until I installed pptview and rebooted.
initramfs came up. :/ what could be the cause?
Please help.

I just installed pptview without any problems. This is the procedure I followed:

```
#Boot into RAM Session
$ sudo rchroot -R
# apt-get install pptview
# exit
```

At this point, it actually failed to unmount the device because it was being used
All I did was reboot, booting back into the RAM Session. Since the install was done to /var/squashfs of the original OS, it's still there - it just hasn't been added to the filesystem.squashfs image yet

Now recreate the squashfs image:

```
$ sudo rupdate --force
$ sudo reboot

```

Is that what you did?

---

### Post by apa2 on 2013-10-23
I've installed Preload or whatever it's called, is it okay to do this method as well at the same time? Or will that cause problems and issues? Also, where are the versions for 13.10 Ubuntu and more clear instruction? Thanks

---

### Post by terminator14 on 2013-10-23
> **apa2 said:**
> I've installed Preload or whatever it's called, is it okay to do this method as well at the same time? Or will that cause problems and issues?

> **http://en.wikipedia.org/wiki/Preload_%28software%29]preload is a free Linux program written by Behdad Esfahbod which runs as a daemon and records statistics about usage of programs using Markov chains said:**
> 

My script loads everything on the OS into RAM during bootup. What's the point of running preload (which puts the most commonly used programs into RAM) if everything is already in RAM?

[QUOTE=apa2;12826053]Also, where are the versions for 13.10 Ubuntu

See **Download** section of the first post of this thread.

> **apa2 said:**
> and more clear instruction?

More clear? The first post outlines the history of the project, what the script does, who it's for, what it will run on, how it does what it does, what the development of it was like, and where to get the script. The script itself explains the rest. What is there left to explain?

---

### Post by apa2 on 2013-10-23
> **terminator14 said:**
> My script loads everything on the OS into RAM during bootup. What's the point of running preload (which puts the most commonly used programs into RAM) if everything is already in RAM?

Oh, okay. Sorry, I'm new to the whole Ubuntu OS, and learning as I go. At this point I'm trying to install helpful things for my system/OS to run faster, better performance and etc. So I guess I'll have to uninstall preload, and install your script.. :) 


> **terminator14 said:**
> 
See **Download** section of the first post of this thread.


Thanks! :)


> **terminator14 said:**
> 
More clear? The first post outlines the history of the project, what the script does, who it's for, what it will run on, how it does what it does, what the development of it was like, and where to get the script. The script itself explains the rest. What is there left to explain?

Sorry, bad choice of words. I just see this thread with 22/23 pages deep, and new Ubuntu versions available, and so many pages of replies holding different information and I guess I just assumed there was a page some where with "comments disabled" that shows the instructions for each Ubuntu version, how to install it, if any special info and instructions per each version of Ubuntu. For example, me coming from Windows 7 OS, a certain script / modification to help the system run better and faster, there would be different steps and different instructions for each flavor of Windows OSes... Because each OS version might handle things and scripts differently. Again, sorry for not understanding, as I'm new to all this Ubuntu stuff. :)

---

### Post by terminator14 on 2013-10-23
> **apa2 said:**
> I just see this thread with 22/23 pages deep, and new Ubuntu versions available, and so many pages of replies holding different information and I guess I just assumed there was a page some where with "comments disabled" that shows the instructions for each Ubuntu version, how to install it, if any special info and instructions per each version of Ubuntu.

The 20+ pages are just discussions of ideas people have, problems they run into, and requests for new versions. The main page that has all the info about the script is just the first post of this thread. Anything that doesn't cover, the script does. It's interactive and pretty much explains what it's doing the entire time. There is no separate page for each version.

> **apa2 said:**
> For example, me coming from Windows 7 OS, a certain script / modification to help the system run better and faster, there would be different steps and different instructions for each flavor of Windows OSes... Because each OS version might handle things and scripts differently. Again, sorry for not understanding, as I'm new to all this Ubuntu stuff. :)

When you are talking about versions of Windows, like say the difference between Wndows XP and Windows Vista, you are talking about a complete rewrite of the operating system over the course of 6 years where WIndows XP code was not used in Vista at all. Windows 7 came 2 years after Windows Vista. Ubuntu on the other hand updates every 6 months. My point is that in the Windows world, when the OS updates, the changes have been pretty massive in the past because they had years to implement them. In contrast, half the time, when I "release a new version of my script" after Ubuntu updates to, say version 13.10, I just run the previous version of my script on it (13.04 in this case) to make sure it still works, change the version of the OS the script is expecting to find, and the name of the file. The script works pretty much exactly the same from version to version since I wrote it in 2010. This is why each version doesn't have it's own README. For anyone that really wants to know what's changed, they can always read the [git]("https://en.wikipedia.org/wiki/Git_%28software%29") logs that I left behind.

---

### Post by apa2 on 2013-10-23
> **terminator14 said:**
> The 20+ pages are just discussions of ideas people have, problems they run into, and requests for new versions. The main page that has all the info about the script is just the first post of this thread. Anything that doesn't cover, the script does. It's interactive and pretty much explains what it's doing the entire time. There is no separate page for each version.

okay, gotcha! thank you! :) 

> **terminator14 said:**
> 
When you are talking about versions of Windows, like say the difference between Wndows XP and Windows Vista, you are talking about a complete rewrite of the operating system over the course of 6 years where WIndows XP code was not used in Vista at all. Windows 7 came 2 years after Windows Vista. Ubuntu on the other hand updates every 6 months. My point is that in the Windows world, when the OS updates, the changes have been pretty massive in the past because they had years to implement them. In contrast, half the time, when I "release a new version of my script" after Ubuntu updates to, say version 13.10, I just run the previous version of my script on it (13.04 in this case) to make sure it still works, change the version of the OS the script is expecting to find, and the name of the file. The script works pretty much exactly the same from version to version since I wrote it in 2010. This is why each version doesn't have it's own README. For anyone that really wants to know what's changed, they can always read the [git]("https://en.wikipedia.org/wiki/Git_%28software%29") logs that I left behind.

yeah true, I just didn't know how often Ubuntu pushed out updates and didn't know the OS is basically kept the same, with each update push. Another reason why I'm loving Ubuntu versus Windows! Lol! :) :D I'll be sure to install your app/script then and thanks for your replies!

---

### Post by AJ12Gamer on 2013-10-24
> **terminator14 said:**
> I just installed pptview without any problems. This is the procedure I followed:  ```
#Boot into RAM Session $ sudo rchroot -R # apt-get install pptview # exit
```  At this point, it actually failed to unmount the device because it was being used All I did was reboot, booting back into the RAM Session. Since the install was done to /var/squashfs of the original OS, it's still there - it just hasn't been added to the filesystem.squashfs image yet  Now recreate the squashfs image:  ```
$ sudo rupdate --force $ sudo reboot 
```  Is that what you did?  I actually uninstalled ram booster then installed pptview then installed ram booster again.  But I will take note of this so I won't mess up again.  Thanks man! :)

---

### Post by AJ12Gamer on 2013-10-29
> **terminator14 said:**
> I just installed pptview without any problems. This is the procedure I followed:

```
#Boot into RAM Session
$ sudo rchroot -R
# apt-get install pptview
# exit
```

At this point, it actually failed to unmount the device because it was being used
All I did was reboot, booting back into the RAM Session. Since the install was done to /var/squashfs of the original OS, it's still there - it just hasn't been added to the filesystem.squashfs image yet

Now recreate the squashfs image:

```
$ sudo rupdate --force
$ sudo reboot

```

Is that what you did?

So I tried finished ram booster with Mplayer installed.
Then uninstalled Mplayer using what you provided above and rebooted.
Mplayer is still installed.

What did I do wrong?

---

### Post by terminator14 on 2013-10-29
> **AJ12Gamer said:**
> So I tried finished ram booster with Mplayer installed.
Then uninstalled Mplayer using what you provided above and rebooted.
Mplayer is still installed.

What did I do wrong?

To permanently uninstall a package from within the RAM session, you run:

```
$ sudo rchroot -R
# apt-get remove mplayer
# exit
$ sudo rupdate --force
$ sudo reboot
```

Is this what you did?

---

### Post by AJ12Gamer on 2013-11-04
> **terminator14 said:**
> To permanently uninstall a package from within the RAM session, you run:

```
$ sudo rchroot -R
# apt-get remove mplayer
# exit
$ sudo rupdate --force
$ sudo reboot
```

Is this what you did?

At first I didn't do the "sudo rchroot -R"
Then when I tried again with "sudo rchroot -R" it says mplayer is not installed but it is still installed.

I am just going to uninstall RAM booster and start over for the second time.

Also I just tried

$ sudo rchroot -R
# apt-get remove simple-scan
# exit
$ sudo rupdate --force
$ sudo reboot

Same thing still installed!

---

### Post by terminator14 on 2013-11-04
> **AJ12Gamer said:**
> At first I didn't do the "sudo rchroot -R"
Then when I tried again with "sudo rchroot -R" it says mplayer is not installed but it is still installed.


Nothing you do in the RAM session has any impact on what's installed and what's not installed on the filesystem.squashfs image. Just because you ran:

```
sudo apt-get install mplayer
```

in the RAM Session doesn't mean "sudo rchroot -R" (the squashfs image) will have it installed. 
There are 2 ways to install stuff: temporarily and permanently.

**Temporarily:**

If you want mplayer, or any package, to be installed temporarily, you can install it as you normally would on any Ubuntu system (sudo apt-get install mplayer). This will be undone as soon as you reboot. This also has no impact on the squashfs image.

**Permanently:**

If you want it to be permanently installed (still there when you reboot), you run "sudo rchroot -R" and install it there. Then you recreate the squashfs image with rupdate. Similarly, if you already added mplayer to the squashfs image and want to remove it, running "sudo apt-get remove mplayer" is temporary. To remove it permanently, you NEED to do it through "rchroot -R".

---

### Post by leepe on 2013-11-04
I'm running lubuntu right now. I have 4 GB of RAM, and could run Ubuntu, but lubuntu just gives me more speed. I tried running the script with 3 different terminals and still no results. I get a terminal window for an instant, and then it instantly quits out. hmm...  In retrospect, is it safe for me to run the script in the first place? Just a question in passing...

---

### Post by terminator14 on 2013-11-04
> **romain_astie2 said:**
> I'm running lubuntu right now. I have 4 GB of RAM, and could run Ubuntu, but lubuntu just gives me more speed. I tried running the script with 3 different terminals and still no results. I get a terminal window for an instant, and then it instantly quits out. hmm...

You're double clicking the file?

```
git clone https://github.com/terminator14/RAM_booster.git
cd RAM_booster
sudo ./RAM_booster_Ubuntu_13.10.sh
```

Assuming you're running lubuntu 13.10, and not an older one.

> **romain_astie2 said:**
> In retrospect, is it safe for me to run the script in the first place? Just a question in passing...

See [http://ubuntuforums.org/showthread.php?t=1594694&page=22&p=12825607#post12825607]("http://ubuntuforums.org/showthread.php?t=1594694&page=22&p=12825607#post12825607")

---

### Post by leepe on 2013-11-04
sudo ./ worked fro some reason when anything else did not. go figure... :) 
thanks for the awesome script!

---

### Post by leepe on 2013-11-04
Hmm however, when I try to boot into the RAM session I get this message:
```

/init: .: line 249: can't open '/scripts/live'
[       1.094961] Kernel panic - not syncing: Attempted to kill init! exitcode=0x00000200
[       1.094961]
```
Any insights?

---

### Post by terminator14 on 2013-11-04
> **romain_astie2 said:**
> Hmm however, when I try to boot into the RAM session I get this message:
```

/init: .: line 249: can't open '/scripts/live'
[       1.094961] Kernel panic - not syncing: Attempted to kill init! exitcode=0x00000200
[       1.094961]
```
Any insights?

What version of lubuntu are you running? 13.10? 32bit? 64bit?
Are you using LVM?

---

### Post by leepe on 2013-11-04
lubuntu 13.10 64 bit. Freshly installed and 100% updated last night. Your script runs updates anyways, so I should be all updated. As for LVM (Logical Volume Management, right?) google searches haven't really helped me in seeing what exactly it is and whether i have and use it or not. I haven't changed any default ubuntu settings, what does lubuntu do by default? when I created a partition to store my home folder on, I made it as a primary partition (not a logical partition... is this the key?)with an ext4 filesystem, using gparted.

---

### Post by terminator14 on 2013-11-04
> **romain_astie2 said:**
> lubuntu 13.10 64 bit. Freshly installed and 100% updated last night. Your script runs updates anyways, so I should be all updated. As for LVM (Logical Volume Management, right?) google searches haven't really helped me in seeing what exactly it is and whether i have and use it or not. I haven't changed any default ubuntu settings, what does lubuntu do by default? when I created a partition to store my home folder on, I made it as a primary partition (not a logical partition... is this the key?)with an ext4 filesystem, using gparted.

Yes - logical volume management. It's an option available during OS install. It sounds like you didn't enable it.

I'm going to give lubuntu 13.10 64bit another try - see if I run into the same problem. I'll post back when I do.

---

### Post by terminator14 on 2013-11-04
> **romain_astie2 said:**
> lubuntu 13.10 64 bit. Freshly installed and 100% updated last night. Your script runs updates anyways, so I should be all updated. As for LVM (Logical Volume Management, right?) google searches haven't really helped me in seeing what exactly it is and whether i have and use it or not. I haven't changed any default ubuntu settings, what does lubuntu do by default? when I created a partition to store my home folder on, I made it as a primary partition (not a logical partition... is this the key?)with an ext4 filesystem, using gparted.

Works perfectly for me. This is what I did:

```
Installed lubuntu 13.10 64bit using the default partitions it chose.
Updated the system with:
[INDENT]sudo apt-get update && sudo apt-get upgrade[/INDENT]
Installed git and gparted:
[INDENT]sudo apt-get install git gparted[/INDENT]
Use gparted to create a primary partition that I will use for /home. Also let gparted format it as ext4. 
Download and run the script:
[INDENT]git clone https://github.com/terminator14/RAM_booster.git
cd RAM_booster
sudo ./RAM_booster_Ubuntu_13.10.sh[/INDENT]
Tell it to use the partition we prepared with gparted as /home (/dev/sdb1 in my case - may be different for you)
Pretty much kept everything else default for the script
Let it finish running
Reboot
```

Did you more or less do the same thing?

If so, try this:

```
ls -l /live/
```
and
```
sed -n '/06_RAMSESS/,/06_RAMSESS/p' /boot/grub/grub.cfg
```

and post the output, so I can see if your filesystem.squashfs image actually exists, is where it should be, and what your grub menu entry says.

PS:
> **romain_astie2 said:**
> Your script runs updates anyways
My script updates the list of packages available from the repos - it does NOT update your system. Are you sure your system was up to date when you ran the script?

---

### Post by leepe on 2013-11-05
I'll try repartitioning and re-running the script EXACTLY as you outlined when I get back to my machine. I ran the script the say way you did (as far as I can remember) but I'll double check and post back
thanks again for all the help

UPDATE:  
```
 sed -n '/06_RAMSESS/,/06_RAMSESS/p' /boot/grub/grub.cfg
```
returns:

```
 ### BEGIN /etc/grub.d/06_RAMSESS ###


menuentry "Ubuntu to RAM" {
  set uuid_grub_boot=07835b3a-e5d6-47d5-b3e8-e546ab92d964
  set uuid_os_root=07835b3a-e5d6-47d5-b3e8-e546ab92d964


  search --no-floppy --fs-uuid $uuid_grub_boot --set=grub_boot


  set grub_boot=($grub_boot)


  if [ $uuid_grub_boot == $uuid_os_root ] ; then                 
     set grub_boot=$grub_boot/boot
  fi


  linux $grub_boot/vmlinuz-3.8.0-32-generic bootfrom=/dev/disk/by-uuid/$uuid_os_root boot=live toram=filesystem.squashfs apparmor=0 security="" root=/dev/disk/by-uuid/$uuid_os_root ro quiet splash
  initrd $grub_boot/initrd.img-3.8.0-32-generic
}
### END /etc/grub.d/06_RAMSESS ###


  
```
and then ls -l /live/ returns:
```
total 1051616-rw-r--r-- 1 root root 1076850688 Nov  5 13:03 filesystem.squashfs



```

---

### Post by terminator14 on 2013-11-05
You said that you were running lubuntu 13.10 64bit here:

> **romain_astie2 said:**
> lubuntu 13.10 64 bit. Freshly installed and 100% updated last night.

But according to this:

> **romain_astie2 said:**
> 
```

  linux $grub_boot/vmlinuz-3.8.0-32-generic bootfrom=/dev/disk/by-uuid/$uuid_os_root boot=live toram=filesystem.squashfs apparmor=0 security="" root=/dev/disk/by-uuid/$uuid_os_root ro quiet splash
  initrd $grub_boot/initrd.img-3.8.0-32-generic

```

Your kernel version is 3.8.0-32. The kernel that comes with lubuntu 13.10 64bit, as seen in the screenshot of a totally unupgraded live cd of it, is 3.11.0-12. You appear to be running an older kernel than lubuntu 13.10 64bit comes with. It sounds like you either manually downgraded your kernel, are running an older version than 13.10, or the 13.10 iso has been updated between when you downloaded it and when I downloaded it without being labeled as such. The fact that you are running an older kernel is NOT a reason that it shouldn't work, but it might explain why I can't reproduce the error. If you are indeed running an unmodified (in terms of kernel or initrd image) lubuntu 13.10 64bit, what is the md5 of the iso you used to install it? It it this?:

```
$ md5sum lubuntu-13.10-desktop-amd64.iso 
37afd5ee2c8a9d55b320b4b7781ed6d9  lubuntu-13.10-desktop-amd64.iso
```

---

### Post by smanet on 2013-11-05
Hi Terminator,
I'm really sorry for this long reply. I changed my job and I had to focus in it :)
I just tried your modification and it works beautifully.
For instance, it was this one:

$ sudo rchroot -O    #Mounts the original OS. You could just reboot into the original OS and skip this step
$ vim /lib/live/boot/9990-overlay.sh

Change:

cow_mountopt="rw,noatime,mode=755"

to read:

cow_mountopt="rw,noatime,mode=755,size=16384M"

$ update-initramfs -u
$ exit            #Now we exit the chroot
Reboot

I assigned just 3 GB, I got 3 GB for the / and the rest in tmpfs (3.9GB), over 8 GB.
I'm going to test with the full 16 GB of my Mac Book, but I believe it will be fine.
I will report it in minutes :D
Just happy and I wanted to share!
Thanks!

Update: done the test with 16 GB, still 3 GB reported for the fileystem, 7.9GB for tmpfs.
Memory available was more than 12 GB, with about 2 GB cached and 2,4 GB in use.
I believe that it's fine!

---

### Post by terminator14 on 2013-11-05
> **smanet said:**
> Hi Terminator,
I'm really sorry for this long reply. I changed my job and I had to focus in it :)
I just tried your modification and it works beautifully.
For instance, it was this one:

$ sudo rchroot -O    #Mounts the original OS. You could just reboot into the original OS and skip this step
$ vim /lib/live/boot/9990-overlay.sh

Change:

cow_mountopt="rw,noatime,mode=755"

to read:

cow_mountopt="rw,noatime,mode=755,size=16384M"

$ update-initramfs -u
$ exit            #Now we exit the chroot
Reboot

I assigned just 3 GB, I got 3 GB for the / and the rest in tmpfs (3.9GB), over 8 GB.
I'm going to test with the full 16 GB of my Mac Book, but I believe it will be fine.
I will report it in minutes :D
Just happy and I wanted to share!
Thanks!

Update: done the test with 16 GB, still 3 GB reported for the fileystem, 7.9GB for tmpfs.
Memory available was more than 12 GB, with about 2 GB cached and 2,4 GB in use.
I believe that it's fine!

Awesome :)

---

### Post by leepe on 2013-11-05
> [B]Originally Posted by Terminator14:
[/B][COLOR=#000000]Your kernel version is 3.8.0-32. The kernel that comes with lubuntu 13.10 64bit, as seen in the screenshot of a totally unupgraded live cd of it, is 3.11.0-12. You appear to be running an older kernel than lubuntu 13.10 64bit comes with. It sounds like you either manually downgraded your kernel, are running an older version than 13.10, or the 13.10 iso has been updated between when you downloaded it and when I downloaded it without being labeled as such. The fact that you are running an older kernel is NOT a reason that it shouldn't work, but it might explain why I can't reproduce the error. If you are indeed running an unmodified (in terms of kernel or initrd image) lubuntu 13.10 64bit, what is the md5 of the iso you used to install it? It it this?:[/COLOR]

then why does it come up with this when I run uname -r?
```
3.11.0-12-generic


```

This output shows the same as your screenshot. What's going on?

---

### Post by terminator14 on 2013-11-05
> **romain_astie2 said:**
> then why does it come up with this when I run uname -r?
```
3.11.0-12-generic


```

This output shows the same as your screenshot. What's going on?

My script uses the following code to figure out which versions of the kernel are available on your system:

```
ls /boot/ | grep vmlinuz
```

It then sorts them by version number, and uses the latest version when it's making the grub entry.
It looks like when you ran the script, you had kernel version 3.8.0-32 available on your system (even though you weren't running it), and my script thought that it was a newer version than the 3.11.0-12 kernel you were running, so that's what it chose. Shortly after, your system must have automatically erased the old kernel, since it knew you were no longer using it, and the RAM session wasn't able to boot.

I just fixed the script by improving the code that determines the latest version of the kernel available on your system. Hopefully, this will fix your problem.
Since you already ran the script, run it again as:

```
sudo ./RAM_booster_Ubuntu_13.10.sh --uninstall
```

to remove what it had already done. Then do one of 2 things to get the latest version of the script:

**Option 1:**

Delete the RAM_booster folder and rerun:

```
git clone https://github.com/terminator14/RAM_booster.git
```

to download the latest version, OR

**Option 2:**

cd into the RAM_booster folder
run:

```
git pull
```

After that, you can run the script again, and hopefully this time, it will work.

---

### Post by leepe on 2013-11-06
alright so I got the script working and now I'm running SUPER FAST. So, in order to get new programs with the RAM session, I need to just do the updates normally and then run 'sudo rupdate' before I reboot, in order to 'flush' the changes made in RAM to the hard disk. 
Am I missing anything?
BTW, the script is super awesome, it takes 20s more to load the files at the beginning but then even my biggest programs (massive IDEs) were able to load pretty much instantly. Cool!
Thanks again for all the help, and for the script. It's awesome that you put so much time to make something like this available to the community.

---

### Post by terminator14 on 2013-11-06
> **romain_astie2 said:**
> alright so I got the script working and now I'm running SUPER FAST. So, in order to get new programs with the RAM session, I need to just do the updates normally and then run 'sudo rupdate' before I reboot, in order to 'flush' the changes made in RAM to the hard disk. 
Am I missing anything?

Not quite. Nothing you do in the RAM session has any effect on the squashfs image you boot from. Any programs you install with apt-get, or synaptic package manager are temporary. In order to add a program to the squashfs image, so that it shows up next time you boot into the RAM session, you would first run:

```
sudo rchroot -R
```

this puts you into the environment that the squashfs image is made from. Anything you change here will be added to your squashfs image. So at this point, you can change config files in /etc, or run "apt-get install stuff" to install programs. After you are done here, you exit out of the environment with "exit", and recreate the squashfs image with "sudo rupdate -f". This is the command that uses the environment that you just modified to create the squashfs image that you boot from.

While updating the system can technically be done with something like:
```

$ sudo rchroot -R
[INDENT]# apt-get update[/INDENT]
[INDENT]# apt-get upgrade[/INDENT]
[INDENT]exit[/INDENT]
$ sudo rchroot -O
[INDENT]# mksquashfs /var/squashfs /live/filesystem.squashfs -noappend -always-use-fragments[/INDENT]
[INDENT]# exit[/INDENT]
```

I have simplified it a bit by making the rupdate script. Running:

```
sudo rupdate
```

does this for you. The rupdate also has a few more advanced features that simplify other tasks as well, but being a simple way to update the RAM session with new versions of packages from the repos is its primary purpose.

> **romain_astie2 said:**
> Thanks again for all the help, and for the script. It's awesome that you put so much time to make something like this available to the community.

Always nice to be appreciated :)

---

### Post by shalokshalom on 2013-11-07
Hi there ^_^

I am new here and just create this Account, because of this Thread:
What is the current Status for this Project, please?
Is it possible, to run kubuntu (13.10) from RAM and use my hdd for /home, /etc and so on?

---

### Post by terminator14 on 2013-11-07
> **shalokshalom said:**
> Hi there ^_^

I am new here and just create this Account, because of this Thread:
What is the current Status for this Project, please?
Is it possible, to run kubuntu (13.10) from RAM and use my hdd for /home, /etc and so on?

Version 13.10 is available. It has not been tested on kubuntu, but considering that it wasn't tested until recently on lubuntu either, and pretty much ran perfectly on that, I would say you are unlikely to have any problems. If you try it, and do run into problems, let me know and I might give kubuntu a try to see if I can fix anything. 

/home on hdd is supported (it's one of the main features).
/etc on hdd is not directly supported, but there is an easy way to update the /etc files (and any other files) that get loaded into RAM (by updating the squashfs image that you boot from)

---

### Post by commensal on 2013-11-15
Does it matter if I have btrfs?
Can't boot to RAM image.

---

### Post by terminator14 on 2013-11-16
> **commensal said:**
> Does it matter if I have btrfs?
Can't boot to RAM image.

Off the top of my head, I would say yes - it matters. The script has several places where it practically forces ext4 on you, and won't be happy with btrfs. 

Having said that, I remember someone else commenting about trying the script with btrfs, and me looking into it. I don't remember what my conclusion was, and I can't find the comments with it now (maybe it was a private message or something).

I'll give my script a try with btrfs sometime in the next 24 hours to see if it works, or how complicated it would be to have it work with btrfs. I'll post back when I do.

---

### Post by terminator14 on 2013-11-16
> **commensal said:**
> Does it matter if I have btrfs?
Can't boot to RAM image.

At this point, my script definitely does not work with btrfs. I've been hammering away at it for hours, trying to get grub, live-boot, and btrfs to work together, but so far no go. I can see why nothing ever came of my previous attempts at getting this to work. I might give it another go tomorrow, but it may just be that live-boot doesn't support btrfs subvolumes.

---

### Post by commensal on 2013-11-17
> **terminator14 said:**
> At this point, my script definitely does not work with btrfs. I've been hammering away at it for hours, trying to get grub, live-boot, and btrfs to work together, but so far no go. I can see why nothing ever came of my previous attempts at getting this to work. I might give it another go tomorrow, but it may just be that live-boot doesn't support btrfs subvolumes.

Thank you for your efforts. I really appreciate it.
I used your script a while ago on 12.10 with ext4 volume.
Now I have ssd and formated it with btrfs (since it has native optimisation (-ssd, -discard)).
 I liked the idea of decreasing the wear of it with your script.
I guess now I have to choose stick to ext4 and RAM or pure ssd.

---

### Post by James Oldiges on 2013-11-21
Hey, I'm kinda new at this, but its not saving properly.  Don't get me wrong, this is the ****, but its frusterating installing chromium every time.

I've done rupdate, rupdate -f, and rupdate --both.  None have worked?  Do I have to boot to the nonram session to get this to work?

---

### Post by terminator14 on 2013-11-21
> **James Oldiges said:**
> Hey, I'm kinda new at this, but its not saving properly.  Don't get me wrong, this is the ****, but its frusterating installing chromium every time.

I've done rupdate, rupdate -f, and rupdate --both.  None have worked?  Do I have to boot to the nonram session to get this to work?

rupdate doesn't save what you do in the ram session. Nothing does that. If you want chromium in the ram session, you have to run "sudo rchroot -R", which will get you into the environment from which the ram session image is constructed. Install chromium with apt-get, leave the environment with "exit", and the rebuild the squashfs image with "rupdate -f"

---

### Post by James Oldiges on 2013-11-23
Thank you very much :)

---

### Post by James Oldiges on 2013-11-24
I'm sorry for bothering you again, but I have new issues.

My computer died during an rupdate, and now won't work properly.
When I try to boot up, it gives me an error, so I have to go to the more options boot and choose a previous kernel (which makes it not in ram -.-)
Now rupdate isn't reconized as a command, and I don't know what to do rather than wiping the partition and starting anew.  Any ideas?

I have tried uninstalling and reinstalling Rambooster, but that didn't work.

> james@Ram:~$ sudo rupdate[sudo] password for james: 
Sorry, try again.
[sudo] password for james: 
sudo: rupdate: command not found
james@Ram:~$ 




---

### Post by terminator14 on 2013-11-24
> **James Oldiges said:**
> I'm sorry for bothering you again, but I have new issues.

Always happy to help

> **James Oldiges said:**
> My computer died during an rupdate, and now won't work properly.
When I try to boot up, it gives me an error, so I have to go to the more options boot and choose a previous kernel (which makes it not in ram -.-)

So you get the error when you try to boot into the RAM Session, or the latest version of your regular OS?
What's the error?

> **James Oldiges said:**
> Now rupdate isn't reconized as a command

rupdate is only available in the RAM Session. It will not be there in the regular OS. This is normal.

> **James Oldiges said:**
> I don't know what to do rather than wiping the partition and starting anew.  Any ideas?

This seems a little extreme. Lets hope it doesn't come to that. I'm still not sure exactly what the problem is.

> **James Oldiges said:**
> I have tried uninstalling and reinstalling Rambooster, but that didn't work.

First, run:

```
sudo ./RAM_booster_Ubuntu_13.10.sh --uninstall
```

Then reboot, and tell me what problems are left.

---

### Post by James Oldiges on 2013-11-25
> [COLOR=#000000]So you get the error when you try to boot into the RAM Session, or the latest version of your regular OS?[/COLOR]
[COLOR=#000000]What's the error?[/COLOR]

Both.

The error is:
> error:  file `/boot/init??.img-3.11.0-14?? not found
Press any key

Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block (0,0)

The question marks are from where I can't read my handwriting, but I don't think they were important.  think second set was "generic"

This should fix itself when the next kernel update comes out, right?

---

### Post by terminator14 on 2013-11-25
> **James Oldiges said:**
> Both.

The error is:

The question marks are from where I can't read my handwriting, but I don't think they were important.  think second set was "generic"

This should fix itself when the next kernel update comes out, right?

The uninstall script should have already done this, but try regenerating the grub menu with:

```
sudo update-grub2
```

There are a few things needed for grub to boot linux:

It needs to know where to find /boot
It needs to know where to find root (/)
It needs to know the file name of the kernel (vmlinuz file)
It needs to know the file name of the initrd image (a very small version of linux that loads kernel modules)

It sounds like grub is pointing to an initrd image that's not there.
Find out the exact file the error mentions (/boot/init??.img-3.11.0-14??), boot into an older kernel and see if that initrd file exists.

If it does not, you can try to recreate it with:

```
sudo update-initramfs -c -k <version>
```

---

### Post by James Oldiges on 2013-12-09
Hey, thanks for the help.
while away on break, I let a friend borrow the computer (in Original OS mode w/ swap tendency at 0).
In having it returned today, I found that there was an update available and I downloaded it.  Updating the base also updated that kernel thing and thus fixed all the problems.

Thank you very much,
     James

---

### Post by terminator14 on 2013-12-10
> **James Oldiges said:**
> Hey, thanks for the help.
while away on break, I let a friend borrow the computer (in Original OS mode w/ swap tendency at 0).
In having it returned today, I found that there was an update available and I downloaded it.  Updating the base also updated that kernel thing and thus fixed all the problems.

Thank you very much,
     James

Ok cool - good to know you're up and running again

---

### Post by AJ12Gamer on 2013-12-15
> **terminator14 said:**
> Nothing you do in the RAM session has any impact on what's installed and what's not installed on the filesystem.squashfs image. Just because you ran:

```
sudo apt-get install mplayer
```

in the RAM Session doesn't mean "sudo rchroot -R" (the squashfs image) will have it installed. 
There are 2 ways to install stuff: temporarily and permanently.

**Temporarily:**

If you want mplayer, or any package, to be installed temporarily, you can install it as you normally would on any Ubuntu system (sudo apt-get install mplayer). This will be undone as soon as you reboot. This also has no impact on the squashfs image.

**Permanently:**

If you want it to be permanently installed (still there when you reboot), you run "sudo rchroot -R" and install it there. Then you recreate the squashfs image with rupdate. Similarly, if you already added mplayer to the squashfs image and want to remove it, running "sudo apt-get remove mplayer" is temporary. To remove it permanently, you NEED to do it through "rchroot -R".


OK

Even if I want to UNinstall a program **Temporarily** or **Permanently** "with or without" "sudo rchroot -R" it will not be UNinstalled after a reboot.

Even if I want to Install a program **Temporarily** or **Permanently** "with or without" "sudo rchroot -R" it will not be Installed after a reboot.

I do not know how to explain it any better.  Could you test it out to see what I mean?

Thanks

---

### Post by terminator14 on 2013-12-15
> **AJ12Gamer said:**
> OK

Even if I want to UNinstall a program **Temporarily** or **Permanently** "with or without" "sudo rchroot -R" it will not be UNinstalled after a reboot.

Even if I want to Install a program **Temporarily** or **Permanently** "with or without" "sudo rchroot -R" it will not be Installed after a reboot.

I do not know how to explain it any better.  Could you test it out to see what I mean?

Thanks

Do you recreate the squashfs image right after?

---

### Post by laurens-helewaut on 2014-01-07
Hi Terminator14, 

I'm a new user of your script, and I would like to ask you a question about it. 
So right now I installed your script on a fresh install of Ubuntu Gnome 13.10, tried to boot on RAM and it worked flawlessly. 
Now I want to install some apps on my laptop, and I'm currently doing that by booting into the original OS and installing from there. 
How can I get those installed apps to my RAM Session? Is that through the rupdate command on the RAM session? 

Thank you in advance!

---

### Post by terminator14 on 2014-01-07
> **laurens-helewaut said:**
> Hi Terminator14, 

I'm a new user of your script, and I would like to ask you a question about it. 
So right now I installed your script on a fresh install of Ubuntu Gnome 13.10, tried to boot on RAM and it worked flawlessly. 
Now I want to install some apps on my laptop, and I'm currently doing that by booting into the original OS and installing from there. 
How can I get those installed apps to my RAM Session? Is that through the rupdate command on the RAM session? 

Thank you in advance!

Not quite. The rupdate command is only for updates. If you want to install programs on the RAM session, or make changes to config files of any kind that survive a reboot, you need to boot into the RAM sessoin and run:

```
sudo rchroot -R
```

this will give you direct access to the filesystem that is used to create the image you boot from.
Make any changes you want from there (eg. if you want to install software, run "apt-get install package_name"), and type exit to leave the chroot environment when you're done.

At this point, you are NOT done yet. Unfortunately, the squashfs image you boot from is read-only. What you just edited was just the files used to create the squashfs image you boot from. That means that now, you have to tell the computer to use the files you just edited to recreate the squashfs image you boot from. You do this by running:

```
sudo rupdate -f
```

Note: The software you installed will not appear until you boot from the new squashfs image (reboot)

---

### Post by laurens-helewaut on 2014-01-07
> **terminator14 said:**
> Not quite. The rupdate command is only for updates. If you want to install programs on the RAM session, or make changes to config files of any kind that survive a reboot, you need to boot into the RAM sessoin and run:

```
sudo rchroot -R
```

this will give you direct access to the filesystem that is used to create the image you boot from.
Make any changes you want from there (eg. if you want to install software, run "apt-get install package_name"), and type exit to leave the chroot environment when you're done.

At this point, you are NOT done yet. Unfortunately, the squashfs image you boot from is read-only. What you just edited was just the files used to create the squashfs image you boot from. That means that now, you have to tell the computer to use the files you just edited to recreate the squashfs image you boot from. You do this by running:

```
sudo rupdate -f
```

Note: The software you installed will not appear until you boot from the new squashfs image (reboot)

So all the apps I installed via my original OS, is there a way to make these ones be seen on the RAM session? Or is it obligatory to install them via rchroot? 
If so, is it possible to just uninstall the script and let it install again to have my apps running on the RAM session? (spent quite a few hours installing all these apps, would be a waste if I can't get them to my RAM session :p)

Thanks for your help!

---

### Post by terminator14 on 2014-01-07
> **laurens-helewaut said:**
> So all the apps I installed via my original OS, is there a way to make these ones be seen on the RAM session? Or is it obligatory to install them via rchroot? 
If so, is it possible to just uninstall the script and let it install again to have my apps running on the RAM session? (spent quite a few hours installing all these apps, would be a waste if I can't get them to my RAM session :p)

Thanks for your help!

When you run my script for the first time on your computer, it creates a completely separate copy of your Ubuntu. Things installed on the Original OS after that point have no effect on the RAM session. The only way to include things that you've installed on the Original OS onto the RAM session would be, as you said, to uninstall the script (which will remove the RAM session completely), and reinstall it.

To uninstall, just run the script again on your Original OS. It will detect that it is already installed and offer to uninstall itself. Do that. When that's done, run the script again to install it again.

---

### Post by laurens-helewaut on 2014-01-08
> **terminator14 said:**
> When you run my script for the first time on your computer, it creates a completely separate copy of your Ubuntu. Things installed on the Original OS after that point have no effect on the RAM session. The only way to include things that you've installed on the Original OS onto the RAM session would be, as you said, to uninstall the script (which will remove the RAM session completely), and reinstall it.

To uninstall, just run the script again on your Original OS. It will detect that it is already installed and offer to uninstall itself. Do that. When that's done, run the script again to install it again.

Okay, thank you very much for your help! You've did an awesome job making that script!

---

### Post by terminator14 on 2014-01-08
> **laurens-helewaut said:**
> Okay, thank you very much for your help! You've did an awesome job making that script!

No problem :)

---

### Post by dyfi on 2014-01-15
@Terminator14 - That script is marvellous!  I am not a fan of UB, prefer Debian testing.  However, with the option to boot to ram I will use it.  Will there be a script for the 14.04 when released?

---

### Post by terminator14 on 2014-01-15
> **dyfi said:**
> @Terminator14 - That script is marvellous!  I am not a fan of UB, prefer Debian testing.  However, with the option to boot to ram I will use it.  Will there be a script for the 14.04 when released?

I use wheezy myself - haven't used Ubuntu since Unity became its default user interface.
If anyone shows interest in me doing a 14.04 version of my script when Ubuntu 14.04 comes out by requesting it (which will also remind me to do it), I'll check how compatible my script is with 14.04, and as long as the changes are nothing major (which they haven't been in the past), I'll update the script. That's pretty much what I've done in the past.

---

### Post by dyfi on 2014-01-15
@terminator14 - For interest, in Debian I have been using Refracta Snapshot and Installer which creates an .iso of your running system.  This can then be burned to DVD  and has the option of boot to ram when run - the DVD can then be removed.  Then, create a couple of symlinks to data files to enable save to disk.  There are .deb files to download and install to existing Debian.  [http://www.ibiblio.org/refracta/](http://www.ibiblio.org/refracta/)

---

### Post by terminator14 on 2014-01-15
> **dyfi said:**
> @terminator14 - For interest, in Debian I have been using Refracta Snapshot and Installer which creates an .iso of your running system.  This can then be burned to DVD  and has the option of boot to ram when run - the DVD can then be removed.  Then, create a couple of symlinks to data files to enable save to disk.  There are .deb files to download and install to existing Debian.  [http://www.ibiblio.org/refracta/](http://www.ibiblio.org/refracta/)

Cool - first I'm hearing of it. Thanks for the info.

---

### Post by dankojoffrey on 2014-01-27
Hi,
so I've decided to try your script... and I got an error after squashfs was loaded into RAM... "boot failed" see picture... any ideas...???

---

### Post by terminator14 on 2014-01-28
> **dankojoffrey said:**
> Hi,
so I've decided to try your script... and I got an error after squashfs was loaded into RAM... "boot failed" see picture... any ideas...???

What's the OS you're using?
[LIST]
[*]Ubuntu
[*]Kubuntu
[*]Xubuntu
[*]Lubuntu
[*]etc.
[/LIST]

What version?
[LIST]
[*]13.10
[*]13.04
[*]12.10
[/LIST]

Are you using LVM or BTRFS?

Any modifications to the filesystem?[LIST]
[*]
[*]Anything you did by hand?
[*]Could any packages you have installed since first setting up ubuntu have made drastic changes to your FS?
[/LIST]

Do you have enough RAM to run the image the script creates?
[LIST]
[*]How big is the image?
[*]How much RAM do you have?
[/LIST]

---

### Post by dankojoffrey on 2014-01-28
Hi,
it's Ubuntu 13.10, kernel 3.12.9, 8GB RAM, image size 3.5GB.
I've been using this install of ubuntu for months  now, so plenty of packages are installed... 

I'll try to do fresh install of ubuntu 13.10 and try it again...

UPDATE: so I did fresh install, installed kernel 3.12.9, few basic apps (vlc, clementine,...), updated system, installed nvidia drivers... and still same error... then I tried to create squashfs with original kernel 3.11 and still same error...

---

### Post by mvlad4 on 2014-04-27
> **terminator14 said:**
> I use wheezy myself - haven't used Ubuntu since Unity became its default user interface.
If anyone shows interest in me doing a 14.04 version of my script when Ubuntu 14.04 comes out by requesting it (which will also remind me to do it), I'll check how compatible my script is with 14.04, and as long as the changes are nothing major (which they haven't been in the past), I'll update the script. That's pretty much what I've done in the past.

I'm currently using 14.04 on usb with a 2GHz Dual Core 4GB RAM 4 year old laptop and its very very slow. Would really like to know if I can use an existing script or if you are going to create one for 14.04.

---

### Post by terminator14 on 2014-04-27
> **mvlad4 said:**
> I'm currently using 14.04 on usb with a 2GHz Dual Core 4GB RAM 4 year old laptop and its very very slow. Would really like to know if I can use an existing script or if you are going to create one for 14.04.

I will be looking into creating a 14.04 version, and probably a video tutorial in the next couple of days.

---

### Post by mvlad4 on 2014-04-27
> **terminator14 said:**
> I will be looking into creating a 14.04 version, and probably a video tutorial in the next couple of days.

Wow thanks, fast answer !!

I've only started using Ubuntu for a  week or so now, but I really like it and think that this script of yours is really useful for usb installs.

Wish you well.

---

### Post by terminator14 on 2014-04-27
> **mvlad4 said:**
> Wow thanks, fast answer !!

I've only started using Ubuntu for a  week or so now, but I really like it and think that this script of yours is really useful for usb installs.

Wish you well.

Version 14.04 has been uploaded to github.
People have tried using my script on USB installs in the past, and have suggested that it may not work. I might give it a try later, but I suggest you proceed carefully not to end up with a system you can't boot into. If you can, try the USB install you want in combination with the script in a virtual machine first, just to be safe.

---

### Post by mvlad4 on 2014-04-28
Ok so I tested it first and and now finished running the script and everything is working great.

Thanks.

---

### Post by terminator14 on 2014-04-28
> **mvlad4 said:**
> Ok so I tested it first and and now finished running the script and everything is working great.

Thanks.

So you did a regular install of Ubuntu onto a USB drive, booted Ubuntu from the USB drive, downloaded and ran my script, and you can now boot into the RAM session?

---

### Post by mvlad4 on 2014-04-29
Yes, and it's working absolutely great. I love it.

The only glitch I have seen is that everytime I open chrome it freezez for about 1-2 minutes and then all of my extensions force quit. But then even if I reload all of the extensions nothing bad happens, everything works good and fast. Doesn't bother me at all.

---

### Post by kevinpknudsen on 2014-05-07
I have problems with this script.
When I boot into ram I get something like this message:

**"file not found: /boot/initrd.img-3.13.0-24-generic.efi.signed"**

When I press enter it shows:

[B]"Kernel panic - not syncing
VFS: unable to mount root fs on unknown-block(0,0)
cpu: 1 PID: 1 Comm:swapper/0 not tainted 3.13.0-24-generic #46-ubuntu"[/B]

... and some more I didn't write down.

Can someone figure out why it can't find this file?


I'm using a recently installed Ubuntu 14.04 that has been working so far.
I'm running with a setup of 8gb ram and the image created was about 2,2gb ram.
My partitions look like this:
/dev/sda1 - fat32 filesystem - boot/efi (flagged boot)
/dev/sda2 - ext4 - /
/dev/sda4 - ext4 - /home  (marked: home)
/dev/sda3 - linux swap..

The laptop is a Samsung 5 series. Could the UEFI be a problem? As I understand it is a replacement for BIOS?

Looking forward to hear from someone who can solve this!
Thanks :)

- Kevin

---

### Post by terminator14 on 2014-05-07
I've answered this question in the reply to the PM you sent me.

---

### Post by C.S.Cameron on 2014-05-07
Lately my installs to USB seem to be running really fast, like the first time I start, say, Libre Office, it takes 15s but the next time less than a second.
I'm wondering if the Ubuntu guys are starting to follow your lead.

---

### Post by terminator14 on 2014-05-08
In theory, that is how all OS's (Windows, Linux and Mac) use RAM.
The first time you start an application, it will take a long time to start as it gets copied from your hard drive to RAM before it runs.
The next time you run it, it will already be in RAM (assuming you weren't short on RAM and nothing replaced it), so it will start quickly.
This may be the first time you notice it, but it was like that long before I wrote my script, and is not something I can take credit for.

---

### Post by terminator14 on 2014-05-13
I just made a few small changes - the script should now work with EFI systems as well.

---

### Post by mvlad4 on 2014-07-23
Hello, me again after a few months. I'm now faced with this messege: [http://i58.tinypic.com/2cyobxc.jpg](http://i58.tinypic.com/2cyobxc.jpg) after I found the "update complete, please reboot" messege last night on my laptop. I'm running ubuntu 14.04 with the ram script for almost 3 months now and no problems untill now. And i'm not very good at finding the problem, maybe you guys know something.

---

### Post by terminator14 on 2014-07-23
> **mvlad4 said:**
> Hello, me again after a few months. I'm now faced with this messege: [http://i58.tinypic.com/2cyobxc.jpg](http://i58.tinypic.com/2cyobxc.jpg) after I found the "update complete, please reboot" messege last night on my laptop. I'm running ubuntu 14.04 with the ram script for almost 3 months now and no problems untill now. And i'm not very good at finding the problem, maybe you guys know something.

What does your setup look like?
Are you using x86/x64? LVM? BTRFS? UEFI? GPT? Just regular old MBR with primary and extended partitions?
What does your partition table look like?

---

### Post by janstavel on 2014-09-10
I had to go through the pain of guessing my login credentials for ubu forums - just so I could say Thank You and Kudos. Great job, everything went smoothly on first try. (Well, except for my ol' Latitude nearly burnt its core2 during the squashfs creation, I don't recall it ever getting to 80°C... Good thing it's quite chilly tonight. Getting new thermal paste is probably a good idea...)

So thank you again, I was fascinated by Parted Magic and Porteus running from ram for some time and wondering how much work would it mean to get Ubuntu and/or Debian to run from it as well. Reading through your previous thread, probably more than 15 minutes it took with your script.... ;)

---

### Post by terminator14 on 2014-09-10
> **janstavel said:**
> I had to go through the pain of guessing my login credentials for ubu forums - just so I could say Thank You and Kudos. Great job, everything went smoothly on first try. (Well, except for my ol' Latitude nearly burnt its core2 during the squashfs creation, I don't recall it ever getting to 80°C... Good thing it's quite chilly tonight. Getting new thermal paste is probably a good idea...)

So thank you again, I was fascinated by Parted Magic and Porteus running from ram for some time and wondering how much work would it mean to get Ubuntu and/or Debian to run from it as well. Reading through your previous thread, probably more than 15 minutes it took with your script.... ;)

Glad to hear people appreciate the hard work I put into it :)

---

### Post by fernando29 on 2014-10-09
Hi [**[COLOR=#000000]terminator14[/COLOR]**]("http://ubuntuforums.org/member.php?u=572729"):

I am testing your script (Ubuntu14.01) and I am having an issue with the network. Ethernet adapter does not get recognized. Before running the script, I completely removed apparmor. If I compare just after the first boot the /etc/network/interfaces file between original OS and the RAM one, it is not the same. While the original is something like:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto p2p1
iface p2p1 inet dhcp

```

Where p2p1 is how my adapter is recognized. The one in RAM session is like:

```
auto lo
iface lo inet loopback

```

I hope you could give me some advice to overcome this. Thanks.

---

### Post by terminator14 on 2014-10-10
> **fernando29 said:**
> I am testing your script (Ubuntu14.01)

Since there is no Ubuntu 14.01 (to my knowledge), I assume you mean Ubuntu 14.10? Something like the ubuntu-14.10-beta2-desktop-amd64.iso file found here?: [http://releases.ubuntu.com/utopic/](http://releases.ubuntu.com/utopic/)
My script doesn't touch the /etc/network/interfaces file directly, so I'm kind of curious how yours gets changed.
Why is it called p2p1 and not like eth0 or something? Is it a regular Ethernet 10/100 or 10/100/1000 interface, or is it something else?

Note: While it would be great to get to the bottom of the problem, one solution you can try is to:

[LIST=1]
[*]Create a RAM Session by running the script (if you still have the RAM session installed, you can use that)
[*]Boot into the RAM Session
[*]Run "sudo rchroot -R"
[*]Use nano or vim to edit /etc/network/interfaces and make it look like the Original OS's /etc/network/interfaces file (add the two p2p1 lines)
[*]Save the file and close the editor
[*]Type "exit" to exit the chroot
[*]Run "sudo rupdate -f" to update the squashfs image you boot from
[*]Reboot
[/LIST]

Steps 3 - 6 MUST be done in the same terminal window, unless you know what it means to be inside of a chroot jail, and exactly what's going on.

---

### Post by fernando29 on 2014-10-10
Hi terminator14. You are right. The version I am using is 14.04. My mistake. I will test your recomendation to see what happens. Thanks.

---

### Post by fernando29 on 2014-10-10
Hi terminator14. I found the following:

1. If I "sudo rchroot -R", /etc/network/interfaces file is exactly as If I "sudo rchroot -O".
2. When I don't rchroot, is when I see the "Incomplete" file (these that does not have the two p2p1 lines). 

I thought that when I am out of rchroot, It should be the same as if I am inside "sudo rchroot -R". Now I see it isn't.

---

### Post by terminator14 on 2014-10-10
> **fernando29 said:**
> Hi terminator14. I found the following:

1. If I "sudo rchroot -R", /etc/network/interfaces file is exactly as If I "sudo rchroot -O".
2. When I don't rchroot, is when I see the "Incomplete" file (these that does not have the two p2p1 lines). 

I thought that when I am out of rchroot, It should be the same as if I am inside "sudo rchroot -R". Now I see it isn't.

When you boot into the RAM session and look at your /etc/network/interfaces, you are looking at a file that resides in your RAM. This file gets loaded from /live/filesystem.squashfs, along with the rest of your filesystem, at boot every time.
When you run "rchroot -R", you are looking at the folder /var/squashfs that is located on your Original OS (on your hard drive). The idea is that in order to change any files on your RAM session, you modify /var/squashfs (by running 'rchroot -R'), make changes, and recreate the filesystem.squashfs image that you boot from.
This is necessary because squashfs images can NOT be modified directly - they are read only images.
All that basically means that the /etc/network/interfaces file you see in your RAM session is not exactly the same as the one that you see when you run 'rchroot -R'. There is a possibility that they can be different, as they are different files.
One is a copy of the other though, so unless something changed it, the files should be the same.

As far as I can tell, one of two things is happening:

1. The /etc/network/interfaces file in your filesystem.squashfs image is NOT the same as the /etc/network/interfaces file in your /var/squashfs (rchroot -R)
[INDENT]Not sure how this happened, but it's possible. When you modify things in the 'rchroot -R' environment, the filesystem.squashfs file does NOT get updated automatically - it must be recreated with 'rupdate -f', so the two places can have different files.[/INDENT]
2. Something is changing your /etc/network/interfaces file at boot.
[INDENT]It might be NetworkManager. You can try turning off NetworkManager by doing
```
rchroot -R
echo "manual" | tee /etc/init/network-manager.override
exit
rupdate -f
```

Note: I got the command for disabling NetworkManager from here: [https://help.ubuntu.com/community/NetworkManager#Disabling_NetworkManager](https://help.ubuntu.com/community/NetworkManager#Disabling_NetworkManager)
and haven't actually tried it.[/INDENT]

Note: I will download Ubuntu 14.04 to see if I can reproduce the problem

---

### Post by terminator14 on 2014-10-10
Something is indeed changing the /etc/network/interfaces file from whatever it is on the filesystem.squashfs image, to this:

```
auto lo
iface lo inet loopback
```

I'm trying to track down what that is.
Disabling NetworkManager does not seem to help.

---

### Post by fernando29 on 2014-10-10
Hi:

It seems that network-manager is not even installed on my system. I am testing all this on a Ubuntu (Lubuntu installer) Minimall install, to which I only added ssh when picking packages, this is basically a headless system with no graphic environment or X Server.

The problem seems to be more than the missing line on interfaces file. If I run, for instance

```
sudo ifup p2p1
```

I get the message:

> Ignoring unknown interface p2p1=p2p1

If I do the same on the system before running the script, I can do ifup and ifdown, and the system knows my adapter.

It is a weird thing.


EDIT: Ok, I have checked. the problem is indeed the interfaces file. If I edit it manually and run $ifup p2p1, the network adapter is started and works. I hope that now that you have reproduced the issue, maybe could find a solutions.

Thanks.

---

### Post by Otto-C on 2014-10-12
Using 12.04 fully up to date. 32 bit desktop.
I found your thread. After reading much of it, totally 
confused re installing.
It would be most helpful if someone could provide a 
step by step install. Many of us are turned off by a
lack instructions.

tia
otto-c

---

### Post by terminator14 on 2014-10-12
> **Otto-C said:**
> Using 12.04 fully up to date. 32 bit desktop.
I found your thread. After reading much of it, totally 
confused re installing.
It would be most helpful if someone could provide a 
step by step install. Many of us are turned off by a
lack instructions.

tia
otto-c

I've been planning to make a video going through the process, but haven't gotten around to it.
I'll see if I can find a mic around the house and record one.

---

### Post by terminator14 on 2014-10-12
> **fernando29 said:**
> I hope that now that you have reproduced the issue, maybe could find a solutions.

I can reproduce the problem, but finding out what is causing it is turning out surprisingly difficult. I've spent a few hours trying to track down what is making changes to /etc/network/interfaces at boot, with no luck.
As a temporary workaround, this seems to work:

Boot into RAM Session
Run "sudo rchroot -R"
Use nano or vim to edit /etc/rc.local
Just BEFORE the "exit 0" line, add something like this:
```
	echo "\nauto p2p1\niface p2p1 inet dhcp" >> /etc/network/interfaces
	ifup p2p1
```
type "exit" to exit chroot
Run "sudo rupdate -f" to recreate the squashfs image
Reboot

Explanation:
[INDENT]rc.local is the last script that runs during system boot
This will write 2 lines to the /etc/network/interfaces file
AFTER whatever is modifying /etc/network/interfaces
is done messing with it, and it will run ifup to bring your
interface up.[/INDENT]

I'm going to have a busy few days, but I'll see if I can give tracking down the problem another shot when I get some time.

---

### Post by fernando29 on 2014-10-13
Hi terminator14.


Thanks for the workaround for the network problem. Even it could be a solution for something that I was going to ask you. I am working on a system, where the only UI is a custom application. By this application, users can make some settings like IP configuration (DHCP, fixed IP etc, netmask, gateway, etc). And this changes have to persist between system boots. My first thinking was that when a change on setting is needed, the aplication to create and launch a script file that makes the rchroot, the changes to the respective files, and finalize with "rupdate -f". But I found that "rupdate -f" can take several minutes, so it was not an option. Now I am thinking, I can store the settings (IP, DHCP, Timezone) in a file under /home, and make these values to be loaded with some commands in rc.local. What do you think of this approach?. Is /home mounted when rc.local gets executed?.


Again, thanks for your thought and your help.

---

### Post by terminator14 on 2014-10-13
> **fernando29 said:**
> But I found that "rupdate -f" can take several minutes, so it was not an option. Now I am thinking, I can store the settings (IP, DHCP, Timezone) in a file under /home, and make these values to be loaded with some commands in rc.local. What do you think of this approach?.

I think that "rupdate -f" would definitely take too long for a simple application to save settings, and that saving the settings to some kind of permanent storage and loading them at boot is a smart way to go.

Using rc.local is probably a good choice. I'm not too familiar with upstart, which may have a better way to run scripts at boot, but rc.local should work.

> **fernando29 said:**
> Is /home mounted when rc.local gets executed?.

I would guess that it is, but you should probably confirm this to be sure.
I would do something like add a simple:
```
echo "stuff" > /home/testfile
```
to your rc.local, reboot, and see if the testfile gets written to your /home, or if it gets written before the system mounts /home, in which case you won't see the testfile under /home.

---

### Post by fernando29 on 2014-10-16
Hi @terminator14.


I have made some tests and I could confirm, the hack for the network works, and /home IS already mounted, when rc.local runs. By the way, I am wondering if is there a way to avoid GRUB menu to show, I mean the system just go straight to load the files system on RAM.

Thanks.

EDIT: It would be better for me if this GRUB configuration could be made by modifying the script, so the system boots straight to RAM since the script is run for first time. I found in the script a function GrubEntry(), that seems to make the GRUB modifications, but with my limited scripting knowledge, I don't dare to modify it.

---

### Post by terminator14 on 2014-10-16
> **fernando29 said:**
> is there a way to avoid GRUB menu to show, I mean the system just go straight to load the files system on RAM.

If you want the actual script to do this, try replacing these lines:

```
#Unhide grub menu by uncommenting line in /etc/default/grub
sudo sed -i 's/\(GRUB_HIDDEN_TIMEOUT=0\)/#\1/g' /etc/default/grub
```

with these ones:

```
#Make sure grub menu boots to default after 1 second
sudo sed -i 's/\(GRUB_HIDDEN_TIMEOUT=\)[0-9]*/\11/g' /etc/default/grub
sudo sed -i 's/\(GRUB_TIMEOUT=\)[0-9]*/\10/g' /etc/default/grub

```

in the script. If you're confused, let me know and I'll upload a modified script for you.
Or if you want to make this change after you have already run the script, try this from the RAM Session instead:

```
$ sudo rchroot -O
edit /etc/default/grub
	#GRUB_HIDDEN_TIMEOUT=0	--> GRUB_HIDDEN_TIMEOUT=1
	GRUB_TIMEOUT=10 --> GRUB_TIMEOUT=0
$ update-grub
$ exit

Note: In this case, you just edited your Original OS (since that's where your main grub files reside),
so there's no need to recreate the squashfs image
```

both give you 1 second to hit escape to bring up the grub menu at boot in case you want to boot into the Original OS, but if you do nothing after 1 second, it boots into the RAM Session.

Explanation of what's going on:

The file /etc/default/grub on your Original OS is the one that has the settings that determine how long the grub menu shows up for, and whether it's hidden or not. More specifically, these 2 lines:

```
GRUB_HIDDEN_TIMEOUT=
GRUB_TIMEOUT=
```

this page explains what both do: [https://www.gnu.org/software/grub/manual/html_node/Simple-configuration.html](https://www.gnu.org/software/grub/manual/html_node/Simple-configuration.html)
but basically, to have the grub menu hidden, set GRUB_TIMEOUT to 0, and set GRUB_HIDDEN_TIMEOUT to the number of seconds you want the hidden grub menu to wait for you to hit Esc before it boots the default entry (RAM Session in our case). If you want the grub menu to show up instead, comment out (add # to the beginning of the line) the GRUB_HIDDEN_TIMEOUT line and set GRUB_TIMEOUT to the length of time in seconds that the grub menu should wait for you before going with the default menu entry. The 2 lines above that I wrote just tell sed how to identify the exact lines in question, and what to change them to. If you do this by hand, remember that:

1. You want the /etc/default/grub on the Original OS, NOT the RAM session
2. You MUST run update-grub after making changes to /etc/default/grub

---

### Post by fernando29 on 2014-10-16
terminator14: Thnaks!!...I tested the script modification, and it worked as expected. The only think I don't understand very well is how "s/\(GRUB_HIDDEN_TIMEOUT=\)[0-9]*/\11/g" produces "GRUB_HIDDEN_TIMEOUT=1" and "s/\(GRUB_TIMEOUT=\)[0-9]*/\10/g" produces "GRUB_TIMEOUT=0"

---

### Post by terminator14 on 2014-10-16
> **fernando29 said:**
> "s/\(GRUB_HIDDEN_TIMEOUT=\)[0-9]*/\11/g" produces "GRUB_HIDDEN_TIMEOUT=1"
> **fernando29 said:**
> "s/\(GRUB_TIMEOUT=\)[0-9]*/\10/g" produces "GRUB_TIMEOUT=0"

Not something you need to know in order to use it, but it's always good to know more.
This is basically what's happening:

You can use sed to replace a string in a file with any other string. Ex:
```
sed -i 's/FIRST_STRING/SECOND_STRING/g' INPUT_FILE
```

Here,

-i means edit file in place. Sed's default behaviour is to do what you ask and output the result to stdout instead of modifying the INPUT_FILE. -i changes that
's/' tells sed to search INPUT_FILE for FIRST_STRING and replace it with SECOND_STRING
'/g' tells sed to look for more than one match per line. This is probably not important in our case - I'm just used to using it, and it does no harm in our case

The FIRST_STRING part is actually a [regular expression]("http://en.wikipedia.org/wiki/Regular_expression") - "a sequence of characters that forms a search pattern, mainly for use in pattern matching with strings" -- Wiki

Now let's take a closer look at a slightly simplified version of the first sed command I used:

```
sudo sed -i 's/GRUB_HIDDEN_TIMEOUT=[0-9]*/GRUB_HIDDEN_TIMEOUT=1/g' /etc/default/grub
```

This basically tells sed to:

Find the string GRUB_HIDDEN_TIMEOUT=, followed immediately by zero or more occurrences of a digit (from 0 to 9).
Once this is found, the second part tells grub to replace that with GRUB_HIDDEN_TIMEOUT=1.

As you can see in the "simplified version" above, the line is long because I had to repeat the long string "GRUB_HIDDEN_TIMEOUT=" in both the FIRST_STRING and the SECOND_STRING. In order to avoid this, and make the line shorter, I used a sed trick:

anything you find in the FIRST_STRING can be surrounded by \( and \), and later used in the second string by using \#, where # is a digit. The first thing you surrounded with \( \) in the first string is referrenced in the SECOND_STRING by \1. The second thing is referenced by \2. The third by \3, and so on. In my case, I only had one thing I surrounded with \( \), so I only used \1.
All this did was just save me from typing out "GRUB_HIDDEN_TIMEOUT=" twice.
The result is the second string being simply "\11". This looks like it should be read as slash eleven, but is actually 2 different parts - slash one and one. The first part, \1, means: recall everything from the FIRST_STRING that was between \( and \) (in our case this was GRUB_HIDDEN_TIMEOUT=). The second part, "1", is just a 1. The result is GRUB_HIDDEN_TIMEOUT=1.

The second sed command does almost the same thing: it find the string GRUB_TIMEOUT=, immediately followed by any number of digits, and replaces it with GRUB_TIMEOUT=, immediately followed by a 0.

For more info, you can read up on the sed command, as well as regular expressions. Regular expressions are used by many linux programs - not just the sed command; in fact they are probably more often used with the grep command, and come in very handy, and knowing at least the basic regular expressions is very important if you want to know more about linux.

---

### Post by terminator14 on 2014-10-17
While looking into the /etc/network/interfaces problem, I noticed a few other problems with my script:

1. during a kernel update, the system would detect that we were running in a live environment and refuse to make the new initrd image, causing boot problems
2. /etc/resolv.conf wasn't being copied over properly, resulting in "rupdate --both" not giving the original OS internet access

Both problems have been fixed, and the updated Ubuntu 14.04 script has been uploaded to github.

---

### Post by fernando29 on 2014-10-19
Hi terminator.

Thanks for your explanation. I think I have a couple of uses for "sed", now that I know how to "search and replace" within the contents of a file. I am going to test the fixed script also, and give any relevant feedback. Thanks.

---

### Post by terminator14 on 2014-10-19
> **fernando29 said:**
> I think I have a couple of uses for "sed", now that I know how to "search and replace" within the contents of a file.

Yup - linux tools like sed, grep, awk, and others are very powerful, and come in very handy when scripting, reviewing log files, searching through files for stuff, and have lots of other uses - they are definitely good to know.

> **fernando29 said:**
> I am going to test the fixed script also, and give any relevant feedback. Thanks.

Awesome! The more feedback I get, the more bugs I can fix to make sure the script is as stable as it can be. Thanks

---

### Post by fernando29 on 2014-10-20
Hi  terminator14.

Before all, excuse me for this little off-topic. Regarding what you explained about sed, how would you do this:

Search in file "/usr/share/X11/xorg.conf.d/10-disp.conf" for the string /dev/fbX, where X can be a number from 0 to 9, and replace it with a variable named VAR. I have the following:

sed -i 's//dev/fb[0-9]*/$VAR/' /usr/share/X11/xorg.conf.d/10-disp.conf

but I am getting an error "sed: -e expression #1, char 8: unknown option to `s'". I think sed doesn't like the double slash after 's'.

---

### Post by terminator14 on 2014-10-20
> **fernando29 said:**
> Hi  terminator14.

Before all, excuse me for this little off-topic. Regarding what you explained about sed, how would you do this:

Search in file "/usr/share/X11/xorg.conf.d/10-disp.conf" for the string /dev/fbX, where X can be a number from 0 to 9, and replace it with a variable named VAR. I have the following:

sed -i 's//dev/fb[0-9]*/$VAR/' /usr/share/X11/xorg.conf.d/10-disp.conf

but I am getting an error "sed: -e expression #1, char 8: unknown option to `s'". I think sed doesn't like the double slash after 's'.

In the expression:

```
sed -i 's/FIRST/SECOND/g' INPUT_FILE
```

the standard practice is to use /'s, but almost any character works. When either FIRST or SECOND have /'s in them, which is quite common when dealing with file paths, the easiest thing is to just switch to another symbol. Eg:

```
sed -i 's|FIRST|SECOND|g' INPUT_FILE
```
OR
```
sed -i 's#FIRST#SECOND#g' INPUT_FILE
```

In your case, something like this should work:

```
sed -i "s|/dev/fb[0-9]|$VAR|g" /usr/share/X11/xorg.conf.d/10-disp.conf
```

a couple of notes about that:

1. If you want the 10-display.conf file to literally say $VAR, you use single quotes around the sed expression as you did. If you want $VAR to be replaced by the actual contents of the $VAR variable, use double quotes as I did.

2. The * symbol means "zero or more occurrences of the previous character". If there was a chance that your device might be called /dev/fb02, or /dev/fb43 or something, you would use [0-9]*. If it is definitely going to be called /dev/fb#, where # is EXACTLY one digit, just use [0-9] as I did. The downside of using * is that "zero or more" in this case means that the expression /dev/fb[0-9]* would match /dev/fb as well, since that's /dev/fb followed by zero occurrences of [0-9]

3. It is important to understand what the g in 's/FIRST/SECOND/g' does. See here for an explanation: [http://www.grymoire.com/Unix/Sed.html#uh-6](http://www.grymoire.com/Unix/Sed.html#uh-6). Basically, it just means if there's a chance that FIRST might appear more than once per line, and you want your expression to match every occurrence of FIRST in the file instead of just the first occurrence it finds on each line, use /g.

---

### Post by terminator14 on 2014-10-20
To anyone interested:

One of the biggest inherent problems with my script from the start has been this:

When you are in the RAM Session and you run "sudo rupdate", if there is a kernel update, the new kernel and initrd image get put into /boot, and the new kernel's modules get placed into the RAM Session's /lib/modules directory. While this works out great for the RAM Session, it messes up the Original OS.

This is because at this point, the Original OS does NOT have the necessary /lib/modules to run the new kernel, but grub doesn't know that. Grub assumes that if /boot has a newer kernel, the OS can and should run it. This results in grub creating grub menu entries for the Original OS to use the new kernel, and the Original OS crashing when you try to boot it using those menu entries.

For the longest time, the only thing I had was a warning in the original post of how to avoid the problem, and how to fix it if it happens, but no actual solution. A few days ago, I came up with a way to detect and warn people inside the script. While this was an improvement, I got a better idea, and today I spent a few hours creating an actual fix. As of now, the latest version of the Ubuntu 14.04 script has a working fix that:

[LIST]
[*]Detects when a kernel cannot be booted by the Original OS
[*]Forces grub to ignore it
[/LIST]
This results in grub menu entries reflecting the latest kernel that a specific OS can boot. This means that the RAM Session might have one version of the kernel in the grub boot menu, while the Original OS can have a slightly older kernel in the grub boot menu until you run updates on the Original OS. This is probably the most elegant solution to the problem, and appears to work pretty well. If this is a problem you have run into, updating the script and reinstalling should fix that for good.

Edit: I just realized that one thing I overlooked was the case where the Original OS is more updated than the RAM Session. This may cause the RAM Session to have issues booting, since the grub boot menu will tell it to use the newer kernel that it has no modules for. I'm looking into this now.

---

### Post by terminator14 on 2014-10-22
All issues with kernel updates should now be fixed.

---

### Post by terminator14 on 2014-10-23
Ubuntu 14.10 script uploaded

---

### Post by amityadav9314 on 2014-11-01
**sudo rupdate -f code is not working for me.** My RAMBooster was installed without error on my ubuntu 14.04 machine.

On running the update command I am getting this error
```

[amit] RAM_booster$ sudo rupdate -f
[sudo] password for amit: 
mount: no such partition found
#
UUID=9BE3-67BF failed to mount to /boot.
umount: /mnt/Original_OS: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
umount: /mnt/Original_OS/var/squashfs/dev: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
[amit] RAM_booster$ ls /
bin   cdrom  etc   initrd.img  lib64       media  opt   RAM_Session  run   srv  tmp  var
boot  dev    home  lib         lost+found  mnt    proc  root         sbin  sys  usr  vmlinuz

```

---

### Post by terminator14 on 2014-11-01
> **amityadav9314 said:**
> **sudo rupdate -f code is not working for me.** My RAMBooster was installed without error on my ubuntu 14.04 machine.

On running the update command I am getting this error
```

[amit] RAM_booster$ sudo rupdate -f
[sudo] password for amit: 
mount: no such partition found
#
UUID=9BE3-67BF failed to mount to /boot.
umount: /mnt/Original_OS: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
umount: /mnt/Original_OS/var/squashfs/dev: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
[amit] RAM_booster$ ls /
bin   cdrom  etc   initrd.img  lib64       media  opt   RAM_Session  run   srv  tmp  var
boot  dev    home  lib         lost+found  mnt    proc  root         sbin  sys  usr  vmlinuz

```

The UUID for your /boot partition (UUID=9BE3-67BF) seems too short to be a proper UUID. The script may be failing to read it from your Original OS's /etc/fstab.
Could you paste the contents of your Original OS's /etc/fstab?

---

### Post by sudodus on 2014-11-01
It seems to be a UUID string of a Microsoft file system (FAT or NTFS). Such a file system might cause problems with a linux file permissions.

---

### Post by terminator14 on 2014-11-01
> **sudodus said:**
> It seems to be a UUID string of a Microsoft file system (FAT or NTFS). Such a file system might cause problems with a linux file permissions.

True - microsoft file systems do have shorter UUIDs like that, which it might be. /etc/fstab should tell us what it is.

---

### Post by amityadav9314 on 2014-11-01
> [COLOR=#000000]The UUID for your /boot partition (UUID=9BE3-67BF) seems too short to be a proper UUID. The script may be failing to read it from your Original OS's /etc/fstab.[/COLOR]
[COLOR=#000000]Could you paste the contents of your Original OS's /etc/fstab?[/COLOR]

This is the output of the OS_Session's /etc/fstab
```

[amit] ~$ ls /mnt
Original_OS
[amit] ~$ cd /mnt/Original_OS/
[amit] Original_OS$ cd etc
[amit] etc$ cat fstab
fstab    fstab.d/ 
[amit] etc$ cat fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=44e1f8e9-68b6-4f89-aabe-29f71009afb8 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=9BE3-67BF  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda3 during installation
UUID=9675bcb0-76f9-4932-bf11-0d2bc9269f2f none            swap    sw              0       0
UUID=0d44b641-9fcb-4b83-a371-ea683205c54b    /home    ext4    auto    0 0
[amit] etc$ 

```


And this is the output of the RAM_Session's /etc/fstab
```

[amit] ~$ ls /
bin   cdrom  etc   initrd.img  lib64       media  opt   RAM_Session  run   srv  tmp  var
boot  dev    home  lib         lost+found  mnt    proc  root         sbin  sys  usr  vmlinuz
[amit] ~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
# /boot/efi was on /dev/sda1 during installation
UUID=9BE3-67BF  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda3 during installation
UUID=9675bcb0-76f9-4932-bf11-0d2bc9269f2f none            swap    sw              0       0
UUID=0d44b641-9fcb-4b83-a371-ea683205c54b	/home	ext4	auto	0 0
[amit] ~$ 



```

---

### Post by terminator14 on 2014-11-02
> **amityadav9314 said:**
> This is the output of the OS_Session's /etc/fstab
...

Yup - you've got a FAT32 formatted /boot partition. Not only that, but your system is also efi.
I'll try to duplicate your setup and see how rupdate does. I'll post back in a bit.

---

### Post by terminator14 on 2014-11-02
> **amityadav9314 said:**
> **sudo rupdate -f code is not working for me.**```

[amit] RAM_booster$ sudo rupdate -f
[sudo] password for amit: 
mount: no such partition found
[B]#
UUID=9BE3-67BF [/B]failed to mount to /boot.

```

Problem ended up having nothing to do with fat32 or efi - I just forgot to ignore comments when reading /etc/fstab. It was trying to figure out how to mount:

```
#
UUID=9BE3-67BF 
```

instead of just 

```
UUID=9BE3-67BF 
```

I fixed both my Ubuntu 14.04 and 14.10 scripts, and uploaded them to github.
You basically have 2 choices for applying the fix. They are:

1. Reinstall the RAM_booster script
[INDENT][LIST=1]
[*]Boot into Original OS
[*]open terminal
[*]cd into script folder
[*]run "sudo ./RAM_booster_Ubuntu_14.04.sh --uninstall" to remove your RAM Session completely
[*]run "git pull" to download the updated scripts from github automatically
[*]run "sudo ./RAM_booster_Ubuntu_14.04.sh" to install again
[/LIST][/INDENT]

2. Replace the old rupdate script with the new one manually
[INDENT][LIST=1]
[*]Boot into RAM Session
[*]Open "/usr/sbin/rupdate" with a text editor
[*]Write down line 13 - the one that looks like this:
```
REG_DEVICE="/dev/sdXY"
```
[*]Close text editor and delete /usr/sbin/rupdate
[*]Download the rupdate script attached below, extract it, and place it in /usr/sbin/
[*]Run "sudo chown root:root /usr/sbin/rupdate; sudo chmod 755 /usr/sbin/rupdate" to change the ownership and permissions of /usr/sbin/rupdate to what they should be
[*]Open "/usr/sbin/rupdate" with a text editor
[*]Replace line 13 with the one you wrote down earlier
[*]Save and exit text editor
[*]Run "sudo rchroot -R"
[*]Delete /usr/sbin/rupdate
[*]Open a new terminal window
[*]Delete /mnt/Original_OS/var/squashfs/usr/sbin/rupdate
[*]Place the rupdate that you just downloaded and extracted (the one attached below) into /mnt/Original_OS/var/squashfs/usr/sbin/
[*]Close this new terminal window, and go back to the original one (the one where you ran "sudo rchroot -R")
[*]Run "sudo chown root:root /usr/sbin/rupdate; sudo chmod 755 /usr/sbin/rupdate" to change the ownership and permissions of /usr/sbin/rupdate to what they should be
[*]Open "/usr/sbin/rupdate" with a text editor
[*]Replace line 13 with the one you wrote down earlier
[*]Save and exit text editor
[*]Run "exit" to exit the chroot
[*]Run "sudo rupdate -f" to recreate the squashfs image with the new rupdate script
[*]Reboot
[/LIST]
[/INDENT]

Let me know if it works so I can delete my test Ubuntu setup that duplicates your partition layout.

---

### Post by amityadav9314 on 2014-11-02
> [COLOR=#000000]Let me know if it works so I can delete my test Ubuntu setup that duplicates your partition layout.[/COLOR]

Hmm, it is working now..:)

---

### Post by michael232 on 2014-11-13
I have a similar issue here. The boot check seems to fail:
rupdate around line 140:

```

> cat $Orig_OS/etc/fstab | grep -v '^[ \t]*#' | grep '/boot'
UUID=40106063-e707-41a9-b1c5-34e25180dc9e       /boot   ext2    defaults        0       2
UUID=F3C4-5323  /boot/efi       vfat    defaults        0       1

```

This should only bring up one line, right?

---

### Post by terminator14 on 2014-11-13
> **michael232 said:**
> I have a similar issue here. The boot check seems to fail:
rupdate around line 140:

```

> cat $Orig_OS/etc/fstab | grep -v '^[ \t]*#' | grep '/boot'
UUID=40106063-e707-41a9-b1c5-34e25180dc9e       /boot   ext2    defaults        0       2
UUID=F3C4-5323  /boot/efi       vfat    defaults        0       1

```

This should only bring up one line, right?

Yup - an oversight on my part.
The fix ended up being 5 characters long, and I've updated both the 14.04 and 14.10 scripts, but applying it might be a bit more difficult. The procedure is almost the same as the one a few posts up, but here it is:

Note: Here, I assume you're using Ubuntu 14.04. Substitute "14.10" where I used "14.04" if you're not.

You basically have 2 choices for applying the fix. They are:

1. Reinstall the RAM_booster script
[INDENT][LIST=1]
[*]Boot into Original OS
[*]open terminal
[*]cd into script folder
[*]run "sudo ./RAM_booster_Ubuntu_14.04.sh --uninstall" to remove your RAM Session completely
[*]run "git pull" to download the updated scripts from github automatically
[*]run "sudo ./RAM_booster_Ubuntu_14.04.sh" to install again
[/LIST][/INDENT]

2. Replace the old rupdate script with the new one manually
[INDENT][LIST=1]
[*]Boot into RAM Session
[*]Open "/usr/sbin/rupdate" with a text editor
[*]Write down line 13 - the one that looks like this:
```
REG_DEVICE="/dev/sdXY"
```
[*]Close text editor and delete /usr/sbin/rupdate
[*]Download the rupdate script attached below, extract it, and place it in /usr/sbin/
[*]Run "sudo chown root:root /usr/sbin/rupdate; sudo chmod 755 /usr/sbin/rupdate" to change the ownership and permissions of /usr/sbin/rupdate to what they should be
[*]Open "/usr/sbin/rupdate" with a text editor
[*]Replace line 13 with the one you wrote down earlier
[*]Save and exit text editor
[*]Run "sudo rchroot -R"
[*]Delete /usr/sbin/rupdate
[*]Open a new terminal window
[*]Delete /mnt/Original_OS/var/squashfs/usr/sbin/rupdate
[*]Place the rupdate that you just downloaded and extracted (the one attached below) into /mnt/Original_OS/var/squashfs/usr/sbin/
[*]Close this new terminal window, and go back to the original one (the one where you ran "sudo rchroot -R")
[*]Run "sudo chown root:root /usr/sbin/rupdate; sudo chmod 755 /usr/sbin/rupdate" to change the ownership and permissions of /usr/sbin/rupdate to what they should be
[*]Open "/usr/sbin/rupdate" with a text editor
[*]Replace line 13 with the one you wrote down earlier
[*]Save and exit text editor
[*]Run "exit" to exit the chroot
[*]Run "sudo rupdate -f" to recreate the squashfs image with the new rupdate script
[*]Reboot
[/LIST]
[/INDENT]

---

### Post by michael232 on 2014-11-19
Thanks for your patch. Problem solved!

---

### Post by magnus.overli on 2014-12-10
Hi! I have just tried your script this morning, and it seems to do exactly what I expected. I have however run into a problem. I cannot seem to save changes done to files in /etc/. 

More specifically, after initially running the script my network interfaces were offline.
/etc/network/interfaces had changed from the Original_OS and did not define my interfaces anymore. At this point I rchrooted into /var/squashfs and tried to edit the file. But that file was as it should be. I did an sudo rupdate --force, rebooted, but this did not change anything. It seems that the /etc/ is synced from somewhere else? Or that is at least what the symptoms are pointing towards. 

Heads up though, this is not my field of expertise! :-) Would appreciate any insight on this issue.

Regards
Magnus

---

### Post by terminator14 on 2014-12-10
For over a month now, several hours a day, I've been rewriting the RAM Booster script, and all accompanying scripts, almost from scratch. It is approaching 500 git commits, and should now be able to handle almost any Ubuntu configuration you can think of: LVM, Encrypted filesystems, Encrypted user home directories, etc. It also addresses many problems with the current code (upstart chroots, kernel updates, etc.). I am a few days away from releasing it - I even have the video explaining how it all works already recorded. Although I did not directly address this issue in the new code, there's a good chance that things like my usage of proper upstart chroots fixes this problem.

It sounds like you have a pretty good grasp of how everything is supposed to work, and are experiencing the same problem that someone posted a while back, about the interfaces file changing in the RAM Session from what it was in the Original OS. I spent a few hours trying to track it down, and although I could reproduce it, the best solution (workaround) I could find at the time is this:

[http://ubuntuforums.org/showthread.php?t=1594694&page=30&p=13141912#post13141912](http://ubuntuforums.org/showthread.php?t=1594694&page=30&p=13141912#post13141912)

I will see if my new script experiences the problem as well, and if so, find what is causing it and make a proper fix.
Either try the workaround above, or check back in a few days and try the new script - hopefully it will not suffer from the same problem, especially now since I'll be looking into it specifically.

---

### Post by magnus.overli on 2014-12-10
> **terminator14 said:**
> For over a month now, several hours a day, I've been rewriting the RAM Booster script, and all accompanying scripts, almost from scratch. It is approaching 500 git commits, and should now be able to handle almost any Ubuntu configuration you can think of: LVM, Encrypted filesystems, Encrypted user home directories, etc. It also addresses many problems with the current code (upstart chroots, kernel updates, etc.). I am a few days away from releasing it - I even have the video explaining how it all works already recorded. Although I did not directly address this issue in the new code, there's a good chance that things like my usage of proper upstart chroots fixes this problem.

It sounds like you have a pretty good grasp of how everything is supposed to work, and are experiencing the same problem that someone posted a while back, about the interfaces file changing in the RAM Session from what it was in the Original OS. I spent a few hours trying to track it down, and although I could reproduce it, the best solution (workaround) I could find at the time is this:

[http://ubuntuforums.org/showthread.php?t=1594694&page=30&p=13141912#post13141912](http://ubuntuforums.org/showthread.php?t=1594694&page=30&p=13141912#post13141912)

I will see if my new script experiences the problem as well, and if so, find what is causing it and make a proper fix.
Either try the workaround above, or check back in a few days and try the new script - hopefully it will not suffer from the same problem, especially now since I'll be looking into it specifically.

Thanks so much for taking the time to answer my request! Means a lot!
And also, thanks for providing the workaround, even though you seem to have a possible fix in the next release. I noticed in your git repo that a new release might be in the works, but I didn´t expect it to be this close! I will (try) to leave things as is for the time being, and I am looking forward to test the upcoming release! 

Great idea! Good work! 
 
:-)

---

### Post by terminator14 on 2014-12-10
> **magnus.overli said:**
> I cannot seem to save changes done to files in /etc/. 

More specifically, after initially running the script my network interfaces were offline.
/etc/network/interfaces had changed from the Original_OS and did not define my interfaces anymore.

I took a look, and it turns out the new script had the same problem. Turns out, live-boot, the main component that makes copying a squashfs image into ram at boot possible, replaces the /etc/network/interfaces file by default at boot.
I made sure that this is fixed in the new script, and appreciate you bringing this to my attention.

I know you said you'll probably wait for the new script, but in case you want to give fixing it a quick try, this should do it:

[LIST]
[*]Boot into your Original OS
[*]Edit /etc/grub.d/06_RAMSESS
[*]Edit the line that starts with "linux" and add this parameter to the end:
[INDENT]ip=frommedia[/INDENT]
[*]Save the file and exit the editor
[*]Run "sudo update-grub" to update the grub boot menu
[/LIST]

I have NOT tested if this will work on the old script (what you're using), but in theory, that should fix it.
Or, of course, you could wait for the new script, which I have tested the fix on, which works great.
Note: Even if you try the fix above and it works, I still suggest coming back in a couple of days to get the new script for all the other improvements it will have.

---

### Post by magnus.overli on 2014-12-11
Quick work! :-)

 I am glad you found out what the problem was, and that you were able to fix it. I am, as you pointed out, running the old script and I have also applied the previously suggested workaround. This is now working and running fine. I appreciate that you encourage me to try the fix you have come up with, but as my system is now working as intended, I will wait for the new script and try it out. However, if you need I can set up a second box that mimics my system and try it out for you...

---

### Post by terminator14 on 2014-12-11
> **magnus.overli said:**
> Quick work! :-)

 I am glad you found out what the problem was, and that you were able to fix it. I am, as you pointed out, running the old script and I have also applied the previously suggested workaround. This is now working and running fine. I appreciate that you encourage me to try the fix you have come up with, but as my system is now working as intended, I will wait for the new script and try it out. However, if you need I can set up a second box that mimics my system and try it out for you...

I appreciate the offer, but I was able to reproduce the problem because I figured out what was causing it, and know that the fix works on the new script. The only thing I didn't know was whether it worked on the old script, which I'll end support for in a few days with the release of the new one, so I'm not overly concerned about it - as long as it works for you. When I do release the new code, if it's still a problem, then I'll really want to know, but I'm 99% sure it won't be.

---

### Post by terminator14 on 2014-12-17
Finally, the new script is released. For anyone reading this, see the original post on page 1 for updated instructions and video.

---

### Post by ibjsb4 on 2014-12-17
I been following this thread.

Lots of work went into this.

Go show :)

---

### Post by oldos2er on 2014-12-18
I may give this a try this weekend. Thank you terminator14 for all your hard work!

---

### Post by sudodus on 2014-12-18
> **ibjsb4 said:**
> I been following this thread.

Lots of work went into this.

Go show :)

+1

Thanks for sharing the result or your good work :KS

---

### Post by terminator14 on 2014-12-19
Thanks guys!

After a month of coding, I'm curious to know if it works for people as well as it worked for me in testing.
Anyone have a chance to try it out?

---

### Post by Sithuk on 2014-12-25
My RAM_booster installation attempt failed because live-boot-initramfs-tools failed to install.

I've tried the latest 14.10 script with Xubuntu 14.10, and also the 14.04.01 script with Xubuntu 14.04.01. I appreciate that the error is not likely to be an error with terminator14's script, but rather an issue with the live-boot-initramfs-tools package installation. I have tried the installation of the package directly on fresh installs of both 14.04.01 and 14.10, and the package fails to install. Does anyone know how I might be able to get around the package installation error for live-boot-initramfs-tools?

I do the following to produce the package installation error directly. I used VirtualBox as a working environment.
1. Create Xubuntu 14.04.01 persistent Live installation using unetbootin.
2. Boot the installation and choose "Try Xubuntu without installing" from the menu. 
3a. Open terminal emulator and enter the following commands.
3b. sudo apt-get update
3c. sudo apt-get install live-boot-initramfs-tools

The package installation error follows below.

```
xubuntu@xubuntu:~$ sudo apt-get install live-boot-initramfs-tools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  live-boot-initramfs-tools
0 upgraded, 1 newly installed, 0 to remove and 258 not upgraded.
Need to get 5,774 B of archives.
After this operation, 66.6 kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/universe live-boot-initramfs-tools all 3.0.1-1 [5,774 B]
Fetched 5,774 B in 0s (13.2 kB/s)              
Selecting previously unselected package live-boot-initramfs-tools.
(Reading database ... 155215 files and directories currently installed.)
Preparing to unpack .../live-boot-initramfs-tools_3.0.1-1_all.deb ...
Unpacking live-boot-initramfs-tools (3.0.1-1) ...
Setting up live-boot-initramfs-tools (3.0.1-1) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.103ubuntu4.2) ...
update-initramfs: Generating /boot/initrd.img-3.13.0-32-generic
cryptsetup: WARNING: failed to detect canonical device of overlayfs
cryptsetup: WARNING: could not determine root device from /etc/fstab
live-boot:
W: live-boot-initramfs-tools (backend) installed without live-boot,
W: this initramfs will *NOT* have live support.
/tmp/mkinitramfs_JYqno7/scripts/casper-bottom/48xubuntu_maybe_ubiquity: 6: .: Can't open /scripts/casper-functions
lzma: (stdin): Cannot allocate memory
dpkg: error processing package initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
E: Sub-process /usr/bin/dpkg returned an error code (1)
xubuntu@xubuntu:~$
```

---

### Post by oldos2er on 2014-12-25
Been using it for a few days now. I had to switch from systemd back to upstart. When running the script under systemd, it didn't recognize that I had squashfs-tools already installed, and would abort with a msg to install it. Changing back to upstart fixed that, and the script completed successfully.

---

### Post by Sithuk on 2014-12-25
> **oldos2er said:**
> Been using it for a few days now. I had to switch from systemd back to upstart. When running the script under systemd, it didn't recognize that I had squashfs-tools already installed, and would abort with a msg to install it. Changing back to upstart fixed that, and the script completed successfully.

Can you post the sequence of commands that you entered to "switch from systemd back to upstart"?

---

### Post by schragge on 2014-12-25
@**oldos2er**: Weird. From looking at the source of RAM booster, any interference between it and systemd or upstart at that point in execution seems extremely unlikely. I'd rather think of some subtle glitch in dpkg or apt databases going away as a side effect of replacing systemd with upstart. Perhaps just *apt-get check* or *apt-get clean* or similar would have the same effect on RAM booster as replacing the init daemon. RAM booster keeps its log in /var/log/ram_booster.log. Unfortunately, it gets overwritten on each new call, so any hints to the possible apt-get glitch are probably lost by now.

---

### Post by oldos2er on 2014-12-25
Yeah, I'm not a programmer, but I don't understand what connection or conflict there might be between systemd and the ram booster script. I just changed to upstart on a hunch.

---

### Post by terminator14 on 2014-12-25
> **Sithuk said:**
> My RAM_booster installation attempt failed because live-boot-initramfs-tools failed to install.

I've tried the latest 14.10 script with Xubuntu 14.10, and also the 14.04.01 script with Xubuntu 14.04.01. I appreciate that the error is not likely to be an error with terminator14's script, but rather an issue with the live-boot-initramfs-tools package installation. I have tried the installation of the package directly on fresh installs of both 14.04.01 and 14.10, and the package fails to install. Does anyone know how I might be able to get around the package installation error for live-boot-initramfs-tools?



The script was never tested with Xubuntu, but I imagine it should probably have no problems working.
I quickly downloaded Xubuntu 14.04.1 and 14.10, and both seem to install live-boot-initramfs-tools fine without unetbootin.
Whatever unetbootin does seems to make live-boot-initramfs-tools unhappy with it.
Are you planning to run the RAM_Booster script from a live environment? It was designed to run from a regular install - I'm not entirely sure how it would behave in a live environment, but at the very least, I would imagine that when it starts copying the entire system to /var/squashfs, you'll run out of RAM (unless you have a huge amount). The redit and rupdate scripts will also probably fail, since /var/squashfs will not exist when you reboot. Neither will /live/filesystem.squashfs come to think of it, so unless you move it somewhere and modify grub manually, I'm pretty sure it won't boot at all. If this is the case, installing live-boot-initramfs-tools is the least of your worries.

> **oldos2er said:**
> Been using it for a few days now. I had to switch from systemd back to upstart. When running the script under systemd, it didn't recognize that I had squashfs-tools already installed, and would abort with a msg to install it. Changing back to upstart fixed that, and the script completed successfully.

What process did you use to install systemd?
Also, as schragge said, at that point, it seems difficult to imagine how systemd would interfere with the script's ability to tell if squashfs-tools are installed.
If you plan to try this with systemd again, you might try running this command, which is what the script does to try to figure out if squashfs-tools are installed:

```
sudo apt-get -y --force-yes install squashfs-tools
```

or, as schragge said, simply check the log after running RAM Booster with systemd installed.

---

### Post by oldos2er on 2014-12-25
I installed systemd with apt-get install, as far as I remember, and enabled it with "GRUB_CMDLINE_LINUX_DEFAULT="quiet splash init=/lib/systemd/systemd" " in /etc/default/grub.

---

### Post by terminator14 on 2014-12-25
> **oldos2er said:**
> I installed systemd with apt-get install, as far as I remember, and enabled it with "GRUB_CMDLINE_LINUX_DEFAULT="quiet splash init=/lib/systemd/systemd" " in /etc/default/grub.

I tried installing systemd with

```
sudo apt-get install systemd-sysv
```

which said that it automatically removed upstart too. I didn't have to make the change in /etc/default/grub. It seemed to work, and my script got passed the squashfs-tools install section.
Not sure what happened with yours. If you run into the problem again, post back and we'll try to figure out what happened.

---

### Post by Sithuk on 2014-12-26
> 
Are you planning to run the RAM_Booster script from a live environment?  It was designed to run from a regular install - I'm not entirely sure  how it would behave in a live environment, but at the very least, I  would imagine that when it starts copying the entire system to  /var/squashfs, you'll run out of RAM (unless you have a huge amount).

The main reason for looking into RAM_booster was because I found running a persistent Live install off a USB stick to be frustratingly slow. I was hoping to load a Xubuntu Live install into the RAM of a 4GB RAM machine. A fresh Live install takes up approximately 2GB with Xubuntu. Why is a Live install likely to need more RAM than loading a full install into RAM?

I had already written off the RAM_booster approach because of the live-boot-initramfs-tools installation issue. I was going to keep a watch incase of an Ubuntu update which resolved the live-boot-initramfs-tools issue, but if RAM booster is not likely to be useful to speed up a Live persistent USB install then perhaps it is not what I'm looking for.

---

### Post by sudodus on 2014-12-26
Maybe *terminator14*'s method will work with a system installed into a USB 3 pendrive. See this link (and links from it)

[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)

---

### Post by ibjsb4 on 2014-12-26
I installed a vanilla u14.04 to ramboost.  Gave it 2G of ram out of 4, and included the home folder.  This was a ubuntu-desktop install without the recommended packages, that was updated.  In the end, the ram_booster installer said that I only used 816M of ram.  

I really like the increase in performance on this dual core vm.  Now I want to add it to my same spec laptop.  This time I shall give ram_booster 1.5G, that should be enough.  I think this will breath some fire into my dual core laptop.

THANKYOU

ps
Any chance of this working in Mate?

---

### Post by schragge on 2014-12-26
Is MATE more of a memory hog than Unity? Don't think so. Then I don't see why it shouldn't work in MATE.

---

### Post by terminator14 on 2014-12-26
> **ibjsb4 said:**
> ... THANKYOU

Good to head that it's working for people. Thanks for the reply.

> **ibjsb4 said:**
> Any chance of this working in Mate?

It's untested, but as schragge pointed out, it should.

---

### Post by terminator14 on 2014-12-26
> **Sithuk said:**
> Why is a Live install likely to need more RAM than loading a full install into RAM?

AFAIK, a live system usually uses something like aufs to merge a squashfs image and RAM. Anything you store gets written directly to RAM, so it uses more RAM than a regular system.
I suppose that a persistent system stores things on USB, so it might not use more RAM than a regular system.
Either way, even if you managed to install live-boot-initramfs-tools, there are differences between it, and a regular system.
The grub menu used by RAM Booster may or may not work with a USB drive as the root partition.
live-boot may or may not work using a USB drive as the place filesystem.squashfs is stored.
rupdate/redit may or may not have trouble mounting drives that are on a USB drive.

Either way, RAM Booster is probably not what you're after. What you want is a ToRAM option on your live disk:

[http://ubuntuforums.org/showthread.php?t=1603423]("http://ubuntuforums.org/showthread.php?t=1603423")

the project is pretty old, but it might still work on the new live CDs.

---

### Post by ibjsb4 on 2014-12-26
In post #1
> Support for other distros (at the very least - Linux Mint)
Took that to mean unsupported at this time.

So anyhow I have installed it on mate 14o4 and is working well.  Total amount of ram used is 1.6G and I again left home in ram.  I also have mate on my laptop, this is where I will first install it.  Hopefully this weekend.

---

### Post by terminator14 on 2014-12-27
> **ibjsb4 said:**
> In post #1

Took that to mean unsupported at this time.

So anyhow I have installed it on mate 14o4 and is working well.  Total amount of ram used is 1.6G and I again left home in ram.  I also have mate on my laptop, this is where I will first install it.  Hopefully this weekend.

There's a difference between Linux Mint, and Ubuntu running Mate.
The script was tested on neither, but in theory probably works. Glad to hear it worked for you.

---

### Post by ibjsb4 on 2014-12-27
> There's a difference between Linux Mint, and Ubuntu running Mate.
Good point, yes there are differences and I do tend to bundle them.  So encase others are wondering, I have installed Mate (all 14.04) to ubuntu using the ppa with ram_booster.  

and ..
I now have ram_boost running in mate on my laptop (using the live dvd install from the mate site).    

Too soon for forming any solid opinions on performance, but I like how easy ram_booster installs.  Also a nice touch being able to switch between the two installs at boot.  Makes comparing easy.

My hdd is hardly being used, a big plus on a laptop.  However boot to ram adds 23 seconds to boot (1.5G to be loaded).  Ubuntu-desktop (no-depends) took only 800M with the Flashback desktop installed.  So I think there is room for improvement.  I also need to clean up my partitioning and create a separate home, but for now I can play with this.

---

### Post by ibjsb4 on 2014-12-28
Ok, I love it :)  My laptop findings:

I did not get the expected results.  My thinking was extreme performance boost with everything in ram.  What I got was a modest to fast performance boost over the entire system.  Everything is faster.  I would guess that code of the software I use is now a bottle neck, slowing ram down.

The HDD now occasionally blinks, its usage is next to zero.  This I love and wonder how much extra battery life I will get.

So far ram_booster has proven unbreakable.  I have remove xorg, desktop and others.  Then with a reboot have returned to the default install.  With no hard disk interaction, I think will be great for testing/playing.

I have done this on a total of 4G of ram.  Wish I had a couple of more G, but I'm getting by.  Now I want to try this on my desktop machine.  Its already fast, so I wonder what ram_booster will do.  I also want to see how a large music collection (4/5G) will do in ram.  I want to do this on a fresh install of .. something ..  Have to give that some thought.

Later

---

### Post by terminator14 on 2014-12-29
> **ibjsb4 said:**
> So far ram_booster has proven unbreakable.

That's what I like to hear :)
To be clear, are you using the new RAM_booster_Ubuntu_14.10_ng.sh version, or the old RAM_booster_Ubuntu_14.04.sh version?

---

### Post by ibjsb4 on 2014-12-29
I run only /old/RAM_booster_Ubuntu_14.04.sh version.  Can I run 14.10_ng.sh on 14.04?

I was curious how much ram Lubuntu would take, so I loaded ram_booster to a vanilla Lu 14.04 and it used 770M (with home).

---

### Post by terminator14 on 2014-12-29
> **ibjsb4 said:**
> I run only /old/RAM_booster_Ubuntu_14.04.sh version.  Can I run 14.10_ng.sh on 14.04?

I was curious how much ram Lubuntu would take, so I loaded ram_booster to a vanilla Lu 14.04 and it used 770M (with home).

There are several issues that the old 14.04 script, and even the old 14.10 script had that the new 14.10_ng.sh script addresses.
My plan was to test the 14.10_ng script with Ubuntu 14.04 to see if there would be any problems, but considering how many options my script can handle (different partition layouts, encrypted home partitions, encrypted filesystems, xfs, ext4, lvm, detecting btrfs, etc), trying every possibility on 14.04 would require quite a bit of time, mostly of installing Ubuntu over and over again, which becomes insanely boring really fast. I haven't gotten around to it yet.
If you feel adventurous, I would suggest giving it a try.

---

### Post by ibjsb4 on 2014-12-30
Ok, didn't realize I had the option to test 14.10_ng.sh.  So I guess its time to reinstall everything :)  I want the new and not the old.

---

### Post by ibjsb4 on 2014-12-31
Finally got around to my desktop computer.

I installed RAM_booster_Ubuntu_**14.10_ng.sh** to a fresh install **Ubuntu 14.04** and again running fine.  I think some software uses ram_booster better than others.  Rhythmbox still takes a moment to load a large collection, but VLC loads instantly.  Gimp has nicely improved in performance.  LibreOffice opens a little faster.  So I guess mileage will vary, but its been a positive experience for me.

Some programs do open a little faster when opened the second time.

I also noticed old kernels being loaded to ram, so this install has only one kernel installed.  This ram_booster install is using 877M of ram to load my 3.1G ubuntu install w/home.

In conclusion
I have installed ram_booster in different configurations (Lubuntu, Ubuntu, Mate) and found it stable.  I like the results of ram_booster and plan to properly set it up for use on my laptop using a separate home directory.

I say ram_booster is well worth trying.  Thanks again

---

### Post by terminator14 on 2015-01-01
> **ibjsb4 said:**
> Finally got around to my desktop computer.

I installed RAM_booster_Ubuntu_**14.10_ng.sh** to a fresh install **Ubuntu 14.04** and again running fine.  I think some software uses ram_booster better than others.  Rhythmbox still takes a moment to load a large collection, but VLC loads instantly.  Gimp has nicely improved in performance.  LibreOffice opens a little faster.  So I guess mileage will vary, but its been a positive experience for me.

Some programs do open a little faster when opened the second time.

I also noticed old kernels being loaded to ram, so this install has only one kernel installed.  This ram_booster install is using 877M of ram to load my 3.1G ubuntu install w/home.

In conclusion
I have installed ram_booster in different configurations (Lubuntu, Ubuntu, Mate) and found it stable.  I like the results of ram_booster and plan to properly set it up for use on my laptop using a separate home directory.

I say ram_booster is well worth trying.  Thanks again

Awesome! Your feedback is much appreciated!
Happy Holidays!

---

### Post by robert144 on 2015-01-03
Hi there,

thanks a lot to your effort in this project. Knowing that Linux Mint 17 is not supported (yet), i gave it a go with the Ubuntu 14.04 script. Everything seems to be working fine, except that it does not know the "redit" and "rupgrade" script. "rupdate" is working. Do you have a hint for me, how i could get this working?

Thanks in advance.

kind regards,

robert

---

### Post by terminator14 on 2015-01-03
> **robert144 said:**
> Hi there,

thanks a lot to your effort in this project. Knowing that Linux Mint 17 is not supported (yet), i gave it a go with the Ubuntu 14.04 script. Everything seems to be working fine, except that it does not know the "redit" and "rupgrade" script. "rupdate" is working. Do you have a hint for me, how i could get this working?

Thanks in advance.

kind regards,

robert

Only the new 14.10_ng script has the redit and rupgrade scripts.
All scripts in the old directory use the older rchroot script, which does a similar thing to redit but works differently, 
and has no way to install script updates (no rupgrade script at all).
The new 14.10_ng script addresses several issues with the old scripts, so it is recommended that
you try running it instead, even if it's on 14.04.

---

### Post by ibjsb4 on 2015-01-03
As we speak, I am running RAM_booster_14.10_ng.sh on Mate 14.04.

If size is a constrain, I suggest cleaning first.  BleachBit works for me.  Localpurge to remove extra languages.  Remove old kernels and packages you don't use.  My first install of ram_booster to a existing Mate install used 1.5G of ram.  I was able to get my second install down to 1.1G of ram (with extra packages like gimp and vlc).

---

### Post by terminator14 on 2015-01-03
> **ibjsb4 said:**
> As we speak, I am running RAM_booster_14.10_ng.sh on Mate 14.04.

If size is a constrain, I suggest cleaning first.  BleachBit works for me.  Localpurge to remove extra languages.  Remove old kernels and packages you don't use.  My first install of ram_booster to a existing Mate install used 1.5G of ram.  I was able to get my second install down to 1.1G of ram (with extra packages like gimp and vlc).

What's your setup like? Encrypted filesystem? Encrypted home directories? LVM?
Is /boot on the same partition as /, or separate? GPT/MBR?

---

### Post by ibjsb4 on 2015-01-03
Hi terminator14

This is a standard install using ext4, default boot partitioning, no efi, no encryption.

---

### Post by cigtoxdoc on 2015-01-04
Yesterday, I installed your software (14.04 64-bit).  Runs fine, except for a mistake I made that is causing *Ubuntu to RAM to have the incorrect fstab and regular Ubutnu to have the correct fstab.  Your program redit as you noted.  I your alternate approach of rupdate --force, and it errored out saying something like it could not do a mkdir.

So, I went to unstall your software.  Not so easy.  You have to rerun the install script to get the uninstall.

Now I am installing the 14.10 script.  I had already set /dev/sda2 to /home a partition I established to get rid of my previous error.  System isntalled, BUT, it loads the RAM file slowly, and essentailly locks the system.

John

---

### Post by terminator14 on 2015-01-04
> **cigtoxdoc said:**
> So, I went to unstall your software.  Not so easy.  You have to rerun the install script to get the uninstall.

Is it really that hard? You just explained how to do it in one short sentence... The uninstall procedure is mentioned in both my original post, and the video.

> **cigtoxdoc said:**
> Now I am installing the 14.10 script.  I had already set /dev/sda2 to /home a partition I established to get rid of my previous error.  System isntalled, BUT, it loads the RAM file slowly, and essentailly locks the system.

When you say 14.10 script, I hope you mean the 14.10_ng script, which is the new one. Don't use the old 14.10 script (the one in the old/ directory).
Do you have enough RAM to fit the image and have some left over?

---

### Post by cigtoxdoc on 2015-01-05
Thank you for your reply.  The 14.10_ng was not usable on my PC.  Appeared to be a major problem with the Intel graphics embedded with the Intel i7-4770K processor.  Your 14.04 software works very well with the same PC.

John

---

### Post by terminator14 on 2015-01-05
> **cigtoxdoc said:**
> Thank you for your reply.  The 14.10_ng was not usable on my PC.  Appeared to be a major problem with the Intel graphics embedded with the Intel i7-4770K processor.  Your 14.04 software works very well with the same PC.

John

Any information you can provide for why exactly the 14.10_ng script wasn't working may help me make sure that it works in the future.
What was the problem? Did it show an error? Did it die while installing RAM Booster, or when trying to boot the RAM Session?
Do you have the /var/log/ram_booster.log on your Original OS from when the 14.10_ng script failed? It might have some useful info.
If it exists, please look through it, and if you see nothing confidential, please consider uploading it - it might help me figure out the problem.
If the Intel graphics of the i7-4770k really is the problem, it might be difficult for me to reproduce the problem since I don't have the same hardware,
but knowing what exactly failed might help me spot the problem anyway.

---

### Post by robert144 on 2015-01-05
> **terminator14 said:**
> Only the new 14.10_ng script has the redit and rupgrade scripts.
All scripts in the old directory use the older rchroot script, which does a similar thing to redit but works differently, 
and has no way to install script updates (no rupgrade script at all).
The new 14.10_ng script addresses several issues with the old scripts, so it is recommended that
you try running it instead, even if it's on 14.04.

Hi,

i have tried it with the 14.10 script. When i run "redit" with sudo it tells me the following

Failed to mount df382bce-b35b-464f-a5b9-c83cf23e5bd2 to /mnt/Original_OS/
Failed to unmount chroot
Scanning for processes holding it up...

None found 


any ideas?

---

### Post by terminator14 on 2015-01-05
> **robert144 said:**
> Hi,

i have tried it with the 14.10 script. When i run "redit" with sudo it tells me the following

Failed to mount df382bce-b35b-464f-a5b9-c83cf23e5bd2 to /mnt/Original_OS/
Failed to unmount chroot
Scanning for processes holding it up...

None found 


any ideas?

Everything after the first line ("Failed to mount") is a bit of an oversight - it failed to mount the base OS so it shouldn't be trying to unmount it. It's not a big deal, but I'll fix that.
Your main problem is the fact that it can't mount your Original OS to /mnt/Original_OS.
What happens when you try to run this in the RAM Session?:
```
sudo mount --uuid df382bce-b35b-464f-a5b9-c83cf23e5bd2 /mnt/Original_OS/
```

If /mnt/Original_OS/ doesn't exist, try:

```
sudo mount --uuid df382bce-b35b-464f-a5b9-c83cf23e5bd2 /mnt/
```

Do you get any errors?

It might also be helpful if you could upload /var/log/ram_booster.log from the Original OS. This might help me reproduce the problem.

---

### Post by cigtoxdoc on 2015-01-05
I am trying this on a second PC that has Ubuntu 14.04 64-bit as OS.  Everything went fine until I told your software that I wanted your /home on /dev/sda8.  It told me that my choice was not valid.  An image of gparted is attached.  Looks like the same situation as worked on first PC.

Thank you,

John

---

### Post by terminator14 on 2015-01-05
> **cigtoxdoc said:**
> I am trying this on a second PC that has Ubuntu 14.04 64-bit as OS.  Everything went fine until I told your software that I wanted your /home on /dev/sda8.  It told me that my choice was not valid.  An image of gparted is attached.  Looks like the same situation as worked on first PC.

Thank you,

John

Are you still using one of the scripts in the "old" folder?
Try 14.10_ng.

---

### Post by cigtoxdoc on 2015-01-05
Thank you for your reply.

I used the script from the "old" folder based on the experience with the previous PC.  I will try the newer script tomorrow.

John

---

### Post by robert144 on 2015-01-06
> **terminator14 said:**
> Everything after the first line ("Failed to mount") is a bit of an oversight - it failed to mount the base OS so it shouldn't be trying to unmount it. It's not a big deal, but I'll fix that.
Your main problem is the fact that it can't mount your Original OS to /mnt/Original_OS.
What happens when you try to run this in the RAM Session?:
```
sudo mount --uuid df382bce-b35b-464f-a5b9-c83cf23e5bd2 /mnt/Original_OS/
```

If /mnt/Original_OS/ doesn't exist, try:

```
sudo mount --uuid df382bce-b35b-464f-a5b9-c83cf23e5bd2 /mnt/
```

Do you get any errors?

It might also be helpful if you could upload /var/log/ram_booster.log from the Original OS. This might help me reproduce the problem.

Ok, the problems seems to be mount --uuid . It wants to be mount -U uuid . But after i successfully mounted to /mnt/Original_OS the "redit" and "rupdate" give me 

"Failed to mount RAM Session. Is it already mounted?"

   Well, yes. It is already mounted. It needs to be or not? The command as far as i unterstood, is to update the image, after modifying any settings in the RAM session, am i right?

---

### Post by terminator14 on 2015-01-06
> **robert144 said:**
> Ok, the problems seems to be mount --uuid . It wants to be mount -U uuid . But after i successfully mounted to /mnt/Original_OS the "redit" and "rupdate" give me 

"Failed to mount RAM Session. Is it already mounted?"

   Well, yes. It is already mounted. It needs to be or not? The command as far as i unterstood, is to update the image, after modifying any settings in the RAM session, am i right?

The redit command lets you modify the image because any modifications in the RAM Session do not get written to the image.
If this is unclear, check out the video if you haven't seen it:

[https://www.youtube.com/watch?v=pmqxDfdtDKg&feature=youtu.be](https://www.youtube.com/watch?v=pmqxDfdtDKg&feature=youtu.be)

As for the problem you've been running into:

The 14.10_ng script was written for Ubuntu 14.10, where the mount command man page looks like this:

```
-U, --uuid _uuid_
```

I just noticed that Ubuntu 14.04's man page looks like this:

```
-U _uuid_
```

Apparently, the version change of the mount command between Ubuntu 14.04 and Ubuntu 14.10 added the --uuid argument, which I use in my scripts.
I just changed all my scripts to use -U instead of --uuid.
If you run:

```
sudo rupgrade
```

in the RAM Session, it should complain about failing to mount the Original OS, then update itself to a version that uses -U, then automatically run the new version and update all the other scripts.
If that doesn't work, let me know.
Thanks for helping me catch that.

---

### Post by robert144 on 2015-01-07
rupgrade
A script for Ubuntu 14.04.1 LTS could not be found in the github RAM Booster repo

---

### Post by terminator14 on 2015-01-07
> **robert144 said:**
> rupgrade
A script for Ubuntu 14.04.1 LTS could not be found in the github RAM Booster repo

It's fixed. Sort of.
You should now be able to run "sudo rupgrade" to update the scripts, but after fixing the above problem, I noticed more trouble. Ubuntu 14.04's umount command also doesn't have the -R argument that Ubuntu 14.10 uses.
This prevents redit from exiting properly, causing it to spit out errors. It probably effects the other scripts too, but I haven't tried those yet.
Unfortunately, this is a bigger problem than --uuid, since there's no equivalent in Ubuntu 14.04 to -R. I'm going to need to write some code to get duplicate the functionality.
I guess my assumption that the script would probably work on 14.04 without any problems was just wishful thinking.
It's 2am here, so I'm going to have to do that tomorrow. After that, I'll probably actually try my script on 14.04 to see if I run into any more problems.
I might not test every option, but at least I can make sure that the basics work.

---

### Post by robert144 on 2015-01-07
alright. Thanks for your help.

rupgrade
Failed to mount RAM Session. Is it already mounted?

I think the best is to get some sleep and try it again :)

---

### Post by terminator14 on 2015-01-07
> **robert144 said:**
> rupgrade
Failed to mount RAM Session. Is it already mounted?

The script doesn't check what you already have mounted - even if it's what's supposed to be mounted.
If something is already mounted, it exits. This is by design.
If you have something mounted there from earlier, either unmount it manually, or reboot. Then try "sudo rupgrade".
I made some more changes, and the umount problem I mentioned earlier should now be fixed in the new versions of the scripts (which get installed by rupgrade).

---

### Post by cigtoxdoc on 2015-01-10
There are several less than friendly issues with this software.  First, if you use SpiderOak or PDFStudioPro, you DO NOT want to use separate directories for /home.  Both of the programs I mentioned consider the second /home to be another unique PC.  Second, if the program is uninstalled or exits without completion (see attachments), it can leave a mess.  When I realized the first installation of RAM_booster_Ubuntu_14.10_ng.sh resulted in "Ubuntu_to_RAM" left out SpiderOak and PDFStudioPro, I installed the program using the dialog that says you need to unistall before beginning a second installation.  I did that only to have the second installation (no separate /home) fail and leave a mess.  I have attached a copy of the latest log file.

How should one recover from this situation so that everything was like it would have been before the first time trying to install the script?

Thank you

John

---

### Post by terminator14 on 2015-01-10
> **cigtoxdoc said:**
> There are several less than friendly issues with this software.  First, if you use SpiderOak or PDFStudioPro, you DO NOT want to use separate directories for /home.  Both of the programs I mentioned consider the second /home to be another unique PC.  Second, if the program is uninstalled or exits without completion (see attachments), it can leave a mess.  When I realized the first installation of RAM_booster_Ubuntu_14.10_ng.sh resulted in "Ubuntu_to_RAM" left out SpiderOak and PDFStudioPro, I installed the program using the dialog that says you need to unistall before beginning a second installation.  I did that only to have the second installation (no separate /home) fail and leave a mess.  I have attached a copy of the latest log file.

How should one recover from this situation so that everything was like it would have been before the first time trying to install the script?

Thank you

John

when_things_go_wrong_Making_Ubuntu_Fast_using_RAM (updated and simplified).pdf
[INDENT]All I see there is the regular install process, which fails to complete because your root partition ran out of space in the middle of creating /live/filesystem.squashfs
Sure, it didn't automatically remove everything at that point, but running the script again will detect that it ran and offer to remove everything
[/INDENT]GParted after failed Fast RAM install.pdf
[INDENT]The only thing I see there is that /mnt/root is mounted, which the script did
To fix it, you would either:
[/INDENT]
[LIST=1]
[*]unmount /mnt/root and delete the folder
OR
[*]reboot and delete the folder
OR
[*]just run the RAM_Booster script again, which will offer to uninstall RAM Booster, which will unmount and delete the folder automatically, and clean up everything else
[*]
[/LIST]

I don't really see any of these as issues, as the script can't write data to a hard drive that's full, and uninstalling is as simple as it gets, which is covered both in the original post, and the video.
The script didn't break because the code malfunctioned - it broke because the partition ran out of space.
Even the "mess" that you are left with before you uninstall should let you boot your Original OS with no problems - the only thing you can't do is boot the RAM Session.

Edit: Since the script doesn't uninstall itself when squashfs fails to be created, I added a note to the new version that tells users that they should probably uninstall it to remove the partially installed files and stuff.
Uninstalling RAM_Booster cleans up everything the script does, no matter if the script finished running or broke somewhere in the middle.

Edit 2: Forgot to mention - I've never heard of SpiderOak or PDFStudioPro so I'm not sure how they effect the RAM Session

---

### Post by adambond on 2015-01-10
Subscribed

---

### Post by claudiocapobianchi on 2015-02-09
Hi! first of all, an entire post should be written only to thank you for the incredible work you did and keeping up. Having an OS loaded on ram is something absolutely astonishing, just imaging all its advantage blows my mind!!! Thank you again :p
 I installed the Ubuntu 14.04_ng_BETA on a EXT4 / sharing the /home partition and all worked fine. On RAM session, I get the information window that suggest me to rupdate to install updates, so after
```
sudo upgrade
```
it hits all repositories, then reports;
```
Failed to unmount chroot
Scanning for processes holding it up...

None found

There was an error unmounting /mnt/Original_OS/
A reboot should fix that
After the reboot, you will need to save your changes by recreating
the squashfs image if there was an update. Just run "sudo redit -s"


```

I rebooted and logged in RAM session, typed
```
sudo redit -s
```
and pressed Y

"squashfs image created successfully
reboot to use it"

after the reboot, 
```
sudo rupgrade
```
"No updates available"

```
sudo rupdate
```
same output about unmounting chroot, and if intstead of rebooting I write
```
sudo rupgrade
```
I get

"Failed to mount RAM Session. Is it already mounted?"

looks like a loop, how can I fix it? here you have the log file [ATTACH]259867[/ATTACH]

Thank you very much.

---

### Post by terminator14 on 2015-02-09
> **claudiocapobianchi said:**
> Hi! first of all, an entire post should be written only to thank you for the incredible work you did and keeping up. Having an OS loaded on ram is something absolutely astonishing, just imaging all its advantage blows my mind!!! Thank you again :p

Always nice to be appreciated :)

I'm not sure how familiar you are with Linux basics, so hopefully you can follow this, but it sounds like this is what's happening:

> **claudiocapobianchi said:**
> after the reboot, 
```
sudo rupgrade
```
"No updates available"


This checks for updates to my scripts from github. As it didn't complain, it seems to have exited and run cleanly.

> **claudiocapobianchi said:**
> ```
sudo rupdate
```
same output about unmounting chroot

It didn't show an error with mounting, so at that point everything seems fine.
After it is done running, it tries to unmount and fails, which gives you the error.
This means that at this point, /mnt/Original_OS, and filesystems underneath it are still mounted.

> **claudiocapobianchi said:**
> and if intstead of rebooting I write
```
sudo rupgrade
```
I get

"Failed to mount RAM Session. Is it already mounted?"

This seems accurate, because from the last error, we can tell that the RAM Session is still mounted.
It prevents it from running when it did not unmount cleanly by design.

The only problem I see is the fact that it couldn't unmount after checking for updates (after rupdate ran), which is a real problem, but a reboot should still be a workaround - it just fails to unmount all over again after a reboot when you run it again, but does actually do its primary function of checking for and installing updates before it fails.

Unfortunately, while a simple mount of like a flash drive or something will almost always unmount without problems, there are many reasons a mounted system with bind mounts of /sys, /dev, /dev/pts, /proc, etc. can fail to unmount. When I was writing the scripts, I spent many days tracking down as many reasons as I could and writing code to handle it, but clearly, there are still things unaccounted for. I'll see if I can reproduce the problem by installing Ubuntu 14.04, but this is one of the hardest problems in the project. The plan was to make this never be a problem again by switch to LXC to make the RAM Session more isolated when it gets mounted, to make it easier to unmount, but I've been busy and haven't gotten around to it.

I'll do some testing and post back.

---

### Post by terminator14 on 2015-02-09
I was able to reproduce the problem, but figuring out what exactly is causing it to fail to unmount is, as predicted, proving to be difficult.
I'll keep at it - hopefully I'll come up with something soon.

---

### Post by terminator14 on 2015-02-10
> **claudiocapobianchi said:**
> ...how can I fix it?

Fixed.
To apply:
[LIST]
[*]Reboot so that nothing is mounted.
[*]Boot into RAM Session
[*]Run "sudo rupgrade"
[*]Let it rebuild the squashfs image when it asks you to
[*]Reboot
[/LIST]

---

### Post by claudiocapobianchi on 2015-02-13
it works! thanks a lot :D
I'd like to report some "issues" I've noticed these days:



[LIST]
[*]in RAM session font is sharper (no anti-aliasing maybe?) than in normal session: [[IMG]http://imagizer.imageshack.us/v2/xq90/538/AMBp1t.png[/IMG]]("https://imageshack.com/i/eyAMBp1tp") vs [[IMG]http://imagizer.imageshack.us/v2/xq90/661/CRZJmW.png[/IMG]]("https://imageshack.com/i/idCRZJmWp") 
[*]in RAM session Software Updater doesn't find any update, in normal session it founds 32 MB of new software. 
[*]in RAM session auto-starting software actually doesn't (i.e. redshift). 
[*]changes applied in ram session (i.e. changing the server for updates or install new software) cancel at reboot even if I recreate the squashfs image with rupdate or redit -s 
[*]if I install software in normal session, although I recreate the image in RAM session with the above commands, at reboot there will be no trace of it. 
[/LIST]


probably the last two points depends on my (not yet accurate) familiarity with RAM session...

By the ways I tried, in ram session, there is no need to run apt-get update, better run rupdate, correct?

---

### Post by terminator14 on 2015-02-13
> **claudiocapobianchi said:**
> 
[LIST]
[*]in RAM session font is sharper (no anti-aliasing maybe?) than in normal session: [[IMG]http://imagizer.imageshack.us/v2/xq90/538/AMBp1t.png[/IMG]]("https://imageshack.com/i/eyAMBp1tp") vs [[IMG]http://imagizer.imageshack.us/v2/xq90/661/CRZJmW.png[/IMG]]("https://imageshack.com/i/idCRZJmWp") [/LIST]

Good catch. I'll look into it when I have some time.

> **claudiocapobianchi said:**
> 
[LIST]
[*]in RAM session Software Updater doesn't find any update, in normal session it founds 32 MB of new software. 
[/LIST]


The normal session and the RAM Session are two distinct operating systems. Just because one gets updated doesn't mean the other is up to date. Seeing available updates in one but not the other is expected.

> **claudiocapobianchi said:**
> 
[LIST]
[*]in RAM session auto-starting software actually doesn't (i.e. redshift). 
[/LIST]

What are you using to auto-start? Are your sure your auto-start changes aren't being deleted at reboot? See below.


> **claudiocapobianchi said:**
> 
[LIST]
[*]changes applied in ram session (i.e. changing the server for updates or install new software) cancel at reboot even if I recreate the squashfs image with rupdate or redit -s 
[/LIST]

This is by design. Changes to the RAM Session are made through "sudo redit". See the video for details:

[https://www.youtube.com/watch?v=pmqxDfdtDKg&feature=youtu.be]("https://www.youtube.com/watch?v=pmqxDfdtDKg&feature=youtu.be")

> **claudiocapobianchi said:**
> 
[LIST]
[*]if I install software in normal session, although I recreate the image in RAM session with the above commands, at reboot there will be no trace of it. 
[/LIST]


The two operating systems are distinct, so nothing you do in one effects the other. Recreating the squashfs image recreates it using /var/squashfs, not the original OS. See the video.

> **claudiocapobianchi said:**
> 
By the ways I tried, in ram session, there is no need to run apt-get update, better run rupdate, correct?

Yes - "apt-get update; apt-get upgrade" only does updates in the current instance of the RAM Session, which goes away after a reboot. rupdate was designed to update /var/squashfs and recreate the squashfs image, which effects the RAM Session as a whole (except the current instance, which is why you should reboot after running rupdate).

---

### Post by claudiocapobianchi on 2015-02-13
> **terminator14 said:**
> What are you using to auto-start? Are your sure your auto-start changes aren't being deleted at reboot? See below.
I thought I solved the problem by putting the tick on autostart: [[IMG]http://imagizer.imageshack.us/v2/xq90/673/vUFUMU.png[/IMG]]("https://imageshack.com/i/ipvUFUMUp") **and** recreating the squashfs with redit -s, but it autostarted only once [edit: it starts randomly], even if the tick is still there.

I watched the video twice, and I got that redit will install software in ram session, not in normal session, and this will be available after the reboot.
This implies that all chages you want become permanent must pass through redit, wich is a command. What can I do to apply "graphical changes" like changing update server o make applications auto-start?
> **terminator14 said:**
> The two operating systems are distinct, so nothing you do in one effects the other. Recreating the squashfs image recreates it using /var/squashfs, not the original OS. 
Yes - "apt-get update; apt-get upgrade" only does updates in the current  instance of the RAM Session, which goes away after a reboot. rupdate  was designed to update /var/squashfs and recreate the squashfs image,  which effects the RAM Session as a whole (except the current instance,  which is why you should reboot after running rupdate).
fundamental clue! so if I want to use all applications installed in normal session I should first install all them, then install the RAM_booster script.


Does this script work on [Ubuntu GNOME]("http://ubuntugnome.org/") edition (or all ubuntu derivatives)?

---

### Post by terminator14 on 2015-02-13
> **claudiocapobianchi said:**
> I thought I solved the problem by putting the tick on autostart: [[IMG]http://imagizer.imageshack.us/v2/xq90/673/vUFUMU.png[/IMG]]("https://imageshack.com/i/ipvUFUMUp") **and** recreating the squashfs with redit -s, but it autostarted only once, even if the tick is still there.

Try using the "gnome-session-properties" app to set startup applications.
IMPORTANT NOTE: You MUST run gnome-session-properties from within the redit environment, AND as your own user for the change to survive a reboot. See below.

> **claudiocapobianchi said:**
> I watched the video twice, and I got that redit will install software in ram session, not in normal session, and this will be available after the reboot.


Yup, assuming you let it recreate the squashfs image when you exit.

> **claudiocapobianchi said:**
> 
This implies that all chages you want become permanent must pass through redit, wich is a command.

Right again. Unless you are talking about updating the ram session, in which case you run "rupdate". rupdate is almost exactly the same as running "redit" and running "apt-get update; apt-get dist-upgrade" from within that.

> **claudiocapobianchi said:**
> What can I do to apply "graphical changes" like changing update server o make applications auto-start?

I cover this at 9:52 in the video.
VERY IMPORTANT: At that point in the video, you already ran "redit" and are in the redit environment.
[http://youtu.be/pmqxDfdtDKg?t=9m52s]("http://youtu.be/pmqxDfdtDKg?t=9m52s")

To just quickly cover what's happening in that section of the video:
You are in the redit environment, which you got into by typing "sudo redit"
You use "su - USERNAME" to become your regular user
[INDENT]99% of the time, a graphical change only effects your user, so we become your user so that the change we make applies to you[/INDENT]
We run the command that starts up the GUI program we want. In the video I used vlc and xeyes as an example. You might want to try gnome-session-properties instead.
We make the changes we want in the GUI program and close the GUI program
We type "exit" once to stop being your user (and return to being root)
We type "exit" again to exit the redit environment

Again, all the steps above are done WITHIN the redit environment. This is different than launching a GUI program normally, since here, any changes you make to its settings get written to /var/squashfs (since we do them in the redit environment) instead of your active RAM Session.

> **claudiocapobianchi said:**
> fundamental clue! so if I want to use all applications installed in normal session I should first install all them, then install the RAM_booster script.

Yes. When the RAM_booster script first runs, it creates a copy of your current OS. Anything you have installed will be available in the RAM Session. After RAM_Booster is done running however, any changes you make to your Original OS are NOT written to your RAM Session. To make changes to the RAM Session after that, you use redit. Your choices for getting software into the RAM Session are basically this:
[LIST=1]
[*]Already have the software installed or the config files changed before you run RAM Booster
[*]Use redit to make changes afterward
[/LIST]

> **claudiocapobianchi said:**
> Does this script work on [Ubuntu GNOME]("http://ubuntugnome.org/") edition (or all ubuntu derivatives)?

The script was only tested on the regular Ubuntu (Unity), but is is very likely to work on most, or even all derivatives.
Having said that, if your try to run the script on Ubuntu GNOME (or any other Ubuntu version) and their grub setup just happens to be different enough that the script can't handle it, you might end up with a system that won't boot. This is why if you want to experiment with things the script wasn't tested on, I highly encourage you to do so in a virtual machine first:

[http://lifehacker.com/5714966/five-best-virtual-machine-applications](http://lifehacker.com/5714966/five-best-virtual-machine-applications)

I use VMware Workstation myself, but it's not free. Some of the other ones on that page are, like VirtualBox.

---

### Post by claudiocapobianchi on 2015-02-13
here there are some interesting things after logged in redit and ran sudo gnome-session-properties:
[LIST]
[*]added and checked teamviewer and close the window 
[*]rebooted WITHOUT recreating the image (I know I should have done it, but I made some mess so i preferred reboot to start over) 
[*]after reboot: 
[*]re-open the startup page and redshift is checked by default, but it is not started 
[*]teamviewer is checked and is started (even if not correctly, infact it is necessary to start the daemon, and that's a tricky issue I'm going to solve later) 
[/LIST]
That's quite strange, looks like startup app list "survived" after reboot; anyway, the only difficult is to find name of those default packets you use by clicking on them, i.e. software-properties-gtk to manage repos. By the way, I tried to change server after "sudo software-properties-gtk" but whatever choice I selected, it automatically retuned to the original setting, like I have no permissions on it.

EDIT: after recreating the image correctly, I get at reboot  a splash error about software-properties-gtk :confused:

---

### Post by terminator14 on 2015-02-13
> **claudiocapobianchi said:**
> ...logged in redit and ran sudo gnome-session-properties:

sudo makes you run commands as root. When you are in the redit environment, you almost never want to use sudo because you are either already root, or if you use "su - USERNAME" to become a user, "sudo" makes you run the command as root again, which defeats the purpose of using "su - USERNAME".

> **claudiocapobianchi said:**
> 
[LIST]
[*]added and checked teamviewer and close the window 
[*]rebooted WITHOUT recreating the image (I know I should have done it, but I made some mess so i preferred reboot to start over) 
[*]after reboot: 
[*]re-open the startup page and redshift is checked by default, but it is not started 
[*]teamviewer is checked and is started (even if not correctly, infact it is necessary to start the daemon, and that's a tricky issue I'm going to solve later) 
[/LIST]
That's quite strange, looks like startup app list "survived" after reboot; anyway, the only difficult is to find name of those default packets you use by clicking on them, i.e. software-properties-gtk to manage repos. By the way, I tried to change server after "sudo software-properties-gtk" but whatever choice I selected, it automatically retuned to the original setting, like I have no permissions on it.

Now that I think about it, you are mounting /home from an actual partition. Most GUI apps save their settings to your home folder (/home/USERNAME/) in invisible dot files (files whose filenames start with a ".", which makes them invisible).
Most of the settings you change in your GUI apps should survive a reboot without redit. If you run an app with "sudo" however, you run it as root. The settings for root are NOT stored in your home directory, which WILL be gone after a reboot.
Technically, this should mean that you can run gnome-session-properties as yourself (do NOT use sudo), make changes, and reboot without using redit.
Also, software-properties-gtk effects the entire system, so you DO need redit to make changes to it that are permanent.

> **claudiocapobianchi said:**
> EDIT: after recreating the image correctly, I get at reboot a splash error about software-properties-gtk

Does that mean you can't boot? What does the error say?

Oh and to find the name of an app, try running:
```
$ xprop | grep WM_CLASS | cut -d '"' -f 2
```
and clicking on the window of a running app. Doesn't always work, but does most of the time.

---

### Post by claudiocapobianchi on 2015-02-13
> **terminator14 said:**
> Now that I think about it, you are mounting /home from an actual partition. Most GUI apps save their settings to your home folder (/home/USERNAME/) in invisible dot files (files whose filenames start with a ".", which makes them invisible).
Most of the settings you change in your GUI apps should survive a reboot without redit.
Brilliant intuitions! anyway even under redit, software-properties-gtk doesn't let me choose another server, it always comes back to the original one. Checking redshift on gnome-session-properties doesn't make it start at reboot as well.

The error is just a crash report saying that software-properties-gtk has stopped unexpectedly, the system is working fine.

Thank you for the xprop tip!

---

### Post by v3.xx on 2015-02-15
First let me say thankyou for the work and effort that went into updating this.

So I humbly ask if one change could be made :)

When using anything that requires sudo to create a reminder that your in ram_booster.

I find myself forgetting at times and making changes meant for the hdd.

Again, thankyou

---

### Post by terminator14 on 2015-02-15
> **v3.xx said:**
> I find myself forgetting at times and making changes meant for the hdd.

Try this in the RAM Session:

Edit the ~/.bashrc file
Add this line to the end:
```
alias sudo='echo You are in the RAM Session; sudo '
```


Note: It will NOT take effect in the current terminal - close it and open a new one, and then run any sudo command to see if that's what you want.
If you're happy with it and want to make it permanent, run:
```
sudo redit
```
and make the same addition in /home/USERNAME/.bashrc
then exit redit and let it recreate the squashfs image.

As for making it part of the official script - there's no inherent difference between running a sudo command and running any other command in the RAM Session in terms of how much in the RAM Session you are (you're either in the RAM Session or you're not), which means there's exactly as many reasons to add that message before ANY command gets executed in the RAM session. Having said that, I doubt many people would want that. If I get a lot of requests for this, I'll think about adding it, but right now, I can't imagine it would help too many people, other than a few specific cases such as yourself. That is not to say there's anything wrong with what you want - it just not something I see many people wanting to do.

---

### Post by v3.xx on 2015-02-15
Thankyou :D

I will give it a go later on.

---

### Post by tomas28 on 2015-02-17
The instruction explain about, copy and seperate, but are not clear about the differences.
The choices input are not clear. Y or N? C or P? are confusing. Y for what? What is user chosing Y for? Is it for C? All scarey choices for a newbie who isn't sure what to do and whether it is risky [It isn't risky].
There is a question asked, answer C or S. Down a bit, is another choice, and instruution about Y or N, but no reference to what a Y or a N means. Uh, know what I mean?
Where is Y? Where is No? The coice is to pick either S or C......
A simple matter of rewording the instructions. simple is not easy, docs are very difficult to work concisely, in fact, docs are a field of work for many many people in tech.
 I don't know enough about anything to recomended wording. The wonderful scrypt is, well, wonderful, but the options are confusing.
Consider being a Linux newbie and trying this scrypt out and being presented with the choices, copy or seperate? And then having to answer with a yes or no. Yes to what? No to what?
See what I mean?
I love the scrypt. Thank you for creating it.
I figured it out, by testing results. I know what I need to do and what is the result, but still cannot make sense out of the instructions [Apply the KISS principle :p  ]

---

### Post by terminator14 on 2015-02-17
> **tomas28 said:**
> The instruction explain about, copy and seperate, but are not clear about the differences.
The choices input are not clear. Y or N? C or P? are confusing. Y for what? What is user chosing Y for? Is it for C? All scarey choices for a newbie who isn't sure what to do and whether it is risky [It isn't risky]. There is a question asked, answer C or S.


Don't take this the wrong way, but the instructions of the script are ten times easier to decipher than your post.
There is no Y/N. The only choices at that point are S or C as made evident by the line [(s)eparate/(c)opy as is]. The brackets indicate that your choices are "s" for separate and "c" for copy. I didn't invent the convention - it existed long before I wrote the script. 

> **tomas28 said:**
> 
 Down a bit, is another choice, and instruution about Y or N, but no reference to what a Y or a N means. Uh, know what I mean?
Where is Y? Where is No? The coice is to pick either S or C......


Every single question that the script asks painstakingly explains what your choices are. If you don't want to read, I can't make you.

> **tomas28 said:**
> 
A simple matter of rewording the instructions. simple is not easy, docs are very difficult to work concisely, in fact, docs are a field of work for many many people in tech.

Again, I'm trying hard not to be offensive, but you seem to be using big words in this sentence, while at the same time making numerous grammatical errors. Your post is also full of spelling errors ("scrypt" is not a word). It's ironic that the point of the sentence is to tell me to write clearer. I'm aware that English might not be your first language (it would be really, really sad if it was), but guess what, it's not mine either, and I still manage.

> **tomas28 said:**
> 
 I don't know enough about anything to recomended wording. The wonderful scrypt is, well, wonderful, but the options are confusing.
Consider being a Linux newbie and trying this scrypt out and being presented with the choices, copy or seperate? And then having to answer with a yes or no. Yes to what? No to what?
See what I mean?


Your choices are C or S, which are very, very obvious. I have no clue where you got the "yes or no" from. You are literally the first out of 40 pages of posts who has had trouble understanding the choices.

> **tomas28 said:**
> 
I love the scrypt. Thank you for creating it.
I figured it out, by testing results. I know what I need to do and what is the result, but still cannot make sense out of the instructions [Apply the KISS principle :p  ]

I spent a long time creating a video that goes over running the script, step by step. Did you watch it?

[https://www.youtube.com/watch?v=pmqxDfdtDKg&feature=youtu.be](https://www.youtube.com/watch?v=pmqxDfdtDKg&feature=youtu.be)

---

### Post by georgesgiralt on 2015-02-23
Hello !
I own a PC which should benefit from your script. But it's installation is somewhat peculiar so I wonder if I can use your script.
Could you please help me ? 
The machine is as follow : 
Ubuntu 12.04 LTS.
All sata disks partitioned as follow 
Part 1 size 200MB used for /boot using RAID 1 (software raid)
Part 2 remaining size used as the sole PV of LVM using RAID 1 software raid. 


Ubuntu sees : 
An EXT 4 partition (md0) mounted as /boot
An LVM PV (md1) used to make vg00 which is split into 
           lvslash (ext4) mounted on /
           lvhome (ext4) mounted on /home
           lvvar (ext4) mounted on /var 
                  .
                  .
           lvswap used for swap. 

The volume group has still a lot of free space.
So what would be the way to use your script ? Create an lv first and assing it to the partition for your script to run or let the script create the lv and use it ? 
What should I do ? 
Many thanks in advance for your help.

---

### Post by terminator14 on 2015-02-23
> **georgesgiralt said:**
> Hello !
I own a PC which should benefit from your script. But it's installation is somewhat peculiar so I wonder if I can use your script.
Could you please help me ? 
The machine is as follow : 
Ubuntu 12.04 LTS.
All sata disks partitioned as follow 
Part 1 size 200MB used for /boot using RAID 1 (software raid)
Part 2 remaining size used as the sole PV of LVM using RAID 1 software raid. 


Ubuntu sees : 
An EXT 4 partition (md0) mounted as /boot
An LVM PV (md1) used to make vg00 which is split into 
           lvslash (ext4) mounted on /
           lvhome (ext4) mounted on /home
           lvvar (ext4) mounted on /var 
                  .
                  .
           lvswap used for swap. 

The volume group has still a lot of free space.
So what would be the way to use your script ? Create an lv first and assing it to the partition for your script to run or let the script create the lv and use it ? 
What should I do ? 
Many thanks in advance for your help.

2 things would worry me about running RAM booster with your setup - the fact that you're running an older Ubuntu, and the RAID.
With Ubuntu 12.04, your choices are basically to use the old 12.04 script, which was a slightly updated version of my first attempt at RAM booster, or the completely rewritten version 14.04.

The 12.04 script may or may not handle lvm well, and will probably die at some point with RAID, because it was never, ever tested with RAID (not by me anyway).
The rewritten 14.04 script is also likely going to give you problems, because:

1. It was written with 14.04 in mind - not 12.04, which have 2 years between them. Even the 6 month difference between Ubuntu 14.04 and 14.10 was enough to break my script and require 2 different versions - one for 14.04 and one for 14.10. Without testing, there's no telling the kind of changes that were made to important software the script uses in the background over these 2 years which might break things. 

2. I tested the new scripts (14.04 and 14.10) with lvm (which it handles fine), encryption, and all kinds of other configurations, but not RAID specifically. There's a good chance that it might work, but it is definitely untested.

Basically, what I want to say is this: there are one or two small problems/challenges that people might run into when running my script under ideal conditions. Your setup is tricky, and if you really, really wanted to try the script, I would HIGHLY recommend that you either:

Test a similar setup to yours in a virtual machine to see how badly the script kills things
Update to Ubuntu 14.10, maybe without using RAID
Do a FULL backup of your entire hard drive(s), like maybe with dd before you try it, so that if it dies, you can restore everything

No matter what you do, if you do anything, proceed very, very carefully.

---

### Post by georgesgiralt on 2015-02-24
Thank you for your documented answer. 
It confirm that I should proceed carefully. 
As per giving up the Raid, it is out of question.  It saved my life many times and allows me to upgrade disks without even backuping anything. (this PC has seen 2 different mainboards 2 different processors and was originaly built with 80 GB disks which over the years evelved into 500 GB disks. The Ubuntu releases also have evolved during the years without reinstallation thanks to the Ubuntu upgrade process). 
As money is becoming scarse, I thought that running on RAM would help postpone the MB and processor migration my wife asks. (she is the quite exclusive user of this machine for her work as a Yoga and Vedic chant teacher see [http://www.yogashraddha.fr](http://www.yogashraddha.fr) )
If I try your solution, I'll report back... :p

---

### Post by terminator14 on 2015-02-24
> **georgesgiralt said:**
> Thank you for your documented answer. 
It confirm that I should proceed carefully. 
As per giving up the Raid, it is out of question.  It saved my life many times and allows me to upgrade disks without even backuping anything. (this PC has seen 2 different mainboards 2 different processors and was originaly built with 80 GB disks which over the years evelved into 500 GB disks. The Ubuntu releases also have evolved during the years without reinstallation thanks to the Ubuntu upgrade process). 
As money is becoming scarse, I thought that running on RAM would help postpone the MB and processor migration my wife asks. (she is the quite exclusive user of this machine for her work as a Yoga and Vedic chant teacher see [http://www.yogashraddha.fr](http://www.yogashraddha.fr) )
If I try your solution, I'll report back... :p

Yup - as a technology, RAID is definitely awesome. I run RAID5 on my 2xNAS boxes myself, which saved my data once or twice. Unfortunately, I didn't have time to test mdadm/dmraid with my script, though I would have liked to. Maybe after I'm finally done writing my LPIC exam in a few days I'll have some more time to try it out and make the necessary changes to the script.

---

### Post by v3.xx on 2015-03-02
I have RAM_booster_14.04_BETA running on a physical install of Mate 14.04.

Really not seeing a difference from running this or 14.10_ng.sh, so I guess thats a good thing :)

---

### Post by terminator14 on 2015-03-04
> **v3.xx said:**
> I have RAM_booster_14.04_BETA running on a physical install of Mate 14.04.

Really not seeing a difference from running this or 14.10_ng.sh, so I guess thats a good thing :)

The code for 14.04_BETA is almost exactly the same as the code for 14.10_ng.sh.
I first wrote the 14.10_ng script, than made a copy of it and made only the changes that were necessary to get it running on 14.04 (backported it), calling it 14.04_BETA, because while I tested every single part of 14.10_ng.sh as I was working on it, 14.04 only received fixes to things that were visibly broken when running on Ubuntu 14.04.
So yes - ideally, both scripts should work exactly the same, even though in the background, they do several things slightly differently.

---

### Post by v3.xx on 2015-03-04
Nice to know.

Currently running a virtual machine through ram_booster session on 14o4 (host).  I did not do this expecting a performance gain, just nice to know I can :)

---

### Post by terminator14 on 2015-03-04
> **v3.xx said:**
> Nice to know.

Currently running a virtual machine through ram_booster session on 14o4 (host).  I did not do this expecting a performance gain, just nice to know I can :)

A VM is how I do all my testing. Being able to reset the entire OS to a known good state in 5 seconds with one button (vmware snapshots) is hundreds of times easier than reinstalling the entire system every time I need to reset and try running a slightly modified RAM_Booster script on a fresh system.
VMs basically made this script possible.

---

### Post by v3.xx on 2015-03-04
I did a poor job of explaining myself.  Check this out ..

[ATTACH=CONFIG]260451[/ATTACH]

---

### Post by terminator14 on 2015-03-04
> **v3.xx said:**
> I did a poor job of explaining myself.  Check this out ..

[ATTACH=CONFIG]260451[/ATTACH]

Oh - that's what you meant. Wow - that is pretty interesting - I would have been uncertain if that was possible.

PS. Awesome diagram!

---

### Post by v3.xx on 2015-03-06
Update

I have been running the above configuration (day 3) and using VMs.  I have not seen any glitching.  So I wanted to put some kind of load on it and updated/upgraded three VMs simultaneously.  This worked without issue.  I'm feeling this is going to be a solid platform.

No need to switch back to the physical drive is a big plus to me.

And yes, that diagram was one of my better works :D

---

### Post by terminator14 on 2015-03-06
> **v3.xx said:**
> Update

I have been running the above configuration (day 3) and using VMs.  I have not seen any glitching.  So I wanted to put some kind of load on it and updated/upgraded three VMs simultaneously.  This worked without issue.  I'm feeling this is going to be a solid platform.

No need to switch back to the physical drive is a big plus to me.

And yes, that diagram was one of my better works :D

Awesome!
What are you using to run VMs? VMware? VirtualBox?

---

### Post by v3.xx on 2015-03-06
Running VirtualBox 4.3.22 downloaded from the vBox site.

---

### Post by v3.xx on 2015-03-09
15.04 switch to systemd today, upstart is no more.  So I thought it would be a good time to try RAM_booster_14.10 on 15.04.  And it works :D

---

### Post by terminator14 on 2015-03-09
> **v3.xx said:**
> 15.04 switch to systemd today, upstart is no more.  So I thought it would be a good time to try RAM_booster_14.10 on 15.04.  And it works :D

Wow. Interesting.
Off the top of my head, I know that the code that unmounts the chroot (in redit and rupdate) specifically checks that no upstart services are running. In systemd, it would need completely different code using systemctl to do the same. This means that at least some of the code would need to be changed, as it is upstart-specific. It's good to hear that most of the code can work though - the more that works in 15.04, the less changes I need to make when I'm working on a 15.04 script.

Having switched to Arch as my main distro several days ago, I've actually been playing around with systemd a lot recently. It will be interesting to see how well it works in a chroot, and how hard it is to duplicate my upstart code using systemd.

---

### Post by v3.xx on 2015-03-15
I switched back to my physical install today, its been a while.

I built three virtual machines while in ram_booster and even though I have these new VMs in my physical (VirtualBox VMs) drive, VirtualBox does not see them.  And when I returned to my ram_booster session, they do not boot.

My other VMs that existed before ram_booster (built on the physical install) seem to work fine in ram_booster.  I can make changes to a vm, just can't build one.

This still works for me.  I just return to the physical drive to build VMs.

There may be other things happening.  I will do a better job of taking notes this time :)

---

### Post by tserts on 2015-03-19
Hey terminator14, I am currently copying the OS to ramfs so I don't know even if it will work, I just want to thank you for all the work you've done on the project, I was looking for this after testing some puppies on a laptop and noticed that it really runs very fast from ram so wanted to give it a try on my ubuntu box, you saved the day! 

I will post results as soon as I have any. Keep it up!

---

### Post by thedroz on 2015-03-21
Will this work with mint?  It's bade on ubuntu, isn't it?  I'm new so bear with me.  I'm running a full install off of a thumb drive and it's crazy slow.

Actually, I already tried to run the script and the error 'command not found' popped up.  It would have been nice to know which command that was...  if anyone can help I'd be really, really greatful.

Thanks

thedroz

---

### Post by terminator14 on 2015-03-21
> **thedroz said:**
> Will this work with mint?  It's bade on ubuntu, isn't it?  I'm new so bear with me.  I'm running a full install off of a thumb drive and it's crazy slow.

Actually, I already tried to run the script and the error 'command not found' popped up.  It would have been nice to know which command that was...  if anyone can help I'd be really, really greatful.

Thanks

thedroz

It was NOT tested with Mint. Which version of Mint are you using? If I have a few minutes, I might give it a try, and if the problems are quick fixes, and don't complicate the code too much, I might apply them.
It was also NOT tested on a system that runs off a thumb drive, which may or may not be your problem as well.

---

### Post by thedroz on 2015-03-21
It's 17.1 cinnamon.  Really appreciate that !

---

### Post by terminator14 on 2015-03-21
> **thedroz said:**
> It's 17.1 cinnamon.  Really appreciate that !

The latest version of Mint (17.1) is NOT based on the latest version of Ubuntu (14.10). Instead, it is based on the slightly older Ubuntu 14.04.
This means that my Ubuntu 14.04 script is better suited to run on Mint 17.1 than my Ubuntu 14.10 script.

I just installed Mint 17.1 and ran my 14.04 script on it, and other than a few harmless warnings, which I have just updated my script to ignore, it seems to work just fine.
I assume you ran my 14.10 script? Try the 14.04 script instead.

Note: Just because it "seems" to work fine on Mint using the one configuration I tested it on does NOT mean that it will run perfect on Mint. I tested the hell out of my script on Ubuntu using every configuration I could think of - MBR vs GPT/UEFI, encrypted home directories, encrypted filesystem, separate partitions for /home and /boot vs all on the same partition, LVM, etc. I tested one common setup on Mint to see if there are any obvious, massive problems with it - there appear to be none. That does not mean that there isn't a Mint configuration out there that might cause issues for the script - so please keep that in mind.

---

### Post by thedroz on 2015-03-21
I appreciate the work you put into it but I'm getting the same problem with both scripts: "command not found."  Sucks... I really could have use the functionality of our script.

---

### Post by terminator14 on 2015-03-21
> **thedroz said:**
> I appreciate the work you put into it but I'm getting the same problem with both scripts: "command not found."  Sucks... I really could have use the functionality of our script.

You're running them wrong.
[http://www.cyberciti.biz/faq/howto-run-a-script-in-linux/](http://www.cyberciti.biz/faq/howto-run-a-script-in-linux/)

After reading that, watch the video for how to use my script specifically:
[https://www.youtube.com/watch?v=pmqxDfdtDKg&feature=youtu.be](https://www.youtube.com/watch?v=pmqxDfdtDKg&feature=youtu.be)

---

### Post by thedroz on 2015-03-23
Ahhhh....  I didn't have the    "./"      sudo  ./RAM_booster_Ubuntu_14.10_ng.sh

Now let's see if it works... thanks

---

### Post by terminator14 on 2015-03-23
> **thedroz said:**
> Ahhhh....  I didn't have the    "./"      sudo  ./RAM_booster_Ubuntu_**14.10**_ng.sh

Now let's see if it works... thanks

Again, for Mint 17.1, you're better off using RAM_booster_Ubuntu_**14.04**_ng_BETA.sh.

---

### Post by thedroz on 2015-03-23
Well, I switched to kubuntu for various reasons and it works with it too.  Wow... that's wicked fast!

Thanks for the help and the awesome software.

---

### Post by claudiocapobianchi on 2015-04-11
HI!
these days I acquired more confidence with redit/rupdate commands and separation between ram session and normal one. I' am trying the script on a 64bit destkop and 32bit notebook,both with Ubuntu mate 14.04, and it works simply flawlessy =d>
It's awesome to install software you just need once and at ram speed too, and on next reboot, voilà! system clean :D\\:D/
Compliments, phenomenal work!
PS I noticed that on destkop, before loading squashfs to ram, looks like it looks for some boot media, in fact there is blinking screen for a few secs, then DVD light and motor turn on for just a sec, and finally it starts loading.
Is there a way to cut off these steps or are they necessary?
PPS: I noticed that when creating the image with 6 cores, it uses only one core at time at 100% and switches between them, while using same processor with four cores disabled, they work both at 100%, same happened with dual-core notebook (this also happens while extracting archives, for example). How can I use all 6 cores? recompiling kernel?

---

### Post by terminator14 on 2015-04-11
> **claudiocapobianchi said:**
> ... Compliments, phenomenal work!

Thanks. I'm glad to hear you're happy with it.

> **claudiocapobianchi said:**
> PS I noticed that on destkop, before loading squashfs to ram, looks like it looks for some boot media, in fact there is blinking screen for a few secs, then DVD light and motor turn on for just a sec, and finally it starts loading.
Is there a way to cut off these steps or are they necessary?

There are many improvements that could be made to the scripts - that is probably one of them. Unfortunately, it would take me days, if not weeks, to go through and research, test, and implement many of these changes.
I am recently unemployed, and while that sounds like I should have a ton of time on my hands, the truth is I'm busier than ever: I'm exercising several hours per day, looking for a job (online searches, meetings with recruiters, interviews, etc), and I'm spending any remaining free time learning Active Directory, as there are unfortunately not many Linux jobs available in my city. I wish I could spend more time with Linux, but it's not something I have time for at the moment. If there are giant bugs that break functionality of my scripts that someone reports, I might find the time to look into it, but efficiency of the code and the process itself is unfortunately pretty low on my big list of stuff to do at the moment.
As it says on my original post, if you, or anyone else reading this is interested in taking over the project, please let me know.

---

### Post by claudiocapobianchi on 2015-04-11
We all hope you can find a satisfying job as soon as possible!

---

### Post by terminator14 on 2015-04-11
> **claudiocapobianchi said:**
> We all hope you can find a satisfying job as soon as possible!

Thanks :)

---

### Post by sudodus on 2015-04-12
> **claudiocapobianchi said:**
> We all hope you can find a satisfying job as soon as possible!

+1

Good luck :-)

---

### Post by terminator14 on 2015-04-12
> **sudodus said:**
> +1

Good luck :-)

Wow - thanks guys. :D

---

### Post by tserts on 2015-04-14
Hey man, good luck on the job hunt..

Just posting to say that it worked so well I did a re-installation with separate /home to use a my main OS in the office. Fast and steady all the way. 

Thanks a lot.

---

### Post by terminator14 on 2015-04-14
> **tserts said:**
> Hey man, good luck on the job hunt..

Thanks :)

> **tserts said:**
> Just posting to say that it worked so well I did a re-installation with separate /home to use a my main OS in the office. Fast and steady all the way. 

Thanks a lot.

Awesome!

---

### Post by claudiocapobianchi on 2015-04-15
hi, looking for a way to reduce squashfs size and boot time, I purged older kernels by tiping
```
dpkg --get-selections | grep linux-image

```
and
```
apt-get purge linux-image-3.13.0-46-generic 

```

and then rebuild the image, probably not a great idea :oops:. In fact, now I am not able to boot in normal session, but only in RAM one lol since it's not detected while updating grub.
I tried:
[LIST]
[*]rupdate with a kernel update (the message "WARNING: A KERNEL UPDATE JUST OCCURRED..." appeared) and rebuilt image 
[*]"update-grub2" within redit 
[*] boot-repair-cd 
[*]to install grub following [this]("http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd") guide 
[/LIST]
with no results.

is a fresh installation the only solution?

---

### Post by terminator14 on 2015-04-15
> **claudiocapobianchi said:**
> hi, looking for a way to reduce squashfs size and boot time, I purged older kernels by tiping
```
dpkg --get-selections | grep linux-image

```
and
```
apt-get purge linux-image-3.13.0-46-generic 

```

and then rebuild the image, probably not a great idea :oops:. In fact, now I am not able to boot in normal session, but only in RAM one lol since it's not detected while updating grub.
I tried:
[LIST]
[*]rupdate with a kernel update (the message "WARNING: A KERNEL UPDATE JUST OCCURRED..." appeared) and rebuilt image 
[*]"update-grub2" within redit 
[*] boot-repair-cd 
[*]to install grub following [this]("http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd") guide 
[/LIST]
with no results.

is a fresh installation the only solution?

It seems that you've deleted your main kernel for your Original OS.
Reinstalling everything is a bit drastic at this point, as there are several ways to recover.

Try this:
Boot into the RAM Session, or even any Ubuntu LiveCD
Mount the Original OS:
```
$ sudo mkdir /mnt/OS
$ sudo mount **/dev/sdX** /mnt/OS
$ sudo mount -o bind /proc /mnt/OS/proc
$ sudo mount -o bind /dev /mnt/OS/dev
$ sudo mount -o bind /dev/pts /mnt/OS/dev/pts
$ sudo mount -o bind /sys /mnt/OS/sys
```

Note: Where **/dev/sdX** is the device of your Original OS. You can use "sudo fdisk -l" to figure that out.
Note 2: If you have a separate partition for /boot, you'll need to mount it to /mnt/OS/boot at this point as well

Chroot into the Original OS mountpoint you just made:
```
$ sudo chroot /mnt/OS
```

IMPORTANT NOTE: If your /boot is either empty, or contains the file "IMPORTANT_README" at this point, you have the wrong /boot mounted, in which case type "exit" to exit the chroot and find the proper device for your /boot to mount at /mnt/OS/boot

Install the kernel:
```
# apt-get install linux-image-3.13.0-46-generic
```

This will probably happen automatically when you install the new kernel, but you can update grub manually just to be safe:
```
# update-grub
```

Exit the chroot, unmount everything, and reboot:
```
# exit
$ sudo umount /mnt/OS/sys
$ sudo umount /mnt/OS/dev/pts
$ sudo umount /mnt/OS/dev
$ sudo umount /mnt/OS/proc
$ sudo umount /mnt/OS
$ sudo rmdir /mnt/OS
$ sudo reboot
```

Basically, the reason the other guides didn't work is because they assume you actually have a kernel to boot into and that your grub is broken. Your grub is almost definitely fine - you just happen to be missing a kernel for it to find and boot.

---

### Post by claudiocapobianchi on 2015-04-16
After chrootig and tried to install kernel 48:
```
linux-image-3.13.0-48-generic is already the newest version.
```
I get
```
The following packages were automatically installed and are no longer required:
  linux-headers-3.13.0-39 linux-headers-3.13.0-39-generic
  linux-image-3.13.0-39-generic linux-image-extra-3.13.0-39-generic
```
so I autoremoved them and reinstalled kernel[...]39 , but in the new grub was no trace of normal session.
After unmounting all, I installed the same kernel this thime within redit, and i get this message:
```
The following packages were automatically installed and are no longer required:
  linux-headers-3.13.0-48 linux-headers-3.13.0-48-generic
Use 'apt-get autoremove' to remove them.
[...]
Found ram session image: /boot/RS_KERNELS/vmlinuz-3.13.0-49-generic
Found linux image: /boot/vmlinuz-3.13.0-39-generic
Found initrd image: /boot/initrd.img-3.13.0-39-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
```
at least, this time kernel 39 was in grub and Imanaged to boot in normal mode :p
Unfortunately on normal mode, newtork module was not loaded and screen had issues with resolution and refresh rate, so it was a bit useless.
came back on ram session, I installed kernel 48 and rebuilt the image, now the desktop is perfect :D

Riassuming:
from redit I installed the two kernels I removed before and rebuilt the image.
So from redit I can affect normal session, and not only the squashfs... :-k

---

### Post by terminator14 on 2015-04-16
> **claudiocapobianchi said:**
> in the new grub was no trace of normal session.
As far as I can tell, you were able to install the 3.13.0-48-generic kernel using the chroot, but it apparently did not automatically tell grub to rebuild itself, which I'm pretty sure it should have.

> **claudiocapobianchi said:**
> After unmounting all, I installed the same kernel this thime within redit, and i get this message:
```
The following packages were automatically installed and are no longer required:
  linux-headers-3.13.0-48 linux-headers-3.13.0-48-generic
Use 'apt-get autoremove' to remove them.
[...]
[COLOR="#FF0000"]Found ram session image: /boot/RS_KERNELS/vmlinuz-3.13.0-49-generic
Found linux image: /boot/vmlinuz-3.13.0-39-generic
Found initrd image: /boot/initrd.img-3.13.0-39-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done[/COLOR]
```


The messages in red are the output of 'update-grub', which is the command that tells grub that new kernels are available and that it should look for them in /boot. This command runs automatically when you install or remove kernels with apt-get. It almost sounds like it didn't run automatically when you installed the kernel in the chroot. If this was the case, the only thing redit did when you installed the new kernel that fixed the Original OS was run that command (update-grub). When you run 'redit', your real /boot gets mounted, so yes, there are a few things that the redit environment can do to effect the boot process, but that is by design.

---

### Post by claudiocapobianchi on 2015-04-21
Sorry for the late reply.
Indeed, grub-update didn't run at all inside chroot since all kernels were already installed, I solved using redit.
In the log I attached you can find all the steps I did and their results, just to know.
In the last part it says that linux-image-3.13.0-49-generic is already installed,  even if I was using -48, solved upgrading on normal-session.
Cheers.
PS this thread should be sticked!

---

### Post by terminator14 on 2015-04-22
> **claudiocapobianchi said:**
> Sorry for the late reply.
Indeed, grub-update didn't run at all inside chroot since all kernels were already installed, I solved using redit.
In the log I attached you can find all the steps I did and their results, just to know.
In the last part it says that linux-image-3.13.0-49-generic is already installed,  even if I was using -48, solved upgrading on normal-session.
Cheers.
PS this thread should be sticked!

Good to hear you got it going.
Ya - messing with kernels and grub can be loads of fun. When you add the increased complexity of RAM Session (which does a few tricks to make sure grub does NOT find kernels that the RAM Session installed but the Original OS did not, or vice versa), the fun just keeps increasing exponentially.

You seem like you have a pretty good idea of installing a kernel and updating grub, but here's a slightly lower level that may one day be useful:

When you run "update-grub", or when it gets run automatically when a new kernel is installed using apt-get (or another package manager), all grub does is check /boot/ for:
[LIST=1]
[*]the kernel (/boot/vmlinuz*)
[*]its accompanying initrd image (/boot/initrd*)
[/LIST]
and if they exist it adds both to a single grub menu entry (the menu that shows up at boot).

Ex:
In your case, when it found:
```
Found linux image: /boot/vmlinuz-3.13.0-48-generic
Found initrd image: /boot/initrd.img-3.13.0-48-generic
```

it knew that they belong together because the suffix (version numbers) are exactly the same on both files, so it added them to the grub menu as a single menu entry at boot.
Another thing that is required, but that grub actually doesn't check for (it assumes it's there) are the actual modules for that kernel, which are found at /lib/modules in a folder that is the same as the kernel version of the kernel you installed.
If you have those 3 things, than you should be able to boot your system.

---

### Post by faure212 on 2015-05-01
What about running it with Lubuntu 15.04 on an old Thinkpad X41 with 1.5 gb of RAM?

---

### Post by terminator14 on 2015-05-01
> **faure212 said:**
> What about running it with Lubuntu 15.04 on an old Thinkpad X41 with 1.5 gb of RAM?

I have not tried Lubuntu, but the image appears to be 700MB. 1.5GB, 700MB of which will be taken up by the image itself leaves you with 800MB of usable RAM tops. That's not very much RAM - my firefox takes more RAM than that half the time (depending on how many tabs I have open). It may or may not run with that little RAM to work with.

Also, the script was NOT tested with Ubuntu 15.04 yet, and considering the fact that 15.04 is the first release of Ubuntu that uses systemd instead of upstart, I can pretty much guarantee that the 14.10 script won't be happy running on 15.04 without modifications. I might give it a try sometime soon and maybe release a 15.04 version of the script.

One last thing I want to mention is this: I do NOT test the script with different flavors of Ubuntu (due to lack of manpower mostly), but it usually works on them anyway because of how similar Ubuntu is to them. That doesn't mean that there can't be some difference between Ubuntu and Lubuntu that makes the script unhappy though, which is another thing to watch out for. If there is a problem, I might just boot up a VM of Lubuntu and give it a quick try to see if the problem is easy to fix, but this won't happen for Lubuntu 15.04 until there's a 15.04 version of my script.

---

### Post by faure212 on 2015-05-02
Thanks for this detailed response.  I was asking because my old Thinkpad X41 laptop/tablet has become unusably slow, and I cannot figure out why.  I have tried Mint, full Ubuntu, but seem unable to restore its usability-- it used to work just fine with Lubuntu until 2 versions ago... ;-(

---

### Post by terminator14 on 2015-05-02
> **faure212 said:**
> Thanks for this detailed response.  I was asking because my old Thinkpad X41 laptop/tablet has become unusably slow, and I cannot figure out why.  I have tried Mint, full Ubuntu, but seem unable to restore its usability-- it used to work just fine with Lubuntu until 2 versions ago... ;-(

Things take more and more RAM every year. 4GB used to be plenty - now it's almost the minimum. These days, 1.5 GB for a system you actually want to do stuff on (watch youtube, surf the web, etc) is almost nothing. Like I said - my firefox can use up more RAM than that easily.
If your CPU is fast enough not to be useless, brining a laptop back to life basically involves one, or both of these things:
[LIST=1]
[*]Get more RAM - assuming the RAM is upgradeable
[*]Get an SSD - won't really help if you'll be using RAM Booster (except speeding up boot process) but if RAM is NOT upgradeable, this might be your best and only option
[/LIST]
Even after both those things, there's no guarantee it will be fast enough to not be painful to use.

If that fails, or if you just don't want to spend the money trying that, you can always make it a server with no GUI. My home router is an Alpine Linux box with 1 CPU core, and 1 GB of RAM, of which it's only using about 300MB. Works awesome. Plenty of other server stuff you can run with no GUI.

---

### Post by sudodus on 2015-05-02
> **faure212 said:**
> Thanks for this detailed response.  I was asking because my old Thinkpad X41 laptop/tablet has become unusably slow, and I cannot figure out why.  I have tried Mint, full Ubuntu, but seem unable to restore its usability-- it used to work just fine with Lubuntu until 2 versions ago... ;-(

Try ***Lubuntu 14.04.2 LTS ***or*** 15.04***, or if you wish something lighter and faster, try ***ToriOS ***or*** TahrPup ***or*** Wary Puppy***. I can run all these distros in my Thinkpad T42, which has a Pentium M processor at 1.7 GHz and 1.25 GB RAM.

---

### Post by claudiocapobianchi on 2015-05-04
Thank you for your explanations!

> **terminator14 said:**
>  I do NOT test the script with different flavors of Ubuntu (due to lack of manpower mostly)

I am daily using it on Ubuntu Mate 32 (notebook) and 64 (desktop) bit, and it works flawlessly!

---

### Post by terminator14 on 2015-05-04
> **claudiocapobianchi said:**
> Thank you for your explanations!



I am daily using it on Ubuntu Mate 32 (notebook) and 64 (desktop) bit, and it work flawlessly!

Awesome :)

From a programmer's point of view however, "the program works flawlessly" and "the program worked for one user in one configuration in such a way as to not have seemed to do anything it shouldn't have" are two different things.
If I was to do real testing of the script on other flavors of Ubuntu, this would involve:
[LIST]
[*]Making sure that every single line of code in the script still does what it's supposed to - some of my lines may have 2>/dev/null which hides errors
[*]Testing on MBR partition tables
[*]Testing with a partition layout where everything is on the same partition
[*]Testing with a partition layout where /boot is on a separate partition
[*]Testing with a partition layout where /home is on a separate partition
[*]Testing with a partition layout where BOTH /home and /boot are on a separate partition at the same time
[*]Testing with a system where the filesystem is encrypted
[*]Testing with a system where the user home directories are encrypted
[*]Testing with a system where BOTH the filesystem and user home directories are encrypted
[*]Testing different types of software to make sure they work in the chroot and don't prevent the chroot from unmounting, or break out of the chroot
[*]Running all those tests again with LVM layouts
[*]Running all those tests again with different filesystems (ext3/ext4/xfs/btrfs) for /, /home, and /boot
[*]Running all those tests again for a GPT/UEFI system
[*]Running all those tests again for every flavor of Ubuntu that I want to test with
[/LIST]
I'm probably missing a few things - those were just off the top of my head.
Every time I say "testing with", ideally this would be more than just configure the system in that way, install RAM Booster, see if it boots, and move on - this should involve actual usage of the system in that configuration for some length of time to see if anything strange happens.
The massive amount of testing is the reason there's only one official version of Ubuntu supported - the main version. Luckily, most flavors are close enough to Ubuntu to not give people trouble.

---

### Post by v3.xx on 2015-05-04
I been running RAM_booster for 2/3 months.  In the beginning I tried to break it and was surprised at how much abuse it could take.  These days I just reap the rewards of your hard work.  Thank you from one with no SSD :)

---

### Post by terminator14 on 2015-05-04
> **v3.xx said:**
> I been running RAM_booster for 2/3 months.  In the beginning I tried to break it and was surprised at how much abuse it could take.  These days I just reap the rewards of your hard work.  Thank you from one with no SSD :)

No problem :)

---

### Post by claudiocapobianchi on 2015-05-05
well if it can help, both my configurations are non-EUFI, have EXT4 /home partition separated with no encryption, MBR, and I use built-in applications plus redshift, tor and telegram ;)

You've been working at this demanding as much as awesome project since 2008 doing it entirely on your own and providing support even 7 years later, making a phenomenal work and all you can do for us, even giving  the smaller tip, it's really a lot for a single man. Thank you.

OT PS: have you included this on your curriculum vitae? :KS

---

### Post by terminator14 on 2015-05-05
> **claudiocapobianchi said:**
> well if it can help, both my configurations are non-EUFI, have EXT4 /home partition separated with no encryption, MBR, and I use built-in applications plus redshift, tor and telegram ;)

Sounds like a fairly basic system. Thanks though - good to hear it works.

> **claudiocapobianchi said:**
> You've been working at this demanding as much as awesome project since 2008 doing it entirely on your own and providing support even 7 years later, making a phenomenal work and all you can do for us, even giving  the smaller tip, it's really a lot for a single man. Thank you.

I try :)

> **claudiocapobianchi said:**
> OT PS: have you included this on your curriculum vitae? :KS

On my linkedin page - yes. Using this project to make my resume sound nicer was obviously not the reason I started the project, but hopefully it helps. Thanks for the suggestion though - I appreciate it.

---

### Post by v3.xx on 2015-05-12
Hi

I haven't loaded up 15.10 yet, but I plan to use upstart and ram_booster.

Is this a good work-a-round?

---

### Post by terminator14 on 2015-05-12
> **v3.xx said:**
> Hi

I haven't loaded up 15.10 yet, but I plan to use upstart and ram_booster.

Is this a good work-a-round?

It's certainly more likely to work, since there is upstart-specific code in the script, but there's no guarantee that some other change that was made between Ubuntu 14.10 and 15.04 (which I assume is the version you meant) hasn't caused other problems for the script.

---

### Post by v3.xx on 2015-05-12
Yes 15.10 is what I meant.  I posted some test results for 15.04 [here]("http://ubuntuforums.org/showthread.php?t=1594694&page=41&p=13242298#post13242298") a while back.

And then dropped further testing.

Let you know what happens.

Thanks

---

### Post by thedroz on 2015-06-03
I can't gt redit to work.  After exiting redit...
--------------------------------------------------

df: ‘/lib/live/mount/medium’: No such file or directory
df: ‘/lib/live/mount/overlay’: No such file or directory
df: ‘/lib/live/mount/overlay’: No such file or directory
df: ‘/sys/fs/cgroup/systemd’: No such file or directory
Failed to unmount chroot
Scanning for processes holding it up...


None found


There was an error unmounting /mnt/Original_OS/
A reboot should fix that
After the reboot, if you need to save your changes by recreating
the squashfs image, just run "sudo redit -s"


After reboot and running  redit -s
---------------------------------------------

Are you sure you want to recreate the squashfs image?
This may take some time to complete
You may use the computer normally during this process - you will NOT disrupt it


Your choice [y/N]: y






Creating squashfs image


Failed to mount RAM Session. Is it already mounted?
droz@drozpc:~$ 




Crap...

---

### Post by chriswill2 on 2015-06-15
Hi, I'm new to ubuntu linux. I've read your articles and I want to try it ( I think it's cool just to bring your thumbdrive and plug it in and have your data always store to ur thumbdrive).

Well I want to try it, but I'm still a noob to this

CMIIW, but the first thing I need to do is to install Ubuntu to my thumbdrive correct ? Should I do full install or persistence will do ? 

Thx, chriswill

---

### Post by lanparty-s on 2015-06-16
Hi I was wishing to install this on ubuntu 15.04. I seen that someone had success with this script in ubuntu 15.04 but can not find the post again.

 I have downloaded the .git file throw the terminal command window, but when I unpack the file there is only scripts for 14.04 and 14.10 so I would like to know what script I should use.

Developer Notes  old
Diagram.png
      RAM_booster_Ubuntu_14.04_ng_BETA.sh
extras_14.04
     RAM_booster_Ubuntu_14.10_ng.sh
extras_14.10 
    README.md

---

### Post by v3.xx on 2015-06-16
> **lanparty-s said:**
> Hi I was wishing to install this on ubuntu 15.04. I seen that someone had success with this script in ubuntu 15.04 but can not find the post again.

 I have downloaded the .git file throw the terminal command window, but when I unpack the file there is only scripts for 14.04 and 14.10 so I would like to know what script I should use.
I did this for a short period while running 15.04 pre-release.

Use the 14.10 script and you will have to run upstart instead of systemd.  The changes to ram_booster have not been made for systemd.

To replace systemd with upstart, just install upstart

---

### Post by lanparty-s on 2015-06-16
Thanks for the quick reply I just did this and it says upstart is already installed,

sudo apt-get install upstart
Reading package lists... Done
Building dependency tree       
Reading state information... Done
upstart is already the newest version.
upstart set to manually installed.
0 to upgrade, 0 to newly install, 0 to remove and 3 not to upgrade.

Have I done this right?

---

### Post by v3.xx on 2015-06-16
Apoligies

That is what I had to do in 15.10.  There is a way to switch between the two in 15.04.  I do not know it off hand and I do not run 15.04 any more.  So You need to search for the proper command.  

[<snip>]("http://www.googlubuntu.com/results/?cx=0mate")

I will assist when I can.

For some reason I cannot post a link, let me work on that.

---

### Post by v3.xx on 2015-06-16
[URL="http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=upstart+systemd+15.04&sa=Search&cof=FORID:9"]http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=upstart+systemd+15.04&sa=Search&cof=FORID:9

OK, that worked.
[/URL]

---

### Post by lanparty-s on 2015-06-16
Thanks again for your reply I have the usb stick in and i have told the system to mount the USB drive but I get this error :

Which partition do you want to use as /home?
Your choice: /dev/sdb1

Running file check on your device...

Everything checks out.
Formatting /dev/sdb1

mke2fs 1.42.12 (29-Aug-2014)
/dev/sdb1 contains a ext4 file system labelled 'RAM_booster'
    last mounted on Wed Jun 17 01:48:18 2015
Proceed anyway? (y,n) y
/dev/sdb1 is mounted; will not make a filesystem here!

Formatting /dev/sdb1 failed.
Exiting...

---

### Post by v3.xx on 2015-06-16
Your setting up a bit different than me.  I did not opt for a separate home.  I felt this may cause confusion with the multiple installs I have.  I find this works well with 24G of ram.  How much ram do you have?

It said formatting sdb1 and stopped.  Sounds like you need to create a partition for home before hand.

---

### Post by lanparty-s on 2015-06-16
> [COLOR=#000000]How much ram do you have?[/COLOR]

I'm running a single core 3.4 gig and 6 gig of ddr2 ram ubuntu 15.04 server.

> [COLOR=#000000]It said formatting sdb1 and stopped. Sounds like you need to create a partition for home before hand.[/COLOR]

Not quite sure what you mean... do i just make a folder inside that usb called /home?

---

### Post by v3.xx on 2015-06-16
Something else about my install.

I keep all my files/collections and other things in a 'data partition'.  Keeping my home folder very empty.  My ram_booster installs use about 1 to 1.5 gig of ram without a separate home.

---

### Post by v3.xx on 2015-06-16
> Not quite sure what you mean... do i just make a folder inside that usb called /home? 
No, I was thinking more like you need to create a partition, but I am not sure about this.

---

### Post by lanparty-s on 2015-06-16
> [COLOR=#000000]No, I was thinking more like you need to create a partition, but I am not sure about this.[/COLOR]

You are right[COLOR=#000000] v3.xx[/COLOR], what I did after thinking on what you said is I changed the name of the usb from ( RAM_booster to /home ) then I told it to install on /dev/sdb1.and all went well.... now I have to pick and would like some advice please on this one.

Would you like to have your Original OS use /dev/sdb1 as its /home as well?


If you choose yes, your Original OS's /home and your RAM Session's /home
will be shared


If you choose no, your Original OS's /home and your RAM Session's /home will
be different


Your choice [Y/n]: 

Should I pick yes or no not sure on this one.

Will I be able to save to  original os later if i pick option 2 (NO) if I needed to at some point?

[COLOR=#000000]
[/COLOR]

---

### Post by v3.xx on 2015-06-16
No, I think your choice.  I have a preference of separate homes, but doesn't necessarily make it the best choice for you.

Edit:
That came out sounding wrong.  For you, I would go with separate homes just for what I would consider a extra layer of protection.

My home resides in ram_booster (in the ram session).

---

### Post by lanparty-s on 2015-06-16
> **v3.xx said:**
> No, I think your choice.  I have a preference of separate homes, but doesn't necessarily make it the best choice for you.

Edit:
That came out sounding wrong.  For you, I would go with separate homes just for what I would consider a extra layer of protection.

My home resides in ram_booster (in the ram session).

I picked NO for that, as I was thinking... if I do not like the setup I can do it again.

I'm up to Creating squashfs image, just realized that I had 3 gig of mail in this server... if I get mail on this server will it wipe it when it restarts? or can i save sessions when needed

---

### Post by lanparty-s on 2015-06-16
[COLOR=#a9a9a9]I can give Thumbs up on **RAM Booster script 14.10** being compatible with **U****buntu 15.04 64bit Serve**r[/COLOR]. _**EDIT**_: Sorry not fully compatible 

 :guitar:

Would also like to Thank...** v3.xx **for his help and **Terminator14 for **all the time you have spent on this project.

[COLOR=#a9a9a9]I Will be testing it on a copy of *Ubuntu 15.04 32bit Desktop* next.[/COLOR]
=====================================

**Edit:** When I try and restart the computer it keeps looping:

[COLOR=#808080][B]Failed unmounting /lib/live/mount/medium...
unmounting /lib/live/mount/medium...
Failed unmounting /lib/live/mount/medium...
unmounting /lib/live/mount/medium...[/B][/COLOR]

It did not do this on the first restart...

---

### Post by lanparty-s on 2015-06-17
I have been trying to uninstall RAM_booter and no matter what I try, I can not get anything to work. I have tried [COLOR=#000000][FONT=Ubuntu Mono]sudo ./RAM_booster.sh --uninstall. in all the folders 

[/FONT][/COLOR]

---

### Post by v3.xx on 2015-06-18
Hey lanparty-s

What has happen?  Thought you was up and running.  Do you have ram_booster file in the first level of your home directory (not in the 'Download' folder)?  Upstart running?

On a side note.
No subscription notification is sent when a post is edited, only a new post will do that :)

---

### Post by lanparty-s on 2015-06-19
> **v3.xx said:**
> Hey lanparty-s

What has happen?  Thought you was up and running.  Do you have ram_booster file in the first level of your home directory (not in the 'Download' folder)?  Upstart running?

On a side note.
No subscription notification is sent when a post is edited, only a new post will do that :)

Yeah I have ram_booster file in /home folder I think its getting stuck on the .squashfs file maybe.

---

### Post by v3.xx on 2015-06-19
Later today I'll load up a copy of 15o4 and see if I can recreate the problem.

Will also take a look at --uninstall.

Later

---

### Post by v3.xx on 2015-06-21
I took a few notes.
```
#first switch to upstart
sudo apt-get install upstart-sysv && sudo update-initramfs -u  && sudo reboot
#followed by a verification
ps -p1 | grep systemd && echo systemd || echo upstart
#next install ram_booster
sudo ./RAM_booster_Ubuntu_14.10_ng.sh
#and one more reboot will auto magically start ram_booster.
```

I next uninstalled
```
sudo ./RAM_booster_Ubuntu_14.10_ng.sh --uninstall
```
And then reinstalled again.
It has worked for me on 15o4..  Leaves me at a lost with whats going on with you.

---

### Post by lanparty-s on 2015-06-21
Hi thanks for your reply v3.xx I think I might of installed it wrong... > [COLOR=#000000]I next uninstalled[/COLOR]
[COLOR=#000000]Code:
[/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono]sudo ./RAM_booster_Ubuntu_14.10_ng.sh --uninstall[/FONT][/COLOR] The code alone did not work for me in /home I had to tell it to go into the RAM_booster folder to find the uninstall not in home? 
    This is what code I had to use was  ```
 root@comp01:/home/comp/RAM_booster# sudo ./RAM_booster_Ubuntu_14.10_ng.sh --uninstall 
```

EDIT: Am I meant to take the files out of the RAM_booster folder adding them files to /Home directory when I reinstall  RAM_booster? I'm a little confused sorry

---

### Post by v3.xx on 2015-06-22
Why are you in your root account?
```
m15@m15:~$ cd /home/m15/RAM_booster
m15@m15:~/RAM_booster$ sudo ./RAM_booster_Ubuntu_14.10_ng.sh --uninstall

This script was written to work with Ubuntu 14.10. You are running Ubuntu
15.04. This means the script has NOT been tested for your OS.
Run this at your own risk.
Press enter to continue or Ctrl+C to exit
```

Edit
Just tried your way using root account to uninstall.  It appears to have worked just fine.

---

### Post by claudiocapobianchi on 2015-07-28
Hi all, I tried to change from "display immediately" to "download & install" security updates by launching software-properties-gtk within redit, but it didn't work, so I changed it within live and looked for changes in some configuration file, that's what I found:

just change /etc/apt/apt.conf.d/10periodic from

```
APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Download-Upgradeable-Packages "0";
APT::Periodic::AutocleanInterval "0";
APT::Periodic::Unattended-Upgrade "0";
```

to

```
APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Download-Upgradeable-Packages "1";
APT::Periodic::AutocleanInterval "0";
APT::Periodic::Unattended-Upgrade "1";
```

and edit the file within redit to do the trick, hope it helps!

Now I am going to try Ram session with /home copied, looking forward to get rid of being bottlenecked by 5400rpm hd :p

---

### Post by carlosdanielgs on 2015-07-31
Just wondering, will this work on a server edition ?

Greatings

---

### Post by crashnburn_in on 2015-08-24
Can I use this for a USB Flash based UBuntu install that I wish to use as a Utility? Pros & Cons?

---

### Post by tobi5 on 2015-09-17
I have an Ubuntu installed on an USB 3.0 Stick.
Now i want to try your script. Are there any disadvantages in this case?
Suffers the stick under to many write accesses or are they going directly in the ramdisk?

---

### Post by v3.xx on 2015-09-17
I have not tried this, but I do have this set up on my laptop and find the HDD down to hardly any usage (dual core/4G ram).  The ram_session will load at boot and I find it takes about 1G of ram.  Also note that this will now only work fully with v14.04.

So I would guess that it would speed things up considerably, if it works from USB.

@terminator14
I hope you consider upgrading your ram_session to work on 16.04.  I had it limping along in 15.04/15.10 and would love to use it for a few more years.

---

### Post by tobi5 on 2015-09-17
Hm, running the script which ends in running out of space for image :-(
My system Ubuntu 14.04 LTS is installed on 16GB usb stick:
/root 8GB
/swap 4GB
/home 3GB

Can someone please tell me how i have to split my partitions to make this script run succesfully?

---

### Post by v3.xx on 2015-09-18
As I said, I do not run from flash drive, but two ideas come to mind.

Cut your swap space in half (2G), see if that gives you enough room.

Or run without a separate home partition.

Just a couple of untried ideas :)

---

### Post by fernando29 on 2015-10-23
Hi @terminator14.

I am using your script on Ubuntu 14.04 and it works as espected, but I have a minor issue. I need /etc/default/grub to have 2 specific options, but it seems these setting are lost when the script is run. They are:

GRUB_CMDLINE_LINUX_DEFAULT="splash quiet"
GRUB_CMDLINE_LINUX="fbcon=map:1"

Is there some hack I could do in the script in order to keep these settings?.

In order to keep the size of the OS small, I have commented out from the script the lines related to git. The git checking (line 203) and "LOGGER" (line 410). Is it safe if I have no plan to make rupgrades in the future?.

Thanks and best regards.

---

### Post by unheatedgarage on 2015-10-27
> **claudiocapobianchi said:**
> Brilliant intuitions! anyway even under redit, software-properties-gtk doesn't let me choose another server, it always comes back to the original one. Checking redshift on gnome-session-properties doesn't make it start at reboot as well.

The error is just a crash report saying that software-properties-gtk has stopped unexpectedly, the system is working fine.

Thank you for the xprop tip!

Regarding Redshift, I had no problems with it auto-starting. However, I happened to have had the good fortune of stumbling upon [this wiki from the good people at Arch Linux]("https://wiki.archlinux.org/index.php/Redshift"), which then led me to [the developer's page]("http://jonls.dk/redshift/").

From what I pieced together from the two, Redshift looks for a configuration file (which must be created). If it doesn't find that file it just goes on ahead with its default settings. I had made that config file before I ran the RAM_booster script, so maybe that had something to do with it working in the RAM session? It auto-starts with no glitches or anything funky. I'm running Ubuntu Unity 14.04 LTS, by the way.

Thank you, Mr. **terminator14** for all your hard work writing and updating this script, for making the youtube video (which I've watched innumerable times), and for your patient replies to this thread, which really helped me trying to understand this thing. I looked on your github page and was saddened to see there isn't anyone else working on this? I'd think it would be a hot item, because it really does work! Anyway, you are a scholar and a gentleman.

Peace, love, and happiness.

---

### Post by dronya on 2016-03-28
Hey. How can I reduce the size of squashfs-file?

---

### Post by komputes on 2016-04-28
I'm a big fan of RAM Booster and the simplicity it offers  in making boot-to-ram images. Ubuntu 16.04 is now out and I was  wondering if RAM Booster would be re-factored.





I'm with v3.xx on this one, as I would love to see this project re-factored for 16.04. 

Looking forward to an  update. terminator14, are you still maintaining this?

---

