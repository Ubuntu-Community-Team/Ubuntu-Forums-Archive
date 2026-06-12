---
title: "firefox location and update  urgent"
date: 2011-07-29
forum: General Help
---

### Post by choochoousmc on 2011-07-29
I really need some help now.
Firefox auto update keeps failing    so...
I need help locating the original installation location.

I tried downloading the update  and using archive manager to open rather than save, but still it wanted to save.  Now I can't find the location it selected.


I want to locate the downloaded saved and delete the new files, to conserve space.

And I need to learn how to force an Automatic update.

I found a folder named firefox   and another firefox 3.0   System will not let me delete / move to trash.

I want to update to latest version.   Don't want to remove the original and lose all my bookmarks

So need some help.     Thanks

---

### Post by lovinglinux on 2011-07-29
> **choochoousmc said:**
> I really need some help now.
Firefox auto update keeps failing    so...

The built-in Firefox updater is disabled by default. You should update Firefox using the the system Update Manager.

> **choochoousmc said:**
> I need help locating the original installation location.

I tried downloading the update  and using archive manager to open rather than save, but still it wanted to save.  Now I can't find the location it selected.

I want to locate the downloaded saved and delete the new files, to conserve space.

Well, if simply downloaded the file and used the archive manager without any special command, then most likely the extracted files are in your home folder somewhere. 

> **choochoousmc said:**
> 
And I need to learn how to force an Automatic update.

Updates are provided by Ubuntu via Update Manager and are installed from a central repository. Usually, you don't go fishing new versions on the Internet. However, Ubuntu has a policy of providing only security and stability patches for the applications. If you are looking for Firefox 5 and if you are not using the latest Ubuntu version, the see [Firefox 4, 5 & Beyond Mega Thread]("http://ubuntuforums.org/showthread.php?t=1712247")

> **choochoousmc said:**
> 
I found a folder named firefox   and another firefox 3.0   System will not let me delete / move to trash.

You should not delete files on your system folders unless you really know what you are doing.

> **choochoousmc said:**
> 
I want to update to latest version.   Don't want to remove the original and lose all my bookmarks

Firefox bookmarks and settings are not stored in the system folders. They are kept separate in your home directory, under an user profile folder. So it doesn't matter which version of Firefox you use, you will always have your personal Firefox data intact.

---

### Post by choochoousmc on 2011-07-30
Thanks to everybody.
I went back and clicked download again, to finf where they are going.
The D/L  location bar  is a picture of a folder and a single  /
I have looked all through my home folder and no firefox.
I did find two folder on system       firefox  and fire fox 3.0
But they do not contain all the files listed in the D/L  location bar.
Plus I cannot delete the firefox & firefox 3.0 folders to start new.
If I use remove option in the repository I lose all my bookmarks, and haven't found a way to export or save them.

I have 11.04, can't find the system update, where is it located?

Thanks

---

### Post by lovinglinux on 2011-07-30
> **choochoousmc said:**
> Thanks to everybody.
I went back and clicked download again, to finf where they are going.
The D/L  location bar  is a picture of a folder and a single  /
I have looked all through my home folder and no firefox.
I did find two folder on system       firefox  and fire fox 3.0
But they do not contain all the files listed in the D/L  location bar.

I could guide you trough the menus, but it is simpler to run a few commands in a terminal. To open a terminal, click the *Applications* button in the left dock (the search lens with a plus sign), then type *Terminal* in the search field, then click the Terminal launcher in the results.

As I said earlier, unless you used a special command, the archive manager wouldn't save your files outside your home.

If you haven't extracted the downloaded file, then you can find it with this terminal command:

```
find $HOME -name 'firefox*tar.bz2'
```

If you have indeed extracted it, then use this instead:

```
sudo find / -name 'firefox-bin'
```

> **choochoousmc said:**
> 
Plus I cannot delete the firefox & firefox 3.0 folders to start new.

As I wrote in my previous reply, DO NOT mess with system folders. Deleting applications folders from your system directory won't uninstall the application and will cause problems.

> **choochoousmc said:**
> 
If I use remove option in the repository I lose all my bookmarks, and haven't found a way to export or save them.

