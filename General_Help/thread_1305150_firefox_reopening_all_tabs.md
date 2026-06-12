---
title: "firefox reopening all tabs"
date: 2009-10-29
forum: General Help
---

### Post by sandyd on 2009-10-29
CUrrently, firefox is reopening alll my last tabs each time i shut down the computer and restart. 

im using "start a new session"
and ive already set firefox to load my homepage at its startup.

help?

---

### Post by sandyd on 2009-10-31
bump

---

### Post by scouser73 on 2009-10-31
You could try creating a new profile: > **firefox -no-remote -P**

A small dialog will appear with options to create a new profile, rename or delete existing profiles, and start Firefox with the selected profile. You also have the option to tell the profile manager whether or not it should ask what profile you want when Firefox is loaded. If you have this box checked, Firefox will automatically load the last profile you used. If it is not checked, you will always be asked which profile you want.

Click the “Create Profile…” button, read the information about profiles, click Next, give the profile a name and click Finish.

Now you have your new profile listed on the Profile Manager. Select it and click “Start Firefox”. When it loads, you’ll be greeted with Firefox as it looked when it was first installed.

---

### Post by ikisham on 2009-10-31
If you shutdown you computer with FF open, it will open the same tabs the next time you open it.
Solution in this case is close FF before shutting down.

---

### Post by sandyd on 2009-11-01
> **ikisham said:**
> If you shutdown you computer with FF open, it will open the same tabs the next time you open it.
Solution in this case is close FF before shutting down.
ah. thats it.
i **might** consider making myself a logoff script that shuts down firefox gracefully instead of killing the process.


any ideas on that?

---

