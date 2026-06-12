---
title: "Problems unlocking LUKS encrypted LVM via SSH"
date: 2010-12-18
forum: General Help
---

### Post by DarkBabar on 2010-12-18
I'm trying to unlock a LUKS encrypted LVM, on which the system resides, via SSH. I am following instructions found in the file "/usr/share/doc/cryptsetup/README.remote.gz" but I'm not having any success.

```
unlocking rootfs via ssh login in initramfs
-------------------------------------------

You can unlock your rootfs on bootup from remote, using ssh to log in to the
booting system while it's running with the initramfs mounted.


Setup
-----

For remote unlocking to work, the following packages have to be installed
before building the initramfs: dropbear busybox

The file /etc/initramfs-tools/initramfs.conf holds the configuration options
used when building the initramfs. It should contain BUSYBOX=y (this is set as
the default when the busybox package is installed) to have busybox installed
into the initramfs, and should not contain DROPBEAR=n, which would disable
installation of dropbear to initramfs. If set to DROPBEAR=y, dropbear will
beinstalled in any case; if DROPBEAR isn't set at all, then dropbear will only
be installed in case of an existing cryptroot setup.

The host keys used for the initramfs are dropbear_dss_host_key and
dropbear_rsa_host_key, both located in/etc/initramfs-tools/etc/dropbear/.
If they do not exist when the initramfs is compiled, they will be created
automatically. Following are the commands to create them manually:

# dropbearkey -t dss -f /etc/initramfs-tools/etc/dropbear/dropbear_dss_host_key
# dropbearkey -t rsa -f /etc/initramfs-tools/etc/dropbear/dropbear_rsa_host_key

As the initramfs will not be encrypted, publickey authentication is assumed.
The key(s) used for that will be taken from
/etc/initramfs-tools/root/.ssh/authorized_keys.
If this file doesn't exist when the initramfs is compiled, it will be created
and /etc/initramfs-tools/root/.ssh/id_rsa.pub will be added to it.
If the latter file doesn't exist either, it will be generated automatically -
you will find the matching private key which you will later need to log in to
the initramfs under /etc/initramfs-tools/root/.ssh/id_rsa (or id_rsa.dropbear
in case you need it in dropbear format). Following are the commands to do the
respective steps manually:

To create a key (in dropbear format):

# dropbearkey -t rsa -f /etc/initramfs-tools/root/.ssh/id_rsa.dropbear

To convert the key from dropbear format to openssh format:

# /usr/lib/dropbear/dropbearconvert dropbear openssh \
        /etc/initramfs-tools/root/.ssh/id_rsa.dropbear \
        /etc/initramfs-tools/root/.ssh/id_rsa

To extract the public key:

# dropbearkey -y -f /etc/initramfs-tools/root/.ssh/id_rsa.dropbear | \
        grep "^ssh-rsa " > /etc/initramfs-tools/root/.ssh/id_rsa.pub

To add the public key to the authorized_keys file:

# cat /etc/initramfs-tools/root/.ssh/id_rsa.pub >> /etc/initramfs-tools/root/.ssh/authorized_keys

In case you want some interface to get configured using dhcp, setting DEVICE= in
/etc/initramfs-tools/initramfs.conf should be sufficient.  The initramfs should
also honour the ip= kernel parameter.
In case you use grub, you probably might want to set it in /boot/grub/menu.lst,
either in the '# kopt=' line or appended to specific 'kernel' line(s).
The ip= kernel parameter is documented in Documentation/nfsroot.txt in the
kernel source tree.


Issues
------

Don't forget to run update-initramfs when you changed the config to make it
effective!

Collecting enough entropy for the ssh daemon sometimes seems to be an issue.
Startup of the ssh daemon might be delayed until enough entropy has been
retrieved. This is non-blocking for the startup process, so when you are at the
console you won't have to wait for the sshd to complete its startup.


Unlocking procedure
-------------------

To unlock from remote, you could do something like this:

# ssh -o "UserKnownHostsFile=~/.ssh/known_hosts.initramfs" \
        -i "~/id_rsa.initramfs" root@initramfshost.example.com \
        "echo -ne \"secret\" >/lib/cryptsetup/passfifo"

This example assumes that you have an extra known_hosts file
"~/.ssh/known_hosts.initramfs" which hold's the cryptroot system's host-key,
that you have a file "~/id_rsa.initramfs" which holds the authorized-key for
the cryptroot system, that the cryptroot system's name is
"initramfshost.example.com", and that the cryptroot passphrase is "secret"

-- <debian@x.ray.net>, Wed, 30 Sep 2009
```

