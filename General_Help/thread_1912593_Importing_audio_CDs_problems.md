---
title: "Importing audio CDs problems"
date: 2012-01-20
forum: General Help
---

### Post by Welly Wu on 2012-01-20
I have an ASUS N61JV-X2 notebook PC with Crucial 8 gigabytes of DDR3 PC-8500 SDRAM and an Intel 2nd Generation MLC NAND FLASH X25-M 160 gigabyte Solid State Drive. I am using Ubuntu 10.04.3 64 bit LTS. I also have a Seagate FreeAgent Desk 1.5 terabyte USB 2 external hard disk drive and a new Kingston DataTraveler HyperX Super Speed USB 3 thumb drive.

I am using Banshee and I am trying to import audio CDs, but most of the time it says that it can not find the metadata for the CD in question. I am getting this problem all of the time. Rhythmbox has the same problem.

I read somewhere that they use Musicbrainz and there is a known problem because they changed their something that prevents these software packages from accessing their metadata server or something else is the problem.

How do I import all of my CDs with the metadata? What software package will get the job done?

I plan to upgrade to Ubuntu 12.04 64 bit LTS on April 26th, 2012. Will this help to solve my problems?

Please offer solutions that will help me to import the metadata for all of my CDs. I plan to rip and compress them into lossless .FLAC files.

Thank you.

---

### Post by Welly Wu on 2012-01-20
I also use TrueCrypt for my Seagate FreeAgent Desk and Kingston DataTraveler HyperX. I setup Ubuntu 10.04.3 64 bit with LUKS/LVM for full disk encryption and I also encrypted my home partition with separate and strong passwords. I can access my encrypted data with the right passwords, but I am having problems importing the metadata for all of my audio CDs.

---

### Post by Welly Wu on 2012-01-21
Can anyone shed some light on this subject matter? Why is it that the most popular software packages used to rip CDs can not get the metadata for most CDs? How am I going to solve this problem?

---

### Post by mc4man on 2012-01-21
I'm not up on how this works in lucid, haven't used in quite some time. I do know that it was quite broken in 11.04 & 11.10.

It was, after a bit of back & forth fixed finally in 11.10 though not sure if the fix made it back further.

The first 'fix' supposedly was here though as I tried to relay it wasn't
[https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/784179](https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/784179)

The actual fix occurred here in 11.10 & is still good in 12.04
[https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/813836](https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/813836)

So your options would be - 
Try to build the latest banshee source where the fix is included, may or may not be easy on 10.04
Get the last banshee source that will build on 10.04 & patch it yourself if not fixed

Try using the Team banshee daily ppa (not really a daily), maybe the build for 10.04 has the fix, the last lucid build was on 10/13
[https://launchpad.net/~banshee-team/+archive/banshee-daily](https://launchpad.net/~banshee-team/+archive/banshee-daily)

Use something else to rip your cd's that uses a cddb lookup instead - what are you ripping your cd's to?

---

### Post by Welly Wu on 2012-01-21
I just added the Team Banshee PPA and I installed the new version of Banshee for Ubuntu 10.04.3 64 bit LTS. I tried three audio CDs and I still can not pull the metadata for those CDs. It looks like I am going to have to upgrade to the latest version of Ubuntu 64 bit to see whether this problem was fixed in Ubuntu 11.10 64 bit or not. I am going to remove the PPA now that I know it won't fix the problem in 10.04.3 64 bit LTS.

I save my .FLAC files to my Seagate FreeAgent Desk external hard disk drive.

Which software packages use CDDB in order to pull metadata for CDs?

---

### Post by mc4man on 2012-01-21
I use either abcde or rubyripper, both are excellent but - 
abcde is a cli app, though it can & usually is configured thru a conf file. So once set up is generally easy to use. Available in repo - a UF member's get started guide
[http://www.andrews-corner.org/abcde.html#flac](http://www.andrews-corner.org/abcde.html#flac)

rubyripper is both gui & cli, but 10.04 thru 11.10 use a bugged ruby version whichs causes RR to hang between tracks when run from the gui.
 One solution is to set up RR thru the gui, then start it from cli. 
The other involves building ruby-gtk from a later version for RR to use. RR does work quite well. I've got several single posts on how to do for various ubuntu releases, may have done one for lucid, would have to check.

What you might first want to take a look at is ripperX, should do the job for you.
There are several others, search the forum if need be...

Edit; I have a how-to post on RR for 10.10 that will work for 10.04 with 1 change. It uses a ppa to provide a good ruby alternative show the whole deal maybe takes 5-10 min, pretty easy.
Let me know

---

### Post by Welly Wu on 2012-01-21
I am in the process of upgrading to Ubuntu 11.10 64 bit right now. I will see if this fixes Banshee with regard to pulling the metadata for my audio CDs. I will be back in about 30 minutes.

---

### Post by Welly Wu on 2012-01-21
I finished my upgrade to Ubuntu 11.10 64 bit.

This new version of Banshee seems to have solved the problem. Out of a dozen or more CDs, I am able to pull the metadata for almost all of them except one new CD which I purchased last week. I will update this thread as I progress through my 1,100+ CDs with Banshee.

---

### Post by mc4man on 2012-01-21
Should  go fairly well, when I was testing the patch it did very well though subsequent to that i did find some more obscure titles that weren't found thru musicbrainz. 
(out of those cddb did retrieve them ,* as noted generally use RR/abcde anyway

---

### Post by Welly Wu on 2012-01-22
I copied 20 CDs so far and Banshee pulled the metadata for almost all of them except for 1 CD which I bought last week. I am guessing that it is too new so I will mark it to be imported at a later date. This is great news for me because I have a CD library in excess of 1,100+ CDs. I want to import them with the metadata into Banshee and convert them to .FLAC files onto my TrueCrypt protected Seagate FreeAgent Desk 1.5 terabyte external hard disk drive. I estimate that it will take up about 345 gigabytes when I am done. I have done this before using Apple iTunes and their proprietary ALAC format. This time, I want no DRM or any type of digital handcuffs to any of my media library which is why I switched to Ubuntu 11.10 64 bit from Microsoft Windows 7 Ultimate 64 bit. I made the right decision. Ubuntu is a far superior operating system and it is easier to learn how to use on a daily basis. Banshee is a good music player. I like it a lot.

I am thinking about installing Amarok because it gives me information about the artists and albums which is a nice feature. It is also a very slick interface. I think that I will install it from the Software Center today.

Thanks for the tip. If I did not know that Ubuntu 11.10 64 bit would solve my problems, then I would not have restarted this CD ripping project.

---

### Post by Welly Wu on 2012-01-22
I finished trying to import 106 CDs. Out of that number, Banshee could not pull the metadata for 9 CDs. Most of them were copies of the original CDs. So, it has a success rate of almost 85 percent. Not bad at all. This is a big improvement from last time when I had Ubuntu 10.04.3 64 bit LTS and an older version of Banshee.

---

### Post by Welly Wu on 2012-01-24
RipperX seems to be able to take care of the 12 CDs that I could not pull the metadata information from Banshee. I am ripping those 12 CDs right now using RipperX and the .FLAC add-on. It seems to be working properly albeit very slowly. Thanks for the tips!

---

