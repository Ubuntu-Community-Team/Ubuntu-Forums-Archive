---
title: "using the same /home partition for two linux operating systems"
date: 2010-10-17
forum: General Help
---

### Post by ipey on 2010-10-17
is it possible? (and probable?) I've successfully followed psychocats' tutorial on creating a separate home in ubuntu and noticed that it basically "only" needs fstab editing, so I wonder if could create the same home for two OSs (ubuntu and fedora). The only problem which comes to my mind is file/folder ownership but I'm not sure. and since I'm just a newbie, I think it'd be better if I consult to this forum first before messing up with OS. I'll be waiting for enlightenment from all of you. Many thanks.


best regards,

---

### Post by PaulW2U on 2010-10-17
> **ipey said:**
> The only problem which comes to my mind is file/folder ownership but I'm not sure.
I had exactly that problem when I installed Ubuntu onto a hard drive that had Fedora on it and tried to keep my existing /home directory.

Different values are used for the UID/GID (500 as opposed to 1000 or v.v.) despite the username being the same. I had to change all the owner/group ids before I could use it again under Ubuntu.

---

### Post by oldfred on 2010-10-17
No, also you may have different versions of software that writes different data.

What you want with multi-OS is a shared /data partition as that has all your data but not the hidden settings that are in /home. When I moved all my data out of /home it became less than 1GB.

Partitioning basics with some info on /data older but still relevant
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

How to Multi-boot (Maintain more then 2 OS) old grub
[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)
Painless Linux Multi-boot Setup - see also comments by Morgan Hall
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions (post #5) of data linking from above blog, based on more from comments 
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)
Suggestion by srs5694 on /shared or /mnt as location to mount data partitions to (better than oldfred's):
[http://ubuntuforums.org/showthread.php?t=1594622](http://ubuntuforums.org/showthread.php?t=1594622)

---

### Post by dimoftheyard on 2010-10-17
Sharing the /home partition between two distros won't work smoothly, but I don't think you need (want?) that. As oldfred said a seperate /data partition could be what you want. Having that you could e.g. make /home/username/Music a symlink to /data/Musik, so you would not notice that your data is stored in a seperate partition.

---

### Post by nothingspecial on 2010-10-17
While all the above is true, ubuntu variants work nicely.

Rather than having the kubuntu and ubuntu desktops installed on the same partition, it works better having them on seperate partitions with a shared home.

Ubuntu + Fedora though, no.

---

### Post by srs5694 on 2010-10-18
I disagree with oldfred and dimoftheyard on this score. You can safely and easily share a single /home partition between distributions; you just need to use different user home directories in the two distributions. For instance, you might use /home/ipeyf for Fedora and /home/ipeyu for Ubuntu. IMHO, this is simpler and cleaner than using a separate data partition, as oldfred suggests; this approach scales better if you add accounts (even if they're just multiple accounts for your own use) and you're keeping your data in the standard location. The simplest way to create separate user home directories is to use different usernames in the two distributions; however, you can use the text-mode usermod program (or probably a distribution-specific GUI counterpart) to change a username after installation so that the usernames match but the home directories are unique.

As PaulW2U says, the default first user ID (UID) and group ID (GID) values differ between Ubuntu and Fedora. These can be synchronized, again using usermod. It's probably safer to change Fedora to use UID 1000 rather than change Ubuntu to use UID 500, but either will work. (I do the latter for historical reasons -- my earliest Linux installations, many years ago, used UID 500, and I've adjusted subsequent installations to match.)

---

### Post by oldfred on 2010-10-18
A question for srs5694.

If I share /home with different users how do you have the same data in both or do you keep data in one user and link into the other users? For example I share my firefox & thunderbird profiles by having them in a shared data folder. Does not ownership and permissions have to then be on a group level rather than just my user.

I also cannot remember all my passwords now, so since my system is my home desktop I keep all user & passwords identical ( or else I would not know what is who:))

---

### Post by srs5694 on 2010-10-18
Ownership and permissions issues are identical when sharing a /home partition between two distributions and using a separate user data partition (/data or whatever). In either case, the best solution is to synchronize UID (and optionally GID) values between the two distributions.

You can create symbolic links for configuration files that you know you can safely share, and you can either create symbolic links for individual subdirectories (say, /home/user1/Photos -> /home/user2/Photos) or link to the whole alternate user directory (as in /home/user1/otherinstall -> /home/user2) to share most ordinary data files.

---

### Post by dimoftheyard on 2010-10-19
srs5694, you have a good point there. It is a matter of taste where somebody wants to store the shared data, but I admit that I did not fully consider the UID problem. And your solution has the advantage of using only one partition instead of three.
But I find having a home with a different name somewhat odd :)

---

### Post by srs5694 on 2010-10-19
> **dimoftheyard said:**
> But I find having a home with a different name somewhat odd :)

Think of it as an undercover identity -- it could be /home/jamesbond or something. You could even [change your login sound appropriately.]("http://titotheman.wordpress.com/2009/11/06/changing-startup-sound-in-ubuntu-9-10-karmic/") ;)

Also, remember that Linux uses case-sensitive filenames, so you could just vary the case if you prefer doing it that way.

---

### Post by btindie on 2010-10-19
Another approach is to use pam_mount (libpam-mount) and have that mount (bind) the users data directories (Documents, Music, Videos, etc...) from another partition when they log in. The data directories then can be mounted across distributions so you can easily access your personal documents from the 'normal' locations. The version specific config files then remain in your home directory - each of them. You of course still need to make sure the UID/GID matches.

---

### Post by ipey on 2010-10-20
Wow, I've got some lights and shadows here. but at least now I know what I have to know first and some alternatives to try out. I've gathered some references based on the keywords all of you imply including links from oldfred. time to read them. thanks a lot guys. I'm glad that I'm a part of this community.

---

