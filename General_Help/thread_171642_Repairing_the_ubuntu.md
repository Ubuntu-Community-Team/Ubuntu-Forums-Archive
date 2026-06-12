---
title: "Repairing the ubuntu"
date: 2006-05-07
forum: General Help
---

### Post by emkay84 on 2006-05-07
I have problem on my ubuntu
After formatting the unused space to make a new partition, i mounted it (the new partition) on /home
after that i faced the problem.i cant access the system folder and other folder as well.
i thought the problem can be solved by logging off the computer. 
but the condition become worst as when i want to login back, i cant.:confused: 
so is anybody here can help me.

thank you.

---

### Post by Ramses de Norre on 2006-05-07
Did you copy over the contents? There is a lot of program information in your /home folder (in hidden files) and a lot of hard & sym links which aren't handled correctly by cp.

What error do you get when trying to acces /?

---

### Post by emkay84 on 2006-05-07
i forgot what the error message  because i cant re-login after i log out.
but after i login there are several message pop-up and then the computer back to login page again.
finally i decided to shut down the computer.

---

### Post by Ramses de Norre on 2006-05-07
Could you describe what exactely you did, how did you copy over your home fiolder if you did?
And what errors pop up?

---

### Post by mikeyman on 2006-05-07
Good news is your data should all be there. The bad news is that it is now hidden. What I would suggest is that you boot up using a live CD. Mount the current / filesystem mkdir /newhome. Then vi or edit the /etc/fstab and point your new partiton to /newhome. Then reboot and you should be back to your starting point. You can then copy (cp /home/* /newhome - Rf) your /home directories to your /newhome. Then umount /newhome and change /etc/fstab to mount /newhome back to /home. Note that doing this will leave your old home folder alone, but hidden so there is some wasted space on your / filesystem. When everything runs OK you can boot up in the live cd again and delete the old stuff (being careful of course to only mount the old / file system and not the new one). Hope that made sense.

---

