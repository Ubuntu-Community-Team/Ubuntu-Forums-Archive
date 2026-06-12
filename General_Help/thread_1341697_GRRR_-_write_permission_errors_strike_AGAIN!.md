---
title: "GRRR - write permission errors strike AGAIN!"
date: 2009-11-30
forum: General Help
---

### Post by osmorphyus on 2009-11-30
alright, a common issue that gives anyone in linux problems here:  DEFAULT PERMISSIONS FOR SAVING FILES!


alright, i get it:  supposedly people will ruin their systems by saving a png file outside of the "home" file system.  no, i don't buy it.  i get it, but i don't buy it, because that wont happen to me.

i need all applications in ubuntu to have GODLIKE POWERS.  that means WRITE PERMISSIONS ALL ACROSS THE BOARD.

pardon the caps, but with this frustration on top of the shitty music my woman is playing in the background behind me, i am an unhappy camper right now.  that is *NOT* me yelling, but expressing a dire and immediate need to have full access to my FS by allll apps.


what happened?  i tried to save a simple gradient into a theme folder in my drupal installation, located at /var/www/aaaa/sites/all/themes/...  you get it.

suuuure, i can save the file to my desktop then manually drag and drop it where i need it to be in root access of PCMAN, but im getting sick of that.  its very convoluted, doing 3 steps to achive 1 step.

so whats up, folks?  how can i assign WRITE permissions all acroos the board for *everything* in ubuntu?  its f'ing ignorant as hell in this day that the linux programmers are still under the impression that people are going to cause drastic harm to their FS by allowing them to write to it.

do i have read/write permissions by default for the folder i am trying to write (save) to?  yes i do!  now its a problem of GIMPS permissions, i assume.

simply summed up with:
HELP!

thanks.

---

### Post by hwttdz on 2009-11-30
You're saying you're having trouble using gimp to save to a folder which has 755 permissions?

---

### Post by u.b.u.n.t.u on 2009-11-30
To run Ubuntu like Windows simply log in as root or in the terminal enter sudo su.

Oh and, don't forget to install a firewall, antivirus, a malicious software blocker, anti trojan, rootkit blocker, anti key logger ... heck, just switch to Windows! lol

Seriously though I hear what you are saying. Creating gradients is pretty cool and being unable to save the same would be most annoying.

That said, unless you plan to spend a lot of time creating gradients, I would recommend just doing it the linux way and being happy you don't need to install software after software to secure your system.

If on the other hand you want to access a particular folder with an on going basis, then change the permissions of that folder.

Choosing between no needed security software for Ubuntu 9.10 and the four security functions I am running on Windows 7, I think Ubuntu is better. Though each to their own.

---

### Post by osmorphyus on 2009-11-30
hwt, your quip helps noone.  i figured out one way to login as root.  its retarded, but so far, so good.

by the way, your quip wasn't very good, either.

ubu, yeah, sudo su all day and night gets old, especially just to open an application with full access.  i think ill be safe running in root, really.  im not cruising for porno enough to snag those kinds of 'viruses'.  as well, i was always under the impression that linux has no threat of viruses.  

as stated i already had set the permissions for the folder for read/write/exe, but gimp still didnt believe it had access to it, even tho i set said permissions before launching gimp.

its all good now, logged in as root, saved away.  continuing my work.  im trying to stay away from windows ever again.  i really don't see the need for windows on one box, lin on another, or windows in a virtualbox, wine for emulating.  maybe someday ubuntu will be as all consuming as windows, and we won't need windows for anything ever again.

good lookin out, ubu.  hwt, keep working on your sarcasm and ideas of what "helping" is.  remember, this is ubuntu, african for community, which means we all have to hold hands and help out, without arrogance, which many wiki people are full of.  snide?  no way, man!

---

### Post by hwttdz on 2009-11-30
osmorphyus, I think you'll find the better the quality of your question the better the quality of the answer people are able to give you.  If your question is actually how to assign write permissions to all directories/files then I believe

sudo find / -print0|xargs -0 -n 10 sudo chmod a+w
sudo chmod a+w /

however you can be pretty sure this will break your system.  Hence my asking if your question is actually having something to do with being unable to save to a directory with 755 permissions.

---

### Post by hwttdz on 2009-11-30
And possibly better questions that you might be thinking of would be how to reconfigure apache to serve a different directory (you can serve a directory from inside your home directory which makes a lot of sense), or how you can create a symbolic link in /var/www to a directory in your home directory, which is a quick easy solution to the problem you may be having.

---

### Post by u.b.u.n.t.u on 2009-11-30
osmorphyus running as root does create many of the problems inherent in Windows and therefore requires many of the security measures.

