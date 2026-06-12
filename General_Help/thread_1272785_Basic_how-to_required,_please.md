---
title: "Basic how-to required, please"
date: 2009-09-22
forum: General Help
---

### Post by TXbirder on 2009-09-22
I am a complete beginner here.  I've used WinXP for years and want to try Ubuntu on my new netbook.  I have never installed an OS before.

I have a flashdrive that I have wiped clean.  If I download the Netbook Remix on the flash drive, then what?  On the download page there is a link to "*how to install UNR".  I read it and I understand virtually nothing on that page.*

Is there a much simpler page of instructions written for the complete Ubuntu novice using no technical terms- for someone who has no idea what an md5 sum(hash) is and finds Oliver's PPA total gibberish?

I have minimal DSL and it will take 2-3 hours to download the URM.  When the download is complete what should I see when I look at the contents of the flashdrive?  I use WinXP:  Start>My Computer>and then open the flash drive.  If all downloaded correctly, what should I see?

John

---

### Post by P4man on 2009-09-22
The MD5 checksum ensures the download is not corrupted. Its optional, and in fact, you can safely skip it, as there is an easier way to verify your stick (when you boot from the stick, in the main menu you will see an option "verify this disc for errors", and running that will ensure the download was okay, and everything is ok on the stick). Even that you can skip.

