---
title: "Random crash reports?"
date: 2012-07-08
forum: General Help
---

### Post by Divisi on 2012-07-08
I keep getting these random crash reports for blueman, which from what I've looked up is a bluetooth application?  I can't get it to stop though.
I also actually JUST got a crash report for tumblerd, which I took a screenshot of.

Thanks!  ):P

---

### Post by ronnysingh on 2012-07-09
I used to get some crash reports after upgrading to 12.04. Those reports always started with '*Sorry*, *Ubuntu 12.04 has suffered an internal program error* '. This particular  version of Ubuntu has 'apport' which reports such crashes. Some people change parameter of apport by using terminal and thus get rid of reports. However, I have not been getting those reports after a few days of upgradation even though I did nothing with apport.

---

### Post by Divisi on 2012-07-09
I haven't done anything with them either, but they seem to pop up at least once when I start it up.

---

### Post by cbraxton on 2012-07-10
I've been getting a lot of tumblerd crashes also in Xubuntu 12.04 64-bit. Did some web searches and it turns out there are a lot of problems being reported with the program, it crashes frequently and sometimes uses up lots of CPU and memory. It's function seems to be to generate the thumbnail images you see in Thunar when viewing directory contents.

I was unable to find an 'official' way to disable this program but found that the executable is /usr/lib/x86_64-linux-gnu/tumbler-1/tumblerd. (Probably different on 32-bit Xubuntu, use the "find" command.) Renaming this file prevents it from launching. No side effects yet aside from thumbnails not being generated. FWIW.

```

$ sudo bash
# find /usr -name tumblerd
/usr/lib/x86_64-linux-gnu/tumbler-1/tumblerd

# cd /usr/lib/x86_64-linux-gnu/tumbler-1/
# mv tumblerd tumblerd.DISABLED
# exit

```

---

### Post by Divisi on 2012-07-10
> **cbraxton said:**
> I've been getting a lot of tumblerd crashes also in Xubuntu 12.04 64-bit. Did some web searches and it turns out there are a lot of problems being reported with the program, it crashes frequently and sometimes uses up lots of CPU and memory. It's function seems to be to generate the thumbnail images you see in Thunar when viewing directory contents.

I was unable to find an 'official' way to disable this program but found that the executable is /usr/lib/x86_64-linux-gnu/tumbler-1/tumblerd. (Probably different on 32-bit Xubuntu, use the "find" command.) Renaming this file prevents it from launching. No side effects yet aside from thumbnails not being generated. FWIW.

```

$ sudo bash
# find /usr -name tumblerd
/usr/lib/x86_64-linux-gnu/tumbler-1/tumblerd

# cd /usr/lib/x86_64-linux-gnu/tumbler-1/
# mv tumblerd tumblerd.DISABLED
# exit

```

Thanks!  Didn't run into any problems, now I'll just wait and see if it pops up again.

Do you know anything about the blueman crash?  Because I don't have a bluetooth device on my net book, but for some reason there is a bluetooth symbol in my bar right now?

---

### Post by cbraxton on 2012-07-10
I don't have bluetooth so have not really played around with that. I think the bluetooth manager launches from "Startup Applications" so you should be able to disable it there.

Also if tumblerd is updated of course a new executable will be put in place and it would start firing up again. Maybe at that point some of the bugs will have been fixed, if not just rename it again. :-)

---

### Post by Divisi on 2012-07-10
> **cbraxton said:**
> I don't have bluetooth so have not really played around with that. I think the bluetooth manager launches from "Startup Applications" so you should be able to disable it there.

Also if tumblerd is updated of course a new executable will be put in place and it would start firing up again. Maybe at that point some of the bugs will have been fixed, if not just rename it again. :-)

I've never messed with startup applications so I didn't even think of that! :lolflag:
Thanks!

---

