---
title: "Unhandled lockdown error (-15)"
date: 2012-09-11
forum: General Help
---

### Post by dr1094 on 2012-09-11
please help, I tried asking this here: [[http://ubuntuforums.org/showthread.php?t=1861617&page=7]](http://ubuntuforums.org/showthread.php?t=1861617&page=7]) but no answers, so...

problem: "Unable to mount iPhone - unhandled lockdown error (-15)" error when I connect my iphone to my laptop.

[*I just want to say in advance that I do not want to install any additional software packages as you will see from my description, that I probably don't need to.*]

I have iPhone 3gs (16 Gig), running iOS 5.1.1, and an iPod Touch 1st Gen running iOS 3.1.2.

I have 3 usernames on my laptop. userA, userB, userC. The iPhone is not detected on only one username (usernameB), it is connected perfectly on other usernames (A&C) on the same machine. 
However, the iPod connects on usernameB perfectly. 

Do i really have to install additonal software, since it works anyway on other usernames?

Other details: 
- the iphone does charge
- cannot see iphone under disk utility- 
- CAN see iphone in terminal: lsusb
- iphone is jailbroken
- before the iphone use to show up in two parts: One was called 'user's iPhone', and other was called 'Document's on user's iPhone'. This is how the iPod stil shows up. However, the iPhone shows up as one directory, called user's iPhone. but it is unaccessible due to error, as above.
- let me know if you need more details


Thanks for any answers, I appreciate all responses.

---

### Post by 2F4U on 2012-09-11
There is a bug report on this issue:

[https://bugs.launchpad.net/ubuntu/+source/libplist/+bug/877440](https://bugs.launchpad.net/ubuntu/+source/libplist/+bug/877440)

and an article on how to fix the problem:

[http://www.upubuntu.com/2012/02/fix-unhandled-lockdown-error-when.html](http://www.upubuntu.com/2012/02/fix-unhandled-lockdown-error-when.html)

---

### Post by dr1094 on 2012-10-12
> **2F4U said:**
> There is a bug report on this issue:

[https://bugs.launchpad.net/ubuntu/+source/libplist/+bug/877440](https://bugs.launchpad.net/ubuntu/+source/libplist/+bug/877440)

and an article on how to fix the problem:

[http://www.upubuntu.com/2012/02/fix-unhandled-lockdown-error-when.html](http://www.upubuntu.com/2012/02/fix-unhandled-lockdown-error-when.html)
I really didn't want to install new packages, but let's move beyond that.

Can someone please tell me the reason that the same iphone gets detected on two out of the three user names (on the same machine)?

---

### Post by dr1094 on 2012-10-12
So I had had enough with this problem and spend the last few minutes tackling it...FOUND THE SOLUTION.

PLEASE READ ENTIRE SOLUTION BEFORE FOLLOWING THE INSTRUCTIONS. I wouldn't try this on the main user (administrator) because I am too paranoid, and wouldn't want to take that risk, could use an expert's opinion on this.

so:
1. At first I reset GNOME by removing the following hidden folders in home directory: .gconf, .gconfd, .gnome2. 
*cut and pasting it into another folder on the desktop will have similar effect.*
Then log out and log back in to complete the gnome reset.

Then I realized that it accomplished nothing but reset the gnome.

2. In the home folder there is a folder called ".config". In the folder .gconfig there is another folder called "libimobiledevice". I cut all the files from the folder 'libimobiledevice' and paste them into a seperate folder on my desktop, so I could recover them incase I was doing something wrong. And Then I logged out. note: I didn't delete, rename, or remove the actual folder 'libimobiledevice' just the files in it.

At this point the iphone is unplugged. And I am still not logged in.

3. Then I turned off the iphone (hold down power button for 5 seconds, and slide the red button.) 

4. When it is completely off, connect it to your computer.

5. Then I logged back in, the iphone was now connected and automatically powered on. And it seems fixed at the moment. It connected without errors.

----------------------------------------------------
Would love to have expert's opinion on this method, I really didn't want to install additional packages. Please comment on my approach especially if I did something terribly wrong. I am thinking step 1 is unnecessary. Please try this and let me know how it works for you. Thanks

---

### Post by temenchat on 2013-04-24
Thank you, your solution works for me.
I do have same problem, and it seems occurred after I reset and erase whole things in my iPhone4s.
I also found an answer from [http://www.upubuntu.com/2012/02/fix-unhandled-lockdown-error-when.html](http://www.upubuntu.com/2012/02/fix-unhandled-lockdown-error-when.html)
But I don't try it since my problem has already been solved

---

