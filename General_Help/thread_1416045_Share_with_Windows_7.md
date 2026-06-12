---
title: "Share with Windows 7"
date: 2010-02-25
forum: General Help
---

### Post by guitarplaya85 on 2010-02-25
I recently purchased a new laptop with Windows 7 and I am happy with the OS.  I was debating between replacing Windows with Ubuntu like I did on my older machine, but the graphics performance in Windows 7 in 1080p tipped the scale in its favor.  That said, I have about 1TB of media on my Ubuntu desktop stored on an ext4 partition that I would like to share over my network with the laptop, but Windows 7 cannot see the shares.  Would this be a file system issue or a Samba compatibility issue?  Also, is there a way I can convert the ext4 to ntfs without data loss if I decide to just put the media in an eSata enclosure?

---

### Post by CharlesA on 2010-02-25
Samba works fine for me with Win7 x64. How is it configured?

---

### Post by guitarplaya85 on 2010-02-25
I'm not sure.  I haven't messed with the smb.conf file, but I know the shares are connected with the workgroup "WORKGROUP" that I pointed my Win7 box to.  The Win7 box doesn't even see the Ubuntu box on the network.  I booted the Ubuntu box into XP to see if the issue was unique to Ubuntu, but the Win7 system could not see the XP system either.  I can see the Win7 system's shares from XP and Ubuntu, but not vice versa.  I have done through the recommended steps for [sharing between Win7 and other OS]("http://windows.microsoft.com/en-US/windows7/Networking-home-computers-running-different-versions-of-Windows"), but still no luck.  I have been accessing these same shares for years from my XBMC Xbox.  Any ideas?  Did yours work out of the box or did you have to do some tweaking?

---

### Post by guitarplaya85 on 2010-03-01
bump

---