I'm trying to unlock using this method, but I get "Permission denied (publickey,password)".
```
# ssh -o "UserKnownHostsFile=~/.ssh/known_hosts.initramfs" \
        -i "/home/darkbabar/id_rsa.initramfs" root@192.168.1.121 \
        "echo -ne \"encryptionpassphrase\" >/lib/cryptsetup/passfifo"
```

The file "/home/darkbabar/id_rsa.initramfs" is a copy of the file "/etc/initramfs-tools/root/.ssh/id_rsa.pub" from the host. The root account has a password set. Could somebody please help me figure out what I'm doing wrong?

---

### Post by DarkBabar on 2010-12-21
Somebody must know a solution to my problem. I can't be the only one wanting to do this.

---

### Post by aeiah on 2010-12-21
have you made sure root is allowed to login via ssh? i dont know if just setting a root password in ubuntu allows this or whether you'll have to specify it in dropbear or whatever. normally you'd do it with /etc/ssh/sshd_config with 'PermitRootLogin yes', but it may be different since you're using dropbear and most system stuff is encrypted at that point.

---

### Post by frostschutz on 2010-12-21
Does your initramfs set up networking at all? And/or do you have supplied the necessary kernel parameters so the kernel sets up networking by itself? (Can you ping the machine when it's supposedly waiting for SSH connection?) Otherwise you may have SSH installed in your initramfs but no network... which is not entirely useful.

---

### Post by DarkBabar on 2010-12-21
> **frostschutz said:**
> Does your initramfs set up networking at all? And/or do you have supplied the necessary kernel parameters so the kernel sets up networking by itself? (Can you ping the machine when it's supposedly waiting for SSH connection?) Otherwise you may have SSH installed in your initramfs but no network... which is not entirely useful.

Yes, the the network is functioning correctly and the server is pingable.

---

### Post by DarkBabar on 2010-12-22
> **aeiah said:**
> have you made sure root is allowed to login via ssh? i dont know if just setting a root password in ubuntu allows this or whether you'll have to specify it in dropbear or whatever. normally you'd do it with /etc/ssh/sshd_config with 'PermitRootLogin yes', but it may be different since you're using dropbear and most system stuff is encrypted at that point.

Root login is permitted. I can login as root with Dropbear after the boot process is complete.

---

### Post by olF23 on 2010-12-23
> **DarkBabar said:**
> The file "/home/darkbabar/id_rsa.initramfs" is a copy of the file "/etc/initramfs-tools/root/.ssh/id_rsa.pub" from the host.

I'm not sure, but shouldn't it be a copy of the *private* key */etc/initramfs-tools/root/.ssh/id_rsa*? 

I hope, this helps. Just found this possibility, so it's more guessing than knowing ;)

Merry Christmas
Flo

---

### Post by Lusen on 2010-12-28
Hi 
> I'm not sure, but shouldn't it be a copy of the *private* key /etc/initramfs-tools/root/.ssh/id_rsa?

Yes "-i "/home/darkbabar/id_rsa.initramfs"" is a copy of "/etc/initramfs-tools/root/.ssh/id_rsa"

I have a problem to.

I have followed this one "/usr/share/doc/cryptsetup/README.remote.gz"

Done this
```

#nano /etc/initramfs-tools/initramfs.conf
    add DROPBEAR=y and chek BUSYBOX=y

#apt-get install dropbear busybox
#cp /etc/initramfs-tools/root/.ssh/id_rsa to remote machine
#update-initramfs -u
#reboot

```
On console it says Enter passphrase: _

---Remote machine-----
```

#touch known_hosts.initramfs    
#ssh -o "UserKnownHostsFile=known_hosts.initramfs" -i "id_rsa" root@192.168.58.131

```
This works and I am logged in

```

#ssh -o "UserKnownHostsFile=known_hosts.initramfs" -i "id_rsa" root@192.168.58.131 "echo -ne \"testpassword\" >/lib/cryptsetup/passfifo"

```
I file with the password is in /lib/cryptsetup/passfifo but nothing happens.

I am running Ubuntu 10.04 LTS server

---

### Post by olF23 on 2010-12-28
Hello

> **Lusen said:**
> 
Yes "-i "/home/darkbabar/id_rsa.initramfs"" is a copy of "/etc/initramfs-tools/root/.ssh/id_rsa"
okay, good. Because in the original post is says to be a copy of the pub-Key. So if this is not a typing mistake, it could be the reason for the problem...


> **Lusen said:**
> ```

#ssh -o "UserKnownHostsFile=known_hosts.initramfs" -i "id_rsa" root@192.168.58.131 "echo -ne \"testpassword\" >/lib/cryptsetup/passfifo"

```
I file with the password is in /lib/cryptsetup/passfifo but nothing happens.


There shouldn't be a *file* there, but a (fifo) queue. This means, the input isn't stored there, but passed to the promt awaiting the password to decrypt the drive. Therefor, a *cat /lib/cryptsetup/passfifo* shouldn't return anything.

If you can already log into your machine, try decrypting it manually:
```

echo -ne yourpassword > /lib/cryptsetup/passfifo

```
This is what should be done automatically with your stated commandline, but maybe there are some special characters that need to be escaped.

Greetings,
Flo

---

### Post by DarkBabar on 2010-12-28
> **olF23 said:**
> I'm not sure, but shouldn't it be a copy of the *private* key */etc/initramfs-tools/root/.ssh/id_rsa*? 

I hope, this helps. Just found this possibility, so it's more guessing than knowing ;)

Merry Christmas
Flo

Thank you very much! This solved part of my problem. Unfortunately, now I have the same problem as Lusen. I can log in now, but the volume stays locked even with "echo -ne yourpassword > /lib/cryptsetup/passfifo". My password doesn't contain any special characters.

---

### Post by olF23 on 2010-12-28
Hi,

> **DarkBabar said:**
> the volume stays locked even with "echo -ne yourpassword > /lib/cryptsetup/passfifo".

I just found, that if you enter a wrong password you get the same output (on an attached monitor) as if you entered it on the keyboard. Do you receive any messages on your monitor indicating something like that?

If not, try passing an invalid password to provoke such a message.

Greetings,
Flo

---

### Post by DarkBabar on 2010-12-29
> **olF23 said:**
> Hi,



I just found, that if you enter a wrong password you get the same output (on an attached monitor) as if you entered it on the keyboard. Do you receive any messages on your monitor indicating something like that?

If not, try passing an invalid password to provoke such a message.

Greetings,
Flo

I'm not getting any output on the monitor, regardless if I enter the correct password or an incorrect one.

I just noticed that there is no "/lib/cryptsetup/passfifo", so issuing "echo -ne yourpassword > /lib/cryptsetup/passfifo" creates a regular file with that name.

---

### Post by olF23 on 2010-12-29
Hi,

> **DarkBabar said:**
> I just noticed that there is no "/lib/cryptsetup/passfifo", so issuing "echo -ne yourpassword > /lib/cryptsetup/passfifo" creates a regular file with that name.

hm, that is pretty bad^^

I just found a bug report[1] that makes Plymouth responsible for all the mess. There's a workaroung stated (don't forget to update your initramfs). The other option would be uninstalling Plymouth..

Unfortunately, I cannot verify this, as my machine is running debian, but maybe it still helps.

Greetings
Flo

[1] [https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/595648](https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/595648)

---

### Post by DarkBabar on 2010-12-29
> **olF23 said:**
> Hi,



hm, that is pretty bad^^

I just found a bug report[1] that makes Plymouth responsible for all the mess. There's a workaroung stated (don't forget to update your initramfs). The other option would be uninstalling Plymouth..

