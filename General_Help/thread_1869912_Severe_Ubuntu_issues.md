---
title: "Severe Ubuntu issues"
date: 2011-10-26
forum: General Help
---

### Post by jbergen1104 on 2011-10-26
Hello, everyone.
I seem to be having trouble with my Ubuntu computer which I am fairly new to using. I never did the installation, my step father did. I know nothing of all the technical stuff such as running command lines through the terminal and usually when I do it, it makes everything worse. So, one to my problem:

A few weeks ago my computer began to have issues applying screen resolutions correctly. My monitor supports up to 1024x768 resolution. Well, my computer stopped being able to apply 1024x768 and began applying 640x480. No matter what. I tried to change the resolution, but the only available resolution was 640x480 and 320x240. 
Well, after weeks of not really caring, I moved into an apartment and when I hooked up my computer it worked on 1024x768 again and no problems at all.
Then just 2 days ago the resolution was reset back to 640x480 again and refused to go back to 1024x768. And whenever I logged in it would say "[COLOR="Red"]Could not apply stored configuration to monitor[/COLOR]."

So, I finally decided to look up help in Google and I found someone with the same issue. One of the answers was to delete something like "[COLOR="red"]Monitors.xml[/COLOR]"(I think that's what it was called) and then reboot the computer. The asker was praising the answer thanking them because it work. So, I tried it and when I rebooted my computer, after the Ubuntu logo it goes to a black screen and says "[COLOR="red"]VGA MODE NOT SUPPORT[/COLOR]" And it never gets past that. I was stuck without a computer for a long time until I finally got access to someone elses computer to look up the issue. I still could not find a fix, however, I was able to find out how to boot my computer in failsafe graphics mode. But many of my features have been removed and I'm desperate to find a fix. Can anyone *please* help me?
I've highlighted the important parts in case you decide to skim through it.

---

### Post by soumyabratapaul on 2011-10-26
> **jbergen1104 said:**
> Hello, everyone.
I seem to be having trouble with my Ubuntu computer which I am fairly new to using. I never did the installation, my step father did. I know nothing of all the technical stuff such as running command lines through the terminal and usually when I do it, it makes everything worse. So, one to my problem:

A few weeks ago my computer began to have issues applying screen resolutions correctly. My monitor supports up to 1024x768 resolution. Well, my computer stopped being able to apply 1024x768 and began applying 640x480. No matter what. I tried to change the resolution, but the only available resolution was 640x480 and 320x240. 
Well, after weeks of not really caring, I moved into an apartment and when I hooked up my computer it worked on 1024x768 again and no problems at all.
Then just 2 days ago the resolution was reset back to 640x480 again and refused to go back to 1024x768. And whenever I logged in it would say "[COLOR="Red"]Could not apply stored configuration to monitor[/COLOR]."

So, I finally decided to look up help in Google and I found someone with the same issue. One of the answers was to delete something like "[COLOR="red"]Monitors.xml[/COLOR]"(I think that's what it was called) and then reboot the computer. The asker was praising the answer thanking them because it work. So, I tried it and when I rebooted my computer, after the Ubuntu logo it goes to a black screen and says "[COLOR="red"]VGA MODE NOT SUPPORT[/COLOR]" And it never gets past that. I was stuck without a computer for a long time until I finally got access to someone elses computer to look up the issue. I still could not find a fix, however, I was able to find out how to boot my computer in failsafe graphics mode. But many of my features have been removed and I'm desperate to find a fix. Can anyone *please* help me?
I've highlighted the important parts in case you decide to skim through it.

Open the terminal by pressing Alt + Ctrl + T simultaneously. Then enter this command

```
sudo nvidia-xconfig
```

After this is done then again enter this command.

```
gksudo nvidia-settings
```

See if this works.

P.S. : You should know your password, because sudo is going to ask for it.

---

### Post by grahammechanical on 2011-10-26
May I also suggest that you check that the machine is not overheating because of air vents blocked by dust and fluff.

You could have a video card that is breaking down due to overheating. I had this.

The OS gets the monitor display mode from the monitor but through the video card. If the video card is unable to read the monitor configuration settings then the OS (or what is called the Xserver) is guessing the video. This in turn messes up the configuration files that are used to drive the monitor.

Regards.

---

### Post by jbergen1104 on 2011-10-26
> **soumyabratapaul said:**
> Open the terminal by pressing Alt + Ctrl + T simultaneously. Then enter this command

```
sudo nvidia-xconfig
```

After this is done then again enter this command.

```
gksudo nvidia-settings
```

See if this works.

P.S. : You should know your password, because sudo is going to ask for it.Thank you very much for your response, however, this did not change anything. I've taken a screen shot of what happens when I entered the above in the terminal as well as recorded a video of what happens while booting the computer up.
[Video Here]("http://www.youtube.com/watch?v=G2u2JT-8Cy4")
[IMG]http://i42.tinypic.com/2uji5g2.png[/IMG]
\\
PS: I was also able to launch a failsafe graphics mode that uses 1024x768, but it's still unable to run many things such as 3D games and certain sites. So, it's the same old failsafe but with higher resolution.

---

### Post by jbergen1104 on 2011-10-26
> **grahammechanical said:**
> May I also suggest that you check that the machine is not overheating because of air vents blocked by dust and fluff.

You could have a video card that is breaking down due to overheating. I had this.

The OS gets the monitor display mode from the monitor but through the video card. If the video card is unable to read the monitor configuration settings then the OS (or what is called the Xserver) is guessing the video. This in turn messes up the configuration files that are used to drive the monitor.

Regards.
Thanks so much for your reply. Yes, I've verified that the ventilation is clear and nothing is stuck in it or on it or blocking the way. There's about 1.5 Ft of space from the back of the computer to the wall.

---

### Post by Atamisk on 2011-10-26
You need to reboot (or at least logout and log back in) after you run nvidia-xconfig. 

Try to reboot and See What Happens (tm).

---

### Post by jbergen1104 on 2011-10-26
> **Atamisk said:**
> You need to reboot (or at least logout and log back in) after you run nvidia-xconfig. 

Try to reboot and See What Happens (tm).

That's precisely what I did. I ran it through the terminal and then rebooted. I always get the same result. I'm fairly hopeless now. I think this computer is doomed.

---

### Post by oldtimer7777 on 2011-10-26
> **jbergen1104 said:**
> That's precisely what I did. I ran it through the terminal and then rebooted. I always get the same result. I'm fairly hopeless now. I think this computer is doomed.

What I did when I had a problem like this is run:

sudo jockey-gtk

from the terminal.. and then I uninstalled the proprietary video driver.. Rebooted.. and then reinstalled it with 

sudo jockey-gtk

Maybe it is worth a try.. :)

---

