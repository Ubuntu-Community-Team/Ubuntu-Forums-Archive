---
title: "boot error USB won't boot"
date: 2011-09-20
forum: General Help
---

### Post by beaver_313 on 2011-09-20
Ok so I have a Toshiba NB505-500 netbook that I am trying to install ANYTHING other than Puppy Linux onto but I can't seem to get it to work. I'm just trying to boot from USB, CD/DVD isn't an option here.

I have tried formatting in FAT and FAT32 neither of which work.

Problem:
  Using unetbootin I check the syslinux.cfg file and it looks ok then I try to boot the USB and I get to a boot error screen and when I check the syslinux.cfg file (using notepad++) afterwards it has been almost wiped but not really there are just a bunch of NULL symbols.

  Using Universal USB Installer I do the same thing and I get a syslinux error No default Configuration or UI file found and again some of my stuff has been erased from the USB.

What is going on??

---

### Post by beaver_313 on 2011-09-20
bumpity bump

---

### Post by beaver_313 on 2011-09-20
Anyone got anything?

---

### Post by ddr3XD on 2011-09-20
if using Linux: [http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)

if using Windows: [http://www.pendrivelinux.com/yumi-multiboot-usb-creator/](http://www.pendrivelinux.com/yumi-multiboot-usb-creator/)

---

### Post by beaver_313 on 2011-09-20
Nope, I tried using YUMI and it worked up until i clicked the linux distro and then the screen went blank and only showed


boot:

---

### Post by beaver_313 on 2011-09-20
Also, I noticed that after I got the boot: screen when I shut down the computer and took the flash drive to my desktop the entire 

syslinux folder of the Linux Distro was empty.

Somehow it had been deleted entirely and I don't know why but I feel like this is the problem somehow my computer is deleting the folder I need to boot the distro.

---

### Post by beaver_313 on 2011-09-20
bump

---

### Post by ddr3XD on 2011-09-20
First question: Have you even manage to boot off of the usb drive yet?
Second question: What OS are you trying to install/boot?

---

### Post by beaver_313 on 2011-09-20
Yes, I can boot puppy linux, dsl, and other really small distros that don't need any folders or anything and I can also boot Windows 7 starter though I can't install that because I get to the setup and it asks to locate the cd/dvd driver even though it's a netbook.

I am trying to install Ubuntu, Fedora, OpenSUSE, LinuxMint, anything really other than the small ones.

---

### Post by ddr3XD on 2011-09-20
> **beaver_313 said:**
> Yes, I can boot puppy linux, dsl, and other really small distros that don't need any folders or anything and I can also boot Windows 7 starter though I can't install that because I get to the setup and it asks to locate the cd/dvd driver even though it's a netbook.

I am trying to install Ubuntu, Fedora, OpenSUSE, LinuxMint, anything really other than the small ones.

So what exactly happens when you try any other ones but the small ones? And can you be more specific with which one your trying to boot because from what I understand so far is that it wont boot any of "The Big" ones but boots "The Small" ones, which would indicate your ram could be malfunctioning or maybe your just doing something wrong.

---

### Post by beaver_313 on 2011-09-20
Check out the attachment. This is what happened after I tried to boot lubuntu usin YUMI from my USB.

Trying to boot Lubuntu produces the error below and nothing happens.

Boot:

---

### Post by ddr3XD on 2011-09-20
Im gonna try this just to make sure it isnt an issue with YUMI itself. So give me some time and ill post my results when im done. And that means no "Bumpity Bump-ing" the thread either lol

---

### Post by ddr3XD on 2011-09-20
When installing Lubuntu using YUMI, did you tick the checkbox that said "Download the iso"? Because if you did that is most likely your problem there

---

### Post by beaver_313 on 2011-09-20
No, I didn't I had already downloaded it previously. =/

Thank you for the help and quick replies btw. I appreciate it.

---

### Post by ddr3XD on 2011-09-20
Ok. Hey can i try Ubuntu? cause im really not in the mood to wait for Lubuntu to finish downloading right now?

PS: Ubuntu does the same thing as Lubuntu right?

---

### Post by beaver_313 on 2011-09-21
Yea sure they are almost identical so it should work the same way.

---

### Post by ddr3XD on 2011-09-21
Well i just successfully booted Ubuntu. So i think somethings wrong on your end. Have you got another flash drive you could try? And also i think there should be some tool for Windows that installs Ubuntu onto a usb drive, ill see if i can find that for you.

EDIT: Lol its located right inside the Ubuntu iso. Its called usb-creator.exe, u should give that a try. I think that should most definitely work.

---

### Post by beaver_313 on 2011-09-21
Alright I'll give it a shot and let you know how it goes tomorrow.
Thanks again!

---

### Post by georgejoy1 on 2012-03-08
well when you use yumi or any boot loader, the problem arises the moment after you alter the partition table after you installing yumi to it. Well i am looking a way to resolve this but until now nothing has shown up

---

