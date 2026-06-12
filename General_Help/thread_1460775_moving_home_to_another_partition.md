---
title: "moving /home to another partition"
date: 2010-04-23
forum: General Help
---

### Post by ognyang on 2010-04-23
Hi guys.
I know there is a lot of tutorials about this but I`m kind a new in Ubuntu and Linux.
I know that it is good to set different partition for /home..
But when I installed my ubuntu 9.10 I made 4 partitions
swap
/boot
/ - 40GB
/usr - 200GB
I thought it was the /usr directory which has to be placed on another partition. :(
Now can you tell me how to fix this ****.
I want to move my /home and delete /usr.
But I don`t want to make a clean install because I already made some settings, updates, installed a virtual machine on my virtualbox and configured it. So.. just want to delete the /usr part and move the /home part on the new partition (/usr)

Please help!

Regards,
Ognyan Guglev

---

### Post by oldfred on 2010-04-23
Welcome to the forums.

I do not know for sure. I did move /boot from root to another partition and edited fstab and it worked. I assume you may be able to do the same.

I would make sure I backed up everything. My main concern would be maintaining permissions and ownership (root) as if any get reset it may be impossible to reset. I would do this in small steps to test. Perhaps first copy everything (as sudo) to /usr and backup fstab and change it to remove the mounting of the separate partition. If that works and I would use system for several days to make sure then you can change the old /usr partition.

read up on cp -a command , -a should preserve file attributes and recursively copy.
man cp

---

### Post by amoun on 2010-05-30
Hi Ognyan

The process is the same for /home as it is for /usr. I have just done both.

When you say delete /usr, do you mean remove it from a separate partition/drive. I'm still on 8.04 and originally all was on one drive 

1. copy the contents from the /usr partition to the /usr directory in the root filesystem

2. Check /etc/fstab to see if you have a line something like

```
# /dev/sdb6
UUID=4e0d74d0-1292-414a-96f8-c509955f055a /usr            ext2    relatime        0       2

```

I imagine you have one mounting your 200G partition as /usr
Disable it by prefixing with a hash

If you want your home to be on the partition - copy the contents of the /home folder to the 200G and then edit the line you commented out to say /home instead of /usr and then uncomment it.

You should now rename or (move) /home to /home-old for safety.

so copy from the source is for example from /home
$sudo cp -ax * /home-old

You must now make a new /home that links to the partition, so

$sudo mkdir /home

Here's the detail of what I did to move /usr for example

The following was carried out to move /usr directory from the 4GB sda on eeePC 900, to allow for more space. sdb was partitioned in 4 x 4Gb. One already used for /home

 > 1. Create new usr space (directory, or partition) or select alterantive drive: Name it usr-new(not critical)
 2. Mount 'new space'
 
 3. Copy contents of /usr to selection in 3 as follows:
    $cd /home
    $sudo cp -ax * /mnt/newhome 

 4. Right click and get UUID from Properties/Volume to use in step 5.
 5. Create new line in /etc/fstab to automount at start up: Place line after sda
	  Example: 
			# /dev/sdb6
			UUID=4e0d74d0-1292-414a-96f8-c509955f055a /usr            ext2    relatime        0       2
			
 6. Unmount result of 3

 7. In terminal login as sudo -i (As I just logined in as a normal user, sudo wouldn't work after moving /usr as sudo script is in usr. Luckily I logged in as root with: /usr-old/bin/sudo -i)
 
 8. mkdir /usr/a-usr *****(This is just to see if the change works. For if it does, when you go to the /usr directory on restart you won't see this directory as the /usr directory was copied before this was added. However you should then find it in /usr-old
 
 9. mv /usr /usr-old *****(Break path to usr contents by renaming)

10. mkdir /usr *****(create new empty /usr directory as mounting point for usr-new)

11. mount /dev/sdb6 /usr ****(link usr-new to default path of usr)

12. Everything should be fine now. Reboot. If it doesn't work, login as admin by holding down esc (hardy) and booting to recovery. Then [mv /usr-old /usr] to restore.
13. When you are sure all is OK /usr-old can be deleted, freeing up space on the 'boot' partition.

keep us in touch with how you get on

Amoun

---

