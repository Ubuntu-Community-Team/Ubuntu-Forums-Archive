---
title: "iPod connecting help. :)"
date: 2009-11-01
forum: General Help
---

### Post by ColdLunch on 2009-11-01
I have a 8 GB iPod touch running version 2.2.1 firmware.

When I plug it in with a USB cable it shows up on my desktop (it has a camera icon though, not sure if thats the problem).

However, I doesn't connect to any program I've tried (Rhythmbox, Banshee, Amarok, gtkpod, Songbird, Exaile.)

What should I do to fix this?  Is it because its being detected as a camera?

Thanks so much! :D

---

### Post by ZankerH on 2009-11-01
You need to first Jailbreak your iPod Touch and install ssh on in (the same exact way you would with an iPhone). Install the latest SVN build of libgpod/gtkpod and sshfs, mount /var/root/Media on the iPod Touch to the directory of your choosing on your filesystem, and transfer away with GTKPod.

---

### Post by Tahakki on 2009-11-01
Unfortunately, at present with your firmware, there's no way to do it without jailbreaking. I have the same problem.

---

### Post by ColdLunch on 2009-11-01
Alright, I will jailbreak soon.

What should I do after the jailbreak?

Also, would there be a way to do it without jailbreaking but upgrading to firmare 3.1?

---

### Post by Tahakki on 2009-11-01
At present, you need to jailbreak, though there's a very-very-alpha method just released - they've reverse-engineered it, so you won't need to jailbreak.

If you're jailbreaking anyway, once it's done edit the Checkpoint.xml and change the database version value from 4 to 2. It should work with Rhythmbox etc.

---

### Post by ColdLunch on 2009-11-01
> **Tahakki said:**
> At present, you need to jailbreak, though there's a very-very-alpha method just released - they've reverse-engineered it, so you won't need to jailbreak.

If you're jailbreaking anyway, once it's done edit the Checkpoint.xml and change the database version value from 4 to 2. It should work with Rhythmbox etc.
Thanks!

Where exactly is the Checkpoint.xml file?

---

### Post by ColdLunch on 2009-11-02
bump! :D

---

### Post by Tahakki on 2009-11-02
It's located at /System/Library/Lockdown/Checkpoint.xml.

I'll be jailbreaking my brother's iPod tonight (Windoze required, unfortunately) and then setting it up to sync with Ubuntu. I'll let you know how it goes. :)

---

### Post by ColdLunch on 2009-11-02
Sweet thanks!

---

### Post by jordanae on 2009-11-02
you can also connect wirelessly (after jailbreaking of course. Look in Cydia for an SSH application and download it. Once you do that got to Places> Connect To Server then select SSH from the dropdown menu, type in 22 as the port number then type in your ipod's IP address

---

### Post by Tahakki on 2009-11-02
Gah. Problems. I simply couldn't get it jailbroken - the only program that can jailbreak a 2G running 2.2.1 is Quickfreedom, and it doesn't work for me.

---

### Post by ColdLunch on 2009-11-02
> **jordanae said:**
> you can also connect wirelessly (after jailbreaking of course. Look in Cydia for an SSH application and download it. Once you do that got to Places> Connect To Server then select SSH from the dropdown menu, type in 22 as the port number then type in your ipod's IP address
After I connect it, how do I add music to it?
> **Tahakki said:**
> Gah. Problems. I simply couldn't get it jailbroken - the only program that can jailbreak a 2G running 2.2.1 is Quickfreedom, and it doesn't work for me.
Ah, oh well.  I have OSX and I've jailbroken a couple ipods with it so hopefully it'll work again.

---

### Post by ColdLunch on 2009-11-05
Been a couple days.  Does anybody know what to do once you've jailbroken the iPod? 

Thanks. :)

---

### Post by Tahakki on 2009-11-06
Edit the file at /System/Library/Lockdown/Checkpoint.xml, find the DBVersion key, and change its value from 4 to 2.

---

### Post by ColdLunch on 2009-11-06
Sorry for my noobiness, but I can't seem to find System or Library...

Can you tell me where it is? Thanks!

---

### Post by Tahakki on 2009-11-07
I thought that once you'd jailbroken it you could just plug it in and see those files?

What does Nautilus show?

---

