---
title: "Should i avoid?  12.04 LTS desktop 64x"
date: 2012-06-07
forum: General Help
---

### Post by fishbutt2 on 2012-06-07
Previously I was having trouble with my embedded ATI graphics not working.  The computer asked me to update to 12.04 so I did.

  This failed, low graphics error and then I could not click anything to continue.  I partitioned some new space and now I have a lot of problems.

  My VPN is just failed.  Works fine in other locations.  Followed forum and website instructions and 2 programs.

  Embedded HD does not work.  Both additional drivers and from the site instructions

  The network just dies.  I have been over an hour into a movie streaming and the connection just dies on me until i reboot.

And now I log in and can not authenticate installing anything.  The auto updates just fail

  Should I just be avoiding this update / system all together?

---

### Post by traditionalist on 2012-06-07
> **fishbutt2 said:**
> Previously I was having trouble with my embedded ATI graphics not working.  The computer asked me to update to 12.04 so I did.

  This failed, low graphics error and then I could not click anything to continue.  I partitioned some new space and now I have a lot of problems.

  My VPN is just failed.  Works fine in other locations.  Followed forum and website instructions and 2 programs.

  Embedded HD does not work.  Both additional drivers and from the site instructions

  The network just dies.  I have been over an hour into a movie streaming and the connection just dies on me until i reboot.

And now I log in and can not authenticate installing anything.  The auto updates just fail

  Should I just be avoiding this update / system all together?

There are problems with ATI Graphics on some machines. The generic Ubuntu drivers work best on my personal  machine for instance, running Ubuntu 12.04 Precise Pangolin, ( Don't install anything else, just use the default setup from Ubuntu), the proprietary AMD drivers are useless. Bad graphics drivers will cause all sorts of problems.

All you can do is try various things until you find one that works.  Unfortunately, all the various instructions for setting up ATI stuff ( I have tried them all!) are invariably extremely complex and don't work anyway on some machines.

---

### Post by fishbutt2 on 2012-06-07
> **traditionalist said:**
> There are problems with ATI Graphics on some machines. The generic Ubuntu drivers work best on my personal  machine for instance, running Ubuntu 12.04 Precise Pangolin, ( Don't install anything else, just use the default setup from Ubuntu), the proprietary AMD drivers are useless. Bad graphics drivers will cause all sorts of problems.

All you can do is try various things until you find one that works.  Unfortunately, all the various instructions for setting up ATI stuff ( I have tried them all!) are invariably extremely complex and don't work anyway on some machines.

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Best link, synaptic package manager is not on ubuntu since maybe 11.04?  other than that these steps work.  There is a command to fix the debian files or download them manually or type in the command to find the files.  

I might try the beginners version of linux.  The one with too much SW on it.  My machine really does not need to be streamline at all to save data and run a vent server lol.

Also trying 32bit maybe that would help?

---

### Post by traditionalist on 2012-06-07
> **fishbutt2 said:**
> [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Best link, synaptic package manager is not on ubuntu since maybe 11.04?  other than that these steps work.  There is a command to fix the debian files or download them manually or type in the command to find the files.  

I might try the beginners version of linux.  The one with too much SW on it.  My machine really does not need to be streamline at all to save data and run a vent server lol.

Also trying 32bit maybe that would help?

I tried a whole load of stuff for several weeks without success. Even when you get the drivers installed correctly they don't work. Extremely frustrating for anybody having such problems and impossible for newbies.

To get synaptic;

 ```
**sudo apt-get install synaptic**
```

---

### Post by QIII on 2012-06-07
I understand that the ATI driver has not worked for you, traditionalist.  I am still researching that.  But I would be careful saying the driver is "useless" universally.

@fishbutt:  try the method for ATI installation in my signature.  Don't add the acceleration files just yet.  I'm trying to help another poster get that sorted out for his integrated graphics.  Incidentally, he has a problem with the reported model, too.  However, I was able to determine that the driver is using the correct GPU settings, so it is working properly even though it is reported incorrectly.

Since integrated graphics are somewhat dependent on how the motherboard OEM wickers them in, odd things can happen.

---

