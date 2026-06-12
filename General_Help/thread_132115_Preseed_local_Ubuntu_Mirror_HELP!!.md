---
title: "Preseed local Ubuntu Mirror HELP?!?!"
date: 2006-02-17
forum: General Help
---

### Post by ximok on 2006-02-17
I have a network of about 650 machines that will be using Ubuntu.  I have set up a local mirror of archive.ubuntu.com so I don't have to worry about 650 machines eating my bandwidth when they go to update.

My problem is this:  I can't seem to get the preseed on the network install to setup Universe, non-free, backports, and Security to point to the local server instead of archive.ubuntu.com.  BIG Problem.  The preseed works fine for the initial install, what am I doing wrong!

On my web server (192.168.1.10) I have these two directories:
/csdubuntu <- mirror of install cd
/archive <- mirror of archive.ubuntu.com (contains EVERYTHING - 110 GIgs or so)

after install I can manually edit the sources.list to point to the webserver and everything works just fine and dandy.  


So, looking at the lines
```

# You can choose to install non-free (= restricted) and universe software,
# or to install software from the backports repository.
base-config apt-setup/non-free         boolean true
base-config apt-setup/universe         boolean true
base-config apt-setup/backports        boolean true

# Do enable security updates.
base-config  apt-setup/security-updates boolean true

```

I thought it would use the server I specified for main.  HELP?

