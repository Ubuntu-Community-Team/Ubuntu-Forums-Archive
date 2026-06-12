---
title: "unable to see shared folders in vmware player"
date: 2009-09-04
forum: General Help
---

### Post by misha680 on 2009-09-04
Dear All:

I am trying VMWare Player 2.5.3 build-185404.

I added the following lines to my vmx file:
```

# For shared folders
isolation.tools.hgfs.disable = "FALSE"

sharedFolder.maxNum = "2"

sharedFolder0.present = "TRUE"
sharedFolder0.enabled = "TRUE"
sharedFolder0.readAccess = "TRUE"
sharedFolder0.writeAccess = "TRUE"
sharedFolder0.hostPath = "/"
sharedFolder0.guestName = "root"
sharedFolder0.expiration = "never"

sharedFolder1.present = "TRUE"
sharedFolder1.enabled = "TRUE"
sharedFolder1.readAccess = "TRUE"
sharedFolder1.writeAccess = "TRUE"
sharedFolder1.hostPath = "/home/misha"
sharedFolder1.guestName = "home"
sharedFolder1.expiration = "never"

```

I am able to see shared folders as you can see from the screenshot in VMWare player. However, they do not appear in the guest (WinXP 64). Any help much appreciated. I am trying to use this vs Samba in Server as Samba seems to have problems with Office. Thank you.

[http://people.hnl.bcm.edu/misha/tmp/vmware.png](http://people.hnl.bcm.edu/misha/tmp/vmware.png)

Thank you
Misha

---

### Post by mr_shedges on 2009-09-11
right there with you man, been googling it for about two days now. why is it things that seem so obvious always end up being the hardest, like dial up in ubuntu 9.04. ahhh.

Please if anyine has an answer chuck it here.

If we can knock it out happy to create a small how to and post. I have also figured out how to change the settings in the vmx file to enable usb 2.0 support. The answer to the blue screen of death when working with iPhone/ iTunes faff. i'll chuck that in there to.

Cheers

---

### Post by misha680 on 2009-09-11
> **mr_shedges said:**
> right there with you man, been googling it for about two days now. why is it things that seem so obvious always end up being the hardest, like dial up in ubuntu 9.04. ahhh.

Please if anyine has an answer chuck it here.

If we can knock it out happy to create a small how to and post. I have also figured out how to change the settings in the vmx file to enable usb 2.0 support. The answer to the blue screen of death when working with iPhone/ iTunes faff. i'll chuck that in there to.

Cheers

I think the trick is a follows.

Get a VMWare Workstation evaluation copy (free):
[https://www.vmware.com/tryvmware/?p=workstation-l](https://www.vmware.com/tryvmware/?p=workstation-l)

Upgrade VMWare Tools.

Then I believe you will see shared folders in VMWare Player.

I will note a _big_ caveat with shared folders is symlinks don't work.

Let me know if this works.

Thanks
Misha

---

