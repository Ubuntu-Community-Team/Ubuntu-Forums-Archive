---
title: "Places &gt; Network - connection lost"
date: 2010-05-03
forum: General Help
---

### Post by Scunnered on 2010-05-03
Prior to loading Lucid I was able to copy my partners information over from her XP system to 9.10.  When I attempted to do so today I was able to see the Windows Network and MSHOME.  Having clicked MSHOME the system was rather slow and eventually produced the following error message :

"[B][I]Unable to mount location
Failed to retrieve share list from server[/I][/B]"

Looking at the XP end I can clearly see the shared folders in the appropriate section.  Strangely enough I can print from one of the shared pictures over to my USB attached printer on Lucid.

Can you please offer guidance?

---

### Post by bhold on 2010-05-03
Not much to add other than I have the same problem. Still works fine when I boot from my 9.10 partition, but fails when I boot into 10.04. I resolve the XP system IP address through /etc/hosts - they are the same in 9.10 and 10.04. No problem with ping from 10.04 to the XP system, but it hits a wall when trying to get the share list.

---

### Post by Scunnered on 2010-05-04
**bhold**

Thanks for your reply. I hope that this is looked at urgently as I backup my partners photos and it is more than my life is worth if it is not done.

Life was simple when access was available but at the moment my ears are getting a bashing at my inability to resolve the problem.

Lets see if there is someone out there who can put us out of our misery.

---

### Post by bhold on 2010-05-04
Attempting to find another way to access my Windows XP shares from 10.04, I installed sambfs and tried to mount the share using mount.cifs. This did not work - times out then tells me to look at the mount.cifs man page. 

Installing sambfs then using mount.cifs to access Windows shares works fine on 9.10. 

I'm not sure what to try next - so will continue to search the forums every few days and wait for the next few rounds of patches to 10.04 and try again. But for now I will continue using 9.10 for my Win share backups.

---

### Post by Scunnered on 2010-05-04
Again thanks for your advice.

I have unfortunately comitted myself to using the LTS and my experience being somewhat limited do not want to attempt to go back.

I am able to fudge round my problem for the moment by using a USB drive but would much prefer to have the status quo.

Like you I will keep my eyes open to see what develops.

---

### Post by bhold on 2010-05-04
I have been able to access my Windows XP shares from 10.04 with the following kluge, here is what I did in case you might find this useful:

1. Installed smbfs.
2. Create a mount point for my share - sudo mkdir /mnt/mydocs
3. mount the share using the following command:
sudo mount -t cifs //10.1.10.100/mydocs /mnt/mydocs --verbose -o user=bhold

Several points on the above command - I had to use the ip address rather than the hostname I entered in /etc/hosts. For some reason I am not getting name resolution. Maybe I have some name resolution config problem on my system. Also I had to do the following, as explained in [http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475) - reply #5 by swizman:

sudo chmod +s `which mount.cifs`
sudo chmod +s `which umount.cifs`

I'm looking forward to getting this working again as it does on 9.10 but for now I can get by with this.

---

### Post by Scunnered on 2010-05-04
Again thanks for your advice.

As my religion is devout coward I think that I will be patient and await the updates which I trust will resolve the problem.

---

### Post by bhold on 2010-05-07
Windows share access from Nautilus on 10.04 is working fine on my system today (Friday May 7). I have been keeping up with 10.04 patch installations, something fixed it. However on 10.04 it is faster to first do a "connect to server" in Nautilus before accessing the share. If I double-click on "Network" before connecting to the server there is a delay.

---

### Post by Scunnered on 2010-05-09
**bhold**

I am glad to see that things are working for you.  I tried again this morning and was informed :

***Failed to retrieve share list from server***

It looks like I will have to devote some time to go over everything again and see what happens.

---

### Post by Scunnered on 2010-05-10
**bhold**

I have been over everything on the XP system and as far as I can see everything is as it should be.  I am also copmpletely up to date with with the Update Manager having checked again before posting.

I still have the same problem where it takes for ever and a day for the search to function and still comes up with the failed to retrieve message. 

Could you please walk me through how you **"connect to server" in Nautilus** in order that I may give it a try.  My book does not cover this.

Hopefully with your kind assistance it will work properly.

---

### Post by bhold on 2010-05-24
Sorry for the delayed response - away from the forums for a while.

To connect to a Windows share through Nautilus on 10.04 I do the following:

Click on "Places"
Under "Network", click on "Connect to Server..."
In Service type, select "Windows share" and specify Server name
Click on "Connect"
At this point I get a Nautilus window showing available shares.

The Server name corresponds to an /etc/hosts entry that I have entered with the ip address of my Windows XP system. There are several ways to resolve the address of your Windows system for access to shares (I am not an expert) - but an entry in /etc/hosts works fine for my very simple network.

---

