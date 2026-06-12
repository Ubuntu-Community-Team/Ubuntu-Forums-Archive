---
title: "Starting programs that require sudo"
date: 2006-06-12
forum: General Help
---

### Post by bohboh on 2006-06-12
I have several programs that need to be run with sudo.

e.g. vmplayer

So to run it i can do

sudo vmplayer

and it works.

From the main Applications/System Tools directory the vmplayer shortcut just has the command "vmplayer". Which doesnt work. So i added sudo and it asks for the password.

Is there a way to run programs from the menu and from startup scripts (.bash) in sudo mode and for it to not ask for a password.

TIA.

---

### Post by mlind on 2006-06-12
read sudo manual and look for NOPASSWD definition
'man sudo' on terminal.

---

### Post by bohboh on 2006-06-12
[QUOTE=mlind]read sudo manual and look for NOPASSWD definition
'man sudo' on terminal.[/QUOTE]

Thanks for that.

I tried editing /etc/sudoers but the file is readonly. So i log in as root and i get the following 

root@mypc:/home/mickey# gedit /etc/sudoers
(gedit:7538): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

Same happens when i run "sudo gedit /etc/sudoers"
How do i go about editing the file?

---

### Post by jocko on 2006-06-12
The only way to edit the sudoers file is this:
```
sudo visudo
```

but make sure you know what you do before you save the changes... I've seen people on this forum that completely lost the permission to use sudo...

---

### Post by aysiu on 2006-06-12
VMPlayer requires root?

Mine doesn't. I mean, it required root to be installed, but now that it's installed, anyone can use it.

---

### Post by bohboh on 2006-06-12
[QUOTE=aysiu]VMPlayer requires root?

Mine doesn't. I mean, it required root to be installed, but now that it's installed, anyone can use it.[/QUOTE]

So can you run it from your Applications menu?

If i run it from the command line i get this and the program doesnt start: 
someone@mypc:~$ vmplayer
/usr/lib/vmware/bin/vmplayer: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)

Yet if i do 

someone@mypc:~$ sudo vmplayer
/usr/lib/vmware/bin/vmplayer: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)

it works.

Has mine somehow been set up differently?

---

### Post by aysiu on 2006-06-12
I'm not sure. Can we get someone else to jump in on this? All I know is that my VMPlayer (either the one I installed from the VMPLayer .tar.gz or the one from the Dapper Multiverse repositories) has never required sudo access to run.

Anyone else use VMPlayer? Do you need sudo access for it?

---

### Post by scxtt on 2006-06-12
when i used VMWare Server it required root access - i'm fairly certain i did install it via sudo ... and i'd just use "run as a different user" from the menu to start it ...

---

### Post by aysiu on 2006-06-12
Is it possible, though, scxtt, that VMWare Server and VMPlayer require different permissions?

---

### Post by jasay on 2006-06-12
I run vmware server as user.

I had the same error though (but it still ran just fine) until I ```
sudo cp /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0
```

You might do a ```
locate libpng12.so.0
``` to make sure the path above is correct.

---

### Post by grendelkhan on 2006-06-12
I had to make links for these files:

/usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0
/usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1

I linked them to the ones on my system:

/usr/lib/libpng12.so.0
/lib/libgcc_s.so.1

Once I did that, WMWare Workstation ran like a champ for me, but I had no problem at all getting VMWare Player to work.  It's even in Multiverse if I recall correctly.

---

### Post by bohboh on 2006-06-12
[QUOTE=grendelkhan]I had to make links for these files:

/usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0
/usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1

I linked them to the ones on my system:

/usr/lib/libpng12.so.0
/lib/libgcc_s.so.1

Once I did that, WMWare Workstation ran like a champ for me, but I had no problem at all getting VMWare Player to work.  It's even in Multiverse if I recall correctly.[/QUOTE]

Are you saying i need to make symbolic links in /usr/lib/vmware/lib/ to point to
the ones in 
/usr/lib/

There are already files there with those names, should i rename them?

---

### Post by bohboh on 2006-06-12
Ok, with your help i have managed to stop the lib errors. But i still cant get it to run without sudo.

Any ideas?

---

### Post by scxtt on 2006-06-12
[QUOTE=aysiu]Is it possible, though, scxtt, that VMWare Server and VMPlayer require different permissions?[/QUOTE]quite possible, i never used the player in Ubuntu (did in windows, didn't like it much) so i used the server from then on - and had no problems "running as root" (as in it didn't bother me to do that) ... i don't remember running it from the command line - actually i think there was an icon for it in my menu and the main reason i was running it as root was because i was sharing VMs b/t Ubuntu and Windows (but the drive they were saved on belonged to root and i didn't feel like changing that) ...

---

### Post by bohboh on 2006-06-12
[QUOTE=scxtt]quite possible, i never used the player in Ubuntu (did in windows, didn't like it much) so i used the server from then on - and had no problems "running as root" (as in it didn't bother me to do that) ... i don't remember running it from the command line - actually i think there was an icon for it in my menu and the main reason i was running it as root was because i was sharing VMs b/t Ubuntu and Windows (but the drive they were saved on belonged to root and i didn't feel like changing that) ...[/QUOTE]

Yeah, there is an icon. I get the "Starting VMPlayer" in the taskbar, then it just disappears. 

I have installed in, reinstalled it. All with the same result.

---

### Post by bohboh on 2006-06-13
Ah. When i run vmware-config.pl i get this:

=Start Paste=
Making sure services for VMware Player are stopped.

Stopping VMware services:
   Virtual machine monitor                                     done
   Bridged networking on /dev/vmnet0                     done
   DHCP server on /dev/vmnet1                              done
   Host-only networking on /dev/vmnet1                  done
   DHCP server on /dev/vmnet8                              done
   NAT service on /dev/vmnet8                              done
   Host-only networking on /dev/vmnet8                 done
   Virtual ethernet                                               failed
Unable to stop services for VMware Player

Execution aborted.
=End Paste=

As you can see, Virutal ethernet failed.

EDIT:

I managed to kill the pid and stop the service, i then reran vmware-config.pl and it bombs out at ...

== Start paste
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Player is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.15-23-386/build/include]

Extracting the sources of the vmmon module.

tar: /usr/lib/vmware-player/modules/source/vmmon.tar: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
Unable to untar the "/usr/lib/vmware-player/modules/source/vmmon.tar" file in
the "/tmp/vmware-config3" directory.

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.
== End paste

I know that the kernel headers exist as i installed them previously.

Edit:
Managed to get it working again, but only with sudo. So back to square 1.

---

