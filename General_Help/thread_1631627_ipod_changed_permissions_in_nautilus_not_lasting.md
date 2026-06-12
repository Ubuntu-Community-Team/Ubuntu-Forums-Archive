---
title: "ipod changed permissions in nautilus not lasting"
date: 2010-11-26
forum: General Help
---

### Post by maramacs on 2010-11-26
Hi,  
I'm using rhythmbox and a classic ipod.  A couple of times I have managed to write podcasts to my ipod. I'm not sure how I did it but it doesn't last. I have tried lots of random things from forum posts.  When I try to change permissions in nautilus they change back straight away. I have my name as owner and group. I have the Lynx Ubuntu OP. Does someone know what did work and why it doesn't last?  It's really confusing me, thanks

---

### Post by dcstar on 2010-11-26
> **maramacs said:**
> Hi,  
I'm using rhythmbox and a classic ipod.  A couple of times I have managed to write podcasts to my ipod. I'm not sure how I did it but it doesn't last. I have tried lots of random things from forum posts.  When I try to change permissions in nautilus they change back straight away. I have my name as owner and group. I have the Lynx Ubuntu OP. Does someone know what did work and why it doesn't last?  It's really confusing me, thanks

You cannot change permissions on FAT filesystems.

---

### Post by maramacs on 2010-11-26
in properties, basic  it says the filesystem type is msdos.  Should it be this?

---

### Post by maramacs on 2010-11-27
Could it be this?
from PokerFacePenguin. 2009:

"I am not sure if this is your problem but this is what I did to fix connection problems with my nano 4GB blue IPOD....

I fired up a windows virtual machine and connected the usb port to my ipod.

Ejected it nicely.  Closed down the virtual pc.  Voila!  Magically my  ipod icon showed up on my desktop and my apps could connect to it.   Ubuntu reported that the IPOD was corrupted and asked me if I would like  to reinitialize it.  I said yes and then named the IPOD.  Now it works.

Was banging my head against the wall for a while thinking it was Ubuntu  that was the problem when really in all likelihood I removed the IPOD  during an operation and corrupted it.

Give it a try.  It can't hurt."

Any ideas as to what to check or do?

Thanks

---

### Post by maramacs on 2010-11-27
Hi,  I'm not getting many replies.  I just want to explain - I'm fairly inexperienced and  should be in beginners. This is my first time on and I didn't realize the forum structure.   I'm using an ipod even if they are bad apple because they are metal and indestructible (on the farm) and I've been through two other pricey mP3 players.  And it has worked before!

I don't understand about the FAT thing, yes mine seems to be (msdos), but it hasn't come up as a problem on other forums.  
In nautilus/ipod/permissions - owner is my name, folder access is create and delete file, file access changes back to ----; group is my name, folder access in none, file access is --- and both change back if I try to change them, other is none and --- , and they change back.

With gtkpod iPod manager i get - 
warning the following has occurred:
iTunesDB'/media/IPOD/iPod_Control/iTunes/iTunesDB' does not match checksum in extended information file '/media.IPOD.iPod_Control/iTunes/iTunesDB.ext'
gtkpod will try to match the information using SHA1 checksums. This may take a long time.

In gPodder I get Cannot open device please check settings in Preferences dialog. Preferneces say ipod is mounted to /media/ipod

I'm wondering if I unmounted it badly at some stage.  I easily could of.  

Can anyone give me any advice, more things to check, my work can be tedious and podcasts would entertain me all day!

thanks heaps

---

### Post by maramacs on 2010-11-27
It worked! I still have a question.
I'm wondering if someone can tell me why and which bit was the part that let it work.  
I opened rhythmbox first. connected ipod and opened with rhythmbox. Extended the ipod files. Opened downlaoded podcasts dragged from there to ipod heading file. Ejected iPod in rhythmbox. And there it was!  Had another go and dragged a few over.  The transferring bar zipped faster than it took to sync since when I ejected it said it was still working.  At this point the ipod symbol in rhythmbox disappeared but on ipod screen said it was still connected so I waited a bit incase something was still happening and then ejected using icon on desktop.  In past I haven't necessarily had rhythmbox open first, and I usually eject using desktop icon.  
I'd love to know why it worked, and what is the real deal with permissions and filetype FAT if anyone knows.  
I hope it continues to work! For some reason having this technology working and my contentment with life is closely connected.

---

### Post by maramacs on 2010-12-09
Also, rhythmbox doesn't turn on the first time.  Need to open it twice. Hope this helps someone because it took me months to get to this place with an ipod.

---

### Post by maramacs on 2010-12-09
Also if track tranfer gets stuck, the only way to clear it is Music>Quit.  If you clear any other way, they will still be there when you open again.

---

### Post by maramacs on 2011-01-21
Hi, I just wanted to add to this and then I'll close the thread I think.  I think the steps are very important. Adding to the (i think) 4th last listing where I described every step, it is very important to double click on podcast in ipod directory before dragging podcasts to the main heading podcast. I didn't use it for a while since my computer broke and it took me ages to work this out again.  Also, I'm not sure if I have explained that I made sure all gk....packages were added as recommended in other posts and I tried changing permissions in nautilus though the read and write one wouldn't stick. Anyway, I like rythmbox now, it's working for me!   :D

---

### Post by maramacs on 2011-01-21
crap it! why is it so inconsistent!  It works then doesn't. Anyone?????????

---

### Post by maramacs on 2011-02-02
Hi, is it that no one knows why? I feel like I'm talking to myself!

---

