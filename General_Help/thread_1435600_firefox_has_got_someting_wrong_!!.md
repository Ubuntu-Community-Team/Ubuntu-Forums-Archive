---
title: "firefox has got someting wrong !!"
date: 2010-03-21
forum: General Help
---

### Post by nos09 on 2010-03-21
when i start firefox today the top massage says that 

> " Your browser has been updated and needs to be restarted"

i thought upgrading to firefox 3.6 would do the trick but no luck
and i just updated the firefox with the following command 

> sudo add-apt-repository ppa:ubuntu-mozilla-daily/ppa

Update source list

   >  sudo apt-get update

>  Install firefox 3.6


and when i type in terminal 
> codename-nos@codename-nos-desktop:~$ firefox --v
Mozilla Firefox 3.5.8, Copyright (c) 1998 - 2010 mozilla.org


---

### Post by _h_ on 2010-03-21
What does it say under Help -> About Mozilla FireFox?

---

### Post by nos09 on 2010-03-21
fixed it.. by restarting my pc.( which i dont like to :p)

and it was like pop-up request with "restart" button on that

---

### Post by soltanis on 2010-03-21
When Firefox is upgraded via the package manager while it is running, it needs to be closed completely and then relooaded into memory to make sure the image running in memory is concurrent with the one on your disk. You shouldn't need to restart your computer, but simply restarting Firefox should be enough.

---

### Post by nos09 on 2010-03-21
> **soltanis said:**
> When Firefox is upgraded via the package manager while it is running, it needs to be closed completely and then relooaded into memory to make sure the image running in memory is concurrent with the one on your disk. You shouldn't need to restart your computer, but simply restarting Firefox should be enough.

ya thats wat i did but it didnt worked so i had to restart my pc.
by closing browser it was not working but i think killing all the firefox pid would do that ( but realized it later ) ;)

---

### Post by soltanis on 2010-03-21
Yeah, Firefox has this annoying habit of running in the background even when the browser window is closed. You should try

```

sudo killall firefox

```

To try to get rid of all processes.

EDIT: Or pressing the restart button in the drop down dialog also does this.

---

### Post by alex4c on 2010-03-22
I wanted to update Firefox (I didn't have any errors I just wanted update) and I followed nos09's post but when I type:
>                                Install firefox 3.6                      
this is what I got: 
>  No command 'Install' found, did you mean:
 Command 'install' from package 'coreutils' (main)
Install: command not found

Sorry, I'm very new, have no idea what this means.

---

### Post by soltanis on 2010-03-22
The program is "apt-get" which does install ("aptitude" also works almost the same). Both of them are package managers which download dpkgs and install them onto your system from the repositories while tracking dependencies and keeping them up to date for you (trust me, on systems without package managers this really sucks).

You should do

```

sudo apt-get install <packages>

```

EDIT:
But his post does not outline the commands for getting Firefox 3.6 clearly. If you want to do that follow the steps on here
[http://www.ubuntugeek.com/how-to-install-firefox-3-6-in-ubuntu-karmicjauntyintrepidhardy.html](http://www.ubuntugeek.com/how-to-install-firefox-3-6-in-ubuntu-karmicjauntyintrepidhardy.html)

---

### Post by alex4c on 2010-03-22
Thanks.

---

