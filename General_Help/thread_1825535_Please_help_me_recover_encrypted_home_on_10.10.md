---
title: "Please help me recover encrypted home on 10.10"
date: 2011-08-15
forum: General Help
---

### Post by lhommedangereux on 2011-08-15
i installed ubuntu 10.10 because i'm not a fan of 11.04 at all.  this was a dual boot ubuntu/windows 7 laptop, i've done this a thousand times so i don't know what went wrong this time, but after a day of working fine, i lost windows 7 from the grub menu, even when i tried sudo update-grub it would only find the linux partitions, i could still however navigate through my windows files through ubuntu so i did so and backed up all my VERY important documents to ubuntu then reinstall my windows 7 which, as i knew it would do, ate my grub bootloader.  so i am running ubuntu 10.10 live trying to figure out how to either restore grub without installing a fresh copy of ubuntu over my important stuff, OR try to recover the files out of ubuntu encrypted home folder and move them to my windows desktop using a live usb.  i have searched the forums and tried several suggestion like this one [http://ubuntuforums.org/showthread.php?t=1597246&highlight=live+cd+recover](http://ubuntuforums.org/showthread.php?t=1597246&highlight=live+cd+recover)  to no avail.  its like the commands don't work for recovering my passphrase.  maybe it is for a different version or something... 

one of the documents is very important to me, its information for an interview with a state police department (not my state) i have coming up on aug 30 and i can't just call and ask for it. that would look really bad and cost me the job im sure. 

any help is extremely appreciated

---

### Post by bodhi.zazen on 2011-08-15
See: [http://bodhizazen.net/Tutorials/Ecryptfs#Live](http://bodhizazen.net/Tutorials/Ecryptfs#Live)

---

### Post by lhommedangereux on 2011-08-15
thank you, that seems to be helping, i got all the way to the ecryptfs-mount-private step and its asking me apt-get install ecryptfs-utils but when i do theres always an error, im guessing its trying to install to my live usb disk and i didn't give it any storage memory, so im going to boot back into windows 7 and use universal usb installer to do that.  hopefully this works.... thank so much for the reply, ill let u know what happens either way.

---

### Post by bodhi.zazen on 2011-08-15
post the error you are getting.

---

### Post by lhommedangereux on 2011-08-17
i would but messing around with the commands in the link provided above i somehow got back to booting into ubuntu with no windows 7 appearing as bootable, grub menu doesn't even show up while booting, so now i am back to my original problem with not being able to boot into windows partition and grub not finding it when i sudo update-grub.   I did find a fix tho, with the windows partition mounted in linux (doesn't have to be live) navigate to the windows partition root and there are two folders named "boot" and "Boot"  i deleted the lower case "boot" folder and then tried sudo update-grub and it found my windows partition!!!!  it is working perfectly now but thank you so much for all the help, ubuntu has some of the most helpful forums i've ever used.

---

