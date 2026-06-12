---
title: "Thunderbird on Ubuntu and Windows"
date: 2010-02-07
forum: General Help
---

### Post by eewoz on 2010-02-07
I have Ubuntu and Windows on the same machine.  If I install Thunderbird on both operating systems is it possible that both installs can access the same email files so that all of my emails will be in one file no matter which operating system was running when emails are downloaded or sent?

Thanks.

---

### Post by howefield on 2010-02-07
If you have an email account in your Windows Thunderbird, load Thunderbird and select Tools > Account Settings, then click on Local Folders, on the right side you should see the current location of the email files under Local Directory. Write it down so that you have it for Ubuntu.

Now boot Ubuntu, open Thunderbird, select Tools > Account Settings, click the Local Folders tab, then use the Browse button to navigate to the same folder that is used in Windows.

---

### Post by eewoz on 2010-02-08
> **howefield said:**
> If you have an email account in your Windows Thunderbird, load Thunderbird and select Tools > Account Settings, then click on Local Folders, on the right side you should see the current location of the email files under Local Directory. Write it down so that you have it for Ubuntu.

Now boot Ubuntu, open Thunderbird, select Tools > Account Settings, click the Local Folders tab, then use the Browse button to navigate to the same folder that is used in Windows.

I don't have Tools>Account Settings, but I am able to get to a window that allows me to specify the location of my local folder.  But when I try to specify the same folder that I use for Windows Thunderbird I get an error message saying ```
This directory is already used by another server.  Please pick another directory.
```Is there any way I can get around this issue?

Thanks.

---

### Post by abhishek.malhotra35 on 2010-02-08
In your account settings, click on local folders. you will see local directory. Change that directory path to one where you have windows local folder for thunderbird. Make sure that your email server local directory is not same as of the local one. Thunderbird will setup a local directory automatically for your server, which you can find in account setting-><your email>. There would be server setting which will have a local directory setted up for you.

---

### Post by eewoz on 2010-02-10
I got it working.  Thanks guys.

---

### Post by Nacht on 2010-02-14
> I am able to get to a window that allows me to specify the location of my local folder
How did you do this? I can't find it at all.

---

### Post by eewoz on 2010-02-14
> **Nacht said:**
> How did you do this? I can't find it at all.

I am using Thunderbird 3.  In that version select Tools > Account Settings.  In the left hand pane select Server Settings under the account that you are interested in.  In the right hand pane near the bottom you should see Local Directory and a text box that lets you specify a directory.

---

