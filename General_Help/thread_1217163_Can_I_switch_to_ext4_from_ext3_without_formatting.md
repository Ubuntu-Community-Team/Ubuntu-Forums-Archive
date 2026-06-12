---
title: "Can I switch to ext4 from ext3 without formatting?"
date: 2009-07-19
forum: General Help
---

### Post by barisurum on 2009-07-19
Hi there;

I considered installing 9.04 with ext4 but as my system is a production one and there were rumours of instabilities of ext4 I decided not to. With 9.10 ext4 will be standard and I think this fs is fairly tested and I want to use it. So can I switch to it without a format? A dependable and secure way?

---

### Post by credobyte on 2009-07-19
[http://maketecheasier.com/how-to-upgrade-from-ext3-to-ext4-without-formatting-the-hard-disk/2009/04/21](http://maketecheasier.com/how-to-upgrade-from-ext3-to-ext4-without-formatting-the-hard-disk/2009/04/21) ;)

---

### Post by barisurum on 2009-07-19
thanks! anyone tried this? is it safe?

---

### Post by whoop on 2009-07-19
> **barisurum said:**
> thanks! anyone tried this? is it safe?
I've had a howto running for some time... It goes properly most of the time... Some people had a few hickups. Look here:
[http://ubuntuforums.org/showthread.php?t=1118295](http://ubuntuforums.org/showthread.php?t=1118295)

---

### Post by KeyserSoze93 on 2009-07-19
You can do an inplace upgrade (see [http://ext4.wiki.kernel.org/index.php/Ext4_Howto#Converting_an_ext3_filesystem_to_ext4](http://ext4.wiki.kernel.org/index.php/Ext4_Howto#Converting_an_ext3_filesystem_to_ext4))

HOWEVER: I would not advise switching to a less comprehensively supported filesystem even if it is perfectly stable.

Jaunty really disappointed me, so I switched back to Hardy. One problem: My /home folder/partition was now useless (I had upgraded to ext4 for whatever reason). I had everything backed up so it was not too much of an issue, however I don't see a downside to continuing to use ext3 unless you have a 16 TB hard drive or you are really struggling with only having the rather small limit of 32000 sub directories.

---

### Post by philcamlin on 2009-07-19
yeah i wouldent upgrade until you go to karamic 

its too risky but you can try just remember to backup your data :popcorn::popcorn::popcorn:

---

### Post by barisurum on 2009-07-20
Thanks everyone, I think I will postpone switching from ext3 to ext4 until karmic koala is well tested, and yes I allways backup my data and encourage everyone to do so.

---