Unfortunately, I cannot verify this, as my machine is running debian, but maybe it still helps.

Greetings
Flo

[1] [https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/595648](https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/595648)

Finally it works! The workaround did the trick. Thank you very, very much for your help! :D

---

### Post by DarkBabar on 2011-01-10
Now I can't enter the encryption password locally anymore, since I applied the hack described earlier. :(
Never mind, I seldom want to do that anyway.

---

### Post by haroldx on 2011-04-13
how do I set IP?
can not figure it out, it keeps on running DHCP
I attempted many possible configurations of  /etc/initramfs-tools/initramfs.conf
Divice=eth0
ip=192.168.0.22

anything i try is ignored, adding ifconfig command to 
somewhere in /usr/share/initramfs-tools/scripts  doesn't do it ether.
Running ubuntu server 10.10....

other than that, i can connect and remotely unlock.
This fix helped me

 [FONT=Calibri]comment the lines in /usr/share/initramfs-tools/scripts/local-top/cryptroot like this:[/FONT]
  [FONT=Calibri]if [ -z "$cryptkeyscript" ]; then[/FONT]
  [FONT=Calibri]   cryptkey="Unlocking the disk $cryptsource ($crypttarget)\nEnter passphrase: "[/FONT]
  [FONT=Calibri]   #if [ -x /bin/plymouth ] && plymouth --ping; then[/FONT]
  [FONT=Calibri]   # cryptkeyscript="plymouth ask-for-password --prompt"[/FONT]
  [FONT=Calibri]   # cryptkey=$(echo -e "$cryptkey")[/FONT]
  [FONT=Calibri]   #else[/FONT]
  [FONT=Calibri]    cryptkeyscript="/lib/cryptsetup/askpass"[/FONT]
  [FONT=Calibri]   #fi[/FONT]
  [FONT=Calibri]  fi[/FONT]
  [FONT=Calibri] [/FONT]
