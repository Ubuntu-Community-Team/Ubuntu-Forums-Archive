---
title: "Deleted Windows partition and cannot boot"
date: 2012-03-25
forum: General Help
---

### Post by campbuds on 2012-03-25
I was ready to delete my windows partition and didn't think of the MBR before I did. Now I cannot boot (accept to live disk).

I tried reinstalling grub but I cannot mount my root partition sda4 and in fact I cannot even view my root partition in the finder. It exists but it says I do not have proper permissions and only shows a "lost and found" folder.

I wish I had done a backup before deleting the windows partition.

I NEED HELP PLEASE! I have never had a time where live disk could not access the hard drive partitions

I am running 11.10 and using an 11.04 live disk

---

### Post by idoitprone on 2012-03-25
> **campbuds said:**
> I was ready to delete my windows partition and didn't think of the MBR before I did. Now I cannot boot (accept to live disk).

I tried reinstalling grub but I cannot mount my root partition sda4 and in fact I cannot even view my root partition in the finder. It exists but it says I do not have proper permissions and only shows a "lost and found" folder.

I wish I had done a backup before deleting the windows partition.

I NEED HELP PLEASE! I have never had a time where live disk could not access the hard drive partitions

I am running 11.10 and using an 11.04 live disk

you can check if the hdd is still there

```
sudo blkid
```if you want us to help you with your boot problem then we need to evaluate the damage

run this boot script
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
[IMG]chrome://dictionarytip/skin/dtipIconHover.png[/IMG]

---

### Post by ajgreeny on 2012-03-25
How did you try to reinstall grub?

Deleting the windows partition should have made no difference to booting to ubuntu, assuming that you had grub 2 set up as default on your system, as grub should be on the mbr of the first disk, not in the windows partition on that disk.

Unfortunately you can not re-install grub on 11.10 using a live 11.04 system; you must use the same live version as the installed version because grub has changed too much along with the underlying OS, I think.

Running the boot-info-script should help sort out the problem, once we've seen the RESULTS.txt file.
Paste contents of RESULTS.txt in a New Reply, then highlight entire file and click on # (code tags) in edit panel to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ CODE] paste here [ /CODE] tags.

---

### Post by campbuds on 2012-03-25
Ok, I found out hat I couldn't use 11.04 to wok on 11.10. That took care of it. Thanks

---

