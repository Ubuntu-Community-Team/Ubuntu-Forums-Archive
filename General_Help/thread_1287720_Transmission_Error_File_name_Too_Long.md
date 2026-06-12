---
title: "Transmission Error: File name Too Long"
date: 2009-10-10
forum: General Help
---

### Post by RJG on 2009-10-10
I'm trying to download a file using Transmission, but it's telling there's an error because the file name is too long.

What's the cause of this, and is there any way around it?

---

### Post by SuperSonic4 on 2009-10-10
The cause is obvious.

You could shorten the filename. There is usually a save as or save torrent in <location>

---

### Post by RJG on 2009-10-10
It's not the torrent file that's too long, it's the file being downloaded via the torrent file.

Is there any way to download the file but save it locally under a different name using a bittorrent client?

---

### Post by marcgenou on 2010-04-11
same problem here using torrent or copying an specific file from a xp 32 bits partition

PS: using lucid beta 2

---

### Post by JamezQ on 2010-04-11
I have the same problem, using transmission a file in the torrent is too long, and it stops the whole download process! For one this is a bug, it should only stop downloading that file and continue later. Anyway I was able to manually make it not download that file so it could download the rest first. 

But I do not see anyway to rename the the file that is too long so no error comes up. Help would be helpful.


Now even though I told the program to not download the file it still gives me the error.

---

### Post by JamezQ on 2010-04-12
This really doesn't seen like it should be that hard to fix?


Anyone know if another program does not do this? And if I could continue a torrent?

---

### Post by JamezQ on 2010-04-12
Alright, can someone point me to the right place to investigate this myself?

If you going to say google, give me search terms, because I have already tried to no avail. I always google things before asking.

---

### Post by WinterRain on 2010-04-12
> **JamezQ said:**
> Alright, can someone point me to the right place to investigate this myself?

If you going to say google, give me search terms, because I have already tried to no avail. I always google things before asking.

Being someone who has used torrents since the beginning, I would say try a different torrent client. If no other client works, then someone is pulling your chain, to put it into layman's terms.

You can continue your download using a different client, as you may already know. If not, ask.

---

### Post by JamezQ on 2010-04-13
I am asking, I don't know how.

---

### Post by WinterRain on 2010-04-15
Download another client such as deluge, and right click your .torrent file and choose open with deluge. But make sure to change the download folder in deluge to the same place as transmission. The download should continue on.

---

### Post by Charles Kerr on 2010-04-20
Transmission doesn't have any code in it that limits filename length.  Also, the phrase "Filename too long" is coming from Ubuntu, not Transmission... so I don't think switching BitTorrent clients will fix anything.

My first guess is that you're saving a long filename to a disk with an older filesystem -- I don't think I've ever seen this message in the real world on ext3/ext4.  Are you perhaps saving the torrent to a flash drive or external HD that's formatted with fat32?  Could you save it to a different disk instead?

---

### Post by nitstorm on 2010-04-20
Try using rtorrent, one of the best torrent downloaders ever. Super-light and picks up where another left off well. Once I started using rtorrent i quit everything else :) lol

here's a pretty good how-to for rtorrent:
[http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/](http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/)

hope this helps somewhat . Cheers!

---

### Post by Ryuho on 2010-08-31
> **nitstorm said:**
> Try using rtorrent, one of the best torrent downloaders ever. Super-light and picks up where another left off well. Once I started using rtorrent i quit everything else :) lol

here's a pretty good how-to for rtorrent:
[http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/](http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/)

hope this helps somewhat . Cheers!

Funny thing, I found this post because I'm getting the same error with rtorrent. 


```
Hashing: Storage error: [Hash checker was unable to map chunk: File name too long]
```

Like Charles Kerr said, this error is coming from Ubuntu. However my rtorrent is running on ext3, standard install that formatted the drive. The drive I'm using is normal SATA connected 3.5 HDD.

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 10.04.1 LTS
Release:        10.04
Codename:       lucid

One thing that does come to mind is that I'm downloading non-english (UTF-8, SHIFT_JIS, or ISO-2022-JP) file names, that could be it, maybe rtorrent doesn't support foreign languages.

---

