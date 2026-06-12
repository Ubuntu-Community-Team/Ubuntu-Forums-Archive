---
title: "Video playback in Firefox"
date: 2011-07-07
forum: General Help
---

### Post by JohnHomos on 2011-07-07
Greetings,
Whenever I try playing a video on Firefox under Ubuntu black boxes appear (especially around the controls).

I had this problem with Ubuntu 10.10. Then I tried it on a fresh installation of Ubuntu 11.04 with the same results.

What's interesting is that the video plays nicely on Chrome under Ubuntu and on FireFox under Windows.
So I'm not sure where the fault lies.

Any help is appreciated

---

### Post by An Sanct on 2011-07-07
Welcome to the forums!

Flash is a proprietary product and is included in the "non-free extras", so it is not installed in a clean install, you have to install it yourself (just like on windows). Have you tried [Flash AID]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/") for Firefox?

Windows utilize flash in a different way and Chrome (Linux) has a built in flash player (that is actually kind of creepy!)

---

### Post by nomko on 2011-07-07
I don't know why everybody is using that Flash-aid add-on for FF. Too much add-ons makes from Ff a christmas tree and slows down FF.
 
Everything you can do either by hand or through synaptic, you won't need any add-on's or similar. 
 
Just install the flashplugin-nonfree package from synaptic and you will be okay with that.
 
