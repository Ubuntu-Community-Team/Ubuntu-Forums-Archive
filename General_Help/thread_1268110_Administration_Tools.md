---
title: "Administration Tools"
date: 2009-09-16
forum: General Help
---

### Post by beavis69 on 2009-09-16
Does Ubuntu have any decent GUI based network application administration tools? Something like the excellent YAST?

My boss is stuck on the idea of Ubuntu, mainly because of the hype and not for any substantive reason. Actually to make matters worse he wants Kubuntu for desktops even though Kubuntu doesn't seem to do a good job with KDE 4 but that is another question.

My main concern is that he wants ease of use for various network apps, which is why I tried to push him into opensuse which has excellent graphical tools for everything imaginable from samba to kerberos. Also how about a run services GUI, it is tiresome having to be forced to do these things on the command line in Ubuntu especially since VI doesn't work the same as it does in other distros.

What can be done on the servers in under 90 minutes in opensuse from install to being completely done takes all freaking day in Ubuntu. It is not a horrible thing, but the problem is the people that are going to maintain it are going to struggle with Ubuntu the way it is now. They were all ready to ditch the office desktops that run Windows and move to Linux, but their nonsensical reason to use Ubuntu because of the hype machine is turning them off to Linux, which is sad because it is not Linux they don't like, it is Ubuntu, yet they won't try another distro because they think they are all the same.

I realize some of this post is worthless rant, but I see this story time and again about Ubuntu scaring people away from Linux permanently. But if I can install stable and functioning tools like YAST maybe that will change their minds about not ditching Windows on the desktop.

---

### Post by tgalati4 on 2009-09-16
This is a great post.  It's the first time that I've seen someone with decision authority bicker over which version of Linux to use.

It's classic.

I agree, SUSE and Fedora are better at wide deployment.  Yast is a decent tool, but there are similar tools in Ubuntu, just not integrated into one massive configurator.

I would set up Koala on one machine, Fedora 11 on a 2nd and OpenSUSE (whatever the latest is) on a third machine.  Let the boss use each one for a week.  The employees should be able to choose as well, based on these three demo machines.

Gnome is more stable than KDE 4.3, but the desktop is less critical than what the employees are supposed to be doing.

It's up to you as the IT guy to make it all work.

What a difficult situation.  Getting paid to integrate linux machines!

Back to your original question:  there are so many network tools, what is it specifically that you need to do?  Are you looking for a large enterprise machine management?  Are you looking for simple ways to assign IP's?

---

### Post by beavis69 on 2009-09-17
Thanks for the excellent response.

For administration purpose he wants samba set set up for remote file system access, running Tomcat, ldap, ftp, vnc and a few other things. They want simple and free so the routing, firewall and VPN is done via Untangle. As much as I whined about setup, it is maintenance that is the bigger problem since no one in the office really knows Linux, they just know they want to get out from under the Redmond hammer, but to them Linux is Linux. I am not really the IT guy, just the only one with any Linux experience(I run Linux at home and use it 99% of the time), but the administration side I have next to no experience in.

I let them play with configuring both opensuse and ubuntu and I think that made my point a little clearer. Thank you for the suggestions for GUI tools, not as nice as unified tools, but still puts things on track. 

On the desktop, I think it matters less, but they seem to heavily favor KDE. They actually don't seem to care if all the desktops run the same distro, so I am just leaving it up to them. Mounting remote file systems and opening a VPN is pretty much the same process across the distros that I have worked with.

I don't know if bicker is the right word, but I like the discussion about which distro to use, hopefully it will result in a better setup than just downloading distro x and using it.

---

### Post by tgalati4 on 2009-09-17
Well, you will become the IT go-to guy when things fail or don't work right under linux.

Untangle is a good product.  Centos is good for production-grade servers, though Ubuntu's Hardy server seems reliable in the 6 months that I have been running it.  I also have a Dapper Drake desktop/server.  It's been running the desktop and serving various applications non-stop since June 2006 when it came out.  Downtime during the past 3 years can be measured in minutes and only for updates (which I do about every 6 months).

Maintenance can be tedious, but install long-term support versions to reduce the headaches.  If you install all the machines with the same root user/password then assign a single user account for each machine, that will limit the damage done by users.

You would only need to update each machine once every 6 months.  Sooner if there is a critical security patch that seems to generate buzz on these forums.

Keep a diary of all of the integration problems that you encounter.  Put them on a blog or an area of your hosted website that you can share for others to learn from.

Post any head-scratchers to these forums, and you will find answers.

KDE 4.3 is shiny, but I'm not sure it's ready for production use.

---

### Post by HermanAB on 2009-09-17
Hmm, if you want wizards, then even Red Hat is better than Ubuntu and Suse or Mandriva would be the way to go.

However, if your boss is hell bent on Ubuntu, then you should make peace with Webmin.  It generally works and will get the job done.

---

### Post by tgalati4 on 2009-09-18
webmin is OK for making the transistion to linux.  It has some security issues for continued use in a business.  Secure ssh and console tools (including custom scripts) are really all that is needed for routine maintenance.

---

### Post by doas777 on 2009-09-18
NX is great for terminal services, whatever distro you choose. 

the Control Center is probably a good central way to get at a lot of the config utilities. you can enable it by editing your menus and eabling it (it's under the "System" tree).

---