[FONT=Calibri]
[/FONT]
  [FONT=Calibri] [/FONT]
[FONT=Calibri][DarkBabar]("http://ubuntuforums.org/member.php?u=137285") - where you able to overcome that local-console password problem?[/FONT]
[FONT=Calibri]it has to do with the fix poster above, but I am not much of a coder, never figure a way to get it to allow both.
[/FONT]
  


also these scripts worked like a charm:


1st:
 [FONT=Calibri]#!/bin/sh[/FONT]
  [FONT=Calibri]#
# This InitRAMFS hook provides:
# Simple script to easily unlock LUKS encrypted root partition from remote (SSH, Telnet)
# Intended for Debian 6.0 Squeeze
#
# Copyright: Matthias Bücher, see [http://www.maddes.net/](http://www.maddes.net/)
# License: GNU GPL v2 or later, see [http://www.gnu.org/licenses/gpl.html](http://www.gnu.org/licenses/gpl.html)
#
# Adopted from [http://www.howtoforge.com/unlock-a-luks-encrypted-root-partition-via-ssh-on-ubuntu#comment-25990](http://www.howtoforge.com/unlock-a-luks-encrypted-root-partition-via-ssh-on-ubuntu#comment-25990)
#
# Thanks to:
# - Wulf Coulmann; [http://gpl.coulmann.de/ssh_luks_unlock.html](http://gpl.coulmann.de/ssh_luks_unlock.html)
#   for his tremendeous effort to unlock LUKS root parititon remotely on Debian 5.0 Lenny and before
#
# How to use:
# - Copy this hook script as /usr/share/initramfs-tools/hooks/cryptroot_unlock
# - chmod +x /usr/share/initramfs-tools/hooks/cryptroot_unlock
# - update-initramfs -u
#
# History:
# v1.0 - 2011-02-15
#  initial release
#[/FONT]
  [FONT=Calibri]PREREQ=""[/FONT]
  [FONT=Calibri]prereqs()
{
        echo "$PREREQ"
}[/FONT]
  [FONT=Calibri]case $1 in
