---
title: "Can't open anything in &quot;places&quot; menu"
date: 2012-09-08
forum: General Help
---

### Post by josephellengar on 2012-09-08
I am using Gnome Classic in Ubuntu 12.04

Any time that I try to open anything in the "places" menu (for example, home folder), I either get an error saying that no program is associated with this option or I get something that says "opening xxx" where xxx is the option, but no nautilus screen every opens. I can use nautilus by opening it with gnome-do, the commands menu, or hotkeys that I had set up. Do you have any suggestions how I can get the places menu to work again? Thanks!

EDIT: Nautilus works everywhere else, and when I try the other menu applet, it still doesn't work.

---

### Post by cortman on 2012-09-08
> **josephellengar said:**
> I am using Gnome Classic in Ubuntu 12.04

Any time that I try to open anything in the "places" menu (for example, home folder), I either get an error saying that no program is associated with this option or I get something that says "opening xxx" where xxx is the option, but no nautilus screen every opens. I can use nautilus by opening it with gnome-do, the commands menu, or hotkeys that I had set up. Do you have any suggestions how I can get the places menu to work again? Thanks!

EDIT: Nautilus works everywhere else, and when I try the other menu applet, it still doesn't work.

```
sudo apt-get install gnome-panel --reinstall
```

? May do the trick.

---

### Post by josephellengar on 2012-09-08
> **cortman said:**
> ```
sudo apt-get install gnome-panel --reinstall
```

? May do the trick.

Nope. No good. But thanks for the advice. I also restarted the computer and did a pkill gnome-panel.

---

### Post by josephellengar on 2012-09-09
Bump with extra information. When I click on the trash applet in my gnome-panel I get the following error:
> 
Error while spawning nautilus:
No application is registered as handling this file


---

### Post by mc4man on 2012-09-09
You should create a new user, log in to it & see if things work or don't there.
If they work as expected then you've some local setting, config or something amiss which shouldn't be too difficult to track down.

---

### Post by josephellengar on 2012-09-09
> **mc4man said:**
> You should create a new user, log in to it & see if things work or don't there.
If they work as expected then you've some local setting, config or something amiss which shouldn't be too difficult to track down.

Hmm, I created a new user but I can't log in. When I try the screen flashes black for an instant and then it goes back to the login screen. It gives me no message or anything. It also definitely does not say the password is wrong. Actually I've tried to login both with and without a password on the account.

---

### Post by josephellengar on 2012-09-09
Solved it. I had to go into nautilus, right-click on a folder, open with other application, show other applications, click "home folder." I figured this out because when I installed another file manager it worked fine, so I just had to associate nautilus again.

Still haven't figured out why that new user didn't work though, but that's not a big deal since I only use one user account.

---

### Post by mining3 on 2012-12-18
[SIZE=3]There is a definite BUG, YES **[SIZE=4]BUG.[/SIZE] ** I had this happen with the "Places" menu before where Pictures, Documents, Home, Desktop, Music, Do[SIZE=3]w[/SIZE]nloads was like dead links[SIZE=3], totally useless forever, never fixed. [/SIZE]This started before before 10.04,  10.10, 11.04 and now 12.04. IT does not happen with a clean install. But does happen with failed to load side by running versions and upgrades.

Call it what ever YOU like but  it's BUG..... so why not a patch for this  call it the Places Patch[SIZE=3]?[/SIZE]

I put on Mate [SIZE=3]easier[/SIZE] to [SIZE=3]use  then U[/SIZE]nity [SIZE=3]and way better than[/SIZE] the new lousy [SIZE=3]Ubuntu[/SIZE] [SIZE=3]C[/SIZE]lassic ............figured that one out myself looks just like the [SIZE=3]C[/SIZE]lassic should look but the "Places" drop menu still does not work[SIZE=3] as [SIZE=3]aforementioned.[/SIZE] [/SIZE]

It's what is coined as foo foo aka ******* around[/SIZE]

---

