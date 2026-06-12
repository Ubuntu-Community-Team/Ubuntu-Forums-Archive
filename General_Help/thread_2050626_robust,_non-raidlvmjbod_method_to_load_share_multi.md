---
title: "robust, non-raid/lvm/jbod method to load share multiple hard drives?"
date: 2012-08-31
forum: General Help
---

### Post by pharcycle on 2012-08-31
Afternoon all,

I'm wondering if anyone could point me towards a method to automatically load share files across multiple hard drives? I'm aware I could set up a RAID, JBOD or LVM to accomplish this but unless I went for a mirrored RAID, a single drive failure could mean the end of all my data. I know its not the absolute end of my files if that happens but its not a simple task to recover them.

I'd prefer to be able to keep the file systems on single drives to avoid these issues but not have the hassle of managing storage locations when one drive gets full. I guess I could write a script to move files from a temporary folder and then write to a particular drive based on the free space available and call it at 3am or so but it would be nice if there was a method for linux to do this in real time.

These drives contain media files so performance isn't paramount by any means and they're certainly not critical so some vulnerability to data loss doesn't bother me. When playing back the files, XBMC can merge multiple locations into a single playlist so this would take care of reading from multiple places.

I'm currently using 2TB drives so getting a larger one isn't really the solution I'm after and the largest one you can realistically get at the moment is only 3TB anyway. I'm currently running a LVM with 2x 2TB drives, I think its a little more safe than a RAID or JBOD but the more I read about them, the less I believe this is true!

Any thoughts or existing solutions anyone cares to share!? Apologies if this is in the wrong section, but its seemed like a general question to me!

Thanks.
David

---