prereqs)
        prereqs
        exit 0
        ;;
esac[/FONT]
  [FONT=Calibri]. /usr/share/initramfs-tools/hook-functions[/FONT]
  [FONT=Calibri]#
# Begin real processing
#[/FONT]
  [FONT=Calibri]SCRIPTNAME=unlock[/FONT]
  [FONT=Calibri]# 1) Create script to unlock luks partitions
cat > ${DESTDIR}/bin/${SCRIPTNAME} << '__EOF'
#!/bin/sh
/lib/cryptsetup/askpass "Enter volume password: " > /lib/cryptsetup/passfifo
__EOF
chmod 700 ${DESTDIR}/bin/${SCRIPTNAME}[/FONT]
  [FONT=Calibri]# 2) Enhance Message Of The Day (MOTD) with info how to unlock luks partition
cat >> ${DESTDIR}/etc/motd << '__EOF'[/FONT]
  [FONT=Calibri]To unlock root-partition run "${SCRIPTNAME}"
__EOF[/FONT]
  


2nd: 
 [FONT=Calibri]#!/bin/sh[/FONT]
  [FONT=Calibri]#
# This InitRAMFS script provides:
# Simple script to kill all DropBear client sessions if the InitRAMFS is left
# Intended for Debian 6.0 Squeeze
#
# Copyright: Matthias Bücher, see [http://www.maddes.net/](http://www.maddes.net/)
# License: GNU GPL v2 or later, see [http://www.gnu.org/licenses/gpl.html](http://www.gnu.org/licenses/gpl.html)
#
# Adopted from [http://www.howtoforge.com/unlock-a-luks-encrypted-root-partition-via-ssh-on-ubuntu#comment-25990](http://www.howtoforge.com/unlock-a-luks-encrypted-root-partition-via-ssh-on-ubuntu#comment-25990)
#
# Thanks to:
# - Wulf Coulmann; [http://gpl.coulmann.de/ssh_luks_unlock.html](http://gpl.coulmann.de/ssh_luks_unlock.html)
#   for his tremendeous effort to unlock LUKS root parititon remotely on Debian 5.0 Lenny and before
#
# How to use:
# - Copy this hook script as /usr/share/initramfs-tools/scripts/local-bottom/dropbear_kill_clients
# - chmod +x /usr/share/initramfs-tools/scripts/local-bottom/dropbear_kill_clients
# - update-initramfs -u
#
# History:
# v1.0 - 2011-02-15
#  initial release
#[/FONT]
  [FONT=Calibri]PREREQ=""[/FONT]
  [FONT=Calibri]prereqs()
{
        echo "$PREREQ"
}[/FONT]
  [FONT=Calibri]case $1 in
prereqs)
        prereqs
        exit 0
        ;;
esac[/FONT]
  [FONT=Calibri]#
# Begin real processing
#[/FONT]
  [FONT=Calibri]NAME=dropbear
PROG=/sbin/dropbear[/FONT]
  [FONT=Calibri]# get all server pids that should be ignored
ignore=""
for server in `cat /var/run/${NAME}*.pid`
 do
        ignore="${ignore} ${server}"
done[/FONT]
  [FONT=Calibri]# get all running pids and kill client connections
