---
title: "lightdm accepts password and drops back to login window"
date: 2011-10-13
forum: General Help
---

### Post by neilmw1 on 2011-10-13
Hi, 

Just upgraded to 11.10, when I put my password in on the lightdm manager (unity selected) it accepts it, a mouse pointer appears on a new window, then it flashes back to the console, and reloads lightdm.

I can log on using unity 2D perfectly - I've looked in the /var/log/lightdm/lightdm log file but I can't see anything to suggest an error. 

Any ideas on what this could be?

Thanks :)

---

### Post by effenberg0x0 on 2011-10-13
I'm supposing your PC has the OpenGL capabilities to run Unity installed and OK. You can test that yourself by running 

```
DISPLAY=:0.0 /usr/lib/nux/unity_support_test -p

```

Save your work.
If you can login to 2D, open a terminal.
If you can't, use Ctrl+Alt+F1 to F6 to drop you to console and login with user/password.

Try this command:

```
sudo mv ~/.Xauthority ~/.Xauthority.backup
sudo service lightdm restart
```

Try to login at lightdm and report back please.

Regards,
Effenberg

---

### Post by neilmw1 on 2011-10-13
Thanks for replying.

I gave the unity_support_test command a try, it just crashed out of X and took me back to the lightdm login window (which is what I suspect is happening when I choose unity - it looks the same anyway).

I've also tried the mv command and restarted the lightdm service and tried again, I am still getting the same issue.

I am fairly sure it should support OpenGL? It's pretty new, only 2 months old.

---

### Post by effenberg0x0 on 2011-10-13
You might need to install proper video drivers. It is very unlikely that unity_support_test would crash.

At a console, run:

lspci | grep -i VGA

Look for information on how to setup your video card driver at the Ubuntu Documentation, here:
[https://help.ubuntu.com/community/Video](https://help.ubuntu.com/community/Video)

Regards,
Effenberg

---

### Post by rob311 on 2011-10-13
> **effenberg0x0 said:**
> 

Try this command:

```
sudo mv ~/.Xauthority ~/.Xauthority.backup
sudo service lightdm restart
```



Thank You! I couldn't get into 2D or 3D. Removing .Xauthority did the trick.

---

### Post by effenberg0x0 on 2011-10-13
Cool! Enjoy Oneiric!

Regards,
Effenberg

---

### Post by philcolbourn on 2012-07-08
> **effenberg0x0 said:**
> I'm supposing your PC has the OpenGL capabilities to run Unity installed and OK. You can test that yourself by running 

```
DISPLAY=:0.0 /usr/lib/nux/unity_support_test -p

```

Save your work.
If you can login to 2D, open a terminal.
If you can't, use Ctrl+Alt+F1 to F6 to drop you to console and login with user/password.

Try this command:

```
sudo mv ~/.Xauthority ~/.Xauthority.backup
sudo service lightdm restart
```

Try to login at lightdm and report back please.

Regards,
Effenberg

Worked for me too. Thanks.

I'm using 12.04.

Also, in my case, all Gnome and Unity sessions (as well as i3) did not work.

---

