---
title: "Unable to install software with Software Center"
date: 2010-02-11
forum: General Help
---

### Post by virsto on 2010-02-11
I get a very strange behavior when I click on install for any package in the software center --- the popup window to authenticate appears for a few milliseconds, jitters horizontally, and then disappears. Thus, I am unable to authenticate any installation and of course installation is not possible.

I suspect that I have by mistake used **chown** or **chmod**  (or both) wrongly; but, I have no idea on how to fix this. :sad:

I was able to use Synaptic Package Manager to reinstall the software center; but this had no effect --- still can not install any package given in the software center!

I am a newbie to Ubuntu and would appreciate greatly help on how to return my system to normal!:?:

---

### Post by virsto on 2010-02-11
> **virsto said:**
> I get a very strange behavior when I click on install for any package in the software center --- the popup window to authenticate appears for a few milliseconds, jitters horizontally, and then disappears. Thus, I am unable to authenticate any installation and of course installation is not possible.

I suspect that I have by mistake used **chown** or **chmod**  (or both) wrongly; but, I have no idea on how to fix this. :sad:

I was able to use Synaptic Package Manager to reinstall the software center; but this had no effect --- still can not install any package given in the software center!

I am a newbie to Ubuntu and would appreciate greatly help on how to return my system to normal!:?:
Interestingly, when testing the installation of software packages in Ubuntu software center further, sometimes the popup for authentication is stable (does not disappear); but, no matter what button I push on (Cancel or Authenticate) nothing happens --- seems to freeze up.
 

Hope this is helpful for solving this problem.

---

### Post by Kevbert on 2010-02-11
Do you get problems with Applications-Accessories-Terminal ?
Please try the following (with an active internet connection) and post back any errors
```
sudo apt-get update
sudo apt-get install -f
sudo apt-get upgrade
```
The first command will update your software package list, the second will try to force a repair on any damaged packages and the third will upgrade the packages to the latest versions.
Are you using wireless ? If so, with an active connection please post the response to
```
iwconfig
```

---

### Post by virsto on 2010-02-11
> **Kevbert said:**
> Do you get problems with Applications-Accessories-Terminal ?
Please try the following (with an active internet connection) and post back any errors
```
sudo apt-get update
sudo apt-get install -f
sudo apt-get upgrade
```
The first command will update your software package list, the second will try to force a repair on any damaged packages and the third will upgrade the packages to the latest versions.
Are you using wireless ? If so, with an active connection please post the response to
```
iwconfig
```
1) I have no problems with the execution of Applications-Accessories-Termina

2) I executed all three of these commands and found no errors.

3) I have no problems with my wireless hardware/software --- I am sure of this.

4) I executed iwconfig and everything looked fine.

Again, I believe that it was my own stupidity in the use of some of the Unix/Linus commands that has caused this problem.

Thanks for your suggestions and help.

--V

---

### Post by virsto on 2010-02-11
I went back through my commands that were given in terminal yesterday and here are some that may have caused the problem:

chmod a+rw ~
chmod a+rw ~ -R
chgrp virgil  ~ -R
chgrp virgil /usr -R
chown virgil /usr -R

--V

---

### Post by labinnsw on 2010-06-17
[Step 1: See this post]("http://ubuntuforums.org/showpost.php?p=9248487&postcount=15")
Step 2: Change the launcher command to ```
gksu software-center
```

---

### Post by labinnsw on 2010-06-29
[CENTER][SIZE="5"]Unable to Authenticate[/SIZE][/CENTER]

Recently I have had an issue with various applications. Some that come readily to mind are Ubuntu Software Center, Screensaver Preferences, Ubuntu One and Network manager. The problem is that whenever I click on the Authenticate button at first nothing seems to happen. If I restart the application, when I should be taken to the Authenticate window, it shimmies then disappears or if it doesn't, when I click on the Authenticate button, it does the little shimmy and then disappears. I have found that a number of steps must be taken to correct the problem. (Wish I new how it developed in the first place.)