Here is my preseed file.
```

#### Modifying syslinux.cfg.

# Copy oem-config along with the desktop.
##d-i	archive-copier/desktop-task	string ubuntu-standard|ubuntu-desktop|oem-config
d-i	archive-copier/desktop-task	string ubuntu-standard|ubuntu-desktop


# Edit the syslinux.cfg (or similar) file, and add parameters to the end
# of the append line(s) for the kernel.
#
# You'll at least want to add a parameter telling the installer where to
# get its preseed file from.
# If you're installing from USB media, use this, and put the preseed file
# in the toplevel directory of the USB stick.
#   preseed/file=/hd-media/preseed
# If you're netbooting, use this instead:
#   preseed/url=http://host/path/to/preseed
# If you're remastering a CD, you could use this:
#   preseed/file=/cdrom/preseed
# Be sure to copy this file to the location you specify.
# 
# While you're at it, you may want to throw a debconf/priority=critical in
# there, to avoid most questions even if the preseeding below misses some.
# And you might set the timeout to 1 in syslinux.cfg to avoid needing to hit
# enter to boot the installer.
#
# Language, country, and keyboard selection cannot be preseeded from a file,
# because the questions are asked before the preseed file can be loaded.
# Instead, to avoid these questions, pass some more parameters to the kernel:
#
#    debian-installer/locale=en_US
#    kbd-chooser/method=us
#
# If you need to pick a particular interface when netbooting before reading
# a preseed URL, pass a parameter like this as well:
#
#    netcfg/choose_interface=eth1
#
# Note that the kernel accepts a maximum of 8 command line options and
# 8 environment options (including any options added by default for the
# installer). If these numbers are exceeded, 2.4 kernels will drop any
# excess options and 2.6 kernels will panic. With kernel 2.6.9 or newer,
# you can use 32 command line options and 32 environment options.
# Some of the default options, like 'vga=normal' and 'devfs=mount' may be
# safely removed for most installations, which may allow you to add more
# options for preseeding.

#### Shell commands.

# d-i preseeding is inherently not secure. Nothing in the installer checks
# for attempts at buffer overflows or other exploits of the values of a
# preseed file like this one. Only use preseed files from trusted
# locations! To drive that home, and because it's generally useful, here's
# a way to run any shell command you'd like inside the installer,
# automatically.

# This first command is run as early as possible, just after
# preseeding is read.
#d-i preseed/early_command              string wget http://url/to/my.udeb -O /tmp/my.udeb; udpkg -i /tmp/my.udeb

# This command is run just before the install finishes, but when there is
# still a usable /target directory.
#d-i preseed/late_command               string for deb in /hd-media/*.deb; do cp $deb /target/tmp; chroot /target dpkg -i /tmp/$(basename $deb); done

# This command is run just as base-config is starting up.
#base-config base-config/early_command  string echo hi mom

# This command is run after base-config is done, just before the login:
# prompt. This is a good way to install a set of packages you want, or to
# tweak the configuration of the system.
#base-config base-config/late_command   string apt-get install zsh; chsh -s /bin/zsh

#### Network configuration.

# Of course, this won't work if you're loading your preseed file from the
# network! But it's great if you're booting from CD or USB stick. You can
# also pass network config parameters in on the kernel params if you are
# loading preseed files from the network.

# netcfg will choose an interface that has link if possible. This makes it
# skip displaying a list if there is more than one interface.
##d-i  netcfg/choose_interface            select auto

# To pick a particular interface instead:
#d-i netcfg/choose_interface            select eth1

# If you prefer to configure the network manually, here's how:
#d-i netcfg/disable_dhcp                boolean true
#d-i netcfg/get_nameservers             string 192.168.1.1
#d-i netcfg/get_ipaddress               string 192.168.1.42
#d-i netcfg/get_netmask                 string 255.255.255.0
#d-i netcfg/get_gateway                 string 192.168.1.1
#d-i netcfg/confirm_static              boolean true

# Note that any hostname and domain names assigned from dhcp take
# precedence over values set here. However, setting the values still
# prevents the questions from being shown even if values come from dhcp.
##d-i  netcfg/get_hostname                string unassigned-hostname
##d-i  netcfg/get_domain                  string unassigned-domain

# Disable that annoying WEP key dialog.
##d-i  netcfg/wireless_wep                string
# The wacky dhcp hostname that some ISPs use as a password of sorts.
#d-i netcfg/dhcp_hostname               string radish

#### Mirror settings.

##d-i  mirror/country                     string enter information manually
##d-i  mirror/http/hostname               string archive.ubuntu.com
##d-i  mirror/http/directory              string /ubuntu
## Uncomment once archive server finishes downloading
##d-i  mirror/suite                       string &releasename;
##d-i  mirror/http/proxy                  string 

d-i mirror/country	string enter information manually
d-i mirror/http/hostname	string 192.168.1.10
d-i mirror/http/directory	string /csdubuntu
d-i mirror/suite 	string breezy
d-i mirror/http/proxy	string

### Partitioning.

# If the system has free space you can choose to only partition that space.
#d-i partman-auto/init_automatically_partition select Use the largest continuous free space

# Alternatively, you can specify a disk to partition. The device name can
# be given in either devfs or traditional non-devfs format.
# For example, to use the first disk devfs knows of:
##d-i  partman-auto/disk                  string /dev/discs/disc0/disc

# You can choose from any of the predefined partitioning recipes:
##d-i  partman-auto/choose_recipe         select All files in one partition (recommended for new users)
#d-i partman-auto/choose_recipe         select Desktop machine
#d-i partman-auto/choose_recipe         select Multi-user workstation

# Or provide a recipe of your own...
# The recipe format is documented in the file devel/partman-auto-recipe.txt.
# If you have a way to get a recipe file into the d-i environment, you can
# just point at it.
#d-i partman-auto/expert_recipe_file    string /hd-media/recipe

# If not, you can put an entire recipe in one line. This example creates
# a small /boot partition, suitable swap, and uses the rest of the space
# for the root partition:
d-i partman-auto/expert_recipe         string boot-root :: 20 50 100 ext3 $primary{ } $bootable{ } method{ format } format{ } use_filesystem{ } filesystem{ ext3 } mountpoint{ /boot } . 500 10000 1000000000 reiserfs method{ format } format{ } use_filesystem{ } filesystem{ reiserfs } mountpoint{ / } . 64 512 300% linux-swap method{ swap } format{ } . 
# For reference, here is that same recipe in a more readable form:
#    boot-root ::
#       40 50 100 ext3
#          $primary{ } $bootable{ }
#          method{ format } format{ }
#          use_filesystem{ } filesystem{ ext3 }
#          mountpoint{ /boot }
#       .
#       500 10000 1000000000 ext3
#          method{ format } format{ }
#          use_filesystem{ } filesystem{ ext3 }
#          mountpoint{ / }
#       .
#       64 512 300% linux-swap
#          method{ swap } format{ }
#       .

# This makes partman automatically partition without confirmation.
d-i partman/confirm_write_new_label     boolean true
d-i partman/choose_partition            select Finish partitioning and write changes to disk
d-i partman/confirm                     boolean true

#### Boot loader installation.

# Grub is the default boot loader (for x86). If you want lilo installed
# instead, uncomment this:
#d-i grub-installer/skip                boolean true

# This is fairly safe to set, it makes grub install automatically to the MBR
# if no other operating system is detected on the machine.
##d-i  grub-installer/only_debian         boolean true

# This one makes grub-installer install to the MBR if if finds some other OS
# too, which is less safe as it might not be able to boot that other OS.
##d-i  grub-installer/with_other_os       boolean true

# Alternatively, if you want to install to a location other than the mbr,
# uncomment and edit these lines:
#d-i grub-installer/bootdev             string (hd0,0)
#d-i grub-installer/only_debian         boolean false
#d-i grub-installer/with_other_os       boolean false

##### Finishing up the first stage install.

# Avoid that last message about the install being complete.
d-i  prebaseconfig/reboot_in_progress   note 


##### Preseeding base-config.

# Avoid the introductory message.
base-config  base-config/intro          note

# Avoid the final message.
base-config  base-config/login          note

# If you installed a display manager, but don't want to start it immediately
# after base-config finishes.
#base-config base-config/start-display-manager        boolean false

###### Time zone setup.

# Controls whether or not the hardware clock is set to GMT.
base-config  tzconfig/gmt                             boolean false
#base-config  tzconfig/pacific                             boolean true

# If you told the installer that you're in the United States, then you
# can set the time zone using this variable.
# (Choices are: Eastern, Central, Mountain, Pacific, Alaska, Hawaii,
# Aleutian, Arizona East-Indiana, Indiana-Starke, Michigan, Samoa, other)

base-config  tzconfig/choose_country_zone/US          select Pacific

# If you told it you're in Canada.
# (Choices are: Newfoundland, Atlantic, Eastern, Central,
# East-Saskatchewan, Saskatchewan, Mountain, Pacific, Yukon, other)
##base-config  tzconfig/choose_country_zone/CA          select Eastern
# If you told it you're in Brazil. (Choices are: East, West, Acre,
# DeNoronha, other)
##base-config  tzconfig/choose_country_zone/BR          select East
# Many countries have only one time zone. If you told the installer you're
# in one of those countries, you can choose its standard time zone via this
# question.
##base-config  tzconfig/choose_country_zone_single      boolean true
# This question is asked as a fallback for countries other than those
# listed above, which have more than one time zone. You can preseed one of
# the time zones, or "other".
#base-config tzconfig/choose_country_zone_multiple    select 

###### Account setup.
#### Stolen from oem.seed
# Create a special user with a preconfigured uid.
#passwd	passwd/user-fullname	string OEM Configuration (temporary user)
#passwd	passwd/username	string oem
#passwd	passwd/user-uid	string 29999


# To preseed the root password, you have to put it in the clear in this
# file. That is not a very good idea, use caution!
#passwd passwd/root-password            password r00tme
#passwd passwd/root-password-again      password r00tme

# If you want to skip creation of a normal user account.
passwd passwd/make-user                boolean true

# Alternatively, you can preseed the user's name and login.
#passwd passwd/user-fullname            string local administrator

#passwd passwd/username                 string administrator

# And their password, but use caution!
#passwd passwd/user-password            password insecure
#passwd passwd/user-password-again      password insecure

###### Apt setup.

# This question controls what source the second stage installation uses
# for packages. Choices are cdrom, http, ftp, filesystem, edit sources list
# by hand


# If you choose ftp or http, you'll be asked for a country and a mirror.

### Uncomment after the apt-mirror finishes
base-config  apt-setup/uri_type         select http
base-config  apt-setup/country          select enter information manually
base-config  apt-setup/hostname         string 192.168.1.10
base-config  apt-setup/directory        string /archive

##base-config  apt-setup/uri_type         select http
##base-config  apt-setup/country          select enter information manually
##base-config  apt-setup/hostname         string archive.ubuntu.com
##base-config  apt-setup/directory        string /ubuntu


# Stop after choosing one mirror.

base-config  apt-setup/another          boolean false

# You can choose to install non-free (= restricted) and universe software,
# or to install software from the backports repository.
base-config apt-setup/non-free         boolean true
base-config apt-setup/universe         boolean true
base-config apt-setup/backports        boolean true

# Do enable security updates.
base-config  apt-setup/security-updates boolean true

###### Package selection.

# You can choose to install any set of packages that are available using
# aptitude patterns (see the aptitude documentation). The default is:

# Install oem-config along with the desktop.
#base-config  base-config/package-selection	string ~tubuntu-standard|~tubuntu-desktop|oem-config
base-config  base-config/package-selection	string ~tubuntu-standard|~tubuntu-desktop

#base-config  base-config/package-selection      string ~tubuntu-standard|~tubuntu-desktop

# ... but you could choose something different, such as:
#base-config base-config/package-selection      string ~tubuntu-standard|openssh-server

# You can also choose to set this to the empty string, and force the
# installation of a set of packages in some other way.

###### X Configuration.

# Preseeding Ubuntu's X config is possible, but you probably need to know
# some details about the video hardware of the machine, since Ubuntu's X
# configurator does not do fully automatic configuration of everything.

# X can detect the right driver for some cards, but if you're preseeding,
# you override whatever it chooses. Still, vesa will work most places.
#xserver-xorg    xserver-xorg/config/device/driver    select vesa

# A caveat with mouse autodetection is that if it fails, X will retry it
# over and over. So if it's preseeded to be done, there is a possibility of
# an infinite loop if the mouse is not autodetected.
#xserver-xorg    xserver-xorg/autodetect_mouse        boolean true

# Monitor autodetection is recommended.
##xserver-xorg    xserver-xorg/autodetect_monitor       boolean true
# Uncomment if you have a LCD display.
#xserver-xorg    xserver-xorg/config/monitor/lcd      boolean true
# X has three configuration paths for the monitor. Here's how to preseed
# the "medium" path, which is always available. The "simple" path may not
# be available, and the "advanced" path asks too many questions.

##xserver-xorg     xserver-xorg/config/monitor/selection-method select medium

#xserver-xorg	xserver-xorg/config/display/default_depth	select 16
#xserver-xorg     xserver-xorg/config/monitor/mode-list select 1024x768 @ 75 Hz


###### Everything else.

# Depending on what software you choose to install, or if things go wrong
# during the installation process, it's possible that other questions may
# be asked. You can preseed those too, of course. To get a list of every
# possible question that could be asked during an install, do an
# installation, and then run these commands:
#   debconf-get-selections --installer > file
#   debconf-get-selections >> file

# If you like, you can include other preseed files into this one.
# Any settings in those files will override pre-existing settings from this
# file. More that one file can be listed, separated by spaces; all will be
# loaded. The included files can have preseed/include directives of their
# own as well. Note that if the filenames are relative, they are taken from
# the same directory as the preseed file that includes them.
#d-i preseed/include                    string x.cfg

# More flexibly, this runs a shell command and if it outputs the names of
# preseed files, includes those files. For example, to switch configs based
# on a particular usb storage device (in this case, a built-in card reader):
#d-i preseed/include_command            string if $(grep -q "GUID: 0aec3050aec305000001a003" /proc/scsi/usb-storage-*/*); then echo kraken.cfg; else echo otherusb.cfg; fi

### Stolen from oem.seed




```

