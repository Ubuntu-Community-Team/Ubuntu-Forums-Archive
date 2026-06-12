---
title: "Setting up a Backup System Over SSH"
date: 2010-07-15
forum: General Help
---

### Post by Penguin Guy on 2010-07-15
I have an external hard drive and have been using it to backup my multiple computers for a while now, but because it needs to be plugged into the mains, it is a pain to move it from one computer to the next. So I've decided to try to set up a SSH backup system that will allow me to backup without having to move the drive.

I made this thread to get help on any hurdles I encounter during the process - thanks for your time :)


Host udev script:
```

ENV{ID_FS_UUID}!="37E5-0513", GOTO="fat32_end"
	IMPORT{program}="/sbin/blkid -o udev -p %N"
	ENV{dir_name}="/mnt/backup/fat32"
	ACTION=="add", RUN+="/bin/mkdir -pm 777 %E{dir_name}", RUN+="/bin/mount -o noauto,noexec,umask=0000 /dev/%k %E{dir_name}"
	ACTION=="remove", RUN+="/bin/umount -l %E{dir_name}", RUN+="/bin/rmdir %E{dir_name}"
LABEL="fat32_end"

ENV{ID_FS_UUID}!="26126d23-2593-43d0-b221-19cb6d44a3fc", GOTO="ext3_end"
	IMPORT{program}="/sbin/blkid -o udev -p %N"
	ENV{dir_name}="/mnt/backup/ext3"
	ACTION=="add", RUN+="/bin/mkdir -pm 777 %E{dir_name}", RUN+="/bin/mount -o noauto,noexec /dev/%k %E{dir_name}"
	ACTION=="remove", RUN+="/bin/umount -l %E{dir_name}", RUN+="/bin/rmdir %E{dir_name}"
LABEL="ext3_end"

```

Host sshd_config:
```

PermitEmptyPasswords yes
PasswordAuthentication yes
AllowUsers backup@192.168.*.* backup@localhost

```

Client backup script:
```

#!/bin/sh -e
if [ -n "$1" ] ; then from="$1" ; else from="$HOME" ; fi
ssh_from="backup@localhost:ext3"
ssh_to="${HOME}/backup-ext3"
backup_dir="$ssh_to/$(hostname)${from}"
backup_file="${backup_dir}/$(date --rfc-3339=date).tar.gz"
backup_started=0

quit()
{
    kill $spinner_proc >/dev/null 2>/dev/null  # FIXME
    fusermount -u "$ssh_to" >/dev/null 2>/dev/null
    rmdir "$ssh_to" >/dev/null 2>/dev/null
    exit $1
}

error()
{
    set +e
    [ -n "$1" ] && message="$1" || message='Unknown error.'
    echo "Error: $message" >&2
    [ $backup_started ] && mv "$backup_file" "$backup_file-incomplete" >/dev/null 2>/dev/null
    quit
}

trap error HUP INT TERM

spinner()
{
    char='|'
    while [ true ]; do
        case "$char" in
            '|') char='/' ;;
            '/') char='-' ;;
            '-') char='\' ;;
            '\') char='|' ;;
        esac
        echo -n "$char" ; sleep 0.1 ; echo -n "\b"
    done
}

mkdir -p "$ssh_to"
sshfs "$ssh_from" "$ssh_to" || { error 'Could not connect to backup drive.' ; } 

mkdir -p "$backup_dir"

if [ -f "$backup_file" ]; then
    echo 'Data has already been backed up today.' >&2
    quit 0
fi

backup() { tar -chaf "$backup_file" "$from" --exclude "$ssh_to"\
 --exclude ".Trash-*" --exclude "lost+found"\
 --exclude "${HOME}/.cache" --exclude "${HOME}/.thumbnails"\
 >/dev/null 2>/dev/null ; }

backup_started=1
backup & backup_proc=$!
spinner & spinner_proc=$!
wait $backup_proc
echo 'Backup complete.'
quit 0

```

---

### Post by Penguin Guy on 2010-07-15
I have two partitions on the backup drive, fat32 and ext3. How can I get the partitions to mount at [FONT="Courier New"]/mnt/backup/fat32[/FONT] and [FONT="Courier New"]/mnt/backup/ext3[/FONT] whenever the drive is attached?

So far I have this FSTab entry:
```

# Backup Drive:
UUID=37E5-0513 /mnt/backup/fat32 vfat   noauto,noexec,umask=0777 0 0
UUID=26126d23-2593-43d0-b221-19cb6d44a3fc /mnt/backup/ext3 ext3 noauto,noexec 0 0

```
But the drive will only mount when requested explicitly through the [FONT="Courier New"]mount[/FONT] command. Removing [FONT="Courier New"]noauto[/FONT] causes errors at boot time.

---

### Post by RiceMonster on 2010-07-15
To start, try using simple "defaults" for the mount options.


EDIT: Oh, if it's an external drive that you want to automically mount, you may want to look into autofs.

---

### Post by jpl888 on 2010-07-15
I have 2 external USB drives configured as a RAID mirror. I then use rsnapshot to automatically backup important machines using rsync and ssh.

You could always just use rsync and ssh on their own either.

---

### Post by Penguin Guy on 2010-07-15
> **RiceMonster said:**
> To start, try using simple "defaults" for the mount options.
The FSTab works fine, the problem is that with the [FONT="Courier New"]noauto[/FONT] option the drive isn't automatically mounted when plugged in, but without the [FONT="Courier New"]noauto[/FONT] option the drive causes an error on startup. I've found a solution using udev, but would have preferred something simpler.

```

IMPORT{program}="/sbin/blkid -o udev -p %N"

ENV{ID_FS_UUID}!="37E5-0513", GOTO="fat32_end"
	ENV{dir_name}="/mnt/backup/fat32"
	ACTION=="add", RUN+="/bin/mount -o noauto,noexec,umask=0000 /dev/%k %E{dir_name}"
	ACTION=="remove", RUN+="/bin/umount -l %E{dir_name}"
LABEL="fat32_end"

ENV{ID_FS_UUID}!="26126d23-2593-43d0-b221-19cb6d44a3fc", GOTO="ext3_end"
	ENV{dir_name}="/mnt/backup/ext3"
	ACTION=="add", RUN+="/bin/mount -o noauto,noexec /dev/%k %E{dir_name}"
	ACTION=="remove", RUN+="/bin/umount -l %E{dir_name}"
LABEL="ext3_end"

```

---

### Post by Penguin Guy on 2010-07-19
Seems like everything's going alright apart from the deletion of [FONT="Courier New"]/mnt/backup/ext3[/FONT] and [FONT="Courier New"]/mnt/backup/fat32[/FONT] on shutdown. Anyone got any suggestions?

> **RiceMonster said:**
> EDIT: Oh, if it's an external drive that you want to automically mount, you may want to look into autofs.
I tried using [FONT="Courier New"]/dev/disk/by-uuid[/FONT] with autofs, but didn't have any success.

---

