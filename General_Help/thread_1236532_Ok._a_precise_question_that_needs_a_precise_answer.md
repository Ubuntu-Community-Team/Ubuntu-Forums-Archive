---
title: "Ok. a precise question that needs a precise answer please."
date: 2009-08-10
forum: General Help
---

### Post by phr33k-dc on 2009-08-10
I am about to do an encrypted install with an alternate cd of ubuntu 64 bit.

I will be doing the LVM thingy. I have heard it is reccommended to create a seperate partition for your /Home. If I choose to do a guided install and then when i boot up go to partition editor and follow this tutorial - [http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")
will it still be encrypted?

or is it possible to create the encrypted /Home partition during the install?

any questions if im not clear?

---

### Post by Maheriano on 2009-08-10
Specific threads need specific titles please.

---

### Post by phr33k-dc on 2009-08-10
ye sorry just ment REALLY NEED HELP. can you help?

---

### Post by Maheriano on 2009-08-10
If you're going to be creating your own partitions during the install, you won't be using the guided option, you'll be using the manual option. As far as I know, the guided option uses EXT3 filesystems and the only way to get EXT4 is to do it manually. You'll have to do it manually anyway to split your /, SWAP and /home directories which is what you're after. There should be an option in there for encrypting the partitions.

---

