---
title: "File Server Back Up and Encryption"
date: 2009-09-27
forum: General Help
---

### Post by TiredBird on 2009-09-27
I needed a special antenna to pick up a weak wireless signal, (with a 650 KB/S connection to the internet), and dedicated a computer to interfacing it and sharing its connection with my other household computers, (which are 3). 

Having devoted a relatively potent computer to the task, (1.8 GHz, 1/2 Gig ram), I decided to also add three 160 GB drives, (from my junk box), and create a file server having solid backup and provision for encryption. I have also added a mirror the software repositories for 8.04 and 9.04. 

The server works great. My total data needs are less that 160 GB so I have two full stages of backup automatically handled by cron. I also update the mirror nightly as a cron job.

Right now I have two computers using the server for internet connection, software updates, home directory, wallpaper, etc. I am about to add the third.

My problems began when I realized that some of my data files are large enough to cause noticeable slowdown when operating them remotely. For the home directory, wallpaper, etc., I concluded that I needed local copies and have added local copies of those items to each computer. 

However, those are also the areas that have a lot of changes. So I have incorporated 'unison' to syncronize my individual computers with the server. That also works fine but...

And this is the big 'but' - I have several directories that are encrypted, using Truecrypt. (Yes, I know that Ubuntu has its own encryption system now but I started using Truecrypt almost three years ago when there were no acceptable alternatives.)

The encrypted data resides in seven different data sets, ranging in size from 100 MB to 6 GB. They are all single file containers in my home directory. Trying to sync them when encrypted is extremely time consuming as the entire container has to be transferred over the network, (at 54 Kb/s), each time there needs to be a syncronization.

Being the brilliant man that I am, (:lolflag:), I decided the way to solve this was to open both copies, (server and client), and do a sync of the unencrypted files. 

You may have noted that my "brilliance" has gotten me progressively deeper and deeper in the smelly stuff. :guitar: No exception this time either.

For some reason, unison will not sync between two Truecrypt datasets. I open and mount one on the server, then I open and mount its counterpart on the client. Then I startup unison which appears to run very quickly with no error messages and reports that the two file systems are equal. (Only they're not. I can see the differences.)

I am open to suggestions. I've already changed this system four or five times, I guess it won't kill me to do it again. :( I am willing to read howto's and tutorials or anything else. I just need someone to tell me what I need to do.

Thanks in advance for your help!
:confused:

---

### Post by StuartN on 2009-09-27
If you split your encrypted data into smaller files then less would have changed. Or separate the older, unchanging data that is encrypted from the newer, changing data that is encrypted then only the smaller set will need copying at most backup stages.

That way the backup software only needs to see that a difference exists between the current and the backup, without any need to decrypt.

---

### Post by TiredBird on 2009-09-27
I'm giving that concept serious thought. But I need to work out a few problems. Mainly I need to be able to access all of the data as if it was one dataset, even though there are only parts of it that change.

---

### Post by TiredBird on 2009-09-28
I rearranged my file structure and got it to work! Then I started looking to see what was different. I discovered that I had left a level out of my paths.

Next thing ya know I'll be forgetting to put the plug in. I really love growing old!

---

