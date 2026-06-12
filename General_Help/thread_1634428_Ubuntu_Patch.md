---
title: "Ubuntu Patch"
date: 2010-11-30
forum: General Help
---

### Post by meyou1 on 2010-11-30
ok, so here's my problem: I'm running Ubuntu 10.04 and I recently decided to boost its speed to maximum
while reading through various Internet sites about different ways of doing this I found out about this patch:
[http://www.omgubuntu.co.uk/2010/11/linux-to-get-a-lot-faster-due-to-new-patch/](http://www.omgubuntu.co.uk/2010/11/linux-to-get-a-lot-faster-due-to-new-patch/)
I'm a noob in computers, especially in Ubuntu since I just recently acquired it so I'm asking the lamest question out there: how do I download this patch, apply it and make it working? Is it worth it? And if not then what other suggestions can you give me?
answer in any way possible but please take note that I'm a beginner and I won't understand *difficult* terms like *compile the source code in terminal* or *add the following lines in the kernel* or something like that
PLS, help!!!!

---

### Post by Manyette on 2010-11-30
No expert here, just one man's opinion, okay.  If this patch is as good as claimed, it will eventually appear in the kernel.  I see no guarantee that it will even work with the current kernel, depending on what version you are currently running.  I personally would not do it until the developers approve it, by including it in a release.

---

### Post by uRock on 2010-11-30
Welcome to the forums. 

There have been two kernel updates since that blog was posted, so chances are that they have already included the patch.

Regards,
uRock

---

### Post by Manyette on 2010-11-30
I seriously doubt it, since I see no change in speed whatsoever, and the website claims it won't be integrated until a 10.10 kernel.  Since I'm staying with 10.04, I'm  disappointed, but that's what is said, anyway.

---

### Post by uRock on 2010-11-30
I haven't had any problems with system speed. The article doesn't say when it will be implemented or to what kernel version.

---

### Post by Joe of loath on 2010-11-30
It's probably currently in a development version of the kernel, I don't know if it'll be backported or not, but probably not.

---

### Post by Manyette on 2010-11-30
Hi URock, it did earlier, and the kernel version in which it was to be implemented ended in ".36".  don't remember what the rest of it was, but it was a kernel that had to be on 10.10, since they never (or at least rarely) implement such fixes on an earlier kernel for fear of breaking something else.  Also wonder why they suddenly changed the page.  It was there just a few hours ago.  Maybe it's just my naturally suspicious nature, but it seems strange.

---

### Post by NightwishFan on 2010-11-30
If you guys are referring to the dubbed "magic (or miracle)" patch. No it is not worth going out of the way for. It is designed to group tasks by terminal to improve interactivity at the cost of performance. For normal desktop apps I do not even think are affected by this. (Unless of course you are running a heavy process in the terminal).

I believe it is slated to be included in 2.6.38 which should be the default kernel in Natty.

---

### Post by Manyette on 2010-11-30
Interesting, it is now back on the page.  Here is the qute. #


you can either compile the kernel from git yourself, wait for the kernel 2.6.38 to be released, wait for the ubuntu kernel team to make a deb for you, or wait to natty

Not sure I know what "git" or "natty" is, but this is what was on the page.

---

### Post by pricetech on 2010-11-30
Natty Narwhal, the next release of Ubuntu, now in testing.

---

### Post by uRock on 2010-11-30
> **Manyette said:**
> Interesting, it is now back on the page.  Here is the qute. #


you can either compile the kernel from git yourself, wait for the kernel 2.6.38 to be released, wait for the ubuntu kernel team to make a deb for you, or wait to natty

Not sure I know what "git" or "natty" is, but this is what was on the page.

Natty is part of the nick name for 11.04. You aren't referring to the article, but a comment below it.:neutral:

@NightwishFan That is good to info. I figured it would be something that doesn't help the average desktop user. Though it may be useful to power users who do a lot of CLI based work.

---

### Post by NightwishFan on 2010-11-30
Yes, as I said this patch is nothing bad, just not anything to go out of your way to pursue. The advice to wait for it to be merged and included in the Ubuntu kernel is solid.

---

### Post by TenPlus1 on 2010-11-30
Phoronix recently published an article regarding a ~200 lines Linux Kernel patch that improves responsiveness under system strain. Well, Lennart Poettering, a RedHat developer replied to Linus Torvalds on a maling list with an alternative to this patch that does the same thing yet all you have to do is run 2 commands and paste 4 lines in your ~/.bashrc file. I know it sounds unbelievable, but apparently someone even ran some tests which prove that Lennart's solution works. Read on!

Basically, Lennart explains you have to add this to your ~/.bashrc file (important: this won't work on Ubuntu. See instructions for Ubuntu further down the post!):

   if [ "$PS1" ] ; then  
           mkdir -m 0700 /sys/fs/cgroup/cpu/user/$$
           echo $$ > /sys/fs/cgroup/cpu/user/$$/tasks
   fi

And run the following commands as super user:

mount -t cgroup cgroup /sys/fs/cgroup/cpu -o cpu
mkdir -m 0777 /sys/fs/cgroup/cpu/user

Further more, a reply to Lennart's email states that his approach is actually better then the actual Kernel patch:


--- UBUNTU INSTRUCTIONS HERE ---


Start by editing your rc.local file, running sudo gedit /etc/rc.local and add the following lines above "exit 0":

mkdir -p /dev/cgroup/cpu
mount -t cgroup cgroup /dev/cgroup/cpu -o cpu
mkdir -m 0777 /dev/cgroup/cpu/user
echo "/usr/local/sbin/cgroup_clean" > /dev/cgroup/cpu/release_agent

Save and exit gedit. Now, make it executable:

sudo chmod +x /etc/rc.local

After doing this, edit the .bashrc file found in your home directory (gedit ~/.bashrc) and, at the end of this file, add:

if [ "$PS1" ] ; then  
   mkdir -m 0700 /dev/cgroup/cpu/user/$$
   echo $$ > /dev/cgroup/cpu/user/$$/tasks
   echo "1" > /dev/cgroup/cpu/user/$$/notify_on_release
fi

One last thing. To make sure that cgroups are deleted whenever the last task leaves, run:

sudo gedit /usr/local/sbin/cgroup_clean

And copy-paste this:

#!/bin/sh
rmdir /dev/cgroup/cpu/$*

Once again, save the file, exit gedit and make it executable:

sudo chmod +x /usr/local/sbin/cgroup_clean

Done! Restart your computer to apply the changes.

---

