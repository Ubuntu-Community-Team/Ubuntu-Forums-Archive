---
title: "Cant mount UDF Vista made DVD"
date: 2011-05-20
forum: General Help
---

### Post by lordbux on 2011-05-20
Dear friends

I had burned a  DVD in Windows Vista from a friends home and then tried to
brows it on my Ubuntu 10.4 System.

But as soon as i pop in the DVD I get an error alert saying:


> Unable to mount UDF Volume
Error mounting: mount: block device /dev/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

So i later tried to mount from command line
and got the error.
```

sudo mount -t udf /dev/cdrom1 /media/cd
mount: block device /dev/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

Please help, this is an emergency situation. the files are of great importance..

Thanks in advance

---

### Post by gsmanners on 2011-05-20
I don't think UDF is the problem. This seems to me more like you have a more subtle problem (a bad burn is most likely). Do other DVDs mount on your computer? Do discs you burn on your own drive mount on your friend's system?

---

### Post by lordbux on 2011-05-22
Bump. . . 
It is only with UDF i have this problem.

---

### Post by philinux on 2011-05-22
From a search it looks complicated. Unless anyone else can shed any light.

[http://www.linuxquestions.org/questions/slackware-14/how-can-i-mount-an-udf-picture-cd-dvd-663945/](http://www.linuxquestions.org/questions/slackware-14/how-can-i-mount-an-udf-picture-cd-dvd-663945/)

[http://ascending.wordpress.com/2008/06/14/howto-read-vista-burnt-udf-dvds-on-ubuntu-linux/](http://ascending.wordpress.com/2008/06/14/howto-read-vista-burnt-udf-dvds-on-ubuntu-linux/)

Although this looks promising.

[http://amazingrando.wordpress.com/2007/05/02/how-to-mount-udf-dvds-in-ubuntu/](http://amazingrando.wordpress.com/2007/05/02/how-to-mount-udf-dvds-in-ubuntu/)

[_My Search_]("http://www.google.com/search?client=ubuntu&channel=fs&q=Cant+mount+UDF+Vista+made+DVD&ie=utf-8&oe=utf-8&gl=uk")

---

### Post by mc4man on 2011-05-22
Your issue _may be due_ to the default method of creating data discs on vista
By default vista would use the 'Live System', UDF 2.01
At this point UDF 2.01 is not an issue on linux, UDF 2.5 may be, not sure, but likely you used 2.01

The other method vista used was 'Mastered', you would have needed to specify it.
The diff is -  with the live system, files, as they were added, were burned immediately, mastered meant you had to add all your files, then burn as DAO

If you used the default live system then vista would not prompt you to close the session - with the session not closed the disk will not be readable or even recognised in linux and many other OS's

To give you an example - screen 1 is a data dvd, live session, UDF 2.01, session left open.
In ubuntu the media does not exist, though I can read it with ImgBurn in wine. ( even ImgBurn can't close the session, though I could probably rip it to iso and extract the files
Look closely at right side box - shows session damaged, track info is incomplete

Screen 2 shows same disc in ubuntu, now found, (auto-mounted) and readable after going back into vista and closing the session, note ImgBurn now shows 'sessions 2' and further disc info inc. address of next writeable sector.

So if this is the case you'll need to return the disc to vista and close the session (insert disc > open My computer > r. click on the drive > close > session (wait until vista prompts you that disk is 'now readable in ..', may take longer than you think

---

