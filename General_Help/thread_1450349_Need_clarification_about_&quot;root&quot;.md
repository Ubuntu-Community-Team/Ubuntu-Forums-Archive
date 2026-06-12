---
title: "Need clarification about &quot;root&quot;"
date: 2010-04-08
forum: General Help
---

### Post by aCsbD6N5xj on 2010-04-08
I just installed Wine (1.1.3* dev release) and installed Notepad++ (OSS) and Net Meter (Freeware, the latest beta is actually OSS too). I also intend to install a few other things later. The only failure so far is the latest WinSCP :(

So it made me wonder about what running a process/software as "root" actually means.

When i use U.S.C or 'apt-get install' to install software on my computer, and type my password, it displays that keyring icon on my systray. Does this mean i am root at that moment? And how about running wine, the wine processes, and any windows *.exe i'm installing and running?

I basically am afraid that I am running all the wine-related stuff as root, even though there is no indication that I at least have elevated privileges. What is/are the worst-case scenario(s) about wine?

Thanks.

---

### Post by MooPi on 2010-04-08
Why would you think your Wine usage is under root privilege ? You don't have to enter your password to start wine so you're alright.

---

### Post by Seq on 2010-04-08
Wine runs as your user, not as root.

The worst case scenario is that you could run a malicious .exe file and hose all your data (by default you can access your home dir, I believe). You won't hose the system itself.

What's your use-case for Notepad++ and WinSCP? Does NetMeter even work in wine?

---

### Post by aCsbD6N5xj on 2010-04-08
> **MooPi said:**
> Why would you think your Wine usage is under root privilege ? You don't have to enter your password to start wine so you're alright.

That would be an explosive blend of my linux newbie status and my natural paranoia. 

I never did  stupid things under windows in the first place (pr0n, warez, etc...) but security was still a minor reason why i switched to ubuntu. So i don't want to have the same threats looming around on a system that's relatively new to me. Hope this makes sense :P

---

### Post by aCsbD6N5xj on 2010-04-08
> **Seq said:**
> Wine runs as your user, not as root.

The worst case scenario is that you could run a malicious .exe file and hose all your data (by default you can access your home dir, I believe). You won't hose the system itself.

What's your use-case for Notepad++ and WinSCP? Does NetMeter even work in wine?

I used Notepad++ in windows as a replacement for Notepad and for programming. Now that I'm on ubuntu, i only use notepad++ for the latter. I don't like jEdit. 

I've googled 'SCP GUI for linux' and as far as i understand, they don't support SSH or something like that. Suggestions for alternatives welcome :)

And yes, the latest stable NetMeter works great for me, except for a little bug :)

---

### Post by Chronon on 2010-04-09
> **BucketBob said:**
> I used Notepad++ in windows as a replacement for Notepad and for programming. Now that I'm on ubuntu, i only use notepad++ for the latter. I don't like jEdit. 

Do you mean Gedit?  You could also try Geany for a programming editor/light IDE.

---

### Post by aCsbD6N5xj on 2010-04-09
> **Chronon said:**
> Do you mean Gedit?  You could also try Geany for a programming editor/light IDE.

No not the gEdit in the default ubuntu installs but jEdit. :)

[HTML]http://en.wikipedia.org/wiki/JEdit[/HTML]I'm having a peek at the wikipedia entry for Geany. It actually looks great!!! Why isn't it more known? I'm not implying I know all the OSS software around but still... :P

Thanks for the tip :D

---

### Post by Seq on 2010-04-09
> **BucketBob said:**
> I used Notepad++ in windows as a replacement for Notepad and for programming. Now that I'm on ubuntu, i only use notepad++ for the latter. I don't like jEdit. 

I suppose I understand that. There are lots of editors out there. I've always stuck by vim, but gedit actually has some decent programming-related functionality in it (syntax highlighting, line highlighting, etc) and a plugin system.

> **BucketBob said:**
> I've googled 'SCP GUI for linux' and as far as i understand, they don't support SSH or something like that. Suggestions for alternatives welcome :)

Nautilus (the regular file manager in Ubuntu) supports sftp out of the box, which is another subsystem built-in to ssh, alongside scp. Open a file manager window, press CTRL+L (a little unintuitive), and type in your info (It will prompt for a password).

