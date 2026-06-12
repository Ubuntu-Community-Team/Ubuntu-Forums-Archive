---
title: "Problem on reinstalling 12.04 :confused:"
date: 2012-06-10
forum: General Help
---

### Post by shurkes on 2012-06-10
Hello,
Few days ago, my Ubuntu 12.04 (dual boot xp) ceased to connect to the internet, it seemed that it not recognize the network adopter (or whatever).
booting on windows and live cd gave me internet connection.
I decided to reinstall Ubuntu, and deleted (not formated) the linux partition.
when i tried to install it from the live CD, after selecting language, timezone, it started to download files and few minutes later a message poped up telling me that tha instaltion cannot be proceeded because there is a problem in the CD that was damaged or was written in high speed.
i made a new CD with the lowest velocity and got the same error.
i can boot to those CDs and can work on them but cannot install.
Maybe ive done some mistakes but hopefully some solucion can be found in order not to format the HD (i did back up so in the worst case, it can be formated)
If any one can suggest something, i will be greatfull.
Thanks

---

### Post by Quarkrad on 2012-06-10
I'm a newbie so not qualified to commet/help as such but I have re-installed Ubuntu in a dual booting scenario many times.  In my experience it is better to format the partition (to ext4) during the install process (you only deleted) and to use a USB stick rather than the CD.  If something goes wrong during the CD build it is quite time consuming to burn another CD - install from USB.  And always Format.

---

### Post by wilee-nilee on 2012-06-10
check the md5sum of the disc.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

I would also try a usb stick as well as suggested could be dirty cd reader or who knows what really if the discs are good and yet you get a failure.

---

### Post by shurkes on 2012-06-10
I am unable to boot from USB stick on that machine.
Why formatting the partition should make it happens?

---

### Post by wilee-nilee on 2012-06-10
> **shurkes said:**
> I am unable to boot from USB stick on that machine.
Why formatting the partition should make it happens?

Give us a screen shot of gparted on that machine, the live cd has gparted.

Did you check the md5sum of the cd?

---

### Post by shurkes on 2012-06-10
how can i check md5sum?
attached printscreen

---

### Post by wilee-nilee on 2012-06-10
> **shurkes said:**
> how can i check md5sum?
attached printscreen  

Use this wiki for help on the md5sum.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by shurkes on 2012-06-10
i will follow that link but is it possible that the CD is defected while it can be used as live CD and it happend twice on two differents CDs and the burning was made by two differents PCs?

---

### Post by black veils on 2012-06-10
> **shurkes said:**
> i will follow that link but is it possible that the CD is defected while it can be used as live CD and it happend twice on two differents CDs and the burning was made by two differents PCs?


yes, if it is a corrupted download file. you need to check the md5sum of every ISO download, to do this....

download and install the relevant version, for whichever computer you are making these discs on: 

win 64 bit
[http://sourceforge.net/projects/akis-sideris.u/files/hc_win_64.zip/download](http://sourceforge.net/projects/akis-sideris.u/files/hc_win_64.zip/download)

win 32 bit
[http://sourceforge.net/projects/akis-sideris.u/files/hc_win_32.zip/download](http://sourceforge.net/projects/akis-sideris.u/files/hc_win_32.zip/download)

(you need to Extract before install)

    1.   Right-click the ISO file.

    2.  Click **Send To**, then **winMD5Sum**.

    3.  Wait for winMD5Sum to load and finish the checksum.

    4.  Copy the operating system md5sum of your relevant version from here [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes), into the bottom text box.

   [COLOR=YellowGreen]**Demo here: **[/COLOR] [https://help.ubuntu.com/community/HowToMD5SUM?action=AttachFile&do=get&target=winMD5Sum.png](https://help.ubuntu.com/community/HowToMD5SUM?action=AttachFile&do=get&target=winMD5Sum.png) 

    5.  Click **Compare**   

    6.  A message box will say "MD5 Check Sums are the same" if the hashes are equal. 


then burn your disc at the slowest speed.

---