Now as how to make the stick.. the instructions are actually quite clear I think. You have to follow the "windows" instructions, Ill quote them here:

   1. Download the desired .img file
   2.

      Download Disk Imager from [https://launchpad.net/win32-image-writer/+download](https://launchpad.net/win32-image-writer/+download)
   3. Insert your flash media
   4. Note the drive letter assigned to your flash media
   5. Start Disk Imager
   6. Select the downloaded file and target device, and click "Write"
   7. Remove your flash media when the operation is complete 


If you got any problems with that, let us know what exactly.

Once you made the stick, you'll have to reboot the computer, and go in to your bios to change the boot device. This is different on each computer, so i can't give you exact instructions. usually you have to press "del" or F1 or F2 right after powering on to enter the bios. Then look for "boot" and set it so it boots from a USB device. Some bioses also have a "select boot device" menu you can access with another key, on my computer its F11, but again it varries.

IF you've gotten that far, you should be greeted with an ubuntu menu, allowing to test ubuntu from the stick (first option in the list).

---

### Post by TXbirder on 2009-09-22
Thanks.  
John

---

### Post by TXbirder on 2009-09-26
In addition to WinXP there are programs like IE and Acrobat Reader that came in my new netbook.  I guess those wont work with Ubuntu.  Practically speaking, can you carry on with just Linux in the computer or do you have to have Windows in there too?

John

---

### Post by MelDJ on 2009-09-26
> **TXbirder said:**
> In addition to WinXP there are programs like IE and Acrobat Reader that came in my new netbook.  I guess those wont work with Ubuntu.  Practically speaking, can you carry on with just Linux in the computer or do you have to have Windows in there too?

John

acrobat is available in the repositories. There is firefox to replace IE. Or you could use wine to run IE in ubuntu. you could run a windows under virtualbox if you really need to

---

### Post by Barijazz on 2009-09-26
> **MelDJ said:**
> acrobat is available in the repositories. There is firefox to replace IE. Or you could use wine to run IE in ubuntu. you could run a windows under virtualbox if you really need to

UNR comes with a PDF-compatible open source Document Viewer.  Firefox 3 is also part of the software bundled with UNR.  If you prefer Acrobat and IE, no prob.

If you haven't heard of it, Wine is, in simple terms, a Windows emulator.  It will allow you to install and run Windows programs in Ubuntu.  Its easy to install and usually runs well without any configuring.  While it doesn't use a lot of system power, netbooks are running on a budget as it is, so programs may not run as fast or as smoothly as they do in WinXP natively.  Nonetheless, if the program you want runs well in Wine, the hardest part will be figuring out how to get it from the CD to your harddrive.

---

### Post by gordintoronto on 2009-09-26
> **TXbirder said:**
> In addition to WinXP there are programs like IE and Acrobat Reader that came in my new netbook.  I guess those wont work with Ubuntu.  Practically speaking, can you carry on with just Linux in the computer or do you have to have Windows in there too?

John

Ubuntu includes a set of application programs, including email, web browser, instant messenger, PDF viewer etc.

It also includes a program called Synaptic, which lets you search a "repository" holding thousands of applications.  It takes about four mouse clicks to install an application you want to try, and you even get automatic updates to the applications as well as the OS.

---

### Post by TXbirder on 2009-09-27
Thanks to you all.
John

---

### Post by TXbirder on 2009-09-27
Just thought of something else:  When I began to download on to my new netbook, it failed because it seems there is something missing from the computer that allows an img file to be downloaded.  So I will use my desktop rather than add a program to the netbook.

If I read correctly I need the Disk Imager in my desktop in order to move the downloaded img file onto the stick.  Do I also need Disk Imager in my netbook when I load the img file from stick to netbook?

John

---

### Post by Dareth on 2009-09-27
It shouldn't; basically, when you write an image to a usb drive, it allows the computer to read it like a cd. You only need the Disk Imager to write it to the stick, not to read it.

---

### Post by TXbirder on 2009-09-27
Thanks

---

### Post by TXbirder on 2009-09-27
Well, I am stuck.    I have Ubuntu in the flash memeory.  I have opened the Toshiba Hardware Setup screen, selected Boot Priority and a menu offers HDD, FDD, LAN.

Do I want FDD?  

John

---

### Post by gordintoronto on 2009-09-27
> **TXbirder said:**
> Well, I am stuck.    I have Ubuntu in the flash memeory.  I have opened the Toshiba Hardware Setup screen, selected Boot Priority and a menu offers HDD, FDD, LAN.

Do I want FDD?  

John

FDD is Floppy disk drive.  It appears that your computer does not support booting from USB.

---

### Post by Tamalin on 2009-09-27
Uh, oh!  You could try an alternative install method, but I didn't see one on the front page.

---

### Post by TXbirder on 2009-09-27
The computer is a Toshiba NB205.

John

---

### Post by P4man on 2009-09-28
IT seems your bios will only show the USB boot option when it detects a bootable USB drive (according to this link : [http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/toshiba-nb205-n210-no-external-boot-drive-753699/](http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/toshiba-nb205-n210-no-external-boot-drive-753699/))

So either you didn't have the usb stick inserted, or you didn't make it properly?

---

### Post by TXbirder on 2009-09-28
I tried inserting the flash drive both before and after Hardware Setup and the computer still doesn't recognize the stick.   I tried WUFU but it started downloading a new copy or Ubuntu rather that setting the computer so I could download the copy I have in the stick.
 
I am about to give up on Ubuntu.  Too much work.
 
John

---

### Post by P4man on 2009-09-28
Dont get me wrong, but if you can't manage to make a bootable usb stick, or find it too much work, then linux (or for that matter, switching to ANY other OS) is probably not for you anyway.

---

### Post by TXbirder on 2009-09-28
Well, excuse me for not being as wonderful as you are.

---

### Post by P4man on 2009-09-29
It has nothing to do with being "wonderful". Switching to and Learning a new OS takes a considerable amount of time and effort, whether that OS is OS-X, Windows or linux.  If you're unwilling or unable to commit that, that's fine of course, thats your choice, not everyone wants to change their OS, but if the first hurdle to take (getting a bootable USB stick) is already  too much work, then most likely the rest will be far too much work/effort.

Your motivation for trying something else may grow the next time your windows gets hit by a virus, and the amount of effort you'll need to clean it may inspire you to give ubuntu a second chance. Should that happen, try a different USB stick. If not, enjoy your netbook regardless of the OS :)

edit: btw, should you ever want to upgrade or reinstall windows, you'll face the exact same installation issues, only far worse. Since you have no CDRom drive, you'll need a bootable USB stick just like for ubuntu, but unlike ubuntu, neither XP nor windows 7 allow booting from a stick without jumping through hoops.

---

