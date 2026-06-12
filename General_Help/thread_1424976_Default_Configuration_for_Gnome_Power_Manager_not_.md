---
title: "Default Configuration for Gnome Power Manager not installed Correctly"
date: 2010-03-08
forum: General Help
---

### Post by pjoshyjosh on 2010-03-08
I ran into this problem yesterday morning when I came down to my computer and tried loggin in.  I had used the computer fine the day before - and setup a new theme and a few other neat features.  I had been using ubuntu for about a month on a Dual Boot system with Windows XP.  My HDD is 160 GB and my Ubuntu Partition was 50 of that.

My computer was left on and went to hibernate mode - so when I moved the mouse to login, I noticed the colors for login were different (now blue for Gnome I guess?).  Needless to say, login failed and I had a message on the top right that the Default Configuration for Gnome Power Manager did not install Correctly.  This was perplexing and I Had no idea what that meant (I am new to Linux).  I searched and searched and found no real solution that worked for me.  I found a few hints and realized that it looked like my Partition was full (50GB).  

Well, I finally looked up some commands and using the Netboot terminal from the Rescue boot I was able to "rm -r xxx" certain directories with large amounts of data (Podcasts and Videos).  

Viola! the system booted with no problem.  

ROOT CAUSE - Ubuntu HDD (Partition on HDD) was full and therefore login would not succeed. 

I will now begin storing all large files on my 500GB backup drive.  (andor buy larger HDD to run Ubuntu dedicated).

Hopefully this saves some people their data - as I had removed or done something to delete my Thunderbird account.  Seems to be all that I lost (my email.. ugh).

Thanks
JM

---

### Post by brucemuir on 2010-04-27
Hi, I was playing around with LVPM ([http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)) trying to get my ubuntu within windows partition to be bigger, and then I got your error.
So I went in and deleted some stuff and that fixed it! Thanks to your post..

But now I'm getting the same power-manager error, and I can't think of anything else to delete. I think it has something to do with me fooling around with LVPM

---

### Post by EliotB on 2010-05-02
I got here because I had the same error message.  In my case, I had a separate partition mounted on /tmp,  and wanted to use it for something else, so I removed it from fstab.

However, the underlying /tmp directory did not have the correct permissions, so I guess some runtime files could not be written there.  Fixing the permissions fixed the problem.

---

### Post by NotTheVistaVirus on 2010-05-23
I have same warning on startup. What permissions did you set on /tmp to get it working?

---

### Post by Random_Dude on 2010-07-01
> **pjoshyjosh said:**
>   

Well, I finally looked up some commands and using the Netboot terminal from the Rescue boot I was able to "rm -r xxx" certain directories with large amounts of data (Podcasts and Videos).

Could you be a little more specific about what you did in this part?

I have the exact same problem and I've tried ctrl+alt+F1 but all I've got is my console giving me some errors messages.

Thanks :cool:

PS: Nevermind, I fixed it.

---

### Post by hoofdbaas on 2010-12-05
> **pjoshyjosh said:**
> I ran into this problem yesterday morning when I came down to my computer and tried loggin in.  I had used the computer fine the day before - and setup a new theme and a few other neat features.  I had been using ubuntu for about a month on a Dual Boot system with Windows XP.  My HDD is 160 GB and my Ubuntu Partition was 50 of that.

My computer was left on and went to hibernate mode - so when I moved the mouse to login, I noticed the colors for login were different (now blue for Gnome I guess?).  Needless to say, login failed and I had a message on the top right that the Default Configuration for Gnome Power Manager did not install Correctly.  This was perplexing and I Had no idea what that meant (I am new to Linux).  I searched and searched and found no real solution that worked for me.  I found a few hints and realized that it looked like my Partition was full (50GB).  

Well, I finally looked up some commands and using the Netboot terminal from the Rescue boot I was able to "rm -r xxx" certain directories with large amounts of data (Podcasts and Videos).  

Viola! the system booted with no problem.  

ROOT CAUSE - Ubuntu HDD (Partition on HDD) was full and therefore login would not succeed. 

I will now begin storing all large files on my 500GB backup drive.  (andor buy larger HDD to run Ubuntu dedicated).

Hopefully this saves some people their data - as I had removed or done something to delete my Thunderbird account.  Seems to be all that I lost (my email.. ugh).

Thanks
JM

Thanks for the tip, ran into the same problem and I don't think I could have solved it without you. Nothing was lost.

---