But what i really miss is this: are you talking about flash video's? Or any kind of video's (streaming video's)?

---

### Post by An Sanct on 2011-07-07
If you use a plugin and then see, that you really don't need it every day, you can simply disable it.

Flash AID is great and fixes Flash problems.

With installation through Synaptics I only found out, that the package is virtual and cannot be installed, also I did not see a 64b version there ...

so: 
-Install Flash AID
-startup Firefox
-wait a few seconds - if it does not prompt you, that a newer version of flash is present, click it and install flash
-optionally remove Flash AID

There: your flash problems are gone and no Firefox-christmass tree for you...

---

### Post by JohnHomos on 2011-07-07
Thank very much for the suggestions

Flash-Aid worked beautifully (and I removed it after installing the correct flash plugin)
Thanks again

---

### Post by beew on 2011-07-07
> **JohnHomos said:**
> Thank very much for the suggestions

Flash-Aid worked beautifully (and I removed it after installing the correct flash plugin)
Thanks again

Why do you remove it? It will alert you when there is a new flash update.

---

### Post by lovinglinux on 2011-07-07
> **nomko said:**
> I don't know why everybody is using that Flash-aid add-on for FF. Too much add-ons makes from Ff a christmas tree and slows down FF.
 
Everything you can do either by hand or through synaptic, you won't need any add-on's or similar. 
 
Just install the flashplugin-nonfree package from synaptic and you will be okay with that.
 
But what i really miss is this: are you talking about flash video's? Or any kind of video's (streaming video's)?

I am the developer of Flash-Aid, so I can explain exactly what it does. First, it detects flash plugin left overs from many locations and removes them. If you have multiple plugins installed on different locations, there is no way to tell which one Firefox will choose. So you might be having flash problems and trying to re-install flash or install a new version without knowing that Firefox is actually using a bad version from a different location. I have even see users with such problems, because Firefox was using a Windows version of flash from Wine drives or versions installed manually on different locations. Flash-Aid takes care of that.

Flash-Aid also detects the system architecture and install different versions accordingly. For instance, I have seen users running Firefox 32bit on a 64bit, so the plugins don't work. Flash-Aid detects if you are running a 32bit browser on a 64bit system and install the 64bit flash on the system folder, but also the 32bit on the Firefox folder, so flash works in the 32bit Firefox.

The 64bit flash installed by flashplugin-nonfree is not actually 64bit. It is a 32bit that uses a 64bit wrapper. So, sometimes it doesn't work as expected. Flash-Aid offers the option to install the 64bit from Adobe labs as well as the 32bit version from the repositories.

Sometimes, users complain that Flash works on Chrome and not on Firefox. Flash-Aid can detect if you have Chrome 32bit installed and offers the option to use the flash plugin bundled with Chrome with Firefox too.

Depending on the Ubuntu version you have and the architecture, there are some common problems that can be solved by editing some config files. For example the bug that affects 64bit users, making impossible to use flash controls. Flash-Aid detects if don't have the bug fix and applies it for you. 

Flash has terrible performance, but Flash-Aid can detect if you have a config tweak that forces hardware acceleration. If not, it offers to apply it. It also detects if you have vdpau installed and make the necessary changes so Flash can use it for increased performance.

It is true that too many add-ons can slow down Firefox. But that depends on the type of add-ons you have. Flash-Aid doesn't overload your Firefox, because it practically does nothing without user interaction. It only checks some system paths and Ubuntu version when you start Firefox. Once a day, it downloads a very tiny json from my site, to check if there is a new Flash version available, but you can turn that off in the preferences.

If you don't care about being notified when a new beta version of flash is available or if you choose the repository version, then you can turn Flash-Aid off and only enable it when you need to install a new version or try a different one.

Anyway, I have 55 add-ons installed on my personal profile and Firefox runs just fine. However, I select my add-ons very carefully and disable them with any sign of trouble. Additionally, I do regular maintenance on my Firefox profile.

It is true that you can accomplish most of what Flash-Aid does via command-line, after all Flash-Aid is essentially a script generator. However, it does most of the hard work for you, without the need to troubleshoot your flash problems.

The idea behind Flash-Aid is to make easy for newcomers to install Flash and solve common issues without wasting any time troubleshooting it. Because of that, it has a Wizard that is very easy to use. However, it also has an Advanced mode, that allows to preview the commands and Quick Modes if you like the default settings.

I hope this clarifies your question.

---

### Post by nomko on 2011-07-07
Okay, nice explanation.
 
But then this: [http://ubuntuforums.org/showthread.php?p=11015613#post11015613](http://ubuntuforums.org/showthread.php?p=11015613#post11015613)
 
Check the postings of alfu. And i have similar issue with flash-aid. After removing it my system is responding very strang on flash video's and my system is more or less on crawling mode now. Before installing Flash-aid i didn't had any of these issue's. Familiar?

---

### Post by lovinglinux on 2011-07-07
> **nomko said:**
> Okay, nice explanation.
 
But then this: [http://ubuntuforums.org/showthread.php?p=11015613#post11015613](http://ubuntuforums.org/showthread.php?p=11015613#post11015613)
 
Check the postings of alfu. And i have similar issue with flash-aid. After removing it my system is responding very strang on flash video's and my system is more or less on crawling mode now. Before installing Flash-aid i didn't had any of these issue's. Familiar?

Please install Flash-Aid again, click the Help menu and generate a report. Paste the contents of the report, so I can analyse your particular situation.

About the other thread, I will reply there.

---

### Post by nomko on 2011-07-07
> **lovinglinux said:**
> Please install Flash-Aid again, click the Help menu and generate a report. Paste the contents of the report, so I can analyse your particular situation.
 
About the other thread, I will reply there.
 
I'll do that tonight. I'm i Holland an dit's now 12:10 pm.
I post the report here!

---

### Post by lovinglinux on 2011-07-07
> **nomko said:**
> I'll do that tonight. I'm i Holland an dit's now 12:10 pm.
I post the report here!

Okay, I watching this thread, so any reply will show up in my control panel.

---

### Post by lovinglinux on 2011-07-07
If you are experiencing problems on Youtube only, then see [YouTube Problems Mega Thread]("http://ubuntuforums.org/showthread.php?t=1799217")

---

### Post by nomko on 2011-07-07
> **lovinglinux said:**
> Okay, I watching this thread, so any reply will show up in my control panel.

Okay, my report is attached!

---

### Post by lovinglinux on 2011-07-07
> **nomko said:**
> Okay, my report is attached!

It seems you have two instances of flash installed. Please execute Flash-Aid Wizard again. Post a new report.

If you still experience problems after that, execute the Wizard again, but disable the option to "Override GPU validation" in the tweaking section.

---

### Post by nomko on 2011-07-08
> **lovinglinux said:**
> It seems you have two instances of flash installed. Please execute Flash-Aid Wizard again. Post a new report.
 
If you still experience problems after that, execute the Wizard again, but disable the option to "Override GPU validation" in the tweaking section.
 
Ah, that could be the problem then. I'll do it tonigth and create a new report.
 
There's 1 thing you could change, in order to get the report i had to make a folder called Desktop since i'm using Ubuntu with the Dutch language. And in Dutch *desktop* is *bureaublad*. So, the program couldn't make the report first, after creating a folder called desktop the report could be made. Maybe you could change the script in such way that the report will be created in /home/{username}/ instead of /home/{username}/desktop.

---

### Post by lovinglinux on 2011-07-08
> **nomko said:**
> Ah, that could be the problem then. I'll do it tonigth and create a new report.
 
There's 1 thing you could change, in order to get the report i had to make a folder called Desktop since i'm using Ubuntu with the Dutch language. And in Dutch *desktop* is *bureaublad*. So, the program couldn't make the report first, after creating a folder called desktop the report could be made. Maybe you could change the script in such way that the report will be created in /home/{username}/ instead of /home/{username}/desktop.

That's odd, because it uses a Firefox component to save to the desktop, which does not depend on localization.

---

### Post by nomko on 2011-07-08
1) I had to create that folder, otherwise it doesn't work.

2) new report attached

---

### Post by lovinglinux on 2011-07-08
> **nomko said:**
> 1) I had to create that folder, otherwise it doesn't work.

2) new report attached

Your report is fine now. Do you see any difference in playback?

---

### Post by nomko on 2011-07-09
> **lovinglinux said:**
> Your report is fine now. Do you see any difference in playback?

What i experience now is that i can't play youtube movies full screen. Before installing Flash-aid i could play them full screen, after installing them i cannot.

---

### Post by lovinglinux on 2011-07-09
> **nomko said:**
> What i experience now is that i can't play youtube movies full screen. Before installing Flash-aid i could play them full screen, after installing them i cannot.

Have you deselected the option to Override GPU validation?

---

### Post by nomko on 2011-07-10
I did that  and it works! Thanks!

---

### Post by lovinglinux on 2011-07-10
> **nomko said:**
> I did that  and it works! Thanks!

Great.

---

