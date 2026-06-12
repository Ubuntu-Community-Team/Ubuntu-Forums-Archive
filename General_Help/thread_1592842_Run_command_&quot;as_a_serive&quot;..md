---
title: "Run command &quot;as a serive&quot;."
date: 2010-10-11
forum: General Help
---

### Post by zespri on 2010-10-11
Hello All,

sometimes you want to run a command every time computer boots up. In DOS there is "autoexec.bat" in windows - "Startup" menu and I'm sure that there is a similar thing exists for Ubuntu, but that's not what I'm after.

These things above will run a command when a user logs on. I want to run a command when a pc boots up. This is not straightforward in Windows, but since I'm a windows guy I can do this. I can install a command as a service with srvany utility that will make sure it will execute on boot up.

Now I want to do a similar thing in ubuntu. I googled a lot but I was not able to find a solution that worked for me.

Could someone please share how do I edit startup scripts in ubuntu to add an arbitrary command? I need to run the command in the context of a particular user, so I normally do it like this:

```
sudo -u myServiceUser -i myService
```

But I want as little downtime as possible and sometimes it takes sometime to find out that there has been a reboot, get to a computer and run the command manually. If I could run this automatically on bootup I wouldn't have this problem.

Thank you in advance,
Andrew

---

### Post by lloyd_b on 2010-10-11
> **zespri said:**
> Hello All,

sometimes you want to run a command every time computer boots up. In DOS there is "autoexec.bat" in windows - "Startup" menu and I'm sure that there is a similar thing exists for Ubuntu, but that's not what I'm after.

These things above will run a command when a user logs on. I want to run a command when a pc boots up. This is not straightforward in Windows, but since I'm a windows guy I can do this. I can install a command as a service with srvany utility that will make sure it will execute on boot up.

Now I want to do a similar thing in ubuntu. I googled a lot but I was not able to find a solution that worked for me.

Could someone please share how do I edit startup scripts in ubuntu to add an arbitrary command? I need to run the command in the context of a particular user, so I normally do it like this:

```
sudo -u myServiceUser -i myService
```

But I want as little downtime as possible and sometimes it takes sometime to find out that there has been a reboot, get to a computer and run the command manually. If I could run this automatically on bootup I wouldn't have this problem.

Thank you in advance,
Andrew

Take a look at [this page]("https://help.ubuntu.com/community/RcLocalHowto") - I believe it explains exactly what you want to do.

Lloyd B.

---

### Post by zespri on 2010-10-11
Yes, this worked. Thank you.

---