for pid in `pidof "${NAME}"`
 do
        # check if correct program, otherwise process next pid
        grep -F -q -e "${PROG}" "/proc/${pid}/cmdline" || {
                continue
        }[/FONT]
  [FONT=Calibri]# check if pid should be ignored (servers)
        skip=0
        for server in ${ignore}
         do
                if [ "${pid}" == "${server}" ]
                 then
                        skip=1
                        break
                fi
        done
        [ "${skip}" -ne 0 ] && continue[/FONT]
  [FONT=Calibri]# kill process
        echo "$0: Killing ${pid}..."
        kill -KILL ${pid}
done[/FONT]
  [FONT=Calibri] [/FONT]


Thank for all the help in here, especially DarkBabar!!!
not much info about this technique out there.  I couldn't have done it without this thread!

---

### Post by carlkek on 2011-04-21
> **haroldx said:**
> how do I set IP?
can not figure it out, it keeps on running DHCP
I attempted many possible configurations of  /etc/initramfs-tools/initramfs.conf
Divice=eth0
ip=192.168.0.22


the syntax for what you want is:

```
ip=<client-ip>:<server-ip>:<gw-ip>:<netmask>:<hostname>:<device>:<autoconf>
```

as of where you can ignore the server-ip part, it's there cause of usage in nfsmounting the root partition

i just tested it on Ubuntu 10.10 with this line:

```
IP=192.168.1.150::192.168.1.1:255.255.255.0:testmachine:eth0:off
```

and it works just fine

a deeper explanation of all the paramaters in the ip line can be found [here]("http://www.kernel.org/doc/Documentation/filesystems/nfs/nfsroot.txt")

Best Regards
Martin

---

### Post by tue.kyndal on 2011-04-29
Hi.

I have followed all the guides described above in this post on a new Virtual Box ubuntu server 10.04 LTS for testing.

I have made both script files and correctly used chmod +x and updated the initramfs image with [FONT=Calibri] update-initramfs -[/FONT]u

I have also fixed the splash screen issue with:
/etc/default/grub

- GRUB_CMDLINE_LINUX_DEFAULT=&#8221;quiet splash&#8221; 

+ GRUB_CMDLINE_LINUX_DEFAULT=&#8221;"

And copyed the keys from the server to my laptop
 
scp /etc/initramfs-tools/root/.ssh/id_rsa [EMAIL="root@192.168.1.2:/root/.ssh"]root@192.168.1.2:/root/.ssh[/EMAIL]/id_rsa 

etc..etc...

I still don't get ssh login, and no decryption over ssh what so ever!
 

I also don't get a static ip -- still stuck with DHCP..which is not good for a headless server on my network.

HOW IS THIS CODE APPLIED in /etc/initramfs-tools/initramfs.conf?

IP=192.168.1.150::192.168.1.1:255.255.255.0:testmachine:eth0 off

It appears that everything now works natively in Debian, but not in Ubuntu.

I tested it with virtual box on debian 6.0, and it worked on my first try?

HOW CAN THIS BE? THIS IS UBUNTU 10.04 LTS....??????

There must be a guide that shows how this is done precisely for ubuntu!

Please help...I cannot be  the only one in the world who would like an encrypted ubuntu server! ...could I?

Im stress for time...need to chose on monday for the server setup..and as I see it, only option left is to change over to debian...which sux because I have everything else on ubuntu, and like it that way.

TK

---

### Post by alyandon on 2011-06-20
Sorry for the thread resurrection but this thread comes up quite often when searching for problems relating to unlocking a LUKS encrypted partition via SSH from inside initramfs.

If you are unable to connect as root to the dropbear instance after following the instructions in the original post you are most likely running a recent version of Ubuntu and have been bitten by a bug in the dropbear hook script in initramfs-tools.  Recent versions of Ubuntu seem to have reorganized the /lib directory and moved some files needed by dropbear without which it'll not be able to find "root" as a valid user.

First, run the following command to determine where the files you need are located:

find /lib -name libnss_files.so.2

On my system, I get the following:

