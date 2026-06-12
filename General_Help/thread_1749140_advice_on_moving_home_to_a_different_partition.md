---
title: "advice on moving home to a different partition"
date: 2011-05-04
forum: General Help
---

### Post by sdowney717 on 2011-05-04
IMO, cant be done.
Prove it too me.
I followed 2 guides and they end up failing with an ICEauthority error and a gconf error and others refering to nautilus. finally left with an empty background and a mouse and that is all.

What happened to me was an upgrade to 11.04 failed.
So I decided to preserve my old home folder.
Booted up liveCD
ran gparted and shrunk old and made nex ext4 partition
copied over the files using rsync
reinstalled 11.04 to the shrunk area which was then unallocated space.
Ubuntu was working fine.
Then edited fstab to mount /home on the uuid of the home partition
And I get continual various errors

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

personally am thinking this might work within the same version of Ubuntu, but not moving to a new version of Ubuntu.

---

### Post by nothingspecial on 2011-05-04
I sometimes do it the other way around. Say you start with just / and /swap on one disc.

From a live cd, mount the / partition and delete everything except /home, move everything out of home then create a new small partition for / and install to that specifying the original partition as /home.......

....... so rather than copying home to a new partition, just delete everything else.........

....... if you see what I mean.

nb when you reinstall, you must make sure your new user has the same uid/gid as the original one.

---

### Post by sdowney717 on 2011-05-04
my sense it only works for some people and certain particular versions of the os and wont work for other people and other versions of the os.
Looking at the multitude of guides out there it ought to work but maybe many of these guides are too old to be of current use. So I have yet to find a comprehensive definitive guide.

I found this which mentions you can try to fix the ICE authority, but it might not work and he even admits in his guide it works for some people not other people.
[http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome)

I tried using his example and it did not work fixing the permissions. And googling this came up with other people claiming ICEauthority issues could be due to a multitude of issues.

what I would like to find is a definitive working guide on how to do this apparently extremely geeky thing which apparently even developers dont care to give out to new installers of linux. I think if it worked, having a separate home would be such a good idea for upgrades and fresh installs it should be the default.

---

