---
title: "Share Thunderbird profile"
date: 2010-10-07
forum: General Help
---

### Post by winecurmudgeon on 2010-10-07
I'm running Xubuntu 10.04 on my desktop and Ubuntu Netbook Remix on an Asus 1005HA. I'd like to move my Thunderbird profile back and forth.

Right now, I'm using Dropbox, which is very slow. Is there a faster way? Will a very simple file sharing setup work? I have a wireless network in my house that I can use.

Thanks for your help.

---

### Post by myii on 2010-11-04
Just a couple of quick pointers:

The following link explains the concept of how to actually configure Thunderbird to link to a profile that is not in the default location: [http://lug.rose-hulman.edu/wiki/Thunderbird#Sharing_a_profile_with_Windows](http://lug.rose-hulman.edu/wiki/Thunderbird#Sharing_a_profile_with_Windows)

The instructions are obviously for a single dual-boot computer but the important part that can be used for your problem is re: [ -profilemanager].

The actual solution could be based around setting up an NFS share on one of your computers that could be accessed from the other.  I'd suppose the profile should be located on your laptop (so that it could be used wherever you go) and then connect to it from your desktop when you're at home (obviously, the laptop needs to be switched on!).

So in summary:
1. Setup a share on your laptop.
2. Connect to that share from your desktop.
3. Configure Thunderbird on the desktop to use the profile on your laptop instead.

Caveat alert: I haven't tried this myself.  I'd be careful using Thunderbird from both computers at the same time, since this *could* lead to profile corruption.  If you're inclined to try that, make sure you make a backup of your profile first.  Actually, **you should make a backup of your profile before trying this at all**.

PS: When configuring the share, you may need to use the *nolock* option as mentioned on: [http://forums.fedoraforum.org/showthread.php?t=192920](http://forums.fedoraforum.org/showthread.php?t=192920).

---

### Post by winecurmudgeon on 2010-11-15
Thanks for the help, myii. Sounds like a project for over the holidays.

---