As I mentioned in my previous post, you do not loose your bookmarks if you remove Firefox. They are stored on a separate folder in your home.

To export your bookmarks see [http://www.webgapps.org/tutorials/firefox/general/profiles-and-backups](http://www.webgapps.org/tutorials/firefox/general/profiles-and-backups)

> **choochoousmc said:**
> I have 11.04, can't find the system update, where is it located?

To update Firefox, copy each command below to the Terminal window and hit *Enter*. Your password will be requested and you won't be able to see it while you type. This is normal. Just type the password and hit *Enter* again:

```
sudo apt-get remove firefox
sudo apt-get remove firefox-3.0
sudo apt-get update
sudo apt-get install firefox
```

---

### Post by choochoousmc on 2011-07-31
Thanks for the tutorial, I will try it later this week as soon as I get time.
I have not extracted the files, as the extract failed. That's why I wanted to delete the .tar file and start again.
But I got to find it first.

---

### Post by lovinglinux on 2011-07-31
> **choochoousmc said:**
> Thanks for the tutorial, I will try it later this week as soon as I get time.
I have not extracted the files, as the extract failed. That's why I wanted to delete the .tar file and start again.
But I got to find it first.

By default, Firefox saves downloaded files in the Download folder. However, the first command I gave you will find it if it was saved elsewhere.

---

### Post by choochoousmc on 2011-08-06
[SIZE=3]Thanks for the help. I ran each of the commands.
The first to find the firfox*tar.bz2  came back as no such file or directory.
The others worked.
I shut down firefox, but not the computer[/SIZE].
[SIZE=3]It is now 3.6.18  still not the newest.
So I will restart the computer and see what happens.
When I am successful I may have to find this page again.


[/SIZE]

---

### Post by lovinglinux on 2011-08-06
Please attach the firefox-report.txt file generated in your desktop after running the commands below:

```

echo 'Ubuntu Architecture' > ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
uname -a >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Ubuntu Version' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
cat /etc/lsb-release >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox Packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'firefox*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox binaries' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
which firefox >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox >> ~/Desktop/firefox-report.txt
file /usr/local/bin/firefox >> ~/Desktop/firefox-report.txt
file /opt/firefox/firefox >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox divertion' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox.ubuntu >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Sources' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
ls /etc/apt/sources.list.d >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
firefox ~/Desktop/firefox-report.txt
```

---

### Post by choochoousmc on 2011-08-06
[SIZE=3]I already closed the window and I rebooted.
I  followed your previous commands and it did remove and
and reinstall Firefox. But it only did 3.6.18
If we have a further issue to explore, I will rerun the terminal commands you gave and then post them here.  TIA

Checking the web I see Firefox 5.0.1listed for linux i686.
So I used Ubuntu software center to remove firefox. rebooted to be on safe side. and reinstalled from there. but it still only installed 3.6.18.
Why is the installation so many versions behind?
Using system search I found most all files named firefox. But either move to trash is grayed out, or the delete function says I don't have permission to delete.. I followed commands several months ago to be SUDO  but not sure if I actually am.[/SIZE] 
[SIZE=3]Thanks for the help so far.[/SIZE]

---

### Post by lovinglinux on 2011-08-06
> **choochoousmc said:**
> [SIZE=3]I already closed the window and I rebooted.
I  followed your previous commands and it did remove and
and reinstall Firefox. But it only did 3.6.18
If we have a further issue to explore, I will rerun the terminal commands you gave and then post them here.  TIA

Checking the web I see Firefox 5.0.1listed for linux i686.
So I used Ubuntu software center to remove firefox. rebooted to be on safe side. and reinstalled from there. but it still only installed 3.6.18.
Why is the installation so many versions behind?
Using system search I found most all files named firefox. But either move to trash is grayed out, or the delete function says I don't have permission to delete.. I followed commands several months ago to be SUDO  but not sure if I actually am.[/SIZE] 
[SIZE=3]Thanks for the help so far.[/SIZE]

Please run the commands, so I can find the source of the problem.

---

