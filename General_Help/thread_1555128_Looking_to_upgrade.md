---
title: "Looking to upgrade"
date: 2010-08-17
forum: General Help
---

### Post by unknown user on 2010-08-17
I have been trying to update my system now for the last 2 months and have been unable to. When I click on update manager and click check it comes back with n my system is up to date. It does say that 9.04 is available.

I want to update but last time I did, the system would not boot and I lost everything. Is the 9.04 update OK and is there a way I cam ensure that nothing is not lost? I have heard that you can take a copy of your user file and use that as a back up if needed, is this correct?

---

### Post by ranch hand on 2010-08-17
8.10 is past its "end of life date".  This occurred when 10.04 was released.

You can probably get some updates if you use synaptic instead of Update Mangler.  The server edition has some support time left so kernel updates may be available and some other core items.

9.04 is a better OS.  Should work fine.

If you are up to it I would do a clean install on 2 partitions and transfer your files to that.  That way you have a better install and can use ext4 instead of ext3 and have a / and a /home partition which is a more robust way to install.

9.04 will also be running out of support here pretty quick.  You might be better off to put your files in some back up media and download the 10.04 LTS release and install it and then put your files in that.

Three years of support on the LTS.  New LTS in 2 years.  LTS to LTS upgrades work (8.04 to 10.04) so 10.04 to 12.04 will be fine too.  You have plenty of support left on the old LTS (one year) to wait for the new one to become stable before upgrading to it.

I do not know if you have space for your files on your HDD or not, but an awful lot can be put on a RW DVD.  Get some of those and you can put get the Live DVD of 10.04 and have all the nice recovery tools that are on the Alt install CD on the Live DVD.

I really would install on 2 partitions and on your 40Gb drive I would go with 8 to 10 Gb for the / (root) partition and 1Gb for swap and the rest for /home.

---

### Post by howefield on 2010-08-17
For clarity, 8.04 has a bit of life left yet.

End of life comes at April 2011 (Desktop) and April 2013 (Server).

---

