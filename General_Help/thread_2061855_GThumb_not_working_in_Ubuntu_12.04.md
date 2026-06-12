---
title: "GThumb not working in Ubuntu 12.04?"
date: 2012-09-23
forum: General Help
---

### Post by captainskyhawk on 2012-09-23
I'm sorry if I'm posting a duplicate of another thread, but I honestly don't think so, because I've search for the solution to this issue for weeks, and haven't found anything -- no in these forums, or on the internet at large, which just boggles the mind.

My problem is this -- in all previous versions of Ubuntu, GThumb has worked fine -- I use it to resize images.  It does this fine.  It's a simple thing.

Now, whenever I try to save an image in GThumb, I get this error message:

"Could not save the file

Could not find a suitable module to save the image as "image/png""

I have no idea what this means, I have no idea what's causing, and I've searched and searched for this error string on the internet -- nothing.  It's like I'm the only person in the universe having this issue.

I've tried deleting and reinstalling GThumb, I've tried deleting the config folder and reinstalling, hell, I've tried reinstalling all of Ubuntu.  Nothing.

What is going on?

---

### Post by Ballistic45 on 2012-10-07
I am having a similar problem, I am running ubuntu 12.04 LTS Precise.     gThumb has been working just fine until Precise did an update..  Ever sense then gThumb resize screen turns BLACK when trying to resize a picture.   Everything else with gThumb seems to work OK just cannot resize a picture any longer..  I am using gThumb 3.1.1..  BUT I believe when it worked before the update, it was an older version, can't remember which..  I have another Computer running the same exact OS with gThumb 2.14.3 and EVERY thing works fine.. I tried to install gThumb 2.14.3 on this machine but it fails do to dependencies not found   and needing older versions of Lib files or something ..  So something has changed, I think in both OS and updated gThumb, so now I can't go back to older version of gThumb and can't get full use out of this one....

Hope ubuntu group or gThumb group fix the conflict...

Anyone have a fix, I'd be most appreciative....... :confused:

---

### Post by goondah on 2012-10-07
I also am having the same problem with resizing photos in gthumb. Everything was working fine until a recent update. I was able to install an older version of gthumb and that has fixed the problem for now. The bug appears to be causing the resized files to be extremely small -- just a few kilobytes and they appear all black when viewed. To install the older version, you can issue the following commands in the terminal:

sudo apt-get purge gthumb
sudo apt-get install gthumb-data=3:2.14.3-0ubuntu1
sudo apt-get --install-recommends install gthumb=3:2.14.3-0ubuntu1

---

### Post by Ballistic45 on 2012-10-08
THANK YOU Goondah !  gThumb works great now..  I have been using ubuntu 10.10 then 12.04 for about two years now and still don't know the tricks to getting some stuff to work, thank God someone does..  Again Thanks...[URL="http://ubuntuforums.org/member.php?u=1740726"]  ):P
[/URL]

---

### Post by Ballistic45 on 2012-10-08
Whoops, spoke to soon, seems I can't save images in gThumb after going back to a previous version, I get this message "Could not find a suitable module to save the image as "image/jpeg", I'll keep trying to see what is holding this up..

---

