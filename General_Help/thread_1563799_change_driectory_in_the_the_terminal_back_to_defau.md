---
title: "change driectory in the the terminal back to default"
date: 2010-08-29
forum: General Help
---

### Post by melinda on 2010-08-29
I was trying to install google earth.  This is what I did:

1. Open a terminal and change to the directory where the installer downloaded to. (on desktop) :

cd ~/Desktop

2. Change the permissions on the installer so you can run it:

chmod +x GoogleEarthLinux.bin

3. Run the installer as the root user:

sudo ./GoogleEarthLinux.bin

4. The installer dialog will open. The default install paths work fine. Click Begin Install.

Once the installation is finished you can click Start to launch Google Earth.


HOW DO I CHANGE BACK TO THE CORRECT DIRECTORY IN THE TERMINAL

AND WHY DOES GOOGLE EARTH JUST CLOSE AFTER THIS?

Thanks
Melinda

---

### Post by scorp123 on 2010-08-29
You could follow this guide:
[https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)

The advantage here would be that GoogleEarth too would auto-update whenever a new version hits the repositories ...

As for your actual question:

The command "**cd**" if entered without any parameter will automatically return you to your user's home directory. And "**pwd**" (short for "**[COLOR="Red"]p[/COLOR]**rint **[COLOR="Red"]w[/COLOR]**orking [COLOR="Red"]**d**[/COLOR]irectory") will show your current location (just in case the shell prompt won't show it). 

Example:
```
> cd /usr/share/man/
> ls -al
total 216
drwxr-xr-x    23 root  wheel     782 Jan 17  2010 .
drwxr-xr-x    57 root  wheel    1938 Aug 28 21:17 ..
drwxr-xr-x     3 root  wheel     102 Jul 14  2009 fr
drwxr-xr-x     3 root  wheel     102 Jul 14  2009 fr.ISO8859-1
drwxr-xr-x     3 root  wheel     102 Jul 14  2009 fr.UTF-8
drwxr-xr-x     3 root  wheel     102 Jul 14  2009 it
drwxr-xr-x     3 root  wheel     102 Jul 14  2009 it.ISO8859-1
drwxr-xr-x     3 root  wheel     102 Jul 14  2009 it.UTF-8
drwxr-xr-x  1500 root  wheel   51000 Aug 29 13:23 man1
drwxr-xr-x  6865 root  wheel  233410 Aug 28 21:17 man3
drwxr-xr-x    39 root  wheel    1326 Jan 17  2010 man4
drwxr-xr-x   193 root  wheel    6562 Aug 28 21:17 man5
drwxr-xr-x     3 root  wheel     102 May 18  2009 man6
drwxr-xr-x    56 root  wheel    1904 Mar 30 12:30 man7
drwxr-xr-x   454 root  wheel   15436 Aug 28 21:17 man8
drwxr-xr-x    23 root  wheel     782 Aug  1  2009 man9
drwxr-xr-x   605 root  wheel   20570 Jul 23  2009 mann
drwxr-xr-x     3 root  wheel     102 Jul 14  2009 pl
drwxr-xr-x     3 root  wheel     102 Jul 14  2009 pl.ISO8859-2
drwxr-xr-x     3 root  wheel     102 Jul 14  2009 pl.UTF-8
drwxr-xr-x     3 root  wheel     102 Jul 14  2009 ru.KOI8-R
drwxr-xr-x     3 root  wheel     102 Jul 14  2009 ru.UTF-8
-rw-r--r--     1 root  wheel  368312 Jan 17  2010 whatis

> pwd
/usr/share/man

> cd
> pwd
/home/myuser
```

If you happen to be logged in as "root" or some other account, then it might be that you end up in a different location. That's normal. In that case you will need to use the "**exit**" command to get out of that account and back into your normal account.

Example:

```
root# whoami
root

root# exit
logout

> whoami
myuser

```

---

### Post by melinda on 2010-08-29
Terminal says this:

robert@robert-desktop:~$


I thot I cd ~/Destop  and that is why it shows the "desktop:~$"

I did the "pwd" and it came back:
/home/robert
robert@robert-desktop:~$

Do I need to do an exit?  I did try to just "cd" or "cd ~"
and all that came up was the same 
robert@robert-desktop:~$

So is that my home directory (yes robert is the user)?  So confused.  Sorry.

Melinda

---

### Post by melinda on 2010-08-29
Scorp123 -- as far as Google Earth..  Well I guess after I installed the bin file....I clicked start.  According to your link I did the WRONG thing:

When installation is complete, press Quit.
/!\ Do not press Start as this will run it as root which is never a good idea. 

So how do I fix it?  I guess now when I try to run google earth I get this:

Google Earth could not write to the current cache or My Places file location. The values will be set as follows:
My Places Path: "/home/robert/.googleearth"
Cache Path: "/home/robert/.googleearth/Cache"

I click OK.  And then Google earth opens and shortly closes.

Help with that too?

Thanks
Melinda

---

### Post by melinda on 2010-08-29
so I uninstalled googleearth.  and then removed the user preferences folder because it contains Google Earth settings and cache.  

I reinstalled and did it correctly.  I still get that funky Alert re the cache preferences. and click ok and then it opens and closes.  Really bizarre.  

Anyone know what I am doing wrong-o?

Melinda

---

### Post by melinda on 2010-08-29
nevermind.  changing thread.  now having just google earth problems.

will start new thread.

---

