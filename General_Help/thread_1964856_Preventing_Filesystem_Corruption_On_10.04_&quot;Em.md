---
title: "Preventing Filesystem Corruption On 10.04 &quot;Embedded&quot; Application"
date: 2012-04-24
forum: General Help
---

### Post by Spaceman Spiff on 2012-04-24
Hello all,
  I am using 10.04 as the base OS in an "embedded" type application I am working on.  The computer it runs on is part of a larger system that is turned off when not in use.  When the system is turned off the computer's power is also removed.

  I am trying to determine a way to prevent my OS from being corrupted on these hard shutdowns.  I have googled around and determined that I need 10.04 to be read-only.  Nothing should be written to the hard drive anyways. Once this system runs, nothing should change... ever.

  I am having difficulty now though, I don't know how to implement this approach.  Should I boot ubuntu regularly then remount the entire partition as read only?  I keep reading that at least some parts of the file system need to be read/write.  Can I avoid that?  I would like to boot read-only, but people seem to state that this is not possible.  If anyone could give me some advice/search terms it would be greatly appreciated.

Thank you,
Constantin

---

### Post by strask on 2012-04-24
I don't know the details, but you might investigate the boot process used by the live installer CDs. Those are on read-only media, and somehow manage to boot into a fully functioning system that doesn't write anything to disk.

Now, technically speaking they run with a read/write filesystem, it's just that the filesystem doesn't have any persistent storage I guess.

---

### Post by Spaceman Spiff on 2012-04-24
Strask, I appreciate this response.  This is an interesting avenue to approach, I will do some googling.

---

