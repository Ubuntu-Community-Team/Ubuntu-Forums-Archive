---
title: "Desktop effects work for one user, but unable to be enabled for other users"
date: 2009-10-23
forum: General Help
---

### Post by ptrinder64 on 2009-10-23
Hi,

I seem to be having problems with my Compiz desktop effects. Whilst they work for one user, for some unknown reason they have stopped working for another. Even after selecting **Appearance > Visual Effects > Normal/Extra** it just attempts to search for the driver and then states that 'Desktop effects could not be enabled'.

I have tried searching the forums and using a few solutions but with no effect. The problem seemed to kick off really in the last week. It was working fine before this. My instant reaction therefore is that it may be something I upgraded, but would have thought this would have effected other users too.

Any help is greatly appreciated!

---

### Post by ptrinder64 on 2009-10-24
To clarify this was after an update last week.

For some reason my wife's account seems to work fine with Compiz running as it should do, but my account doesn't. 

When I run compiz in the terminal on my account I get the following error:

```
/usr/bin/compiz.real (core) - Error: Could not acquire compositing manager selection on screen 0 display ":0.0"
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

```

When I do the same in my wife's account it seems to run perfectly, although the following entry in the terminal looks suspect to me:

```
*** glibc detected *** /usr/bin/compiz.real: double free or corruption (!prev): 0x09b21868 ***
```

Does anyone have any ideas? I'm running Ubuntu 9.04 with an Nvidia GeForce 8400 GS card, and the NVIDIA driver 180...

---

### Post by ptrinder64 on 2009-10-27
I may have stumbled across the solution to getting desktop effects working again. I noticed that when I logged into the user for whom Compiz was working, the backend preference was set to **GConf Configuration Backend**. When I logged into the user for which Compiz was not working, this was set to **Flat-file Configuration Backend**. This is located in **System > Preferences > CompizConfig Settings Manager** and then click on **Preferences** which is located just above **Advanced Search** which in turn is above the close button. Change the backend configuration to GConf.

With this changed, I then came across this thread [http://ubuntuforums.org/showthread.php?t=1232865]("http://ubuntuforums.org/showthread.php?t=1232865") which basically states to go into gconf (**Applications > System Tools > Configuration Editor**) then select **Apps > Metacity > General** and unticking the **Compositing_Manager** box.

Now go back to the **Appearances** option and click on **Extra**.

This fixed it for me.

---

