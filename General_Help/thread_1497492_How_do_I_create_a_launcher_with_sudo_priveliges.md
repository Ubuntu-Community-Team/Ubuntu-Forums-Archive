---
title: "How do I create a launcher with sudo priveliges?"
date: 2010-05-30
forum: General Help
---

### Post by davidov009 on 2010-05-30
I am wondering how to create a launcher with 2 functions in Ubuntu 10.04. The functions I want are both in terminal, and I want them executed in this order:
# sync
# echo 3 > /proc/sys/vm/drop_caches
The echo 3 command requires root privileges to run, and I haven't figured out how to do that yet.
I am brand new in ubuntu, and have only been using it for about 2 weeks.
The reason behind this is that I want a launcher in the bar at the top of the screen that I can click periodically to dump my ram cache, since I have 4 gb of ram, and do not see the point of using 100 percent of that when just sitting on the desktop.

---

### Post by arrange on 2010-05-30
Please don't get offended, I'm just asking out of curiosity - why do you need to do this? If you have too much RAM, wouldn'i it be easier to take one RAM stick out instead? The cache is dropped automatically when memory is needed.

---

### Post by kerry_s on 2010-05-30
i agree, cache is for performance. your basically just making your system work harder.

anyways you would add "echo" to the nopasswd in sudoers.

in terminal-> **sudo visudo**
on the bottom put:
```
your-name ALL=NOPASSWD: /bin/echo
```


i would suggest you leave it alone, add the monitor applet if you want to keep a eye on it. it will tell you whats in use & cache.

i have 1gb ram & see mine go up & down through out the day.

---

### Post by sdennie on 2010-05-30
You probably don't want to make this launcher because, as stated above, having things in the cache is probably the single biggest speed improvement available on your machine.  Essentially, the cache is there to hide the fact that your disks are very slow but, is easily evicted from memory if applications need it.

---

### Post by trikster_x on 2010-05-30
The best thing to do would be to create a shell script and place it in your home folder under the name "something.sh" or similar so you can just open a terminal and type
```
./something.sh
```
It will not exempt you from entering a password, but it also leaves the security of the echo command in place.

This would be the basic shell script, just create a text file, name it "something.sh"
```
#!/bin/bash
sync
sudo echo 3 > /proc/sys/vm/drop_caches

```

Then go to properties and under "permissions", check the "Allow executing file as program" box, or type into the terminal:
```
 chmod 777 ./NameOfScript.sh

```

As anyone will tell you, there is a reason for certain commands to require sudo privileges, generally because you are attempting to manipulate files or programs at a root level.  Adding any command to a sudoers NOPASSWD list is almost always a bad idea, since running that command will no longer require your password whatsoever.

---

### Post by formaldehyde_spoon on 2010-05-30
+1 to the "This is a strange thing to want to do" crowd.

---

### Post by davidov009 on 2010-05-31
I found a way to do this.
Create a script with the following:
```
#!/bin/sh
 sync
 echo 3 | sudo tee -a /proc/sys/vm/drop_caches
```Place the script in the /usr/local/bin folder, and create a launcher to that script.
My reasoning behind this:
I just got came off of the Windows boat, and, what I'm used to is using as little ram as possible. Microsoft calls this &quot;Room to Zoom&quot;. The excess use of ram, to me, looks bad. So, every now and then, I wanted to clear the cache to free up all kinds of space.
This thread has been solved.

---

### Post by davidov009 on 2010-05-31
It's not the fact that I have too much physical ram. It's just that all of that ram was being used, 90 percent by the cache, and only 10 percent by the programs. I just want to dump the cache to free up what I like to call the "unused" ram, even though it is used by the cache, and I understand that the cache will be dumped when ram is required, but I come from a windows platform, and I am used to using as little ram as possible to get the job done.

---

### Post by finlost on 2010-05-31
You are going to find that Ubuntu runs a whole lot lighter than Windows.

---

### Post by formaldehyde_spoon on 2010-05-31
> **davidov009 said:**
> It's not the fact that I have too much physical ram. It's just that all of that ram was being used, 90 percent by the cache, and only 10 percent by the programs. I just want to dump the cache to free up what I like to call the &quot;unused&quot; ram, even though it is used by the cache, and I understand that the cache will be dumped when ram is required, but I come from a windows platform, and I am used to using as little ram as possible to get the job done.

Just as long as you realize that you will be degrading performance instead of improving it...

---

### Post by sdennie on 2010-05-31
> **davidov009 said:**
> It's not the fact that I have too much physical ram. It's just that all of that ram was being used, 90 percent by the cache, and only 10 percent by the programs. I just want to dump the cache to free up what I like to call the "unused" ram, even though it is used by the cache, and I understand that the cache will be dumped when ram is required, but I come from a windows platform, and I am used to using as little ram as possible to get the job done.

This is a poor mindset to come into for a new Linux user.  The black magic you have used in the past for Windows is no longer valid here.  However, do not despair; We have a whole other set of black magic.  And we are more than happy to teach it to you.

Lesson 1:

Don't drop the cache

---