```
sftp://user@example.com/path/to/stuff
```

It will prompt you for the password (and you can have the keyring remember it). If you like, you can press CTRL+D to bookmark it in the sidebar (and the places menu) so you don't have to type out the url.

If you prefer a side-by-side paned view, you can also try gftp. Despite the "ftp" in the name, it does many file transfer protocols, including sftp as well.

> **BucketBob said:**
> And yes, the latest stable NetMeter works great for me, except for a little bug :)

Interesting. I've never heard of this particular software, but I figured since it looks like it monitors your local network connection, it either wouldn't work, or would only show net utilization for other wine apps.

---

### Post by aCsbD6N5xj on 2010-04-09
> **Seq said:**
> I suppose I understand that. There are lots of editors out there. I've always stuck by vim, but gedit actually has some decent programming-related functionality in it (syntax highlighting, line highlighting, etc) and a plugin system.

gEdit would actually suffice for me :S. Seeing NetMeter work under wine made me want to install other win software, just for the sake of it. I used vi in putty, i hated it.

> **Seq said:**
> 
 If you prefer a side-by-side paned view, you can also try gftp. Despite  the "ftp" in the name, it does many file transfer protocols, including  sftp as well.

GUI + SSH support + "double-paned" layout... gftp = epic win. Does gftp support drag n' drop? They don't answer that question anywhere on their website. If yes, then great!!!

> **Seq said:**
> 
Interesting. I've never heard of this particular software, but I figured  since it looks like it monitors your local network connection, it  either wouldn't work, or would only show net utilization for other wine  apps.     

It mainly monitors Upls and Dwls on a per week/month basis.  The frontend GUI is also supposed to display daily, weekly and monthly reports but clicking the respective tabs only gives a grey area :( That may only be because it's been only a few hours since i installed it though :-k

---

### Post by aCsbD6N5xj on 2010-04-09
nvm, it says in U.S.C that gftp supports drag n' drop. thanks for the tip :D

---

### Post by aCsbD6N5xj on 2010-05-29
BUMP.

I have one more qs: Is it safe to surf the web while having temporary root privileges, like while installing software?

---

### Post by srs5694 on 2010-05-30
I'd like to get back to the basic issue: When you run a program via sudo, gksudo, or a similar tool, you run *that one program* as root. Other programs that are already running, or programs that you launch subsequently, do *not* run as root. This is true whether you explicitly type "sudo", "gksudo", etc., or if it's done via a menu option on your desktop.

For instance, if you're running a Web browser in a normal user login, then type "gksudo gedit /etc/fstab &" in a shell to edit the /etc/fstab file, and then launch an e-mail reader from the same shell you used to edit /etc/fstab, then neither the Web browser nor the mail reader runs with root privileges; only gedit runs as root.

That said, it is possible to mistakenly run a program as root. Ubuntu's reliance on sudo for root access is designed to minimize this risk; however, even with sudo or gksudo, you can cause problems if you do something like launch a Nautilus file browser and then use that to edit files or run other programs. Those processes that derive from sudo or gksudo will normally run as root. If you lose track of what you launch via sudo/gksudo, and especially if something you launch in this way can launch other programs itself, you can end up running programs as root without realizing that they're running in this way.

As a general rule, you should try to keep your use of sudo/gksudo to a minimum. If you find you need it every few minutes, chances are you're doing something wrong. For instance, you might need to adjust mount options on a shared NTFS partition to enable ordinary users to access it. You should only need root privileges to adjust system-wide settings -- to install software, back up the OS, change partitions, alter your network configuration, etc. Once your system is installed and properly configured, most people shouldn't need to do this sort of thing very often.

---

### Post by aCsbD6N5xj on 2010-05-30
> **srs5694 said:**
> I'd like to get back to the basic issue: When you run a program via sudo, gksudo, or a similar tool, you run *that one program* as root. Other programs that are already running, or programs that you launch subsequently, do *not* run as root. This is true whether you explicitly type "sudo", "gksudo", etc., or if it's done via a menu option on your desktop.

For instance, if you're running a Web browser in a normal user login, then type "gksudo gedit /etc/fstab &" in a shell to edit the /etc/fstab file, and then launch an e-mail reader from the same shell you used to edit /etc/fstab, then neither the Web browser nor the mail reader runs with root privileges; only gedit runs as root.

That said, it is possible to mistakenly run a program as root. Ubuntu's reliance on sudo for root access is designed to minimize this risk; however, even with sudo or gksudo, you can cause problems if you do something like launch a Nautilus file browser and then use that to edit files or run other programs. Those processes that derive from sudo or gksudo will normally run as root. If you lose track of what you launch via sudo/gksudo, and especially if something you launch in this way can launch other programs itself, you can end up running programs as root without realizing that they're running in this way.

As a general rule, you should try to keep your use of sudo/gksudo to a minimum. If you find you need it every few minutes, chances are you're doing something wrong. For instance, you might need to adjust mount options on a shared NTFS partition to enable ordinary users to access it. You should only need root privileges to adjust system-wide settings -- to install software, back up the OS, change partitions, alter your network configuration, etc. Once your system is installed and properly configured, most people shouldn't need to do this sort of thing very often.

Oh ok I get it. Thx. 

I don't 'sudo' that often in the terminal. But I often plug in my external HD, which is encrypted with truecrypt, and still need my user password to mount the drive (after giving the TC password).

So let's suppose I lost track of what was launched with sudo, is there a command that's gonna end all these processes at once?

---

### Post by pmooney78 on 2010-08-02
Late reply, but here goes:

First, you don't necessarily have to manually mount your external hard drive in a terminal and type your user password. There are several ways to manage your drives, Probably the best is to edit the /etc/fstab file (there's a good tutorial at [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html) or you can type 'man fstab' -- no quotes -- in a terminal). You'll want to add the "user" or "users" option to the line describing your drive.

