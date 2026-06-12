---
title: "All the files from my home folder disappeared"
date: 2009-11-08
forum: General Help
---

### Post by rafaelpagliuca on 2009-11-08
I installed Ubuntu 9.10 3 days ago, and had already set it up for work.
I imported my Thunderbird profile from Windows and installed Eclipse with PDT + Subclipse and SVN.

This morning, while I was browsing my home folder with Nautilus suddenly the default folders (Images, Videos, Desktop etc) started to disappear, one by one, as well as my eclipse projects folder and others, until the whole ~ folder got empty.

I thought it a Nautilus bug. I pressed F5 to refresh the folder, but none of them showed up again.

I went to terminal and ls ~ returned an empty folder, as well. This meant that even invisible/profiles folder got deleted, including the trash folder.

So everything got deleted, including the trash folder itself, and I could not get to restore anything.

I'm not worried about the files, because basically I was just importing stuff from another box.

I just lost confidence on Ubuntu file system. What if this happens again just after I finish some project? I know backup is important, but it's very time-spending to backup everything all the time.

Has anyone got any problem similar to that one? Any suggestions to avoid this happening again?

Sorry about my bad English, it's not my mother language.

Please share your thoughts.

Best regards, Rafael.

---

### Post by kronomia on 2009-11-16
[SIZE=3]Hello, I faced the same problem... It is really depressing when you lose your project files. _**My projects folder simply got disappeared as if it was permanently deleted.**_ This is the first time i encouter such an event in an Ubuntu System. Please anyone have any idea what happened? Is this a bug or something. I am quite sure that i didn't do anything abnormal on that day. I am not new to Ubuntu. I was used to work with Fedora and Unix-based systems before. I hope the Debian-based Ubuntu is not the cause of the problem.

[B]_I am using the following:_
*Ubuntu 9.04- the Jaunty Jackalope - 32bit edition
*GNOME Version: 2.26.1
*The folder that disappeared is located in sub-folder in my home directory: home/user/myFiles/myFolder
[/B]
I will be waiting for your help,

Thanks a lot and regards,[/SIZE]

---

### Post by sgosnell on 2009-11-16
I have no idea.  I've never heard of this happening.  Can you give more detailed information on exactly what you did and what happened?

---

### Post by blazemore on 2009-11-16
The two people who have lost files:
What filesystem are you using?

---

### Post by rafaelpagliuca on 2009-11-16
I'm using ext4.

As a work-around I'm avoiding storing important stuff on the home folder. But I haven't got any more problems since the first one.

Thanks for the people which are trying to help us.

---

### Post by P4man on 2009-11-16
I never heard this and it seems .. well hard to believe really.
Have you guys checked your filesystem for errors? Are you sure the /home partition is not full? Have you looked in .trash folders and elsewhere?

---

### Post by kgas on 2009-11-16
If your home folder is mounted on a separate partition, your can try to recover it using testdisk.(boot with ubuntu cd  and install testdisk)

---

### Post by blazemore on 2009-11-16
Ahh, that's a good point. If your home directory is mounted elsewhere, make sure there's no problems with the disk.
Do ```
sudo mount -av
```

---

### Post by kronomia on 2009-11-16
**First of all, I really want to thank all the people who are trying to help us. I really appreciate your work.** Thanks very much!

_**Here are more details:**_
*I am the only user and admin on the computer.
*This is only one operating system that is running: Ubuntu 9.04
*There is no partitions at all... I have only one partition which the operating system resides on.
*The type of the partition is: ext3. I used to feel comfortable with ext3.

_**What i think:**_
_**Reason #1:**_ I used to to do "suspend" a lot during the day while programs are running which may cause loss of data.
_**Reason #2:**_ My Hard drive has experiences some bad sectors in the past but i managed to isolate them successfully. Still though, it might have something to do with that.

_**What i tried to do before posting:**_

_**Try #1:**_ I tried to recover deleted files assuming that my files got deleted somehow. 
I used the following commands:

foremost -v -q -t cpp -i /dev/sda1 -T
and
foremost -v -t cpp -i /dev/sda1 -T

But really no use... It was taking more than 6 hours without any progress. As you can see i lost (.cpp) files as I am a C++ programmer. ;)

_**Try #2:**_ Then i decided to check if that is the only file that got deleted. It seems that indeed it was the only one. So i proceeded to the next step which it was making sure if the files are exist or not. So i carried an intensive search for specific files. No results found.

_**Try #3:**_ I applied all the direction of the user: "blazemore" who was trying really hard to help me. I really want to give him special thanks for posting and trying to support us. Thanks Blazemore. 

_**Right Now: **_
Right now, everything is fine, no new files are disappearing any more. I am able also to compile and link without any problems. Mainly i use this PC for programming. There is no games, or unnecessary applications or anything like that. So i think the firewall and my C++ compiler are the only things i care about.

