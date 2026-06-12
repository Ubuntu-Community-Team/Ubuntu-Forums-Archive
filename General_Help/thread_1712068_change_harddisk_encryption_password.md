---
title: "change harddisk encryption password"
date: 2011-03-22
forum: General Help
---

### Post by vilwarin on 2011-03-22
Dear Forum,

I decided to go for an encrypted home folder. It's really really cool that ubuntu offers the encryption now out of the box!
However it auto generated a password for the encryption for me. While the password might be safe, it is impossible for me to remember. And writing it down on a piece of paper, which I would then carry around along with my laptop seems to make the whole encryption obsolete...

Long story short: Can you pinpoint me on how to change the encryption password? 

Thank You!

vilwarin

---

### Post by deconstrained on 2011-03-22
I'm not quite clear on this -- is it the *folder* that's encrypted, or the *hard drive partition* on which /home resides? If the latter, then it's most likely LUKS, in which case boot to a livedisk, and use "cryptsetup luksAddKey [device]" to add a new passphrase, then "cryptsetup luksKillSlot [device] [slot]" to delete the old passphrase. 

Otherwise, it's probably the pam-encfs method of encrypting stuff in the filesystem (which is useful for most practical purposes but won't stop someone with superuser access from reading it), in which case I don't know how to change the passphrase but I imagine there's a built-in method for doing so.

---

