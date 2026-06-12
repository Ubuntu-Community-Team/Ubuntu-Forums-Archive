---
title: "Uninstall Ubuntu 10.10 and give space back to Windows 7. Sorry I tried to like Ubuntu"
date: 2010-10-26
forum: General Help
---

### Post by mindstormmaster1 on 2010-10-26
Sorry I know this is a sad thing to post, but after installing Ubuntu 10.10 I realized I only ever use Windows 7 so I just need to have Ubuntu gone and get my space back.

I was wondering I ran EASEUS Partition Master and it shows the ubuntu and the ubuntu swap partition as well as the windows partition and a data partition which I want to give ubuntus space to.  Is it as simple as using the program to format the ubuntu partitions and merge them to the data partition?  And if that does work how do I them get rid of grub as once I only have Windows 7 installed I wont need it.

Thank you,

Ethan

---

### Post by Quackers on 2010-10-27
You just need to delete the Ubuntu partitions. This will leave unallocated space which can then be added to another partition. I would advise you to run one step at a time.
NOTE You will then have a system that starts with grub and grub will fail due to the partitions having been deleted. You will need to restore the Windows MBR with the Windows repair disk.

---

### Post by katykat on 2010-10-27
Though i do not use win7, traditionally FDISK /MBR restores the boot partition to Windows disks. This should stop the grub2 loadup. (Oops... newer versions dont have FDISK. Use FIXBOOT at the recovery console :
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392) )



But, kindly, consider a few points. 

The new buggers created by the Russians will breeze right through Win7 as it, like all M$ software has gaping security holes by default in the software. Should the system go down, and if god forbid it is the only system you have you would need the expertise to be able to deal with a potentially damaged OS or risk expensive repairs. 

Linux would be a good option to use not only to be able to access the net safely, but also to repair the Win drive, as it would be able to see and replace virus files that cannot be accessed during a Windows session, often even from a boot disk. 

Its an insurance policy. 

But also remember that Linux out of the box looks like crap. Meerkat is the most impressive I've seen, and I've been running Linux on and off since version 0.9. 
And even Meerkat needed a good makeover. The utilities outside of Firefox are kludgy. The torrent clients suck. The newsreaders look horrid. The media players? Well...

But in most cases you'll find you can run your favorite Win apps like uTorrent (v2.0 at least) and other basic apps, and they will automagically run under wine after you install it.  And in an overall safer environment (though win apps can still be infected at least in theory). 

There are around 30,000 free apps on the repostories. And without a registry you can load as many as you want. Many are actually quite good and well designed, and open source guarantees that they will not be time bombed to shut down and demand moiney. 

So: You have more freedom of choice. And ALOT more options. 

Take Linux off your primary drive. 

Get a cheap second hand drive and install it , and load linux on that. 

And when you have spare time, play with it. 

It might grow on you.

---

### Post by choochoousmc on 2010-11-13
This doen't answer your question but like another said.
I wouldn't give up on Ubuntu so easily.
Yes it has some quirks and bugs. All software does.
I have been using windows since 3. And each version has gotten bigger and clunkier
and tried to be idiot proof, where it keeps protecting you from you. So sometimes you can't do what you want or need to.
Plus I don't like Gates way of doing business and charging so much for tech suppport.
And trying to squeeze out all the other OSes over the years.

I also was tired of having 5 different anti virus and malware programs. Of having to download programs from all over the net to increase my safety and security, and having
to pay for most of them. When they really should of been included in Windows. And then only getting 20 /25 times to use MS Office or such. Then have to buy it at an overly inflated price. 

so I started looking into Linux last winter. settled on Ubuntu.
for the most part all the commands, mouse movements, menus work just like Windows.
Very little tweaking was needed.
I installed some optional programs from the FREE repository. Some worked good and I liked, some not, so tried others.
so far I believe Linux has been more secure and crash proof than Windows ever was.

It recognized all my built in hardware right away, and saw my wireless router and internet connection as soon as it installed, and my wireless printer.
I plug my camera in and it sees it.
The "safely eject" USB drives, seems to work much better than windows.
Only thing that has not worked yet and it's not a big deal, is the scanner software.
Hopefully they will get that fixed in a future release.
So yes I would implore you to keep Ubuntu. Any program you have in windows, is probably available in Linux and for free to boot.
Or as another said. Install wine and run windows and windows apps from there.

---

### Post by victorhugo289 on 2010-11-13
why you're leaving?!  don't give up

---

