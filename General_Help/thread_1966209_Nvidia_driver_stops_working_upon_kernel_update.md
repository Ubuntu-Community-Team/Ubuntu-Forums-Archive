---
title: "Nvidia driver stops working upon kernel update"
date: 2012-04-26
forum: General Help
---

### Post by josephellengar on 2012-04-26
Hi. With the last kernel update (to 3.2.0-24-generic) my Nvidia driver stopped working. I was unable to use either the version current or the post-release update version (neither would install) and my screen resolution dropped to 1024x768 from the normal 1600x900. To fix this I had to go back to 3.2.0-23-generic, and now it works fine. 

Any idea why this would be? I am attaching the logfile for the driver installation process (zipped because the text file was too large to upload). Jockey-gtk would simply say "installation failed" whenever I tried to upload either one.

Note, probably unrelated: I also couldn't suspend with the new kernel, but didn't put much time into debugging it.

---

### Post by techsupport on 2012-04-26
> **josephellengar said:**
> Hi. With the last kernel update (to 3.2.0-24-generic) my Nvidia driver stopped working. I was unable to use either the version current or the post-release update version (neither would install) and my screen resolution dropped to 1024x768 from the normal 1600x900. To fix this I had to go back to 3.2.0-23-generic, and now it works fine. 

Any idea why this would be? I am attaching the logfile for the driver installation process (zipped because the text file was too large to upload). Jockey-gtk would simply say "installation failed" whenever I tried to upload either one.

Note, probably unrelated: I also couldn't suspend with the new kernel, but didn't put much time into debugging it.

There is a bug with that video driver. Drop to Ubuntu 2D session until it is eventually patched very soon, or you can try switching to GDM instead of LightDM. ):P

---

### Post by josephellengar on 2012-04-26
> **techsupport said:**
> There is a bug with that video driver. Drop to Ubuntu 2D session until it is eventually patched very soon, or you can try switching to GDM instead of LightDM. ):P

Thanks. Do you know where I can find the bug on launchpad so I can subscribe? I've got my lightdm setup exactly how I like it, so I don't want to switch. Also, any idea how long very soon will be?

Thanks!

---

### Post by UltimateCat on 2012-04-26
If your running Ultimate Edition that group can help-
They helped me:

ultimateditionoz.com

---

### Post by wojox on 2012-04-26
> **josephellengar said:**
> Hi. With the last kernel update (to 3.2.0-24-generic) my Nvidia driver stopped working.

Your not using the supported kernel? Where is that kernel update from?

---

### Post by josephellengar on 2012-04-26
> **wojox said:**
> Your not using the supported kernel? Where is that kernel update from?

This is the supported kernel. I'm running 12.04. The update came through update manager. No additional repos enabled except for the one for Google Chrome.

---

### Post by techsupport on 2012-04-26
I didn't bookmark it, but it is over in Launchpad. 

You can either use Ubuntu 2D session or uninstall lightdm and install gdm instead until they can get the problem patched.  Who knows how long that might take, I don't know.

---

### Post by NoNameWill on 2012-04-26
Or just rollback to the 295.33 or earlier nvidia driver.

---

### Post by josephellengar on 2012-04-26
> **techsupport said:**
> I didn't bookmark it, but it is over in Launchpad. 

You can either use Ubuntu 2D session or uninstall lightdm and install gdm instead until they can get the problem patched.  Who knows how long that might take, I don't know.

gdm solves the problem?

---

### Post by techsupport on 2012-04-26
> **josephellengar said:**
> gdm solves the problem?

affirmative :guitar:

---

### Post by josephellengar on 2012-04-26
> **techsupport said:**
> affirmative :guitar:

Hmm, just went back to kernel 3.2.0-24-generic and installed gdm. Didn't solve the problem. Driver still wouldn't install. :(

EDIT: Is there anything else I should try? Do I have to do something from within gdm?

---

### Post by techsupport on 2012-04-26
> **josephellengar said:**
> Hmm, just went back to kernel 3.2.0-24-generic and installed gdm. Didn't solve the problem. Driver still wouldn't install. :(

I read that other users had some success with older video drivers and switching to gdm and uninstalling lightdm.  Other than that, your only option is to drop to Ubuntu 2D and wait it out for now.

---

### Post by NoNameWill on 2012-04-26
Roll the driver back the Nvidia driver 295.40 is not working in any debian based distro. 

Nvidia drivers are pain in the rear regardless of the windowing manager. The 11.xx version of ubuntu lulled people in to a false sense with nvidia driver. ):P

[http://ubuntuforums.org/showpost.php?p=11865859&postcount=5](http://ubuntuforums.org/showpost.php?p=11865859&postcount=5)

replace the last command with you version of the 295.33 driver (i.e. 32 or 64 bit)

---

### Post by NoNameWill on 2012-04-26
> **techsupport said:**
> I read that other users had some success with other video drivers and switching to gdm and uninstalling lightdm.  Other than that, your only option is to drop to Ubuntu 2D and wait it out for now.

Stop saying that. That is BS. ):P I am using the 295.33 driver rocking 3d unity. :popcorn:

---

### Post by josephellengar on 2012-04-26
Well, thanks for all of the help guys. Personally, I don't mind not having the latest and greatest kernel and with the 3.2.0-23 kernel, there are no problems at all with the most recent driver, so I'll just stick with that for now. No reason to mess with the system too much. But I really appreciate the help. I'll mark the thread solved.

---

### Post by techsupport on 2012-04-26
> **NoNameWill said:**
> Stop saying that. That is BS. ):P I am using the 295.33 driver rocking 3d unity. :popcorn:
I'm not talking about your video driver. I'm talking about the other video drivers, but whatever. 

I sure hope they fix this soon. This really sucks.

---