/lib/i386-linux-gnu/libnss_files.so.2

The part you are interested in is the "**i386-linux-gnu**" part.  

Now, edit (as root) /usr/share/initramfs-toosl/hooks/dropbear.  Look around line 30 for the following:

cp /lib/libnss_* "${DESTDIR}/lib/"

Replace that with:

cp /lib/**i386-linux-gnu**/libnss_* "${DESTDIR}/lib/"

As root, run the following:
update-initramfs -u

You should now at least be able to connect to the dropbear instance with the dropbear key that was automagically generated.

Now, reboot your system and check to make sure you can connect to the dropbear instance.  To unlock your LUKS partition, use the steps below to work-around the plymouth issue (tested on Natty 11.04).  This work-around will at least guarantee that plymouth is still able to unlock the LUKS root volume at the console instead of being rendered non-functional like most of the other work-arounds I've tried.

1) run "ps aux" and located the process id for the /scripts/local-top/cryptroot script
2) run "kill -9 pid" replacing pid with the process id you found in step 1
3) run "ps aux" again and look for a wait-for-root script and note the timeout on the command line
4) twiddle you thumbs for that many seconds - what will happen is that script will exit and start an initramfs shell
5) run "/scripts/local-top/cryptroot" and wait for it to prompt for your unlock passphrase
6) enter the unlock passphrase and wait for it to return you to the busybox shell prompt
7) run "ps aux" again and locate the process id of "/bin/sh -i"
8) run "kill -9 pid" using the process id you found from step 7

initramfs should be continuing the boot process at this point with your mounted root volume.  You'll know this is happening because dropbear just had "/" yanked out from underneath it and you'll not be able to run any more commands in your ssh session as /bin no longer is available.  Go ahead and disconnect and wait an appropriate amount of time for your system to finish starting up. After your system has finished booting, you should now be able to connect to it remotely just as if you had typed your unlock passphrase into the console.

If someone more knowledgeable than me with the inner workings of initramfs-tools and plymouth wants to step up and file a proper bug report along with streamlining the work-around for plymouth I've listed.

---

### Post by moscao on 2011-07-07
A big thank u to you alyandon, this stupid change in the location of the libnss was driving me cray since my boot was not working anymore after my server update...!
There should be a clear guide/warning about all this procedure of booting remotely via ssh an encrypted LVM in the official ubuntu pages.

FYI, regarding the booting procedure I used the following procedure:

1) Replace the script cryptroot in /usr/share/initramfs-tools/hooks/ with the one provided here (in german):
[http://forum.ubuntuusers.de/topic/script-verschluesseltes-system-via-ssh-freisch/](http://forum.ubuntuusers.de/topic/script-verschluesseltes-system-via-ssh-freisch/)

2) In file /usr/share/initramfs-tools/hooks/plymouth, replace the line
```
echo 'root:x:0:0:root:/root:/bin/bash' >${DESTDIR}/etc/passwd
```with
```
echo 'root:x:0:0:root:/root:/bin/sh' >${DESTDIR}/etc/passwd
```3) when booting via ssh use the ssh key and when you are in the prompt enter:
```
echo -n "Passphrase" > /lib/cryptsetup/passfifo
``` where Passphrase is the one which decrypts the LVM (keep quotes "" around passphrase).

4) Finally, run the command:
```
unlock
```This will trigger the decryption process. Wait 10-15 seconds and boot as usual.

Dunno if it is the optimal security stuff but it works :)

BR

---

### Post by alyandon on 2011-07-20
Glad to know that helped someone.  I'll give that script a try when I get the chance!

---

### Post by boba23 on 2012-02-29
Hey folks,

I just got back to my remote unlock setup, which I didn't use for months, since it was broken as discussed here.
Is there going to be an official fix anytime soon? Or will those workarounds mentioned here .. which don't work for me btw, be the only way to "fix" this?
I guess I will be trying debian testing then, and see if this works out of the box ....

boba

---