Essentially you are wanting to run Gimp as root. Is that correct? If so, then a solution limited to that is what is required and nothing more.

Securing your work from the net is important. Running default as root seriously compromises all of your creative artwork. Best to reconsider such a move.

All the best.

---

### Post by scouser73 on 2009-11-30
> **osmorphyus said:**
> alright, a common issue that gives anyone in linux problems here:  DEFAULT PERMISSIONS FOR SAVING FILES!


alright, i get it:  supposedly people will ruin their systems by saving a png file outside of the "home" file system.  no, i don't buy it.  i get it, but i don't buy it, because that wont happen to me.

i need all applications in ubuntu to have GODLIKE POWERS.  that means WRITE PERMISSIONS ALL ACROSS THE BOARD.

pardon the caps, but with this frustration on top of the shitty music my woman is playing in the background behind me, i am an unhappy camper right now.  that is *NOT* me yelling, but expressing a dire and immediate need to have full access to my FS by allll apps.


what happened?  i tried to save a simple gradient into a theme folder in my drupal installation, located at /var/www/aaaa/sites/all/themes/...  you get it.

suuuure, i can save the file to my desktop then manually drag and drop it where i need it to be in root access of PCMAN, but im getting sick of that.  its very convoluted, doing 3 steps to achive 1 step.

so whats up, folks?  how can i assign WRITE permissions all acroos the board for *everything* in ubuntu?  its f'ing ignorant as hell in this day that the linux programmers are still under the impression that people are going to cause drastic harm to their FS by allowing them to write to it.

do i have read/write permissions by default for the folder i am trying to write (save) to?  yes i do!  now its a problem of GIMPS permissions, i assume.

simply summed up with:
HELP!

thanks.

**1** - Go to **Terminal**, copy & paste this command: **gksudo nautilus** that will open Terminal as root

**2** - Navigate to your  folder/file/drive, **Right Click**, select the **Permissions** tab 

**3** - Change the **Owner** drop-down menu to your name, then change **Folder Access** to **Create & Delete Files**, then **File Access** to **Read & Write**, then **Group** to your name, **Folder Access** to **Create & Delete Files**, **File Access** to **Read & Write** then click **Apply Permissions To Enclosed Files**.

You will now have full access to your folder/file/drive.

---

### Post by osmorphyus on 2009-11-30
thanks for all the tips, guys.

i setup another box so i can dink around and learn more about the priveledges with linux.  so far on my main box, i havent had problems with root, but i have since also decided ill stick with a standard user login until i know more about it.

it is very different for people new to the linux environment, having so many locked rights to your HD/FS.  i dont understand the reasoning behind it all yet, but i have been reading in the forums here and other places since last i was here posting.

i have to say this much - before i started taking ubuntu seriously, i was walways excited to see "what was new" when MS released a new windows.  since my experience in ubuntu, i havent had one shred of want to check out win 7.

i was turned off of ubuntu a fwe years ago when i tried it on an old laptop, the hardy heron release didnt support my sound device properly (only had 1 channel output thru the headphone jack!) and i had no control of my screen resolution.  the reason why i decided to get started with ubuntu again?  my windows based HD is failing, slower to boot than ever, and i've began thinking that the NTFS/FAT based FS's are destructive to HD life.  that may not be so, but i have been wondering if the excessive load on the HD from the impractical way that FAT (if not NTFS as well) writes causes premature HD failure.  of all the HD's i have had die on me, they have all been FAT32 or NTFS based.  i figured that needing to constantly reorganize the HD's contents (defrag) adds an excessive load to the HD.  i could be wrong, but until i know more, it seemed like a decent hypothesis.

and yes, maybe my question was a bit long and off the wall, but i was soo frustrated at the time.  fortunately however, i got a lot of good tips and advice from you guys.  i appreciate all of it.

ill be around!  thanks again to everyone!  :popcorn:

---

### Post by osmorphyus on 2009-11-30
the idea of setting up apache/mysql/php outside of its default and protected directory intrigues me.  do any of you have any information on this?

i found this on google but it doesnt really get at what im thinking was suggested:
[http://articles.techrepublic.com.com/5100-22_11-5076696.html](http://articles.techrepublic.com.com/5100-22_11-5076696.html)

---

### Post by u.b.u.n.t.u on 2009-11-30
> **osmorphyus said:**
> the idea of setting up apache/mysql/php outside of its default and protected directory intrigues me.  do any of you have any information on this?

i found this on google but it doesnt really get at what im thinking was suggested:
[http://articles.techrepublic.com.com/5100-22_11-5076696.html](http://articles.techrepublic.com.com/5100-22_11-5076696.html)

I think your question warrants a new thread.

---