### Post by tripzilch on 2011-03-09
Yeah. I'm getting the same error in Transmission. For anyone that wants to doublecheck, it's happening with this torrent of public domain homebrewing PDFs (all public domain, so it's legal, so it's not a problem to post the link for other people to check and perhaps help out here, right?) [http://www.homebrewkorea.com/forums/viewtopic.php?f=2&t=769&p=5815](http://www.homebrewkorea.com/forums/viewtopic.php?f=2&t=769&p=5815)

I agree that at least ONE part of the behaviour is a bug in Transmission. Even if the "File name too long" error comes from the OS, Transmission should just skip that file and continue with the rest of the torrent. Currently it just pauses the entire torrent. Which makes it kind of hard to download the other files, because this forces me to disable downloading that one file, start the torrent again, and wait until it errors on the next file ... then repeat. Very tedious. And the torrent properties files tab list is unfortunately in a proportional (not monospaced) font, so it's very difficult to just eyeball from that list which filenames would be too long and which aren't.

That said, my filesystem is ext4. Somebody in the thread said this one shoudln't have any (significant) filename length limit? Is that correct? Then why do I get this error?

Another thing that is *very* strange, is that as I'm disabling files considered having a too long name, and restarting the torrent and such, I'm seeing in the file list that some of these "too long" files are already downloaded for as much as 65% ! How can that be? If the filename is too long, how can it be downloading these things? What's it complaining about?

---

### Post by andrew.46 on 2011-03-20
> **tripzilch said:**
> Yeah. I'm getting the same error in Transmission. For anyone that wants to doublecheck, it's happening with this torrent of public domain homebrewing PDFs (all public domain, so it's legal, so it's not a problem to post the link for other people to check and perhaps help out here, right?) [http://www.homebrewkorea.com/forums/viewtopic.php?f=2&t=769&p=5815](http://www.homebrewkorea.com/forums/viewtopic.php?f=2&t=769&p=5815)

I have just checked the torrent with Transmission and there seems to be no problem on my system. Admittedly I am using the latest Transmission, so perhaps there has been a bug fixed...

Andrew

---

### Post by cherep on 2011-05-27
I had the same problem with ext4. However, it works when I try to save the file to NTFS. 

Transmission was used.

---

### Post by boxie on 2011-06-20
having the same problem with transmission and ext4.

when i go into the folder where the file is downloading and make a file with a long name, i get an error saying the file name is too long.

example name 'ffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffff'

that isn't so many characters, is ext4 so limited that i can't make my file names this long? could this be a limitation of ubuntu and not ext4?

---

### Post by asistjk on 2011-08-07
> **cherep said:**
> I had the same problem with ext4. However, it works when I try to save the file to NTFS. 

Transmission was used.
Thank you Cherep! It works for me too!! :P

---

### Post by patryk77 on 2012-01-07
> **tripzilch said:**
> Yeah. I'm getting the same error in Transmission. For anyone that wants to doublecheck, it's happening with this torrent of public domain homebrewing PDFs (all public domain, so it's legal, so it's not a problem to post the link for other people to check and perhaps help out here, right?) [http://www.homebrewkorea.com/forums/viewtopic.php?f=2&t=769&p=5815](http://www.homebrewkorea.com/forums/viewtopic.php?f=2&t=769&p=5815)

Same problem here on an ext4.

Try changing the download path:
Open terminal; type:
```
sudo mkdir /d
sudo chown MYUSERNAME /d
```

Then right click on the torrent in the download list, choose "select location" and move it to /d. It works for me with this particular file. Bug seems related to the entire path, not just the filename.

P.S.: Cheers! Awesome torrent is awesome!

---

### Post by HiImTye on 2012-03-06
I find it strange that NTFS worked but ext4 failed as ext4 has a limit of 256 bytes while NTFS is 255 characters

there are other file systems that have much larger file name limits, such as ReiserFS

---

### Post by pgotsis on 2012-04-14
I think I nailed the source of the error. This appears when you are saving in an encrypted folder. When you select to encrypt your home folder during the OS installation, you also encrypt the default download location for the various applications. I had the same issue, but when I moved the data to another folder, outside of the encrypted folder structure, the error disappeared.

---

### Post by Teerapong on 2012-06-07
Thanks pgotsis for your suggestion. 

However, here's to say that with Deluge you can change the destination file name.

---

### Post by Gabrielko114 on 2012-10-13
Long Path Tool helped me in this situation. [http://PathTooDeep.com](http://PathTooDeep.com)

---

### Post by wildmanne39 on 2012-10-13
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

