---
title: "&quot;gnome-session not found&quot;"
date: 2011-05-05
forum: General Help
---

### Post by maizuddin35 on 2011-05-05
Hello guys, everyone, I need help from you guys

I installed gnome3 and I configure the problem things and some other stuffs that are needed when I want to install gnome3.

Now,I have weird problem where I can not log into my gnome shell. 

When I turn on my computer and try to login, using the "Ubuntu Gnome Shell Session"
A pop up window appear telling me, "Failed to load gnome-session" and "Logout"I can't get into my ubuntu Natty in any other session.

I get into root(the command line)and when I sudo apt-get upgrade there is an installation of gnome-session and some stuffs.

The thing is I don't have any direct internet connection , just a wifi internet connection provided by my university . 

anyone any ideas on how to fix this? If there is nothing ... I think I just reinstall everything back. 

Thanks in advance

---

### Post by maizuddin35 on 2011-05-06
Alhamdulllah. 

Since no body don't even bother to reply this thread :P I think I just solve this thing by my own :D

I know at first I just need to install gnome-session for gnome3.
So , I get into ubuntu liveUSB, when in there, I put the ppa for the latest gnome3 and update the repository.After that, I open synaptic and search for gnome-session for gnome 3 that I just put . Marked it, and generate the download script. After that , I downloaded all the related packages for that, and put it inside my ubuntu home folder.

I reboot. and login as "Recovery Session" and **sudo dpkg -i *.deb **. rebooted and done. :)

This is one of my noob way :)

If there is anymore in installing this kinda thing in other concept please share with is the newbie :)

---

