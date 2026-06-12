---
title: "Reading an unbootable Ubuntu drive in a USB external enclosure"
date: 2011-10-24
forum: General Help
---

### Post by irongiant14 on 2011-10-24
Hi people,

I would appreciate some sage advice, since I'm relatively new to Ubuntu and am in a tough spot.

I had a Natty install, my first Linux box, on a 2005 Gateway GT5040, but the  [upgrade to 11.10 was a disaster]("http://ubuntuforums.org/showthread.php?t=1862522").  If you know of a way to get the drive to boot, I would love to hear it but my research suggests this may not be possible. At this point, I would like to retrieve files created on the disk before  reformatting/reinstalling. 

The broken install is on a single partition and the files I want are in  the home directory, so I can't simply reinstall over the last OS, from  what i understand. 

I removed the drive from the case, put it in an external enclosure, and  booted an XP PC with my Natty install CD. I can now read the disk but  when I go to the user folder it says I don't have permission to read it.  I know the password but don't see anyplace to enter it. Is this a dead  end or is there some way to unlock the data? 

Or should I look at Virtual Box? My reading leads me to believe that if I  install virtual box on the XP PC I may be able to share files with  another Linux computer through a network but I don't know if it will  work through a USB drive. Is this a lot of work to get set up?

I've also got a Macbook with OS X 10.4.11 tiger, if that would help.

---

### Post by spiky001 on 2011-10-24
Have you tried booting from the cd as in live cd, You can run from the cd then mount your external drive, Was the home partition encyrpted

---

### Post by satanselbow on 2011-10-24
> **irongiant14 said:**
> Hi people,

I would appreciate some sage advice, since I'm relatively new to Ubuntu and am in a tough spot.

I had a Natty install, my first Linux box, on a 2005 Gateway GT5040, but the  [upgrade to 11.10 was a disaster]("http://ubuntuforums.org/showthread.php?t=1862522").  If you know of a way to get the drive to boot, I would love to hear it but my research suggests this may not be possible. At this point, I would like to retrieve files created on the disk before  reformatting/reinstalling. 

The broken install is on a single partition and the files I want are in  the home directory, so I can't simply reinstall over the last OS, from  what i understand. 

I removed the drive from the case, put it in an external enclosure, and  booted an XP PC with my Natty install CD. I can now read the disk but  when I go to the user folder it says I don't have permission to read it.  I know the password but don't see anyplace to enter it. Is this a dead  end or is there some way to unlock the data? 

Or should I look at Virtual Box? My reading leads me to believe that if I  install virtual box on the XP PC I may be able to share files with  another Linux computer through a network but I don't know if it will  work through a USB drive. Is this a lot of work to get set up?

I've also got a Macbook with OS X 10.4.11 tiger, if that would help.


1) Boot from the live CD
2) plug in usb drive (close the nautilus window it opens up)

If you then launch a terminal and start nautilus with elevated privaleges ie:

```
sudo nautilus
```

You should not encounter the permissions problem ;)

You could also then take the opportunity to back those files up onto your XP machine's hdd so you can format the usb drive with a clear conscience :D

---

### Post by ajgreeny on 2011-10-24
> 1) Boot from the live CD
2) plug in usb drive (close the nautilus window it opens up)

If you then launch a terminal and start nautilus with elevated privileges ie:

     Code:
     sudo nautilus 
You should not encounter the permissions problem.

