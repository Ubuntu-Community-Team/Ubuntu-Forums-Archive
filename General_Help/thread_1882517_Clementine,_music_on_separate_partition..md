---
title: "Clementine, music on separate partition."
date: 2011-11-17
forum: General Help
---

### Post by clark333 on 2011-11-17
Hi -

Ive had ubuntu 11.10 dual booted for some days now.  I mainly use my netbook to listen to music.  I installed clemintine for this purpose.  Every time i restart my netbook, i loose my library and have to add the folder again.  My music is located on a seperate partition.  Can anyone help me with this or reccomend a player that doesnt fail?

thanks for any help

---

### Post by TBABill on 2011-11-17
Have you gone into settings and told Clementine where your library is so it'll retain the settings? And as a kind recommendation, I'd change your subject to something useful regarding Clementine rather than threatening to go back to Windows. You'll get better assistance that way.

---

### Post by papibe on 2011-11-17
Hi clark333.

Do you have your music on a network share? or
Is it in your Windows partition?

If so, it may be necessary to setup the that location as an automatic mount at start up time.

I don't know about clemintine's configuration, but Rhythmbox works pretty good for me if the remote music files are mounted.

Regards.

---

### Post by clark333 on 2011-11-17
Hi there, nice talking to you.  My music is on a windows partition (ntfs).  How do I set up the partition to automatically mount on start-up?

---

### Post by fantab on 2011-11-17
> **clark333 said:**
> Hi -

Ive had ubuntu 11.10 dual booted for some days now.  I mainly use my netbook to listen to music.  I installed clemintine for this purpose.  Every time i restart my netbook, i loose my library and have to add the folder again.  My music is located on a seperate partition.  Can anyone help me with this or reccomend a player that doesnt fail?

If you wish to use the title of the thread as threat to leave Ubuntu in favor of Windows then let me tell you quite frankly, NOBODY CARES, NOBODY GIVES A ****. 

If you need any help... please be polite.

As for your problem, you need to mount the "separate partition" before you open/run Clementine, [**SEE THIS**]("http://www.psychocats.net/ubuntu/mountlinux"). [**THIS**]("https://help.ubuntu.com/community/MountingWindowsPartitions") AND [**THIS**]("http://www.psychocats.net/ubuntu/mountwindows")

The Third link is simplest.

---

### Post by boast on 2011-11-17
> **clark333 said:**
> Hi there, nice talking to you.  My music is on a windows partition (ntfs).  How do I set up the partition to automatically mount on start-up?

need to edit your /etc/fstab with something like this ```
/dev/<NTFS-part>  /mnt/windows  ntfs-3g   defaults		  0       0
```

---

### Post by clark333 on 2011-11-17
> **fantab said:**
> If you wish to use the title of the thread as threat to leave Ubuntu in favor of Windows then let me tell you quite frankly, NOBODY CARES, NOBODY GIVES A ****. 

If you need any help... do that politely. 

As for your problem, you need to mount the "separate partition" before you open/run Clementine, [**SEE THIS**]("http://www.psychocats.net/ubuntu/mountlinux"). [**THIS**]("https://help.ubuntu.com/community/MountingWindowsPartitions") AND [**THIS**]("http://www.psychocats.net/ubuntu/mountwindows")

The Third link is simplest.

Im grateful for any help.  I definitely like Linux and Ubuntu - im just wanting everything to run properly.  Clemintine is the third music app that ive tried with no success, so exucse my ignorance never realised how much everyone is anti-windows here.  thanks for any help non the less.

---

### Post by mörgæs on 2011-11-17
Thread title changed.

---

### Post by Elfy on 2011-11-17
> **clark333 said:**
> Im grateful for any help.  I definitely like Linux and Ubuntu - im just wanting everything to run properly.  Clemintine is the third music app that ive tried with no success, so exucse my ignorance never realised how much everyone is anti-windows here.  thanks for any help non the less.

Very few are anti-windows - a fair few take exception to silly threats about going back to it :)

Not only that - but people use the thread title to see if they can offer help. 

Pointless thread titles waste people's time.

---

### Post by sixthwheel on 2011-11-17
> If you wish to use the title of the thread as threat to leave Ubuntu in favor of Windows then let me tell you quite frankly, NOBODY CARES, NOBODY GIVES A ****. 

If you need any help... [COLOR="Red"]please be polite.[/COLOR]

You mean, like you?

---

### Post by clark333 on 2011-11-17
Oh, I see.  Should have thought about the subject heading, as you say - people are offering their own help.  Will bear that in mind.  Funnily enough, my music partition seems to auto-mount everytime i restart ubuntu.  Just restarted and my library was ok.  So for some strange reason my problem no longer exists.

thanks anyway to all, sorry about the original subject title.  and many greetings from Edinburgh.

---

