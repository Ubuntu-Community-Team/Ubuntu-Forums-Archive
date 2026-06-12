---
title: "Roaming with the laptop: network drive tips?"
date: 2006-03-28
forum: General Help
---

### Post by bjornkri on 2006-03-28
I've had Ubuntu on my laptop for quite a few weeks now and it's been great fun. I'm settling into Linux quite well, but there are a few things I feel I can streamline, my methods sometime feel a bit awkward.

So, first of all, as I'm using a laptop and I'm not always on the same network, so some drives are unavailable from time to time. Mounting those in fstab caused a long delay when booting away from home while it searched for the drives, so I quickly removed those entries.

My (rather clumsy) solution was to put the commands for mounting into a hidden file with root as owner and group so the files cannot be viewed. 

For instance, at home I'd sudo ./.mountall.sh:
```
echo "Mounting Greebo..."
mount -t smbfs -o username=xxx,password=xxx,dmask=777,fmask=777 //weatherwax/Greebo /media/greebo
echo "Mounting Angua..."
mount -t smbfs -o username=xxx,password=xxx,dmask=777,fmask=777 //weatherwax/Angua /media/angua
echo "All done!"

```

I can't help feeling there must be a more 'proper' way to do this. ](*,)

Is there?  :-k

---

### Post by bjornkri on 2006-03-29
No one?

To be clear I guess I'm looking for some sort of a network drive manager, if there is such a thing.

---

### Post by schilcha on 2006-03-29
Personally, I like your approach to write a script that mounts the drives (I have one like that too). Here're some suggestions to streamline this procedure...

Extend the script such that it'll figure where your're at (try checking the netmask or ping one or the other host). E.g., in my situation I connect to my home-lan, which is set up as 10.42.42.0/24 and to the office-lane (10.0.0.0/24) as well. Tell your script to look at the netmask and determine which filesystems to mount accordingly.

Also, execute the script at startup or login. 

To avoid the pwd-prompt, configure sudo such that you're allowed to exec the script w/o pwd -- if you exec it at startup, you wont need that since it'll be run with root priviliges anyways. 

I'm sorry, I can't point you towards a network drive manager. Still, I hope, you can achieve a satisfying solution.

Good Luck.

P.S. Don't hesitate to ask, if you've further questions.

---

### Post by seppo on 2006-03-29
how about autofs? It doesn't have the time out issue, because drives are dynamically mounted when you access them. I use it on my laptop for samba shares. I have no delay with booting when i'm outside the office, because i don't access them. If you do acces them when they are not available, you just get an emtpy mount point, no timeouts, lockups etc.

---

### Post by bjornkri on 2006-03-30
Thanks guys. Both options seem interesting, but I'm too much of a newbie to tell ;) I think I'd like to try both, just for the experience.

The scripting option looks kinda cool, but I'm not too good at the scripting part. I know enough programming generally to find my way into and out of a loop, but what functions to call and programs to run and so on I don't know. I get stuck after the pinging, can I somehow check if a certain string is found (or isn't found, like 'Unreachable') and mount accordingly?

Autofs I don't know anything about, I'll browse the man pages and google for it. Any good resources would be welcome though :)

---

### Post by seppo on 2006-03-31
Here you go:

[http://www.linux-consulting.com/Amd_AutoFS/autofs-HOWTO.html](http://www.linux-consulting.com/Amd_AutoFS/autofs-HOWTO.html)

Or a shorter gentoo manual:

[http://gentoo-wiki.com/HOWTO_Auto_mount_filesystems_(AUTOFS](http://gentoo-wiki.com/HOWTO_Auto_mount_filesystems_(AUTOFS))

good luck!

---

