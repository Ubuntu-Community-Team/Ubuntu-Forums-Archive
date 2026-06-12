---
title: "Evolution message store moving it to another drive"
date: 2011-01-23
forum: General Help
---

### Post by blahsnr on 2011-01-23
Hi I have the netbook remix (10.10 running with the Gnome desktop) installed on a 4 GB SSD on my EEEPC. Unfortunately the tendency for Linux apps to put data (emails, firefox cache) on the OS drive means that I am rapidly running out of space. 

Is there a simple idiot's guide to moving the .evolution folder to another drive? An hour of searching on the net has failed to find one that I feel confident in trying. I am used to using the command line if the commands are clearly explained. 

Are there any other tips for minimizing usage of the limited space on the OS disk (besides sudo apt-get clean=?

Thanks in advance
Stan

---

### Post by dcstar on 2011-01-24
> **blahsnr said:**
> Hi I have the netbook remix (10.10 running with the Gnome desktop) installed on a 4 GB SSD on my EEEPC. Unfortunately the tendency for Linux apps to put data (emails, firefox cache) on the OS drive means that I am rapidly running out of space. 

Is there a simple idiot's guide to moving the .evolution folder to another drive? An hour of searching on the net has failed to find one that I feel confident in trying. I am used to using the command line if the commands are clearly explained. 

Are there any other tips for minimizing usage of the limited space on the OS disk (besides sudo apt-get clean=?

Thanks in advance
Stan

You can replace the original .evolution with a link to another folder on a **Linux filesystem**. Just make sure all the permissions are correct.

Do not (ever) try to move Linux program files/folders to crap filesystems like NTFS or FAT.

---

### Post by HermanAB on 2011-01-24
Howdy,

The trick is to install Linux with multiple partitions.

I stuck a 16GB camera card into my Eeep, formatted it with ext3 and use it as the /tmp, /swap, /usr, /var and /home partitions.

---

### Post by blahsnr on 2011-01-24
> **HermanAB said:**
> Howdy,

The trick is to install Linux with multiple partitions.

I stuck a 16GB camera card into my Eeep, formatted it with ext3 and use it as the /tmp, /swap, /usr, /var and /home partitions.
But not if you dont want to take your EeePC apart to get at the SSD that is fixed to the motherboard and replace it with a 16GB one.

I had a 16GB SDHC card with Ubuntu 10.10 but for the second time in a month a set of Ubuntu updates has stuffed grub on that card. :-| I am hoping that installing it on the internal SSD card will make Ubuntu more reliable and resilient to accepting its own upgrades without commiting boot suicide. I want to use the slower internal 16GB SSD as a data store.

At least with the OS installed on the 4GB internal card I should be able to get the grub install working on the 16GB SDHC card with the chroot method (when I can be bothered to).

Thanks for the suggestion though.
Regards
Stan

---

### Post by blahsnr on 2011-01-24
> **dcstar said:**
> You can replace the original .evolution with a link to another folder on a **Linux filesystem**. Just make sure all the permissions are correct.

Do not (ever) try to move Linux program files/folders to crap filesystems like NTFS or FAT.
Well blow me, that actually seems to work. It cannot be that simple can it? :D

Just to check I did the right thing, I copied the .evolution folder to media/linuxstore and created a link
I renamed .evolution on the original drive to .evolutionOK.
I copied the link into the folder where .evolutionOK was and renamed the link to .evolution . I then moved .evolutionOK to the trash bin.
I then started up Evolution and downloaded mail. The copy folder on media/linuxstore grew in size whilst the original home directory did not.

If this is correct, is it possible to do the same with the .mozilla folder and other such program folders?
Cheers
Stan

---

