---
title: "End of Life Support - am I a little exposed?"
date: 2012-04-11
forum: General Help
---

### Post by Quarkrad on 2012-04-11
I maintain a number of family and friends machines that I have converted from Windows - all are very happy and all but one (they are on 11.10) are on 10.10.  For numerous reasons Unity was not the way to go so virtually all have stayed in the 10.10 world and are more than happy.  I have just discovered 10.10 has a end of life of April 10 - I thought it would be 2013 like 10.04.  (Seems strange to me that a later release has an earlier EOL).  There is some advice to wait until the 1st step release of 12.04, due July 19th I believe for a robust, bug ironed out, release - but 10.10 'runs-out' on April 10.  To be honest I'm not sure of the impact of this gap April 10 - July 19; is there anything to worry about?  I have 7 machines (4 family 3 friends) that are currently on 10.10.  I intend to re-install 12.04 on all 8 PCs but the question is when - any advice appreciated.  (note - all these PCs are used for low level activity, mostly email, surfing and a little photo work.  My main concern is the lack of support in terms of virus updates).

---

### Post by kimda on 2012-04-11
> **Quarkrad said:**
> I maintain a number of family and friends machines that I have converted from Windows - all are very happy and all but one (they are on 11.10) are on 10.10.  For numerous reasons Unity was not the way to go so virtually all have stayed in the 10.10 world and are more than happy.  I have just discovered 10.10 has a end of life of April 10 - I thought it would be 2013 like 10.04.  (Seems strange to me that a later release has an earlier EOL).  There is some advice to wait until the 1st step release of 12.04, due July 19th I believe for a robust, bug ironed out, release - but 10.10 'runs-out' on April 10.  To be honest I'm not sure of the impact of this gap April 10 - July 19; is there anything to worry about?  I have 7 machines (4 family 3 friends) that are currently on 10.10.  I intend to re-install 12.04 on all 8 PCs but the question is when - any advice appreciated.  (note - all these PCs are used for low level activity, mostly email, surfing and a little photo work.  My main concern is the lack of support in terms of virus updates).

10.04 is a LTS release they have longer support than the regular releases. 
I would install 12.04 first on your own PC to see how you like it before installing it on the other PC's. You can also install gnome classic on 12.04 if you do not like Unity. I've installed it on my laptop and PC and its pretty stable so far. 

[http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed/](http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed/)

---

### Post by dcstar on 2012-04-11
> **Quarkrad said:**
> 
.........
My main concern is the lack of support in terms of virus updates.

There are really no "virus" issues in the updates. Ubuntu releases receive Security Updates during their support periods to patch potential issues that may (in very rare circumstances) threaten a system.

Most Linux systems behind NAT firewalls are already protected from any direct attacks via the Internet, and the general Linux security model protects a system from 99.9% of the stupidity that plagues Windows systems.

If you want to keep systems secure then simply don't install software from non-official repositories and you immediately prevent the major threat to any Ubuntu installation.

---

### Post by Quarkrad on 2012-04-11
I have installed 12.04 on my machine in virtualbox and it is OK for all the pc/laptops in either native (unity) or classic form. From what you say, if I wait until July 19 before upgrading them, then the 10.10 machines will be as safe as they were prior to July 19 with full support.  Thanks.

---

### Post by kimda on 2012-04-11
Most malware and virusses are targetting Windows. I wouldn't be too worried. Like dcstar said just install software via the trusted repositories. You can lock the other pc's more down by giving those users no admin rights. I guess that you are the user with the (sudo) admin rights on these machines?

---

### Post by Mark Phelps on 2012-04-11
Given the inability to roll-back to previous versions, I would NOT just jump in and install 12.04 on your PC.  IF there are problems, and since it's STILL in Beta, there are likely to be, there is no simple way to go back to a working Ubuntu version.

Instead, use the LiveCD or LiveUSB method to try it out first.  That way, if it works OK, you can upgrade without problems.

---

### Post by forrestcupp on 2012-04-11
> **Mark Phelps said:**
> 
Instead, use the LiveCD or LiveUSB method to try it out first.  That way, if it works OK, you can upgrade without problems.

Definitely test with a LiveCD/USB first on each computer. Also, back up all of your important data in case something goes wrong.

12.04 is the next LTS (Long Term Support) version, so it should be pretty stable when it gets past beta. The final release is April 26th.

You could use Gnome Classic, which is as close to Gnome 2 as you're going to get. Or you could also check out Xubuntu, which uses the Xfce desktop environment. It's more similar to what you're used to than the new DEs.

---

### Post by mastablasta on 2012-04-11
additionally the 12.04 release will be supported for 5 years.

---

### Post by Bucky Ball on 2012-04-11
As mentioned, wait til it's stable on your machine then deploy 12.04 LTS! I always do stick with the LTS releases when installing on and maintaining other people's machines. They tend to be more robust, break less and therefore need less of my attention, and the extra long support means you don't have to go through the release upgrade for three or, in this case, five years. ;)

---

### Post by theDaveTheRave on 2012-04-11
Your other option is to set up a dual boot on the pc's to have a working copy of 12.04 (although it is still in Beta).

Your family can try it out, see if they like it, still access all of the data from the other partition. But if it is horribly buggy they can simply down tools and forget about using it untill it we get to april 26th.

Obviously the dual boot idea will work for any version of Ubuntu. And they don't have the 'no rolling back' issue.

Or alternatively they could try another flavour of linux (I keep thinking of having a try at Mint).

Try giving your family and friends some options, especially as they have obviously allready made the hardest part of the journey away from Windows. You may be surprised that they like the idea of trying other distros in a dual boot.

(i suspect, like me, you want to stay with an ubuntu or debian based release, hence the suggestion for mint).

---

### Post by muteXe on 2012-04-11
I normally (not going to install this time) give it at least one month after release before considering a fresh install.

---

### Post by Quarkrad on 2012-04-11
Thank you all.  I went 11.10 on one machine only because mother-in-law, who is in her 80's, is in love with a damn slimline Apple Keyboard and try as I might I could not get it to work on 10.10.  11.10 was the only version I could get it to work on (note - I'm a newbie so it was 11.10 for me).  Most of my family/friends are 60+ so they just want a 'working machine' - since 8.04 (my first Ubuntu machine) I have wiped the partitions and done a clean install when a new version comes out. All the Desktops have another HD in them for backup and for the laptops I use Dropbox or Ubuntu Cloud for key ./home files.  12.04 looks good for all our machines in my Virtualbox environment so reading all your replies I think I might keep them all at 10.10, as they are, until the first step release on 19th and then upgrade.  I appreciate re-install rather than upgrading is a little longer but reading this forum the past years (since 8.04) some people seem to have issues when upgrading rather than re-installing.  As I have quite simple machines I tend to re-install rather than upgrade.  Appreciate all your advice.

---

