---
title: "Remastering Ubuntu Install CD with default Bengali language"
date: 2006-06-25
forum: General Help
---

### Post by suzan229 on 2006-06-25
Hi all,
I'm trying to remastering Ubuntu Dapper with default Bengali language.

I already remastered Ubuntu with only en_US, bn_BD & bn_IN languages and with some multimedia Packages (Restricted Format). But en_US is the default language there. I used "d-i debconf/language	string	bn_BD" in preseed file . But that time I can see no font, as Bengali is not working on text mode. So can anyone tell me way of make default bn_BD(Bengali, My mother tongue) language in my remastered Ubuntu.

Best regards,
Suzan
[https://launchpad.net/people/suzan](https://launchpad.net/people/suzan)

I'm adding my preseed file here. 

####

# Choose your location:
d-i	countrychooser/country-name	select	Bangladesh

# Internal use
d-i	debian-installer/country	string	BD

# Choices: IN, BD, other
d-i	countrychooser/shortlist-bn	select	BD

### Network configuration
# netcfg will choose an interface that has link if possible. This makes it
# skip displaying a list if there is more than one interface.
d-i netcfg/choose_interface select auto

# Any hostname and domain names assigned from dhcp take precedence over
# values set here. However, setting the values still prevents the questions
# from being shown, even if values come from dhcp.
d-i netcfg/get_hostname string ankur
d-i netcfg/get_domain string ankur

# Disable that annoying WEP key dialog.
d-i netcfg/wireless_wep string

### Clock and time zone setup
# Controls whether or not the hardware clock is set to UTC.
#d-i clock-setup/utc boolean false

# You may set this to any valid setting for $TZ; see the contents of
# /usr/share/zoneinfo/ for valid values.
d-i time/zone string Asia/Dhaka

### Apt setup
# You can choose to install restricted and universe software, or to install
# software from the backports repository.
d-i apt-setup/universe boolean true
d-i apt-setup/multiverse boolean true


# Alternatively, create a normal user account.
d-i passwd/user-fullname string Ubuntu User
d-i passwd/username string ubuntu
# Normal user's password, either in clear text
d-i passwd/user-password password ubuntu
d-i passwd/user-password-again password ubuntu


### Package selection
# The default is:
d-i pkgsel/install-pattern string ~t^ubuntu-standard$|~t^ubuntu-desktop$

#Supported locale
d-i localechooser/supported-locales multiselect bn_BD, bn_IN

# Patterns for language packs to install
d-i	pkgsel/language-pack-patterns	string	language-pack-gnome-$LL

#Bengali Default
d-i debian-installer/locale select bn_BD
#d-i debian-installer/language	string	bn_BD
d-i languagechooser/language-name  select  Bengali


# This is fairly safe to set, it makes grub install automatically to the MBR
# if no other operating system is detected on the machine.
d-i grub-installer/only_debian boolean true

# This one makes grub-installer install to the MBR if if finds some other OS
# too, which is less safe as it might not be able to boot that other OS.
d-i grub-installer/with_other_os boolean true

### Finishing up the first stage install
# Avoid that last message about the install being complete.
d-i prebaseconfig/reboot_in_progress note

# Avoid the introductory message.
base-config  base-config/intro          note

# Avoid the final message.
base-config  base-config/login          note

#Time Zone
# Controls whether or not the hardware clock is set to GMT.
#base-config	tzconfig/gmt		boolean true

### Clock and time zone setup
# Controls whether or not the hardware clock is set to UTC.
d-i clock-setup/utc boolean false


# Monitor autodetection is recommended.
xserver-xorg xserver-xorg/autodetect_monitor boolean true
# Uncomment if you have an LCD display.
#xserver-xorg xserver-xorg/config/monitor/lcd boolean true
# X has three configuration paths for the monitor. Here's how to preseed
# the "medium" path, which is always available. The "simple" path may not
# be available, and the "advanced" path asks too many questions.
xserver-xorg xserver-xorg/config/monitor/selection-method select medium
xserver-xorg xserver-xorg/config/monitor/mode-list select 1024x768 @ 60 Hz


#d-i debconf/language	string	bn_BD

# Eject CD-ROM when finished?
d-i	cdrom-detect/eject	boolean	true


####

---

