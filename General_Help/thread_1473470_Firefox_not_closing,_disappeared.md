---
title: "Firefox not closing, disappeared"
date: 2010-05-05
forum: General Help
---

### Post by lakelovers on 2010-05-05
I'm running 10.04, and Firefox disappeared from the screen and when I try to start it, I get the message

>   Firefox is already running, but is not responding. To open a new window, you must first close the existing Firefox process, or restart your system.

This happened after I tried to restore the bookmarks from my backup drive. How do I close firefox when no firefox is showing?

---

### Post by Detonate on 2010-05-05
Quick way. Go to System>Administration>System Monitor.  Click on the Processes tab.  Find firefox in the list and click the "End Process" button.

---

### Post by warfacegod on 2010-05-05
Detonate's suggestion is valid. However, I've often seen Firefox totally ignore the End Proccess command. If this happens to you, right click the Firefox process (which should be called firefox-bin) and select Kill Process.

---

### Post by warfacegod on 2010-05-05
You may find this useful: [http://ubuntuforums.org/showthread.php?t=1193567]("http://ubuntuforums.org/showthread.php?t=1193567")

---

### Post by lakelovers on 2010-05-05
I've tried your suggestions. So far nothing has worked. I reinstalled firefox but I still get the same measage. I'm thinking that the profile in my file system is corrupt. I should probably delete that file then remove firefox completely and reinstall it. I'll try that in a bit.

---

### Post by lovinglinux on 2010-05-05
> **lakelovers said:**
> I've tried your suggestions. So far nothing has worked. I reinstalled firefox but I still get the same measage. I'm thinking that the profile in my file system is corrupt. I should probably delete that file then remove firefox completely and reinstall it. I'll try that in a bit.

Don't delete your entire profile. Since the problem started when you tried to restore your bookmarks, then move the file places.sqlite from FF profile folder and start Firefox. This should fi the problem, but you will need to restore the bookmarks again.

---

### Post by Detonate on 2010-05-05
Try one more thing before doing all that.  In System Monitor note the pid of any running firefox.

Then open a terminal and enter "sudo kill (the pid here)" without the parenthesis.  If there is more than one pid, you can enter both, with a space between them.  We'll try to kill it with root privileges.

---

### Post by whiskeylover on 2010-05-05
Or just type "killall firefox"

---

### Post by lakelovers on 2010-05-05
Still no luck. I tried "killall firefox," and got the message "not process found." I've looked at the listings in the system monitor several times and can find no firebox. Could it be under any other name?

---

### Post by warfacegod on 2010-05-05
Are you using Swiftfox?

---

### Post by lovinglinux on 2010-05-05
What you need is **killall firefox-bin**

---

### Post by lakelovers on 2010-05-05
I'm using Firefox 3.6.3+nobinonly-outbundu4. I believe that's the one that came with 10.04. I have no idea what the stuff is that comes after the "3.6.3"

---

### Post by lakelovers on 2010-05-05
I tried "killall firefox-bin" and I get "no process found."

---

### Post by lovinglinux on 2010-05-05
> **lakelovers said:**
> I tried "killall firefox-bin" and I get "no process found."

Open a terminal and run this

```
firefox -no-remote -P
```

This should open the profile manager, even  with Firefox already opened or give you some errors.

Create a new profile from the profile manager and start it. See if it launches. Then try do do the same with your default profile. If it doesn't work, then move the file **places.sqlite** from the default profile folder to somewhere you can recover it later, then start Firefox using the default profile.

---

### Post by lakelovers on 2010-05-05
I created a new profile per your instructions and Firefox loaded just fine. However, I can't find "places.sqlite." It doesn't show anyplace in my file system. What do you suggest?

---

### Post by lovinglinux on 2010-05-05
> **lakelovers said:**
> I created a new profile per your instructions and Firefox loaded just fine. However, I can't find "places.sqlite." It doesn't show anyplace in my file system. What do you suggest?

go to your home folder, hit CTRL+H to see the hidden files and folders, then open ~/.mozilla/firefox and find the default profile folder. Open it and you should find a places.sqlite file.

---

### Post by lakelovers on 2010-05-05
Okay, thanks. I moved places.sqlite then tried the default profile. It didn't work. I got this: 

> Firefox cannot use the profile "default" because it is in use.
To continue, close the running instance of Firefox or choose a different profil.

There is a second places.sqlite that has zero content. I'm thinking that I sould move that too and see what happens.

---

### Post by lovinglinux on 2010-05-05
> **lakelovers said:**
> Okay, thanks. I moved places.sqlite then tried the default profile. It didn't work. I got this: 

.

There is a second places.sqlite that has zero content. I'm thinking that I sould move that too and see what happens.

Close Firefox before moving any files, then run **killall firefox-bin** then start it again.

---

### Post by lakelovers on 2010-05-05
I closed firefox and ran "killall firefox-bin" and got the message "no process found."
When I moved places.sqlite, I believe I had firefox open. Should I keep firefox closed and move it back. Obviously, I way over my head, but I would sure like to get this thing fixed.

---

### Post by lovinglinux on 2010-05-06
> **lakelovers said:**
> I closed firefox and ran "killall firefox-bin" and got the message "no process found."
When I moved places.sqlite, I believe I had firefox open. Should I keep firefox closed and move it back. Obviously, I way over my head, but I would sure like to get this thing fixed.

If you still have the problem, then I would recommend using the new profile. Something other than places.sqlite in your default profile is causing the problem. If you want to restore some settings and data from the old profile, then see [http://kb.mozillazine.org/Profile_folder_-_Firefox#Files](http://kb.mozillazine.org/Profile_folder_-_Firefox#Files)

---

### Post by lakelovers on 2010-05-06
Thanks for all your help. I think I'll stick with the new profile. I'm afraid if I try to recover elements of the old profile I screw something up.

**Edit: I reinstalled 10.04, fresh. Fixed everything.**

---

