---
title: "HFS+ is read-only, how do change in Terminal?"
date: 2010-03-31
forum: General Help
---

### Post by meathane on 2010-03-31
hi guys,

firstly i sorry to post something so basic, but ive looked everywhere for the answer but can't find out how to do it.

basically i have a 1TB USB HDD that is formatted HFS+ (i used to use it attached to a hacked AppleTV, it has loads of media on it).

appletv wasn't great, so now i have a lovely acer revo running XBMC Live, and it's blooming great. my problem is my USB drive mounts, but i think it's read-only, as i am struggling to sftp new files to it. so my question is:

how do i make the drive writeable?

i've read things about disabling journling, an fstab file, chown in terminal, but im really struggling.

in temrinal if i navigate to the /media folder and run ls -al, i get this: (note the usb drive is called AppleTV)

revo@XBMCLive:/media$ ls -al
total 16
drwxr-xr-x  4 root root 4096 2010-03-31 20:56 .
drwxr-xr-x 21 root root 4096 2010-03-25 14:58 ..
drwxrwxrwx  1   99   99   21 2010-03-30 20:57 AppleTV (it also has blue text on green background!)
lrwxrwxrwx  1 root root    6 2010-03-25 14:57 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2010-03-25 14:57 cdrom0
-rw-r--r--  1 root root   70 2010-03-31 20:56 .hal-mtab
-rw-------  1 root root    0 2010-03-31 20:56 .hal-mtab-lock


can anyone tell me how to make it read-write? i'm happy for it to have full write access by root, or all users or whatever. im sure its 1 line in terminal but it's driving me mad!

i promise i have searched, and again sorry if its a dupe or very basic

any help would be great

thanks

---

### Post by meathane on 2010-03-31
a little progress, i attached the drive to my mac, and ran

diskutil disableJournal /Volumes/AppleTV

and now i can sftp files to the drive, but only the root of the drive, and 1 folder deep! on the root i have 2 folders say, Movies, and TV Shows, and i can put new things in both of those, as well as the root. In the TV Shows folder, there are many other folders, (TV show names), that i cannot write to (either renaming or copying new file to).

AppleTv
_---Movies
_---TV Shows
___---Ricky Gervais Show  (<--- i cannot copy new episodes to this folder)


seems very strange, i didn't think it would behave like this

---