[1. Make sure the PolicyKit Authentication Agent is pointing to the right script.]("http://ubuntuforums.org/showpost.php?p=9248487&postcount=15")

Instead of the remaining steps, you could use the administrative command to launch the application. e.g. sudo application, gksu application, or gksudo application (Not sure when to use which, I find trial and error works without doing any harm.) I go through the remainder of the process because I want to maintain my normal user themes whenever possible.

2. Open the application in a terminal and attempt a task requiring Authentication.

3. Make a note of the terminal output. It should look something like this. 

WARNING:root:_on_trans_error: [COLOR="DarkGreen"]**org.freedesktop.PolicyKit.Error.NotAuthorized**[/COLOR]: ('system-bus-name', {'name': ':1.73'}) is not authorized: [COLOR="Blue"]**org.debian.apt.**[/COLOR]**[COLOR="Red"]install-packages[/COLOR]**
** Message: console message: undefined @1: ReferenceError: Can't find variable: showProgress

(If not, close the terminal and try again)

The bold green portion indicates that the problem lies in the policy kit. The bold blue and red portions point to the relevant policy kit. These are located at /usr/share/polkit-1/actions

4. Use your favourite editor to open /usr/share/polkit-1/actions/[COLOR="Blue"]the blue bold portion.policy[/COLOR] for editing in administrative mode. (e.g sudo gedit /usr/share/polkit-1/actions/org.debian.apt.policy)

5. Search for the bold red portion. (in this case &#8220;install-packages&#8221;)

6. Scroll to the end of the that block of code and look for &#8220;allow_active&#8221;
      <allow_any>auth_admin</allow_any>
      <allow_inactive>auth_admin</allow_inactive>
      <allow_active>auth_admin_keep</**allow_active**>

7. Change **auth_admin_keep** to **yes**.

8. Save and close


References
[http://ubuntuforums.org/showpost.php?p=9248487&postcount=15](http://ubuntuforums.org/showpost.php?p=9248487&postcount=15)
[http://ubuntuforums.org/showpost.php?p=8782060&postcount=14](http://ubuntuforums.org/showpost.php?p=8782060&postcount=14)
[http://ubuntuforums.org/showpost.php?p=9473710&postcount=6](http://ubuntuforums.org/showpost.php?p=9473710&postcount=6)[CENTER][/CENTER]

---

### Post by warfacegod on 2010-06-29
> **labinnsw said:**
> [Step 1: See this post]("http://ubuntuforums.org/showpost.php?p=9248487&postcount=15")
Step 2: Change the launcher command to ```
gksu software-center
```

I've always recommended this be:```
gksudo software-center
```

Don't know if it makes any difference though.

For those that don't know how to change the launcher command:

Right click your Apps/Places/System Menu> select Edit Menus> find the app (in this case Ubuntu Software Center> highlight it and click the Properties button on the right> change the "Command:"

It will look something like this:

---

### Post by philinux on 2010-06-29
gksu is the same as gksudo in effect.

The man pages are identical. I really don't know why there is both.

Aha gksu is less typing. ;)

---

### Post by warfacegod on 2010-06-29
> **philinux said:**
> gksu is the same as gksudo in effect.

The man pages are identical. I really don't know why there is both.

Aha gksu is less typing. ;)

That's what I figured.

If less typing is the idea, why not make sudo into su? Curses, then there'd be no sudo su.
I feel a Dr. Suess moment coming on.

Apt-get got su but not sudo.
But not apt-get gksu nor gksudo.

Now there's all these sus and sudos,
Feeling like they'd gotten got.
And all these gksus and gksudos,
Running around knowing they did not.


(Sorry. Off topic, I know, but I couldn't resist.)

---

### Post by 3ruce on 2011-02-26
> **Kevbert said:**
> Do you get problems with Applications-Accessories-Terminal ?
Please try the following (with an active internet connection) and post back any errors
```
sudo apt-get update
sudo apt-get install -f
sudo apt-get upgrade
```The first command will update your software package list, the second will try to force a repair on any damaged packages and the third will upgrade the packages to the latest versions.


This nailed it for me - thank you :-)

---

