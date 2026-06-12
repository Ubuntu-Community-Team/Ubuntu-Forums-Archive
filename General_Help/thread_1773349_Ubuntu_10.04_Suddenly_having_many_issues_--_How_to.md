---
title: "Ubuntu 10.04 Suddenly having many issues -- How to diagnose problem?"
date: 2011-06-01
forum: General Help
---

### Post by Dante311 on 2011-06-01
I have been using Ubuntu 10.04 for a couple months now and all had been doing well until recently.  Upon start up about a week ago, it would freeze and flash the cursor at the top without continuing to load.  I wasn't even given the option to choose how to start up since I'm using dual-boot.

I was able to get around this by pressing the power key once and it skipped to start up but now I'm having a host of other issues.  All my fonts seem to be messed up and returning them to what I've read are defaults doesn't look right either.

I am frequently finding programs freeze up now and am forced to restart.  When I look at system monitor, my CPU2 is running at 100% all the time.  It's behaving a lot like windows now :S.

I am not a computer nor Ubuntu expert.  How can I diagnose and hopefully fix this issue?  I am guessing there must be an update or something I downloaded that caused all this to happen at once.

Thanks in advance!

---

### Post by wlraider70 on 2011-06-01
1. backup your files, better safe then sorry.

2. if you can get into ubuntu got to /var/log/syslog and post some logs. look for errors. You can also run 
$ cat /var/log/syslog | grep error

---

### Post by Dante311 on 2011-06-02
Here is what I get when I run the second command:

quentin@quentin-laptop:~$ cat /var/log/syslog | grep error
Jun  1 17:44:52 quentin-laptop kernel: [   16.384654] radeon 0000:01:00.0: Fatal error during GPU init
Jun  1 17:44:52 quentin-laptop kernel: [   16.467631] radeon: probe of 0000:01:00.0 failed with error -22
Jun  1 17:44:53 quentin-laptop NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
Jun  1 21:58:48 quentin-laptop NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
Jun  1 21:58:49 quentin-laptop kernel: [   19.621597] radeon 0000:01:00.0: Fatal error during GPU init
Jun  1 21:58:49 quentin-laptop kernel: [   19.627761] radeon: probe of 0000:01:00.0 failed with error -22
Jun  1 22:08:42 quentin-laptop NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
Jun  1 22:08:44 quentin-laptop kernel: [   19.481544] radeon 0000:01:00.0: Fatal error during GPU init
Jun  1 22:08:44 quentin-laptop kernel: [   19.481719] radeon: probe of 0000:01:00.0 failed with error -22

I'm not sure how to post the logs you had mentioned.

---

### Post by wildmanne39 on 2011-06-02
> **Dante311 said:**
> Here is what I get when I run the second command:

quentin@quentin-laptop:~$ cat /var/log/syslog | grep error
Jun  1 17:44:52 quentin-laptop kernel: [   16.384654] radeon 0000:01:00.0: Fatal error during GPU init
Jun  1 17:44:52 quentin-laptop kernel: [   16.467631] radeon: probe of 0000:01:00.0 failed with error -22
Jun  1 17:44:53 quentin-laptop NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
Jun  1 21:58:48 quentin-laptop NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
Jun  1 21:58:49 quentin-laptop kernel: [   19.621597] radeon 0000:01:00.0: Fatal error during GPU init
Jun  1 21:58:49 quentin-laptop kernel: [   19.627761] radeon: probe of 0000:01:00.0 failed with error -22
Jun  1 22:08:42 quentin-laptop NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
Jun  1 22:08:44 quentin-laptop kernel: [   19.481544] radeon 0000:01:00.0: Fatal error during GPU init
Jun  1 22:08:44 quentin-laptop kernel: [   19.481719] radeon: probe of 0000:01:00.0 failed with error -22

I'm not sure how to post the logs you had mentioned.
Hi, did you install a  new driver for your video card it says it failed.

---

### Post by Dante311 on 2011-06-02
Not that I am aware of.  I saw that as well and checked to see if my driver was turned on in "Hardware Drivers" and it is not(I had been having issues with turning the driver on before).  So unless it was updated somehow with update manager I didn't update it.

---

### Post by wildmanne39 on 2011-06-02
> **Dante311 said:**
> Not that I am aware of.  I saw that as well and checked to see if my driver was turned on in "Hardware Drivers" and it is not(I had been having issues with turning the driver on before).  So unless it was updated somehow with update manager I didn't update it.Hi, did it show that there is a driver to activate? if so activate it, it might have got disabled some how.

---

### Post by Dante311 on 2011-06-02
I have not activated the driver because when I freshly dual-booted my computer, activating the driver would cause problems in XP.  My Ubuntu set-up was working fine without it activated before.

---

### Post by wildmanne39 on 2011-06-02
> **Dante311 said:**
> I have not activated the driver because when I freshly dual-booted my computer, activating the driver would cause problems in XP.  My Ubuntu set-up was working fine without it activated before.

Hi. ok I am out of ideas if you can not activate the driver, that is the only thing that I see would be the problem, unless your video card failed but I am sure it still works in xp, unless something really weird happened activating the driver would not effect xp, it might if you are running it in a wubi install but other then that it would have to have been a very strange situation. I am sorry that I do not have the answer.

---

### Post by wildmanne39 on 2011-06-02
> **Dante311 said:**
> I have not activated the driver because when I freshly dual-booted my computer, activating the driver would cause problems in XP.  My Ubuntu set-up was working fine without it activated before.

Hi, one last thought with all the problems your are having if it is not a hardware failure I think you should reinstall ubuuntu you can save your personal documents and pics and things to and external drive but wipe everything out and reinstall by reformatting that partition ubuntu is on do not just reinstall over the old ubuntu that will most likely cause more problems.

---

### Post by dFlyer on 2011-06-02
I would agree that you should back up any important files to be safe. I don't know if this could be your problem or not but could you go to disk utility and see if you have any back sectors. Sounds like I had a many years back, when I was dual booting. Windows would boot and linux would crash. I ended up having bad cluster/sectors on the hd.

---

### Post by Dante311 on 2011-06-03
I did does say I have some bad sectors.  Not certain this is the cause of my problem but I attached the screenshot for those that know better than I how to read it.

---

### Post by wildmanne39 on 2011-06-03
> **Dante311 said:**
> I did does say I have some bad sectors.  Not certain this is the cause of my problem but I attached the screenshot for those that know better than I how to read it.
Hi, a few bad sectors is normal to some degree, but you probably have files in those bad sectors, if you reformat your hard drive it will try to repair them and if it cant it will block those sectors out so no more data will go there and you should be fine after a reinstall, also keep a check on it but with disk utility if you are about to have a hard drive failure it will tell you unless it quits all at once.

---

### Post by Dante311 on 2011-07-09
The story continues...

I had decided to bring my laptop into a local guy to diagnose and he found nothing to be wrong with the HD itself.  He had reset the BIOS and it had been working fine for the last month.

However, now the same issue is happening again.  It appears to start happening out of nowhere.  I can still load into my WinXP partition(which I am typing from now), but my Ubuntu won't boot.  I just have the black screen after selecting it.

Why would resetting BIOS have fixed the problem?

I appreciate the help.

---

