---
title: "Firefox not working when clicking"
date: 2010-08-21
forum: General Help
---

### Post by akumasaint on 2010-08-21
Hello again, let me get to the point...

I can't get Firefox to load up. I know what the problem is by reading this post

[http://ubuntuforums.org/showthread.php?t=828648](http://ubuntuforums.org/showthread.php?t=828648)

But I can't get it to go back to working by using the solution provided. I'm using Lucid Lynix by the way. Any help would be welcome.

---

### Post by lovinglinux on 2010-08-21
First make sure you don't have permission issues.  See the first item on [this list]("http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html").

Then kill any firefox process that might be running in the background with:

```
killall firefox-bin
```

Then go to your profile folder, which is located under **~/.mozilla/firefox/** and delete the files **compatibility.ini** and *secmod.db*. Start Firefox. 

If it works, then get [ProfileCleaner]("https://addons.mozilla.org/en-US/firefox/addon/213326/") extension and set it to delete those files every time Firefox closes.

If it doesn't help, then see Firefox [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) tutorial.

---

### Post by akumasaint on 2010-08-21
That's the thing, it is that. It says root has it. The other post says to do that but it doesn't work...

---

### Post by lovinglinux on 2010-08-22
> **akumasaint said:**
> That's the thing, it is that. It says root has it. The other post says to do that but it doesn't work...

Run the following command on a terminal, without changing anything:

```
sudo chown -R $USER:$USER ~/.mozilla
```

This should make you the owner of ~/.mozilla folder again and fix the issue.

---

### Post by akumasaint on 2010-08-22
> **lovinglinux said:**
> Run the following command on a terminal, without changing anything:

```
sudo chown -R $USER:$USER ~/.mozilla
```

This should make you the owner of ~/.mozilla folder again and fix the issue.

Still nothing

---

### Post by lovinglinux on 2010-08-22
Have you tried to start Firefox in safe mode or create a new profile as explained in my tutorial?

Please tell me what have you tried so far.

---

### Post by akumasaint on 2010-08-23
Okay, I got it work now. I try to start it in safe mode but that didn't work. I don't know if I read it in the tut but I deleted the ~.mozailla in the root AND in my folder. I then completely uninstall it then reinstall and it worked. 

Thank you:D

---

### Post by lovinglinux on 2010-08-23
> **akumasaint said:**
> Okay, I got it work now. I try to start it in safe mode but that didn't work. I don't know if I read it in the tut but I deleted the ~.mozailla in the root AND in my folder. I then completely uninstall it then reinstall and it worked. 

Thank you:D

You are welcome.

---

