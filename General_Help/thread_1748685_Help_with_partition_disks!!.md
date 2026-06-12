---
title: "Help with partition disks!??!"
date: 2011-05-03
forum: General Help
---

### Post by mattintc10 on 2011-05-03
I am in the installation of it all and i came to the partition disk and i have no idea what i need to do and i have windows XP i need to keep on this laptop.

EDIT: nevermind i found something online that may be helpful

---

### Post by Hedgehog1 on 2011-05-03
In case the internet article doesn't get you were you need to be. here is my 'cheat sheet':

Using the LiveCD/LiveUSB, select 'TRY'...

In gparted, create 3 partitions:

1) ext4 '/'
2) Linux swap
3) ext4 '/home'

[IMG]http://img215.imageshack.us/img215/8985/01gparted.png[/IMG]
 
Once your three partitions are laid out, you will start the install and eventually get to this screen:

[IMG]http://img829.imageshack.us/img829/4196/02specifypartitons.png[/IMG]

Here is what the allocation screen looks like:

[IMG]http://img27.imageshack.us/img27/6770/03allocdrivespace1.png[/IMG]

First, make /dev/sda5 your '/' (root) partition:

[IMG]http://img31.imageshack.us/img31/7520/04allocdrivespace2.png[/IMG]

[IMG]http://img130.imageshack.us/img130/9673/05allocdrivespace3.png[/IMG]

Next, set up the swap partition.  This usually sets itself up just fine, but double check it.

[IMG]http://img263.imageshack.us/img263/7656/06allocdrivespace4.png[/IMG]

---

### Post by Hedgehog1 on 2011-05-03
The last partition to setup is the '/home' one:

**[SIZE="4"]IF YOU ARE DOING AN UPGRADE, DO NOT FORMAT THIS PARTITION![/SIZE]**

[IMG]http://img202.imageshack.us/img202/6828/07allocdrivespace5.png[/IMG]

This separates your documents and 'stuff' from the system files and 'stuff' in the '/' partition.

This brings you to here:

[IMG]http://img34.imageshack.us/img34/6017/08allocdrivespace6.png[/IMG]

[SIZE="4"]**Please install the Boot Loader on /dev/sda !**[/SIZE]

Press "Install Now" and you are on your way:

[IMG]http://img855.imageshack.us/img855/7153/09installbegin.png[/IMG]

Here is a view of the final layout of the partitions:

[IMG]http://img853.imageshack.us/img853/841/10diskutility2.png[/IMG]


***The Hedge***

:KS

---

### Post by xenophilius on 2011-05-03
Try to backup your important files as it's always risky (I have partitioned my windows/linux dual boots about 15 times with no problems and yet when I did it to my Dad's computer - crash!  Go figure).

If you follow the installation guide you'll have an option to install alongside windows.  If you like, use a parted magic CD to shrink the windows partition first in which case you can install in the free space.

Defragment your Windows drive first.

---

### Post by mattintc10 on 2011-05-03
> **Hedgehog1 said:**
> The last partition to setup is the '/home' one:

**[SIZE=4]IF YOU ARE DOING AN UPGRADE, DO NOT FORMAT THIS PARTITION![/SIZE]**

[IMG]http://img202.imageshack.us/img202/6828/07allocdrivespace5.png[/IMG]

This separates your documents and 'stuff' from the system files and 'stuff' in the '/' partition.

This brings you to here:

[IMG]http://img34.imageshack.us/img34/6017/08allocdrivespace6.png[/IMG]

[SIZE=4]**Please install the Boot Loader on /dev/sda !**[/SIZE]

Press "Install Now" and you are on your way:

[IMG]http://img855.imageshack.us/img855/7153/09installbegin.png[/IMG]

Here is a view of the final layout of the partitions:

[IMG]http://img853.imageshack.us/img853/841/10diskutility2.png[/IMG]


***The Hedge***

:KS

Thank you so much. I got permission just now that i can wipe out windows! so i am going that route.

---

