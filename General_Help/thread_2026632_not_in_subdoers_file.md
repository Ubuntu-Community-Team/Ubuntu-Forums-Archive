---
title: "not in subdoers file"
date: 2012-07-15
forum: General Help
---

### Post by goodbye-windows(tm) on 2012-07-15
I have a new Xubuntu 12.04 instillation. 

The install went well, and everything worked, with one major exception and a few very minor exceptions.

The biggie right now is getting encrypted cd's to play.

I'm following the tutorial for the process at:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

In the first step of the encryption installation process, I open the terminal and enter:

```
sudo -E wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo sed -i "/^# deb .*partner/ s/^# //" /etc/apt/sources.list && sudo apt-get --quiet update && sudo apt-get -y --force-yes --quiet --allow-unauthenticated install medibuntu-keyring app-install-data-medibuntu apport-hooks-medibuntu && sudo apt-get update

```

When I am asked for the password, I enter it, and it tells me I'm not in the subdoers file and that the incident will be reported.

I've used sudo on the new installation before this, so something I've done recently has changed.....

What's interesting is that I type in gibberish at the password command, and it responds with 'try again'. When I enter in the correct password, it says the incident will be reported.

Any idea what's going on?

TY.

Art

---

### Post by ajgreeny on 2012-07-15
Have you at some point used sudo to start a GUI (gnome or kde or xfce) application instead of the correct gksu or kdesu.  If you have it can occasionally cause the problem you are seeing now.

Compare your sudoers file which you can see with ```
sudo cat /etc/sudoers
``` with this default version, and if necessary edit yours to the same content with ```
sudo visudo
``` which opens it with root permissions in nano, a cli editor.

---

### Post by ajgreeny on 2012-07-15
Have you at some point used sudo to start a GUI (gnome or kde or xfce) application instead of the correct gksu or kdesu.  If you have it can occasionally cause the problem you are seeing now.

Compare your sudoers file which you can see with ```
sudo cat /etc/sudoers
``` with this default version, and if necessary edit yours to the same content with ```
sudo visudo
``` which opens it with root permissions in nano, a cli editor.
```
#
# This file MUST be edited with the 'visudo' command as root.
#
# Please consider adding local content in /etc/sudoers.d/ instead of
# directly modifying this file.
#
# See the man page for details on how to write a sudoers file.
#
Defaults    env_reset
Defaults    secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL:ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
%sudo    ALL=(ALL:ALL) ALL

# See sudoers(5) for more information on "#include" directives:

#includedir /etc/sudoers.d
```

---

### Post by goodbye-windows(tm) on 2012-07-15
> **ajgreeny said:**
> Have you at some point used sudo to start a GUI (gnome or kde or xfce) application instead of the correct gksu or kdesu.  If you have it can occasionally cause the problem you are seeing now.

Compare your sudoers file which you can see with ```
sudo cat /etc/sudoers
``` with this default version, and if necessary edit yours to the same content with ```
sudo visudo
``` which opens it with root permissions in nano, a cli editor.

Both of these commands are rejected, because the system won't let me do any sudo commands-says not in subdoers file.

Can I do this from the super users account? After I got Xubuntu running, I created a separate account for myself and have been using that account.

Can I look at the subdoers file by booting with the live cd?

TY.

Art

---

### Post by goodbye-windows(tm) on 2012-07-15
I logged in as the super user, and was able to read the subdoers file.

This is it......

```
nowinderz@nowinderz-MS-7104:~$ sudo cat /etc/sudoers
[sudo] password for nowinderz: 
#
# This file MUST be edited with the 'visudo' command as root.
#
# Please consider adding local content in /etc/sudoers.d/ instead of
# directly modifying this file.
#
# See the man page for details on how to write a sudoers file.
#
Defaults    env_reset
Defaults    secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL:ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
%sudo    ALL=(ALL:ALL) ALL

# See sudoers(5) for more information on "#include" directives:

#includedir /etc/sudoers.d
nowinderz@nowinderz-MS-7104:~$ 
```

---

### Post by OM55 on 2012-07-15
In order to be allowed to use sudo command you have to be in the administrator group or an administrator. Even if beforehand you were an administrator, if you removed this privilage from your user, you have to add it first. If there is no other administrator password - you may be out of luck. 
If you had previously specifically set a password for the root user, you could have SSH in from another machine as root and correct the privilages of your user, but I assume you did not do that.

So what I suggest is to try to add your username to the administrator group and hopefully that would be sufficient.

---

### Post by ajgreeny on 2012-07-15
> **goodbye-windows(tm) said:**
> Both of these commands are rejected, because the system won't let me do any sudo commands-says not in subdoers file.

Can I do this from the super users account? After I got Xubuntu running, I created a separate account for myself and have been using that account.

Can I look at the subdoers file by booting with the live cd?

TY.

Art
So have you got two users on the machine, the one original one that you are calling super-user, and a second that you subsequently added for your everyday use?

Only the first user made during installation of ubuntu will be a member of the admin group and able to use sudo; all other users will not be admin group members and will therefore not be able to use sudo.  You can see what groups each of those two users is in from the **Users & Groups** menu item.

---