You could also then take the opportunity to back those files up onto  your XP machine's hdd so you can format the usb drive with a clear  conscience.Just to say that you should always use ```
gksu nautilus
``` or ```
gksudo nautilus
``` for gui applications like nautilus not just sudo.

See **Rootsudo** in my signature for the details and reasons behind this.

---

### Post by irongiant14 on 2011-10-24
> **satanselbow said:**
> 1) Boot from the live CD
2) plug in usb drive (close the nautilus window it opens up)

If you then launch a terminal and start nautilus with elevated privaleges ie:

```
sudo nautilus
```You should not encounter the permissions problem ;)

You could also then take the opportunity to back those files up onto your XP machine's hdd so you can format the usb drive with a clear conscience :D

Thanks, Spikey, SatansElbow and AJGreeny. I appreciate your efforts  a lot. :p

I've just booted the XP box with the Live CD and and followed your instructions. I'm still getting only the Access-Your-Private-Data.desktop and README.txt files in Nautilus' Home/Kim directory, though. I've tried both 'gksu nautilus' and 'gksudo nautilus', too. Am I missing something? 

Would this be easier if, instead of having the drive in the USB enclosure, I put it back in the case and booted from the Live CD in that situation?

Not to complicate the thread, but as I waited for your kind posts, I continued searching the boards for answers and came across this link to what they call an automated recovery app: [http://blog.dustinkirkland.com/2011/04/introducing-ecryptfs-recover-private.html](http://blog.dustinkirkland.com/2011/04/introducing-ecryptfs-recover-private.html)

I tried following the steps on that page and in the video with no success. **sudo ecryptfs-recover-private **was not found when I entered it into the Terminal, even though I've got the Natty Narwhal 11.04 Live CD  indicated in the instructions. I think maybe I'm not properly mounting the volume, but it shows up just fine when I plug it into the USB port and I see it in Nautilus. Is this method worth pursuing? Your suggestions sound a lot easier.;)

In the event that I get an opportunity to enter my password, I have learned that the Mount Password is separate from the User password. Is this mount password the string that Ubuntu install urgently asked me to record during set up? I have a note from the original install with a 30 digit string that I labeled "Home directory". Or is it something I create in this recovery session?

---

### Post by irongiant14 on 2011-10-25
I figured I'd try the above method, with the drive in the case, instead of the external enclosure. The result is the same in the nautilus GUI but the Terminal gave me this:

```
ubuntu@ubuntu:~$ gksu nautilus
Initializing nautilus-gdu extension

** (nautilus:4515): WARNING **: Failed to get the current CK session: GDBus.Error:org.freedesktop.ConsoleKit.Manager.GeneralError: Unable to lookup session information for process '4515'

(nautilus:4515): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:4515): GLib-GIO-WARNING **: Missing callback called fullpath = /root/.config/user-dirs.dirs

Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

```Also many lines of:

```
(nautilus:4515): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
```And two of:
```

** (nautilus:4515): WARNING **: bookmark uri is file:///home, but expected file:///
```Does this give me anything to work with?

---

### Post by satanselbow on 2011-10-25
> **irongiant14 said:**
> I'm still getting only the Access-Your-Private-Data.desktop and README.txt files in Nautilus' Home/Kim directory, though.

You used the EncryptedPrivateDirectory on your last install? As per:

[https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory)

Can't say I have any experience of this although i'm sure someone around here will have ;)

edit: there appears to be some good info here: [http://www.linuxquestions.org/questions/ubuntu-63/fresh-install-with-encrypted-home-partition-765465/](http://www.linuxquestions.org/questions/ubuntu-63/fresh-install-with-encrypted-home-partition-765465/) that refers back to a post on this forum too.



As to "gksudo" **ajgreeny** is quite correct... let's call it a typo on my part :rolleyes:

---

### Post by cryptotheslow on 2011-10-25
Try having a read through Bodhi.Zazen's (you'll find them in red on this forum) walkthrough of how to mount that encrypted home directory from your LiveCD environment at the link below.

[http://bodhizazen.net/Tutorials/Ecryptfs#Live](http://bodhizazen.net/Tutorials/Ecryptfs#Live)

It worked fine for me - but I was just messing around seeing how stuff worked rather than having to do it  in a real life or death scenario :)

---

### Post by irongiant14 on 2011-10-26
> **cryptotheslow said:**
> Try having a read through Bodhi.Zazen's (you'll find them in red on this forum) walkthrough of how to mount that encrypted home directory from your LiveCD environment at the link below.

[http://bodhizazen.net/Tutorials/Ecryptfs#Live](http://bodhizazen.net/Tutorials/Ecryptfs#Live)



I am very happy to report that I've got all my data off the unbootable drive! The above Bodhi Method worked for me, after a lot of failures. One really must focus. Special thanks to Cryptotheslow for link! ):P

And to AJGreeny because without ```
'gksu nautilus'
``` I wouldn't have been able to copy the files. The Bodhi method eventually let me view my home folder by entering **/mnt/home/*my-username-here* **but I lacked permission to copy the files to an external drive! Calling **'gksu nautilus'** let me open the extrenal drive and copy the locked files into it.

I'm really happy to have my and my girl's files back. Many thanks for your time and attention!!

---

