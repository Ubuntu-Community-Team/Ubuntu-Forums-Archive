---
title: "Raid 1 array not showing up"
date: 2010-08-28
forum: General Help
---

### Post by Floss on 2010-08-28
I am using Ubuntu 10.04 x64.  I am not trying to install Ubuntu on a RAID 1 drive like all of the guides are for.  I have a RAID 1 array that I am using for data storage.  In windows it shows as a single array just fine.  In linux it shows as 2 separate drives.  I don't care how they show up to be honest I just have to data written to one drive written to the other automatically as well so my RAID isn't screwed up.

Looking through different articles and forums I find a lot of stuff saying that it should show up under /dev/mapper/dxxx or something under /dev/mapper.  All that shows up there for me is a device called control which doesn't seem to do something.

Also dmraid is already installed I just can't figure out what I am supposed to do with it :(

---

### Post by ronparent on 2010-08-28
Try in a terminal the command 'dmraid -ay' and see if anything shows up.

---

