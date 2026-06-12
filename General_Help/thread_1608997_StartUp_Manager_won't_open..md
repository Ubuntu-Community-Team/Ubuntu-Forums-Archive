---
title: "StartUp Manager won't open."
date: 2010-10-29
forum: General Help
---

### Post by winchendonsprings on 2010-10-29
The problem is

I click StartUp-Manager from the System menu

password prompt

the "preforming pre-configuration tasks"  starts up

then... nothing. no startup manager window.

any ideas?

here is the terminal output

> 
ry@ry-desktop:~$ startupmanager
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.35-23-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Grub2 detected
Usplash not detected
Splashy not detected
Traceback (most recent call last):
  File "/usr/sbin/startupmanager", line 54, in <module>
    main()
  File "/usr/sbin/startupmanager", line 51, in main
    SumGui()
  File "/usr/share/startupmanager/gtk_frontend.py", line 193, in __init__
    self.setup_widgets()
  File "/usr/share/startupmanager/gtk_frontend.py", line 202, in setup_widgets
    self.set_shared_grub_widgets()
  File "/usr/share/startupmanager/gtk_frontend.py", line 223, in set_shared_grub_widgets
    self.timeout_spinner.set_value(self.grub.get_timeout())
  File "/usr/lib/pymodules/python2.6/bootconfig/grub.py", line 91, in get_timeout
    timeout = utils.extract_number(line)
  File "/usr/lib/pymodules/python2.6/bootconfig/utils.py", line 64, in extract_number
    match = number_filter.search(line)
TypeError: expected string or buffer
ry@ry-desktop:~$ 



---

### Post by winchendonsprings on 2010-10-30
little bump up

no one has run into this?

---

### Post by stanoly on 2010-11-16
I have the same experience with startupmanager.
Output from terminal:Grub2 detected
Usplash not detected
Splashy not detected
Traceback (most recent call last):
  File "/usr/sbin/startupmanager", line 54, in <module>
    main()
  File "/usr/sbin/startupmanager", line 51, in main
    SumGui()
  File "/usr/share/startupmanager/gtk_frontend.py", line 193, in __init__
    self.setup_widgets()
  File "/usr/share/startupmanager/gtk_frontend.py", line 202, in setup_widgets
    self.set_shared_grub_widgets()
  File "/usr/share/startupmanager/gtk_frontend.py", line 223, in set_shared_grub_widgets
    self.timeout_spinner.set_value(self.grub.get_timeout())
  File "/usr/lib/pymodules/python2.6/bootconfig/grub.py", line 91, in get_timeout
    timeout = utils.extract_number(line)
  File "/usr/lib/pymodules/python2.6/bootconfig/utils.py", line 64, in extract_number
    match = number_filter.search(line)
TypeError: expected string or buffer
 I am trying to get plymouth working in Ubuntu Lucid. No luck.

---

### Post by svalbard on 2010-11-16
I am running into an identical problem with Startup Manager on Linux Mint 9. 

I should note that this problem manifested immediately after I upgraded from 2.6.35-21-generic to 2.6.35-25-generic.

---

### Post by jsonder on 2010-12-09
I'm having a similar problem with a new Dell XPS L501.  Running startupmanager yields the following:

dad@dad-XPS-L501X:~$ startupmanager
Found initrd image: /boot/initrd.img-2.6.35-24-generic
Found linux image: /boot/vmlinuz-2.6.35-23-generic
Found initrd image: /boot/initrd.img-2.6.35-23-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda2
done
Grub2 detected
Usplash not detected
Splashy not detected
**
GLib-GIO:ERROR:/build/buildd/glib2.0-2.26.0/gio/gdbusconnection.c:2270:initable_init: assertion failed: (connection->initialization_error == NULL)
dad@dad-XPS-L501X:~$ 


Any one have suggestions for resolving this?

Thanx,
john

---

### Post by wilee-nilee on 2010-12-09
So here is the deal although your problems seem similar, due to the startup manager being the culprit you all have different set ups on your HD. So anybody wanting help should start a personal thread with a appropriate header, and do this.

So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags  paste all the text in between.

You can run this script in a installed Ubuntu setup as well.

If you want me to look at the script pm me. This script will give us the what is where and pertinent information, it is a great tool.

The first post was not being able to use the password login to startup manager be sure to confirm if this also happening in your personal setups.

---

### Post by dragon999 on 2011-02-21
I upgraded from 2.6.35-23-generic to 2.6.35-25-generic in Ubuntu. I can open the startup manager ( and it works) but I have no Appearance Tab. I am not able to change the the u splash theme. I have tried to change the u splash through the terminal window, but had no luck.

Any ideas would help and would be greatly appreciated...

---

### Post by zedwards on 2011-04-09
Sigh...same problem. Yet another ubuntuforum problem that goes unhelped. Are there people who have any answers in this forum? Never have ever seen a problem answered here.

---

### Post by zedwards on 2011-04-09
Oh figured it out on my own. Run sudo startupmanager instead of just startupmanager.

---

### Post by voyager99 on 2011-04-20
I installed my own version of python (2.7.1) in /usr/local/bin
and because this is the default version (set in my PATH)
it's not allowing startupmanager to run.
If you sudo su (to become root) and rename /usr/local/bin/python to some other name
and then make sure that /usr/bin/python is the executable that runs your python
scripts, then startupmanager works fine!
My installed python is missing the pygtk modules/libraries.

To get it running:

sudo su
mv /usr/local/bin/python /usr/local/bin/python-orig
ln -s /usr/bin/python /usr/local/bin/python

startupmanager
(now you can change GRUB via gui)

rm /usr/local/bin/python
mv /usr/local/bin/python-orig /usr/local/bin/python

---

