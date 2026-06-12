---
title: "white desktop...my wallpaper doesn't appear!"
date: 2011-04-22
forum: General Help
---

### Post by justborn on 2011-04-22
i'm reccently having problems wid ma wallper.it's like as if a white cloak has been put on top of ma wallpaper.

---

### Post by justborn on 2011-04-22
bump!

---

### Post by KegHead on 2011-04-22
Hi!

just an idea:

goto;

system..preferences..appearance..background.

KegHead

---

### Post by justborn on 2011-04-22
yeah,i tried that...

---

### Post by justborn on 2011-04-23
nyone got a solution? :(

---

### Post by Rasa1111 on 2011-04-23
did you remove Unity by any chance?
I found this..
[http://askubuntu.com/questions/19962/error-with-missing-wallpaper-after-remove-unity-from-sudo-command](http://askubuntu.com/questions/19962/error-with-missing-wallpaper-after-remove-unity-from-sudo-command)

Sorry if it's no help. lol :???:

good luck.

---

### Post by justborn on 2011-04-23
> **Rasa1111 said:**
> did you remove Unity by any chance?
I found this..
[http://askubuntu.com/questions/19962/error-with-missing-wallpaper-after-remove-unity-from-sudo-command](http://askubuntu.com/questions/19962/error-with-missing-wallpaper-after-remove-unity-from-sudo-command)

Sorry if it's no help. lol :???:

good luck.

yes,i jus realized that...the problem occurred after i uninstalled unity in meerkat,but now i've upgraded to 11.04.and the problem still exists...

---

### Post by KegHead on 2011-04-23
Hi!

Just an idea:

Have you tried 11.04 Ubuntu classic?

KegHead

---

### Post by justborn on 2011-04-23
> **Rasa1111 said:**
> did you remove Unity by any chance?
I found this..
[http://askubuntu.com/questions/19962/error-with-missing-wallpaper-after-remove-unity-from-sudo-command](http://askubuntu.com/questions/19962/error-with-missing-wallpaper-after-remove-unity-from-sudo-command)

Sorry if it's no help. lol :???:

good luck.

by following the the solution in the link,won't i mess up my unity?

---

### Post by justborn on 2011-04-24
> **KegHead said:**
> Hi!

Just an idea:

Have you tried 11.04 Ubuntu classic?

KegHead

yeah,ve the same problem in classic mode too.

---

### Post by KegHead on 2011-04-24
Hi!

Maybe a defective monitor or connection/wire?

KegHead

---

### Post by Krytarik on 2011-04-24
> **justborn said:**
> by following the the solution in the link,won't i mess up my unity?
If you mean removing "mutter" and its dependencies, you can safely do that, since Unity in 11.04 uses Compiz, whereas Unity in 10.10 uses Mutter.

I suggest just running:
```
sudo apt-get autoremove
```
If that doesn't remove "mutter", remove it manually.

Also, check if one of the mentioned (now broken) symlinks might be in place.

Hope it helps!

---

### Post by justborn on 2011-04-25
> **KegHead said:**
> Hi!

Maybe a defective monitor or connection/wire?

KegHead

c'mon dude,seriously???y do i get a feeling that u r just doing it for the beans?

---

### Post by justborn on 2011-04-25
n guys please checkout ma idea at brainstorm(my signature link)...n plz vote, if u like it. :KS

---

### Post by KegHead on 2011-04-25
Hi!

I'm seriously trying to help.

KegHead

---

### Post by Spyderkid on 2011-04-25
hold Alt + F2,   then type in ccsm into the box that appears and press enter.

then find under utilities the box that says Wallpaper.
Change that and apple it.

---

### Post by justborn on 2011-04-25
> **Krytarik said:**
> If you mean removing "mutter" and its dependencies, you can safely do that, since Unity in 11.04 uses Compiz, whereas Unity in 10.10 uses Mutter.

I suggest just running:
```
sudo apt-get autoremove
```
If that doesn't remove "mutter", remove it manually.

Also, check if one of the mentioned (now broken) symlinks might be in place.

Hope it helps!

i performed autoremove,and mutter hasn't been installed in the first place,so there's no point in  trying to remove it.

---

### Post by justborn on 2011-04-25
> **Spyderkid said:**
> hold Alt + F2,   then type in ccsm into the box that appears and press enter.

then find under utilities the box that says Wallpaper.
Change that and apple it.

i'd ve to install ccsm for that...can it not be done without doing that?

---

### Post by Krytarik on 2011-04-25
> **justborn said:**
> i performed autoremove,and mutter hasn't been installed in the first place,so there's no point in  trying to remove it.
Really!? Without installing Mutter as a dependency you were not even have been able to install Unity at all:
[http://packages.ubuntu.com/maverick-updates/unity](http://packages.ubuntu.com/maverick-updates/unity)

Please check if it is still installed with:
```
dpkg -l |grep mutter
```Also, how about the mentioned symlinks?

---

### Post by justborn on 2011-04-27
```
arpit@arpit-Inspiron-N5010:~$ mutter
The program 'mutter' is currently not installed.  You can install it by typing:
sudo apt-get install mutter
```

i toldya...

---

### Post by wojox on 2011-04-27
Let me guess, Nvidia Driver?

---

### Post by justborn on 2011-04-27
> **wojox said:**
> Let me guess, Nvidia Driver?

nah...ATI, n for some reason i'm not able to activate it using the gui.

---

### Post by zebrattt on 2011-04-30
> **Krytarik said:**
> Really!? Without installing Mutter as a dependency you were not even have been able to install Unity at all:
[http://packages.ubuntu.com/maverick-updates/unity](http://packages.ubuntu.com/maverick-updates/unity)

Please check if it is still installed with:
```
dpkg -l |grep mutter
```Also, how about the mentioned symlinks?


 I have the same problem (wallpaper not displayed). I didn't have mutter.  but after I install mutter,  there is still no  wallpaper.

---

### Post by Krytarik on 2011-04-30
> **zebrattt said:**
> I have the same problem (wallpaper not displayed). I didn't have mutter.  but after I install mutter,  there is still no  wallpaper.
You don't need to install Mutter, in fact it was an idea that *it* may be the cause of that issue.
There seem to be a number of users with Natty who are experiencing that issue, but right now I have no idea what may be the cause of it.

---

### Post by justborn on 2011-05-16
anyone???my desktops been white since the day i upgraded to 11.04.....

---

### Post by Krytarik on 2011-05-16
How about replacing the official Nautilus by Nautilus Elementary?
Not only did we have success with it in another thread, but you may also like its slimmer look and additional features.

To 'upgrade' to it:
```
sudo add-apt-repository ppa:am-monkeyd/nautilus-elementary-ppa
sudo apt-get update
sudo apt-get upgrade

```[https://launchpad.net/~am-monkeyd/+archive/nautilus-elementary-ppa]("https://launchpad.net/%7Eam-monkeyd/+archive/nautilus-elementary-ppa")

To 'downgrade' to the official version again:
```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:am-monkeyd/nautilus-elementary-ppa
```After either operation, restart Nautilus:
```
killall nautilus
```Greetings.

---

### Post by justborn on 2011-05-18
> **Krytarik said:**
> How about replacing the official Nautilus by Nautilus Elementary?
Not only did we have success with it in another thread, but you may also like its slimmer look and additional features.

To 'upgrade' to it:
```
sudo add-apt-repository ppa:am-monkeyd/nautilus-elementary-ppa
sudo apt-get update
sudo apt-get upgrade

```[https://launchpad.net/~am-monkeyd/+archive/nautilus-elementary-ppa]("https://launchpad.net/%7Eam-monkeyd/+archive/nautilus-elementary-ppa")

To 'downgrade' to the official version again:
```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:am-monkeyd/nautilus-elementary-ppa
```After either operation, restart Nautilus:
```
killall nautilus
```Greetings.

It only partly solves the issue.when i login i get the same wallpaper that was before updating from the repos&#8230;..the selected wallpaper remains only untill the particular session.

---

### Post by Krytarik on 2011-05-18
> **justborn said:**
> when i login i get the same wallpaper that was before updating from the repos
Does that mean that you can't change the wallpaper?
> **justborn said:**
> the selected wallpaper remains only untill the particular session.
Is your theme working correctly?

---

### Post by justborn on 2011-05-19
> **Krytarik said:**
> Does that mean that you can't change the wallpaper?

Is your theme working correctly?

my themes r working f9.but my chosen wallpaper only lasts till the end of one session.if i log-out and then again log-in or restart,my desktop will have the same wallpaper as that of before updating from repos.

---

### Post by Krytarik on 2011-05-19
Make sure that everything in your home directory is owned by you.

---

### Post by justborn on 2011-05-20
> **Krytarik said:**
> Make sure that everything in your home directory is owned by you.

and how do i do that?

---

### Post by linuxinstalledfromhdd on 2011-05-20
Ok ok..

You had Unity installed in 10.10? 

Then you uninstalled it.

Then you upgraded to Natty..

Then you reinstalled it again.

Then your wallpaper had a breakdown.

Look.. look..  

Backup your stuff. 

Reinstall Ubuntu 11.04 from a live USB stick. 

It takes what, the most of 20 minutes tops, even on an old slow system. 

[http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/](http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/)

Follow that checklist step, by step, by step..  Get your system together.

---

### Post by Krytarik on 2011-05-20
> **justborn said:**
> and how do i do that?
I thought you would know, sorry.

I could have included that command in my previous post, as it's not really much to type:
```
sudo chown USERNAME:USERNAME -R /home/USERNAME
```

---

### Post by justborn on 2011-05-22
> **Krytarik said:**
> I thought you would know, sorry.

I could have included that command in my previous post, as it's not really much to type:
```
sudo chown USERNAME:USERNAME -R /home/USERNAME
```

```
chown: cannot access `/home/arpit/.gvfs': Permission denied
```


i got this. :confused:

---

### Post by Krytarik on 2011-05-22
I get the same error, so that's fine.

Did that fix the issue?

---

### Post by justborn on 2011-05-24
> **Krytarik said:**
> I get the same error, so that's fine.

Did that fix the issue?
 

:( no,it's still da same.

---

