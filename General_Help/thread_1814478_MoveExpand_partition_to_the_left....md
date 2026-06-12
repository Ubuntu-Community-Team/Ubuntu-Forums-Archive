---
title: "Move/Expand partition to the left..."
date: 2011-07-29
forum: General Help
---

### Post by [::AP::] on 2011-07-29
Greetings - 

Yes, this has been covered many times. I cannot seem to find a clear solution, however.

I need to expand /dev/sda6 into the unallocated space proceeding it (to the left).

GParted (*0.6.2-1ubuntu1*) does not allow me to Resize/Move. When I select /dev/sda6 the button becomes greyed out. 

The GParted on my Parted Magic disk (I don't know which version, sorry, but I can check) gives me an "Ubable to satisfy all constraints on the partition" error. I may be able to uploar a log and take a picture (with physical camera, no screenshot ability in Parted Magic, sorry.) 

[[IMG]http://img810.imageshack.us/img810/3397/screenshotiuu.png[/IMG]](http://imageshack.us/photo/my-images/810/screenshotiuu.png/)

Uploaded with [ImageShack.us](http://imageshack.us)
[http://img810.imageshack.us/img810/3397/screenshotiuu.png](http://img810.imageshack.us/img810/3397/screenshotiuu.png)

One solution is to delete partition to make one large partition, and then fill it back up with the previous data.

other than that, are there other methods (that do not require burining another Live CD) ? 

Any commands I need to run?

Apologies for the noobish-ness and the repeat of a question.

Thanks, 

[::AP::]

---

### Post by Theredbaron1834 on 2011-07-29
Expand sda3 first. Because sda6 is is inside sda3. As of right now, sda3's space is filled. You have to increase the free space inside sda3.

This is all because there can only be 4 partition's, inless you trick it like this.

---

### Post by [::AP::] on 2011-07-29
Thanks for the reply. 

I am unable to do that - I tried previously in PartedMagic and then in GParted, and then once again after the suggestion. 

In Parted Magic, I get an error.
In Gparted, the Resize/Move option is greyed out for both sda 3 and sda 6.

Thanks for the reply,

[::AP::]

---

### Post by oldfred on 2011-07-29
The little keys say its mounted.

You have to do it from a liveCD so nothing is mounted, but liveCDs oftern automatically mount swap to speed things up. So from liveCD click on swap and right click swap off. Then you should show no little keys and can expand extended partition left. 

If moving a partition left do not interrupt it, nor have power failure. Best to have good backups before starting.

---

### Post by Chiel92 on 2011-07-29
I'm not certain, but I think using a live CD or USB to run gparted will help, since sda3 and sda6 are active now.

---

### Post by Theredbaron1834 on 2011-07-29
> **oldfred said:**
> The little keys say its mounted.

I can't believe I missed that.

Also, since you are trying to expand your / directory, you can't do that from in the os. As th e OS is using the files at the time, you can't unmount it. So Either burn a live disk (I always have a buntu live disk for just such a think though you could use a gparted live disk as it is smaller) or use unetbootin/multisystem to boot a livedisk from usb, and run gparted from the live environment.

ANd then do what oldfred said.

---

