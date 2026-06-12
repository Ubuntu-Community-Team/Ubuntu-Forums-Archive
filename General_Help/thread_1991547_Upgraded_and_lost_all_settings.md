---
title: "Upgraded and lost all settings"
date: 2012-05-30
forum: General Help
---

### Post by jlh68 on 2012-05-30
I upgraded from 10.10 to 12.04LTS, and I no longer have any settings for email, web browser, etc.  My old HOME folder is on another partition and now I have that as another drive, and a secondary list of empty files called: desktop, documents, downloads, music, pictures public, templates, videos, and examples.  All of these are also on my home partition with my data in them.  So now my home file is this new empty file.  I also lost all of my folders in Thunderbird as well as my calendar.

How should I have upgraded so that these settings would have been retained?

How do I find them or should I create some new partitions for them, so next time I don't have this problem?

This is an area that Ubuntu is weak in explaining  and the choices when upgrading.  I just hope my dual boot is not screwed up.:(

---

### Post by ianc1 on 2012-05-30
Sorry to hear you're having issues.  I usually do a fresh install myself which means I also loose settings.  Like yourself the main thing I care about is the browser and mail desktop client, I used to use Thunderbird.

Firefox settings are in a directory ~/.mozilla.  I am fairly sure you can just copy this across, but maybe someone else can confirm this.

I think Thunderbirds settings are in ~/.thunderbird.

Hope this helps.

---

### Post by ajgreeny on 2012-05-30
I think that you did not choose the old /home partition as the new, unformatted /home partition when you got to the partitioning stage of the installation.  You must, I think, have used a clean install using a CD, not done an online upgrade of distro, or the old home would have been automatically used

It is easy to put right once we know what the partition layout and UUIDs are on your system.  The one needed is the UUID for the old home partition, which you can find from the command ```
sudo blkid
```Once you are sure simply use command ```
gksudo gedit /etc/fstab
``` and add a line or two to /etc/fstab which needs to be in this format:-
```
# /home on /dev/[COLOR=Red]sda#[/COLOR]
UUID=[COLOR=Red]e2554df2-7e16-4864-97c9-834d8bebecda[/COLOR] /home           ext4    defaults        0       2
``` Change the parts shown in red above to whatever your partition device name and UUID is, of course, and then you should be able to use command ```
sudo mount -a
``` or just reboot to have your old /home back.

If you are still not sure about this, show the output of the blkid command, tell us which was the old home partition and we'll take it from there.

---

### Post by jlh68 on 2012-05-30
**ajgreeny**  I followed your codes and it now works like it should.

Thanks for the prompt response.

** ianc1**  thanks, I have a feeling that all of my settings and old emails are gone.  I should have figured oout a way to save all of that.  I did export my address books to a flash drive.  Now I need to import them.

I guess I was reluctant to use Unity in 11.04 and 11.10 and I now have all three computers on 12.04LTS.

---

### Post by jlh68 on 2012-05-31
**ianc1**  Well what do you know, when I got my /home partition reattached to my menu correctly, I now have all my old emails, and settings, and some other apps like gnote.

Thinkgs are deffinately looking better.  I just need to figure out how to clear the recent files so they don't show.

---

### Post by ajgreeny on 2012-05-31
> **jlh68 said:**
> **ianc1**  Well what do you know, when I got my /home partition reattached to my menu correctly, I now have all my old emails, and settings, and some other apps like gnote.

Thinkgs are deffinately looking better.  I just need to figure out how to clear the recent files so they don't show.
That is what I expected, as all your mail etc etc was in the hidden folders in your old home.

For recently used files have a look in the file **.local/share/recently-used.xbel** in your home and rename it as recently-used.backup.  I can't promise it will get rid of the lists, but it should do for some at least.

---

