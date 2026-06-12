---
title: "New iso image of lucid lynx"
date: 2010-05-20
forum: General Help
---

### Post by Midnytpudding on 2010-05-20
i had been trying to install lucid 64bit on my machine for a number of days now with no  proper success, using either cd or flash drives, most of the time problems interrupts installations but sometimes succeeds, but when i install the latest updates, my system always gets broken.

will canonical release a new disc image of lucid  with the latest updates included? thank you.

---

### Post by dino99 on 2010-05-20
follow this thread:

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by iponeverything on 2010-05-20
> **Midnytpudding said:**
> i had been trying to install lucid 64bit on my machine for a number of days now with no  proper success, using either cd or flash drives, most of the time problems interrupts installations but sometimes succeeds, but when i install the latest updates, my system always gets broken.

will canonical release a new disc image of lucid  with the latest updates included? thank you.

Have your tried the alternate disk? 

[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

---

### Post by Midnytpudding on 2010-05-20
thank you for the quick replies.

[dino99]("http://ubuntuforums.org/member.php?u=129712") - i want ubuntu to be my  primary os with no other partitions.

[iponeverything]("http://ubuntuforums.org/member.php?u=643833") - yes, but with no success.

---

### Post by Midnytpudding on 2010-05-20
i am now currently installing ubuntu 9.10 64bit using a flash drive, and maybe, upgrade to lucid from there.

---

### Post by Midnytpudding on 2010-05-20
dunno if this will work.. **cross fingers**

---

### Post by iponeverything on 2010-05-20
I don't really know if they update ISO or not, I don't think that they do.

---

### Post by dino99 on 2010-05-20
> **Midnytpudding said:**
> thank you for the quick replies.

[dino99]("http://ubuntuforums.org/member.php?u=129712") - i want ubuntu to be my  primary os with no other partitions.

[iponeverything]("http://ubuntuforums.org/member.php?u=643833") - yes, but with no success.

post # 2 is ok for 1 to 999 installed distro :P just follow the spirit :)

---

### Post by Midnytpudding on 2010-05-20
still, i cant install ubuntu 9.10 or 10.4 properly on my machine..

---

### Post by Midnytpudding on 2010-05-20
btw, my system specs are:

cpu: intel core i5-750
vga: powercolor radeon hd 5750
chipset: asus p7p55d-e
ram: 4gig ddr3 1033
hd: 500gig

---

### Post by bodhi.zazen on 2010-05-20
> **Midnytpudding said:**
> i had been trying to install lucid 64bit on my machine for a number of days now with no  proper success, using either cd or flash drives, most of the time problems interrupts installations but sometimes succeeds, but when i install the latest updates, my system always gets broken.

will canonical release a new disc image of lucid  with the latest updates included? thank you.

I believe there are plans to release Ubuntu 10.04.1 in July, this is at lease what they say in the release announcement:

[https://lists.ubuntu.com/archives/ubuntu-announce/2010-April/000133.html](https://lists.ubuntu.com/archives/ubuntu-announce/2010-April/000133.html)

I would not expect an updated iso before that time.

If the Ubuntu Alternate CD fails, you will have to try to figure out why or try another OS. I have a box that will not run Ubuntu due to an as of yet unpatched BUG (fix released, but not committed). I found that by determining the problem and searching the bug reports, so, on this particular box, 

no fix == no Ubuntu , I can not write the code myself.

Fedora 13 runs fairly well, a few small issues with gallium.

Without knowing the problem, simply stating that it is broken makes it difficult to help you. I understand figuring out the problem is not easy, but if you can not, try a different distro.

---

### Post by Midnytpudding on 2010-05-21
thank you for the reply.

up to now, my experience with lucid is unsatisfactory, i am still unsuccessful.  

one issue that i have experienced is that when i install updates in lucid , after a reboot, i get a  install problem in configuration of gnome power management. and then everything is broken, i cant install or uninstall packages/programs.

---

### Post by Midnytpudding on 2010-05-21
is it possible to install the latest ubuntu updates for lucid on a flash drive? then, install lucid using the flash drive along with the updates?

---

### Post by bodhi.zazen on 2010-05-21
> **Midnytpudding said:**
> is it possible to install the latest ubuntu updates for lucid on a flash drive? then, install lucid using the flash drive along with the updates?

IMO the esaiest thing to do is use the minimal CD.

This is a net install and downloads and installs the latest packages.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

BUT , I would also tell you, if if is broken when you upgrade it will probably also be broken with the method you are using.

I think you are barking up the wrong tree, you need to try to identify the problem, not blindly install packages and hope for the best ...

Edit: I give this advice because, as I indicated in my previous post, on one machine I too have a bug, Ubuntu 10.04 will not boot properly. Once I identified the problem (in general terms) I did a google search -> looked at a few launchpad reports -> found the "bug report" for the problem I am having, and am subscribed to the bug report. Until a fix is available it does not really matter how many times I install and update Ubuntu, it will fail.

But, because I am subscribed to the bug report, I will get an email when a fix is available, and I will then know I can try to install at that time.

My solution, on the machine in question, which is used by my children, was to install Fedora 13. There were a few initial bugs, but I was able to solve or work around them.

Once Ubuntu releases a fix they can easily be migrated to Ubuntu.

---

### Post by sandyd on 2010-05-21
> **Midnytpudding said:**
> btw, my system specs are:

cpu: intel core i5-750
vga: powercolor radeon hd 5750
chipset: asus p7p55d-e
ram: 4gig ddr3 1033
hd: 500gig

according to your specs, 10.04 should install, but not 9.10 (because of your motherboard and CPU). there was a user with the same specs as you who succeded in installing the beta version of lucid lynx (10.04). did you verify the md5sum of the isos?

---

### Post by Midnytpudding on 2010-05-21
nope, im too lazy to do that but i downloaded iso images of lucid mutiple times now (torrent or direct), and burned it on cds and dvds at 4x speed, i also tried installing lucid using two diff. flash drives but i am still unsuccessful.

i know, 9.10 is not for my system but i just want to try out other ways to install.

---

### Post by Midnytpudding on 2010-05-21
[[COLOR=#980101]**bodhi.zazen**[/COLOR]]("http://ubuntuforums.org/member.php?u=89054"), thank you for the advice, ill try your solution and take note of the problems..

---