---

### Post by ximok on 2006-02-18
Really, all I need the preseed file to do is make it to where all the repositories in apt.sources go to the server mentioned above.  Any thoughts on how to do this?

---

### Post by grahamw on 2006-11-10
I'm looking for a solution to this problem as well.

I did find the following located [here]("http://d-i.alioth.debian.org/manual/en.i386/install.en.txt")

> B.4.7. Apt setup

Setup of the /etc/apt/sources.list and basic configuration options is fully
automated based on your installation method and answers to earlier questions.
You can optionally add other (local) repositories.

# You can choose to install non-free and contrib software.
#d-i apt-setup/non-free boolean true
#d-i apt-setup/contrib boolean true
# Uncomment this to avoid adding security sources, or
# add a hostname to use a different server than security.debian.org.
#d-i apt-setup/security_host string

# Additional repositories, local[0-9] available
#d-i apt-setup/local0/repository string \
#       deb [http://local.server/debian](http://local.server/debian) stable main
#d-i apt-setup/local0/comment string local server
# Enable deb-src lines
#d-i apt-setup/local0/source boolean true
# URL to the public key of the local repository
#d-i apt-setup/local0/key string [http://local.server/key](http://local.server/key)

I have no idea whether this will work as it's from the Sarge's current development manual.  I'll post my success or failure, once I've had a chance to give it a try.

