---
title: "Two Linux OS's, How to remove one, while leaving the other opperational"
date: 2011-11-21
forum: General Help
---

### Post by Bach.Greenville IT on 2011-11-21
Hey guys,
I couldn't seem to find anything on the internet that explained this: I have two Linux OS's installed; Kubuntu, and Ubuntu. I would like to remove Kubuntu (for the HD space), and leave Ubuntu fully operational. Is there a way to do this without completely re-installing my system? And if so, could you please provide detailed instructions on how to do so. (I'm using GParted as my manager.)

---

### Post by oldfred on 2011-11-21
Only one is in control of MBR. Which system is first in the menu that you boot from. If it is the one you want to keep then it is already in the MBR and you do not have to do anything. But if the first is the one you want to delete you need to boot into the one you want to keep and install grub2's boot loader to the MBR.
#reinstall from working (not liveCD) system - first find Ubuntu drive (example is drive sda but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
# then refresh menu
sudo update-grub

Then you can use gparted to remove Kubuntu. You can reformat space to data folder(s) or move /home into it. You could expand / (root), but i normally suggest / be 10-20GB for efficiency and have all your personal data in a data partition or have all user settings & data in a separate /home partition.
After you have deleted the Kubuntu data another sudo update-grub will remove it from the boot menu.

---

### Post by Bach.Greenville IT on 2011-11-21
Thank you oldfred!
That was very precise and quick. However, I am still confused. (Sorry.) You asked which system is first: well Ubuntu is first in the list. (/dev/sda1 [I think. I'll check to be sure.]) But you said if it is first in the list, I don't have to do anything. However I can't seem to unmount /dev/sda6 to reformat it. I have attached a screenshot of my GParted readings, and of the boot list (sorry for the quality, my phone cam isn't very good). Thank you for your patience with me. Hope that info can help.

---

### Post by oldfred on 2011-11-21
You cannot use gparted on mounted partitions (the little key). And if any logical partition is mounted it in effect mounts the entire extended partition.

When I said first, it is first in the grub menu? Not partition order.

So you need to use a liveCD and liveCDs usually use the swap partition to speed things up. So click on swap(s) and right click choose swap off. 

You show you are using sda6, is that your Ubuntu or Kubunutu? and sda1 is mounted as /media/....UUID. You need to be sure which is which.

May be best to post this from your Ubuntu install. It will show all the details:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
sudo apt-get install mawk

---

