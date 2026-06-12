---
title: "Clean install with new /home or point to an existing /home during installation"
date: 2009-11-14
forum: General Help
---

### Post by SvenBuntu on 2009-11-14
I'm about to install karmic koala. My setup has a separate /home partition (current os: jaunty). The question I have for a new install is: should I install cleanly and then re-point /home to my existing or should I specify /home during installation? 

I considering installing KK on yet another partition to test it out since so many people had troubles in which case I wouldn't want to use the current /home not to delete any settings should I want to go back to JJ. 
Is it possible to change the /home partition afterwards wihtout braking software? I can see applications failing due to not having the correct versioned settings?

Also, I can't remember how the installation works, will it not overwrite the current /home partition? 

Finally, I don't post here much but use the forums extensively for any Ubuntu related information. So I wanted to say thanks to all people putting in their time to help. It's a great support tool and has kept me staying clear from Windows for two years now.

---

### Post by 23dornot23d on 2009-11-14
[I'm about to install karmic koala. My setup has a separate /home partition (current os: jaunty). The question I have for a new install is: should I install cleanly and then re-point /home to my existing or should I specify /home during installation? ]

I would create a seperate /home and not relate it to a previous one ..... if your intention is to boot with JJ and KK in seperate partitions ......

I would also stick the new version of KK in EXT3 rather than EXT4 ,,,,, 

my reason is only that you will be able to read the new home from JJ .......

If you set KK as EXT4 ...... you will not be able to access it from JJ

if this does not matter to you then EXT4 is ok ..... 

It also uses GRUB2 ....... just to let you know ,,,, if you did not already know that



ok thats my 2 cents worth ....... just for info ......

---

### Post by louieb on 2009-11-14
23dornot23d has some good points. Just one correction. Jaunty can read a partition formatted with ext4. (It was the 1st Ubuntu release to have ext4 support).

I dual booted Jaunty and Karmic for a while - gave each its own /home partition. Just copied the .configuration files as needed.  BTW: I'm sticking with Jaunty.

---

### Post by slakkie on 2009-11-14
You can use Jaunties homedir without a problem. 

You can set the installer to format your old /home, or you can say that it must leave the data alone. Depends on what you want really. In your case, you need to specify the correct mountpoint and tell it to leave the data alone. You can use ext4 with both Jaunty and Karmic.

I've been using the same homedir for Ubuntu Hardy/Jaunty/Karmic and Debian without a problem.

---

