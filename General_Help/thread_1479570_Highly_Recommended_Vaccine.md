---
title: "Highly Recommended Vaccine"
date: 2010-05-10
forum: General Help
---

### Post by Ron O on 2010-05-10
I put much of this in another post but thought it should be posted as a new thread.

I recently had a new installation of Xubuntu Lucid corrupted after a week with a boot-up halt screen relating to mounting issues that I spent hours researching and could not fix. Since I am not that good at transferring items from a previous installation into a fresh install (and wonder how reliable this is), it takes me 2 nights to get a fresh install tweaked the way I want it. But luckily, I had made an image of my tweaked installation about an hour or two before my system became corrupted, so I just restored that image in about 5 minutes.

I HIGHLY recommend downloading the Parted Magic live cd (boot cd) and burn as an iso. Google PartedMagic. It comes with an app called CloneZilla which is awesome- on the idea of Norton Ghost, only more reliable. To use, all you have to do is set the bios to boot from CD, hook up a usb hard drive, and make an image of your ubuntu partition onto the external hard drive. Since it does not copy free space when you back up a partition, it is very fast (5-10 minutes to back up or restore), and the restores are flawless. Every time my system is running perfectly, I make an image, then restore it if I have issues that I or the community cannot solve in a reasonable time. It is easy to use, fast, and reliable and saves hours of trying to decipher system logs, researching fixes, or loading additional packages in the hopes of getting help. It is way better than ANY backup scheme that approaches backups from a file level rather than a partition level. And it makes you un-afraid to try something on your current system for fear of doing your installation irreversible harm.

I am using the Parted Magic 4.3 CD which includes CloneZilla that I got about a year ago, and can testify that it works perfectly, so I'm guessing the new one does as well. Follow the on-screen directions exactly since a few items may be counterintuitive- like for a backup you define the target first (external hard drive) and then the source (your ubuntu partition) second. And you select save parts (system partition) rather than the entire disk. The program mounts and unmounts partitions on both drives as needed to make the image. You can also use it to clone a Windoze installation if you have not completely severed that relationship by now. This program saved me 2 days work doing another fresh Lucid install with all the tweaks to Firefox etc etc. I just had to send PartedMagic a donation.

Whenever I have one of those moments when I am complimenting myself on a perfectly functioning and built-up system, I load CloneZilla and make an image. In fact, when I first installed Lucid with the alt cd, it took way longer than I expected, so I imaged the raw installation before I made many changes to it.

I thought I should post this now since Lucid LTS has just been released, and you can try it on a system with no personal data on it yet. Image your old system as a fall back, then install Lucid. But be aware that you cannot read or restore individual files, only the entire partition, but this is the key to it's absolute reliability. Some people actually complained about this. 

If anyone feels they need a step by step guide with screenshots, I'll write one on the version I am using and make a pdf if I am allowed by the developers.

---

### Post by zvacet on 2010-05-11
Write **How to** or **tutorial**.I think it will be good reference.

---

### Post by Ron O on 2010-05-16
The Clonezilla version I used had no version number, only the Parted Magic on the CD had a version number, but judging from the date, it was pretty old. I just downloaded the latest Clonezilla from THEIR website and it seems substantially similar. I'll have to try this version first and do screenshots.

---

### Post by kaibob on 2010-05-16
I agree that clonezilla is excellent. I always accept the defaults and only select the image file name, location, and the like. There is a decent howto at:

[http://www.tuxradar.com/content/how-clone-hard-drives-clonezilla](http://www.tuxradar.com/content/how-clone-hard-drives-clonezilla)

---

