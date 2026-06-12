---
title: "Fileshare Problems Ubuntu 11.10 and Vista"
date: 2011-12-05
forum: General Help
---

### Post by j.gray08 on 2011-12-05
I am having some issues setting up file share between Win Vista and Ubuntu 11.10.

The Vista machine has several folders set to share with anyone on the network.
Buntu is set up with Samba configured to the workgroup on Vista, users on both machines are identical name/password. Files on Buntu are set to be shared with guest users as well for now till i get it working flawlessly.

When i go into the network on the Buntu, it brings up Windows Network inside that we have the Workgroup, and inside that we have both machines visible. However when i try to access the Vista machine, i get "unable to mount   failed to retrieve share list from server.

Now from Vista, In network i get Vista, a media share from the vista comp, and an unknown device. now i know that the unknown device is the Buntu machine, when i take it off the network, i lose the unknown device.

doing research i found where to go into the terminal and editing certain files that change workgroup and set up a share that way, but it hasn't worked either.

      Any Help would Be Appreciated. Thx

    i will also eventually have to add a Win7 machine to the set-up as well

---

### Post by gennatolls on 2011-12-06
Try searching Morbius1 on the forum search. He/she is a samba ninja and probably has answered your question already, there was a thread similar to yours earlier today that they solved.

---

### Post by 2F4U on 2011-12-06
Is there a firewall on the Windows machine that may prevent accessing it.

---

### Post by j.gray08 on 2011-12-06
okay, i searched Morbius1 and his/her post were lost on me, hopefully they can help sometime though.

anyways, i got home today and tried again. Today the Buntu doesnt show up at all, not even as an unknown dev. i booted up Win7 machine, and it and the vista machine have no problem communicating. saw your post about the firewall and turned off the firewall, restarted both machines and still same problem.

The buntu Machine will not even connect to the Workgroup today, now that is where it says unable to retrieve file share list from server...

Thx for the quick replies, hopefully we can figure this out soon.

---

### Post by gennatolls on 2011-12-06
Have you thought about using SSH and Putty? Its really simple once you get familiar with the command line if you haven't already. I have had terrible luck with samba. Once getting it configured perfectly then following the same steps and being unsuccessful on a different pc. I use SSH and SCP almost every day, they are very reliable and I haven't had an issue with them. If your determined to use Samba, make sure you backup your smb.conf (/etc/samba/smb.conf) file first . Then install Samba by searching for it in the software centre (the one with the windoze logo). I used that and was sucessful. I followed this guide:
 [http://www.howtogeek.com/74459/how-to-create-samba-windows-shares-in-linux-the-easy-way/](http://www.howtogeek.com/74459/how-to-create-samba-windows-shares-in-linux-the-easy-way/)  

Here's another good tutorial that may help: [http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

Also to note, I'm not sure if Samba can access drives mounted at /media (i e : external hdd's,usb drives, CD's etc). You may need to edit /etc/fstab to have those drives mounted somewhere else if that's what your trying to access. Hope you get it working, I feel your pain. I convinced my room mate to split the cost of a Terabyte drive to place into my computer to give him 500gb of backup space in exchange. Luckily Deja Dup allows backingup over SSH. :) Good luck.

---

### Post by j.gray08 on 2011-12-06
i was just using samba because I had used it in a different setup with an ubuntu 10.10/vista share...   i have been attempting this through a wireless network, just to try i hardwired both comps to the network, now Buntu has access to Vista comp, however Vista is still showing Buntu as unknown dev.

i have uninstalled everything samba i have added/edited, rebooted, then right clicked/share the folders i wish to share. this prompted the reinstall of Samba, however it is not in my dash. went through the terminal and made sure im still set for workgroup.

wrap up---
     wired connection Vista: no access to Ubuntu (Ubuntu shows up as unknown device)
                              Ubuntu: access to Vista shares
     
     wireless connection Vista: "same as above"
                                  Ubuntu: access windows network, but not workgroup


i really cannot see it being a vista setting, i have access from a xbox 360 through the network, 2 windows phone 7's through the network, and a Win7 laptop

---

### Post by gennatolls on 2011-12-06
> **j.gray08 said:**
> 
i really cannot see it being a vista setting, i have access from a xbox 360 through the network, 2 windows phone 7's through the network, and a Win7 laptop

There's your problem, too much Windows :D

All kidding aside, Did you try using the Samba GUI I mentioned? I agree its not a Vista problem, I've gotten that same error message you are getting. I tried and tried how you mentioned then gave up and restored my default smb.conf file and used the GUI and it worked.
Something wasn't properly configured for me by clicking "share" on the folder options. When I used the Samba GUI, in Nautilus the folder didn't show up as "Shared" even though it was actually configured to share. The only way I was able to access the Samba share that I "Shared" through Nautilus as you have was on my MacBook (I hate Mac too so hold the jokes). I don't think Nautilus handles it properly. Give that Samba GUI a try. 

Good luck.

---

