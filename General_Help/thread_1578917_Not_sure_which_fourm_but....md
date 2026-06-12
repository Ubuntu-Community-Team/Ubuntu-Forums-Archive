---
title: "Not sure which fourm but..."
date: 2010-09-21
forum: General Help
---

### Post by Pazaz on 2010-09-21
HELP! I downloaded the iso thning, And I don't know how to use it, Any ideas? I don't want to use VMware due to the current connection, You know, Traveling.... Bad Connection, Any other things to do is what I'm asking. And I don't want to have to download the windows installer....

---

### Post by ad_267 on 2010-09-21
Ahh what?

Is this what you're after? [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by Pazaz on 2010-09-21
Actually, I don't have a cd/dvd drive, And I don't have anything to use as it, So I just want to know how to use this.

---

### Post by Rubi1200 on 2010-09-21
Are you able to install via a USB port? Is this a netbook we are talking about? Please post the specifications.

---

### Post by Pazaz on 2010-09-21
Might be tomorrow, I'm going to Fries electronics in california tomorrow, Might pick up a Few Gig USB...

---

### Post by Ordes on 2010-09-21
if u just need to get to the content of the iso you could use:
> gmount iso
> acetone iso

to mount them;
or u use the terminal instead:

1) u need to create a folder in /media ( this will be where u mount the iso ); e.g
$sudo mkdir /media/myiso  (myiso can be anything u like)

2) mount iso file; if you are in the ISO directory:
$sudo mount myisofile.iso /media/myiso -t iso9660 -o loop

---

### Post by Pazaz on 2010-09-21
Thank you.  I will try that.

---

### Post by Pazaz on 2010-09-21
Thanks, I remembered about daemon tools when I used to use it, So I did that, And It works perfectly! I've gotta say, Full install Should be the thing for me. :D:KS

---