### Post by Morbius1 on 2012-07-15
@ajgreeny, this is probably an unwelcomed interruption and I'm not in Linux at the moment but didn't 12.04 mess with the admin group? It's adm now and I'm not sure sudo is part of it. Anyway, can't he just add the other user to the sudo group:
```
sudo gpasswd -a other-user sudo
```

---

### Post by goodbye-windows(tm) on 2012-07-15
> So have you got two users on the machine, the one original one that you are calling super-user, and a second that you subsequently added for your everyday use?

Yes, the original user, the one I call 'super user' (in this case, is called nowinderz. I did the bulk of the updating, adding software and fine tuning from the super users account.

After I got things reasonably well updated with most of the software, I added a second user for myself, called 'artie'. 

I'm fairly certain that I used the sudo command from artie's account before, but perhaps I am in error.

The following was asked earlier.....

> Have you at some point used sudo to start a GUI (gnome or kde or xfce) application instead of the correct gksu or kdesu. Yes, I probably did do that, but am not positive. I did download another search utility to replace ;catfish;. Catfish comes with Xubuntu, but it leaves much to be desired. A user on this forum suggested using a KDE search utility called kfind. I downloaded, installed it from the software center. But, after the install, I couldn't locate it with in the menus anywhere. A user here suggested I try to run it from the command line.

```

kfind

```When I tried it in terminal mode, it started great. But the gui interface came up.

I tested it, found it worked ok and I'm currently looking for info on how to manually add an entry to the menu or the launcher.  But, I did run a gui that was made for KDE.

I'll see if I can add myself to the admin group. I'm new, but am learning FAST!!!!

TY.

Art

---

### Post by goodbye-windows(tm) on 2012-07-15
>  
this is probably an unwelcomed interruption and I'm not in Linux at the moment but didn't 12.04 mess with the admin group? It's adm now and I'm not sure sudo is part of it. Anyway, can't he just add the other user to the sudo group:


```
sudo gpasswd -a other-user sudo
```OK, I tried this from the super users account and it went well. It told me 'artie' was added to the sudo group.

I'm going to switch over to artie's account now and see if I can do sudo commands.

BRB.

Art

---

### Post by goodbye-windows(tm) on 2012-07-15
Yes, it works now!!! What a big difference a few characters typed in the terminal can make!!! 

Here's what happened when I tested....

```

artie@nowinderz-MS-7104:~$ sudo mount
[sudo] password for artie: 
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/artie/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=artie)
artie@nowinderz-MS-7104:~$ 


```

I am getting an error report, which I thought i had cleared. It had to do with abiword, which is now included in Xubuntu. I uninstalled abiword though, not sure why I'm still getting as error message. I am prompted for a password to report the error, but I don't have any idea what it's about. Hopefully it will stop soon::>

TY to all, back to trying to add decryption for cd's now.

Art

---

### Post by ajgreeny on 2012-07-16
> **Morbius1 said:**
> @ajgreeny, this is probably an unwelcomed interruption and I'm not in Linux at the moment but didn't 12.04 mess with the admin group? It's adm now and I'm not sure sudo is part of it. Anyway, can't he just add the other user to the sudo group:
```
sudo gpasswd -a other-user sudo
```
Crikey, you're correct!

I had not picked up on that change, so thanks for the heads-up.  Why was the change made; any idea?

---

### Post by Morbius1 on 2012-07-16
> **ajgreeny said:**
> I had not picked up on that change, so thanks for the heads-up.  Why was the change made; any idea?
I don't know about you but I never read the release notes but if I had:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop]("https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop:")
> Up until Ubuntu 11.10, administrator access using the sudo tool was granted via the "admin" Unix group. In Ubuntu 12.04, administrator access will be granted via the "sudo" group. This makes Ubuntu more consistent with the upstream implementation and Debian. For compatibility purposes, the "admin" group will continue to provide sudo/administrator access in 12.04. 
I think "admin" was always an Ubuntu thing since I don't remember it in Debian. The only problem with the quote above is that as far as I can tell there is no admin group "for compatibility purposes" or otherwise. So I don't know if they are just saying that to keep us confused or what :)

---

### Post by ajgreeny on 2012-07-16
> **Morbius1 said:**
> I don't know about you but I never read the release notes but if I had:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop:](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop:)
I think "admin" was always an Ubuntu thing since I don't remember it in Debian. The only problem with the quote above is that as far as I can tell there is no admin group "for compatibility purposes" or otherwise. So I don't know if they are just saying that to keep us confused or what :)
I usually skate over them very quickly, but as you can see, I'm still using 10.04 on my main system.

I have Lubuntu 12.04 on a netbook, and several other distros of the ubuntu family on test partitions of a second disk in my main machine, but I have not really used them much so far other than to see which DE I like best.

Very curious about the lack of an admin group in spite of the release notes saying there would still be one "for compatibility purposes", but I suppose at some point it was decided that it was not really needed, and the sudo group was all that was necessary.

Confusing, isn't it?  Though I suppose it makes some sense that the users permitted to use "sudo" should be in a group by with the same name.

---

### Post by steeldriver on 2012-07-16
although there's no actual admin group in a clean install, there's a legacy entry for admin in /etc/sudoers - I guess that means if you import an existing user / group structure into 12.xx it doesn't break it?

```
# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
%sudo    ALL=(ALL:ALL) ALL

```

---

