---
title: "Is there any fork of remastersys?"
date: 2011-10-10
forum: General Help
---

### Post by papaapa on 2011-10-10
Hello!

Today i look remastersys for Ubuntu 11.10 but i see this page: [http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)

Is there any for of this program? Or any same purposed program?

Thank you!

---

### Post by haqking on 2011-10-10
> **papaapa said:**
> Hello!

Today i look remastersys for Ubuntu 11.10 but i see this page: [http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)

Is there any for of this program? Or any same purposed program?

Thank you!

it is called re-linux

[http://sourceforge.net/projects/re-linux/](http://sourceforge.net/projects/re-linux/)

---

### Post by inameiname on 2011-10-11
> **papaapa said:**
> Hello!

Today i look remastersys for Ubuntu 11.10 but i see this page: [http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)

Is there any for of this program? Or any same purposed program?

Thank you!

I just noticed this too! It is one of my most-used programs, and best easy Live disc backup one I use in Linux. I sure hope a good fork does come up. 

Re-linux looks very promising. Hopefully in no time a gui for it will come out, as that would be best, particularly for those who are not very comfortable with the command line. 

BTW, does anybody know if Re-linux does full system backups, such as the 'backup' feature in remastersys, which includes the home directory and everything? I noticed the command line choices differ from remastersys a bit, and I am unsure which to use to generate a full computer backup to a live iso.


UPDATE:

Thinking about a gui for this, I wonder if the folks at USU Desktop ([http://download.learnfree.eu/repository/skss/](http://download.learnfree.eu/repository/skss/)) might be able to tweak a version for re-linux. They actually have a remastersys-gtk that improves the normal gui for remastersys (remastersys-gui), and now that remastersys is no more, I wonder... I will email both to see if anything can come.

I have just always loved Remastersys and if there is a similar one out there, I would love to find it.

---

### Post by inameiname on 2011-10-11
For those interested, I threw together a debian file of re-linux for easy installation. It's just the latest release (relinux-0.2.1b1), made into debian form.

Also, to make it much easier, I made it so it will automatically create a '~/.relinux.conf' file upon first use, something you would have had to do before. So it is just a matter of installing and running.

---

### Post by lkjoel on 2011-10-11
Thanks for that! I'll update my script (I'll change it a bit, just making a new option to generate the relinux.conf).

---

### Post by inameiname on 2011-10-11
> **lkjoel said:**
> Thanks for that! I'll update my script (I'll change it a bit, just making a new option to generate the relinux.conf).

Sure. To note, I also changed the ~/relinux.conf to ~/.relinux.conf, so as to not have it always there and easily seen in my home directory. Of course, that can easily be changed.

Anyway, it was nothing. I have sort of become fairly good at hand-making debian files from things via a couple little nautilus-scripts called Deb-Tweaker I wrote: [http://gnome-look.org/content/show.php/Deb-Tweaker?content=129857](http://gnome-look.org/content/show.php/Deb-Tweaker?content=129857). And once I start using relinux fulltime, I will definitely add it to my PPA for easy installation.

---

### Post by elliotn on 2011-10-11
am waiting for GUI

---

### Post by lkjoel on 2011-10-11
It'll come in 1.0

---

### Post by inameiname on 2011-10-12
Here is another small thread on this issue. 

[http://ubuntuforums.org/showthread.php?p=11333024#post11333024](http://ubuntuforums.org/showthread.php?p=11333024#post11333024)


Also, here is an article by Joel (lkjoel, the author of re-linux) regarding his new fork of remastersys:

[http://lkubuntu.wordpress.com/2011/10/10/relinux-a-way-to-create-a-bootable-iso-out-of-your-system/](http://lkubuntu.wordpress.com/2011/10/10/relinux-a-way-to-create-a-bootable-iso-out-of-your-system/)


I figure it a good idea to link similar threads together so we can all benefit, particularly for those of us who may have thought we were alone in our dependency and love for remastersys and all its glory. ;)

---

### Post by papaapa on 2011-10-14
Has someone tried with Ubuntu 11.10 stable with re-linux?

---

### Post by lkjoel on 2011-10-14
Yes, I developed relinux with Ubuntu 11.10, so it is made to work with it.

---

### Post by papaapa on 2011-10-14
> **lkjoel said:**
> Yes, I developed relinux with Ubuntu 11.10, so it is made to work with it.

Can you please **simply** explain how you created the iso (not distro iso, i need backup iso). I am not a prof. user.

Thank you!

---

### Post by lkjoel on 2011-10-14
Sorry, backup is not included yet in relinux. It is targeted for 1.0, but I think I'll change it to 0.3, so it will come shortly.

---

### Post by inameiname on 2011-10-16
> **lkjoel said:**
> Sorry, backup is not included yet in relinux. It is targeted for 1.0, but I think I'll change it to 0.3, so it will come shortly.


Speaking of backup mode, have you run across this package? It seems to be another fork of remastersys, but far more simpler, and only seems to do backup mode. I haven't tested it to see how well it works or not.

It is called refractasnapshot. I only looked at one thread about it thus far. I'll attach the two debs for it.

---

### Post by lkjoel on 2011-10-16
> **inameiname said:**
> Speaking of backup mode, have you run across this package? It seems to be another fork of remastersys, but far more simpler, and only seems to do backup mode. I haven't tested it to see how well it works or not.

It is called refractasnapshot. I only looked at one thread about it thus far. I'll attach the two debs for it.
Yeah, but it isn't a fork of remastersys. I'll include the backup option in 0.3, based on both programs (remastersys and refractasnapshot).
Thanks for the deb files of refractasnapshot!

---

### Post by inameiname on 2011-10-16
> **lkjoel said:**
> Yeah, but it isn't a fork of remastersys. I'll include the backup option in 0.3, based on both programs (remastersys and refractasnapshot).
Thanks for the deb files of refractasnapshot!

Oh, I see. There wasn't much info found on it, so I just figured it was designed to be a very lightweight, literally two-click option for full backup only fork of Remastersys. Though, I did notice the structure of the final .iso is different than yours or that of remastersys.

Well okie dokie. I appreciate the info!

---

### Post by lkjoel on 2011-10-16
I don't know about the structure about the ISO file, but just check out the source code. It's completely different.
I'm going to copy some code over from both, so that relinux will have a great backup feature.

---

### Post by inameiname on 2011-10-17
> **lkjoel said:**
> I don't know about the structure about the ISO file, but just check out the source code. It's completely different.
I'm going to copy some code over from both, so that relinux will have a great backup feature.

Sounds like the smart way to do it then.

---

### Post by lkjoel on 2011-10-17
I'm currently working on it, and I'm just going to do it the lazy mans way, but it's actually better than remastersys's way (and I'm merging some code from refractasnapshot). It doesn't have a backup *mode*, but it's a configuration file option.

---

### Post by inameiname on 2011-10-18
> **lkjoel said:**
> I'm currently working on it, and I'm just going to do it the lazy mans way, but it's actually better than remastersys's way (and I'm merging some code from refractasnapshot). It doesn't have a backup *mode*, but it's a configuration file option.

Gotcha. As I asked on that article you wrote about Relinux, so long as that 'backup' 'configuration file option' does what the 'backup mode' did in Remastersys, then I'm happy. Hehe

---

### Post by inameiname on 2011-10-18
[FONT=Verdana][FONT=Verdana]For those further interested, as of 18 October, I threw together an updated Debian (.deb) package of the latest source code of Relinux. I'll attach.

Along with that, I'll attach another debian package of it, one  with a few minor tweaks of mine. Basically its the same, with the  addition of a few changes. Here is what I changed for  my package that is also in my PPA:

[/FONT][/FONT]> 
* Changed the configuration file to always get generated inside the $HOME directory rather than the current one (reflected that in menu option). 
  * Renamed './relinux.conf' to "$HOME/.relinux.conf" (prefer to keep it hidden, rather than easily seen inside the $HOME directory). 
  * Added an auto-backup of an older "$HOME/.relinux.conf", if there is one, as a way to have easy access to past settings. 
  * Also changed one setting on '/etc/relinux/relinux.conf': 'Y' for keeping relinux installed in the ISO (no need to reinstall now for every update ISO). 
Remember, this is just a snapshot version of Relinux of the latest source code. So use at your own risk. Same goes for my version. Its just what I prefer, and by no means better or worse. Although, both seem to work correctly so far. Also to note, who knows how the final release will be.

---

### Post by gluni on 2011-10-18
if you could make relinux compatible for other distributions that would be great, lets say for sabayon (gentoo) maybe…?
Those distributions dont have any tools like remastersys or so to do the “backup” mode.

---

### Post by ourasi on 2011-10-18
Latest snapshot of relinux works now also in VirtualBox, older versions stopped at the beginning. Backup = Y doesn't differ (yet) from dist mode.

I tested also refractasnapshot. It seemed to make backup from Lubuntu 11.10 installation and booted in VBox and from usb. My 3g network was only connection I could use, wi-fi and wired network didn't work. Installation from live system didn't work either. Must test again with some Debian, maybe LMDE.

---

### Post by lkjoel on 2011-10-18
> **gluni said:**
> if you could make relinux compatible for other distributions that would be great, lets say for sabayon (gentoo) maybe…?
Those distributions dont have any tools like remastersys or so to do the “backup” mode.
Thanks, but if you want a new feature, please ask it in the Tickets section of the relinux home page: [http://sourceforge.net/p/re-linux/tickets/](http://sourceforge.net/p/re-linux/tickets/)

---

### Post by lkjoel on 2011-10-18
> **ourasi said:**
> Latest snapshot of relinux works now also in VirtualBox, older versions stopped at the beginning. Backup = Y doesn't differ (yet) from dist mode.

I tested also refractasnapshot. It seemed to make backup from Lubuntu 11.10 installation and booted in VBox and from usb. My 3g network was only connection I could use, wi-fi and wired network didn't work. Installation from live system didn't work either. Must test again with some Debian, maybe LMDE.
Backup=Y does include the /home directory. The problem is that it still removes many directories, so I'm looking into the problem.

---

### Post by JosephC on 2011-10-20
Thank you for the packages, inameiname. Very convenient.

And thank you so much for forking Remastersys, Joel Leclerc. Relinux looks to be a natural progression. It is an absolutely necessary piece of software, and handles personal customization like a dream. 

You have made a lot of people very happy.

---

### Post by inameiname on 2011-10-20
> **JosephC said:**
> Thank you for the packages, inameiname. Very convenient.

And thank you so much for forking Remastersys, Joel Leclerc. Relinux looks to be a natural progression. It is an absolutely necessary piece of software, and handles personal customization like a dream. 

You have made a lot of people very happy.

No problem. I always prefer debian packages for installation of things, so its something I always do for myself anyway.

And definitely. Relinux is coming along well it seems, and it is really great something took over the reigns. Thanks again Joel.

---

### Post by tabishq on 2011-10-21
I tried relinux with Ubuntu 11.10. Everything "seems" to go fine, but when you install it, and boot the system, it lands you at a grub prompt. Apparently it doesn't create a grub configuration.

---

### Post by inameiname on 2011-10-21
> **tabishq said:**
> I tried relinux with Ubuntu 11.10. Everything "seems" to go fine, but when you install it, and boot the system, it lands you at a grub prompt. Apparently it doesn't create a grub configuration.

That happens to me when I do it as well (using the /etc/skel method too as found on the link via this thread), but I know it is being worked on a fair amount, and as others seem to be very successful, there must be something up on our end. Regardless, whether or not that is the case, again, lots of work is being done on it, so just hold your breath a short bit and I am sure the issue will be resolved. 

In the meantime, you can always file a bug report/feature request, via a ticket, here: 

[https://sourceforge.net/p/re-linux/tickets/3/](https://sourceforge.net/p/re-linux/tickets/3/)

---

### Post by tabishq on 2011-10-21
> **inameiname said:**
> That happens to me when I do it as well (using the /etc/skel method too as found on the link via this thread), but I know it is being worked on a fair amount, and as others seem to be very successful, there must be something up on our end. Regardless, whether or not that is the case, again, lots of work is being done on it, so just hold your breath a short bit and I am sure the issue will be resolved. 

In the meantime, you can always file a bug report/feature request, via a ticket, here: 

[https://sourceforge.net/p/re-linux/tickets/3/](https://sourceforge.net/p/re-linux/tickets/3/)

I think the problem was not at relinux's end. I built the iso again after adding lot of stuff like skype, google-earth, latex, gimp, gthumb, pidgin etc and making gnome-shell as the default for lightdm, and did a reinstallation without fiddling with network connections during the install. And everything went fine, and I have a running system which logs into gnome-shell by default.
I noticed once before while installing vanilla Ubuntu 11.10 that during the install I fiddled with the wireless connections, and the installation crashed. I don't know if that was connected to the fiddling around.
**However, now I can vouch that relinux works well with Ubuntu 11.10!** :)
I was also happy to notice that squashfs uses all the four cores of my processors, and so the remastering was very fast. By the way, I do the remastering on a separate partition, and not in a virtual machine.

---

### Post by papaapa on 2011-10-21
We are waiting for a stable version for Ubuntu 11.10 backup mode :)

---

### Post by lkjoel on 2011-10-21
> **papaapa said:**
> We are waiting for a stable version for Ubuntu 11.10 backup mode :)
Actually, the backup mode will come in 0.3, and not 1.0!

---

### Post by inameiname on 2011-10-22
> **tabishq said:**
> I think the problem was not at relinux's end. I built the iso again after adding lot of stuff like skype, google-earth, latex, gimp, gthumb, pidgin etc and making gnome-shell as the default for lightdm, and did a reinstallation without fiddling with network connections during the install. And everything went fine, and I have a running system which logs into gnome-shell by default.
I noticed once before while installing vanilla Ubuntu 11.10 that during the install I fiddled with the wireless connections, and the installation crashed. I don't know if that was connected to the fiddling around.
**However, now I can vouch that relinux works well with Ubuntu 11.10!** :)
I was also happy to notice that squashfs uses all the four cores of my processors, and so the remastering was very fast. By the way, I do the remastering on a separate partition, and not in a virtual machine.

That's good to hear. I have heard that for the most part it does work for 11.10. I just have to figure out what steps I am not doing correctly. Of course, as mentioned before, I am not a distro mode man, but a backup mode one, and I also do not use another partition, nor a virtual machine. So who knows. I'll figure it out somehow. Anyway, glad you got it up and working!

---

### Post by inameiname on 2011-10-27
Here is the latest SVN snapshot of relinux, as of 26 October 2011. One is the original, and the other is one I tweaked a very small bit. Here is what I changed:

```

  * Changed the configuration file to always get generated inside the  $HOME directory rather than the current one (reflected that in menu  option). 
  * Renamed './relinux.conf' to "$HOME/.relinux.conf" (prefer to keep it  hidden, rather than easily seen inside the $HOME directory). 
  * Added an auto-backup of an older "$HOME/.relinux.conf", if there is one, as a way to have easy access to past settings. 
  * Also changed two settings on '/etc/relinux/relinux.conf': 'Y' for  keeping relinux installed in the ISO AND REMOVEAFTERINSTALL="", keeping "ubiquity".                       

```Once again, use one or the other at your own risk. They are just current snapshots of the latest relinux.

To note, now relinux conflicts with remastersys, so you cannot have both installed on your machine. (/usr/bin/remastersys) is now inside both.)

relinux_0.2.1b1+svn20111026-1_all.deb:
[http://www.2shared.com/file/6kqW4O1n/relinux_021b1svn20111026-1_all.html](http://www.2shared.com/file/6kqW4O1n/relinux_021b1svn20111026-1_all.html)

or

relinux_0.2.1b1+svn20111026-1ppa1~inameiname1_all.deb:
[http://www.2shared.com/file/4RQ-Gp53/relinux_021b1svn20111026-1ppa1.html](http://www.2shared.com/file/4RQ-Gp53/relinux_021b1svn20111026-1ppa1.html)

---

### Post by Fragadelic on 2011-10-27
Due to the number of emails I received after I decided to stop development it has made me reconsider my decision.

Remastersys is back up and running.  A new update to both debian and ubuntu versions will arrive in the next couple of weeks.

What this means is that as long as I am able to keep things going I will continue to develop remastersys for debian and ubuntu.

I will also be incorporating some of my other distro making scripts within remastersys to make it easier for folks.  These other scripts have been used by my own distributions and those that I work with and have been quite heavily tested so even though they will be new to the package they are not new scripts at all.

---

### Post by inameiname on 2011-10-27
> **Fragadelic said:**
> Due to the number of emails I received after I decided to stop development it has made me reconsider my decision.

Remastersys is back up and running.  A new update to both debian and ubuntu versions will arrive in the next couple of weeks.

What this means is that as long as I am able to keep things going I will continue to develop remastersys for debian and ubuntu.

I will also be incorporating some of my other distro making scripts within remastersys to make it easier for folks.  These other scripts have been used by my own distributions and those that I work with and have been quite heavily tested so even though they will be new to the package they are not new scripts at all.

Wow, I wasn't expecting this. And based on the threads you had posted on just prior to when you halted Remastersys support, sounds like you weren't either. I was definitely sadden to hear it, but also understood why you had stopped. Well, good to know the Linux community finally realized just how important you and your Remastersys was for them; enough, apparently to get you back in the game. :P 

Anyway, I look forward to see what is new in the works with Remastersys. Also, now with Relinux around too, it will be interesting to see what improvements may come in both. Relinux has plenty of interesting techniques on the way that I am curious to see how it will come out (such as Wubi support, backup mode, multi-system support, and etc). Maybe some collaboration, perhaps... ;)

---

### Post by Lumsdoni on 2011-10-28
Great to here!

One question regarding relinux.

In the conf file, what settings should I change the Liveuser, Livename and hostname to?

I have one user on my netbook and I want to be able to use the livecd to keep my gnome shell login with wallpapers etc, settings, keyboard shortcuts etc.

---

### Post by Lumsdoni on 2011-10-28
OK. I followed the directions to move the home file to etc/skel.

Incidentally the instructions don't mention that it will delete all your settings. But no big deal as I didn't have much.

Rewrote my scripts etc. and backed up.

Now the livecd that it makes boots straight into my desktop with shortcuts and custom shortcuts intact.

Great.

Only thing it doesn't do is boot into gnome 3 which is what I did the backup under.

I tried to log out but then I cannot log back in with my user and password.

If i run a terminal I am logged in as custom@custom-desktop

What is the password for custom?

---

### Post by Lumsdoni on 2011-10-28
Ahh, user Custom, password is "" (blank)

However, if I choose gnome from the drop down on login it still boots to unity.

Tried installing gnome again, but livecd says its already installed (hence the drop down option).

Thanks for such a great tool.  Love being able to do a full system backup.

---

### Post by lkjoel on 2011-10-28
Liveuser is the username of the live user (in your case, custom). Livename is the full name of the live user (much less important). Hostname is the hostname of the live system (in your case, custom-desktop).

What do you mean to select GNOME instead of Unity? Is it on the LiveCD or on the Desktop?

---

### Post by JosephC on 2011-11-06
> **Fragadelic said:**
> Due to the number of emails I received after I decided to stop development it has made me reconsider my decision.

Remastersys is back up and running.  A new update to both debian and ubuntu versions will arrive in the next couple of weeks.

What this means is that as long as I am able to keep things going I will continue to develop remastersys for debian and ubuntu.

I will also be incorporating some of my other distro making scripts within remastersys to make it easier for folks.  These other scripts have been used by my own distributions and those that I work with and have been quite heavily tested so even though they will be new to the package they are not new scripts at all.

The Ubuntu world just did this:

[http://www.youtube.com/watch?v=-1BPx5Wsm7k&t=02m23s](http://www.youtube.com/watch?v=-1BPx5Wsm7k&t=02m23s)

---

### Post by Fragadelic on 2011-11-07
> **JosephC said:**
> The Ubuntu world just did this:

[http://www.youtube.com/watch?v=-1BPx5Wsm7k&t=02m23s](http://www.youtube.com/watch?v=-1BPx5Wsm7k&t=02m23s)

Thanks but that grossly over-exaggerates the importance of remastersys.

---

### Post by a111111111 on 2011-11-29
Will you write the remastersys from zero? The backup mode will support on the new version? Re-linux will support the other operation systems except Debian - based systems?

---

### Post by Fragadelic on 2011-11-29
> **a111111111 said:**
> Will you write the remastersys from zero? The backup mode will support on the new version? Re-linux will support the other operation systems except Debian - based systems?
No.  Most of my remastersys code goes back to the beginning - 2007 and is still relevant today since the live boot hasn't changed a whole lot.  Backup mode has always been part of remastersys and will always remain part of it.  Remastersys only supports ubuntu and debian and I don't have any plans to support any other distributions except Mint LMDE provided I can get info from them on it.

---

### Post by lkjoel on 2011-11-29
> **a111111111 said:**
> Will you write the remastersys from zero? The backup mode will support on the new version? Re-linux will support the other operation systems except Debian - based systems?
Relinux 0.5 will support Ubuntu, Debian, Fedora, Madriva, CentOS, Slackware-based, and Gentoo Linux.
Of course, it isn't only limited to that, but if we need support for other systems, we will add it in a later release.

---

