---
title: "Samba no longer follows symbolic links"
date: 2010-03-25
forum: General Help
---

### Post by piratebill on 2010-03-25
I have been running a samba server for a while now with no issues.  The other day I ran apt-get update && apt-get upgrade on my server and samba was updated.  Now when I try to access sym links Windows tells me I dont have permission to access those folders.  When I try to access them with the terminal it works just fine.  Any ideas?  Also I am using Windows 7.


EDIT:
It does the same thing on Xp too.

EDIT V2:
I have added the following to my smb.conf

follow symlinks = yes
wide symlinks = yes
unix extensions = no

Still nothing....

---

### Post by piratebill on 2010-03-25
Fixed it.  According to [http://www.samba.org/samba/news/symlink_attack.html](http://www.samba.org/samba/news/symlink_attack.html)

wide links are now set to no as a default.  I changed it back to yes and it works fine now.

---

### Post by theLured on 2010-03-26
Thanks I solved it by opening this file
```
sudo gedit /etc/samba/smb.conf
```

Then I put this under the [global] section
Note: It's "wide links" and not "wide symlinks"
```
follow symlinks = yes
wide links = yes
unix extensions = no
```

Save it and then run this to restart samba.
```
sudo /etc/init.d/samba restart
```

This worked for me.
Thanks piratebill

---

### Post by michael_j_w on 2010-03-28
> Then I put this under the [global] section
Note: It's "wide links" and not "wide symlinks"

 
Quite right! I followed the same thread and was equally lead astray, but thanks to you and you correction everything is working jolly good.
 
Thanks

---

### Post by _mobius_ on 2010-03-28
Worked for me.  I just had to listen to the kids whine for 2 days before I broke down and dug for the solution.  Now all is well again.

---

### Post by ansarte on 2010-03-28
I was having the same problem with Karmic and the next three lines worked for me:

follow symlinks = yes
 wide symlinks = yes
 unix extensions = no

After an update to Lucid beta 1 it stopped working.

---

### Post by doobiest on 2010-03-29
> **michael_j_w said:**
> Quite right! I followed the same thread and was equally lead astray, but thanks to you and you correction everything is working jolly good.
 
Thanks

Thanks, I has wide symlinks too, that fixed it for me.

Are you guys using ubuntu 10.04?  I have had samba working in the same nature for years on various ubuntu versions, and I only had to add this in after upgrading to 10.04.  If that's the same for you we should get a bug filed on launchpad. This will break existing functionality and might be confusing for new users.

I'm guessing either widelinks was a hard coded default in previous versions of samba, meaning it could be absent from the config file yet still work. Or something else has changed in samba now requiring widelinks.

I've had two user experiences here. At one point my symlinks would show up, but they would have a reported size of 0KB and could not be accessed. Later, I experienced no symlinks being displayed at all.

---

### Post by doas777 on 2010-03-29
I've never had a problem with this before in ubuntu, but I have had to add those lines to my NAS's smb config

---

### Post by dphirschler on 2010-03-30
This isn't working for me.  My server is Ubuntu 8.10.  It has two hdds, each 500GB like so:

/mnt/store          <--- first hdd mounted in fstab
/mnt/store2         <--- second hdd mounted in fstab

On the server, I went to /mnt/store and made a symlink called Video pointing to store2.

sudo ln -s /mnt/store2 Video

"store" works fine on all the PCs on the network, both WinXP and Ubuntu (9.10 and 9.04).  But the link 'Video' shows up as both locked and broken.  I've set permissions on both hdds to '777' and the owner to nobody:nogroup.  I am stumped now.

I've tried the above settings in my smb.conf file.  As soon as I try 'unix extensions = no' the Ubuntu client sees all the directories on the server as text files, even the symlink.  Double-clicking them tries to load the file instead of changing into the directory.

So what's wrong?


Darryl

---

### Post by wb4alm on 2010-04-03
SAMBA on my 8.04 development system was updated on March 24th, and the change in "how it works" prevented me from using my "hosted" winxp system to complete some production work.

I found that I had to create (1) new "shares" using Natilus, (2) and add some users to the Linux box to match the Ids from the Windox box, (3) and add some new [share] definitions to smb.conf to get any kind of access to the linux files.

Once I was able to get that to work, I discovered that the Symbolic links no longer worked, so I added the    follow symlinks = yes  
command, which did not help.

after more hours of trying things and reading the internet, I found this post.

When I added the  wide links = yes
and               unix extensions = no

everything finally worked as I had originally intended (2 years ago), and had originally coded with a lot less lines in smb.conf   I am still unable to use my original share definition, so apparently that security update changed a lot of internal behavor.

Thanks for the post, I don't know how long it would have taken me to try the Wide Links option.

---

### Post by oddentity on 2010-04-05
So, does this mean that the only way to get symbolic links working in samba shares accessed by Windows clients is to create a security hole?

---

### Post by nexist on 2010-04-16
Thank you for posting the solution. Life is good now.

---

### Post by PeterK2003 on 2010-05-02
After updating to 10.04 it broke my symlinks.  I have already added the 3 setting mentioned before.  Any suggestions?

---

### Post by PeterK2003 on 2010-05-02
and 3 sec after i post i figure it out!

Thanks anyways.

---

### Post by neutron68 on 2010-05-05
never mind. :)

