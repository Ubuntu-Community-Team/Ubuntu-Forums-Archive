---
title: "Firefox Issue (Adblock and Flash)"
date: 2011-10-02
forum: General Help
---

### Post by shad0w7 on 2011-10-02
My firefox is really slow especially when viewing flash movies online, like youtube. I installed "flash-aid" and then I went to "quick mode > install stable version", but it seems that when i restart firefox nothing changes, and the option to install it is still there. Plus I installed "Adblock", but it doesn't seem to work since, I visit the same websites i did before and the ads are still there. It is like I am installing add-ons on firefox but nothing happens.
As for the flash problem, is due tomy graphics card drivers? i have a nvidia 9600m gt. What is the command to update it?

---

### Post by Frogs Hair on 2011-10-02
I don't think it is the card its self  because my 8 series Nvidia card works fine . Open additional drivers and install the Nvidia current recommended driver if not already .

With Flash Aid quick mode you may want to  install the beta flash version to see if it preforms any better . Adblock should have no effect when watching movies .

---

### Post by pqwoerituytrueiwoq on 2011-10-02
to update the gpu drivers
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates;sudo apt-get update;sudo apt-get upgrade;
```look into enabling vdpau if you are using 10.04 it is default in 10.10+
@[Frogs Hair]("http://ubuntuforums.org/member.php?u=1024576")
the next flash version is not a beta it is a release candidate (for now anyway)

---

### Post by Frogs Hair on 2011-10-02
> @[Frogs Hair]("http://ubuntuforums.org/member.php?u=1024576")
the next flash version is not a beta it is a release candidate (for now anyway)

Thanks ! , the options in Flash Aid appear as stable or beta .

---

### Post by lovinglinux on 2011-10-04
> **Frogs Hair said:**
> Thanks ! , the options in Flash Aid appear as stable or beta .

I have named Beta and Stable for convenience, but the current version is the Release Candidate. Flash-Aid will get it as well, if you select the Beta option.

About the option to install being still there is because Flash-Aid always remove all plugins and install again when you click the Wizard. However, it doesn't mean it isn't installed. Take a look at the Removal Options in the wizard. If flash is installed, it will be listed there.

Please click Flash-Aid menu, select "Help >> Generate Report" and post the report here, so I can take a look.

About AdBlock, you need to subscribe to a filter list (I recommend Easy List) or create your own filters.You can do that from the extension preferences.

---

