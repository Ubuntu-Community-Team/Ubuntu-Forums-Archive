---
title: "Firefox 3.5 launcher issues"
date: 2009-11-08
forum: General Help
---

### Post by sports fan Matt on 2009-11-08
How can I get the original FF 3.5 Launcher? This one is not it and looking in edit menus/properties it is not there.

---

### Post by 101011010010 on 2009-11-08
Hello there.
Try Applications>Internet, then right click on the Firefox option and select add to panel.
I hope this helps.

---

### Post by scouser73 on 2009-11-08
> **sox fan Matt said:**
> How can I get the original FF 3.5 Launcher? This one is not it and looking in edit menus/properties it is not there.

Hi Matt, you can get the firefox png by Googling, but I've save you the trouble and found one for you.  Don't worry about the initial size of it, as it appears in the menu as it would normally.

[http://www.apfelnews.eu/wp-content/uploads/2008/12/firefox.png](http://www.apfelnews.eu/wp-content/uploads/2008/12/firefox.png)

All you need to do, is copy that to your hard drive then right click on the Ubuntu start icon, select Edit Menus, then go to Internet, select Firefox click Properties and then choose the icon that you've downloaded.

---

### Post by sports fan Matt on 2009-11-08
Thanks for the icon scuouser:)

However it fails to launch with "Failed to execute child process "firefox&u" (No such file or directory)"

Any ideas?

---

### Post by scouser73 on 2009-11-08
Ahh right I see, sorry lol.  Did you manually install Firefox?

---

### Post by peculiar penguin on 2009-11-08
You're missing the space between "firefox" and the parameter "%u".

You should be able to drag and drop the launcher from the Applications menu to make a copy.

---

### Post by scouser73 on 2009-11-08
Mat, follow these instructions.  It does mean that you'll be installing Firefox but my instructions are straightforward.

[[COLOR="Red"]**Download Firefox**[/COLOR]]("http://www.mozilla-europe.org/en/firefox/")

**1** - Right click & Extract the Firefox tar.bz2

**2** - Enter **gksudo nautilus** in Terminal

**3** - Copy & paste the Firefox file that you have just extracted to **/opt**

**4** - Right click on the Ubuntu start logo, select **Edit Menus**, 

**5** - Highlight the Internet sub menu & click New Item

You will now see a small dialogue box appear

**6** - In the Name field, type **Firefox**

**7** - In the Command field type **/opt/firefox/firefox**

**8** - In the Comment field type **Firefox**

You will now have firefox installed.

---

### Post by sports fan Matt on 2009-11-08
I had originally installed it through ubuntuzilla (which in turn gave me the shiretoko version at 1st, then i stupidly un installed that icon hence where I am at present)

---

### Post by sports fan Matt on 2009-11-08
I have it installed..It just won't seem to run.  I had tried those instructions and didn't seem to work.  (Couldnt get the right file permissions to extract to opt even with gksudo nautilus) In time, I will investigate but now I can spend no more time working on it. If anyone has any more ideas I will check them later..thanks for the help so far! :)

---

### Post by scouser73 on 2009-11-08
> **sox fan Matt said:**
> I have it installed..It just won't seem to run.  I had tried those instructions and didn't seem to work.  (Couldnt get the right file permissions to extract to opt even with gksudo nautilus) In time, I will investigate but now I can spend no more time working on it. If anyone has any more ideas I will check them later..thanks for the help so far! :)

**1** - Go to **Terminal**, copy & paste this command: **gksudo nautilus** that will open Terminal as root

**2** - Navigate to your new drive, **Right Click**, select the **Permissions** tab 

**3** - Change the **Owner** drop-down menu to your name, then change **Folder Access** to **Create & Delete Files**, then **File Access** to **Read & Write**, then **Group** to your name, **Folder Access** to **Create & Delete Files**, **File Access** to **Read & Write** then click **Apply Permissions To Enclosed Files**.

You will now have full access to your drive/folder/file.

---

### Post by sports fan Matt on 2009-11-09
Sorry I didnt get back to this sooner but all is well.  Firefox is installed and running normally.

---

