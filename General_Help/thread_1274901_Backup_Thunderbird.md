---
title: "Backup Thunderbird"
date: 2009-09-25
forum: General Help
---

### Post by Quarkrad on 2009-09-25
In my very limited experience it has been better to reinstall from new, rather than upgrade, new releases of Ubuntu (e.g. 8.04 to 8.10 and 8.10 to 9.04).  I am keen on 9.10 with grub2 so am expecting to reinstall a new build.  However, I use Thunderbird mail with three different email addresses in it - it works great, as can use all three mail addresses in one client.  A quick Google has advised using third party apps that make this easy but so far all I have found are none Linux apps.  How can I save all my mails, contacts, etc in Ubuntu/Thunderbird?  As a newbie a GUI would be preferable although the terminal is becoming a little familiar - although I tend to use it with blind faith rather than know what I am typing in actually means.

---

### Post by akakingess on 2009-09-25
I'm not in front of my Ubuntu machine right now so this isn't a definite, but usually there is a hidden folder like .thunderbird or something of that nature, notice the .  in the front, that denotes hidden, and those folders usually hold profiles,settings, and I think in the case of Thunderbird possibly the emails.  Of course, I will have to recommend that you do the proper exporting and all that jazz as the safest way to make sure you get everything, but I believe that if you get that hidden Thunderbird folder you should be safe, but please don't take just my word for it. BTW, to view hidden files/folders within Nautilus just hit CTRL + H and you will be able to see the hidden files. Thunderbirds may be under a Mozilla folder as well. I wish I were in front of my Ubuntu laptop and hadn't left it at home (I am currently at work) otherwise I would have a more definite answer for you, but at least this is a start.

---

### Post by scouser73 on 2009-09-25
The Thunderbird profile can be found by showing the hidden files, to do this please follow the steps.

**1** - Go to **/home/yourname**

**2** - Press **CTRL & H** to open the hidden files & folders

**3** - Now you can see the file **/home/yourname/.mozilla-thunderbird**

**4** - Save the folder **/home/yourname/.mozilla-thunderbird** onto a CD or external drive

**5** - Install Thunderbird on your new drive.

**6** - Now open the newly installed Thunderbird & then close it immediately

**7** - Now go to the newly made Thunderbird folder: **/home/yourname/.mozilla-thunderbird** and delete all the contents inside the newly created folder but not the folder itself

**8** - Now paste your existing Thunderbird profile into **/home/yourname/.mozilla-thunderbird**

**9** - Start up Thunderbird, and now you will see all your email accounts, contacts & emails


[COLOR="Red"]**Ubuntu Karmic Koala is still only in Alpha at present**[/COLOR]

---

### Post by akakingess on 2009-09-25
Thank you scouser73 for going into more detail, like I stated before, it is hard to remember some of those things when you are forced to sit in front of a Windows machine ; )

---

### Post by Quarkrad on 2009-09-25
Thank you - that was perfect.  Can I do the same thing with firefox?  I know bookmarks have an export function but what about passwords etc?

---

### Post by nikhilk on 2009-09-25
> **Quarkrad said:**
> Thank you - that was perfect.  Can I do the same thing with firefox?  I know bookmarks have an export function but what about passwords etc?

Yes, all your settings, bookmarks, history, saved form values etc will be backed up if copy your firefox profile folder.

---

### Post by scouser73 on 2009-09-25
Yes, the same instructions apply except the folder is **/home/yourname/.mozilla**

**1** - Copy **/home/yourname/.mozilla** onto a CD or external drove

**2** - Install Firefox on your drive

**3** - Start Firefox and immediately close it again

**4** - Delete everything in the newly created **/home/yourname/.mozilla** but not the folder itself

**5** - Paste your original Firefox profile into **/home/yourname/.mozilla**

Start Firefox and all your bookmarks & saved passwords and everything else from your previous firefox profile will be there.

---

### Post by Quarkrad on 2009-09-25
Thanks again - when I change over to 9.10 I now have confidence I will get my 'Old Ubuntu' back again but with the new features.  :)

---