As srs said, the best thing you can do is to keep your use of (gk)sudo to a minimum -- use them to open a tool, accomplish whatever you need to accomplish, and then close the tool you were using. But if you do want to find everything that you've opened with (gk)sudo, you can type

```

ps ax | grep sudo

```

"ps ax" just lists all running processes (that's a lot ... ALL processes, including the system background stuff). "grep" is a program that filters the output; piping it through "grep sudo" means that only lines containing the string "sudo" anywhere in the line get printed (of course, this also includes gksudo). This works because ps ax outputs the entire command that was used to start the program.

Note that this doesn't include all root processes (those could theoretically be started in other ways, such as at system start time, for instance), but only those that were invoked via sudo -- which is probably what you want.

Hope that helps.

---

### Post by aCsbD6N5xj on 2010-11-05
> **pmooney78 said:**
> Late reply, but here goes:

First, you don't necessarily have to manually mount your external hard drive in a terminal and type your user password. There are several ways to manage your drives, Probably the best is to edit the /etc/fstab file (there's a good tutorial at [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html) or you can type 'man fstab' -- no quotes -- in a terminal). You'll want to add the "user" or "users" option to the line describing your drive.

As srs said, the best thing you can do is to keep your use of (gk)sudo to a minimum -- use them to open a tool, accomplish whatever you need to accomplish, and then close the tool you were using. But if you do want to find everything that you've opened with (gk)sudo, you can type

```

ps ax | grep sudo

```"ps ax" just lists all running processes (that's a lot ... ALL processes, including the system background stuff). "grep" is a program that filters the output; piping it through "grep sudo" means that only lines containing the string "sudo" anywhere in the line get printed (of course, this also includes gksudo). This works because ps ax outputs the entire command that was used to start the program.

Note that this doesn't include all root processes (those could theoretically be started in other ways, such as at system start time, for instance), but only those that were invoked via sudo -- which is probably what you want.

Hope that helps.

Thanks!!!

Sorry for the late reply... I haven't been on the forums in a long while! :P

---

### Post by TracyO on 2010-11-22
Thank you for taking the time to write a pretty thorough explanation.  I just found out I was hacked, so now I have a healthy dose of paranoia, and someone mentioned that the hacker could have gained entry if I was running Firefox as root.  I never open programs through my terminal, which if I understand correctly, means that running programs as root should NOT be how the hacker gained access?

I think I'm secure for now, but looking through the forums to see what I can do to better protect myself.  Thanks for root help.

---

### Post by hardfire_avk on 2010-11-22
it is better if u open programs as root only if it is required, else the normal user works just awesome.

---

