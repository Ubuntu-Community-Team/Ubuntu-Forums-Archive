---
title: "Help me with the final push away from Windows"
date: 2006-06-14
forum: General Help
---

### Post by flub on 2006-06-14
HI all,

I've been using Ubuntu Breezy and now Dapper for 6 months and love it. I'm running on a dual boot with XP SP2 and Dapper. Each week I remove more and more programs from the Windows partition as I find and become proficiant with their Linux equivilant. I'm now very near to removing the Windows partition competely.

The following is stopping me.

[COLOR="Silver"]1) Is there a basic video editing package that can be installed in Ubuntu?[/COLOR] **ANSWERED**

[COLOR="Silver"]2) I'm still not sure if I need a Virus Scanner for Ubuntu (for Windows I use ZoneAlarm Spyware and Virus Scanner)[/COLOR] **ANSWERED**

[COLOR="Silver"]3) As above but for Firewall.[/COLOR] **ANSWERED**

[COLOR="Silver"]4) How can I backup just my settings and preferences? and how do I restore them if needed?[/COLOR] **ANSWERED**

[COLOR="Silver"]5) New PC. If I get a new pc how can I quickly transfer over my setup from my old PC. I would like to preserve my alias, mounts, printer settings etc[/COLOR] **ANSWERED**


[COLOR="Silver"]6) Is there a "Virtual CD/DVD Drive" program. Much like Daemon Tools or Alcohol 120% do for windows.[/COLOR] **ANSWERED**

Thanks in advance for any advice and help for finally getting me off Windows.

---

### Post by jethro10 on 2006-06-14
I'll try to help on some of these if I can.

1. [http://heroinewarrior.com/cinelerra.php3](http://heroinewarrior.com/cinelerra.php3) and here [http://cvs.cinelerra.org/](http://cvs.cinelerra.org/) looks advanced, but if you ignore most of it, its fine.

2. No scanner needed.

3. It's on by default, just hidden away. It's called iptables and disables most ports by default. Install Firestarter, i think its called as a front end to the firewall. But really just forget it.

4. I'd be interested in the answer to this but here is what I have. I re-installed and nearly everything was setup as it was, but I have 2 partitions. a 20Gb for root and this is basically your system disk with programs. And a second as /home/ which is your data disk. In your /home/user/ directory there is lots of files and folders that are hidden. these seem to hold most of the configuration. I just used the package manager, re-installed all software and everything was back to normal. This WONT work on a single partition as you will lose your /home/ directories. I'm sure there's lots more as i've just installed apache and some config files are on the root partition.

5.Not sure, 4. above may be the answer, just restore the /home/ directories.

6. no idea.

I'll follow this thread also as it raises some interesting questions on backup/resore.

J

---

### Post by kb3hkg on 2006-06-14
here are some answers for you numbered to match your questions

1) kino and cinelera are both for video editing
2)you don't necessarily need one but if you want one I recommend clam av
3)for a firewall I recommend you use firestarter
4)not sure on that one, other then finding the files for them and burning them to a disk
5)new pc, easiest would be to just create an image of the drive and transfer it, easiest done over network, or external hard drive
6)yes programs like Alcohol do exist but not sure of the names, it is also possible to mount an iso file as a drive in linux though

---

### Post by taloche on 2006-06-14
I can't answer all your questions, but here's what I know:

2. You don't need an antivirus. But you can try AVG if you really want one.

3. Ubuntu has a built-in firewall that you can configure with iptables. However, using iptables can quickly become painful so I suggest you use firehol. Firehol is a set of scripts that makes it very easy to configure iptables. I don't think that there's any gui to configure it, but there is a good tutorial at [http://firehol.sourceforge.net/](http://firehol.sourceforge.net/).

4. Essentially, you have two different kinds of settings in linux:
* User-specific settings (your gnome session, your firefox theme, your mail account, etc.. ) are stored in your home folder (located in /home/yourlogin).
* Application settings (firewall configuration, hostname, network config, etc... ) are stored in /etc.

By default, ubuntu creates two separate partitions for / and /home. Think of it as C: = / and D: = /home. If you go from / to /home, you go to a different drive. Reinstalling ubuntu will erase / (and /etc) but not /home (so you keep your user settings). Basically:

* If you want to save your user settings, backup your /home/user directory 
* If you want to keep your global settings, backup your /etc directory. However, note that brutally restoring an old backup of /etc might wreak havoc on your distro. Maybe someone knows about a dedicated program to handle that cleanly...

6. This can be done easily. Enter a shell an type:

sudo mkdir /media/iso
sudo mount cdimage.iso -o bind -t iso9660 /media/iso
The -t option might be optional. Check in man mount for the loopback option if you have troubles.

Good luck,

---

### Post by flub on 2006-06-14
Thanks guys, I've marked the original with the answered questions. I'll check out the video packages, they look pretty advanced which is great.

The who backup/restore etc I'll leave open to get some more responses.

---

### Post by flub on 2006-06-14
taloche, thanks for the great info on the User/Application settings and the ISO/Mount information. Very cool.

---

### Post by andb on 2006-06-14
2) Viruses take advantage of OS flaws. Most, if not nearly all, viruses are written for Windows. They will not affect any other system. You may want to install a virus scanner just to make sure that you dont forward infected attachments to your friends and colleagues.

3) Firewall is built in to the kernel. When the system starts, it configures the kernel firewall. Ubuntu starts with NO firewall. But, it starts NO services that listen. This is arguably as good as a firewall. Windows firewalls basically plug all the holes were listening services sit. No listening services, no holes. Firestarter is a great basic firewall and will show you whats happening. Even if firestarter GUI doesnt load, the firewall rules are loaded into the kernel at startup. 

4) In Nautalis, the file browser, pres ctrl-h. It will show you all the hidden files. These are the user specific config files. Different users can ha ve truly "different" interfaces to the same machine. Windows tried to do this but really only made different doc folders. The system config files are in /etc. Learn what files are needed for the software you run, back them up individually. I feel that its better to reconfigure the less complex services than to copy files. So often you upgrade software when you upgrade a machine. 

6) Not even needed. The system command "mount" with the "-o loop" switch will mount an iso on a mountpoint, for example /media/cdrom! Easy. It doesnt get around the nice copy protection that Deamon Tools will circumvent, but Im assuming you just want to use non-copywrited isos.

Best way to move over, just wipe out the old system and struggle a bit :) Sink or swim :) To learn more about whats under the hood, check out [http://learnlinux.tsf.org.za/](http://learnlinux.tsf.org.za/) They have some great docs about fundementals, networking, scripting... Good stuff.

---

### Post by flub on 2006-06-14
andb, thank you very much for the post and the information. Very much appreciated.

I think I will wipe my Windows after I've checked out the video software.

---

### Post by prash@linuxitarian on 2006-06-14
4) How can I backup just my settings and preferences? and how do I restore them if needed?

There are command line ways to backup but perhaps the easiest graphical utility is "keep" (KDE). Check it out, I think it lets you backup the way you want to.

As mentioned before, you transfer your old setup by restoring the backup to your new pc.

---

### Post by nocturn on 2006-06-14
4 and 5 are partially solved by backing up your home directory.

Most settings are in files beginning with a dot (.), they are hidden by default.

---

### Post by flub on 2006-06-14
Thanks everyone, I'm very impressed not only with the Software but with the people :)

My Windows partition is currently formatting !!!!

---

