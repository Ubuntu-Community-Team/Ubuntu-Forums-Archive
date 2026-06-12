---
title: "Trying to Dual-Boot Windows 7 and Ubuntu"
date: 2011-09-02
forum: General Help
---

### Post by owenc on 2011-09-02
So, I currently run Ubuntu as  the sole OS on my Laptop. Using a G-Parted live CD I partitioned half of  my disk space, the one half dedicated to running Ubuntu and the other  half to Windows 7. I downloaded a torrent of Windows 7, one that I have  used before with success (so one that I trust) and burned it to a DVD-RW  at the slowest burning speed possible. I booted Windows 7 through the  DVD and began to do a clean install of Windows 7 on this one Partition  that I left completely empty for the new OS. Everything runs smoothly  and I go through the set-up until suddenly the installation hangs at 0%  when 'Expanding Windows Files'. I have exhausted pretty much all the  possibilities of what could be going wrong to my knowledge - saying that  however my knowledge isn't very extensive at all.

Could someone possible share some info on what I could be doing wrong?  I'm desperate to get Windows 7 up and running on this computer so I can  begin playing some games that are otherwise impossible or incredibly  difficult to get working on Ubuntu, notably, as an avid player of the  Football Manager series, the upcoming release of FM12.

If anyone can offer some sort of help/fix I'll be extremely grateful. Like seriously.

---

### Post by spiky001 on 2011-09-02
This is a linux forum you might have better luck in a Windows forum. Did you format the partition 1st with windows disc, It might be the download is no good

---

### Post by garvinrick4 on 2011-09-02
I know little about the installation of Windows 7 but when I purchased a laptop it came with Windows7 and
I burned 3 dvd's for Windows7 operating System. And did not use read write dvd. How big is your .iso of
Windows7?

---

### Post by PCFreak2 on 2011-09-02
1st primary partition should be SYSTEM
2nd primary partition should be Windows 7
Then shrink Windows 7 for Ubuntu and Swap (Make the swap size equal to your RAM, I would use GParted)
Format Swap in EXT3 (3rd partition)
Format Ubuntu in EXT3 (4th partition)
Then when u get here:

[IMG]http://www.ubuntu.com/sites/www.ubuntu.com/files/active/natty/04-allocate-drive-space.jpg[/IMG]

Click something else
Then select swap to be formatted as swap
And select Ubuntu partition and mount as /

---

### Post by Jerry N on 2011-09-02
To PCFreak2:  Please don't confuse the OP - he already has Ubuntu and wants to add Windows 7, not the other way around.

When I am setting up for multiboot, I always use gparted to format the Windows partition to NTFS before installing Windows.  This has worked for me on numerous installs of Win2000, Win XP, and Win 7.

Jerry

---

### Post by owenc on 2011-09-02
> **spiky001 said:**
> This is a linux forum you might have better luck in a Windows forum. Did you format the partition 1st with windows disc, It might be the download is no good

Cheers mate, fair enough! 

> **garvinrick4 said:**
> I know little about the installation of Windows 7 but when I purchased a laptop it came with Windows7 and
I burned 3 dvd's for Windows7 operating System. And did not use read write dvd. How big is your .iso of
Windows7?

It's about 4.4gb.

> **PCFreak2 said:**
> 1st primary partition should be SYSTEM
2nd primary partition should be Windows 7
Then shrink Windows 7 for Ubuntu and Swap (Make the swap size equal to your RAM, I would use GParted)
Format Swap in EXT3 (3rd partition)
Format Ubuntu in EXT3 (4th partition)
Then when u get here:

[IMG]http://www.ubuntu.com/sites/www.ubuntu.com/files/active/natty/04-allocate-drive-space.jpg[/IMG]

Click something else
Then select swap to be formatted as swap
And select Ubuntu partition and mount as /

Apologies mate but if I understood your instructions correctly I think you're assuming that I already have Windows 7 and I'm installing Ubuntu side-by-side whereas it's actually the other way round? Or have I got you completely wrong?

---

### Post by owenc on 2011-09-02
> **Jerry N said:**
> To PCFreak2:  Please don't confuse the OP - he already has Ubuntu and wants to add Windows 7, not the other way around.

When I am setting up for multiboot, I always use gparted to format the Windows partition to NTFS before installing Windows.  This has worked for me on numerous installs of Win2000, Win XP, and Win 7.

Jerry

Ah so I wasn't getting mixed up :p! Thanks for the help Jerry but sad to say I've already formatted the Windows Partition to NTFS - I believe it's required for you to even load up the install load up the installation process. Cheers Jerry:)!

---

### Post by garvinrick4 on 2011-09-02
> It's about 4.4gb.My Windows 7 disks are about 10.8 gig

---

### Post by owenc on 2011-09-02
> **garvinrick4 said:**
> My Windows 7 disks are about 12 gig.

Strange.. the torrent that I have used this time however has been successful for me in the past so the legitimacy of the ISO isn't an issue for me. Ergh, have such a love/hate relationship with computers :p!

---

### Post by Jerry N on 2011-09-03
I might be wrong but I think Windows must be installed in the first partition on the drive - sda1.

Jerry

---

### Post by Starfleet on 2011-09-03
Jerry N is correct. You can only install Windows 7 on a primary partition. Windows will not install if Ubuntu is already on the hd occupying that space. I'm afraid you must back up your current Ubuntu installation and reload Windows as the first system on the drive. Then re-install Ubuntu in the usual way using the 'side by side' installation technique. It's very straight forward.

---

### Post by Jerry N on 2011-09-03
> **Starfleet said:**
> Jerry N is correct. You can only install Windows 7 on a primary partition. Windows will not install if Ubuntu is already on the hd occupying that space. I'm afraid you must back up your current Ubuntu installation and reload Windows as the first system on the drive. Then re-install Ubuntu in the usual way using the 'side by side' installation technique. It's very straight forward.

I prefer the manual install myself but then I have done it over 100 times.

Jerry

P.S. ...and I can still find ways to screw it up!

---

