---
title: "To open up space, may I move /usr to another partition?"
date: 2009-10-09
forum: General Help
---

### Post by ikisham on 2009-10-09
Hello, I'm asking this for another person. She has a netbook with a 4GB SSD that is almost full and she can add another 32 GB memory card to expand the space.
So there's two thing I would like to know. If the system can be expanded with the SD card (like pluging it in at the boot time) and if it's possible to move the current /usr directory to the SD card to make room for more applications without having to reinstall.

Thanks.

---

### Post by ikisham on 2009-10-09
Well, I found out that it's not recommended to use the SD to expand the system since it's slow and would wear too much.
Then I thought that if she wants to stay with Jaunty NBR (instead of moving to a smaller distro), she could maybe install a live system to the SD. Is it possible (like a live USB)?
Better still would be to install the live system directly to the SSD, maybe. Is this possible?

---

### Post by jeremyswalker on 2009-10-09
What you suggest is absolutely possible. Search around, there are a TON of tutorials around on such things.

---

### Post by undecim on 2009-10-09
As far as I know, data isn't written to /usr/ very much (just when installing stuff), and its writes that will wear down flash media (sd cards, thumb drives, etc)

What you will need to do is boot to a livecd (or in this case, use the startup disk creator to make a live thumb drive, since this is a netbook)

Once its loaded, format the SD card (ext4 is probably best), and mount it.

Then, move the contents of /usr/ from the 4GB media to the SD card, then add a line to /etc/fstab (on the 4GB media):

```
/dev/sdx1 /usr ext4 defaults,noatime 0 0
```where /dev/sdx1 is the memory card device (look at the output of 'mount' to determine that)

EDIT: The caveat here is that you will require the SD on boot, or you will have problems.

---

### Post by ikisham on 2009-10-09
Thanks udexim, that's what I was looking for. I'll see how it goes.

---

### Post by sgosnell on 2009-10-09
I use an SD card all the time.  You can certainly move anything to it, and there are user guides on eeeuser.com forums and wiki.  I've installed many systems on SD card completely, partitioning as necessary.  I currently have Karmic beta on an SD card, and it works well enough, considering it's a beta and slow anyway.  On an EEE-PC, the SD card is about as fast as the installed SSD, and since it's far cheaper, worrying about wearing it out is a waste of time.  It will take years of constant writing to wear one out in any case, and in that time you'll want a newer, bigger card anyway.

---

### Post by ikisham on 2009-10-09
Reading again, couldn't she just move the /usr folder to the SD and edit the fstab?
I mean from within the system.
Then she should check mtab to see the proper mountpoint and add the line udexim posted, right? (as I can see she should first create a partition in the SD so /usr doesn't mix with other data)

*edit* - anyway, since I'm only givin' advice I think I know already what I should know.

Thanks everybody.

---

### Post by mike555 on 2009-10-09
Sounds like moving /home would be better , maybe that's what is wanted...

---

### Post by geckosenator on 2009-10-22
Hi,

I moved both /home and /usr to an SD card because of lack of space.  I found it is a little slower but not too bad at all.  The problem I have, is sometimes it does not boot correctly because /dev/sdb doesn't exist in time, and it tries to execute programs located in /usr.  At this point I just reboot.

Usually it boots just fine.  Is there a way to force it to have SD card support and mount /usr earlier?

Thanks

---

