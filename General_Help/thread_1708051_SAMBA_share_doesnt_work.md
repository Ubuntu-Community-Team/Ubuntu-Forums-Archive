---
title: "SAMBA share doesnt work"
date: 2011-03-16
forum: General Help
---

### Post by lauznis on 2011-03-16
My SAMBA share doesnt work. i have added valid users, public (not protected by password) shares are working but intended password protected share isnt.

Windows XP says:
```

 "You might not have petrmission to use network resource.

Multiple connections to server or shared resource by the same user, using more than one username are not allowed. disconnect all previous connections to the server or shared resource and try again.."
```/etc/init.d/smb.conf
```
[protected]
path = /home/pass
writable = yes
browseable = yes
security = user
valid users = janis
```

---

### Post by gtzam on 2011-03-16
Have you added a samba password for the user?
sudo smbpasswd -a USERNAME (Username=janis in your case)
sudo smbpasswd -e USERNAME (to enable it)
Samba has a separate set of passwords than the linux system, but the user has to be a real user of the system (e.g. able to log-in with the terminal)

for window$ share, the window$ login name has to be mapped in the  /etc/smbusers file
Edit the /etc/smbusers file to map your machine names to unix users names:
The following file is an example:

root = window$ window$2
nobody = guest pcguest smbguest
USERNAME = micro$oft_user

In this case anyone logging in from machines window$ or 2 will be mapped as user "root". 

and make sure the ntfs permissions are set properly (for ntfs partitions)...
For ntfs samba share to work:
-do not check "Allow access to Everyone" but specify the user names that are allowed to access it
-make sure that when mounted, the ntfs partition is accessible by the users intended to connect to it via samba. Check the dmask and fmask options, as well as the umask option in the /etc/fstab. dmask 000 equals 777 access rights. dmask 027 equals 750, etc...
Here is an example:
UUID=601DD7821CC75228 /media/External_USB ntfs-3g defaults,dmask=027,fmask=027,uid=1000,gid=100 0 0

the above partition is mounted with 750 rights. Make sure the dir /media/External_USB has corresponding rights.




Have a look at this [link]("http://www.jonathanmoeller.com/screed/?p=1168"):

or [here]("https://help.ubuntu.com/community/SettingUpSamba#Samba%20Server%20Configuration%20-%20Manual"):

---

### Post by lauznis on 2011-03-16
Interesting, I have enabled smbuser and added it to /etc/samba/smbusers just as you told and nothing changed after samba restart.

Error log says: NT_STATUS_NOT_FOUND

---

### Post by lauznis on 2011-03-16
So, checked almost everything today, i did literally everything i could think of, copied smbpasswd, smb.conf, smbusers files from a working machine...
The error is that after i type in user and pass, it gives me a error in windows, that i don't have permission to read/see this resourse. Permission are 777, with guest enabled i can access with no problems. Is there any difference if i use smbpasswd or defauldt .tdb password file?

I attacked smb.conf as well

---

### Post by lauznis on 2011-03-16
Smb.conf

---

### Post by NumPy on 2011-03-16
Its best to issue a testparm with tinkering with samba after you edit things, this will always give a direction to where to look at things. 
Two things occur to me, the security setting, (which does not seem to be set) and the guest_only option you have set. Is there a reason you have that set?

---

### Post by gtzam on 2011-03-17
> **lauznis said:**
> 
The error is that after i type in user and pass, it gives me a error in windows, that i don't have permission to read/see this resourse. Permission are 777, with guest enabled i can access with no problems. ?


Have you mapped the windows login name to a linux username in the smbusers file?
Is it an ntfs partition you are trying to share or an ext3/4 one?

---

### Post by skorrdal on 2011-03-17
I have the same problem. Isn't there - anywhere in the eather of the WHOLE Internet - a Samba for Dummies? I am reading about the same problem, again and again, since 2005(!) - and I have still not found any thread that helps; they all walk you through the same steps - that don't work...

I am sorry, but I am trying to be a very easy here - but all replies I read are written for some one who has used Linux since 1986 - or there abouts...

---

### Post by NumPy on 2011-03-18
> **skorrdal said:**
> I have the same problem. Isn't there - anywhere in the eather of the WHOLE Internet - a Samba for Dummies? I am reading about the same problem, again and again, since 2005(!) - and I have still not found any thread that helps; they all walk you through the same steps - that don't work...

I am sorry, but I am trying to be a very easy here - but all replies I read are written for some one who has used Linux since 1986 - or there abouts...

