---
title: "Binary SATA utility?"
date: 2010-11-11
forum: General Help
---

### Post by dan_hurst on 2010-11-11
Does anyone know of a utility or commands that will let me read / write binary data to a SATA hard disk drive without using a file system on that drive?

---

### Post by mcduck on 2010-11-11
the "dd" command will write anything you want to a drive, completely ignoring file systems and nonsense like that. :)

But better be careful with it, it doesn't care about little things like partition tables or MBR either, not to mention any existing data on the drive.. 

[http://en.wikipedia.org/wiki/Dd_%28Unix%29]("http://en.wikipedia.org/wiki/Dd_%28Unix%29")

---

### Post by dan_hurst on 2010-11-11
Thanks, i've just found the dd command and am having a play with it.

That wikipedia page is really useful, just what I'm looking for!

Is there a way to access/skip units of data smaller than 512 bytes (one block?) ?

Also do you know if there is a windows equivelent to this command (I don't have linux at work... yet :-)

---

### Post by mcduck on 2010-11-11
I don't think dd will allow you to skip anything, you'd have to do it before sending the data to dd. Dd doesn't really care at all about what the bits it's reading/writing are, or if it's just empty space.

As far as I know there is no Windows equivalent for dd. It might be possible (but probably not easy) to use dd with Cygwin on Windows.

edit: [http://www.packetninjas.net/blog/2008/12/31/commentary-on-using-dd-in-cygwin-forensics.html]("http://www.packetninjas.net/blog/2008/12/31/commentary-on-using-dd-in-cygwin-forensics.html")

---

### Post by dan_hurst on 2010-11-11
I think I've figured it out, apparently dd lets you skip blocks and it lets you set the block size.
 e.g. if I wanted bytes 7-9 of /dev/sda I could get it like this:

 sudo dd if=/dev/sda bs=1 count=3 skip=7


Thanks for the link, cygwin will probably be the way to go for now.

---

