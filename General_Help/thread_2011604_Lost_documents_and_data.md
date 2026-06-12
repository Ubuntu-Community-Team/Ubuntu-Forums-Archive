---
title: "Lost documents and data"
date: 2012-06-27
forum: General Help
---

### Post by christon74 on 2012-06-27
Hello everybody  :)
Is there a way to retrieve to retrieve lost documents and data? I have just done a fresh install of Ubuntu 12.04 LTS. I had to. What happened is a few days back Ubuntu would not load completely. The desktop and icons (left side panel) were there but everything was 'frozen' and no application would launch. Solution= recovery mode, run dpkg, repair broken packages and then reboot normally_ a bit tedious.  Then somebody suggested that I remove Unity and use GNOME desktop instead. Very Bad idea. I did that and found out that my password no longer was recognized. That is why I had to re-install 12.04.
But I have lost some documents and data. Is there a way I can retrieve them or are they really lost for good? 

Thanks to all in advance for any tip.

C.NAUD

---

### Post by GreatDanton on 2012-06-27
During the installation if you used option USE THE ENTIRE DISK- then your data is lost. If you use option install side by side then your data is still on disk.

Ps. I heard something about programs for data rescue, however they are very expensive.

Maybe some expert will tell us more about data rescue :)

---

### Post by ajgreeny on 2012-06-27
> **christon74 said:**
> Hello everybody  :)
Is there a way to retrieve to retrieve lost documents and data? I have just done a fresh install of Ubuntu 12.04 LTS. I had to. What happened is a few days back Ubuntu would not load completely. The desktop and icons (left side panel) were there but everything was 'frozen' and no application would launch. Solution= recovery mode, run dpkg, repair broken packages and then reboot normally_ a bit tedious.  Then somebody suggested that I remove Unity and use GNOME desktop instead. Very Bad idea. I did that and found out that my password no longer was recognized. That is why I had to re-install 12.04.
But I have lost some documents and data. Is there a way I can retrieve them or are they really lost for good? 

Thanks to all in advance for any tip.

C.NAUD
More information please about the way your old ubuntu was setup, most importantly; did you have a separate /home partition or was everything installed according to the default way that ubuntu does it, ie everything except swap on one partition.

If everything was on the one partition and you don't have any backups, I suspect you will have to say goodbye to the lost files.  However you should stop using the new installation immediately and do everything I suggest here with a live CD/USB.  Boot to a live system, install testdisk and run that live, and you may be lucky and be able to retrieve some files.  I have never had to use it so can not help any more about using it, so search that out separately.

Good luck!  And in future **MAKE BACKUPS!!**

---

### Post by christon74 on 2012-07-04
Hello ajgreeny :)
Yes I think everything swap on one partition (default)
The previous 12.04 was slightly different and I had other options (it was still possible to choose Meerkat on boot _ not any longer)
I am trying to recover document files (odt or doc) I have just launched foremost and it says:
'Processing: stdin' and there is a white square that keeps flashing on and off. How long does it take for foremost to do the job?

Thanks.

---

