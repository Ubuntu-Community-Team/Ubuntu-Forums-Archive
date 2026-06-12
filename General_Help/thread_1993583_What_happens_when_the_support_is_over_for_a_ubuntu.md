---
title: "What happens when the support is over for a ubuntu release"
date: 2012-06-02
forum: General Help
---

### Post by sd@ksu on 2012-06-02
I have 11.04 installed on my system and also on a few other computers in the lab. We DO NOT plan to upgrade to 11.10 or something else. We just want to keep 11.04 FOREVER! Now my question is, when the support for 11.04 expires in October 2012, what will happen? How will it hamper my normal operations. Say, will I be able to do updates from update manager? Say I want to install a package with ```
sudo apt-get install <package>
``` will I be able to do that? Please help.
.......
I found this thread online : [http://askubuntu.com/questions/101479/are-existing-updates-available-after-end-of-support]("http://askubuntu.com/questions/101479/are-existing-updates-available-after-end-of-support")
...............
which talks about this issue but they also say : > As time goes by, though, you will find that the usual source of newer software - PPAs, will tend to dry up as the maintainers move onto newer versions of ubuntu. which to me means that I would not have access to newer software but I can still keep on using the old ones by pointing the system to the old release area. 
..........
Another question is: will I be able to use a newer software (which is released after 11.04 support ends) in 11.04?
................
I have found this two threads in the forum also...
[http://ubuntuforums.org/showthread.php?t=1841976]("http://ubuntuforums.org/showthread.php?t=1841976")
and
[http://ubuntuforums.org/showthread.php?p=11250875]("http://ubuntuforums.org/showthread.php?p=11250875")
...
I am also considering giving pclinuxos a try.
[http://www.pclinuxos.com/?page_id=1413]("http://www.pclinuxos.com/?page_id=1413")

---

### Post by forrestcupp on 2012-06-02
It means they will never add anything else to the repositories. There will be no software updates or even security updates. They will not be developing the software anymore, and you're not going to get any help with it. Just like what you quoted, there will be no new software, and eventually, even the people maintaining 3rd party PPAs are going to move on and stop supporting that version. You'll be stuck running old software that may have security breaches. It may still work, but you won't get anything new, and it isn't going to be secure.

It's not wise to keep running an unsupported version. If your issue is that you don't like the direction they are going with Unity, you may be better off upgrading and looking into different desktop environments that are more like the old paradigm. A couple of decent choices would be Xfce, LXDE, and Cinnamon, which is what Mint uses. You can also use Gnome Classic in Ubuntu. If you want stability and long term support without having to upgrade a lot, you're better off going with an LTS release.

---

### Post by Paqman on 2012-06-02
They do actually shut the repos, too. So not only will you be unable to get updates, you'll be unable to install anything you don't have the packages for in your cache. I believe there are some alternate repos available that you can switch to.

However, that's all moot since the most important thing to do would be disconnect the machine from the internet. A machine that isn't getting security patches shouldn't be accessible from the intertubes unless you actually want it to get pwned by the script kiddies.

---

### Post by sd@ksu on 2012-06-02
You guys just scared me out...that means ubuntu is not good for long term...and by long i mean really long not the standard 5 yr lts support...this sux big time...:mad::mad::mad::mad::mad::mad::mad:

---

### Post by Paqman on 2012-06-03
Five years is a really long time in computer world. If you bought a machine today and installed 12.04 on it you could use it for another 9 years and 10 months with only one upgrade. That's pretty geriatric for a computer, it's likely it wouldn't be capable of running any contemporary software by then.

All OSes are the same. Windows support is for 10 years, but you'll get at least one Service Pack in that time, which is analogous to upgrading your Ubuntu version. OS X upgrades about every two years, and renders older versions obsolete very quickly (oldest currently supported version came out 2009).

---

### Post by codemaniac on 2012-06-03
> **sd@ksu said:**
> You guys just scared me out...that means ubuntu is not good for long term...and by long i mean really long not the standard 5 yr lts support...this sux big time...:mad::mad::mad::mad::mad::mad::mad:

Upgrading your ubuntu version is just a walk in the park and many people are living happily and securely with Ubuntu by upgrading the flavor in timely interval .

[http://www.ubuntu.com/download/desktop/upgrade](http://www.ubuntu.com/download/desktop/upgrade)

---

### Post by decrepit on 2012-06-03
> **sd@ksu said:**
> You guys just scared me out...that means ubuntu is not good for long term...and by long i mean really long not the standard 5 yr lts support...this sux big time...:mad::mad::mad::mad::mad::mad::mad:

I chose ubuntu because of it's long term support, (3 years) but you have to use the LTS releases, ie 10.4, 12.4.

I looked around for a while and there are a few other linux OS with longish support. "Centos" and Scientific Linux" to name a couple. Most of the others are 6 months to a year.

---

### Post by mcduck on 2012-06-03
> **sd@ksu said:**
> You guys just scared me out...that means ubuntu is not good for long term...and by long i mean really long not the standard 5 yr lts support...this sux big time...

By that definition there is and has never been *any* operating system (free or commercial) that would be good for long-term use...

(Perhaps excluding Windows XP which lived long past it's expected lifetime, probably because of the infamous Vista that followed it.)

---

### Post by viperdvman on 2012-06-03
You can definitely run it... but it's just like installing Windows 98 or Windows 2000. You can **run** them, but they're completely obsolete and no updates past the end of their life are available... thus unless you're running the older OS's for a reason, it's not recommended for regular use.

You can run it, it's just not recommended.

---

### Post by 3rdalbum on 2012-06-03
Just don't do it.

I can't think of a reason not to upgrade to 12.04 LTS - so do it, and you'll be able to stay with 12.04 for five years if you wish.

Ubuntu has never made a secret of being a fast-paced distro. If you want to stay with a release for 5 years, then you must use an LTS release. If you want a longer period of support, Ubuntu is not for you - but some other Linux distros may be. This is no secret and no shame for Ubuntu.

---

### Post by colin.p on 2012-06-03
However, even though it is recommended to keep an up to date system, how often are you going into "dangerous" territory? I have been "on the web" since '94 and have never gotten any malware. Even though I don't go to dodgy sites by design, I have ended up there by accident. 

During those years I was a security freak and had my windows OS's nailed pretty shut(SRP, LUA and surun). I even ran a "non-kosher" copy of XP for several years, that other than sp3, never got any updates, and again narry a whiff of a virus. Of course things have gotten worse since then, but still, linux is far more secure out of the box than windows.

So, you can run your oneiric(sorry, it's natty) for awhile and probably won't have any security problems, BUT, again you may.

---

### Post by Erik1984 on 2012-06-03
> **mcduck said:**
> By that definition there is and has never been *any* operating system (free or commercial) that would be good for long-term use...

(Perhaps excluding Windows XP which lived long past it's expected lifetime, probably because of the infamous Vista that followed it.)

Yep, it's only because of popular demand (especially business demand) that they support XP for so long. Problem is that people might see XP as the standard now in stead of an exception in terms of support duration.

---

### Post by mcduck on 2012-06-03
> **Euroman said:**
> Yep, it's only because of popular demand (especially business demand) that they support XP for so long. Problem is that people might see XP as the standard now in stead of an exception in terms of support duration.

Well, that's going to get fixed over time, seeing that Mictrosoft is not plannig on supporting any of the later versions that long.

Vista is pretty much gone by now, and the planned support time for Win 7 is going to be around the same 5 years you'd get on Ubuntu LTS releases. And of course if you compare these to OS X, where even Snow Leopard users are starting to run into lack of support by now, 3 years after the release, I'd say Ubuntu is actually doing very well on long-term support... :)

---

### Post by sd@ksu on 2012-06-04
My porblem is..I LIKE UBUNTU...so can not get away from it. I am even thinking about getting rid of windows-7 from my lappy and put UBUNTU on it to live happily ever after. BUT THAT'S FOR MY PERSONAL USE.
...
The problem I am facing here is for my workspace. I have set up a 3 computer NFS network in our lab where the files of every user are saved in one computer (the server). THe other two (locals) are used for data collection. I have used some scripts (kept in /usr/local/bin) and tweaked with some settings (e.g., edited /etc/skel/.bashrc and prifle; edited adduser.conf and edited /etc/xdg/user-dirs.defaults) for our use. On the local machines I am running 11.04. Now if I do an upgrade, it might mess things up. Especially I still use the classic ubuntu (my boss prefers that). So now you guys tell me what will my best scenario? We use these systems to collect data in an academic environment but we do have then connected to internet.

---

### Post by jmore9 on 2012-06-04
I usually use the long term on my tv machine so i don't have ot connect it up to internet much.  Most of the time i use the regular releases on the internet machine be they ubuntu, fedora, Suse, Debian, etc as they ( most of the time ) the most up to date security fixes and software updates.

With the apt package manager , ( which is the only reason i use ubuntu ) it is really easy to upgrade your distro.  Most of the time it is painless but sometimes not so much.  But there is nothing perfect in life so sometimes a little work is required.

---

### Post by blackflame2996 on 2012-06-04
> **sd@ksu said:**
>  We DO NOT plan to upgrade to 11.10 or something else. We just want to keep 11.04 FOREVER! 
Why are you stuck on 11.04?:confused:

---

### Post by sd@ksu on 2012-06-04
Tell me one thing, if I upgrade...shall I lose all my settings (read my last post) ... I have root, boot, home on separate partitions though.?

---

### Post by sd@ksu on 2012-06-04
@ blackflame2996: because i have two data acquisition systems running with it...i do not want to install the softwares, configure the hardwares etc.. again...

---

### Post by capscrew on 2012-06-04
> **sd@ksu said:**
> @ blackflame2996: because i have two data acquisition systems running with it...i do not want to install the softwares, configure the hardwares etc.. again...

The real question is:  did you document all your mods.  I still run scripts that started our on Solaris 8 (Perl with appropriate tweaks).  If you have documented your modifications you should be able to bring up a testing host to confirm that everything works. 

You might even thing about how V2 should be constructed to lessen the effect of upgrades. 

One word about an academic environment.  I have found that security in the universities own network is far more dangerous that the internet well ever be.  It is expected that high level hacking is going on and even encouraged in some areas.

Edit: I would personally do a fresh install of 12.04.  As you have a working host to verify your modifications you can document and update the testing host before it goes online.  I will say that even with all the careful planning there were still many "late night adventures" in the NOC when we rolled out new hardware, services or OS Upgrades.  Someone always would forget some little used undocumented mod that was "done on the fly years ago".

---

### Post by hawthornso23 on 2012-06-05
I can't imagine why you are so attached to 11.04 in particular. I might understand if you were trying to hang onto 10.10 which in my opinion was a really good classic ubuntu 'vintage'. But most of us don't have fond memories of 11.04. Is this because it is the last version to run gnome2? 

I strongly recommend you upgrade to 12.04 which is shaping up to be one of the best ubuntus ever in my opinion. If your reluctance to upgrade is due to a dislike of unity then you should know that if you  use gnome-fallback these days you  can almost pretend that the nightmare of unity never happened. 

And as 12.04 is a LTS release, it will be maintained for a very long time.

---

### Post by sd@ksu on 2012-06-05
@ capscrew and hawthornso23 : thanks for the encouraging words..yeah it is because it is the last one of the gnome2..probably..am a novice...my reason has been righly pointed by capscrew..I think i need to do the documentation first..rather than keeping it in my dull mind..:D...
Will get back to you guys soon.. i shall 1st document the changes I did; then try the upgrade on my vmware ubuntu 11.04 before trying on the real systems. ...
..........
Can anyone tell me if i shall have to reinstall the softwares again after the upgrade? I think so as it will replace the /etc and /usr which are in my root parttion>..right?

---

### Post by capscrew on 2012-06-05
> **sd@ksu said:**
> 
..........
Can anyone tell me if i shall have to reinstall the softwares again after the upgrade? I think so as it will replace the /etc and /usr which are in my root parttion>..right?

Maybe.  ;-)

That's allways a tricky thing.  Most of the upgrades try and preserve programs and settings, bu there is no guarantee of backwards comparability. 

I have always installed fresh and transferred the data back to where I wanted it if needed.  Mostly I keep the data on it's own partition that is also on it's own spindle (physical harddrive).

---

### Post by hawthornso23 on 2012-06-06
An upgrade gives you a chance of retaining installed software. The upgrade process these days is pretty good. However you can't upgrade direct from 11.04 to 12.04. You'll have to pass through 11.10. 

If you do a clean install you can go straight to 12.04. But you'll definitely have to reinstall everything if you go that route. 

Good Luck

---

### Post by capscrew on 2012-06-06
> **hawthornso23 said:**
> An upgrade gives you a chance of retaining installed software. The upgrade process these days is pretty good. However you can't upgrade direct from 11.04 to 12.04. You'll have to pass through 11.10. 

If you do a clean install you can go straight to 12.04. But you'll definitely have to reinstall everything if you go that route. 

Good Luck

An upgrade (vs a fresh install) always has some backwards comparability issues with the OS and older installed applications.  Trade-offs have to be made.  In most cases you won't have problems, but you could down the road.  The advantage with  a fresh install is that these issues don't happen.  You may have problems but not with backwards compatibility and old dependencies that need to be met.

@sd@ksu

So there you have it.  Both sides of the coin upgrade or reinstall, that is the question.

---

### Post by 3rdalbum on 2012-06-06
> **capscrew said:**
> An upgrade (vs a fresh install) always has some backwards comparability issues with the OS and older installed applications.  Trade-offs have to be made.  In most cases you won't have problems, but you could down the road.  The advantage with  a fresh install is that these issues don't happen.  You may have problems but not with backwards compatibility and old dependencies that need to be met.

@sd@ksu

So there you have it.  Both sides of the coin upgrade or reinstall, that is the question.

That's not the question. There is another option.

The Ubuntu desktop CD installer also gives you the option to "Upgrade". This is actually a fresh install, but it reinstalls newer versions of your existing programs, and it preserves /home (so, all the user accounts and files and settings stay!).

It does not preserve /etc so you need to backup your server configuration files if they have been changed from the default, but otherwise it sounds like a much better option than either "Dist upgrade and chance everything becoming borked, or fresh install and lose everything".

---

### Post by capscrew on 2012-06-06
> **3rdalbum said:**
> That's not the question. There is another option.

The Ubuntu desktop CD installer also gives you the option to "Upgrade". This is actually a fresh install, but it reinstalls newer versions of your existing programs, and it preserves /home (so, all the user accounts and files and settings stay!).

It does not preserve /etc so you need to backup your server configuration files if they have been changed from the default, but otherwise it sounds like a much better option than either "Dist upgrade and chance everything becoming borked, or fresh install and lose everything".
Hmmmm, an interesting option.  It automates what I proposed above. > ...installed fresh and *transferred the data back*... 
In my case the data is always on a separate spindle so it never goes away on any install or upgrade.  :D

---

### Post by sd@ksu on 2012-06-06
I shall try and let you guys know...but I do not think I shall have time to do it for a while now..thanks anyways...

---

### Post by VanillaMozilla on 2012-06-06
sd@ksu,
After you install gnome-session-fallback, you will have a choice of desktops on login (there's a button you push, and you can remove some of the choices later).  I suggest Gnome Classic (no effects).  You probably already know this.

Keep in mind that there will be some differences, and some things will be missing.

To make changes in the panel, it's now <alt> right-click instead of just right-click.

Also, your screen saver will be gone.  You can install another if you wish, but I don't recommend it.

---

### Post by sd@ksu on 2012-07-08
I just upgraded to Ubuntu 12.04 guys...and I like it...even the unity..:o

---

### Post by sd@ksu on 2012-07-08
Thanks a lot for your suggestion guys..this forum rocks...

---

