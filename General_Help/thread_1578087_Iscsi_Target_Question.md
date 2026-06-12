---
title: "Iscsi Target Question"
date: 2010-09-19
forum: General Help
---

### Post by donthem on 2010-09-19
Hello,

Im creating an iscsi share and I would like to share the entire disk.  

Most sites recommend this 

Target iqn.2001-04.com.example:storage.lun1
        IncomingUser someuser secret
        OutgoingUser
        Lun 0 Path=/dev/sda1,Type=fileio
        Alias LUN1
        #MaxConnections  6

but is there a way to specify the UUID since /dev/sda1 can change frequently 

Thanks

:guitar:

---

### Post by cenwesi on 2010-09-24
You might want to look up udev that should fix this problem for you.

---

### Post by annoyingrob on 2010-10-15
You can point the path to /dev/disk/by-uuid/xxxxxxxxxxxxxx to mount to the UUID

---

### Post by TheR on 2010-12-08
This is how I did it:

1. Create file /etc/udev/rules.d/60-persistent-iscsi.rules

ENV{DEVTYPE}=="disk", ENV{ID_PATH}=="", DEVPATH!="*/virtual/*", IMPORT{program}="path_id %p"
ENV{DEVTYPE}=="disk", ENV{ID_PATH}=="?*", PROGRAM="/usr/local/bin/persistent_iscsi.rb $env{ID_PATH}", SYMLINK+="%c"


2. Create file /etc/iscsi/persistent.names.conf 

iqn.2010-01.com.my:disk.sas1;10;iscsi/testdisk
iqn.2010-01.com.my:disk.sas1;11;iscsi/windc1_c
iqn.2010-01.com.my:disk.sas1;12;iscsi/windc1_d
iqn.2010-01.com.my:disk.sas1;13;iscsi/ub1004_template


3. Create /usr/local/bin/persistent_iscsi.rb
[RUBY]
#!/usr/bin/ruby
# parameter : ip-192.168.2.199:3260-iscsi-iqn.2010-01.com.my:disk.sas1-lun-10
device = nil
# parse parm on - sign
a = ARGV.first.split('-')
# third element should be iscsi
exit 1 unless a[2] == 'iscsi'
# set iqn and lun
id_iqn = a[3] + '-' + a[4]
id_lun = a[6]
# read my configuration file /etc/iscsi/persistent.names.conf
File.new('/etc/iscsi/persistent.names.conf').readlines.each do |line|
# config line looks like this: iqn.2100-05.si.ozs:diski.sas;2;iscsi/dns1
  iqn, lun, dev = line.chomp.split(';')
  if iqn == id_iqn and lun == id_lun
    device = dev
    break
  end
end
# Error if not found
exit 1 if device.nil?
# out device name on stdout
puts device
[/RUBY]

----------------------------------------------------------------
1. Study about /etc/udev/rules.d. Basically it is a set of rules which may run a program whenever new system event is triggered. In my case when new device is determined by system. Be it at startup or with "iscsiadm -m session -R" command.

2. This file is pure my idea. Each line has 3 informations delimited with semicolon.

iqn.2010-01.com.my:disk.sas1;10;iscsi/testdisk
SAN identifier ; LUN number ; device to map

3. I do all my scripting in Ruby, but it shouldn't be problem translate this to shell script. Program is triggered by udev rule with specified parameter. It returns device name to be used on stdout.

Result:
ls /dev/iscsi
ub1004_template    testdisk    windc1_c     windc1_d     


Works like a charm.

by
TheR

---

