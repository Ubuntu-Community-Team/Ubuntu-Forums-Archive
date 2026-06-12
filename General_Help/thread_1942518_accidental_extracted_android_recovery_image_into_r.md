---
title: "accidental extracted android recovery image into root"
date: 2012-03-17
forum: General Help
---

### Post by kaefert66014235 on 2012-03-17
Hi there!

I have the following problem:
I used a perl-script downloaded from here:
[http://android-dls.com/wiki/index.php?title=HOWTO:_Unpack%2C_Edit%2C_and_Re-Pack_Boot_Images](http://android-dls.com/wiki/index.php?title=HOWTO:_Unpack%2C_Edit%2C_and_Re-Pack_Boot_Images)

that was ment to unpack a image of an android recovery into a subdirectory of the current directory that it created beforehand. but this script sadly missed the parameter "--no-absolute-filenames" for the cpio command (line 57)

Lazy and stupid as I am, I didn't read what the problem was when executing it, maybe I was tired also, I just thought heck maybe it need root permissions... and that way I overwrote A LOT of files from the /sbin directory.

```

[
[[
adbd
ash
awk
basename
bbconfig
bunzip2
busybox
bzcat
bzip2
cal
cat
catv
charge
chgrp
chmod
choice_fn
chown
chroot
cksum
clear
cmp
cp
cpio
cut
date
dc
dd
depmod
detect_key
devmem
df
diff
dirname
dmesg
dos2unix
du
dump_image
e2fsck
echo
edify
egrep
env
erase_image
expr
false
fdisk
fgrep
find
fix_permissions
flash_image
fold
free
freeramdisk
fuser
getopt
grep
gunzip
gzip
head
hexdump
hw_diag_app
id
insmod
install
kill
killall
killall5
killrecovery.sh
length
less
list.txt
ln
losetup
ls
lsmod
lspci
lsusb
lzop
lzopcat
md5sum
mkdir
mke2fs
mkfifo
mkfs.ext2
mknod
mkswap
mktemp
mkyaffs2image
modprobe
more
mount
mountpoint
mv
nandroid
nandroid-md5.sh
nice
nohup
od
offmode_charging
parted
patch
pgrep
pidof
pkill
port-bridge
power_test
printenv
printf
ps
pwd
rdev
readlink
realpath
reboot
recovery
renice
reset
rm
rmdir
rmmod
rmt_oeminfo
rmt_storage
run-parts
sdparted
sed
seq
setsid
sh
sha1sum
sha256sum
sha512sum
sleep
sort
split
stat
strings
stty
swapoff
swapon
sync
sysctl
tac
tail
tar
tee
test
time
top
touch
tr
true
tty
tune2fs
ueventd
umount
uname
uniq
unix2dos
unlzop
unyaffs
unzip
uptime
usleep
uudecode
uuencode
volume
watch
wc
which
whoami
xargs
yes
zcat

```

I removed them again to at least be able to run sudo chmod and stuff like that again, which at least worked.

But I have two really annoying issues now:

1.) I can't unlock the screensaver the normal way (it says wrong password) - I have to use the "switch user" and enter my password on the loginpage.

2.) I cannot run ifconfig -->
```

kaefert@blechmobil ~ $ ifconfig
Die Anwendung »ifconfig« ist momentan nicht installiert.  Sie können sie durch folgende Eingabe installieren:
sudo apt-get install net-tools
kaefert@blechmobil ~ $ sudo apt-get install net-tools
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Statusinformationen werden eingelesen... Fertig
net-tools ist schon die neueste Version.
0 aktualisiert, 0 neu installiert, 0 zu entfernen und 1 nicht aktualisiert.
kaefert@blechmobil ~ $ 

```

Is there some solution to this other than formatting and reinstall ubuntu from scratch? Thanks for any help in advance

I also tried to remove and install package net-tools, but that also didn't help anything

---

