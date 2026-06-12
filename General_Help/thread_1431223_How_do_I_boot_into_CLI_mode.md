---
title: "How do I boot into CLI mode?"
date: 2010-03-16
forum: General Help
---

### Post by nl4m on 2010-03-16
I would like to know how do I get my Ubuntu 9.10 OS to boot into the command promp. Something along the lines of what you get when you hit CTRL+ALT+F1. 

What I have done so far is:
1. Made a "inittab" file and wrote in it :id:S:initdefault: (something like that, did not work).
2. "sudo update-rc.d -f gdm remove" (did not work)
3. Write in the rc.local script "/etc/init.d/gdm stop"  (this killed the system all together).
4. "sudo chmod a-x /etc/init.d/gdm" (did not work)
5. Write in the file ~/bashrc "sudo /etc/init.d/gdm stop 1>&2" (it takes me to the command promp after the gdm loads, and I open the gnome terminal).
6. I tried to edit the /etc/default file to add "GRUB_CMDLINE_LINUX_DEFAULT="quiet splash text" (did not work. The file does not exist).
7. Lastly I found online that you can stop GDM from starting up from the "services-admin" program. Only that program was taken out in 9.10.

Is there anyway to boot into the command line promp, without deleting the GDM? The only other way I found to boot into a select "Recovery Mode" from the Grub menu as a default boot. That, too, does not boot me into a command promp directly. It boots into that blue screen (no pun intended. hahahaha... Linux has a blue screen:) ) with the options. Any advice?

---

### Post by slakkie on 2010-03-16
Remove gdm?

or *update-rc.d -f gdm remove* which will remove it from /etc/rc?.d/ and thus not start the service.

If you are using karmic, you probably have upstart and then you need to remove the gdm entry there. See also: [http://joeb454.ubuntuforums.org/showpost.php?p=8168164&postcount=2](http://joeb454.ubuntuforums.org/showpost.php?p=8168164&postcount=2)

---

### Post by nl4m on 2010-03-16
I do not want to remove GDM. I am scared that I may not be able to get it back again. 

The tried the whole "*update-rc.d -f gdm remove*"  thing but it did not work. I'll try your link now.

P.S. I don't know if it helps but I did not do a clean install of 9.10. I began with 8.04 and just updated it. Can it be that the OS is still using some components on it's older distro's?

P.P.S.S. When I do the "telinit 1,2,3,4,5...." the screen goes black and freezes. When I do it through the ctrl+alt+f1 command promp it freezes too after gives me alot of I/O error messages.

---

### Post by slakkie on 2010-03-16
> **nl4m said:**
> I do not want to remove. I am scared that I may not be able to get it back again. 

The "*update-rc.d -f gdm remove*" tried it but it did not work. I will try your link.

P.S. I don't know if it helps but I did not do a clean install of 9.10. I began with 8.04 and just updated it. can it be that the OS is still using some components on it's older distro's?

Remove it, if you want it back:

sudo aptitude install gdm

No biggy at all.

And you need to use the link, since in karmic gdm got moved to upstart. And no, it is not using old stuff :)

---

### Post by nl4m on 2010-03-16
I've had Linux go bad on me a few times. Where the GUI got messed up beyond all repairs. Every time I would boot it would only get me to the command promp (at the time it was not what I wanted). I tried to fix it but in CLI mode I could not connect to the net. So now I'm thinking if I remove the GDM, and use the command line only that I wont be able to connect online to reinstall it. 

And it does use old things. I have a few computers. On one of them I did a clean install of 9.10 and the Grub boot menu is different. Not more "Press ESC...". But if you upgrade from 9.04 to 9.10 you keep the old "Press ESC..." option.

---

### Post by slakkie on 2010-03-16
They made a deliberate decision not to update grub-legacy to grub2 for Karmic. You only get that package when you do a clean install. That behaviour is expected.

You can manually upgrade to grub2 if you want though and then you will not have grub-legacy and you will not have the ESC thingy.

---

### Post by stephan.t on 2010-03-16
Yes, Slakkie is right. 
Comment out gdm startup script - you don't have to remove it. 
In karmic (9.10) you go /etc/init and rename the "gdm.conf" to "gdm.cong.SAVED" or whatever fits you. Reboot after. It can be done without reboot but this is the simplest solution. 
If you have an older version you go in /etc/init.d look for some gdm* script and rename it.

If you want it back just rename it to original name.

Cheers,
Stephan.

p.s.