If an idea came to your mind about what had happened or how to avoid it for next time, it will be great if you can post it here.

Thanks again for everything guys and regards,

---

### Post by blazemore on 2009-11-16
If you ever get files disappearing again, it's definitely new hard disk time!

Also, if I were you I'd stick important files like cpps in your Ubuntu One. They tend to be small, but very time consuming to replace.

ps, I was so touched by your message of thanks that I included it in my sig.

---

### Post by Sin@Sin-Sacrifice on 2009-11-16
There's always the other thing that could have happened. I know of people who are capable and malicious enough to do things like this and I hate them for it. Around here we call then crackers. Unfriendly hackers... these are the same people that make virus' and worms and what have you. I personally know a guy that "cracked" a home PC of some unsuspecting no name user and deleted his entire system32 folder just for fun. I, of course, kicked his teeth in and we haven't spoken since. He thought it was funny... until he was bleeding. He's a Windows user and only knows Windows but who knows? Not to say this is what happened to yous guys but it's always something to consider. Check out [http://www.ubuntu.com/usn/](http://www.ubuntu.com/usn/) often and make sure you have all security updates.

---

### Post by blazemore on 2009-11-17
It probably isn't. These people nowadays don't WANT their malicious software to be detected.
Their idea of the perfect virus runs undetected in the background, earning them money by popping up adverts, or stealing credit card details which they can sell or use.

The days of "LOL I HAXX0RED YOUR SYSTEM I PWNS U LOOLLLOLLL"
are (sadly?) long gone.

---

### Post by blueridgedog on 2009-11-17
These two cases look like common cases of disk failure.  I would use palimpsest (installed in 9.10 now) to view the bad sectors and also run fsck on the partitions involved while booted from a LiveCD (unless the partitions can be unmounted during normal use).

---

### Post by Braytonio on 2010-01-23
The fellow who reported the problem, which I am also suddenly seeing, mentioned that he suspends a lot.

Interesting. I had just done a lot of installing and uninstalling of packages and then suspended my computer for the night. When I went to wake it up, gdm crashed and the computer rebooted. 

After reboot, I have a desktop with mounted volume icons and the Downloads folder. Folders I had added to the Desktop are gone. My home directory structure is now

```
/home/macunaima/Downloads
```

That is all there is in it, aside from hidden folders such as .nautilus and other app configuration folders. 

I have recently fscked, and palimpsest shows no bad sectors. I also use the ext4 file system that became the default with Karmic, I think.

The odd thing is that my recently added Tomboy notes are still accessible. These are supposed to be stored in 

```
~/.local/share/tomboy/
```

That folder no longer exists in my home directory, according to what nautilus and the command line terminal are telling me. 

I have also lost most of my confidence in Ubuntu. Karmic has caused me so many problems and taken up so much of my time with troubleshooting that I really think I may end my longtime commitment to Ubuntu in search of a simpler, more straightforward distro.

---

### Post by Braytonio on 2010-01-23
> **Braytonio said:**
> 

```
~/.local/share/tomboy/
```

That folder no longer exists in my home directory, according to what nautilus and the command line terminal are telling me. 


I take that back. Here it is. And you know what? The entire contents of my home folder have been copied into it! Did I do that? I certainly don't remember doing it, although I did copy my old Tomboy notes into the folder. I am pretty sure I did not have a brain fart while doing that. 

So I go to copy all that back to where it belongs -- /home/macunaima -- and I see that gdm is now treating my home folder as the Desktop. Whoa. How to set Desktop as the folder displayed on the Desktop?

---

### Post by ankspo71 on 2010-01-23
I had a mysterious deletion of the contents of my home folder once too. At the time it happened, I was trying to compile a source package that appeared to be for debian only. The reason why I say that is because it was a package available in debian repos, but not in ubuntu's (including some of it's dependencies). What I did was reinstalled ubuntu after reformatting the drive, just in case I inadvertently created a malicious program. This might have been close to a year ago, haven't had a problem since, and my hard drive is still going strong.

So I think the problem might be a possible software issue (a bug), as much as it could be a possible hardware issue (hard drive). I would be suspecting the last program used, maybe get your home folder back and see if running that program makes it happen again. Also, I have read that Ext4 did have a few complaints with data loss when it first came out too. I just Googled **Ext4 data loss** and it returned 20,200 results. Ext4 been good to me though... unless it had something to do with the above problem.

---

### Post by blueridgedog on 2010-01-23
> **Braytonio said:**
> How to set Desktop as the folder displayed on the Desktop?

1) open gconf-editor
2) browse to /apps/nautilus/preferences entry in it
3) verify that set desktop_is_home_dir flag is not set

As to the other issues, it may have been human error, or it may have been a combination of installs.  You should have a backup of your home directory, preferably two.  

If you find another distribution of Linux that meets your needs better, post here with the results.  I have found Ubuntu to be a great distro.  If you want less issues, try to use the current LTS issue.

---

