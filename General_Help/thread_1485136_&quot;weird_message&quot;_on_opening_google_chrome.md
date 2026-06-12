---
title: "&quot;weird message&quot; on opening google chrome"
date: 2010-05-16
forum: General Help
---

### Post by shantiq on 2010-05-16
[INDENT][INDENT][B][COLOR="Blue"]this has been opening on my desktop for the last 2 days

not sure what it means


i took off chrome and reinstalled   still there

i do not understand what it means and what has changed to bring it on


any ideas?

[CENTER][IMG]http://img80.imageshack.us/img80/2566/screenshotnx.png[/IMG][/CENTER][/COLOR][/B][/INDENT][/INDENT]

---

### Post by robincawser on 2010-05-16
Is it to do with the google account Chrome is synced with for bookmarks etc?

---

### Post by robincawser on 2010-05-16
Oh, and also [http://www.google.co.uk/search?sourceid=chrome&client=ubuntu&channel=cs&ie=UTF-8&q=your+profile+could+not+be+opened+correctly]("http://www.google.co.uk/search?sourceid=chrome&client=ubuntu&channel=cs&ie=UTF-8&q=your+profile+could+not+be+opened+correctly")

---

### Post by shantiq on 2010-05-16
[INDENT][INDENT][INDENT][INDENT][B][COLOR="Blue"][B]thanx for the links robin this worked for me

from this post ===>[here]("http://saravananthirumuruganathan.wordpress.com/2010/05/10/how-to-solve-your-profile-could-not-be-opened-correctly-issue-in-chrome-or-chromium-without-losing-your-profile/#comment-176")


i used method 2 and it did not even knock off my history[/B][/COLOR][/INDENT][/INDENT][/INDENT][/INDENT]

[INDENT][INDENT][INDENT][INDENT]I use Google Chrome as my default browser. So when I started getting errors saying "Your profile could not be opened correctly" , it was quite annoying. I tried lot of fixes on my own and nothing seemed to work. I checked the forums and most of the solutions were to basically create a new profile which was not acceptable to me.


Method 1 : Check if there is any zombie processes[/B]

This is probably the most common scenario. If you get an error “Your profile could not be opened” , close all Chrome windows. Now check using ps if there is any chrome process still alive. A simple ps –aux | grep –i chrome or ps –aux | grep –i chromium should do.  If there is any processes still alive kill them (use kill, pkill or killall). Make sure all chrome processes are dead and start Chrome again. If the error does not come again, great ! Else follow the other steps.

If you are in Windows, then use the task explorer to kill all chrome processes.


**Method 2 : Removing Web Data file    [COLOR="Red"]worked for me!![/COLOR] **

Try this method first as this was the issue in my system. Google Chrome has a file called "Web Data" which stores lot of info in it – including your passwords (wink wink). In my case this file was corrupted. I deleted this file and all worked well.

If you are in Linux , you can find the "Web Data" file at ~/.config/google-chrome/Default (if you are using Chrome) or at ~/.config/chromium/Default (if you are using Chromium). If you are in Windows (atleast in Windows 7), the file is at C:\Users\<username>\AppData\Local\Google\Chrome\User Data\Default\ . Delete the file and restart Chrome. Hopefully everything should work well. Of course, you will lose all your stored passwords and the search engines.



[B]Method 3 : Check if any of the SQLite databases is locked
[/B]
Chrome uses SQLite to store lot of information. Some times, the database might be locked and Chrome might not be able to access it. In this case, follow Kyron’s script in this Chrome forum.

Basically what he does is this : he dumps the SQLite database data into an SQL file, deletes the database , recreates it using the SQL file. This script should work if you are in Linux. (I think it should work for Mac too). His script is written for Chromium. If you are using Google Chrome, change the folder ~/.config/chromium/Default/ to ~/.config/google-chrome/Default/ .



**Method 4 : Creating a new profile with most of the data from old profile**

This method is very similar to the previous methods where instead of removing "Web Data", it tries to create a new profile with most of the useful data from old profile copied in to it. The steps are :

    a) Rename the Default folder at ~/.config/google-chrome/Default or ~/.config/chromium/Default to say backup. For Windows, the folder is at C:\Users\<username>\AppData\Local\Google\Chrome\User Data\Default\
    b) create a new folder with name "Default"
    c) copy the files/folders given below from original Default folder (currently named as backup) to the new Default folder one by one . After each step, try opening Chrome to see if the error comes. If an error comes, then the latest object you copied caused the issue.

        Preferences file
        Bookmarks file
        Extensions folder (contains all your extension’s source code)
        Local Storage folder : copy only files beginning with "chrome-extension_"  (other files are most likely not needed )
        History* (all your history ) [/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by linfidel on 2010-06-27
> **shantiq said:**
> [INDENT][INDENT][INDENT][INDENT] **Method 4 : Creating a new profile with most of the data from old profile**

This method is very similar to the previous methods where instead of removing "Web Data", it tries to create a new profile with most of the useful data from old profile copied in to it. The steps are :

    a) Rename the Default folder at ~/.config/google-chrome/Default or ~/.config/chromium/Default to say backup. For Windows, the folder is at C:\Users\<username>\AppData\Local\Google\Chrome\User Data\Default\
    b) create a new folder with name "Default"
    c) copy the files/folders given below from original Default folder (currently named as backup) to the new Default folder one by one . After each step, try opening Chrome to see if the error comes. If an error comes, then the latest object you copied caused the issue.

        Preferences file
        Bookmarks file
        Extensions folder (contains all your extension’s source code)
        Local Storage folder : copy only files beginning with "chrome-extension_"  (other files are most likely not needed )
        History* (all your history ) [/INDENT][/INDENT][/INDENT][/INDENT]
I used method 4, and found that my history file was bad.  I then restored the original data, and tried opening history, which hung.  I then tried deleting history from within Chrome, and it hung or crashed.

So I deleted the History* files from the profile, and everything worked normally except, of course, I had no history.  All passwords, cookies, etc, were still fine.

---

