---
title: "Failed install issue (trouble booting)"
date: 2006-03-12
forum: General Help
---

### Post by Jonas54 on 2006-03-12
Okay, so I decided to try out Ubuntu and install it on an old PIII 450MHz. The install started off okay but was taking forever to install the base system, so I ended up leaving it and going to bed. 

The next day I came back to it and it was at a blank screen with "GRUB" at the top left and I was unable to type anything. I rebooted and started the install process all over again. This time it encountered an error, it was unable to install the base system. I then tried re-burning the install disk at a slower speed and tried installing it again, no luck.

I figured perhaps it was an issue with Ubuntu and my hardware and decided to try installing the latest version of SuSE, since that worked fine before. Here's where my main problem comes in, the system didn't boot off the SuSE CD, instead it went back to that screen with "GRUB" on it. I realize GRUB is the bootloader, but I have no idea of how to use it and as I've said I can't type anything at the screen. I also tried Kubuntu and a Knoppix Live CD, same thing. I even tried booting off a floppy, same thing. However, booting off the Ubuntu CD still works, just nothing else.

I discovered just today that by going through the expert install there's an option to verify CD-ROM integtrity. I did this and the test failed, so I guess that's why the installation failed. I don't know why, I've installed other Linux distros burned with the same CD burner fine in the past.

How can I fix this? I was going to try installing Ubuntu from Knoppix in case Ubuntu just didn't like my CD-ROM drive for some reason, but I can't even do that since it won't boot from the Knoppix CD.

Any help is appreciated, thanks in advance.

---

### Post by BoneKracker on 2006-03-12
You've done a good job isolating the fault so far to the CD being bad.  Now that you've burned a bad one twice, my next step would be to confirm that I had a good copy of the ISO file to begin with.

Did you verify the health of the ISO image by doing an MD5 checksum on it after you downloaded it?  If not, do so.  If you need instructions how to do this just ask and somebody will help.

---

### Post by o_fortuna on 2006-03-12
It also may have something to do with the CD drive itself; I know some people have had this problem.

Also, you should (if you can) download the ISO with Bittorrent. Bittorrent automatically checks MD5 sums to make sure the ISO is correct. (Look for the .torrent files on the CD download page).

---

### Post by Jonas54 on 2006-03-12
I still have the ISO and just did an MD5 checksum check on it and it was fine, thanks though.

---

### Post by docmarkc on 2006-04-24
I was having an almost identical issue when I tried running both the live CD as well as the installer on a junker HP home desktop machine.  I was installing on a whim so I haphazzardly went through errors, but I remember one of the primary errors was that the CDROM was "Confused"..  Go figure.
Anyway, eventualy I moved the CDROM from being a slave on the primary IDE controller, to the master on the secondary controller.  Everything installed without a hitch after that.
Not that I am even attempting to give any advise...  Just relaying what happened for me.  I was using the "Poke at it with a stick until it works" method of troubleshooting.

---

### Post by MystaMax on 2006-05-07
I just had similar problems when installing Ubuntu via a ShipIT CD on a Dell PowerEdge 2850. I replied to [this thread]("http://www.ubuntuforums.org/showthread.php?p=990274#post990274") with [this post]("http://www.ubuntuforums.org/showpost.php?p=993675&postcount=7"). I hope that helps anyone in the same predicament as I was in!  Good day! ;)

---