I don't know what bug bit them @Ubuntu. They keep changing and changing as mad. At this pace, soon everybody will be completely lost in the Ubuntu jungle.
:-(

---

### Post by nl4m on 2010-03-16
@Slakkie: I love the old Grub. I wish I can get the new one the act the same way. I prefer the old "Press ESC...". It looks more elegant.

@Stephan: I have both /etc/init and /etc/init.d. Since I'm using Karmic 9.10 I'll rename the config file... Wish me luck. And you're right. Ubuntu is changing Fast. The thing I Hate the most about 9.10 is that they took away my splash screen. Before I had to punch in me username and password, which was cool. Now the username is already there fro you. And you can't customize the login background picture :( And, for me, the boot time is slower. They had it right in 8.10. That was fast, customizable and you had the "service-admin" option, and the animation did not freeze when you paused a song.

---

### Post by HotForLinux on 2010-03-16
> **stephan.t said:**
> 
.....
I don't know what bug bit them @Ubuntu. They keep changing and changing as mad. At this pace, soon everybody will be completely lost in the Ubuntu jungle.
:-(

That's what I'm afraid of too
[-(

---

### Post by stephan.t on 2010-03-16
>> "I have both /etc/init and /etc/init.d"

That's normal. The new init-startup "fashion" named "Upstart" is not fully implemented in 9.10. This is what I was making allusion in my p.s. I mean I'm not against the progress and "New-things" BUT test it before and when you add it to a new release of Ubuntu add it completely.

It has been added partially and let to coexist with the old way of starting the system -  which is using the etc/init.d/. Documentation is scarce if inexistent. Looks to me like a PHD dissertation without any consideration/respect for the end user. 

I like Ubuntu but I need stability. I do not have the time to discover and adapt to all fantasies Ubuntu team is throwing at me. I'm paid to be EFFICIENT!

Sorry for the rant! 

Cheers,
Stephan.

---

### Post by nl4m on 2010-03-16
By the way:
sudo aptitude remove gdm
is to remove it, right? and :
sudo aptitude install gdm
is to reinstall it, using and internet connection, right?

---

### Post by stephan.t on 2010-03-16
Yes you're correct.

to learn more:
    [http://ubuntuforums.org/showthread.php?t=205766](http://ubuntuforums.org/showthread.php?t=205766)
and
    [http://pthree.org/2007/08/12/aptitude-vs-apt-get/](http://pthree.org/2007/08/12/aptitude-vs-apt-get/)

Good luck!
Stephan

---

### Post by slakkie on 2010-03-16
Correct, if you have an internet connection now, you can do:

sudo aptitude --download-only install gdm and it will download the package for you, so you can install it later on. It places the .deb file in /var/cache/apt, don't run aptitude clean or apt-get's variants, you'll wipe it.

When you then run aptitude install it will get the package from your cache. So you don't need connectivity.

---

### Post by nl4m on 2010-03-17
> **slakkie said:**
> Correct, if you have an internet connection now, you can do:

sudo aptitude --download-only install gdm and it will download the package for you, so you can install it later on. It places the .deb file in /var/cache/apt, don't run aptitude clean or apt-get's variants, you'll wipe it.

When you then run aptitude install it will get the package from your cache. So you don't need connectivity.

I did as you told me and it worked great. What happened is that I "LS -L | GREP 'gdm'" in my /etc directory. What I didn't notice is that it was a directory itself. So I rename it and it worked. I booted into the CLI, THANKS!!!!

As for the comments here I'm confused. The syntax is "sudo aptitude --download-only install gdm". Is it ok if I just write "sudo aptitude --download-only" without the "install". I know that you use "install" when you want to install a package. Why do we use it when we just want to download a package? Second question. Once the package is downloaded it's stored in the /var/cache/apt/archives", right ? Not in /var/cache/apt. Third question. The package is downloaded. How do I install it ? Running "aptitude install (name of package)" will try to get it from the internet. It will not bother looking that the /var/cache/* directory, right ? Why I ask this question is that I read that once you use "aptitude --download-only" you have to use the "dpkg -i (package name and/or path)" to install it. Which one is right? The "dpkg -i" or "sudo aptitude install"?

---

### Post by slakkie on 2010-03-18
> **nl4m said:**
> I did as you told me and it worked great. What happened is that I "LS -L | GREP 'gdm'" in my /etc directory. What I didn't notice is that it was a directory itself. So I rename it and it worked. I booted into the CLI, THANKS!!!!

As for the comments here I'm confused. The syntax is "sudo aptitude --download-only install gdm". Is it ok if I just write "sudo aptitude --download-only" without the "install". I know that you use "install" when you want to install a package.


No, you need to issue a command (eg, install).

> 
Why do we use it when we just want to download a package? 


Because it is an option which can be useful. During the Karmic development release I often issued a safe-upgrade command with the --download-only option. Then backed up my full root. This allowed me to perform multiple upgrades from the same base and not having to download all the packages every time I restored the backup. Other reasons could be to download the packages at work/home and install them somewhere else (eg in the train).


> 
Second question. Once the package is downloaded it's stored in the /var/cache/apt/archives", right ? Not in /var/cache/apt.


Yes, that is correct, the /var/cache/apt is just the location of the apt cache. I backup that dir because it also contains the cache for apt-file. But you are right, the downloaded packages reside in /var/cache/apt/archives.


> 
Third question. The package is downloaded. How do I install it ? Running "aptitude install (name of package)" will try to get it from the internet. It will not bother looking that the /var/cache/* directory, right ?


No, it will only download it from the internet if there is a newer version/candidate available (compared to the version present in the cache). You can see this by doing: 

sudo aptitude install hello
sudo aptitude purge hello
sudo aptitude install hello

The first time you install hello, it will download the package from the repo. Then you remove it, and then you install it again. The second time you install it, it will notice the package is in the cache and will install that version.

Then delete your cache (sudo aptitude clean) and uninstall the hello package and perform the following:

sudo aptitude --download-only install hello
sudo aptitude install hello

You will see the same behaviour.

> 
 Why I ask this question is that I read that once you use "aptitude --download-only" you have to use the "dpkg -i (package name and/or path)" to install it. Which one is right? The "dpkg -i" or "sudo aptitude install"?

You can use both, it doesn't really matter unless there is a newer version available in the repos. If there is a newer package available and you don't want to install that package, but the one from the archive, you can use dpkg -i or aptitude install packagename=version. Where version should be the same as the version available in your cache.

The available versions of a package can be found by running apt-cache policy packagename:

```

$ apt-cache policy hello            
hello:
  Installed: 2.2-2
  Candidate: 2.5-1
  Version table:
     2.5-1 0
        990 ftp://ftp.nl.debian.org testing/main Packages
        500 ftp://ftp.nl.debian.org unstable/main Packages
 *** 2.2-2 0
        500 ftp://ftp.nl.debian.org lenny/main Packages
        100 /var/lib/dpkg/status

```

I can now install 2.5.1 by running aptitude install hello=2.5-1 (not needed in this case, but just an example).

---

