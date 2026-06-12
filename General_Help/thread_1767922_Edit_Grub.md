---
title: "Edit Grub"
date: 2011-05-26
forum: General Help
---

### Post by drakejacob on 2011-05-26
Hello,
Can please anyone tell me how to edit the grub listing that appears during computer boot.
My listing shows 3 OS:-
1. Ubuntu 10.04
2. Ubuntu 9.10
3. Windows XP

I have deleted Windows XP, meaning that my system does not contain Windows XP.

---

### Post by Elfy on 2011-05-26
Assuming that you're using grub2 then

```
sudo update-grub 
```

should do it.

---

### Post by oldfred on 2011-05-26
Since you have two Ubuntus, you have to run the update to grub in the Ubuntu that has control of the MBR and is the one listed on top of the menu. 
If you run it on the other install it will not change the menu of the version you boot.

---

### Post by drakejacob on 2011-05-27
> **forestpiskie said:**
> Assuming that you're using grub2 then

```
sudo update-grub 
```should do it.

I did that and the output was:

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-31-generic
Found initrd image: /boot/initrd.img-2.6.32-31-generic
Found linux image: /boot/vmlinuz-2.6.31-23-generic
Found initrd image: /boot/initrd.img-2.6.31-23-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
done

All I want to do is remove the entries for Ubuntu 9.10 and Windows XP.

This listing appears because there was Windows XP installed on my system. Later, on I formatted the drive containing it and installed Ubuntu 9.10 in its place.

During Update of Ubuntu 9.10, I upgraded it to Ubuntu 10.04.2 .

But, I do not know how to remove these entries.

---

### Post by dragonfly41 on 2011-05-27
You can install Grub Customizer which you can then launch from System Tools.

---

### Post by drakejacob on 2011-05-27
> **dragonfly41 said:**
> You can install Grub Customizer which you can then launch from System Tools.

Thank you for the help but I also want to know if there is any manual way of doing it?

---

### Post by LordNeo on 2011-05-27
The Windows partition is still there? If not, it shouldn't detect the Windows entry and delete it automatically...
You can always rename the "otherOS" file from /etc/grub.d/ and then do update-grub, it will not read the other OS entries

EDIT: Sorry, it's called, OS Prober

---

### Post by oldfred on 2011-05-27
If you deleted windows from sda1 then the os-prober will not find it. You must have boot.ini, ntldr, ntdetect.com. If you delete the boot files then it will not find XP.

You can remove old kernels in synaptic, just be sure to not remove the one you are using:
Check current kernel:
lsb_release -a
Go to Synaptic Package Manager and search for linux-image.
More info in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

---

### Post by drakejacob on 2011-05-28
> **LordNeo said:**
> The Windows partition is still there? If not, it shouldn't detect the Windows entry and delete it automatically...
You can always rename the "otherOS" file from /etc/grub.d/ and then do update-grub, it will not read the other OS entries

EDIT: Sorry, it's called, OS Prober

The output of the update-grub command is:
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-31-generic
Found initrd image: /boot/initrd.img-2.6.32-31-generic
Found linux image: /boot/vmlinuz-2.6.31-23-generic
Found initrd image: /boot/initrd.img-2.6.31-23-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
done

After doing this, I restarted and the listings of Windows XP and Ubuntu 9.10 were still there.

---

### Post by oldfred on 2011-05-28
Post this so we can see what is where:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by drakejacob on 2011-05-28
> **oldfred said:**
> Post this so we can see what is where:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

Thanks for the help, but right now I booted the system and all the listings were gone only the required listings of Ubuntu 10.04.2 were there. All I did was as told to rename OS Prober and run update-grub. It didn't happen before but now the listings have changed.

I also edited OS Prober but due to compilation errors, I had to undo the corrections. But later, on I found the Windows XP related files and deleted them and perhaps the Ubuntu 9.10 entry was deleted by running update-grub command.

Thank you

---

### Post by j0eb0b on 2011-05-28
I too want to edit out my old Unbuntu kernels.  Synaptic shows that OS Prober is installed but I can't find it in the Admin menu.  Is OS Prober invoked from terminal?

Sorry for this basic question.  You'd think I'd be able for find this after all these years.

---

### Post by drakejacob on 2011-05-28
> **j0eb0b said:**
> I too want to edit out my old Unbuntu kernels.  Synaptic shows that OS Prober is installed but I can't find it in the Admin menu.  Is OS Prober invoked from terminal?

Sorry for this basic question.  You'd think I'd be able for find this after all these years.

OS Prober is a file which can be found under
/etc/grub.d/

It would probably be named as 30_os-prober or something like that.

---

### Post by Elfy on 2011-05-28
> I too want to edit out my old Unbuntu kernels. Synaptic shows that OS Prober is installed but I can't find it in the Admin menu. Is OS Prober invoked from terminal?

Sorry for this basic question. You'd think I'd be able for find this after all these years.This is a different kettle of fish completely and exactly why it's best to start a thread of your own.

Find the old kernels you no longer want in synaptic - try a search in there for linux-image - mark for removal - grub will update - you'll no longer see them in grub.

If for some reason you actually want to keep the old kernels and not see them in grub then it needs the posts taking out of this thread and starting a new one - that being the case - report the post(s) and ask for them to be moved to a new thread or PM and I will do so when I next login.

---

### Post by j0eb0b on 2011-05-29
Thanks for the advice. I will give it a try.

I didn't mean to hijack the thread.  I guess I didn't understand the original question and responses.

---

### Post by linuxinstalledfromhdd on 2011-05-29
> **forestpiskie said:**
> This is a different kettle of fish completely and exactly why it's best to start a thread of your own.

Find the old kernels you no longer want in synaptic - try a search in there for linux-image - mark for removal - grub will update - you'll no longer see them in grub.

If for some reason you actually want to keep the old kernels and not see them in grub then it needs the posts taking out of this thread and starting a new one - that being the case - report the post(s) and ask for them to be moved to a new thread or PM and I will do so when I next login.

Also if you want, Ubuntu-Tweak has an option to automatically remove older Kernels. It's handy :) :P

---

### Post by Elfy on 2011-05-30
> **linuxinstalledfromhdd said:**
> Also if you want, Ubuntu-Tweak has an option to automatically remove older Kernels. It's handy :) :P
I thought all it did was remove them from the list?

---

### Post by j0eb0b on 2011-05-30
Your advice to mark the old kernels for uninstall in Synaptic did what I was trying to achieve.  Thanks for the help and sorry to muddy the water.

---

