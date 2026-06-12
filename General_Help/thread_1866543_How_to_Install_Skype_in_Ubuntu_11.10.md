---
title: "How to Install Skype in Ubuntu 11.10?"
date: 2011-10-21
forum: General Help
---

### Post by Simeo on 2011-10-21
Hey sorry if this is redundant but I haven't been able to find a definitive answer. I have a 64-bit system and I'm trying to install Skype, but the package isn't available. 

Case in point:

```
_______________:~$ sudo apt-get install skype:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package skype:i386
_____________:~$ sudo apt-get install skype
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package skype
```

Am I doing something wrong?

---

### Post by lovinglinux on 2011-10-21
Download the 64bit from Skype web site. I have installed it yesterday.

[http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/](http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/)

---

### Post by Simeo on 2011-10-21
> **lovinglinux said:**
> Download the 64bit from Skype web site. I have installed it yesterday.

[http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/](http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/)

The ubuntu 11.04 version or .....?

---

### Post by lovinglinux on 2011-10-21
> **Simeo said:**
> The ubuntu 11.04 version or .....?

The 10.4+ will do. I have installed it on 11.10.

---

### Post by spielball on 2011-12-19
I have 64-bit, too. Downloaded the package from Skype website, as said. Installed the package. But when I start Skype, the icon in the launcher blinks and then nothing happens. No Skype coming up, nowhere to find, nada. What can I do?

---

### Post by howefield on 2011-12-19
Try launching from a terminal, you'll likely get a clue in the output.

Also, there is a skype package in the Ubuntu repositories, to get it, you'd need to enable the partner repository.

---

### Post by spielball on 2011-12-19
Thanks for that hint! Problem solved. :)

What happened?

My first try was to install it from the partner repositories, which I enabled in 'System Settings' > 'Software Sources'. This install didn't work. So I uninstalled it again.
Then I downloaded the package directly from the Skype website. However, after installation, nothing happened when I clicked the icon in the launcher. What I didn't notice is that this icon was a left-over from the previous, non-working installation. And so of course, it didn't work when clicking this icon. I have to say, this is a big flaw in Unity. The launcher should tell me when a launch-icon leads to nowhere.

Starting Skype through Terminal worked. This gave me the hint that it's there and working. And so I removed the old icon from the launcher and selected "Keep in launcher" for the new icon as Skype was running. Also, of course, I can start Skype through the Application Lens of the Dash. I just didn't know that it's there, as I thought the install went wrong.

So, everyone who wants to install Skype in 11.10, they should NOT use the package from Canonical's partner repositories, but download the installer package directly from Skype's website. By the way, 'Skype:i386' strangewise is listed double in the Software Manager's list. Something's wrong there. I hope Canonical will fix it.

---