---

### Post by Sciamano on 2010-05-06
> **PeterK2003 said:**
> and 3 sec after i post i figure it out!

Thanks anyways.

How did you solve? I've been fighting with this for a week without any success!!

---

### Post by pricetech on 2010-05-06
> **PeterK2003 said:**
> and 3 sec after i post i figure it out!

Thanks anyways.

Please post your solution to help others.

---

### Post by pricetech on 2010-05-06
OK, here's what worked for me.  From an article at:
[http://www.jonathanmoeller.com/screed/?p=1590](http://www.jonathanmoeller.com/screed/?p=1590)
I ran smbpasswd and mine started working.

I had already installed via Synaptic and had configured using the gui tool.

Worked for me.

---

### Post by Alain Knaff on 2010-05-10
> **Sciamano said:**
> How did you solve? I've been fighting with this for a week without any success!!

Simply add "unix extensions = no" into the [global] section of smb.conf

Just a remark for those gotten bitten by this behavior, and want to avoid similar occurrences in the future: The samba team doesn't read distribution's bug trackers and forums, but they do have their own list: 

[EMAIL="samba-technical@lists.samba.org"]samba-technical@lists.samba.org[/EMAIL]

The samba team lives under the impression that only a tiny minority of people are affected by this bug, and they can only be convinced otherwise if more people make their voices heard. So if you care, drop a note to [EMAIL="samba-technical@lists.samba.org"]samba-technical@lists.samba.org[/EMAIL]

Thanks,

Alain

---

### Post by zdude on 2010-05-13
I ended up using these three options in the global sections:

follow symlinks = yes
wide links - yes
unix extensions = no


This was the only way that I could follow sym links in Lucid that previously worked in 8.04.

---

### Post by Sciamano on 2010-05-13
> **zdude said:**
> I ended up using these three options in the global sections:

follow symlinks = yes
wide links - yes
unix extensions = no


This was the only way that I could follow sym links in Lucid that previously worked in 8.04.

Didn't work for me. Had to add:

force user = USERNAME

in each share section.

---

### Post by satosh on 2010-05-16
> **theLured said:**
> Thanks I solved it by opening this file
```
sudo gedit /etc/samba/smb.conf
```

Then I put this under the [global] section
Note: It's "wide links" and not "wide symlinks"
```
follow symlinks = yes
wide links = yes
unix extensions = no
```

Save it and then run this to restart samba.
```
sudo /etc/init.d/samba restart
```

This worked for me.
Thanks piratebill
Success! Thank you all!

---

### Post by Blonddeeni on 2010-07-04
Thanks to all the previous replies to this thread I've managed to get my samba share working also, but have had to change my /etc/samba/smb.conf even more than the others on this thread.

I'm running Ubuntu 10.04 on a desktop and a Laptop, and the only way I can get them to do a samba share and follow symlinks is to add the following to both the   [global]   AND  [My.Username] sections of /etc/samba/smb.conf.

follow symlinks = yes
wide links = yes
unix extensions = no

So to repeat, those three lines are in my Global section, and down the end of the file in my Username section. The only other line in my username section is the directory which has the symlinks pointing to the directories I'm willing to share.

Very glad i found this thread. :D

So that's Samba, ssh and ftp with login working, now to find out what webDav does.

Cheers all.

---

### Post by SlugSlug on 2011-11-07
> **theLured said:**
> Thanks I solved it by opening this file
```
sudo gedit /etc/samba/smb.conf
```Then I put this under the [global] section
Note: It's "wide links" and not "wide symlinks"
```
follow symlinks = yes
wide links = yes
unix extensions = no
```Save it and then run this to restart samba.
```
sudo /etc/init.d/samba restart
```This worked for me.
Thanks piratebill




Thanks!!

---

### Post by sohmc on 2012-01-05
I know this is bumping a new thread, but wanted to post another fix.

It seems that 11.10 that this issue still occurs and the fix to disable unix extensions and enable wide links does not work.  The solution to this is a bit more complicated.

The security issue that [the article](http://www.samba.org/samba/news/symlink_attack.html) suggests is actually fairly serious.  If you are working in an environment where you cannot trust your users, you should consider the solution below:

Edit /etc/fstab.  You will need to use sudo as it's a system file.

At the bottom, type in the following line:
```

/path/to/directory   /home/user/directory_link   none   bind   0 0

```

The first parameter is the directory you want to link to.  The second directory is the directory you want to link to.  This directory should be EMPTY be an actual directory (or folder as is the parlance of Windows users).  It should also be placed within the samba share branch you plan on exporting.  In this case, I'm sharing my home directory and placed directory_link within it.

The third parameter indicates the type of partition your mounting.  In this case, since your just mounting folder, it is set to none.  The fourth option indicates the type of mount.  Your binding to a directory.  The last two are options are for actual partitions so they are set to 0.

Once you add the line to the file, mount the partition:
```
sudo mount /home/user/directory_link
```

Since you placed this in /etc/fstab, it will survive reboots.

---

### Post by piratebill on 2012-01-20
> **sohmc said:**
> I know this is bumping a new thread, but wanted to post another fix.

It seems that 11.10 that this issue still occurs and the fix to disable unix extensions and enable wide links does not work.  The solution to this is a bit more complicated.

The security issue that [the article](http://www.samba.org/samba/news/symlink_attack.html) suggests is actually fairly serious.  If you are working in an environment where you cannot trust your users, you should consider the solution below:

Edit /etc/fstab.  You will need to use sudo as it's a system file.

At the bottom, type in the following line:
```

/path/to/directory   /home/user/directory_link   none   bind   0 0

```

The first parameter is the directory you want to link to.  The second directory is the directory you want to link to.  This directory should be EMPTY be an actual directory (or folder as is the parlance of Windows users).  It should also be placed within the samba share branch you plan on exporting.  In this case, I'm sharing my home directory and placed directory_link within it.

The third parameter indicates the type of partition your mounting.  In this case, since your just mounting folder, it is set to none.  The fourth option indicates the type of mount.  Your binding to a directory.  The last two are options are for actual partitions so they are set to 0.

Once you add the line to the file, mount the partition:
```
sudo mount /home/user/directory_link
```

Since you placed this in /etc/fstab, it will survive reboots.


that is very clever.  Doing it in samba (as far as I understand) only creates a security hole if you have admins who do stupid things.  If you (or an admin) creates a sym link to dangerous areas yes that is a problem.  Otherwise I don't think there would be any security hole.

---

