---
title: "Dual boot, can Thunderbird share the folders?"
date: 2011-06-25
forum: General Help
---

### Post by profozone on 2011-06-25
I have a dual boot computer; Windows 7 and Ultimate Edition 2.6.1 (Ubuntu 10.04).  Is it possible to load Thunderbird onto both Windows and Ubuntu and have the emails go to the same folder, so I can feel free to look at my email in either OS without having to remember which email I looked at in which OS, if I want to read them again?

Thank you in advance.

---

### Post by -kg- on 2011-06-25
> **profozone said:**
> I have a dual boot computer; Windows 7 and Ultimate Edition 2.6.1 (Ubuntu 10.04).  Is it possible to load Thunderbird onto both Windows and Ubuntu and have the emails go to the same folder, so I can feel free to look at my email in either OS without having to remember which email I looked at in which OS, if I want to read them again?

Yes, you should be able to share your email files between the two OSes.  Under Thunderbird, I always store my email files in a location other than the default.  Just make sure to copy your email files to a location on a FAT/NTFS partition so that both OSes can access them, then point the account(s...I have several) to that (or those) folder(s) on the FAT/NTFS partition.

They should mark themselves as read for Thunderbird in both OSes...I've transferred control of my email folders and accounts numerous times, between both OSes, and they show up as read or unread in every case.  So it should work switching back and forth between the OSes in a dual boot configuration, as well.

---

### Post by profozone on 2011-06-25
That friggin' rocks!

And so do you.

Thank you for your response.  I'll begin doing that right away.

---

### Post by HermanAB on 2011-06-25
Howdy,

The better way is to use an IMAP mail server and leave the mail on the server.  E.g. Gmail.

---

### Post by MartyBuntu on 2011-06-25
> **HermanAB said:**
> Howdy,

The better way is to use an IMAP mail server and leave the mail on the server.  E.g. Gmail.

That's what I use for access to emails on multiple machines and my phone.

---

### Post by profozone on 2011-06-25
Sorry, not finished yet.

I knew you could format a drive with FAT and I knew you could format a drive with NTFS, but I didn't know you could format one as FAT/NTFS.  I have just built this system and just loaded Windows onto a new SSD and Ubuntu onto a different new SSD.  I just plugged in my two older hardrives and they are both formatted as NTFS.  I still have a lot of shuffling to do between all of these drives before I feel comfortable wiping either of them.  I do have another drive laying around I could install, but I'm not sure I really need 5 physical drives in my system.  So. . . uh could comment on that?

Thanks again.

---

### Post by profozone on 2011-06-25
Regarding the IMAP thing.  Yes I agree.  I started with an email address with my local ISP.  When I grew disappointed with them, I didn't want to switch to a different service because I didn't want to lose my email.  So, I opened a Gmail account and started only giving out my new email, but I still get a lot of stuff on the old account and more importantly I have a lot of old emails I want to keep and access regardless of what OS I'm in.

Thanks for the comments though.

---

### Post by -kg- on 2011-06-25
> **profozone said:**
> Sorry, not finished yet.

I knew you could format a drive with FAT and I knew you could format a drive with NTFS, but I didn't know you could format one as FAT/NTFS.

LOL!  I meant format the partition as FAT ***_OR_*** NTFS.  No, you can't format one as both!

Sorry about the misunderstanding.  A real good guide on partitioning operations can be found at the link in my signature block. :)

---

### Post by -kg- on 2011-06-25
> **profozone said:**
> Regarding the IMAP thing.  Yes I agree.  I started with an email address with my local ISP.  When I grew disappointed with them, I didn't want to switch to a different service because I didn't want to lose my email.  So, I opened a Gmail account and started only giving out my new email, but I still get a lot of stuff on the old account and more importantly I have a lot of old emails I want to keep and access regardless of what OS I'm in.

Thanks for the comments though.

I certainly agree with you and am in your position.  I have emails and newsletters from back in the mid-'90s, some of them almost from the very beginning of the newsletters.  There's nothing like local storage to preserve them.  If I had to stick with them because I might lose my emails, I'd likely still be with my old dial-up account!

Instead, I store my emails locally (backed up on 4 different hard drives...how's ***that*** for multiple redundancy? :P ) and have used Netscape Mail or Thunderbird from the beginning. I still have all the emails I wanted to keep from way back...some of my friends are dead, but I still have their emails.

IMAP is fine for disposable communications, but there's nothing like a local client for the ones you want to archive.  The IMAP accounts are then "disposable" if they become too spam-ridden, and I have quite a few of those, as well.

---

### Post by oldfred on 2011-06-25
I am like -kg- and used to use FAT 4 years ago and converted to NTFS about 2 years ago. I also copy my profiles to my portable when we travel and back when we get home. I do the same for Firefox so I have the same bookmarks. It complains about a few add-ins when I reboot, but still works.

I find I have to start Thunderbird once to create the default profile and profile.ini. Then I edit profile.ini with the new location and never use the one created. 

Update to tb3
[http://ubuntuforums.org/showthread.php?t=1349889](http://ubuntuforums.org/showthread.php?t=1349889)
new 
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

---

### Post by profozone on 2011-06-26
Well, your reply got me searching and it seems that Ubuntu 10.04, which I'm using can only read to NTFS drives, which mine are, unless you have the ntfs-3g driver.  Is this true?  Will that give me problems?

---

### Post by Morbius1 on 2011-06-26
>  it seems that Ubuntu 10.04, which I'm using can only read to NTFS  drives, which mine are, unless you have the ntfs-3g driver.  Is this  true?  ntfs-3g is installed by default in Ubuntu and has been since I think Hardy so your information is incorrect. In fact there is a symbolic link from the "ntfs" fstype to "ntfs-3g" so you don't even have to specify ntfs-3g in a mount command or in fstab any more to make a mounted ntfs partition write enabled.  A given user may not be able to write to the partition but that depends on how it's mounted.

---

### Post by profozone on 2011-06-26
Awesome.  Thanks for the info Mobius.  Some of the threads I visited were old.  Probably explains it.

---