The problem I see then, is there really isn't a 'one stop shop' for samba configuration and setup. There are ways to build samba completely unsecured, and completely locked down as a Domain Controller. (or BDC). Samba is a fairly simple protocol to setup once you have read the tutorials, and the documentation. One place I land on when Googling for 'Samba Tutorial' is:
[http://www.iamjacksdesign.com/blog/a-decent-samba-tutorial-for-ubuntu/]("http://www.iamjacksdesign.com/blog/a-decent-samba-tutorial-for-ubuntu/")
This guy has pulled old Ubuntu Articles that work if you follow them completely and understand the basics behind them. Don't fret too much its not really that hard. Even if you are a beginner.

---

### Post by aktiwers on 2011-03-18
I just learned about a GUI app today that lets you configure smb.conf

Maybe it will be useful?
```
sudo apt-get install system-config-samba -y
```
```
sudo system-config-samba
```

---

### Post by Neobuntu on 2011-03-19
Ah, No! I recently had a problem with the right click; to share a folder method, in that it wouldn't take the password. It just flashed and asked again. Keep in mind, it was working.

In my (convoluted) travels, I tried all manner of config file adjustments, and yes, I know, the planets have to darn near align, like firewall settings, and all, including syntax and many other things. I decided to set up samba the other, recommended way, and gain faster transfers, and all that jazz.

I used "sudo apt-get install system-config-samba" and it worked just fine. No longer did I need go and re-enter the same darn SMB passwd. All WAS well. 

Now, after days of working, even after turning off AND on, the computer each day, THE SAME DARN PROBLEM STARTS! It's like the password does not work, any more, and yes, I'm sure I entered it correctly.

Um, I've been into computer since 1982, This is BS! This MUST be corrected. It's just insane. no one is going to WANT this, as it is; broken.

I believe that Ubuntu 10.10, should not be broken with Samba, in March of 2011. I'm the hugest supporter of open software, known to man. So, go ahead and bash my "attitude", if that blows your skirt up, but my point still stands. This is NOT where we need to be, at this precarious stage of the game, dear people.

These bugs have been reported over and over again, please, does anyone have a work around? This is a primary function.

---

### Post by aktiwers on 2011-03-19
Actually I have been setting up a simulair setup and recently ask the same question.

You might want to have a look at that thread:
[http://ubuntuforums.org/showthread.php?t=1709425](http://ubuntuforums.org/showthread.php?t=1709425)

I will test it out in next week, I can send you my smb.conf if I get it to work.

---

### Post by Morbius1 on 2011-03-19
@Neobuntu
> Now, after days of working, even after turning off AND on, the computer  each day, THE SAME DARN PROBLEM STARTS! It's like the password does not  work, any more, and yes, I'm sure I entered it correctly.I have no idea based on your description if this is the problem but beginning with 10.10 Ubuntu by default installs a package called:
```
libpam-smbpass
```It's function is to override the password you set for userX in smbpasswd with the local login password for userX. It does that on every reboot.

I don't know why anyone was asked to write such a utility or why anyone would want to install it as it makes no sense to have such a thing happen in a real Sever or in a home LAN. The solution is to remove it:
```
sudo apt-get remove libpam-smbpass
```If your samba password already is the same as your login password then you have a different problem.

---

### Post by Neobuntu on 2011-03-19
Thank you all. I hope you understand. I looked at that thread.

Thanks Morbius1, I used

> sudo apt-get remove libpam-smbpass 

and we'll see how it goes. 

Last night I reset the smbpasswd, again, to the same password (not my sudo passwd) and after reboot, it seems to take. guess what,. today, it DI NOT work, until I reset/reentered the smbpasswd, again.

Perhaps removing libpam-smbpass was exactly the issue and I will test it. Thank you for sharing with me, even though I'm upset these things persist.I expect SOME bugs, but not like this. Job one, is winning the hearts and mind or what people about THINK Ubuntu. I'm trying to keep it real, so we actually KEEP something, people PREFER.

I LOVE the choice, I take issue with the (not working) defaults. There is a difference.

It should (perhaps) go without saying, the only changes to my system, were standard upgrades. I had CLEAN installed Ubuntu 10.10 64bit, just to eliminate any question. Like I said, When the ship is cruising along nicely, why break it? Again and again, by in release upgrades? When that is (rarely) unavoidable, how are we going to fix it faster?

Maybe we should focus on one Samba setup, as the default, and keep that simple. You can "choice" all over the place, but not with THE defaults. We should only have to plug-in our personal info, and go. Crazy tests accepted, but not a release that is old.

I think it's at simple as this. Heavy, testing developers, do not care if they break the main stream, Ubuntu defaults. That, needs revision. Not everyone, wants a basket case project, even partly. Why can't we protect the base defaults? Then go crazy altering it, individually, if you wish?

---

### Post by NumPy on 2011-03-19
> **Morbius1 said:**
> @Neobuntu
I have no idea based on your description if this is the problem but beginning with 10.10 Ubuntu by default installs a package called:
```
libpam-smbpass
```It's function is to override the password you set for userX in smbpasswd with the local login password for userX. It does that on every reboot.

I don't know why anyone was asked to write such a utility or why anyone would want to install it as it makes no sense to have such a thing happen in a real Sever or in a home LAN. The solution is to remove it:
```
sudo apt-get remove libpam-smbpass
```If your samba password already is the same as your login password then you have a different problem.

Thanks for that information...THAT is just a silly utility and should NOT be included by default. 
@Neobuntu:
Most every Samba upgrade I have ever experienced on Ubuntu has given the option to leave my smb.conf alone, or to overwrite it. Choice is always mine. Its very disturbing that you have run into this issue on our vanilla install/upgrade. I have half a mind to troll my landscape updates for this possible issue. That tool if it indeed IS the problem (again I say) needs to be put as an alternative package only. /sigh.

---

### Post by aktiwers on 2011-03-22
The instructions in my link above (post #12), worked fine for me.

Try it out

---