---

### Post by Paul Weaver on 2008-03-20
Just as a little update for those of us who googled their way here

I set up a very simple preseed setup for a PXE boot, the machine is hidden behind an external web proxy, and is unroutable to the net.

My pxe config file (32 bit) contains
LABEL test-710
        kernel ubuntu-installer/i386-710/linux
        append base-installer/kernel/linux/extra-packages-2.6= tasks=standard pk
gsel/language-pack-patterns= pkgsel/install-language-support=false locale=en_GB 
console-setup/ask_detect=false console-setup/layoutcode=gb preseed/url=http://10
.129.134.101/dhcp/test.cfg initrd=ubuntu-installer/i386-710/initrd.gz  --

And test.cfg is:
d-i netcfg/get_domain string mydomain.mycorp.co.uk

d-i time/zone string Europe/London
d-i clock-setup/utc boolean true

**d-i mirror/country string enter information manually**
[B]d-i mirror/http/hostname string 10.129.139.43:3142
d-i mirror/http/directory string /gb.archive.ubuntu.com/ubuntu[/B]
d-i mirror/suite string feisty
d-i mirror/http/proxy string
**d-i apt-setup/security_host string 10.129.139.43:3142/security.ubuntu.com**
d-i apt-setup/local0/repository string deb [http://mydebserver01.mydomain.mycorp/debs](http://mydebserver01.mydomain.mycorp/debs) ./
d-i apt-setup/local0/comment string My Repository
#d-i debian-installer/allow_unauthenticated string true
#d-i apt-setup/local0/key string [http://must/figure/it/out](http://must/figure/it/out)

d-i apt-setup/restricted boolean true
d-i apt-setup/universe boolean true
d-i apt-setup/multiverse boolean true

d-i passwd/root-login boolean false
d-i passwd/user-fullname string My User Name
d-i passwd/username string myusername
d-i passwd/user-password-crypted password (output of echo "mypass"|mkpasswd -s -H MD5)

d-i pkgsel/include string openssh-server build-essential


This works, note that I used debian-installer/allow_unauthenticated as I haven't figured out gpg signing my own repository, commented here in case anyone copies/pastes.

---

### Post by PmDematagoda on 2008-03-20
This thread is really old and there is no point in reviving it in order to convey your guide since the topic defeats your purpose. Therefore I advise you to put up your guide in a new thread of your own.

This thread is closed.

---

