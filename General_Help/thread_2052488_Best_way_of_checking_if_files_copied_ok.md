---
title: "Best way of checking if files copied ok?"
date: 2012-09-03
forum: General Help
---

### Post by bob-linux-user on 2012-09-03
I am running Ubuntu 12.04. To backup my files I copy on to a partition on an external usb drive. (The partition is crypted using ecrypt first).

I have found that some large movie files have been corrupted when transferred over.

Up until now I have checked a backup has been done by selecting files in Nautilus and looking at the properties. The computer "says xxx number of files 33.2 gigabytes" or similar. If the count and number of gigabytes comes out the same for both the originals and the copies then I have assumed all is ok.

However I now find some movie files were cut short last time and this did not show on the gigabyte count as it only shows to one decimal place. 

What is the best way of doing a comparison between folders please? Is there a program which does an md5 on a folder as opposed to an individual file, or, some program which analyses the difference between 2 folders down to the last byte? I have tried installing meld but could not get it to work.

---

### Post by Lars Noodén on 2012-09-03
I would use [rsync](http://manpages.ubuntu.com/manpages/precise/en/man1/rsync.1.html) for that.  It copies and verifies.

```

rsync -avHP /source/ /destination/

```

See also: 
[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)

---

### Post by dcstar on 2012-09-03
> **bob-linux-user said:**
> I am running Ubuntu 12.04. To backup my files I copy on to a partition on an external usb drive. (The partition is crypted using ecrypt first).

I have found that some large movie files have been corrupted when transferred over.
........
What is the best way of doing a comparison between folders please? 
........

[http://serverfault.com/questions/303365/calculate-md5-checksum-of-a-directory](http://serverfault.com/questions/303365/calculate-md5-checksum-of-a-directory)

---

### Post by Lars Noodén on 2012-09-03
Also, what filesystem do you have on your target disk?

---

### Post by Dave_L on 2012-09-03
For comparing existing files or folders, you can use diff:

```
diff --brief --recursive --report-identical-files /folder1 /folder2
```

[http://manpages.ubuntu.com/manpages/lucid/en/man1/diff.1.html](http://manpages.ubuntu.com/manpages/lucid/en/man1/diff.1.html)

---

### Post by bob-linux-user on 2012-09-03
Thanks to all for the swift replies. I will have to do some experimenting.

@Lars...
The file sytem according to gparted is crypt-luks. I used Disk Utility as per

[http://www.liberiangeek.net/2012/04/encrypt-your-external-usb-drives-in-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/04/encrypt-your-external-usb-drives-in-ubuntu-12-04-precise-pangolin/)

to format the drive as ext4

---

### Post by bob-linux-user on 2012-09-04
I am looking at using dirdiff or Winmerge running in Wine. Both these seem to do what I want.

---

### Post by Lars Noodén on 2012-09-05
If you just want to know if the files differ or not, then [diff](http://manpages.ubuntu.com/manpages/precise/en/man1/diff.1.html) will do that for you.

```

diff -qr /*somedir*/ /*someotherdir*/

```

If you want to try to sync the files as well, then rsync is the way to go.

---

